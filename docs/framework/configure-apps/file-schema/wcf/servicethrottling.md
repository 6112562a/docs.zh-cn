---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 77ed5e91f09d9e658deeb7996baaca445b4e0c90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937106"
---
# <a name="servicethrottling"></a><span data-ttu-id="7220f-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="7220f-101">\<serviceThrottling></span></span>
<span data-ttu-id="7220f-102">指定 Windows Communication Foundation (WCF) 服务的限制机制。</span><span class="sxs-lookup"><span data-stu-id="7220f-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="7220f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7220f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7220f-104">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="7220f-104">\<behaviors></span></span>  
<span data-ttu-id="7220f-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7220f-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="7220f-106">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="7220f-106">\<behavior></span></span>  
<span data-ttu-id="7220f-107">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="7220f-107">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7220f-108">语法</span><span class="sxs-lookup"><span data-stu-id="7220f-108">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7220f-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="7220f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7220f-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7220f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7220f-111">特性</span><span class="sxs-lookup"><span data-stu-id="7220f-111">Attributes</span></span>  
  
|<span data-ttu-id="7220f-112">特性</span><span class="sxs-lookup"><span data-stu-id="7220f-112">Attribute</span></span>|<span data-ttu-id="7220f-113">描述</span><span class="sxs-lookup"><span data-stu-id="7220f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7220f-114">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="7220f-114">maxConcurrentCalls</span></span>|<span data-ttu-id="7220f-115">一个正整数，用于限制当前在整个 <xref:System.ServiceModel.ServiceHost> 中处理的消息数目。</span><span class="sxs-lookup"><span data-stu-id="7220f-115">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="7220f-116">超出限制的调用会进行排队。</span><span class="sxs-lookup"><span data-stu-id="7220f-116">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="7220f-117">将此值设置为 0 与将其设置为 Int32.MaxValue 等效。</span><span class="sxs-lookup"><span data-stu-id="7220f-117">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="7220f-118">默认值是 16 \* 处理器计数。</span><span class="sxs-lookup"><span data-stu-id="7220f-118">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="7220f-119">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="7220f-119">maxConcurrentInstances</span></span>|<span data-ttu-id="7220f-120">一个正整数，用于限制在整个 <xref:System.ServiceModel.InstanceContext> 中一次执行的 <xref:System.ServiceModel.ServiceHost> 对象数。</span><span class="sxs-lookup"><span data-stu-id="7220f-120">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="7220f-121">用于创建其他实例的请求将会排队，并在出现低于该限值的槽时完成。</span><span class="sxs-lookup"><span data-stu-id="7220f-121">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="7220f-122">默认值是 maxConcurrentSessions 和 MaxConcurrentCalls 的和</span><span class="sxs-lookup"><span data-stu-id="7220f-122">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="7220f-123">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="7220f-123">maxConcurrentSessions</span></span>|<span data-ttu-id="7220f-124">一个正整数，用于限制 <xref:System.ServiceModel.ServiceHost> 对象可以接受的会话数。</span><span class="sxs-lookup"><span data-stu-id="7220f-124">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="7220f-125">此服务将接受超出限制的连接，但是，只有处于限制范围之内的通道处于活动状态（会从此通道中读取消息）。</span><span class="sxs-lookup"><span data-stu-id="7220f-125">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="7220f-126">将此值设置为 0 与将其设置为 Int32.MaxValue 等效。</span><span class="sxs-lookup"><span data-stu-id="7220f-126">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="7220f-127">默认值是 100 \* 处理器计数。</span><span class="sxs-lookup"><span data-stu-id="7220f-127">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7220f-128">子元素</span><span class="sxs-lookup"><span data-stu-id="7220f-128">Child Elements</span></span>  
 <span data-ttu-id="7220f-129">无。</span><span class="sxs-lookup"><span data-stu-id="7220f-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7220f-130">父元素</span><span class="sxs-lookup"><span data-stu-id="7220f-130">Parent Elements</span></span>  
  
|<span data-ttu-id="7220f-131">元素</span><span class="sxs-lookup"><span data-stu-id="7220f-131">Element</span></span>|<span data-ttu-id="7220f-132">描述</span><span class="sxs-lookup"><span data-stu-id="7220f-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7220f-133">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7220f-133">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7220f-134">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="7220f-134">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7220f-135">备注</span><span class="sxs-lookup"><span data-stu-id="7220f-135">Remarks</span></span>  
 <span data-ttu-id="7220f-136">限制控件会对并发调用、实例或会话的数目施加限制以防止过度使用资源。</span><span class="sxs-lookup"><span data-stu-id="7220f-136">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="7220f-137">每次达到属性值时，就会记录一个跟踪。</span><span class="sxs-lookup"><span data-stu-id="7220f-137">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="7220f-138">第一个跟踪将记录为警告。</span><span class="sxs-lookup"><span data-stu-id="7220f-138">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7220f-139">示例</span><span class="sxs-lookup"><span data-stu-id="7220f-139">Example</span></span>  
 <span data-ttu-id="7220f-140">下面的配置示例指定服务将最大并发调用数限制为 2，并将最大并发实例数限制为 10。</span><span class="sxs-lookup"><span data-stu-id="7220f-140">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="7220f-141">有关运行此示例的详细示例, 请参阅[限制](../../../wcf/samples/throttling.md)。</span><span class="sxs-lookup"><span data-stu-id="7220f-141">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="7220f-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="7220f-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="7220f-143">使用 ServiceThrottlingBehavior 控制 WCF 服务性能</span><span class="sxs-lookup"><span data-stu-id="7220f-143">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
