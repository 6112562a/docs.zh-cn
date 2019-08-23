---
title: <activityStateQuery>WCF 的
ms.date: 03/30/2017
ms.assetid: d6cdc04b-6f3a-4097-a623-ee4a1be3b5c4
ms.openlocfilehash: ce7505896b9c5bb605bb0f67d735cb324f4fd493
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926899"
---
# <a name="activitystatequery-of-wcf"></a><span data-ttu-id="dad4d-102">\<WCF 的 activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="dad4d-102">\<activityStateQuery> of WCF</span></span>

<span data-ttu-id="dad4d-103">表示一个查询，该查询用于跟踪构成工作流实例的活动的生命周期更改。</span><span class="sxs-lookup"><span data-stu-id="dad4d-103">Represents a query that is used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="dad4d-104">例如, 你可能想要跟踪每次在工作流实例中完成 "发送电子邮件" 活动的时间。</span><span class="sxs-lookup"><span data-stu-id="dad4d-104">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="dad4d-105">跟踪参与者需要用此查询来订阅活动状态记录对象。</span><span class="sxs-lookup"><span data-stu-id="dad4d-105">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="dad4d-106">在 ActivityStates 中指定了要订阅的可用状态。</span><span class="sxs-lookup"><span data-stu-id="dad4d-106">The available states to subscribe to are specified in ActivityStates.</span></span>  
  
<span data-ttu-id="dad4d-107">有关跟踪配置文件查询的详细信息, 请参阅[跟踪配置文件](../../../windows-workflow-foundation/tracking-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="dad4d-107">For more information on tracking profile queries, see [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>

<span data-ttu-id="dad4d-108">\<system.serviceModel> \<tracking></span><span class="sxs-lookup"><span data-stu-id="dad4d-108">\<system.serviceModel> \<tracking></span></span>  
<span data-ttu-id="dad4d-109">\<profiles> \<trackingProfile></span><span class="sxs-lookup"><span data-stu-id="dad4d-109">\<profiles> \<trackingProfile></span></span>  
<span data-ttu-id="dad4d-110">\<工作流 ></span><span class="sxs-lookup"><span data-stu-id="dad4d-110">\<workflow></span></span>  
<span data-ttu-id="dad4d-111">\<activityStateQueries></span><span class="sxs-lookup"><span data-stu-id="dad4d-111">\<activityStateQueries></span></span>  
<span data-ttu-id="dad4d-112">\<activityStateQuery></span><span class="sxs-lookup"><span data-stu-id="dad4d-112">\<activityStateQuery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dad4d-113">语法</span><span class="sxs-lookup"><span data-stu-id="dad4d-113">Syntax</span></span>  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <activityStateQueries>
          <activityStateQuery activityName="String">
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String" />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQuery>
        </activityStateQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dad4d-114">特性和元素</span><span class="sxs-lookup"><span data-stu-id="dad4d-114">Attributes and elements</span></span>  

<span data-ttu-id="dad4d-115">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="dad4d-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dad4d-116">特性</span><span class="sxs-lookup"><span data-stu-id="dad4d-116">Attributes</span></span>  
  
|<span data-ttu-id="dad4d-117">特性</span><span class="sxs-lookup"><span data-stu-id="dad4d-117">Attribute</span></span>|<span data-ttu-id="dad4d-118">描述</span><span class="sxs-lookup"><span data-stu-id="dad4d-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dad4d-119">activityName</span><span class="sxs-lookup"><span data-stu-id="dad4d-119">activityName</span></span>|<span data-ttu-id="dad4d-120">一个字符串，指定要对其筛选 <xref:System.Activities.Tracking.ActivityStateRecord> 实例的活动的名称。</span><span class="sxs-lookup"><span data-stu-id="dad4d-120">A string that specifies the name of the activity to filter <xref:System.Activities.Tracking.ActivityStateRecord> instances on.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dad4d-121">子元素</span><span class="sxs-lookup"><span data-stu-id="dad4d-121">Child elements</span></span>  
  
|<span data-ttu-id="dad4d-122">元素</span><span class="sxs-lookup"><span data-stu-id="dad4d-122">Element</span></span>|<span data-ttu-id="dad4d-123">描述</span><span class="sxs-lookup"><span data-stu-id="dad4d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dad4d-124">\<参数 ></span><span class="sxs-lookup"><span data-stu-id="dad4d-124">\<arguments></span></span>](../windows-workflow-foundation/arguments.md)|<span data-ttu-id="dad4d-125">与此活动查询关联的自变量的集合。</span><span class="sxs-lookup"><span data-stu-id="dad4d-125">A collection of arguments associated with this activity query.</span></span>|  
|[<span data-ttu-id="dad4d-126">\<states></span><span class="sxs-lookup"><span data-stu-id="dad4d-126">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="dad4d-127">一个配置元素集合，这些元素包含应为其发出跟踪记录的已订阅活动的状态。</span><span class="sxs-lookup"><span data-stu-id="dad4d-127">A collection of configuration elements that contain the states of the subscribed activity for which a tracking record should be emitted.</span></span>|  
|[<span data-ttu-id="dad4d-128">\<states></span><span class="sxs-lookup"><span data-stu-id="dad4d-128">\<states></span></span>](../windows-workflow-foundation/states.md)|<span data-ttu-id="dad4d-129">与此活动查询关联的变量的集合。</span><span class="sxs-lookup"><span data-stu-id="dad4d-129">A collection of variables associated with this activity query.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dad4d-130">父元素</span><span class="sxs-lookup"><span data-stu-id="dad4d-130">Parent elements</span></span>  
  
|<span data-ttu-id="dad4d-131">元素</span><span class="sxs-lookup"><span data-stu-id="dad4d-131">Element</span></span>|<span data-ttu-id="dad4d-132">描述</span><span class="sxs-lookup"><span data-stu-id="dad4d-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dad4d-133">\<faultPropagationQuery></span><span class="sxs-lookup"><span data-stu-id="dad4d-133">\<faultPropagationQuery></span></span>](../windows-workflow-foundation/faultpropagationquery.md)|<span data-ttu-id="dad4d-134">表示一个配置元素列表，这些元素用于跟踪父活动取消子活动的请求。</span><span class="sxs-lookup"><span data-stu-id="dad4d-134">Represents a list of configuration elements that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="dad4d-135">跟踪参与者需要用此查询来订阅取消请求记录对象。</span><span class="sxs-lookup"><span data-stu-id="dad4d-135">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dad4d-136">备注</span><span class="sxs-lookup"><span data-stu-id="dad4d-136">Remarks</span></span>

<span data-ttu-id="dad4d-137">ActivityStateQuery 的一项独特功能是能够在跟踪工作流的执行时提取数据。</span><span class="sxs-lookup"><span data-stu-id="dad4d-137">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="dad4d-138">这在访问跟踪记录后续执行时可提供其他上下文。</span><span class="sxs-lookup"><span data-stu-id="dad4d-138">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="dad4d-139">您可以使用[ \<参数 >](../windows-workflow-foundation/arguments.md)、 [ \<状态 >](../windows-workflow-foundation/states.md)和[ \<状态 >](../windows-workflow-foundation/states.md)元素从工作流中的任何活动提取任何变量或参数。下面的示例演示在发出活动的`Closed`跟踪记录时提取变量和参数的活动状态查询。</span><span class="sxs-lookup"><span data-stu-id="dad4d-139">You can use the [\<arguments>](../windows-workflow-foundation/arguments.md), [\<states>](../windows-workflow-foundation/states.md) and [\<states>](../windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="dad4d-140">变量和参数只能通过 ActivityStateRecord 提取, 因此使用[ \<activityStateQuery >](../windows-workflow-foundation/activitystatequery.md)在跟踪配置文件内进行订阅。</span><span class="sxs-lookup"><span data-stu-id="dad4d-140">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../windows-workflow-foundation/activitystatequery.md).</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed" />
  </states>
  <variables>
    <variable name="FromAddress" />
  </variables>
  <arguments>
    <argument name="Result" />
  </arguments>
</activityStateQuery>
```  
  
## <a name="see-also"></a><span data-ttu-id="dad4d-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="dad4d-141">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElement>
- <xref:System.Activities.Tracking.ActivityStateQuery>
- [<span data-ttu-id="dad4d-142">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="dad4d-142">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="dad4d-143">跟踪配置文件</span><span class="sxs-lookup"><span data-stu-id="dad4d-143">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
