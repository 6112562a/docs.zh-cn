---
title: 负载均衡
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: a444df2b05803ec54c5bd9030ce12209cfe9bd07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183982"
---
# <a name="load-balancing"></a><span data-ttu-id="261ba-102">负载均衡</span><span class="sxs-lookup"><span data-stu-id="261ba-102">Load Balancing</span></span>
<span data-ttu-id="261ba-103">增加 Windows 通信基础 （WCF） 应用程序的容量的一个方法是通过将它们部署到负载均衡的服务器场来扩展它们。</span><span class="sxs-lookup"><span data-stu-id="261ba-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="261ba-104">WCF 应用程序可以使用标准负载平衡技术实现负载平衡，包括 Windows 网络负载平衡等软件负载平衡器以及基于硬件的负载平衡设备。</span><span class="sxs-lookup"><span data-stu-id="261ba-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="261ba-105">以下各节讨论使用各种系统提供的绑定构建的负载平衡 WCF 应用程序的注意事项。</span><span class="sxs-lookup"><span data-stu-id="261ba-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="261ba-106">基本 HTTP 绑定的负载平衡</span><span class="sxs-lookup"><span data-stu-id="261ba-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="261ba-107">从负载平衡的角度来看，使用<xref:System.ServiceModel.BasicHttpBinding>进行通信的 WCF 应用程序与其他常见类型的 HTTP 网络流量（静态 HTML 内容、ASP.NET页或 ASMX Web 服务）没有什么不同。</span><span class="sxs-lookup"><span data-stu-id="261ba-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="261ba-108">使用此绑定的 WCF 通道本质上是无状态的，并在通道关闭时终止其连接。</span><span class="sxs-lookup"><span data-stu-id="261ba-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="261ba-109">因此，<xref:System.ServiceModel.BasicHttpBinding> 可以很好地与现有的 HTTP 负载平衡技术一起使用。</span><span class="sxs-lookup"><span data-stu-id="261ba-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="261ba-110">默认情况下，<xref:System.ServiceModel.BasicHttpBinding> 会在消息中发送一个具有 `Keep-Alive` 值的连接 HTTP 标头，该标头可让客户端建立到支持这些客户端的服务的持续连接。</span><span class="sxs-lookup"><span data-stu-id="261ba-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="261ba-111">这种配置具有高的吞吐量，因为可以重新使用以前建立的连接向同一个服务器发送后续消息。</span><span class="sxs-lookup"><span data-stu-id="261ba-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="261ba-112">然而，重新使用连接可能导致客户端与负载平衡场中的特定服务器密切关联，从而降低循环负载平衡的效率。</span><span class="sxs-lookup"><span data-stu-id="261ba-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="261ba-113">如果不需要此行为，则可以使用 `Keep-Alive` 或用户定义的 <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> 在使用 <xref:System.ServiceModel.Channels.CustomBinding> 属性的服务器上禁用 HTTP <xref:System.ServiceModel.Channels.Binding>。</span><span class="sxs-lookup"><span data-stu-id="261ba-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="261ba-114">下面的示例演示如何使用配置来执行该操作。</span><span class="sxs-lookup"><span data-stu-id="261ba-114">The following example shows how to do this using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="261ba-115">使用 .NET 框架 4 中引入的简化配置，可以使用以下简化配置完成相同的行为。</span><span class="sxs-lookup"><span data-stu-id="261ba-115">Using the simplified configuration introduced in .NET Framework 4, the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="customBinding" />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="261ba-116">有关默认终结点、绑定和行为的详细信息，请参阅[简化配置](simplified-configuration.md)和 [WCF 服务的简化配置](./samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="261ba-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="261ba-117">WSHttp 绑定和 WSDualHttp 绑定的负载平衡</span><span class="sxs-lookup"><span data-stu-id="261ba-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="261ba-118">如果对默认的绑定配置进行一些修改，则 <xref:System.ServiceModel.WSHttpBinding> 和 <xref:System.ServiceModel.WSDualHttpBinding> 都可以使用 HTTP 负载平衡技术来实现负载平衡。</span><span class="sxs-lookup"><span data-stu-id="261ba-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="261ba-119">关闭安全上下文的建立：这可以通过将 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> 上的 <xref:System.ServiceModel.WSHttpBinding> 属性设置为 `false` 来完成。</span><span class="sxs-lookup"><span data-stu-id="261ba-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="261ba-120">或者，如果需要安全会话，则可以使用安全会话主题中所述的有状态安全[会话](./feature-details/secure-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="261ba-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](./feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="261ba-121">有状态安全会话使服务保持无状态，因为安全会话的所有状态都随每个请求作为保护安全令牌的一部分进行传输。</span><span class="sxs-lookup"><span data-stu-id="261ba-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="261ba-122">请注意，若要启用有状态安全会话，必须使用 <xref:System.ServiceModel.Channels.CustomBinding> 或用户定义的 <xref:System.ServiceModel.Channels.Binding>，因为系统提供的 <xref:System.ServiceModel.WSHttpBinding> 和 <xref:System.ServiceModel.WSDualHttpBinding> 上并不会公开必需的配置设置。</span><span class="sxs-lookup"><span data-stu-id="261ba-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
- <span data-ttu-id="261ba-123">不要使用可靠会话。</span><span class="sxs-lookup"><span data-stu-id="261ba-123">Do not use reliable sessions.</span></span> <span data-ttu-id="261ba-124">默认情况下此功能处于关闭状态。</span><span class="sxs-lookup"><span data-stu-id="261ba-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="261ba-125">使 Net.TCP 绑定实现负载平衡</span><span class="sxs-lookup"><span data-stu-id="261ba-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="261ba-126">可以使用 IP 层负载平衡技术实现 <xref:System.ServiceModel.NetTcpBinding> 的负载平衡。</span><span class="sxs-lookup"><span data-stu-id="261ba-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="261ba-127">不过，默认情况下，<xref:System.ServiceModel.NetTcpBinding> 会汇集 TCP 连接以减少连接延迟。</span><span class="sxs-lookup"><span data-stu-id="261ba-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="261ba-128">这是一种干扰负载平衡基本机制的优化。</span><span class="sxs-lookup"><span data-stu-id="261ba-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="261ba-129">用于优化 <xref:System.ServiceModel.NetTcpBinding> 的主配置值是租约超时，它是连接池设置的一部分。</span><span class="sxs-lookup"><span data-stu-id="261ba-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="261ba-130">连接池导致客户端连接与场内特定的服务器关联。</span><span class="sxs-lookup"><span data-stu-id="261ba-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="261ba-131">随着这些连接的生存期的增加（一个受租约超时设置控制的因素），场内不同服务器上的负载分布会变得不平衡。</span><span class="sxs-lookup"><span data-stu-id="261ba-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="261ba-132">结果使平均调用时间增加。</span><span class="sxs-lookup"><span data-stu-id="261ba-132">As a result the average call time increases.</span></span> <span data-ttu-id="261ba-133">因此，在负载平衡方案中使用 <xref:System.ServiceModel.NetTcpBinding> 时，应考虑减少由绑定使用的默认租约超时。</span><span class="sxs-lookup"><span data-stu-id="261ba-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="261ba-134">虽然租约超时的最佳值取决于应用程序，但 30 秒的租约超时对于负载平衡方案不失为一个合理的始点。</span><span class="sxs-lookup"><span data-stu-id="261ba-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="261ba-135">有关通道租约超时和其他传输配额的详细信息，请参阅[传输配额](./feature-details/transport-quotas.md)。</span><span class="sxs-lookup"><span data-stu-id="261ba-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="261ba-136">若要在负载平衡方案中获得最佳性能，请考虑使用 <xref:System.ServiceModel.NetTcpSecurity>（<xref:System.ServiceModel.SecurityMode.Transport> 或 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>）。</span><span class="sxs-lookup"><span data-stu-id="261ba-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="261ba-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="261ba-137">See also</span></span>

- [<span data-ttu-id="261ba-138">Internet Information Services 承载最佳做法</span><span class="sxs-lookup"><span data-stu-id="261ba-138">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)
