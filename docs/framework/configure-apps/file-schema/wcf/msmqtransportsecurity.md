---
title: '&lt;msmqTransportSecurity&gt;'
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 2a4daea50e1b6c24d923e01a6bc7ae913c241001
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54593480"
---
# <a name="ltmsmqtransportsecuritygt"></a><span data-ttu-id="675cf-102">&lt;msmqTransportSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="675cf-102">&lt;msmqTransportSecurity&gt;</span></span>
<span data-ttu-id="675cf-103">指定自定义绑定的 MSMQ 传输的安全设置。</span><span class="sxs-lookup"><span data-stu-id="675cf-103">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
 <span data-ttu-id="675cf-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="675cf-104">\<system.serviceModel></span></span>  
<span data-ttu-id="675cf-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="675cf-105">\<bindings></span></span>  
<span data-ttu-id="675cf-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="675cf-106">\<customBinding></span></span>  
<span data-ttu-id="675cf-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="675cf-107">\<binding></span></span>  
<span data-ttu-id="675cf-108">\<msmqIntegration></span><span class="sxs-lookup"><span data-stu-id="675cf-108">\<msmqIntegration></span></span>  
<span data-ttu-id="675cf-109">\<msmqTransportSecurity></span><span class="sxs-lookup"><span data-stu-id="675cf-109">\<msmqTransportSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="675cf-110">语法</span><span class="sxs-lookup"><span data-stu-id="675cf-110">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="675cf-111">特性和元素</span><span class="sxs-lookup"><span data-stu-id="675cf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="675cf-112">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="675cf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="675cf-113">特性</span><span class="sxs-lookup"><span data-stu-id="675cf-113">Attributes</span></span>  
  
|<span data-ttu-id="675cf-114">特性</span><span class="sxs-lookup"><span data-stu-id="675cf-114">Attribute</span></span>|<span data-ttu-id="675cf-115">描述</span><span class="sxs-lookup"><span data-stu-id="675cf-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="675cf-116">指定 MSMQ 传输必须采用什么方式对消息进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="675cf-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="675cf-117">如果将此属性设置为 `None`，则 `msmqProtectionLevel` 属性的值也必须设置为 `None`。</span><span class="sxs-lookup"><span data-stu-id="675cf-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="675cf-118">包括以下有效值：</span><span class="sxs-lookup"><span data-stu-id="675cf-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="675cf-119">-None:无身份验证。</span><span class="sxs-lookup"><span data-stu-id="675cf-119">-   None: No authentication.</span></span><br /><span data-ttu-id="675cf-120">-Windows:身份验证机制使用 Active Directory 获取与消息关联的 SID 的 X.509 证书。</span><span class="sxs-lookup"><span data-stu-id="675cf-120">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="675cf-121">然后使用它来检查队列的 ACL 以确保用户有权写入队列。</span><span class="sxs-lookup"><span data-stu-id="675cf-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="675cf-122">-证书：通道从证书存储获取的证书。</span><span class="sxs-lookup"><span data-stu-id="675cf-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="675cf-123">默认值为 Windows。</span><span class="sxs-lookup"><span data-stu-id="675cf-123">The default value is Windows.</span></span> <span data-ttu-id="675cf-124">此属性的类型为 <xref:System.ServiceModel.MsmqAuthenticationMode>。</span><span class="sxs-lookup"><span data-stu-id="675cf-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="675cf-125">指定在消息队列管理器之间传输消息时用于在网络上对消息进行加密的算法。</span><span class="sxs-lookup"><span data-stu-id="675cf-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="675cf-126">包括以下有效值：</span><span class="sxs-lookup"><span data-stu-id="675cf-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="675cf-127">-   RC4Stream</span><span class="sxs-lookup"><span data-stu-id="675cf-127">-   RC4Stream</span></span><br /><span data-ttu-id="675cf-128">-   AES</span><span class="sxs-lookup"><span data-stu-id="675cf-128">-   AES</span></span><br /><br /> <span data-ttu-id="675cf-129">默认值为 RC4Stream。</span><span class="sxs-lookup"><span data-stu-id="675cf-129">The default value is RC4Stream.</span></span> <span data-ttu-id="675cf-130">此属性的类型为 <xref:System.ServiceModel.MsmqEncryptionAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="675cf-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="675cf-131">指定在 MSMQ 传输级别采用什么方式来保护消息。</span><span class="sxs-lookup"><span data-stu-id="675cf-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="675cf-132">加密可以确保消息的完整性，而 EncryptAndSign 不仅可以确保消息的完整性，还可以确保消息的不可否认性，也就是说，消息确实来自发送者，并且发送者与其所声称的身份一致。</span><span class="sxs-lookup"><span data-stu-id="675cf-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="675cf-133">包括以下有效值：</span><span class="sxs-lookup"><span data-stu-id="675cf-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="675cf-134">-None:无保护。</span><span class="sxs-lookup"><span data-stu-id="675cf-134">-   None: No protection.</span></span><br /><span data-ttu-id="675cf-135">登录：对消息进行签名。</span><span class="sxs-lookup"><span data-stu-id="675cf-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="675cf-136">-EncryptAndSign:对消息进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="675cf-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="675cf-137">默认值为 Sign。</span><span class="sxs-lookup"><span data-stu-id="675cf-137">The default value is Sign.</span></span> <span data-ttu-id="675cf-138">此属性的类型为 <xref:System.Net.Security.ProtectionLevel>。</span><span class="sxs-lookup"><span data-stu-id="675cf-138">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="675cf-139">指定用于计算签名中的摘要的算法。</span><span class="sxs-lookup"><span data-stu-id="675cf-139">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="675cf-140">包括以下有效值：</span><span class="sxs-lookup"><span data-stu-id="675cf-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="675cf-141">-   MD5</span><span class="sxs-lookup"><span data-stu-id="675cf-141">-   MD5</span></span><br /><span data-ttu-id="675cf-142">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="675cf-142">-   SHA1</span></span><br /><span data-ttu-id="675cf-143">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="675cf-143">-   SHA256</span></span><br /><span data-ttu-id="675cf-144">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="675cf-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="675cf-145">默认值为 SHA1。</span><span class="sxs-lookup"><span data-stu-id="675cf-145">The default value is SHA1.</span></span> <span data-ttu-id="675cf-146">此属性的类型为 <xref:System.ServiceModel.MsmqSecureHashAlgorithm>。</span><span class="sxs-lookup"><span data-stu-id="675cf-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="675cf-147">子元素</span><span class="sxs-lookup"><span data-stu-id="675cf-147">Child Elements</span></span>  
 <span data-ttu-id="675cf-148">无。</span><span class="sxs-lookup"><span data-stu-id="675cf-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="675cf-149">父元素</span><span class="sxs-lookup"><span data-stu-id="675cf-149">Parent Elements</span></span>  
  
|<span data-ttu-id="675cf-150">元素</span><span class="sxs-lookup"><span data-stu-id="675cf-150">Element</span></span>|<span data-ttu-id="675cf-151">描述</span><span class="sxs-lookup"><span data-stu-id="675cf-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="675cf-152">\<msmqIntegration></span><span class="sxs-lookup"><span data-stu-id="675cf-152">\<msmqIntegration></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegration.md)|<span data-ttu-id="675cf-153">指定与消息队列 (MSMQ) 发送方或接收方进行交互所需的设置。</span><span class="sxs-lookup"><span data-stu-id="675cf-153">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[<span data-ttu-id="675cf-154">\<msmqTransport></span><span class="sxs-lookup"><span data-stu-id="675cf-154">\<msmqTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransport.md)|<span data-ttu-id="675cf-155">指定使用本机 MSMQ 协议的 Windows Communication Foundation (WCF) 服务的队列通信属性。</span><span class="sxs-lookup"><span data-stu-id="675cf-155">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="675cf-156">备注</span><span class="sxs-lookup"><span data-stu-id="675cf-156">Remarks</span></span>  
 <span data-ttu-id="675cf-157">传输安全性的详细信息，请参阅[传输安全](../../../../../docs/framework/wcf/feature-details/transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="675cf-157">For more information on transport security, see [Transport Security](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="675cf-158">请参阅</span><span class="sxs-lookup"><span data-stu-id="675cf-158">See also</span></span>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="675cf-159">WCF 中的队列</span><span class="sxs-lookup"><span data-stu-id="675cf-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="675cf-160">传输</span><span class="sxs-lookup"><span data-stu-id="675cf-160">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="675cf-161">选择传输</span><span class="sxs-lookup"><span data-stu-id="675cf-161">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="675cf-162">绑定</span><span class="sxs-lookup"><span data-stu-id="675cf-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="675cf-163">扩展绑定</span><span class="sxs-lookup"><span data-stu-id="675cf-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="675cf-164">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="675cf-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="675cf-165">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="675cf-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="675cf-166">传输安全性</span><span class="sxs-lookup"><span data-stu-id="675cf-166">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
