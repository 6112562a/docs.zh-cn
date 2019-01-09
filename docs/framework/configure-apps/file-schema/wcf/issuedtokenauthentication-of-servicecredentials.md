---
title: '&lt;serviceCredentials&gt; 的 &lt;issuedTokenAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: 5c2e288f-f603-4d13-839a-0fd6d1981bec
ms.openlocfilehash: 43f03ad32345195324c9ba2a3977d294a7a2b789
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151483"
---
# <a name="ltissuedtokenauthenticationgt-of-ltservicecredentialsgt"></a><span data-ttu-id="cd422-102">&lt;serviceCredentials&gt; 的 &lt;issuedTokenAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="cd422-102">&lt;issuedTokenAuthentication&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="cd422-103">指定作为服务凭据颁发的自定义令牌。</span><span class="sxs-lookup"><span data-stu-id="cd422-103">Specifies a custom token issued as a service credential.</span></span>  
  
 <span data-ttu-id="cd422-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cd422-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cd422-105">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="cd422-105">\<behaviors></span></span>  
<span data-ttu-id="cd422-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="cd422-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="cd422-107">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="cd422-107">\<behavior></span></span>  
<span data-ttu-id="cd422-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="cd422-108">\<serviceCredentials></span></span>  
<span data-ttu-id="cd422-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="cd422-109">\<issuedTokenAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd422-110">语法</span><span class="sxs-lookup"><span data-stu-id="cd422-110">Syntax</span></span>  
  
```xml  
<issuedTokenAuthentication allowUntrustedRsaIssuers="Boolean"
                           audienceUriMode="Always/BearerKeyOnly/Never"
                           customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                           certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                           revocationMode="NoCheck/Online/Offline"
                           samlSerializer="String"
                           trustedStoreLocation="CurrentUser/LocalMachine">
  <allowedAudienceUris>
    <add allowedAudienceUri="String" />
  </allowedAudienceUris>
  <knownCertificates>
    <add findValue="String"
         storeLocation="CurrentUser/LocalMachine"
         storeName=" CurrentUser/LocalMachine"
         x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd422-111">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cd422-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cd422-112">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cd422-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd422-113">特性</span><span class="sxs-lookup"><span data-stu-id="cd422-113">Attributes</span></span>  
  
|<span data-ttu-id="cd422-114">特性</span><span class="sxs-lookup"><span data-stu-id="cd422-114">Attribute</span></span>|<span data-ttu-id="cd422-115">描述</span><span class="sxs-lookup"><span data-stu-id="cd422-115">Description</span></span>|  
|---------------|-----------------|  
|`allowedAudienceUris`|<span data-ttu-id="cd422-116">获取 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全令牌的目标 URI 集，只有在使用这些目标 URI 时，<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> 实例才会将该令牌视为有效令牌。</span><span class="sxs-lookup"><span data-stu-id="cd422-116">Gets the set of target URIs for which the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token can be targeted for in order to be considered valid by a <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> instance.</span></span> <span data-ttu-id="cd422-117">有关使用此属性的更多信息，请参见 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>。</span><span class="sxs-lookup"><span data-stu-id="cd422-117">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>.</span></span>|  
|`allowUntrustedRsaIssuers`|<span data-ttu-id="cd422-118">一个布尔值，指定是否允许不可信的 RSA 证书颁发者。</span><span class="sxs-lookup"><span data-stu-id="cd422-118">A Boolean value that specifies if untrusted RSA certificate issuers are allowed.</span></span><br /><br /> <span data-ttu-id="cd422-119">证书由证书颁发机构 (CA) 签名，以验证真实性。</span><span class="sxs-lookup"><span data-stu-id="cd422-119">Certificates are signed by certification authorities (CAs) to verify authenticity.</span></span> <span data-ttu-id="cd422-120">不可信的颁发者是指未被指定为可信的证书签名者的 CA。</span><span class="sxs-lookup"><span data-stu-id="cd422-120">An untrusted issuer is a CA that is not specified to be trusted to sign certificates.</span></span>|  
|`audienceUriMode`|<span data-ttu-id="cd422-121">获取一个值，该值指定是否应验证 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 安全令牌的 <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition>。</span><span class="sxs-lookup"><span data-stu-id="cd422-121">Gets a value that specifies whether the <xref:System.IdentityModel.Tokens.SamlSecurityToken> security token's <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> should be validated.</span></span> <span data-ttu-id="cd422-122">此值的类型为 <xref:System.IdentityModel.Selectors.AudienceUriMode>。</span><span class="sxs-lookup"><span data-stu-id="cd422-122">This value is of type <xref:System.IdentityModel.Selectors.AudienceUriMode>.</span></span> <span data-ttu-id="cd422-123">有关使用此属性的更多信息，请参见 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>。</span><span class="sxs-lookup"><span data-stu-id="cd422-123">For more information on using this attribute, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="cd422-124">设置证书验证模式。</span><span class="sxs-lookup"><span data-stu-id="cd422-124">Sets the certificate validation mode.</span></span> <span data-ttu-id="cd422-125"><xref:System.ServiceModel.Security.X509CertificateValidationMode> 的有效值之一。</span><span class="sxs-lookup"><span data-stu-id="cd422-125">One of the valid values of <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="cd422-126">如果设置为 `Custom`，则还必须提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="cd422-126">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="cd422-127">默认值为 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="cd422-127">The default is `ChainTrust`.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="cd422-128">可选的字符串。</span><span class="sxs-lookup"><span data-stu-id="cd422-128">Optional string.</span></span> <span data-ttu-id="cd422-129">一个用于验证自定义类型的类型和程序集。</span><span class="sxs-lookup"><span data-stu-id="cd422-129">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="cd422-130">当 `certificateValidationMode` 设置为 `Custom` 时，必须设置此属性。</span><span class="sxs-lookup"><span data-stu-id="cd422-130">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`revocationMode`|<span data-ttu-id="cd422-131">设置吊销模式以指定是否进行吊销检查，以及是联机执行还是脱机执行。</span><span class="sxs-lookup"><span data-stu-id="cd422-131">Sets the revocation mode that specifies whether a revocation check occurs, and if it is performed online or offline.</span></span> <span data-ttu-id="cd422-132">此属性的类型为 <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>。</span><span class="sxs-lookup"><span data-stu-id="cd422-132">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span>|  
|`samlSerializer`|<span data-ttu-id="cd422-133">一个可选字符串属性，指定用于服务凭据的 SamlSerializer 的类型。</span><span class="sxs-lookup"><span data-stu-id="cd422-133">An optional string attribute that specifies the type of SamlSerializer that is used for the service credential.</span></span> <span data-ttu-id="cd422-134">默认值为一个空字符串。</span><span class="sxs-lookup"><span data-stu-id="cd422-134">The default is an empty string.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="cd422-135">可选的枚举。</span><span class="sxs-lookup"><span data-stu-id="cd422-135">Optional enumeration.</span></span> <span data-ttu-id="cd422-136">两个系统存储位置之一：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="cd422-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd422-137">子元素</span><span class="sxs-lookup"><span data-stu-id="cd422-137">Child Elements</span></span>  
  
|<span data-ttu-id="cd422-138">元素</span><span class="sxs-lookup"><span data-stu-id="cd422-138">Element</span></span>|<span data-ttu-id="cd422-139">描述</span><span class="sxs-lookup"><span data-stu-id="cd422-139">Description</span></span>|  
|-------------|-----------------|  
|`knownCertificates`|<span data-ttu-id="cd422-140">指定一个 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> 元素的集合，此集合指定服务凭据的可信颁发者。</span><span class="sxs-lookup"><span data-stu-id="cd422-140">Specifies a collection of <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement> elements that specifies trusted issuers for the service credential.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd422-141">父元素</span><span class="sxs-lookup"><span data-stu-id="cd422-141">Parent Elements</span></span>  
  
|<span data-ttu-id="cd422-142">元素</span><span class="sxs-lookup"><span data-stu-id="cd422-142">Element</span></span>|<span data-ttu-id="cd422-143">描述</span><span class="sxs-lookup"><span data-stu-id="cd422-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd422-144">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="cd422-144">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="cd422-145">指定要用于对服务进行身份验证的凭据以及与客户端凭据验证相关的设置。</span><span class="sxs-lookup"><span data-stu-id="cd422-145">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd422-146">备注</span><span class="sxs-lookup"><span data-stu-id="cd422-146">Remarks</span></span>  
 <span data-ttu-id="cd422-147">颁发的令牌方案包含三个阶段。</span><span class="sxs-lookup"><span data-stu-id="cd422-147">The issued token scenario has three stages.</span></span> <span data-ttu-id="cd422-148">在第一阶段，尝试访问服务的客户端被指引到*安全令牌服务*。</span><span class="sxs-lookup"><span data-stu-id="cd422-148">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="cd422-149">然后，安全令牌服务对该客户端进行身份验证，随后向该客户端颁发一个令牌（通常是一个安全断言标记语言 (SAML) 令牌）。</span><span class="sxs-lookup"><span data-stu-id="cd422-149">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="cd422-150">接下来，客户端携带此令牌返回服务。</span><span class="sxs-lookup"><span data-stu-id="cd422-150">The client then returns to the service with the token.</span></span> <span data-ttu-id="cd422-151">服务检查该令牌，以获取使其可以对该令牌并进而对该客户端进行身份验证的数据。</span><span class="sxs-lookup"><span data-stu-id="cd422-151">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="cd422-152">若要对令牌进行身份验证，安全令牌服务所使用的证书必须为该服务所知。</span><span class="sxs-lookup"><span data-stu-id="cd422-152">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="cd422-153">此元素是所有此类安全令牌服务证书的储存库。</span><span class="sxs-lookup"><span data-stu-id="cd422-153">This element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="cd422-154">若要添加证书，请使用[ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="cd422-154">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="cd422-155">插入[\<添加 >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)为每个证书，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="cd422-155">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 <span data-ttu-id="cd422-156">默认情况下，必须从安全令牌服务那里获取证书。</span><span class="sxs-lookup"><span data-stu-id="cd422-156">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="cd422-157">这些“已知的”证书可以确保只有合法的客户端才能访问服务。</span><span class="sxs-lookup"><span data-stu-id="cd422-157">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="cd422-158">使用此配置元素的详细信息，请参阅[如何：联合身份验证服务上配置凭据](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="cd422-158">For more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd422-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="cd422-159">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
 [<span data-ttu-id="cd422-160">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="cd422-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="cd422-161">如何：联合身份验证服务上配置凭据</span><span class="sxs-lookup"><span data-stu-id="cd422-161">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
