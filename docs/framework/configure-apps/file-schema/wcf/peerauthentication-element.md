---
title: '&lt;peerAuthentication&gt; 元素'
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 8937df6a2fcab305a519d566f7d666a3d94b4061
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149711"
---
# <a name="ltpeerauthenticationgt-element"></a><span data-ttu-id="10477-102">&lt;peerAuthentication&gt; 元素</span><span class="sxs-lookup"><span data-stu-id="10477-102">&lt;peerAuthentication&gt; Element</span></span>
<span data-ttu-id="10477-103">指定用于对等客户端的身份验证选项。</span><span class="sxs-lookup"><span data-stu-id="10477-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="10477-104">有关对等编程的详细信息，请参阅[对等网络](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="10477-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="10477-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="10477-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="10477-106">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="10477-106">\<behaviors></span></span>  
<span data-ttu-id="10477-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="10477-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="10477-108">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="10477-108">\<behavior></span></span>  
<span data-ttu-id="10477-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="10477-109">\<clientCredentials></span></span>  
<span data-ttu-id="10477-110">\<对等 ></span><span class="sxs-lookup"><span data-stu-id="10477-110">\<peer></span></span>  
<span data-ttu-id="10477-111">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="10477-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10477-112">语法</span><span class="sxs-lookup"><span data-stu-id="10477-112">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10477-113">特性和元素</span><span class="sxs-lookup"><span data-stu-id="10477-113">Attributes and Elements</span></span>  
 <span data-ttu-id="10477-114">以下几节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="10477-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10477-115">特性</span><span class="sxs-lookup"><span data-stu-id="10477-115">Attributes</span></span>  
  
|<span data-ttu-id="10477-116">特性</span><span class="sxs-lookup"><span data-stu-id="10477-116">Attribute</span></span>|<span data-ttu-id="10477-117">描述</span><span class="sxs-lookup"><span data-stu-id="10477-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="10477-118">可选的字符串。</span><span class="sxs-lookup"><span data-stu-id="10477-118">Optional string.</span></span> <span data-ttu-id="10477-119">一个用于验证自定义类型的类型和程序集。</span><span class="sxs-lookup"><span data-stu-id="10477-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="10477-120">当 `certificateValidationMode` 设置为 `Custom` 时，必须设置此属性。</span><span class="sxs-lookup"><span data-stu-id="10477-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certifcateValidationMode`|<span data-ttu-id="10477-121">可选的枚举。</span><span class="sxs-lookup"><span data-stu-id="10477-121">Optional enumeration.</span></span> <span data-ttu-id="10477-122">指定用来验证凭据的三种模式之一。</span><span class="sxs-lookup"><span data-stu-id="10477-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="10477-123">如果设置为 `Custom`，则还必须提供 `customCertificateValidator`。</span><span class="sxs-lookup"><span data-stu-id="10477-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="10477-124">默认值为 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="10477-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="10477-125">可选的枚举。</span><span class="sxs-lookup"><span data-stu-id="10477-125">Optional enumeration.</span></span> <span data-ttu-id="10477-126">用于检查吊销证书列表 (CRL) 的一种模式。</span><span class="sxs-lookup"><span data-stu-id="10477-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="10477-127">默认值为 `Online`。</span><span class="sxs-lookup"><span data-stu-id="10477-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="10477-128">可选的枚举。</span><span class="sxs-lookup"><span data-stu-id="10477-128">Optional enumeration.</span></span> <span data-ttu-id="10477-129">两个系统存储位置之一：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="10477-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="10477-130">在向客户端协商服务证书时使用此值。</span><span class="sxs-lookup"><span data-stu-id="10477-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="10477-131">对执行验证**受信任的人员**将存储在指定的存储位置。</span><span class="sxs-lookup"><span data-stu-id="10477-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="10477-132">默认值为 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="10477-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="10477-133">customCertificateValidatorType 属性</span><span class="sxs-lookup"><span data-stu-id="10477-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="10477-134">值</span><span class="sxs-lookup"><span data-stu-id="10477-134">Value</span></span>|<span data-ttu-id="10477-135">描述</span><span class="sxs-lookup"><span data-stu-id="10477-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10477-136">String</span><span class="sxs-lookup"><span data-stu-id="10477-136">String</span></span>|<span data-ttu-id="10477-137">指定类型名称和程序集以及用于查找类型的其他数据。</span><span class="sxs-lookup"><span data-stu-id="10477-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="10477-138">至少需要命名空间和类型名称。</span><span class="sxs-lookup"><span data-stu-id="10477-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="10477-139">可选信息包括：程序集名称、版本号、区域性和公钥标记。</span><span class="sxs-lookup"><span data-stu-id="10477-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="10477-140">certificateValidationMode 属性</span><span class="sxs-lookup"><span data-stu-id="10477-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="10477-141">值</span><span class="sxs-lookup"><span data-stu-id="10477-141">Value</span></span>|<span data-ttu-id="10477-142">描述</span><span class="sxs-lookup"><span data-stu-id="10477-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10477-143">枚举</span><span class="sxs-lookup"><span data-stu-id="10477-143">Enumeration</span></span>|<span data-ttu-id="10477-144">下列值之一：`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust` 和 `Custom`。</span><span class="sxs-lookup"><span data-stu-id="10477-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="10477-145">默认值为 `ChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="10477-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="10477-146">有关详细信息，请参阅[Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="10477-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="10477-147">revocationMode 属性</span><span class="sxs-lookup"><span data-stu-id="10477-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="10477-148">值</span><span class="sxs-lookup"><span data-stu-id="10477-148">Value</span></span>|<span data-ttu-id="10477-149">描述</span><span class="sxs-lookup"><span data-stu-id="10477-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10477-150">枚举</span><span class="sxs-lookup"><span data-stu-id="10477-150">Enumeration</span></span>|<span data-ttu-id="10477-151">下列值之一：`NoCheck`、`Online` 和 `Offline`。</span><span class="sxs-lookup"><span data-stu-id="10477-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="10477-152">默认值为 `Online`。</span><span class="sxs-lookup"><span data-stu-id="10477-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="10477-153">有关详细信息，请参阅[Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="10477-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="10477-154">trustedStoreLocation 属性</span><span class="sxs-lookup"><span data-stu-id="10477-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="10477-155">值</span><span class="sxs-lookup"><span data-stu-id="10477-155">Value</span></span>|<span data-ttu-id="10477-156">描述</span><span class="sxs-lookup"><span data-stu-id="10477-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10477-157">枚举</span><span class="sxs-lookup"><span data-stu-id="10477-157">Enumeration</span></span>|<span data-ttu-id="10477-158">下列值之一：`LocalMachine` 或 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="10477-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="10477-159">默认值为 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="10477-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="10477-160">如果客户端应用程序在系统帐户下运行，则证书通常位于 `LocalMachine`。</span><span class="sxs-lookup"><span data-stu-id="10477-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="10477-161">如果客户端应用程序在用户帐户下运行，则证书通常位于 `CurrentUser`。</span><span class="sxs-lookup"><span data-stu-id="10477-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10477-162">子元素</span><span class="sxs-lookup"><span data-stu-id="10477-162">Child Elements</span></span>  
 <span data-ttu-id="10477-163">无。</span><span class="sxs-lookup"><span data-stu-id="10477-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10477-164">父元素</span><span class="sxs-lookup"><span data-stu-id="10477-164">Parent Elements</span></span>  
  
|<span data-ttu-id="10477-165">元素</span><span class="sxs-lookup"><span data-stu-id="10477-165">Element</span></span>|<span data-ttu-id="10477-166">描述</span><span class="sxs-lookup"><span data-stu-id="10477-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10477-167">\<peer></span><span class="sxs-lookup"><span data-stu-id="10477-167">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="10477-168">指定一个用于向对等服务证明客户端身份的凭据。</span><span class="sxs-lookup"><span data-stu-id="10477-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10477-169">备注</span><span class="sxs-lookup"><span data-stu-id="10477-169">Remarks</span></span>  
 <span data-ttu-id="10477-170">`<authentication>` 元素与 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> 类相对应。</span><span class="sxs-lookup"><span data-stu-id="10477-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="10477-171">此元素指定一个验证程序，在网格中执行邻居对等身份验证的过程中将调用该验证程序。</span><span class="sxs-lookup"><span data-stu-id="10477-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="10477-172">当新对等方尝试建立邻居连接时，它会将自己的凭据传递到响应的对等方。</span><span class="sxs-lookup"><span data-stu-id="10477-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="10477-173">将调用响应方的验证程序来验证远程方的凭据。</span><span class="sxs-lookup"><span data-stu-id="10477-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="10477-174">每当在网格中建立对等连接时，对等方将会相互进行身份验证，这意味着会同时在两方调用验证程序。</span><span class="sxs-lookup"><span data-stu-id="10477-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10477-175">示例</span><span class="sxs-lookup"><span data-stu-id="10477-175">Example</span></span>  
 <span data-ttu-id="10477-176">下面的代码将证书验证模式设置为 `PeerOrChainTrust`。</span><span class="sxs-lookup"><span data-stu-id="10477-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="10477-177">请参阅</span><span class="sxs-lookup"><span data-stu-id="10477-177">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="10477-178">使用证书</span><span class="sxs-lookup"><span data-stu-id="10477-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="10477-179">对等网络</span><span class="sxs-lookup"><span data-stu-id="10477-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="10477-180">对等通道消息身份验证</span><span class="sxs-lookup"><span data-stu-id="10477-180">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="10477-181">对等通道自定义身份验证</span><span class="sxs-lookup"><span data-stu-id="10477-181">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="10477-182">保护对等通道应用程序</span><span class="sxs-lookup"><span data-stu-id="10477-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
