---
title: '&lt;states&gt; 的 &lt;state&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: ab483c7f-a091-4933-ba6b-708d96846d38
ms.openlocfilehash: e4eaf1cbe788018b46759efb1e9755d65b19cc60
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148285"
---
# <a name="ltstategt-of-ltstatesgt"></a><span data-ttu-id="5e676-102">&lt;states&gt; 的 &lt;state&gt;</span><span class="sxs-lookup"><span data-stu-id="5e676-102">&lt;state&gt; of &lt;states&gt;</span></span>
<span data-ttu-id="5e676-103">一个配置元素，该元素包含应为其发出跟踪记录的已订阅活动的状态。</span><span class="sxs-lookup"><span data-stu-id="5e676-103">A configuration element that contains the state of the subscribed activity for which a tracking record should be emitted.</span></span>  
  
 <span data-ttu-id="5e676-104">有关跟踪配置文件查询的详细信息，请参阅[跟踪配置文件](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="5e676-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="5e676-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5e676-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5e676-106">\<跟踪 ></span><span class="sxs-lookup"><span data-stu-id="5e676-106">\<tracking></span></span>  
<span data-ttu-id="5e676-107">\<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="5e676-107">\<trackingProfile></span></span>  
<span data-ttu-id="5e676-108">\<工作流 ></span><span class="sxs-lookup"><span data-stu-id="5e676-108">\<workflow></span></span>  
<span data-ttu-id="5e676-109">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="5e676-109">\<activityStateQueries></span></span>  
<span data-ttu-id="5e676-110">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="5e676-110">\<activityStateQuery></span></span>  
<span data-ttu-id="5e676-111">\<状态 ></span><span class="sxs-lookup"><span data-stu-id="5e676-111">\<states></span></span>  
<span data-ttu-id="5e676-112">\<状态 ></span><span class="sxs-lookup"><span data-stu-id="5e676-112">\<state></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e676-113">语法</span><span class="sxs-lookup"><span data-stu-id="5e676-113">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <states>
          <state name="String" />
        </states>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e676-114">特性和元素</span><span class="sxs-lookup"><span data-stu-id="5e676-114">Attributes and Elements</span></span>  
 <span data-ttu-id="5e676-115">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5e676-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e676-116">特性</span><span class="sxs-lookup"><span data-stu-id="5e676-116">Attributes</span></span>  
  
|<span data-ttu-id="5e676-117">特性</span><span class="sxs-lookup"><span data-stu-id="5e676-117">Attribute</span></span>|<span data-ttu-id="5e676-118">描述</span><span class="sxs-lookup"><span data-stu-id="5e676-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e676-119">name</span><span class="sxs-lookup"><span data-stu-id="5e676-119">name</span></span>|<span data-ttu-id="5e676-120">一个字符串，指定应为其发出跟踪记录的已订阅活动的状态。</span><span class="sxs-lookup"><span data-stu-id="5e676-120">A string that specifies the state of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e676-121">子元素</span><span class="sxs-lookup"><span data-stu-id="5e676-121">Child Elements</span></span>  
 <span data-ttu-id="5e676-122">无。</span><span class="sxs-lookup"><span data-stu-id="5e676-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e676-123">父元素</span><span class="sxs-lookup"><span data-stu-id="5e676-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5e676-124">元素</span><span class="sxs-lookup"><span data-stu-id="5e676-124">Element</span></span>|<span data-ttu-id="5e676-125">描述</span><span class="sxs-lookup"><span data-stu-id="5e676-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e676-126">\<状态 ></span><span class="sxs-lookup"><span data-stu-id="5e676-126">\<states></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states-of-activitystatequery.md)|<span data-ttu-id="5e676-127">一个配置元素集合，这些元素包含应为其发出跟踪记录的已订阅活动的状态。</span><span class="sxs-lookup"><span data-stu-id="5e676-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e676-128">备注</span><span class="sxs-lookup"><span data-stu-id="5e676-128">Remarks</span></span>  
 <span data-ttu-id="5e676-129">ActivityStateQuery 的一项独特功能是能够在跟踪工作流的执行时提取数据。</span><span class="sxs-lookup"><span data-stu-id="5e676-129">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="5e676-130">这在访问跟踪记录后续执行时可提供其他上下文。</span><span class="sxs-lookup"><span data-stu-id="5e676-130">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="5e676-131">可以使用[\<自变量 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md)， [\<状态 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)并[\<状态 >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md)元素提取任何变量或参数从工作流中的任何活动。</span><span class="sxs-lookup"><span data-stu-id="5e676-131">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.</span></span> <span data-ttu-id="5e676-132">下面的示例演示用于在发出活动的 `Closed` 跟踪记录时提取变量和自变量的活动状态查询。</span><span class="sxs-lookup"><span data-stu-id="5e676-132">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="5e676-133">变量和自变量只能使用 ActivityStateRecord 可以提取并因此内进行订阅跟踪配置文件使用[ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)。</span><span class="sxs-lookup"><span data-stu-id="5e676-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e676-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="5e676-134">See Also</span></span>  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>       
 <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>       
 [<span data-ttu-id="5e676-135">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="5e676-135">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="5e676-136">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="5e676-136">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
