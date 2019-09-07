---
title: <netTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: c2d0a5729aeea3cd30e07ce1cfa485bda7b8ed20
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400143"
---
# <a name="nettcpbinding"></a><span data-ttu-id="1f425-101">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="1f425-101">\<netTcpBinding></span></span>

<span data-ttu-id="1f425-102">指定一种适合于跨计算机通信的安全、可靠且进行了优化的绑定。</span><span class="sxs-lookup"><span data-stu-id="1f425-102">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="1f425-103">默认情况下，它会生成一个运行时通信堆栈，该堆栈包含 Windows Security 以保证消息安全性和进行身份验证，包含 TCP 以便进行消息传递，并且包含二进制消息编码机制。</span><span class="sxs-lookup"><span data-stu-id="1f425-103">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

<span data-ttu-id="1f425-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f425-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1f425-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1f425-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1f425-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<绑定 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="1f425-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="1f425-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netTcpBinding >**</span><span class="sxs-lookup"><span data-stu-id="1f425-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netTcpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f425-108">语法</span><span class="sxs-lookup"><span data-stu-id="1f425-108">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f425-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="1f425-109">Attributes and elements</span></span>

<span data-ttu-id="1f425-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1f425-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f425-111">特性</span><span class="sxs-lookup"><span data-stu-id="1f425-111">Attributes</span></span>  
  
|<span data-ttu-id="1f425-112">特性</span><span class="sxs-lookup"><span data-stu-id="1f425-112">Attribute</span></span>|<span data-ttu-id="1f425-113">描述</span><span class="sxs-lookup"><span data-stu-id="1f425-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="1f425-114">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1f425-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="1f425-115">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1f425-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1f425-116">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1f425-116">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="1f425-117">指定用于分析 URI 的 HTTP 主机名比较模式。</span><span class="sxs-lookup"><span data-stu-id="1f425-117">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="1f425-118">此属性的类型为 <xref:System.ServiceModel.HostNameComparisonMode>，指示在对 URI 进行匹配时，是否使用主机名来访问服务。</span><span class="sxs-lookup"><span data-stu-id="1f425-118">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="1f425-119">默认值为 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示忽略匹配项中的主机名。</span><span class="sxs-lookup"><span data-stu-id="1f425-119">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="1f425-120">一个正整数，指定侦听器上等待接受的最大通道数。</span><span class="sxs-lookup"><span data-stu-id="1f425-120">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="1f425-121">超出此限制的连接会被排队，直到连接数低于限制值。</span><span class="sxs-lookup"><span data-stu-id="1f425-121">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="1f425-122">`connectionTimeout` 属性限制客户端在引发连接异常之前将等待连接的时间。</span><span class="sxs-lookup"><span data-stu-id="1f425-122">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="1f425-123">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="1f425-123">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="1f425-124">一个整数，指定此绑定的最大缓冲池大小。</span><span class="sxs-lookup"><span data-stu-id="1f425-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="1f425-125">默认值为 512 \* 1024 字节。</span><span class="sxs-lookup"><span data-stu-id="1f425-125">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="1f425-126">Windows Communication Foundation (WCF) 的许多部件使用缓冲区。</span><span class="sxs-lookup"><span data-stu-id="1f425-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="1f425-127">每次使用缓冲区时，创建和销毁它们都将占用大量资源，而缓冲区的垃圾回收过程也是如此。</span><span class="sxs-lookup"><span data-stu-id="1f425-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="1f425-128">利用缓冲池，可以从缓冲池中获得缓冲区，使用缓冲区，然后在完成工作后将其返回给缓冲池。</span><span class="sxs-lookup"><span data-stu-id="1f425-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="1f425-129">这样就避免了创建和销毁缓冲区的系统开销。</span><span class="sxs-lookup"><span data-stu-id="1f425-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="1f425-130">一个正整数，指定内存中用于存储消息的缓冲区的最大大小（字节）。</span><span class="sxs-lookup"><span data-stu-id="1f425-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="1f425-131">如果 `transferMode` 属性等于 `Buffered`，则此属性应等于 `maxReceivedMessageSize` 属性值。</span><span class="sxs-lookup"><span data-stu-id="1f425-131">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="1f425-132">如果 `transferMode` 属性等于 `Streamed`，则此属性不能大于 `maxReceivedMessageSize` 属性值，应当至少为标头的大小。</span><span class="sxs-lookup"><span data-stu-id="1f425-132">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="1f425-133">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="1f425-133">The default is 65536.</span></span> <span data-ttu-id="1f425-134">有关详细信息，请参阅 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>。</span><span class="sxs-lookup"><span data-stu-id="1f425-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="1f425-135">一个整数，指定服务将创建/接受的最大出站和入站连接数。</span><span class="sxs-lookup"><span data-stu-id="1f425-135">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="1f425-136">传入和传出连接分别根据此属性指定的限制进行计数。</span><span class="sxs-lookup"><span data-stu-id="1f425-136">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="1f425-137">超出此限制的入站连接需要排队，直到连接数低于限制值。</span><span class="sxs-lookup"><span data-stu-id="1f425-137">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="1f425-138">超出此限制的出站连接需要排队，直到连接数低于限制值。</span><span class="sxs-lookup"><span data-stu-id="1f425-138">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="1f425-139">默认值为 10。</span><span class="sxs-lookup"><span data-stu-id="1f425-139">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="1f425-140">一个正整数，指定采用此绑定配置的通道上可以接收的最大消息大小（字节），包括消息头。</span><span class="sxs-lookup"><span data-stu-id="1f425-140">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="1f425-141">如果消息超出此限制，则发送方将收到 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="1f425-141">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="1f425-142">接收方将删除该消息，并在跟踪日志中创建事件项。</span><span class="sxs-lookup"><span data-stu-id="1f425-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="1f425-143">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="1f425-143">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="1f425-144">一个包含绑定的配置名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="1f425-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="1f425-145">因为此值用作绑定的标识，所以它应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="1f425-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="1f425-146">从 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 开始，不要求绑定和行为具有名称。</span><span class="sxs-lookup"><span data-stu-id="1f425-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="1f425-147">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="1f425-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="1f425-148">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1f425-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="1f425-149">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1f425-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1f425-150">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1f425-150">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="1f425-151">一个布尔值，指定是否为此连接启用 TCP 端口共享。</span><span class="sxs-lookup"><span data-stu-id="1f425-151">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="1f425-152">如果此值为 `false`，则每个绑定都使用自己的独占端口。</span><span class="sxs-lookup"><span data-stu-id="1f425-152">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="1f425-153">此设置只与服务相关，因为客户端不受影响。</span><span class="sxs-lookup"><span data-stu-id="1f425-153">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="1f425-154">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1f425-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="1f425-155">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1f425-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1f425-156">默认值为 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="1f425-156">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="1f425-157">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="1f425-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="1f425-158">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="1f425-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="1f425-159">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="1f425-159">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="1f425-160">一个布尔值，指定绑定是否支持流动 WS-Transactions。</span><span class="sxs-lookup"><span data-stu-id="1f425-160">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="1f425-161">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="1f425-161">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="1f425-162">指定与此绑定一起使用的事务处理协议。</span><span class="sxs-lookup"><span data-stu-id="1f425-162">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="1f425-163">有效值为</span><span class="sxs-lookup"><span data-stu-id="1f425-163">Valid values are</span></span><br /><br /> <span data-ttu-id="1f425-164">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="1f425-164">-   OleTransactions</span></span><br /><span data-ttu-id="1f425-165">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="1f425-165">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="1f425-166">默认值为 OleTransactions。</span><span class="sxs-lookup"><span data-stu-id="1f425-166">The default is OleTransactions.</span></span> <span data-ttu-id="1f425-167">此属性的类型为 <xref:System.ServiceModel.TransactionProtocol>。</span><span class="sxs-lookup"><span data-stu-id="1f425-167">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="1f425-168">一个 <xref:System.ServiceModel.TransferMode> 值，指定为请求或响应对消息进行缓冲处理还是流式处理。</span><span class="sxs-lookup"><span data-stu-id="1f425-168">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f425-169">子元素</span><span class="sxs-lookup"><span data-stu-id="1f425-169">Child elements</span></span>  
  
|<span data-ttu-id="1f425-170">元素</span><span class="sxs-lookup"><span data-stu-id="1f425-170">Element</span></span>|<span data-ttu-id="1f425-171">描述</span><span class="sxs-lookup"><span data-stu-id="1f425-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f425-172">\<security></span><span class="sxs-lookup"><span data-stu-id="1f425-172">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="1f425-173">定义绑定的安全设置。</span><span class="sxs-lookup"><span data-stu-id="1f425-173">Defines the security settings for the binding.</span></span> <span data-ttu-id="1f425-174">此元素的类型为 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="1f425-174">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|<span data-ttu-id="1f425-175">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1f425-175">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="1f425-176">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="1f425-176">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="1f425-177">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="1f425-177">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="1f425-178">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1f425-178">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="1f425-179">指定是否在通道终结点之间建立可靠会话。</span><span class="sxs-lookup"><span data-stu-id="1f425-179">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f425-180">父元素</span><span class="sxs-lookup"><span data-stu-id="1f425-180">Parent elements</span></span>  
  
|<span data-ttu-id="1f425-181">元素</span><span class="sxs-lookup"><span data-stu-id="1f425-181">Element</span></span>|<span data-ttu-id="1f425-182">描述</span><span class="sxs-lookup"><span data-stu-id="1f425-182">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f425-183">\<bindings></span><span class="sxs-lookup"><span data-stu-id="1f425-183">\<bindings></span></span>](bindings.md)|<span data-ttu-id="1f425-184">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="1f425-184">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f425-185">备注</span><span class="sxs-lookup"><span data-stu-id="1f425-185">Remarks</span></span>

<span data-ttu-id="1f425-186">默认情况下，此绑定会生成一个运行时通信堆栈，该堆栈使用传输安全、用于消息传递的 TCP 和二进制消息编码机制。</span><span class="sxs-lookup"><span data-stu-id="1f425-186">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="1f425-187">此绑定是适当的 Windows Communication Foundation （WCF）系统提供的选择，用于通过 Intranet 进行通信。</span><span class="sxs-lookup"><span data-stu-id="1f425-187">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="1f425-188">的`netTcpBinding`默认配置比提供`wsHttpBinding`的配置更快，但它仅适用于 WCF 通信。</span><span class="sxs-lookup"><span data-stu-id="1f425-188">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="1f425-189">可以使用可选的 `securityMode` 属性配置安全行为。</span><span class="sxs-lookup"><span data-stu-id="1f425-189">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="1f425-190">使用可选的 `reliableSessionEnabled` 属性可以配置 WS-ReliableMessaging 的用法。</span><span class="sxs-lookup"><span data-stu-id="1f425-190">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="1f425-191">但是在默认情况下可靠消息传递为关闭状态。</span><span class="sxs-lookup"><span data-stu-id="1f425-191">But reliable messaging is off by default.</span></span> <span data-ttu-id="1f425-192">一般来说，HTTP 系统提供的绑定（如 `wsHttpBinding` 和 `basicHttpBinding`）是默认配置为打开事项，而 `netTcpBinding` 绑定是默认配置为关闭事项，因此，你必须选择性加入所需事项才能获取支持，例如获取对一种 WS-\* 规范的支持。</span><span class="sxs-lookup"><span data-stu-id="1f425-192">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="1f425-193">这意味着在终结点之间交换消息时，TCP 的默认配置比 HTTP 绑定的默认配置更快。</span><span class="sxs-lookup"><span data-stu-id="1f425-193">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f425-194">示例</span><span class="sxs-lookup"><span data-stu-id="1f425-194">Example</span></span>

<span data-ttu-id="1f425-195">绑定是在客户端和服务的配置文件中指定的。</span><span class="sxs-lookup"><span data-stu-id="1f425-195">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="1f425-196">绑定类型是在 `binding` 元素的 `<endpoint>` 属性中指定的。</span><span class="sxs-lookup"><span data-stu-id="1f425-196">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="1f425-197">如果要配置 netTcpBinding 绑定并更改它的一些设置，则必须定义绑定配置。</span><span class="sxs-lookup"><span data-stu-id="1f425-197">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="1f425-198">终结点必须使用 `bindingConfiguration` 特性来引用绑定配置。</span><span class="sxs-lookup"><span data-stu-id="1f425-198">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="1f425-199">在下面的示例中，定义了一个绑定配置。</span><span class="sxs-lookup"><span data-stu-id="1f425-199">In the following example, a binding configuration is defined.</span></span>  
  
```xml  
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
    <endpoint address=""
              binding="netTcpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
    ...
  </service>
</services>
<bindings>
  <netTcpBinding>
    <binding closeTimeout="00:01:00"
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"
                       enabled="false" />
      <security mode="Transport">
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />
      </security>
    </binding>
  </netTcpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="1f425-200">请参阅</span><span class="sxs-lookup"><span data-stu-id="1f425-200">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [<span data-ttu-id="1f425-201">绑定</span><span class="sxs-lookup"><span data-stu-id="1f425-201">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1f425-202">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="1f425-202">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1f425-203">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="1f425-203">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1f425-204">\<binding></span><span class="sxs-lookup"><span data-stu-id="1f425-204">\<binding></span></span>](../../../misc/binding.md)
