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
# <a name="configuring-timeout-values-on-a-binding"></a><span data-ttu-id="dced7-102">在绑定上配置超时值</span><span class="sxs-lookup"><span data-stu-id="dced7-102">Configuring Timeout Values on a Binding</span></span>
<span data-ttu-id="dced7-103">WCF 绑定中提供了很多超时设置。</span><span class="sxs-lookup"><span data-stu-id="dced7-103">There are a number of timeout settings available in WCF bindings.</span></span> <span data-ttu-id="dced7-104">正确设置这些超时设置不仅可以提高您服务的性能，而且对发挥您服务的可用性和安全性起到重要作用。</span><span class="sxs-lookup"><span data-stu-id="dced7-104">Setting these timeout settings correctly can improve not only your service’s performance but also play a role in the usability and security of your service.</span></span> <span data-ttu-id="dced7-105">WCF 绑定中提供了下列超时：</span><span class="sxs-lookup"><span data-stu-id="dced7-105">The following timeouts are available on WCF bindings:</span></span>  
  
1. <span data-ttu-id="dced7-106">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="dced7-106">OpenTimeout</span></span>  
  
2. <span data-ttu-id="dced7-107">CloseTimeout</span><span class="sxs-lookup"><span data-stu-id="dced7-107">CloseTimeout</span></span>  
  
3. <span data-ttu-id="dced7-108">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="dced7-108">SendTimeout</span></span>  
  
4. <span data-ttu-id="dced7-109">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="dced7-109">ReceiveTimeout</span></span>  
  
## <a name="wcf-binding-timeouts"></a><span data-ttu-id="dced7-110">WCF 绑定超时</span><span class="sxs-lookup"><span data-stu-id="dced7-110">WCF Binding Timeouts</span></span>  
 <span data-ttu-id="dced7-111">本主题中讨论的每个设置都是在绑定本身上设置的（无论是在代码还是在配置中）。</span><span class="sxs-lookup"><span data-stu-id="dced7-111">Each of the settings discussed in this topic are made on the binding itself, either in code or configuration.</span></span> <span data-ttu-id="dced7-112">下面的代码演示如何对自承载服务的上下文中的 WCF 绑定以编程方式设置超时。</span><span class="sxs-lookup"><span data-stu-id="dced7-112">The following code shows how to programmatically set timeouts on a WCF binding in the context of a self-hosted service.</span></span>  
  
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
  
 <span data-ttu-id="dced7-113">下面的示例演示如何在应用程序配置文件中配置绑定超时。</span><span class="sxs-lookup"><span data-stu-id="dced7-113">The following example shows how to configure timeouts on a binding in a configuration file.</span></span>  
  
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
  
 <span data-ttu-id="dced7-114">有关这些设置的更多信息，可以在 <xref:System.ServiceModel.Channels.Binding> 类的参考文档中找到。</span><span class="sxs-lookup"><span data-stu-id="dced7-114">More information about these settings can be found in the documentation for the <xref:System.ServiceModel.Channels.Binding> class.</span></span>  
  
### <a name="client-side-timeouts"></a><span data-ttu-id="dced7-115">客户端超时</span><span class="sxs-lookup"><span data-stu-id="dced7-115">Client-side Timeouts</span></span>  
 <span data-ttu-id="dced7-116">在客户端：</span><span class="sxs-lookup"><span data-stu-id="dced7-116">On the client side:</span></span>  
  
1. <span data-ttu-id="dced7-117">SendTimeout — 用于初始化 OperationTimeout，此设置控制发送消息的整个过程，包括接收请求/答复服务操作的答复消息。</span><span class="sxs-lookup"><span data-stu-id="dced7-117">SendTimeout – used to initialize the OperationTimeout, which governs the whole process of sending a message, including receiving a reply message for a request/reply service operation.</span></span> <span data-ttu-id="dced7-118">从回调协定方法发送答复消息时，此超时也适用。</span><span class="sxs-lookup"><span data-stu-id="dced7-118">This timeout also applies when sending reply messages from a callback contract method.</span></span>  
  
2. <span data-ttu-id="dced7-119">OpenTimeout — 打开通道时未不指定任何显式超时值时使用。</span><span class="sxs-lookup"><span data-stu-id="dced7-119">OpenTimeout – used when opening channels when no explicit timeout value is specified.</span></span>  
  
3. <span data-ttu-id="dced7-120">CloseTimeout — 关闭通道时未不指定任何显式超时值时使用。</span><span class="sxs-lookup"><span data-stu-id="dced7-120">CloseTimeout – used when closing channels when no explicit timeout value is specified.</span></span>  
  
4. <span data-ttu-id="dced7-121">ReceiveTimeout – 未使用。</span><span class="sxs-lookup"><span data-stu-id="dced7-121">ReceiveTimeout – is not used.</span></span>  
  
### <a name="service-side-timeouts"></a><span data-ttu-id="dced7-122">服务端超时</span><span class="sxs-lookup"><span data-stu-id="dced7-122">Service-side Timeouts</span></span>  
 <span data-ttu-id="dced7-123">在服务端：</span><span class="sxs-lookup"><span data-stu-id="dced7-123">On the service side:</span></span>  
  
1. <span data-ttu-id="dced7-124">SendTimeout、 OpenTimeout、 CloseTimeout 都在客户端上相同。</span><span class="sxs-lookup"><span data-stu-id="dced7-124">SendTimeout, OpenTimeout, CloseTimeout are the same as on the client.</span></span>  
  
2. <span data-ttu-id="dced7-125">ReceiveTimeout — 服务框架层用于初始化会话空闲超时，它控制一个会话在空闲多久之后发生超时。</span><span class="sxs-lookup"><span data-stu-id="dced7-125">ReceiveTimeout – used by the Service Framework Layer to initialize the session-idle timeout which controls how long a session can be idle before timing out.</span></span>
