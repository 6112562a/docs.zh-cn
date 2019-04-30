---
title: 使用 ServiceHostFactory 扩展宿主
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: e553fe161ffc5b50850d916cf1cef6b38dd5c1a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991310"
---
# <a name="extending-hosting-using-servicehostfactory"></a>使用 ServiceHostFactory 扩展宿主
标准<xref:System.ServiceModel.ServiceHost>用于承载服务中 Windows Communication Foundation (WCF) API 是 WCF 体系结构中的扩展点。 在打开服务之前，用户可以从 <xref:System.ServiceModel.ServiceHost> 派生各自的宿主类，通常是重写 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> 以使用 <xref:System.ServiceModel.Description.ServiceDescription> 来以强制方式添加默认终结点或修改行为。  
  
 在自承载环境中，无需创建自定义 <xref:System.ServiceModel.ServiceHost>，因为您可以编写实例化宿主的代码，然后在实例化宿主后调用宿主上的 <xref:System.ServiceModel.ICommunicationObject.Open>。 在这两个步骤之间，可以执行所需的任何操作。 例如，可以添加新的 <xref:System.ServiceModel.Description.IServiceBehavior>：  
  
```  
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 此方法不可重用。 操作说明的代码将会编码到宿主程序中（在本例中为 Main() 函数），因此在其他上下文中重用该逻辑很困难。 还有其他不需要强制性代码的添加 <xref:System.ServiceModel.Description.IServiceBehavior> 的方式。 可以从 <xref:System.ServiceModel.ServiceBehaviorAttribute> 派生属性并将其放置在服务实现类型上，或者可以使自定义行为成为可配置的并使用配置以动态方式对其进行组合。  
  
 但是，对示例稍加变化也可解决此问题。 一个办法是将添加 ServiceBehavior 的代码从 `Main()` 中移动到 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 的自定义派生的 <xref:System.ServiceModel.ServiceHost> 方法中：  
  
```  
public class DerivedHost : ServiceHost  
{  
   public DerivedHost( Type t, params Uri baseAddresses ) :  
      base( t, baseAddresses ) {}  
  
   public override void OnOpening()  
   {  
  this.Description.Add( new MyServiceBehavior() );  
   }  
}  
```  
  
 然后，可以使用以下代码来替代 `Main()`：  
  
```  
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 现在您已将自定义逻辑封装到一个全新的抽象中，该抽象可以很容易地在许多不同的宿主可执行文件之间进行重用。  
  
 如何从 Internet 信息服务 (IIS) 或 Windows 进程激活服务 (WAS) 中使用此自定义 <xref:System.ServiceModel.ServiceHost> 并不是立即就显而易见的。 这些环境与自承载环境不同，因为宿主环境是代表应用程序实例化 <xref:System.ServiceModel.ServiceHost> 的环境。 IIS 和 WAS 宿主基础结构不清楚有关自定义 <xref:System.ServiceModel.ServiceHost> 派生的任何情况。  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory> 旨在解决从 IIS 或 WAS 中访问自定义 <xref:System.ServiceModel.ServiceHost> 的问题。 因为从 <xref:System.ServiceModel.ServiceHost> 派生的自定义宿主是动态配置的并且可能为各种类型，所以宿主环境决从不会直接将其实例化。 相反，WCF 使用工厂模式提供宿主环境和服务的具体类型之间的间接层。 除非进行通知，否则它使用返回 <xref:System.ServiceModel.Activation.ServiceHostFactory> 的实例的 <xref:System.ServiceModel.ServiceHost> 的默认实现。 但也可以提供您自己通过指定工厂实现中的 CLR 类型名称返回派生的宿主的工厂@ServiceHost指令。  
  
 对于简单的情形，实现您自己的工厂的练习应该是简单明了的。 例如，下面是用于返回派生的 <xref:System.ServiceModel.Activation.ServiceHostFactory> 的自定义 <xref:System.ServiceModel.ServiceHost>：  
  
```  
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 若要使用此工厂，而不使用默认工厂，提供中的类型名称@ServiceHost指令，如下所示：  
  
```  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 尽管对于从 <xref:System.ServiceModel.ServiceHost> 返回的 <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A> 可以执行什么操作没有技术限制，但建议您尽可能使工厂实现简单化。 如果有大量的自定义逻辑，最好将这些逻辑放入宿主内而不是工厂内，以便可以重用它们。  
  
 应在这里提及另一个承载 API 的层。 WCF 还拥有<xref:System.ServiceModel.ServiceHostBase>并<xref:System.ServiceModel.Activation.ServiceHostFactoryBase>，从中<xref:System.ServiceModel.ServiceHost>和<xref:System.ServiceModel.Activation.ServiceHostFactory>分别派生。 对于您必须通过自己的自定义创建来交换元数据系统的大型组件的更高级方案，存在上述这些特性。
