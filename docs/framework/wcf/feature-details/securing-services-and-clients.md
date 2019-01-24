---
title: 保护服务和客户端的安全
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: ad5bffdb98276864501861d36ea4353eed6860b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691445"
---
# <a name="securing-services-and-clients"></a><span data-ttu-id="f6da9-102">保护服务和客户端的安全</span><span class="sxs-lookup"><span data-stu-id="f6da9-102">Securing Services and Clients</span></span>
<span data-ttu-id="f6da9-103">在本部分中的信息重点介绍编程安全 Windows Communication Foundation (WCF) 中。</span><span class="sxs-lookup"><span data-stu-id="f6da9-103">The information in this section focuses on programming security in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="f6da9-104">通常，这包括选择系统提供的相应绑定、设置安全元素的属性，然后设置服务行为的属性（控制检索凭据以供服务或客户端使用的方式）。</span><span class="sxs-lookup"><span data-stu-id="f6da9-104">Generally, this includes selecting an appropriate system-provided binding, setting the properties of the security element, and then setting properties of the service behaviors that govern how credentials are retrieved for use by either the service or the client.</span></span> <span data-ttu-id="f6da9-105">这些技术涵盖大多数情况下，大多数用户的安全要求，如中所示[常用安全方案](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="f6da9-105">These techniques cover the security requirements of most users for most scenarios, as shown in [Common Security Scenarios](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md).</span></span> <span data-ttu-id="f6da9-106">如果你的方案需要更多的功能，首先请参阅[使用自定义绑定的安全功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); 如果解决方案并不明显，请参阅[扩展安全](../../../../docs/framework/wcf/extending/extending-security.md)。</span><span class="sxs-lookup"><span data-stu-id="f6da9-106">If your scenario requires more capabilities, first see [Security Capabilities with Custom Bindings](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md); if a solution is not apparent, see [Extending Security](../../../../docs/framework/wcf/extending/extending-security.md).</span></span> <span data-ttu-id="f6da9-107">如果要创建 （或与进行互操作） 的系统使用丰富的声明，请参阅中的主题[授权](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="f6da9-107">If you are creating (or interoperating with) a system that uses rich claims, see the topics in [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f6da9-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="f6da9-108">In This Section</span></span>  
 [<span data-ttu-id="f6da9-109">WCF 安全编程</span><span class="sxs-lookup"><span data-stu-id="f6da9-109">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 <span data-ttu-id="f6da9-110">用于保护消息安全的编程模型概述。</span><span class="sxs-lookup"><span data-stu-id="f6da9-110">An overview of the programming model used to secure messages.</span></span>  
  
 [<span data-ttu-id="f6da9-111">传输安全性概述</span><span class="sxs-lookup"><span data-stu-id="f6da9-111">Transport Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)  
 <span data-ttu-id="f6da9-112">如何通过传输层保护消息安全概述。</span><span class="sxs-lookup"><span data-stu-id="f6da9-112">An overview of how to secure messages through the transport layer.</span></span>  
  
 [<span data-ttu-id="f6da9-113">消息安全性</span><span class="sxs-lookup"><span data-stu-id="f6da9-113">Message Security</span></span>](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)  
 <span data-ttu-id="f6da9-114">总结了使用 Windows Communication Foundation (WCF) 中的消息级安全性的原因。</span><span class="sxs-lookup"><span data-stu-id="f6da9-114">Summarizes reasons for using message-level security in Windows Communication Foundation (WCF).</span></span>  
  
 [<span data-ttu-id="f6da9-115">安全会话</span><span class="sxs-lookup"><span data-stu-id="f6da9-115">Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-sessions.md)  
 <span data-ttu-id="f6da9-116">讨论的所需保护 WCF 会话时的注意事项。</span><span class="sxs-lookup"><span data-stu-id="f6da9-116">A discussion of the considerations required when securing a WCF session.</span></span>  
  
 [<span data-ttu-id="f6da9-117">使用证书</span><span class="sxs-lookup"><span data-stu-id="f6da9-117">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 <span data-ttu-id="f6da9-118">说明使用 X.509 证书时必须完成的一些常见任务。</span><span class="sxs-lookup"><span data-stu-id="f6da9-118">An explanation of some of the common tasks required when using X.509 certificates.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f6da9-119">参考</span><span class="sxs-lookup"><span data-stu-id="f6da9-119">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="f6da9-120">相关章节</span><span class="sxs-lookup"><span data-stu-id="f6da9-120">Related Sections</span></span>  
 [<span data-ttu-id="f6da9-121">安全性概念</span><span class="sxs-lookup"><span data-stu-id="f6da9-121">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
  
 [<span data-ttu-id="f6da9-122">扩展安全性</span><span class="sxs-lookup"><span data-stu-id="f6da9-122">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="f6da9-123">常用安全方案</span><span class="sxs-lookup"><span data-stu-id="f6da9-123">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
 [<span data-ttu-id="f6da9-124">绑定与安全</span><span class="sxs-lookup"><span data-stu-id="f6da9-124">Bindings and Security</span></span>](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [<span data-ttu-id="f6da9-125">使用自定义绑定的安全功能</span><span class="sxs-lookup"><span data-stu-id="f6da9-125">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
  
 [<span data-ttu-id="f6da9-126">扩展安全性</span><span class="sxs-lookup"><span data-stu-id="f6da9-126">Extending Security</span></span>](../../../../docs/framework/wcf/extending/extending-security.md)  
  
 [<span data-ttu-id="f6da9-127">授权</span><span class="sxs-lookup"><span data-stu-id="f6da9-127">Authorization</span></span>](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="f6da9-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="f6da9-128">See also</span></span>
- [<span data-ttu-id="f6da9-129">基本 WCF 编程</span><span class="sxs-lookup"><span data-stu-id="f6da9-129">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [<span data-ttu-id="f6da9-130">Windows Server App Fabric 的安全模型</span><span class="sxs-lookup"><span data-stu-id="f6da9-130">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
