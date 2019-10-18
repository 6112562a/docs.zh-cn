---
title: 了解保护级别
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 0c034608-a1ac-4007-8287-b1382eaa8bf2
ms.openlocfilehash: 896b75d3dfb5ebace9bef0c410e4a86dfb765bd8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321517"
---
# <a name="understanding-protection-level"></a><span data-ttu-id="92878-102">了解保护级别</span><span class="sxs-lookup"><span data-stu-id="92878-102">Understanding Protection Level</span></span>

<span data-ttu-id="92878-103">在许多不同的类中可以找到 `ProtectionLevel` 属性，例如 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 类。</span><span class="sxs-lookup"><span data-stu-id="92878-103">The `ProtectionLevel` property is found on many different classes, such as the <xref:System.ServiceModel.ServiceContractAttribute> and the <xref:System.ServiceModel.OperationContractAttribute> classes.</span></span> <span data-ttu-id="92878-104">此属性控制部分（或整个）消息的保护方式。</span><span class="sxs-lookup"><span data-stu-id="92878-104">The property controls how a part (or whole) of a message is protected.</span></span> <span data-ttu-id="92878-105">本主题介绍 Windows Communication Foundation （WCF）功能及其工作原理。</span><span class="sxs-lookup"><span data-stu-id="92878-105">This topic explains the Windows Communication Foundation (WCF) feature and how it works.</span></span>

<span data-ttu-id="92878-106">有关设置保护级别的说明，请参阅[如何：设置 ProtectionLevel 属性](how-to-set-the-protectionlevel-property.md)。</span><span class="sxs-lookup"><span data-stu-id="92878-106">For instructions on setting the protection level, see [How to: Set the ProtectionLevel Property](how-to-set-the-protectionlevel-property.md).</span></span>

> [!NOTE]
> <span data-ttu-id="92878-107">只能在代码中设置保护级别，不能在配置中设置。</span><span class="sxs-lookup"><span data-stu-id="92878-107">Protection levels can be set only in code, not in configuration.</span></span>

## <a name="basics"></a><span data-ttu-id="92878-108">基本知识</span><span class="sxs-lookup"><span data-stu-id="92878-108">Basics</span></span>

<span data-ttu-id="92878-109">若要了解保护级别功能，以下基本语句适用：</span><span class="sxs-lookup"><span data-stu-id="92878-109">To understand the protection level feature, the following basic statements apply:</span></span>

- <span data-ttu-id="92878-110">消息的任何部分都存在三种基本保护级别。</span><span class="sxs-lookup"><span data-stu-id="92878-110">Three basic levels of protection exist for any part of a message.</span></span> <span data-ttu-id="92878-111">属性（无论它出现在哪里）设置为 <xref:System.Net.Security.ProtectionLevel> 枚举值之一。</span><span class="sxs-lookup"><span data-stu-id="92878-111">The property (wherever it occurs) is set to one of the <xref:System.Net.Security.ProtectionLevel> enumeration values.</span></span> <span data-ttu-id="92878-112">按升序的保护顺序，它们包括：</span><span class="sxs-lookup"><span data-stu-id="92878-112">In ascending order of protection, they include:</span></span>

  - <span data-ttu-id="92878-113">`None`</span><span class="sxs-lookup"><span data-stu-id="92878-113">`None`.</span></span>

  - <span data-ttu-id="92878-114">`Sign`</span><span class="sxs-lookup"><span data-stu-id="92878-114">`Sign`.</span></span> <span data-ttu-id="92878-115">受保护的部分进行数字签名。</span><span class="sxs-lookup"><span data-stu-id="92878-115">The protected part is digitally signed.</span></span> <span data-ttu-id="92878-116">这样做可以保证检测到对受保护的消息部分进行的任何篡改。</span><span class="sxs-lookup"><span data-stu-id="92878-116">This ensures detection of any tampering with the protected message part.</span></span>

  - <span data-ttu-id="92878-117">`EncryptAndSign`</span><span class="sxs-lookup"><span data-stu-id="92878-117">`EncryptAndSign`.</span></span> <span data-ttu-id="92878-118">签名前会对消息部分进行加密，以确保其保密性。</span><span class="sxs-lookup"><span data-stu-id="92878-118">The message part is encrypted to ensure confidentiality before it is signed.</span></span>

- <span data-ttu-id="92878-119">仅可通过此功能为*应用程序数据*设置保护要求。</span><span class="sxs-lookup"><span data-stu-id="92878-119">You can set protection requirements only for *application data* with this feature.</span></span> <span data-ttu-id="92878-120">例如，WS-Addressing 标头是基础结构数据，因此不受 `ProtectionLevel` 影响。</span><span class="sxs-lookup"><span data-stu-id="92878-120">For example, WS-Addressing headers are infrastructure data and, therefore, are not affected by the `ProtectionLevel`.</span></span>

- <span data-ttu-id="92878-121">当安全模式设置为 `Transport` 时，整个消息由传输机制进行保护。</span><span class="sxs-lookup"><span data-stu-id="92878-121">When the security mode is set to `Transport`, the entire message is protected by the transport mechanism.</span></span> <span data-ttu-id="92878-122">因此，为消息的不同部分设置单独的保护级别没有作用。</span><span class="sxs-lookup"><span data-stu-id="92878-122">Therefore, setting a separate protection level for different parts of a message has no effect.</span></span>

- <span data-ttu-id="92878-123">@No__t_0 是一种方法，使开发人员可以设置绑定必须符合的*最低级别*。</span><span class="sxs-lookup"><span data-stu-id="92878-123">The `ProtectionLevel` is a way for the developer to set the *minimum level* that a binding must comply with.</span></span> <span data-ttu-id="92878-124">在部署了服务时，在配置中指定的实际绑定不一定支持最低级别。</span><span class="sxs-lookup"><span data-stu-id="92878-124">When a service is deployed, the actual binding specified in configuration may or may not support the minimum level.</span></span> <span data-ttu-id="92878-125">例如，默认情况下，<xref:System.ServiceModel.BasicHttpBinding> 类不提供安全性（尽管可以启用安全性）。</span><span class="sxs-lookup"><span data-stu-id="92878-125">For example, by default, the <xref:System.ServiceModel.BasicHttpBinding> class does not supply security (although it can be enabled).</span></span> <span data-ttu-id="92878-126">因此，将它与具有任何非 `None` 设置的协定一起使用将导致引发异常。</span><span class="sxs-lookup"><span data-stu-id="92878-126">Therefore, using it with a contract that has any setting other than `None` will cause an exception to be thrown.</span></span>

- <span data-ttu-id="92878-127">如果该服务要求 `Sign` 所有消息的最小 `ProtectionLevel`，则客户端（可能由非 WCF 技术创建）可以加密和签名所有消息（超过所需的最小值）。</span><span class="sxs-lookup"><span data-stu-id="92878-127">If the service requires that the minimum `ProtectionLevel` for all messages is `Sign`, a client (perhaps created by a non-WCF technology) can encrypt and sign all messages (which is more than the minimum required).</span></span> <span data-ttu-id="92878-128">在这种情况下，WCF 不会引发异常，因为客户端已经完成了超过最小值。</span><span class="sxs-lookup"><span data-stu-id="92878-128">In this case, WCF will not throw an exception because the client has done more than the minimum.</span></span> <span data-ttu-id="92878-129">但请注意，如果可能，WCF 应用程序（服务或客户端）不会过度保护消息部分，但将符合最低级别。</span><span class="sxs-lookup"><span data-stu-id="92878-129">Note, however, that WCF applications (services or clients) will not over-secure a message part if possible but will comply with the minimum level.</span></span> <span data-ttu-id="92878-130">还要注意，当使用 `Transport` 作为安全模式时，传输可能过度保护消息流，因为它在本质上无法以更精细的级别进行保护。</span><span class="sxs-lookup"><span data-stu-id="92878-130">Also note that when using `Transport` as the security mode, the transport may over-secure the message stream because it is inherently unable to secure at a more granular level.</span></span>

- <span data-ttu-id="92878-131">如果将 `ProtectionLevel` 显式设置为 `Sign` 或 `EncryptAndSign`，则你必须使用启用安全的绑定，否则将会引发异常。</span><span class="sxs-lookup"><span data-stu-id="92878-131">If you set the `ProtectionLevel` explicitly to either `Sign` or `EncryptAndSign`, then you must use a binding with security enabled or an exception will be thrown.</span></span>

- <span data-ttu-id="92878-132">如果你选择启用安全的绑定，并且未在协定的任何位置设置 `ProtectionLevel` 属性，则将对所有的应用程序数据进行加密或签名。</span><span class="sxs-lookup"><span data-stu-id="92878-132">If you select a binding that enables security and you do not set the `ProtectionLevel` property anywhere on the contract, all application data will be encrypted and signed.</span></span>

- <span data-ttu-id="92878-133">如果您选择未启用安全的绑定（例如，`BasicHttpBinding` 类在默认情况下禁用安全），并且没有显式设置 `ProtectionLevel`，那么所有应用程序数据都不会受到保护。</span><span class="sxs-lookup"><span data-stu-id="92878-133">If you select a binding that does not have security enabled (for example, the `BasicHttpBinding` class has security disabled by default), and the `ProtectionLevel` is not explicitly set, then none of the application data will be protected.</span></span>

- <span data-ttu-id="92878-134">如果所使用的绑定应用传输级别的安全，则将根据传输的功能对所有应用程序数据进行保护。</span><span class="sxs-lookup"><span data-stu-id="92878-134">If you are using a binding that applies security at the transport level, all application data will be secured according to the capabilities of the transport.</span></span>

- <span data-ttu-id="92878-135">如果所使用的绑定应用消息级别的安全，则将根据协定上设置的保护级别对应用程序数据进行保护。</span><span class="sxs-lookup"><span data-stu-id="92878-135">If you use a binding that applies security at the message level, then application data will be secured according to the protection levels set on the contract.</span></span> <span data-ttu-id="92878-136">如果不指定保护级别，则将对消息中所有的应用程序数据进行加密和签名。</span><span class="sxs-lookup"><span data-stu-id="92878-136">If you do not specify a protection level, then all application data in the messages will be encrypted and signed.</span></span>

- <span data-ttu-id="92878-137">可以在不同范围级别设置 `ProtectionLevel`。</span><span class="sxs-lookup"><span data-stu-id="92878-137">The `ProtectionLevel` can be set at different scoping levels.</span></span> <span data-ttu-id="92878-138">有一个与范围关联的层次结构，这将在下一节中进行说明。</span><span class="sxs-lookup"><span data-stu-id="92878-138">There is a hierarchy associated with scoping, which is explained in the next section.</span></span>

## <a name="scoping"></a><span data-ttu-id="92878-139">范围</span><span class="sxs-lookup"><span data-stu-id="92878-139">Scoping</span></span>

<span data-ttu-id="92878-140">设置最顶层 API 上的 `ProtectionLevel` 可以为它下面所有级别设置级别。</span><span class="sxs-lookup"><span data-stu-id="92878-140">Setting the `ProtectionLevel` on the topmost API sets the level for all levels below it.</span></span> <span data-ttu-id="92878-141">如果 `ProtectionLevel` 在较低级别上设置为其他值，该层次结构中该级别下的所有 API 都将立即重置为新级别（然而它上面的 API 仍将受最顶层级别影响）。</span><span class="sxs-lookup"><span data-stu-id="92878-141">If the `ProtectionLevel` is set to a different value at a lower level, all APIs below that level in the hierarchy will now be reset to the new level (APIs above it, however, will still be affected by the topmost level).</span></span> <span data-ttu-id="92878-142">该层次结构如下所示。</span><span class="sxs-lookup"><span data-stu-id="92878-142">The hierarchy is as follows.</span></span> <span data-ttu-id="92878-143">同一级别的属性是对等的。</span><span class="sxs-lookup"><span data-stu-id="92878-143">Attributes at the same level are peers.</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>

- <xref:System.ServiceModel.OperationContractAttribute>

- <xref:System.ServiceModel.FaultContractAttribute>

- <xref:System.ServiceModel.MessageContractAttribute>

- <xref:System.ServiceModel.MessageHeaderAttribute>

- <xref:System.ServiceModel.MessageBodyMemberAttribute>

## <a name="programming-protectionlevel"></a><span data-ttu-id="92878-144">ProtectionLevel 的编程</span><span class="sxs-lookup"><span data-stu-id="92878-144">Programming ProtectionLevel</span></span>

<span data-ttu-id="92878-145">若要在层次结构中的任意点对 `ProtectionLevel` 进行编程，只需在应用此属性 (Attribute) 时将其属性 (Property) 设置为适当的值即可。</span><span class="sxs-lookup"><span data-stu-id="92878-145">To program the `ProtectionLevel` at any point in the hierarchy, simply set the property to an appropriate value when applying the attribute.</span></span> <span data-ttu-id="92878-146">有关示例，请参阅[如何：设置 ProtectionLevel 属性](how-to-set-the-protectionlevel-property.md)。</span><span class="sxs-lookup"><span data-stu-id="92878-146">For examples, see [How to: Set the ProtectionLevel Property](how-to-set-the-protectionlevel-property.md).</span></span>

> [!NOTE]
> <span data-ttu-id="92878-147">要设置错误和消息协定的属性，需要了解这些功能的工作原理。</span><span class="sxs-lookup"><span data-stu-id="92878-147">Setting the property on faults and message contracts requires understanding how those features work.</span></span> <span data-ttu-id="92878-148">有关详细信息，请参阅[如何：设置 ProtectionLevel 属性](how-to-set-the-protectionlevel-property.md)和[使用消息协定](./feature-details/using-message-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="92878-148">For more information, see [How to: Set the ProtectionLevel Property](how-to-set-the-protectionlevel-property.md) and [Using Message Contracts](./feature-details/using-message-contracts.md).</span></span>

## <a name="ws-addressing-dependency"></a><span data-ttu-id="92878-149">WS-Addressing 依赖性</span><span class="sxs-lookup"><span data-stu-id="92878-149">WS-Addressing Dependency</span></span>

<span data-ttu-id="92878-150">在大多数情况下，使用 " [svcutil.exe" 元数据实用工具（）](servicemodel-metadata-utility-tool-svcutil-exe.md)来生成客户端可确保客户端和服务协定相同。</span><span class="sxs-lookup"><span data-stu-id="92878-150">In most cases, using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to generate a client ensures that the client and service contracts are identical.</span></span> <span data-ttu-id="92878-151">但是，看起来相同的协定却可能导致客户端引发异常。</span><span class="sxs-lookup"><span data-stu-id="92878-151">However, seemingly identical contracts can cause the client to throw an exception.</span></span> <span data-ttu-id="92878-152">只要绑定不支持 WS-Addressing 规范并且在协定上指定了多个保护级别，就会发生这种情况。</span><span class="sxs-lookup"><span data-stu-id="92878-152">This occurs whenever a binding does not support the WS-Addressing specification and multiple levels of protection are specified on the contract.</span></span> <span data-ttu-id="92878-153">例如，<xref:System.ServiceModel.BasicHttpBinding> 类不支持此规范，或者您创建一个不支持 WS-Addressing 的自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="92878-153">For example, the <xref:System.ServiceModel.BasicHttpBinding> class does not support the specification, or if you create a custom binding that does not support WS-Addressing.</span></span> <span data-ttu-id="92878-154">`ProtectionLevel` 功能依靠 WS-Addressing 规范在单个协定上启用不同的保护级别。</span><span class="sxs-lookup"><span data-stu-id="92878-154">The `ProtectionLevel` feature relies on the WS-Addressing specification to enable different protection levels on a single contract.</span></span> <span data-ttu-id="92878-155">如果绑定不支持 WS-Addressing 规范，所有级别都将设置为同一保护级别。</span><span class="sxs-lookup"><span data-stu-id="92878-155">If the binding does not support the WS-Addressing specification, all levels will be set to the same protection level.</span></span> <span data-ttu-id="92878-156">协定上所有范围的有效保护级别将设置为在协定上使用的最高保护级别。</span><span class="sxs-lookup"><span data-stu-id="92878-156">The effective protection level for all scopes on the contract will be set to the strongest protection level used on the contract.</span></span>

<span data-ttu-id="92878-157">这可能会引起初看上去难以调试的问题。</span><span class="sxs-lookup"><span data-stu-id="92878-157">This may cause a problem that is hard to debug at first glance.</span></span> <span data-ttu-id="92878-158">可以创建一个包括多个服务的方法的客户端协定（一个接口）。</span><span class="sxs-lookup"><span data-stu-id="92878-158">It is possible to create a client contract (an interface) that includes methods for more than one service.</span></span> <span data-ttu-id="92878-159">也就是说，使用同一接口创建一个与许多服务通信的客户端，而该单个接口包含针对所有服务的方法。</span><span class="sxs-lookup"><span data-stu-id="92878-159">That is, the same interface is used to create a client that communicates with many services, and the single interface contains methods for all services.</span></span> <span data-ttu-id="92878-160">在这种罕见的情况下，开发人员必须注意仅调用那些适用于每个特定服务的方法。</span><span class="sxs-lookup"><span data-stu-id="92878-160">The developer must take care in this rare scenario to invoke only those methods that are applicable for each particular service.</span></span> <span data-ttu-id="92878-161">如果绑定是 <xref:System.ServiceModel.BasicHttpBinding> 类，则不支持多个保护级别。</span><span class="sxs-lookup"><span data-stu-id="92878-161">If the binding is the <xref:System.ServiceModel.BasicHttpBinding> class, multiple protection levels cannot be supported.</span></span> <span data-ttu-id="92878-162">但是，对客户端进行答复的服务可能会对保护级别比要求的为低的客户端进行响应。</span><span class="sxs-lookup"><span data-stu-id="92878-162">However, a service replying to the client might respond to a client with a lower protection level than required.</span></span> <span data-ttu-id="92878-163">在这种情况下，客户端将会引发异常，因为它需要更高的保护级别。</span><span class="sxs-lookup"><span data-stu-id="92878-163">In this case, the client will throw an exception because it expects a higher protection level.</span></span>

<span data-ttu-id="92878-164">可用一个代码示例解释这个问题。</span><span class="sxs-lookup"><span data-stu-id="92878-164">An example of the code illustrates this problem.</span></span> <span data-ttu-id="92878-165">下面的示例显示一个服务和一个客户端协定。</span><span class="sxs-lookup"><span data-stu-id="92878-165">The following example shows a service and a client contract.</span></span> <span data-ttu-id="92878-166">假定绑定是[\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md)元素。</span><span class="sxs-lookup"><span data-stu-id="92878-166">Assume that the binding is the [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) element.</span></span> <span data-ttu-id="92878-167">因此，对协定的所有操作都具有相同的保护级别。</span><span class="sxs-lookup"><span data-stu-id="92878-167">Therefore, all operations on a contract have the same protection level.</span></span> <span data-ttu-id="92878-168">这一统一的保护级别被确定为所有操作中的最高保护级别。</span><span class="sxs-lookup"><span data-stu-id="92878-168">This uniform protection level is determined as the maximum protection level across all operations.</span></span>

<span data-ttu-id="92878-169">服务协定为：</span><span class="sxs-lookup"><span data-stu-id="92878-169">The service contract is:</span></span>

[!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
[!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]

<span data-ttu-id="92878-170">下面的代码显示客户端协定接口。</span><span class="sxs-lookup"><span data-stu-id="92878-170">The following code shows the client contract interface.</span></span> <span data-ttu-id="92878-171">请注意它包括一个 `Tax` 方法，此方法旨在与一个不同的服务一起使用：</span><span class="sxs-lookup"><span data-stu-id="92878-171">Note that it includes a `Tax` method that is intended to be used with a different service:</span></span>

[!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
[!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]

<span data-ttu-id="92878-172">当客户端调用 `Price` 方法时，它在接收到服务的答复时引发异常。</span><span class="sxs-lookup"><span data-stu-id="92878-172">When the client calls the `Price` method, it throws an exception when it receives a reply from the service.</span></span> <span data-ttu-id="92878-173">发生这种情况是因为客户端未指定 `ProtectionLevel` 的 `ServiceContractAttribute`，所以客户端为所有方法使用默认值 (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>)，包括 `Price` 方法。</span><span class="sxs-lookup"><span data-stu-id="92878-173">This occurs because the client does not specify a `ProtectionLevel` on the `ServiceContractAttribute`, and therefore the client uses the default (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) for all methods, including the `Price` method.</span></span> <span data-ttu-id="92878-174">但是，服务返回该值时使用 <xref:System.Net.Security.ProtectionLevel.Sign> 级别，因为服务协定定义了一个单一的方法，此方法将其保护级别设置为 <xref:System.Net.Security.ProtectionLevel.Sign>。</span><span class="sxs-lookup"><span data-stu-id="92878-174">However, the service returns the value using the <xref:System.Net.Security.ProtectionLevel.Sign> level because the service contract defines a single method that has its protection level set to <xref:System.Net.Security.ProtectionLevel.Sign>.</span></span> <span data-ttu-id="92878-175">在这种情况下，客户端在验证服务的响应时将引发错误。</span><span class="sxs-lookup"><span data-stu-id="92878-175">In this case, the client will throw an error when validating the response from the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="92878-176">请参阅</span><span class="sxs-lookup"><span data-stu-id="92878-176">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageHeaderAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- <xref:System.Net.Security.ProtectionLevel>
- [<span data-ttu-id="92878-177">保护服务</span><span class="sxs-lookup"><span data-stu-id="92878-177">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="92878-178">如何：设置 ProtectionLevel 属性</span><span class="sxs-lookup"><span data-stu-id="92878-178">How to: Set the ProtectionLevel Property</span></span>](how-to-set-the-protectionlevel-property.md)
- [<span data-ttu-id="92878-179">在协定和服务中指定并处理错误</span><span class="sxs-lookup"><span data-stu-id="92878-179">Specifying and Handling Faults in Contracts and Services</span></span>](specifying-and-handling-faults-in-contracts-and-services.md)
- [<span data-ttu-id="92878-180">使用消息协定</span><span class="sxs-lookup"><span data-stu-id="92878-180">Using Message Contracts</span></span>](./feature-details/using-message-contracts.md)
