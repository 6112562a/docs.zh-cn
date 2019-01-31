---
title: <add> 的 <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 128aaabe-3f1a-4c3b-b59f-898d0f02910f
ms.openlocfilehash: 022030489551bfaf48cffd4ba983bbd3c99abc87
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274282"
---
# <a name="add-of-knowncertificates"></a><span data-ttu-id="783ed-102">\<add> of \<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="783ed-102">\<add> of \<knownCertificates></span></span>
<span data-ttu-id="783ed-103">向已知证书集合添加 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="783ed-103">Adds an X.509 certificate to the collection of known certificates.</span></span>  
  
 <span data-ttu-id="783ed-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="783ed-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="783ed-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="783ed-105">\<behaviors></span></span>  
<span data-ttu-id="783ed-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="783ed-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="783ed-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="783ed-107">\<behavior></span></span>  
<span data-ttu-id="783ed-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="783ed-108">\<serviceCredentials></span></span>  
<span data-ttu-id="783ed-109">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="783ed-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="783ed-110">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="783ed-110">\<knownCertificates></span></span>  
<span data-ttu-id="783ed-111">\<add></span><span class="sxs-lookup"><span data-stu-id="783ed-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="783ed-112">语法</span><span class="sxs-lookup"><span data-stu-id="783ed-112">Syntax</span></span>  
  
```xml  
<knownCertificates>
   <add findValue="String"
      storeLocation="CurrentUser/LocalMachine"
      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
      x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="783ed-113">特性和元素</span><span class="sxs-lookup"><span data-stu-id="783ed-113">Attributes and Elements</span></span>  
 <span data-ttu-id="783ed-114">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="783ed-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="783ed-115">特性</span><span class="sxs-lookup"><span data-stu-id="783ed-115">Attributes</span></span>  
  
|<span data-ttu-id="783ed-116">特性</span><span class="sxs-lookup"><span data-stu-id="783ed-116">Attribute</span></span>|<span data-ttu-id="783ed-117">描述</span><span class="sxs-lookup"><span data-stu-id="783ed-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="783ed-118">findValue</span><span class="sxs-lookup"><span data-stu-id="783ed-118">findValue</span></span>|<span data-ttu-id="783ed-119">字符串。</span><span class="sxs-lookup"><span data-stu-id="783ed-119">String.</span></span> <span data-ttu-id="783ed-120">要搜索的值。</span><span class="sxs-lookup"><span data-stu-id="783ed-120">The value to search for.</span></span>|  
|<span data-ttu-id="783ed-121">storeLocation</span><span class="sxs-lookup"><span data-stu-id="783ed-121">storeLocation</span></span>|<span data-ttu-id="783ed-122">枚举。</span><span class="sxs-lookup"><span data-stu-id="783ed-122">Enumeration.</span></span> <span data-ttu-id="783ed-123">要搜索的两个存储位置之一。</span><span class="sxs-lookup"><span data-stu-id="783ed-123">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="783ed-124">storeName</span><span class="sxs-lookup"><span data-stu-id="783ed-124">storeName</span></span>|<span data-ttu-id="783ed-125">枚举。</span><span class="sxs-lookup"><span data-stu-id="783ed-125">Enumeration.</span></span> <span data-ttu-id="783ed-126">要搜索的系统存储之一。</span><span class="sxs-lookup"><span data-stu-id="783ed-126">One of the system stores to search.</span></span>|  
|<span data-ttu-id="783ed-127">x509FindType</span><span class="sxs-lookup"><span data-stu-id="783ed-127">x509FindType</span></span>|<span data-ttu-id="783ed-128">枚举。</span><span class="sxs-lookup"><span data-stu-id="783ed-128">Enumeration.</span></span> <span data-ttu-id="783ed-129">要搜索的证书字段之一。</span><span class="sxs-lookup"><span data-stu-id="783ed-129">One of the certificate fields to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="783ed-130">findValue 属性</span><span class="sxs-lookup"><span data-stu-id="783ed-130">findValue Attribute</span></span>  
  
|<span data-ttu-id="783ed-131">值</span><span class="sxs-lookup"><span data-stu-id="783ed-131">Value</span></span>|<span data-ttu-id="783ed-132">描述</span><span class="sxs-lookup"><span data-stu-id="783ed-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="783ed-133">String</span><span class="sxs-lookup"><span data-stu-id="783ed-133">String</span></span>|<span data-ttu-id="783ed-134">值取决于搜索的字段（由 X509FindType 属性指定）。</span><span class="sxs-lookup"><span data-stu-id="783ed-134">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="783ed-135">例如，如果搜索指纹，则此值必须为十六进制数字字符串。</span><span class="sxs-lookup"><span data-stu-id="783ed-135">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="783ed-136">x509FindType 属性</span><span class="sxs-lookup"><span data-stu-id="783ed-136">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="783ed-137">值</span><span class="sxs-lookup"><span data-stu-id="783ed-137">Value</span></span>|<span data-ttu-id="783ed-138">描述</span><span class="sxs-lookup"><span data-stu-id="783ed-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="783ed-139">枚举</span><span class="sxs-lookup"><span data-stu-id="783ed-139">Enumeration</span></span>|<span data-ttu-id="783ed-140">值包括：FindByThumbprint、 FindBySubjectName、 FindBySubjectDistinguishedName、 FindByIssuerName、 FindByIssuerDistinguishedName、 FindBySerialNumber、 FindByTimeValid、 FindByTimeNotYetValid、 FindBySerialNumber、 FindByTimeExpired、 FindByTemplateNameFindByApplicationPolicy、 FindByCertificatePolicy、 FindByExtension、 FindByKeyUsage、 和 FindBySubjectKeyIdentifier。</span><span class="sxs-lookup"><span data-stu-id="783ed-140">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="783ed-141">storeLocation 属性</span><span class="sxs-lookup"><span data-stu-id="783ed-141">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="783ed-142">值</span><span class="sxs-lookup"><span data-stu-id="783ed-142">Value</span></span>|<span data-ttu-id="783ed-143">描述</span><span class="sxs-lookup"><span data-stu-id="783ed-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="783ed-144">枚举</span><span class="sxs-lookup"><span data-stu-id="783ed-144">Enumeration</span></span>|<span data-ttu-id="783ed-145">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="783ed-145">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="783ed-146">storeName 属性</span><span class="sxs-lookup"><span data-stu-id="783ed-146">storeName Attribute</span></span>  
  
|<span data-ttu-id="783ed-147">值</span><span class="sxs-lookup"><span data-stu-id="783ed-147">Value</span></span>|<span data-ttu-id="783ed-148">描述</span><span class="sxs-lookup"><span data-stu-id="783ed-148">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="783ed-149">枚举</span><span class="sxs-lookup"><span data-stu-id="783ed-149">Enumeration</span></span>|<span data-ttu-id="783ed-150">值包括：AddressBook、 AuthRoot、 CertificateAuthority、 Disallowed、 My、 根、 TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="783ed-150">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="783ed-151">子元素</span><span class="sxs-lookup"><span data-stu-id="783ed-151">Child Elements</span></span>  
 <span data-ttu-id="783ed-152">无。</span><span class="sxs-lookup"><span data-stu-id="783ed-152">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="783ed-153">父元素</span><span class="sxs-lookup"><span data-stu-id="783ed-153">Parent Elements</span></span>  
  
|<span data-ttu-id="783ed-154">元素</span><span class="sxs-lookup"><span data-stu-id="783ed-154">Element</span></span>|<span data-ttu-id="783ed-155">描述</span><span class="sxs-lookup"><span data-stu-id="783ed-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="783ed-156">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="783ed-156">\<knownCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)|<span data-ttu-id="783ed-157">表示一个 X.509 证书集合，这些证书由安全令牌服务 (STS) 提供以用于验证安全令牌。</span><span class="sxs-lookup"><span data-stu-id="783ed-157">Represents a collection of X.509 certificates that are provided by a Security Token Service (STS) for validation of security tokens.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="783ed-158">备注</span><span class="sxs-lookup"><span data-stu-id="783ed-158">Remarks</span></span>  
 <span data-ttu-id="783ed-159">颁发的令牌方案包含三个阶段。</span><span class="sxs-lookup"><span data-stu-id="783ed-159">The issued token scenario has three stages.</span></span> <span data-ttu-id="783ed-160">在第一阶段，尝试访问服务的客户端被指引到*安全令牌服务*。</span><span class="sxs-lookup"><span data-stu-id="783ed-160">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="783ed-161">然后，安全令牌服务对该客户端进行身份验证，随后向该客户端颁发一个令牌（通常是一个安全断言标记语言 (SAML) 令牌）。</span><span class="sxs-lookup"><span data-stu-id="783ed-161">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="783ed-162">接下来，客户端携带此令牌返回服务。</span><span class="sxs-lookup"><span data-stu-id="783ed-162">The client then returns to the service with the token.</span></span> <span data-ttu-id="783ed-163">服务检查该令牌，以获取使其可以对该令牌并进而对该客户端进行身份验证的数据。</span><span class="sxs-lookup"><span data-stu-id="783ed-163">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="783ed-164">若要对令牌进行身份验证，安全令牌服务所使用的证书必须为该服务所知。</span><span class="sxs-lookup"><span data-stu-id="783ed-164">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="783ed-165">[ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)元素是所有此类安全令牌服务证书的存储库。</span><span class="sxs-lookup"><span data-stu-id="783ed-165">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="783ed-166">若要添加证书，请使用[ \<knownCertificates >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)。</span><span class="sxs-lookup"><span data-stu-id="783ed-166">To add certificates, use the [\<knownCertificates>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="783ed-167">插入[\<添加 > 元素\<knownCertificates > 元素](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)为每个证书，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="783ed-167">Insert an [\<add> element \<knownCertificates> Element](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="783ed-168">默认情况下，必须从安全令牌服务那里获取证书。</span><span class="sxs-lookup"><span data-stu-id="783ed-168">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="783ed-169">这些“已知的”证书可以确保只有合法的客户端才能访问服务。</span><span class="sxs-lookup"><span data-stu-id="783ed-169">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="783ed-170">若要查看条件所需的客户端进行身份验证的联合的服务，以及使用此配置元素的详细信息，请参阅[如何：联合身份验证服务上配置凭据](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)。</span><span class="sxs-lookup"><span data-stu-id="783ed-170">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="783ed-171">有关联合方案的详细信息，请参阅[联合身份验证和颁发令牌](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="783ed-171">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="783ed-172">示例</span><span class="sxs-lookup"><span data-stu-id="783ed-172">Example</span></span>  
 <span data-ttu-id="783ed-173">下面的示例将证书添加到任意 STS 证书的存储库。</span><span class="sxs-lookup"><span data-stu-id="783ed-173">The following example adds certificate to the repository for any STS certificates.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <serviceCredentials>
      <issuedTokenAuthentication>
        <knownCertificates>
          <add findValue="www.contoso.com"
               storeLocation="LocalMachine"
               storeName="CertificateAuthority"
               x509FindType="FindByIssuerName" />
        </knownCertificates>
      </issuedTokenAuthentication>
    </serviceCredentials>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="783ed-174">请参阅</span><span class="sxs-lookup"><span data-stu-id="783ed-174">See also</span></span>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="783ed-175">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="783ed-175">\<knownCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md)
- [<span data-ttu-id="783ed-176">使用证书</span><span class="sxs-lookup"><span data-stu-id="783ed-176">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="783ed-177">联合令牌与颁发的令牌</span><span class="sxs-lookup"><span data-stu-id="783ed-177">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="783ed-178">如何：联合身份验证服务上配置凭据</span><span class="sxs-lookup"><span data-stu-id="783ed-178">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="783ed-179">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="783ed-179">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
