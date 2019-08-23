---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 1d4611d6fee9dad057985f7d8f5ef961d384efcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945977"
---
# <a name="bufferreceive"></a><span data-ttu-id="31d04-101">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="31d04-101">\<bufferReceive></span></span>
<span data-ttu-id="31d04-102">一种服务行为，允许服务使用缓冲接收处理，以使工作流服务能够处理无序消息。</span><span class="sxs-lookup"><span data-stu-id="31d04-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="31d04-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="31d04-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="31d04-104">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="31d04-104">\<behaviors></span></span>  
<span data-ttu-id="31d04-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="31d04-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="31d04-106">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="31d04-106">\<behavior></span></span>  
<span data-ttu-id="31d04-107">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="31d04-107">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d04-108">语法</span><span class="sxs-lookup"><span data-stu-id="31d04-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31d04-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="31d04-109">Attributes and Elements</span></span>  
 <span data-ttu-id="31d04-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="31d04-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31d04-111">特性</span><span class="sxs-lookup"><span data-stu-id="31d04-111">Attributes</span></span>  
  
|<span data-ttu-id="31d04-112">特性</span><span class="sxs-lookup"><span data-stu-id="31d04-112">Attribute</span></span>|<span data-ttu-id="31d04-113">描述</span><span class="sxs-lookup"><span data-stu-id="31d04-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31d04-114">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="31d04-114">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="31d04-115">一个整数，指定每个通道允许的最大挂起消息数。</span><span class="sxs-lookup"><span data-stu-id="31d04-115">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="31d04-116">默认值为 512。</span><span class="sxs-lookup"><span data-stu-id="31d04-116">The default value is 512.</span></span> <span data-ttu-id="31d04-117">此属性限制工作流服务可接收的无序消息数。</span><span class="sxs-lookup"><span data-stu-id="31d04-117">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31d04-118">子元素</span><span class="sxs-lookup"><span data-stu-id="31d04-118">Child Elements</span></span>  
 <span data-ttu-id="31d04-119">无。</span><span class="sxs-lookup"><span data-stu-id="31d04-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31d04-120">父元素</span><span class="sxs-lookup"><span data-stu-id="31d04-120">Parent Elements</span></span>  
  
|<span data-ttu-id="31d04-121">元素</span><span class="sxs-lookup"><span data-stu-id="31d04-121">Element</span></span>|<span data-ttu-id="31d04-122">描述</span><span class="sxs-lookup"><span data-stu-id="31d04-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31d04-123">\<serviceBehaviors > 的\<行为 ></span><span class="sxs-lookup"><span data-stu-id="31d04-123">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="31d04-124">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="31d04-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31d04-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="31d04-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
