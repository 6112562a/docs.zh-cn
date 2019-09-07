---
title: <factorySettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
ms.openlocfilehash: 48731e7ed8aaf7d8d543f3a303577480a29588ea
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398749"
---
# <a name="factorysettings"></a><span data-ttu-id="69f93-101">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="69f93-101">\<factorySettings></span></span>
<span data-ttu-id="69f93-102">指定通道工厂缓存的设置。</span><span class="sxs-lookup"><span data-stu-id="69f93-102">Specifies the settings of the channel factory cache.</span></span>  
  
<span data-ttu-id="69f93-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="69f93-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="69f93-104">&nbsp;&nbsp;[ **\<主板.>** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="69f93-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="69f93-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行为 >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="69f93-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="69f93-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="69f93-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="69f93-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行为 >** ](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="69f93-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="69f93-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sendMessageChannelCache >** ](sendmessagechannelcache.md)</span><span class="sxs-lookup"><span data-stu-id="69f93-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sendMessageChannelCache>**](sendmessagechannelcache.md)</span></span>\
<span data-ttu-id="69f93-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<factorySettings >**</span><span class="sxs-lookup"><span data-stu-id="69f93-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<factorySettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69f93-110">语法</span><span class="sxs-lookup"><span data-stu-id="69f93-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <factorySettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69f93-111">特性和元素</span><span class="sxs-lookup"><span data-stu-id="69f93-111">Attributes and Elements</span></span>  
 <span data-ttu-id="69f93-112">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="69f93-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69f93-113">特性</span><span class="sxs-lookup"><span data-stu-id="69f93-113">Attributes</span></span>  
  
|<span data-ttu-id="69f93-114">特性</span><span class="sxs-lookup"><span data-stu-id="69f93-114">Attribute</span></span>|<span data-ttu-id="69f93-115">描述</span><span class="sxs-lookup"><span data-stu-id="69f93-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="69f93-116">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="69f93-116">idleTimeout</span></span>|<span data-ttu-id="69f93-117">一个 TimeSpan 值，指定对象在被释放之前可在缓存中保持空闲的最大时间间隔。</span><span class="sxs-lookup"><span data-stu-id="69f93-117">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="69f93-118">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="69f93-118">leaseTimeout</span></span>|<span data-ttu-id="69f93-119">一个 TimeSpan 值，该值指定从缓存中删除对象之前的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="69f93-119">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="69f93-120">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="69f93-120">maxItemsInCache</span></span>|<span data-ttu-id="69f93-121">一个整数，指定可以位于缓存中的最大对象数。</span><span class="sxs-lookup"><span data-stu-id="69f93-121">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69f93-122">子元素</span><span class="sxs-lookup"><span data-stu-id="69f93-122">Child Elements</span></span>  
 <span data-ttu-id="69f93-123">无。</span><span class="sxs-lookup"><span data-stu-id="69f93-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69f93-124">父元素</span><span class="sxs-lookup"><span data-stu-id="69f93-124">Parent Elements</span></span>  
  
|<span data-ttu-id="69f93-125">元素</span><span class="sxs-lookup"><span data-stu-id="69f93-125">Element</span></span>|<span data-ttu-id="69f93-126">描述</span><span class="sxs-lookup"><span data-stu-id="69f93-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69f93-127">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="69f93-127">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="69f93-128">一种服务行为，可用于自定义缓存共享级别、通道工厂缓存的设置，以及使用发送消息传递活动将消息发送到服务终结点的工作流的通道缓存的设置。</span><span class="sxs-lookup"><span data-stu-id="69f93-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69f93-129">备注</span><span class="sxs-lookup"><span data-stu-id="69f93-129">Remarks</span></span>  
 <span data-ttu-id="69f93-130">此服务行为适用于将消息发送给服务终结点的工作流。</span><span class="sxs-lookup"><span data-stu-id="69f93-130">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="69f93-131">这些工作流通常是客户端工作流，但也可以是在 <xref:System.ServiceModel.WorkflowServiceHost> 中承载的工作流服务。</span><span class="sxs-lookup"><span data-stu-id="69f93-131">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="69f93-132">默认情况下，在 <xref:System.ServiceModel.WorkflowServiceHost> 承载的工作流中，由 <xref:System.ServiceModel.Activities.Send> 消息传递活动使用的缓存可在 <xref:System.ServiceModel.WorkflowServiceHost> 中的所有工作流实例中共享（主机级缓存）。</span><span class="sxs-lookup"><span data-stu-id="69f93-132">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="69f93-133">对于未由 <xref:System.ServiceModel.WorkflowServiceHost> 承载的客户端工作流，缓存仅对该工作流实例可用（实例级缓存）。</span><span class="sxs-lookup"><span data-stu-id="69f93-133">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="69f93-134">对于已在配置中定义了终结点的工作流中的所有 Send 活动，默认情况下为禁用缓存。</span><span class="sxs-lookup"><span data-stu-id="69f93-134">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="69f93-135">有关如何更改通道工厂和通道缓存的默认缓存共享级别和缓存设置的详细信息，请参阅[更改发送活动的缓存共享级别](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="69f93-135">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69f93-136">示例</span><span class="sxs-lookup"><span data-stu-id="69f93-136">Example</span></span>  
 <span data-ttu-id="69f93-137">在承载的工作流服务中，可以在应用程序配置文件中指定工厂缓存和通道缓存设置。</span><span class="sxs-lookup"><span data-stu-id="69f93-137">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="69f93-138">为此，应添加一个包含工厂和通道缓存的缓存设置的服务行为，并将此服务行为添加到您的服务中。</span><span class="sxs-lookup"><span data-stu-id="69f93-138">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="69f93-139">下面的示例显示了配置文件的内容，其中包含具有`MyChannelCacheBehavior`自定义工厂缓存和通道缓存设置的服务行为。</span><span class="sxs-lookup"><span data-stu-id="69f93-139">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="69f93-140">此服务行为通过`behaviorConfiguration`属性添加到服务。</span><span class="sxs-lookup"><span data-stu-id="69f93-140">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69f93-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="69f93-141">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="69f93-142">更改发送活动的缓存共享级别</span><span class="sxs-lookup"><span data-stu-id="69f93-142">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
