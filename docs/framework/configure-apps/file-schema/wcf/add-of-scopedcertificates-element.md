---
title: '&lt;scopedCertificates&gt; 的 &lt;add&gt; 元素'
ms.date: 03/30/2017
ms.assetid: e21c1ef8-d6d6-4bca-ac5a-6fbf4bd77412
ms.openlocfilehash: a173d3b137833abfe8a69aed55b972c9b6469890
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146090"
---
# <a name="ltaddgt-of-ltscopedcertificatesgt-element"></a><span data-ttu-id="04651-102">&lt;scopedCertificates&gt; 的 &lt;add&gt; 元素</span><span class="sxs-lookup"><span data-stu-id="04651-102">&lt;add&gt; of &lt;scopedCertificates&gt; Element</span></span>
<span data-ttu-id="04651-103">向作用域证书集合添加 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="04651-103">Adds an X.509 certificate to the collection of scoped certificates.</span></span>  
  
 <span data-ttu-id="04651-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="04651-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="04651-105">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="04651-105">\<behaviors></span></span>  
<span data-ttu-id="04651-106">endpointBehaviors 部分</span><span class="sxs-lookup"><span data-stu-id="04651-106">endpointBehaviors section</span></span>  
<span data-ttu-id="04651-107">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="04651-107">\<behavior></span></span>  
<span data-ttu-id="04651-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="04651-108">\<clientCredentials></span></span>  
<span data-ttu-id="04651-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="04651-109">\<serviceCertificate></span></span>  
<span data-ttu-id="04651-110">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="04651-110">\<scopedCertificates></span></span>  
<span data-ttu-id="04651-111">\<添加 > 元素\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="04651-111">\<add> element for \<scopedCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04651-112">语法</span><span class="sxs-lookup"><span data-stu-id="04651-112">Syntax</span></span>  
  
```xml  
<add findValue="String"
     storeLocation="CurrentUser/LocalMachine"
     storeName=" CurrentUser/LocalMachine"
     targetUri="string"
     x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04651-113">特性和元素</span><span class="sxs-lookup"><span data-stu-id="04651-113">Attributes and Elements</span></span>  
 <span data-ttu-id="04651-114">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="04651-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04651-115">特性</span><span class="sxs-lookup"><span data-stu-id="04651-115">Attributes</span></span>  
  
|<span data-ttu-id="04651-116">特性</span><span class="sxs-lookup"><span data-stu-id="04651-116">Attribute</span></span>|<span data-ttu-id="04651-117">描述</span><span class="sxs-lookup"><span data-stu-id="04651-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="04651-118">targetUri</span><span class="sxs-lookup"><span data-stu-id="04651-118">targetUri</span></span>|<span data-ttu-id="04651-119">字符串。</span><span class="sxs-lookup"><span data-stu-id="04651-119">String.</span></span> <span data-ttu-id="04651-120">指定与证书相关的服务的 URI。</span><span class="sxs-lookup"><span data-stu-id="04651-120">Specifies the URI of the service associated with the certificate.</span></span>|  
|<span data-ttu-id="04651-121">findValue</span><span class="sxs-lookup"><span data-stu-id="04651-121">findValue</span></span>|<span data-ttu-id="04651-122">字符串。</span><span class="sxs-lookup"><span data-stu-id="04651-122">String.</span></span> <span data-ttu-id="04651-123">要搜索的值。</span><span class="sxs-lookup"><span data-stu-id="04651-123">The value to search for.</span></span>|  
|<span data-ttu-id="04651-124">x509FindType</span><span class="sxs-lookup"><span data-stu-id="04651-124">x509FindType</span></span>|<span data-ttu-id="04651-125">枚举。</span><span class="sxs-lookup"><span data-stu-id="04651-125">Enumeration.</span></span> <span data-ttu-id="04651-126">要搜索的证书字段之一。</span><span class="sxs-lookup"><span data-stu-id="04651-126">One of the certificate fields to search.</span></span>|  
|<span data-ttu-id="04651-127">storeLocation</span><span class="sxs-lookup"><span data-stu-id="04651-127">storeLocation</span></span>|<span data-ttu-id="04651-128">枚举。</span><span class="sxs-lookup"><span data-stu-id="04651-128">Enumeration.</span></span> <span data-ttu-id="04651-129">要搜索的两个存储位置之一。</span><span class="sxs-lookup"><span data-stu-id="04651-129">One of the two store locations to search.</span></span>|  
|<span data-ttu-id="04651-130">storeName</span><span class="sxs-lookup"><span data-stu-id="04651-130">storeName</span></span>|<span data-ttu-id="04651-131">枚举。</span><span class="sxs-lookup"><span data-stu-id="04651-131">Enumeration.</span></span> <span data-ttu-id="04651-132">要搜索的系统存储之一。</span><span class="sxs-lookup"><span data-stu-id="04651-132">One of the system stores to search.</span></span>|  
  
## <a name="findvalue-attribute"></a><span data-ttu-id="04651-133">findValue 属性</span><span class="sxs-lookup"><span data-stu-id="04651-133">findValue Attribute</span></span>  
  
|<span data-ttu-id="04651-134">值</span><span class="sxs-lookup"><span data-stu-id="04651-134">Value</span></span>|<span data-ttu-id="04651-135">描述</span><span class="sxs-lookup"><span data-stu-id="04651-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04651-136">String</span><span class="sxs-lookup"><span data-stu-id="04651-136">String</span></span>|<span data-ttu-id="04651-137">值取决于搜索的字段（由 X509FindType 属性指定）。</span><span class="sxs-lookup"><span data-stu-id="04651-137">The value depends on the field (specified by the X509FindType attribute) being searched.</span></span> <span data-ttu-id="04651-138">例如，如果搜索指纹，则此值必须为十六进制数字字符串。</span><span class="sxs-lookup"><span data-stu-id="04651-138">For example, if searching for a thumbprint, the value must be a string of hexadecimal numbers.</span></span>|  
  
## <a name="x509findtype-attribute"></a><span data-ttu-id="04651-139">x509FindType 属性</span><span class="sxs-lookup"><span data-stu-id="04651-139">x509FindType Attribute</span></span>  
  
|<span data-ttu-id="04651-140">值</span><span class="sxs-lookup"><span data-stu-id="04651-140">Value</span></span>|<span data-ttu-id="04651-141">描述</span><span class="sxs-lookup"><span data-stu-id="04651-141">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04651-142">枚举</span><span class="sxs-lookup"><span data-stu-id="04651-142">Enumeration</span></span>|<span data-ttu-id="04651-143">值包括：FindByThumbprint、 FindBySubjectName、 FindBySubjectDistinguishedName、 FindByIssuerName、 FindByIssuerDistinguishedName、 FindBySerialNumber、 FindByTimeValid、 FindByTimeNotYetValid、 FindBySerialNumber、 FindByTimeExpired、 FindByTemplateNameFindByApplicationPolicy、 FindByCertificatePolicy、 FindByExtension、 FindByKeyUsage、 和 FindBySubjectKeyIdentifier。</span><span class="sxs-lookup"><span data-stu-id="04651-143">Values include: FindByThumbprint, FindBySubjectName, FindBySubjectDistinguishedName, FindByIssuerName, FindByIssuerDistinguishedName, FindBySerialNumber, FindByTimeValid, FindByTimeNotYetValid, FindBySerialNumber, FindByTimeExpired, FindByTemplateName, FindByApplicationPolicy, FindByCertificatePolicy, FindByExtension, FindByKeyUsage, FindBySubjectKeyIdentifier.</span></span>|  
  
## <a name="storelocation-attribute"></a><span data-ttu-id="04651-144">storeLocation 属性</span><span class="sxs-lookup"><span data-stu-id="04651-144">storeLocation Attribute</span></span>  
  
|<span data-ttu-id="04651-145">值</span><span class="sxs-lookup"><span data-stu-id="04651-145">Value</span></span>|<span data-ttu-id="04651-146">描述</span><span class="sxs-lookup"><span data-stu-id="04651-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04651-147">枚举</span><span class="sxs-lookup"><span data-stu-id="04651-147">Enumeration</span></span>|<span data-ttu-id="04651-148">CurrentUser 或 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="04651-148">CurrentUser or LocalMachine.</span></span>|  
  
## <a name="storename-attribute"></a><span data-ttu-id="04651-149">storeName 属性</span><span class="sxs-lookup"><span data-stu-id="04651-149">storeName Attribute</span></span>  
  
|<span data-ttu-id="04651-150">值</span><span class="sxs-lookup"><span data-stu-id="04651-150">Value</span></span>|<span data-ttu-id="04651-151">描述</span><span class="sxs-lookup"><span data-stu-id="04651-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="04651-152">枚举</span><span class="sxs-lookup"><span data-stu-id="04651-152">Enumeration</span></span>|<span data-ttu-id="04651-153">值包括：AddressBook、 AuthRoot、 CertificateAuthority、 Disallowed、 My、 根、 TrustedPeople 和 TrustedPublisher。</span><span class="sxs-lookup"><span data-stu-id="04651-153">Values include: AddressBook, AuthRoot, CertificateAuthority, Disallowed, My, Root, TrustedPeople, and TrustedPublisher.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04651-154">子元素</span><span class="sxs-lookup"><span data-stu-id="04651-154">Child Elements</span></span>  
 <span data-ttu-id="04651-155">无。</span><span class="sxs-lookup"><span data-stu-id="04651-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04651-156">父元素</span><span class="sxs-lookup"><span data-stu-id="04651-156">Parent Elements</span></span>  
  
|<span data-ttu-id="04651-157">元素</span><span class="sxs-lookup"><span data-stu-id="04651-157">Element</span></span>|<span data-ttu-id="04651-158">描述</span><span class="sxs-lookup"><span data-stu-id="04651-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="04651-159">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="04651-159">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="04651-160">表示特定服务为身份验证提供的 X.509（作用域）证书的集合。</span><span class="sxs-lookup"><span data-stu-id="04651-160">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04651-161">备注</span><span class="sxs-lookup"><span data-stu-id="04651-161">Remarks</span></span>  
 <span data-ttu-id="04651-162">此元素使客户端能够根据与它通信的服务的 URL 来配置要使用的服务证书。</span><span class="sxs-lookup"><span data-stu-id="04651-162">This element enables the client to configure a service certificate to use based on the URL of the service it communicates with.</span></span> <span data-ttu-id="04651-163">这在已颁发令牌的方案中尤其有用，在这些方案中，客户端可与多个服务（终端服务以及中间的安全令牌服务）进行通信。</span><span class="sxs-lookup"><span data-stu-id="04651-163">This is especially useful in issued token scenarios where a client can be communicating to multiple services (the end service as well as intermediary security token services).</span></span> <span data-ttu-id="04651-164">对于使用基于证书的消息安全的绑定，此证书用于加密发送给服务的消息，并期望服务用它来对客户端的应答进行签名。</span><span class="sxs-lookup"><span data-stu-id="04651-164">For bindings that use certificate-based message security, this certificate is used to encrypt messages to the service, and is expected to be used by the service for signing replies to the client.</span></span>  
  
 <span data-ttu-id="04651-165">如果绑定需要服务的证书，但在 ScopedCertificates 中未找到服务 URL 的特定证书，则使用默认证书。</span><span class="sxs-lookup"><span data-stu-id="04651-165">If a binding requires a certificate for the service and no specific certificate for the service URL is found in the ScopedCertificates, the default certificate is used.</span></span>  
  
 <span data-ttu-id="04651-166">有关详细信息，请参阅的"作用域证书"部分[如何：创建联合客户端](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)。</span><span class="sxs-lookup"><span data-stu-id="04651-166">For more information, see the "Scoped Certificates" section of [How to: Create a Federated Client](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04651-167">示例</span><span class="sxs-lookup"><span data-stu-id="04651-167">Example</span></span>  
 <span data-ttu-id="04651-168">下面的示例向集合中添加一个 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="04651-168">The following example adds an X.509 certificate the collection.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <serviceCertificate>
          <scopedCertificates>
            <add targetUri="http://www.contoso.com"
                 findValue="www.Contoso.com"
                 storeLocation="LocalMachine"
                 storeName="Root"
                 x509FindType="FindByIssuerName" />
          </scopedCertificates>
        </serviceCertificate>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="04651-169">请参阅</span><span class="sxs-lookup"><span data-stu-id="04651-169">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [<span data-ttu-id="04651-170">如何：创建联合客户端</span><span class="sxs-lookup"><span data-stu-id="04651-170">How to: Create a Federated Client</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [<span data-ttu-id="04651-171">使用证书</span><span class="sxs-lookup"><span data-stu-id="04651-171">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="04651-172">保护客户端</span><span class="sxs-lookup"><span data-stu-id="04651-172">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="04651-173">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="04651-173">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
