---
title: WCF 的 &lt;activityScheduledQueries&gt;
ms.date: 03/30/2017
ms.assetid: e351329f-9676-4f11-9b19-f4bac82f36fc
ms.openlocfilehash: 5430058049e8a09c1e2a289e1f997338c23b9d94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492151"
---
# <a name="ltactivityscheduledqueriesgt-of-wcf"></a><span data-ttu-id="4e00a-102">WCF 的 &lt;activityScheduledQueries&gt;</span><span class="sxs-lookup"><span data-stu-id="4e00a-102">&lt;activityScheduledQueries&gt; of WCF</span></span>
<span data-ttu-id="4e00a-103">表示一个查询集合，这些查询用于跟踪安排给父活动来执行的活动。</span><span class="sxs-lookup"><span data-stu-id="4e00a-103">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="4e00a-104">跟踪参与者需要用此查询来订阅活动安排记录。</span><span class="sxs-lookup"><span data-stu-id="4e00a-104">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>  
  
<span data-ttu-id="4e00a-105">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span><span class="sxs-lookup"><span data-stu-id="4e00a-105">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)</span></span>  
  
<span data-ttu-id="4e00a-106">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4e00a-106">\<system.serviceModel></span></span>  
<span data-ttu-id="4e00a-107">\<tracking></span><span class="sxs-lookup"><span data-stu-id="4e00a-107">\<tracking></span></span>  
<span data-ttu-id="4e00a-108">\<配置文件 ></span><span class="sxs-lookup"><span data-stu-id="4e00a-108">\<profiles></span></span>  
<span data-ttu-id="4e00a-109">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="4e00a-109">\<trackingProfile></span></span>  
<span data-ttu-id="4e00a-110">\<workflow></span><span class="sxs-lookup"><span data-stu-id="4e00a-110">\<workflow></span></span>  
<span data-ttu-id="4e00a-111">\<activityScheduledQueries></span><span class="sxs-lookup"><span data-stu-id="4e00a-111">\<activityScheduledQueries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e00a-112">语法</span><span class="sxs-lookup"><span data-stu-id="4e00a-112">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityScheduledQueries>
          <activityScheduledQuery activityName="String"
                                  childActivityName="String" />
        </activityScheduledQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e00a-113">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4e00a-113">Attributes and elements</span></span>  

<span data-ttu-id="4e00a-114">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4e00a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e00a-115">特性</span><span class="sxs-lookup"><span data-stu-id="4e00a-115">Attributes</span></span>  

<span data-ttu-id="4e00a-116">无。</span><span class="sxs-lookup"><span data-stu-id="4e00a-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4e00a-117">子元素</span><span class="sxs-lookup"><span data-stu-id="4e00a-117">Child elements</span></span>  
  
|<span data-ttu-id="4e00a-118">元素</span><span class="sxs-lookup"><span data-stu-id="4e00a-118">Element</span></span>|<span data-ttu-id="4e00a-119">描述</span><span class="sxs-lookup"><span data-stu-id="4e00a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e00a-120">\<activityScheduledQuery></span><span class="sxs-lookup"><span data-stu-id="4e00a-120">\<activityScheduledQuery></span></span>](activityscheduledquery-of-wcf.md)|<span data-ttu-id="4e00a-121">一个查询，用于跟踪安排给父活动来执行的活动。</span><span class="sxs-lookup"><span data-stu-id="4e00a-121">A query that is used to track an activity scheduled for execution by a parent activity.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4e00a-122">父元素</span><span class="sxs-lookup"><span data-stu-id="4e00a-122">Parent elements</span></span>  
  
|<span data-ttu-id="4e00a-123">元素</span><span class="sxs-lookup"><span data-stu-id="4e00a-123">Element</span></span>|<span data-ttu-id="4e00a-124">描述</span><span class="sxs-lookup"><span data-stu-id="4e00a-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e00a-125">\<workflow></span><span class="sxs-lookup"><span data-stu-id="4e00a-125">\<workflow></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|<span data-ttu-id="4e00a-126">一个配置元素，包含 `activityDefinitionId` 属性所标识的特定工作流的所有查询。</span><span class="sxs-lookup"><span data-stu-id="4e00a-126">A configuration element that contains all queries for a specific workflow identified by the `activityDefinitionId` property.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e00a-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="4e00a-127">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityScheduledQueryElementCollection>
- <xref:System.Activities.Tracking.ActivityScheduledQuery>
- [<span data-ttu-id="4e00a-128">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="4e00a-128">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="4e00a-129">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="4e00a-129">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
