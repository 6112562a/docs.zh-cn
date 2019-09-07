---
title: <security> 的 <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: ab5969da6a2d7cb59c057fd5bb909add6b6398a4
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399784"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="45ff8-102">\<ws2007HttpBinding 的\<安全 > ></span><span class="sxs-lookup"><span data-stu-id="45ff8-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="45ff8-103">表示与[ \<ws2007HttpBinding >](ws2007httpbinding.md)元素一起使用的安全设置。</span><span class="sxs-lookup"><span data-stu-id="45ff8-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
<span data-ttu-id="45ff8-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="45ff8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="45ff8-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="45ff8-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="45ff8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<绑定 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="45ff8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="45ff8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="45ff8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="45ff8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<绑定 >** </span><span class="sxs-lookup"><span data-stu-id="45ff8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="45ff8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全 >**</span><span class="sxs-lookup"><span data-stu-id="45ff8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45ff8-110">语法</span><span class="sxs-lookup"><span data-stu-id="45ff8-110">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45ff8-111">特性和元素</span><span class="sxs-lookup"><span data-stu-id="45ff8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="45ff8-112">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="45ff8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45ff8-113">特性</span><span class="sxs-lookup"><span data-stu-id="45ff8-113">Attributes</span></span>  
  
|<span data-ttu-id="45ff8-114">特性</span><span class="sxs-lookup"><span data-stu-id="45ff8-114">Attribute</span></span>|<span data-ttu-id="45ff8-115">描述</span><span class="sxs-lookup"><span data-stu-id="45ff8-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="45ff8-116">可有可无.</span><span class="sxs-lookup"><span data-stu-id="45ff8-116">-   Optional.</span></span> <span data-ttu-id="45ff8-117">指定所应用的安全类型。</span><span class="sxs-lookup"><span data-stu-id="45ff8-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="45ff8-118">默认值为 `Message`。</span><span class="sxs-lookup"><span data-stu-id="45ff8-118">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="45ff8-119">此属性的类型为 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="45ff8-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="45ff8-120">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="45ff8-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="45ff8-121">值</span><span class="sxs-lookup"><span data-stu-id="45ff8-121">Value</span></span>|<span data-ttu-id="45ff8-122">描述</span><span class="sxs-lookup"><span data-stu-id="45ff8-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="45ff8-123">禁用安全性。</span><span class="sxs-lookup"><span data-stu-id="45ff8-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="45ff8-124">使用 HTTPS 提供安全性。</span><span class="sxs-lookup"><span data-stu-id="45ff8-124">Security is provided using HTTPS.</span></span> <span data-ttu-id="45ff8-125">此服务必须使用安全套接字层 (SSL) 证书进行配置。</span><span class="sxs-lookup"><span data-stu-id="45ff8-125">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="45ff8-126">消息使用 HTTPS 获得全面保护，而且客户端使用服务的 SSL 证书对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="45ff8-126">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="45ff8-127">客户端身份验证通过`ClientCredentials` [ \<传输 >](transport-of-ws2007httpbinding.md)元素的属性进行控制。</span><span class="sxs-lookup"><span data-stu-id="45ff8-127">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="45ff8-128">使用 SOAP 消息安全提供安全性。</span><span class="sxs-lookup"><span data-stu-id="45ff8-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="45ff8-129">默认情况下，将对 SOAP 正文进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="45ff8-129">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="45ff8-130">此模式提供了各种各样的功能，例如服务凭据在带外客户端是否可用、要使用的算法套件以及通过 <xref:System.ServiceModel.Security.SecurityMessageProperty> 要应用于消息正文的保护级别。</span><span class="sxs-lookup"><span data-stu-id="45ff8-130">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="45ff8-131">每个会话将执行一次客户端身份验证，身份验证的结果在会话过程中将进行缓存。</span><span class="sxs-lookup"><span data-stu-id="45ff8-131">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="45ff8-132">在此模式下，HTTPS 将提供完整性、保密性和服务器身份验证，SOAP 消息安全将提供客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="45ff8-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="45ff8-133">默认情况下，每个会话将执行一次客户端身份验证，身份验证的结果在会话过程中将进行缓存。</span><span class="sxs-lookup"><span data-stu-id="45ff8-133">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45ff8-134">子元素</span><span class="sxs-lookup"><span data-stu-id="45ff8-134">Child Elements</span></span>  
  
|<span data-ttu-id="45ff8-135">元素</span><span class="sxs-lookup"><span data-stu-id="45ff8-135">Element</span></span>|<span data-ttu-id="45ff8-136">描述</span><span class="sxs-lookup"><span data-stu-id="45ff8-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45ff8-137">\<transport></span><span class="sxs-lookup"><span data-stu-id="45ff8-137">\<transport></span></span>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="45ff8-138">定义传输安全设置。</span><span class="sxs-lookup"><span data-stu-id="45ff8-138">Defines the transport security settings.</span></span> <span data-ttu-id="45ff8-139">此元素与 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 类型相对应。</span><span class="sxs-lookup"><span data-stu-id="45ff8-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="45ff8-140">仅在将模式设置为“Transport”时才应用这些设置。</span><span class="sxs-lookup"><span data-stu-id="45ff8-140">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="45ff8-141">\<message></span><span class="sxs-lookup"><span data-stu-id="45ff8-141">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="45ff8-142">定义消息的安全设置。</span><span class="sxs-lookup"><span data-stu-id="45ff8-142">Defines the security settings for the message.</span></span> <span data-ttu-id="45ff8-143">此元素与 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 类型相对应。</span><span class="sxs-lookup"><span data-stu-id="45ff8-143">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="45ff8-144">将模式设置为“Transport”时，不应用这些设置。</span><span class="sxs-lookup"><span data-stu-id="45ff8-144">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="45ff8-145">父元素</span><span class="sxs-lookup"><span data-stu-id="45ff8-145">Parent Elements</span></span>  
  
|<span data-ttu-id="45ff8-146">元素</span><span class="sxs-lookup"><span data-stu-id="45ff8-146">Element</span></span>|<span data-ttu-id="45ff8-147">描述</span><span class="sxs-lookup"><span data-stu-id="45ff8-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45ff8-148">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="45ff8-148">\<ws2007HttpBinding></span></span>](ws2007httpbinding.md)|<span data-ttu-id="45ff8-149">HTTP 传输应用程序的安全绑定。</span><span class="sxs-lookup"><span data-stu-id="45ff8-149">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45ff8-150">备注</span><span class="sxs-lookup"><span data-stu-id="45ff8-150">Remarks</span></span>  
 <span data-ttu-id="45ff8-151">此元素专用于与实现 WS-\* 规范的服务进行互操作。</span><span class="sxs-lookup"><span data-stu-id="45ff8-151">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="45ff8-152">此绑定的传输安全为 HTTP 上的安全套接字层 (SSL)，即 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="45ff8-152">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45ff8-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="45ff8-153">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="45ff8-154">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="45ff8-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="45ff8-155">绑定</span><span class="sxs-lookup"><span data-stu-id="45ff8-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="45ff8-156">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="45ff8-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="45ff8-157">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="45ff8-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="45ff8-158">\<binding></span><span class="sxs-lookup"><span data-stu-id="45ff8-158">\<binding></span></span>](../../../misc/binding.md)
