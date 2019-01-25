---
title: '&lt;endToEndTracing&gt;'
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: c2f5e33eff4fdc6dfa85bcc10b59a7c1436cabb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519358"
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="e2a1e-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="e2a1e-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="e2a1e-103">一个配置元素，用于启用和禁用服务应用程序运行过程中端对端跟踪的不同方面。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="e2a1e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e2a1e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e2a1e-105">\<diagnostic></span><span class="sxs-lookup"><span data-stu-id="e2a1e-105">\<diagnostic></span></span>  
<span data-ttu-id="e2a1e-106">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="e2a1e-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2a1e-107">语法</span><span class="sxs-lookup"><span data-stu-id="e2a1e-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2a1e-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e2a1e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e2a1e-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2a1e-110">特性</span><span class="sxs-lookup"><span data-stu-id="e2a1e-110">Attributes</span></span>  
  
|<span data-ttu-id="e2a1e-111">特性</span><span class="sxs-lookup"><span data-stu-id="e2a1e-111">Attribute</span></span>|<span data-ttu-id="e2a1e-112">描述</span><span class="sxs-lookup"><span data-stu-id="e2a1e-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="e2a1e-113">一个布尔值，指定是否启用活动跟踪。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="e2a1e-114">一个布尔值，指定是否启用消息流跟踪。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="e2a1e-115">一个布尔值，指定是否将传播特性设置为 true。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2a1e-116">子元素</span><span class="sxs-lookup"><span data-stu-id="e2a1e-116">Child Elements</span></span>  
 <span data-ttu-id="e2a1e-117">无。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2a1e-118">父元素</span><span class="sxs-lookup"><span data-stu-id="e2a1e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e2a1e-119">元素</span><span class="sxs-lookup"><span data-stu-id="e2a1e-119">Element</span></span>|<span data-ttu-id="e2a1e-120">描述</span><span class="sxs-lookup"><span data-stu-id="e2a1e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2a1e-121">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="e2a1e-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="e2a1e-122">定义管理员运行时检查和控制的 WCF 设置。</span><span class="sxs-lookup"><span data-stu-id="e2a1e-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2a1e-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="e2a1e-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="e2a1e-124">端到端跟踪</span><span class="sxs-lookup"><span data-stu-id="e2a1e-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
