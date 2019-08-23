---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: de53eb16d53d1e37209e36f2f6bfdc4bdfd84465
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947549"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="eb43a-101">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="eb43a-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="eb43a-102">一种服务行为, 可用于自定义缓存共享级别、通道工厂缓存的设置, 以及使用发送消息传递活动将消息发送到服务终结点的工作流的通道缓存的设置。</span><span class="sxs-lookup"><span data-stu-id="eb43a-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="eb43a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="eb43a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="eb43a-104">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="eb43a-104">\<behaviors></span></span>  
<span data-ttu-id="eb43a-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="eb43a-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="eb43a-106">\<行为 ></span><span class="sxs-lookup"><span data-stu-id="eb43a-106">\<behavior></span></span>  
<span data-ttu-id="eb43a-107">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="eb43a-107">\<sendMessageChannelCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb43a-108">语法</span><span class="sxs-lookup"><span data-stu-id="eb43a-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
        <factorySettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb43a-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="eb43a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eb43a-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="eb43a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb43a-111">特性</span><span class="sxs-lookup"><span data-stu-id="eb43a-111">Attributes</span></span>  
  
|<span data-ttu-id="eb43a-112">特性</span><span class="sxs-lookup"><span data-stu-id="eb43a-112">Attribute</span></span>|<span data-ttu-id="eb43a-113">描述</span><span class="sxs-lookup"><span data-stu-id="eb43a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb43a-114">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="eb43a-114">allowUnsafeCaching</span></span>|<span data-ttu-id="eb43a-115">一个布尔值，该值指示是否启用缓存。</span><span class="sxs-lookup"><span data-stu-id="eb43a-115">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="eb43a-116">如果工作流服务具有自定义绑定或自定义行为，缓存会变得不安全，因此默认情况下禁用缓存。</span><span class="sxs-lookup"><span data-stu-id="eb43a-116">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="eb43a-117">但是, 如果要启用缓存, 请将此属性设置为**true**。</span><span class="sxs-lookup"><span data-stu-id="eb43a-117">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb43a-118">子元素</span><span class="sxs-lookup"><span data-stu-id="eb43a-118">Child Elements</span></span>  
  
|<span data-ttu-id="eb43a-119">元素</span><span class="sxs-lookup"><span data-stu-id="eb43a-119">Element</span></span>|<span data-ttu-id="eb43a-120">描述</span><span class="sxs-lookup"><span data-stu-id="eb43a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb43a-121">\<channelSettings></span><span class="sxs-lookup"><span data-stu-id="eb43a-121">\<channelSettings></span></span>](channelsettings.md)|<span data-ttu-id="eb43a-122">指定通道缓存的设置。</span><span class="sxs-lookup"><span data-stu-id="eb43a-122">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="eb43a-123">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="eb43a-123">\<factorySettings></span></span>](factorysettings.md)|<span data-ttu-id="eb43a-124">指定通道工厂缓存的设置。</span><span class="sxs-lookup"><span data-stu-id="eb43a-124">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eb43a-125">父元素</span><span class="sxs-lookup"><span data-stu-id="eb43a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="eb43a-126">元素</span><span class="sxs-lookup"><span data-stu-id="eb43a-126">Element</span></span>|<span data-ttu-id="eb43a-127">描述</span><span class="sxs-lookup"><span data-stu-id="eb43a-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb43a-128">\<serviceBehaviors > 的\<行为 ></span><span class="sxs-lookup"><span data-stu-id="eb43a-128">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="eb43a-129">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="eb43a-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb43a-130">备注</span><span class="sxs-lookup"><span data-stu-id="eb43a-130">Remarks</span></span>  
 <span data-ttu-id="eb43a-131">此服务行为适用于将消息发送给服务终结点的工作流。</span><span class="sxs-lookup"><span data-stu-id="eb43a-131">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="eb43a-132">这些工作流通常是客户端工作流，但也可以是在 <xref:System.ServiceModel.WorkflowServiceHost> 中承载的工作流服务。</span><span class="sxs-lookup"><span data-stu-id="eb43a-132">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="eb43a-133">默认情况下，在 <xref:System.ServiceModel.WorkflowServiceHost> 承载的工作流中，由 <xref:System.ServiceModel.Activities.Send> 消息传递活动使用的缓存可在 <xref:System.ServiceModel.WorkflowServiceHost> 中的所有工作流实例中共享（主机级缓存）。</span><span class="sxs-lookup"><span data-stu-id="eb43a-133">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="eb43a-134">对于未由 <xref:System.ServiceModel.WorkflowServiceHost> 承载的客户端工作流，缓存仅对该工作流实例可用（实例级缓存）。</span><span class="sxs-lookup"><span data-stu-id="eb43a-134">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="eb43a-135">对于已在配置中定义了终结点的工作流中的所有 Send 活动，默认情况下为禁用缓存。</span><span class="sxs-lookup"><span data-stu-id="eb43a-135">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="eb43a-136">有关如何更改通道工厂和通道缓存的默认缓存共享级别和缓存设置的详细信息, 请参阅[更改发送活动的缓存共享级别](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="eb43a-136">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb43a-137">示例</span><span class="sxs-lookup"><span data-stu-id="eb43a-137">Example</span></span>  
 <span data-ttu-id="eb43a-138">在承载的工作流服务中，可以在应用程序配置文件中指定工厂缓存和通道缓存设置。</span><span class="sxs-lookup"><span data-stu-id="eb43a-138">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="eb43a-139">为此，应添加一个包含工厂和通道缓存的缓存设置的服务行为，并将此服务行为添加到您的服务中。</span><span class="sxs-lookup"><span data-stu-id="eb43a-139">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="eb43a-140">下面的示例显示了配置文件的内容, 其中包含具有`MyChannelCacheBehavior`自定义工厂缓存和通道缓存设置的服务行为。</span><span class="sxs-lookup"><span data-stu-id="eb43a-140">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="eb43a-141">此服务行为通过`behaviorConfiguration`属性添加到服务。</span><span class="sxs-lookup"><span data-stu-id="eb43a-141">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>    
  <system.serviceModel>  
    <!-- List of other config sections here -->   
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->   
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb43a-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="eb43a-142">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="eb43a-143">更改发送活动的缓存共享级别</span><span class="sxs-lookup"><span data-stu-id="eb43a-143">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
