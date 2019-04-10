---
title: 在绑定上配置超时值
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: f323dfff338f8a3ba24caab6df3b3916d3ae0d13
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59339757"
---
# <a name="configuring-timeout-values-on-a-binding"></a>在绑定上配置超时值
WCF 绑定中提供了很多超时设置。 正确设置这些超时设置不仅可以提高您服务的性能，而且对发挥您服务的可用性和安全性起到重要作用。 WCF 绑定中提供了下列超时：  
  
1. OpenTimeout  
  
2. CloseTimeout  
  
3. SendTimeout  
  
4. ReceiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>WCF 绑定超时  
 本主题中讨论的每个设置都是在绑定本身上设置的（无论是在代码还是在配置中）。 下面的代码演示如何对自承载服务的上下文中的 WCF 绑定以编程方式设置超时。  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");
    
    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));
        
        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);
        
        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();
        
        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 下面的示例演示如何在应用程序配置文件中配置绑定超时。  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00" 
                 closeTimeout="00:10:00" 
                 sendTimeout="00:10:00" 
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 有关这些设置的更多信息，可以在 <xref:System.ServiceModel.Channels.Binding> 类的参考文档中找到。  
  
### <a name="client-side-timeouts"></a>客户端超时  
 在客户端：  
  
1. SendTimeout — 用于初始化 OperationTimeout，此设置控制发送消息的整个过程，包括接收请求/答复服务操作的答复消息。 从回调协定方法发送答复消息时，此超时也适用。  
  
2. OpenTimeout — 打开通道时未不指定任何显式超时值时使用。  
  
3. CloseTimeout — 关闭通道时未不指定任何显式超时值时使用。  
  
4. ReceiveTimeout – 未使用。  
  
### <a name="service-side-timeouts"></a>服务端超时  
 在服务端：  
  
1. SendTimeout、 OpenTimeout、 CloseTimeout 都在客户端上相同。  
  
2. ReceiveTimeout — 服务框架层用于初始化会话空闲超时，它控制一个会话在空闲多久之后发生超时。
