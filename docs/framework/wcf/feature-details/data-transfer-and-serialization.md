---
title: 数据传输和序列化
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 1eefd82a149d0bc215ca441e92c7d737a744b1e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856552"
---
# <a name="data-transfer-and-serialization"></a><span data-ttu-id="4cb46-102">数据传输和序列化</span><span class="sxs-lookup"><span data-stu-id="4cb46-102">Data Transfer and Serialization</span></span>
<span data-ttu-id="4cb46-103">在已连接的系统中，服务和客户端依赖于数据交换来完成任何任务。</span><span class="sxs-lookup"><span data-stu-id="4cb46-103">In a connected system, services and clients depend on the exchange of data to accomplish any task.</span></span> <span data-ttu-id="4cb46-104">作为服务或客户端的开发人员，您还必须了解 Windows Communication Foundation (WCF) 如何才能创建高效且易于维护的应用程序处理了数据和数据序列化。</span><span class="sxs-lookup"><span data-stu-id="4cb46-104">As a developer of a service or client, you must also understand how Windows Communication Foundation (WCF) handles data and data serialization in order to create applications that are efficient and easy to maintain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4cb46-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="4cb46-105">In This Section</span></span>  
 [<span data-ttu-id="4cb46-106">在服务协定中指定数据传输</span><span class="sxs-lookup"><span data-stu-id="4cb46-106">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 <span data-ttu-id="4cb46-107">描述服务中数据传输的基本概念。</span><span class="sxs-lookup"><span data-stu-id="4cb46-107">Describes the basic concepts of data transfer in services.</span></span>  
  
 [<span data-ttu-id="4cb46-108">使用数据协定</span><span class="sxs-lookup"><span data-stu-id="4cb46-108">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 <span data-ttu-id="4cb46-109">描述什么是数据协定以及如何创建和使用它们。</span><span class="sxs-lookup"><span data-stu-id="4cb46-109">Describes what data contracts are and how to create and use them.</span></span>  
  
 [<span data-ttu-id="4cb46-110">数据协定序列化程序</span><span class="sxs-lookup"><span data-stu-id="4cb46-110">Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 <span data-ttu-id="4cb46-111">描述如何通过 <xref:System.Runtime.Serialization.DataContractSerializer> 类或 <xref:System.Runtime.Serialization.XmlObjectSerializer> 类的任何扩展完成数据序列化。</span><span class="sxs-lookup"><span data-stu-id="4cb46-111">Describes how to accomplish serialization of data with the <xref:System.Runtime.Serialization.DataContractSerializer> class or any extension of the <xref:System.Runtime.Serialization.XmlObjectSerializer> class.</span></span>  
  
 [<span data-ttu-id="4cb46-112">使用 XmlSerializer 类</span><span class="sxs-lookup"><span data-stu-id="4cb46-112">Using the XmlSerializer Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 <span data-ttu-id="4cb46-113">描述如何使用以及为什么使用 <xref:System.Xml.Serialization.XmlSerializer> 类（<xref:System.Runtime.Serialization.DataContractSerializer> 类的替代类）。</span><span class="sxs-lookup"><span data-stu-id="4cb46-113">Describes how and why to use the <xref:System.Xml.Serialization.XmlSerializer> class, an alternative to the <xref:System.Runtime.Serialization.DataContractSerializer> class.</span></span>  
  
 [<span data-ttu-id="4cb46-114">使用消息协定</span><span class="sxs-lookup"><span data-stu-id="4cb46-114">Using Message Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 <span data-ttu-id="4cb46-115">描述消息协定如何允许很好的控制 SOAP 消息。</span><span class="sxs-lookup"><span data-stu-id="4cb46-115">Describes how message contracts allow fine control over SOAP messages.</span></span>  
  
 [<span data-ttu-id="4cb46-116">使用 Message 类</span><span class="sxs-lookup"><span data-stu-id="4cb46-116">Using the Message Class</span></span>](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 <span data-ttu-id="4cb46-117">描述如何使用消息类功能。</span><span class="sxs-lookup"><span data-stu-id="4cb46-117">Describes how to use Message class features.</span></span>  
  
 [<span data-ttu-id="4cb46-118">筛选</span><span class="sxs-lookup"><span data-stu-id="4cb46-118">Filtering</span></span>](../../../../docs/framework/wcf/feature-details/filtering.md)  
 <span data-ttu-id="4cb46-119">描述基于各种条件启用消息预处理的筛选。</span><span class="sxs-lookup"><span data-stu-id="4cb46-119">Describes filtering, which enables pre-processing of a message based on various criteria.</span></span>  
  
 [<span data-ttu-id="4cb46-120">大数据和流式处理</span><span class="sxs-lookup"><span data-stu-id="4cb46-120">Large Data and Streaming</span></span>](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 <span data-ttu-id="4cb46-121">描述如何发送大数据块，如二进制文件。</span><span class="sxs-lookup"><span data-stu-id="4cb46-121">Describes how to send a large block of data, such as a binary file.</span></span>  
  
 [<span data-ttu-id="4cb46-122">数据的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="4cb46-122">Security Considerations for Data</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 <span data-ttu-id="4cb46-123">描述在对数据传输和序列化进行编程时要注意的项。</span><span class="sxs-lookup"><span data-stu-id="4cb46-123">Describes items to be aware of when programming data transfer and serialization.</span></span>  
  
 [<span data-ttu-id="4cb46-124">数据传输体系结构概述</span><span class="sxs-lookup"><span data-stu-id="4cb46-124">Data Transfer Architectural Overview</span></span>](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 <span data-ttu-id="4cb46-125">介绍 WCF 中的数据传输的总体设计视图。</span><span class="sxs-lookup"><span data-stu-id="4cb46-125">Describes a view of the overall design of data transfer in WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4cb46-126">参考</span><span class="sxs-lookup"><span data-stu-id="4cb46-126">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a><span data-ttu-id="4cb46-127">相关章节</span><span class="sxs-lookup"><span data-stu-id="4cb46-127">Related Sections</span></span>  
 [<span data-ttu-id="4cb46-128">扩展编码器和序列化程序</span><span class="sxs-lookup"><span data-stu-id="4cb46-128">Extending Encoders and Serializers</span></span>](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a><span data-ttu-id="4cb46-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="4cb46-129">See also</span></span>

- [<span data-ttu-id="4cb46-130">最佳做法：数据协定版本管理</span><span class="sxs-lookup"><span data-stu-id="4cb46-130">Best Practices: Data Contract Versioning</span></span>](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
- [<span data-ttu-id="4cb46-131">服务版本控制</span><span class="sxs-lookup"><span data-stu-id="4cb46-131">Service Versioning</span></span>](../../../../docs/framework/wcf/service-versioning.md)
