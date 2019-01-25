---
title: '&lt;ws2007FederationHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
ms.openlocfilehash: 7869737f1e3d8c7a9ba569991ead6f7f759e6c58
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616883"
---
# <a name="ltws2007federationhttpbindinggt"></a><span data-ttu-id="de040-102">&lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="de040-102">&lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="de040-103">安全且可互操作的绑定，它派生[ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)并支持联合的安全。</span><span class="sxs-lookup"><span data-stu-id="de040-103">A secure and interoperable binding that derives from [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) and supports federated security.</span></span>  
  
 <span data-ttu-id="de040-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="de040-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="de040-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="de040-105">\<bindings></span></span>  
<span data-ttu-id="de040-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="de040-106">\<ws2007FederationHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de040-107">语法</span><span class="sxs-lookup"><span data-stu-id="de040-107">Syntax</span></span>  
  
```xml  
<ws2007FederationHttpBinding>
  <binding bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
           maxBufferPoolSize="integer"
           maxReceivedMessageSize="integer"
           messageEncoding="Text/Mtom"
           name="string"
           openTimeout="TimeSpan"
           privacyNoticeAt="Uri"
           privacyNoticeVersion="Integer"
           proxyAddress="Uri"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transactionFlow="Boolean"
           useDefaultWebProxy="Boolean">
    <security mode="None/Message/TransportWithMessageCredential">
      <message negotiateServiceCredential="Boolean"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey">
      </message>
    </security>
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</ws2007FederationHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de040-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="de040-108">Attributes and Elements</span></span>  
 <span data-ttu-id="de040-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="de040-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de040-110">特性</span><span class="sxs-lookup"><span data-stu-id="de040-110">Attributes</span></span>  
  
|<span data-ttu-id="de040-111">特性</span><span class="sxs-lookup"><span data-stu-id="de040-111">Attribute</span></span>|<span data-ttu-id="de040-112">描述</span><span class="sxs-lookup"><span data-stu-id="de040-112">Description</span></span>|  
|---------------|-----------------|  
|`bypassProxyOnLocal`|<span data-ttu-id="de040-113">一个值，指示是否对本地地址不使用代理服务器。</span><span class="sxs-lookup"><span data-stu-id="de040-113">A value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="de040-114">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="de040-114">The default is `false`.</span></span>|  
|`closeTimeout`|<span data-ttu-id="de040-115">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="de040-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="de040-116">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="de040-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="de040-117">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="de040-117">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="de040-118">指定用于分析 URI 的 HTTP 主机名比较模式。</span><span class="sxs-lookup"><span data-stu-id="de040-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="de040-119">此属性的类型为 <xref:System.ServiceModel.HostNameComparisonMode>，指示在对 URI 进行匹配时，是否使用主机名来访问服务。</span><span class="sxs-lookup"><span data-stu-id="de040-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="de040-120">默认值为 <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>，表示忽略匹配项中的主机名。</span><span class="sxs-lookup"><span data-stu-id="de040-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="de040-121">此绑定的最大缓冲池大小。</span><span class="sxs-lookup"><span data-stu-id="de040-121">The maximum buffer pool size for this binding.</span></span> <span data-ttu-id="de040-122">默认值为 524,288 字节 (512 \* 1024)。</span><span class="sxs-lookup"><span data-stu-id="de040-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="de040-123">Windows Communication Foundation (WCF) 的许多部件使用缓冲区。</span><span class="sxs-lookup"><span data-stu-id="de040-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="de040-124">每次使用缓冲区时，创建和销毁它们都将占用大量资源，而缓冲区的垃圾回收过程也是如此。</span><span class="sxs-lookup"><span data-stu-id="de040-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="de040-125">利用缓冲池，可以从缓冲池中获得缓冲区，使用缓冲区，然后在完成工作后将其返回给缓冲池。</span><span class="sxs-lookup"><span data-stu-id="de040-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="de040-126">这样就避免了创建和销毁缓冲区的系统开销。</span><span class="sxs-lookup"><span data-stu-id="de040-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="de040-127">在采用此绑定配置的通道上可以接收的最大消息大小（包括标头），单位为字节。</span><span class="sxs-lookup"><span data-stu-id="de040-127">The maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="de040-128">如果消息超出此限制，则发送方将收到 SOAP 错误。</span><span class="sxs-lookup"><span data-stu-id="de040-128">The sender of a message that exceeds this limit receives a SOAP fault.</span></span> <span data-ttu-id="de040-129">接收方将删除该消息，并在跟踪日志中创建事件项。</span><span class="sxs-lookup"><span data-stu-id="de040-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="de040-130">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="de040-130">The default is 65536.</span></span>|  
|`messageEncoding`|<span data-ttu-id="de040-131">定义用于对消息进行编码的编码器。</span><span class="sxs-lookup"><span data-stu-id="de040-131">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="de040-132">包括以下有效值：</span><span class="sxs-lookup"><span data-stu-id="de040-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="de040-133">-文本：使用文本消息编码器。</span><span class="sxs-lookup"><span data-stu-id="de040-133">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="de040-134">Mtom:使用消息传输组织机制 1.0 (MTOM) 编码器。</span><span class="sxs-lookup"><span data-stu-id="de040-134">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="de040-135">默认值为 Text。</span><span class="sxs-lookup"><span data-stu-id="de040-135">The default is Text.</span></span><br /><br /> <span data-ttu-id="de040-136">此属性的类型为 <xref:System.ServiceModel.WSMessageEncoding>。</span><span class="sxs-lookup"><span data-stu-id="de040-136">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="de040-137">绑定的配置名称。</span><span class="sxs-lookup"><span data-stu-id="de040-137">The configuration name of the binding.</span></span> <span data-ttu-id="de040-138">因为此值用作绑定的标识，所以它应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="de040-138">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="de040-139">从 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 开始，不要求绑定和行为具有名称。</span><span class="sxs-lookup"><span data-stu-id="de040-139">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="de040-140">有关默认配置以及无名称绑定和行为的详细信息，请参阅[Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)并[WCF 服务的简化配置](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="de040-140">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="de040-141">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="de040-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="de040-142">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="de040-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="de040-143">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="de040-143">The default is 00:01:00.</span></span>|  
|`privactyNoticeAt`|<span data-ttu-id="de040-144">隐私声明所在的 URI。</span><span class="sxs-lookup"><span data-stu-id="de040-144">A URI at which the privacy notice is located.</span></span>|  
|`privactyNoticeVersion`|<span data-ttu-id="de040-145">当前隐私声明的版本。</span><span class="sxs-lookup"><span data-stu-id="de040-145">The version of the current privacy notice.</span></span>|  
|`proxyAddress`|<span data-ttu-id="de040-146">一个指定 HTTP 代理的地址的 URI。</span><span class="sxs-lookup"><span data-stu-id="de040-146">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="de040-147">如果 `useDefaultWebProxy` 为 `true`，则此设置必须为 `null`。</span><span class="sxs-lookup"><span data-stu-id="de040-147">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="de040-148">默认值为 `null`。</span><span class="sxs-lookup"><span data-stu-id="de040-148">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="de040-149">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="de040-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="de040-150">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="de040-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="de040-151">默认值为 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="de040-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="de040-152">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="de040-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="de040-153">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="de040-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="de040-154">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="de040-154">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="de040-155">设置要用来在绑定上发出消息的字符集编码。</span><span class="sxs-lookup"><span data-stu-id="de040-155">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="de040-156">包括以下有效值：</span><span class="sxs-lookup"><span data-stu-id="de040-156">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="de040-157">-BigEndianUnicode:Unicode Big Endian 编码。</span><span class="sxs-lookup"><span data-stu-id="de040-157">-   BigEndianUnicode: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="de040-158">Unicode:16 位编码。</span><span class="sxs-lookup"><span data-stu-id="de040-158">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="de040-159">-UTF8:8 位编码。</span><span class="sxs-lookup"><span data-stu-id="de040-159">-   UTF8: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="de040-160">默认值为 UTF8。</span><span class="sxs-lookup"><span data-stu-id="de040-160">The default is UTF8.</span></span> <span data-ttu-id="de040-161">此属性的类型为 <xref:System.Text.Encoding>。</span><span class="sxs-lookup"><span data-stu-id="de040-161">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transactionFlow`|<span data-ttu-id="de040-162">一个值，指定绑定是否支持流动 WS-Transactions。</span><span class="sxs-lookup"><span data-stu-id="de040-162">A value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="de040-163">默认值为 `false`。</span><span class="sxs-lookup"><span data-stu-id="de040-163">The default is `false`.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="de040-164">一个值，指示是否使用系统的自动配置 HTTP 代理。</span><span class="sxs-lookup"><span data-stu-id="de040-164">A value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="de040-165">如果此属性为 `null`，则代理地址必须为 `true`（即，不设置代理地址）。</span><span class="sxs-lookup"><span data-stu-id="de040-165">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="de040-166">默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="de040-166">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de040-167">子元素</span><span class="sxs-lookup"><span data-stu-id="de040-167">Child Elements</span></span>  
  
|<span data-ttu-id="de040-168">元素</span><span class="sxs-lookup"><span data-stu-id="de040-168">Element</span></span>|<span data-ttu-id="de040-169">描述</span><span class="sxs-lookup"><span data-stu-id="de040-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de040-170">\<security></span><span class="sxs-lookup"><span data-stu-id="de040-170">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="de040-171">定义消息的安全设置。</span><span class="sxs-lookup"><span data-stu-id="de040-171">Defines the security settings for the message.</span></span> <span data-ttu-id="de040-172">此元素的类型为 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="de040-172">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="de040-173">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="de040-173">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="de040-174">定义可由采用此绑定配置的终结点进行处理的 SOAP 消息的复杂性约束。</span><span class="sxs-lookup"><span data-stu-id="de040-174">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="de040-175">此元素的类型为 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>。</span><span class="sxs-lookup"><span data-stu-id="de040-175">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="de040-176">reliableSession</span><span class="sxs-lookup"><span data-stu-id="de040-176">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="de040-177">指定是否在通道终结点之间建立可靠会话。</span><span class="sxs-lookup"><span data-stu-id="de040-177">Specifies whether reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="de040-178">父元素</span><span class="sxs-lookup"><span data-stu-id="de040-178">Parent Elements</span></span>  
  
|<span data-ttu-id="de040-179">元素</span><span class="sxs-lookup"><span data-stu-id="de040-179">Element</span></span>|<span data-ttu-id="de040-180">描述</span><span class="sxs-lookup"><span data-stu-id="de040-180">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="de040-181">\<bindings></span><span class="sxs-lookup"><span data-stu-id="de040-181">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="de040-182">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="de040-182">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de040-183">备注</span><span class="sxs-lookup"><span data-stu-id="de040-183">Remarks</span></span>  
 <span data-ttu-id="de040-184">联合是一种可以在多个企业或信任域通过共享标识进行身份验证和授权的功能。</span><span class="sxs-lookup"><span data-stu-id="de040-184">Federation is the ability to share identities across multiple enterprises or trust domains for authentication and authorization.</span></span> <span data-ttu-id="de040-185">它使用 WS-Trust 协议将标识的表示形式从一个信任域映射到另一个信任域。</span><span class="sxs-lookup"><span data-stu-id="de040-185">It uses the WS-Trust protocol to map the identity representation from one trust domain to another.</span></span> <span data-ttu-id="de040-186">联合 HTTP 绑定支持 SOAP 安全以及混合模式安全，但不支持传输安全。</span><span class="sxs-lookup"><span data-stu-id="de040-186">Federated HTTP binding supports SOAP security as well as mixed-mode security, but it does not support transport security.</span></span> <span data-ttu-id="de040-187">配置了此绑定的服务必须使用 HTTP 传输。</span><span class="sxs-lookup"><span data-stu-id="de040-187">Services configured with this binding must use the HTTP transport.</span></span> <span data-ttu-id="de040-188">有关详细信息，请参阅[ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="de040-188">For more information, see [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="de040-189">示例</span><span class="sxs-lookup"><span data-stu-id="de040-189">Example</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <ws2007FederationHttpBinding>
        <binding bypassProxyOnLocal="false"
                 transactionFlow="false"
                 hostNameComparisonMode="WeakWildcard"
                 maxReceivedMessageSize="1000"
                 messageEncoding="Mtom"
                 proxyAddress="http://www.contoso.com"
                 textEncoding="Utf16TextEncoding"
                 useDefaultWebProxy="false">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="None">
            <message negotiateServiceCredential="false"
                     algorithmSuite="Aes128"
                     issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"
                     issuedKeyType="PublicKey">
              <issuer address="http://localhost/Sts" />
            </message>
          </security>
        </binding>
      </ws2007FederationBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="de040-190">请参阅</span><span class="sxs-lookup"><span data-stu-id="de040-190">See also</span></span>
- <xref:System.ServiceModel.WS2007FederationHttpBinding>
- <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>
- [<span data-ttu-id="de040-191">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="de040-191">\<wsFederationHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)
- [<span data-ttu-id="de040-192">绑定</span><span class="sxs-lookup"><span data-stu-id="de040-192">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="de040-193">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="de040-193">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="de040-194">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="de040-194">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="de040-195">\<binding></span><span class="sxs-lookup"><span data-stu-id="de040-195">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
