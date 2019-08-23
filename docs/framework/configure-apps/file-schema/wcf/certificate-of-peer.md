---
title: <certificate> 的 <peer>
ms.date: 03/30/2017
ms.assetid: 48b69142-c957-4305-a042-c9d0c9a55c0e
ms.openlocfilehash: 72128aca1321f3adc4c99ce0e3a47489b1640e31
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919591"
---
# <a name="certificate-of-peer"></a><span data-ttu-id="7372c-102">\<对等 > \<的证书 ></span><span class="sxs-lookup"><span data-stu-id="7372c-102">\<certificate> of \<peer></span></span>
<span data-ttu-id="7372c-103">指定对等方使用的证书。</span><span class="sxs-lookup"><span data-stu-id="7372c-103">Specifies a certificate used by a peer.</span></span>  
  
 <span data-ttu-id="7372c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7372c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7372c-105">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="7372c-105">\<behaviors></span></span>  
<span data-ttu-id="7372c-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7372c-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7372c-107">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="7372c-107">\<behavior></span></span>  
<span data-ttu-id="7372c-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="7372c-108">\<serviceCredentials></span></span>  
<span data-ttu-id="7372c-109">\<对等 ></span><span class="sxs-lookup"><span data-stu-id="7372c-109">\<peer></span></span>  
<span data-ttu-id="7372c-110">\<证书 ></span><span class="sxs-lookup"><span data-stu-id="7372c-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7372c-111">语法</span><span class="sxs-lookup"><span data-stu-id="7372c-111">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7372c-112">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7372c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7372c-113">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7372c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7372c-114">特性</span><span class="sxs-lookup"><span data-stu-id="7372c-114">Attributes</span></span>  
  
|<span data-ttu-id="7372c-115">特性</span><span class="sxs-lookup"><span data-stu-id="7372c-115">Attribute</span></span>|<span data-ttu-id="7372c-116">描述</span><span class="sxs-lookup"><span data-stu-id="7372c-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="7372c-117">一个字符串，包含要在 X.509 证书存储中搜索的值。</span><span class="sxs-lookup"><span data-stu-id="7372c-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="7372c-118">此属性中包含的类型必须满足指定 `x509FindType` 的要求。</span><span class="sxs-lookup"><span data-stu-id="7372c-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="7372c-119">默认值为一个空字符串。</span><span class="sxs-lookup"><span data-stu-id="7372c-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="7372c-120">指定客户端可用于验证对等方的证书的 X.509 证书存储的位置。</span><span class="sxs-lookup"><span data-stu-id="7372c-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="7372c-121">包括以下有效值：</span><span class="sxs-lookup"><span data-stu-id="7372c-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7372c-122">-LocalMachine: 分配给本地计算机的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="7372c-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="7372c-123">-CurrentUser: 分配给当前用户的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="7372c-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="7372c-124">默认值为 LocalMachine。</span><span class="sxs-lookup"><span data-stu-id="7372c-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="7372c-125">指定要打开的 X.509 证书存储区的名称。</span><span class="sxs-lookup"><span data-stu-id="7372c-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="7372c-126">包括以下有效值：</span><span class="sxs-lookup"><span data-stu-id="7372c-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7372c-127">通讯簿其他用户的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="7372c-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="7372c-128">AuthRoot第三方证书颁发机构 (Ca) 的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="7372c-128">-   AuthRoot: Certificate store for third-party certificate authorities (CAs).</span></span><br /><span data-ttu-id="7372c-129">CertificateAuthority中间证书颁发机构 (Ca) 的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="7372c-129">-   CertificateAuthority: Certificate store for intermediate certificate authorities (CAs).</span></span><br /><span data-ttu-id="7372c-130">禁用吊销的证书的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="7372c-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="7372c-131">记住个人证书的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="7372c-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="7372c-132">Root受信任的根证书颁发机构 (Ca) 的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="7372c-132">-   Root: Certificate store for trusted root certificate authorities (CAs).</span></span><br /><span data-ttu-id="7372c-133">TrustedPeople直接受信任的人和资源的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="7372c-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="7372c-134">TrustedPublisher直接受信任的发布者的证书存储区。</span><span class="sxs-lookup"><span data-stu-id="7372c-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="7372c-135">默认值为 My。</span><span class="sxs-lookup"><span data-stu-id="7372c-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="7372c-136">定义要执行的 X.509 搜索的类型。</span><span class="sxs-lookup"><span data-stu-id="7372c-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="7372c-137">包括以下有效值：</span><span class="sxs-lookup"><span data-stu-id="7372c-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7372c-138">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="7372c-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="7372c-139">-   FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="7372c-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="7372c-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="7372c-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="7372c-141">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="7372c-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="7372c-142">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="7372c-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="7372c-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="7372c-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="7372c-144">-   FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="7372c-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="7372c-145">-   FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="7372c-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="7372c-146">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="7372c-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="7372c-147">-   FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="7372c-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="7372c-148">-   FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="7372c-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="7372c-149">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="7372c-149">-   FindByExtension</span></span><br /><span data-ttu-id="7372c-150">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="7372c-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="7372c-151">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="7372c-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="7372c-152">`findValue` 属性中包含的类型必须满足指定 `X509FindType` 的要求。</span><span class="sxs-lookup"><span data-stu-id="7372c-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="7372c-153">默认值为 FindBySubjectDistinguishedName。</span><span class="sxs-lookup"><span data-stu-id="7372c-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7372c-154">子元素</span><span class="sxs-lookup"><span data-stu-id="7372c-154">Child Elements</span></span>  
 <span data-ttu-id="7372c-155">无。</span><span class="sxs-lookup"><span data-stu-id="7372c-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7372c-156">父元素</span><span class="sxs-lookup"><span data-stu-id="7372c-156">Parent Elements</span></span>  
  
|<span data-ttu-id="7372c-157">元素</span><span class="sxs-lookup"><span data-stu-id="7372c-157">Element</span></span>|<span data-ttu-id="7372c-158">描述</span><span class="sxs-lookup"><span data-stu-id="7372c-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7372c-159">\<peer></span><span class="sxs-lookup"><span data-stu-id="7372c-159">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="7372c-160">指定对等节点的当前凭据。</span><span class="sxs-lookup"><span data-stu-id="7372c-160">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7372c-161">备注</span><span class="sxs-lookup"><span data-stu-id="7372c-161">Remarks</span></span>  
 <span data-ttu-id="7372c-162">此配置元素包含对对等网格中的邻居进行身份验证时使用的 `X509Certificate2` 实例。</span><span class="sxs-lookup"><span data-stu-id="7372c-162">This configuration element contains an `X509Certificate2` instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="7372c-163">有关对等编程的详细信息, 请参阅对等[网络](../../../wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="7372c-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7372c-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="7372c-164">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="7372c-165">使用证书</span><span class="sxs-lookup"><span data-stu-id="7372c-165">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="7372c-166">对等网络</span><span class="sxs-lookup"><span data-stu-id="7372c-166">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="7372c-167">[对等通道消息身份验证](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7372c-167">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="7372c-168">[对等通道自定义身份验证](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7372c-168">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="7372c-169">保护对等通道应用程序</span><span class="sxs-lookup"><span data-stu-id="7372c-169">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="7372c-170">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="7372c-170">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
