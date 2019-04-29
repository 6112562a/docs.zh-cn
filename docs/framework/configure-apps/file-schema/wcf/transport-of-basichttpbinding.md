---
title: <transport> 的 <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: 5d1ef059f8fde7c41e333571d1c025a9c0c7e03f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788383"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="870c2-102">\<transport> of \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="870c2-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="870c2-103">为 HTTP 传输定义控制身份验证参数的属性。</span><span class="sxs-lookup"><span data-stu-id="870c2-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
 <span data-ttu-id="870c2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="870c2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="870c2-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="870c2-105">\<bindings></span></span>  
<span data-ttu-id="870c2-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="870c2-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="870c2-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="870c2-107">\<binding></span></span>  
<span data-ttu-id="870c2-108">\<安全 ></span><span class="sxs-lookup"><span data-stu-id="870c2-108">\<security></span></span>  
<span data-ttu-id="870c2-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="870c2-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="870c2-110">语法</span><span class="sxs-lookup"><span data-stu-id="870c2-110">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="870c2-111">特性和元素</span><span class="sxs-lookup"><span data-stu-id="870c2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="870c2-112">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="870c2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="870c2-113">特性</span><span class="sxs-lookup"><span data-stu-id="870c2-113">Attributes</span></span>  
  
|<span data-ttu-id="870c2-114">特性</span><span class="sxs-lookup"><span data-stu-id="870c2-114">Attribute</span></span>|<span data-ttu-id="870c2-115">描述</span><span class="sxs-lookup"><span data-stu-id="870c2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="870c2-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="870c2-116">clientCredentialType</span></span>|<span data-ttu-id="870c2-117">-指定要执行使用 HTTP 身份验证的客户端身份验证时要使用的凭据类型。</span><span class="sxs-lookup"><span data-stu-id="870c2-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="870c2-118">默认值为 `None`。</span><span class="sxs-lookup"><span data-stu-id="870c2-118">The default is `None`.</span></span> <span data-ttu-id="870c2-119">此属性的类型为 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="870c2-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="870c2-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="870c2-120">proxyCredentialType</span></span>|<span data-ttu-id="870c2-121">-指定要执行从使用 HTTP 上的代理服务器在域中的客户端身份验证时要使用的凭据类型。</span><span class="sxs-lookup"><span data-stu-id="870c2-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="870c2-122">只有当父 `mode` 元素的 `security` 属性为 `Transport` 或 `TransportCredentialsOnly` 时，此属性才适用。</span><span class="sxs-lookup"><span data-stu-id="870c2-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="870c2-123">此属性的类型为 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="870c2-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="870c2-124">realm</span><span class="sxs-lookup"><span data-stu-id="870c2-124">realm</span></span>|<span data-ttu-id="870c2-125">一个字符串，指定摘要式或基本身份验证的 HTTP 身份验证方案所使用的领域。</span><span class="sxs-lookup"><span data-stu-id="870c2-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="870c2-126">默认值为一个空字符串。</span><span class="sxs-lookup"><span data-stu-id="870c2-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="870c2-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="870c2-127">policyEnforcement</span></span>|<span data-ttu-id="870c2-128">此枚举指定应何时强制实施 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>。</span><span class="sxs-lookup"><span data-stu-id="870c2-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="870c2-129">1.Never – 绝不强制实施此策略（禁用扩展保护）。</span><span class="sxs-lookup"><span data-stu-id="870c2-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="870c2-130">2.WhenSupported – 仅在客户端支持扩展保护时才强制实施此策略。</span><span class="sxs-lookup"><span data-stu-id="870c2-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="870c2-131">3.Always – 总是强制实施此策略。</span><span class="sxs-lookup"><span data-stu-id="870c2-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="870c2-132">不支持扩展保护的客户端将无法进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="870c2-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="870c2-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="870c2-133">protectionScenario</span></span>|<span data-ttu-id="870c2-134">此枚举指定此策略强制实施的保护方案。</span><span class="sxs-lookup"><span data-stu-id="870c2-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="870c2-135">clientCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="870c2-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="870c2-136">“值”</span><span class="sxs-lookup"><span data-stu-id="870c2-136">Value</span></span>|<span data-ttu-id="870c2-137">描述</span><span class="sxs-lookup"><span data-stu-id="870c2-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="870c2-138">None</span><span class="sxs-lookup"><span data-stu-id="870c2-138">None</span></span>|<span data-ttu-id="870c2-139">在传输过程中不能保证消息的安全。</span><span class="sxs-lookup"><span data-stu-id="870c2-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="870c2-140">Basic</span><span class="sxs-lookup"><span data-stu-id="870c2-140">Basic</span></span>|<span data-ttu-id="870c2-141">指定基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="870c2-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="870c2-142">摘要</span><span class="sxs-lookup"><span data-stu-id="870c2-142">Digest</span></span>|<span data-ttu-id="870c2-143">指定摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="870c2-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="870c2-144">Ntlm</span><span class="sxs-lookup"><span data-stu-id="870c2-144">Ntlm</span></span>|<span data-ttu-id="870c2-145">指定 NTLM 身份验证（如果可能且 Windows 身份验证失败）。</span><span class="sxs-lookup"><span data-stu-id="870c2-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="870c2-146">Windows</span><span class="sxs-lookup"><span data-stu-id="870c2-146">Windows</span></span>|<span data-ttu-id="870c2-147">指定 Windows 集成身份验证。</span><span class="sxs-lookup"><span data-stu-id="870c2-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="870c2-148">proxyCredentialType 属性</span><span class="sxs-lookup"><span data-stu-id="870c2-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="870c2-149">“值”</span><span class="sxs-lookup"><span data-stu-id="870c2-149">Value</span></span>|<span data-ttu-id="870c2-150">描述</span><span class="sxs-lookup"><span data-stu-id="870c2-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="870c2-151">None</span><span class="sxs-lookup"><span data-stu-id="870c2-151">None</span></span>|<span data-ttu-id="870c2-152">的在传输过程中不是安全消息数。</span><span class="sxs-lookup"><span data-stu-id="870c2-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="870c2-153">Basic</span><span class="sxs-lookup"><span data-stu-id="870c2-153">Basic</span></span>|<span data-ttu-id="870c2-154">指定基本身份验证定义的 RFC 2617 – HTTP 身份验证：基本和摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="870c2-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="870c2-155">摘要</span><span class="sxs-lookup"><span data-stu-id="870c2-155">Digest</span></span>|<span data-ttu-id="870c2-156">指定摘要式身份验证定义的 RFC 2617 – HTTP 身份验证：基本和摘要式身份验证。</span><span class="sxs-lookup"><span data-stu-id="870c2-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="870c2-157">Ntlm</span><span class="sxs-lookup"><span data-stu-id="870c2-157">Ntlm</span></span>|<span data-ttu-id="870c2-158">指定 NTLM 身份验证（如果可能且 Windows 身份验证失败）。</span><span class="sxs-lookup"><span data-stu-id="870c2-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="870c2-159">Windows</span><span class="sxs-lookup"><span data-stu-id="870c2-159">Windows</span></span>|<span data-ttu-id="870c2-160">指定 Windows 集成身份验证。</span><span class="sxs-lookup"><span data-stu-id="870c2-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="870c2-161">证书</span><span class="sxs-lookup"><span data-stu-id="870c2-161">Certificate</span></span>|<span data-ttu-id="870c2-162">使用证书执行客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="870c2-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="870c2-163">此选项只在父 `Mode` 元素的 `security` 属性设置为“Transport”时才起作用，如果该属性设置为“TransportCredentialOnly”，则此选项将不起作用。</span><span class="sxs-lookup"><span data-stu-id="870c2-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="870c2-164">子元素</span><span class="sxs-lookup"><span data-stu-id="870c2-164">Child Elements</span></span>  
 <span data-ttu-id="870c2-165">None</span><span class="sxs-lookup"><span data-stu-id="870c2-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="870c2-166">父元素</span><span class="sxs-lookup"><span data-stu-id="870c2-166">Parent Elements</span></span>  
  
|<span data-ttu-id="870c2-167">元素</span><span class="sxs-lookup"><span data-stu-id="870c2-167">Element</span></span>|<span data-ttu-id="870c2-168">描述</span><span class="sxs-lookup"><span data-stu-id="870c2-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="870c2-169">\<security></span><span class="sxs-lookup"><span data-stu-id="870c2-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="870c2-170">定义的安全功能[ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="870c2-170">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="870c2-171">示例</span><span class="sxs-lookup"><span data-stu-id="870c2-171">Example</span></span>  
 <span data-ttu-id="870c2-172">下面的示例演示如何对基本绑定使用 SSL 传输安全。</span><span class="sxs-lookup"><span data-stu-id="870c2-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="870c2-173">默认情况下，基本绑定支持 HTTP 通信。</span><span class="sxs-lookup"><span data-stu-id="870c2-173">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="870c2-174">请参阅</span><span class="sxs-lookup"><span data-stu-id="870c2-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="870c2-175">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="870c2-175">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="870c2-176">绑定</span><span class="sxs-lookup"><span data-stu-id="870c2-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="870c2-177">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="870c2-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="870c2-178">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="870c2-178">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="870c2-179">\<binding></span><span class="sxs-lookup"><span data-stu-id="870c2-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
