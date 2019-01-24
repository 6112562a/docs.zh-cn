---
title: '&lt;sendMessageChannelCache&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: dce81dec9067c25fc85b62cc4aa5860499347ab2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657345"
---
# <a name="ltsendmessagechannelcachegt"></a><span data-ttu-id="8e659-102">&lt;sendMessageChannelCache&gt;</span><span class="sxs-lookup"><span data-stu-id="8e659-102">&lt;sendMessageChannelCache&gt;</span></span>
<span data-ttu-id="8e659-103">一种服务行为，允许自定义的缓存共享级别、 通道工厂缓存的设置和用于将消息发送到服务终结点使用 Send 消息传递活动的工作流的通道缓存设置。</span><span class="sxs-lookup"><span data-stu-id="8e659-103">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="8e659-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8e659-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8e659-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="8e659-105">\<behaviors></span></span>  
<span data-ttu-id="8e659-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="8e659-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="8e659-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="8e659-107">\<behavior></span></span>  
<span data-ttu-id="8e659-108">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="8e659-108">\<sendMessageChannelCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e659-109">语法</span><span class="sxs-lookup"><span data-stu-id="8e659-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e659-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="8e659-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8e659-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8e659-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e659-112">特性</span><span class="sxs-lookup"><span data-stu-id="8e659-112">Attributes</span></span>  
  
|<span data-ttu-id="8e659-113">特性</span><span class="sxs-lookup"><span data-stu-id="8e659-113">Attribute</span></span>|<span data-ttu-id="8e659-114">描述</span><span class="sxs-lookup"><span data-stu-id="8e659-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e659-115">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="8e659-115">allowUnsafeCaching</span></span>|<span data-ttu-id="8e659-116">一个布尔值，该值指示是否启用缓存。</span><span class="sxs-lookup"><span data-stu-id="8e659-116">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="8e659-117">如果工作流服务具有自定义绑定或自定义行为，缓存会变得不安全，因此默认情况下禁用缓存。</span><span class="sxs-lookup"><span data-stu-id="8e659-117">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="8e659-118">但是，如果你想要启用缓存在此属性设置为 **，则返回 true**。</span><span class="sxs-lookup"><span data-stu-id="8e659-118">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e659-119">子元素</span><span class="sxs-lookup"><span data-stu-id="8e659-119">Child Elements</span></span>  
  
|<span data-ttu-id="8e659-120">元素</span><span class="sxs-lookup"><span data-stu-id="8e659-120">Element</span></span>|<span data-ttu-id="8e659-121">描述</span><span class="sxs-lookup"><span data-stu-id="8e659-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e659-122">\<channelSettings></span><span class="sxs-lookup"><span data-stu-id="8e659-122">\<channelSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/channelsettings.md)|<span data-ttu-id="8e659-123">指定通道缓存的设置。</span><span class="sxs-lookup"><span data-stu-id="8e659-123">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="8e659-124">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="8e659-124">\<factorySettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/factorysettings.md)|<span data-ttu-id="8e659-125">指定通道工厂缓存的设置。</span><span class="sxs-lookup"><span data-stu-id="8e659-125">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8e659-126">父元素</span><span class="sxs-lookup"><span data-stu-id="8e659-126">Parent Elements</span></span>  
  
|<span data-ttu-id="8e659-127">元素</span><span class="sxs-lookup"><span data-stu-id="8e659-127">Element</span></span>|<span data-ttu-id="8e659-128">描述</span><span class="sxs-lookup"><span data-stu-id="8e659-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8e659-129">\<行为 > 的\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="8e659-129">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="8e659-130">指定行为元素。</span><span class="sxs-lookup"><span data-stu-id="8e659-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e659-131">备注</span><span class="sxs-lookup"><span data-stu-id="8e659-131">Remarks</span></span>  
 <span data-ttu-id="8e659-132">此服务行为适用于将消息发送给服务终结点的工作流。</span><span class="sxs-lookup"><span data-stu-id="8e659-132">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="8e659-133">这些工作流通常是客户端工作流，但也可以是在 <xref:System.ServiceModel.WorkflowServiceHost> 中承载的工作流服务。</span><span class="sxs-lookup"><span data-stu-id="8e659-133">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="8e659-134">默认情况下，在 <xref:System.ServiceModel.WorkflowServiceHost> 承载的工作流中，由 <xref:System.ServiceModel.Activities.Send> 消息传递活动使用的缓存可在 <xref:System.ServiceModel.WorkflowServiceHost> 中的所有工作流实例中共享（主机级缓存）。</span><span class="sxs-lookup"><span data-stu-id="8e659-134">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="8e659-135">对于未由 <xref:System.ServiceModel.WorkflowServiceHost> 承载的客户端工作流，缓存仅对该工作流实例可用（实例级缓存）。</span><span class="sxs-lookup"><span data-stu-id="8e659-135">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="8e659-136">对于已在配置中定义了终结点的工作流中的所有 Send 活动，默认情况下为禁用缓存。</span><span class="sxs-lookup"><span data-stu-id="8e659-136">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="8e659-137">有关如何更改默认的缓存共享级别以及通道工厂和通道缓存的缓存设置的详细信息，请参阅[更改发送活动的缓存共享级别](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="8e659-137">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e659-138">示例</span><span class="sxs-lookup"><span data-stu-id="8e659-138">Example</span></span>  
 <span data-ttu-id="8e659-139">在承载的工作流服务中，可以在应用程序配置文件中指定工厂缓存和通道缓存设置。</span><span class="sxs-lookup"><span data-stu-id="8e659-139">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="8e659-140">为此，应添加一个包含工厂和通道缓存的缓存设置的服务行为，并将此服务行为添加到您的服务中。</span><span class="sxs-lookup"><span data-stu-id="8e659-140">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="8e659-141">下面的示例显示了包含的配置文件的内容**MyChannelCacheBehavior**服务使用自定义工厂缓存和通道缓存设置的行为。</span><span class="sxs-lookup"><span data-stu-id="8e659-141">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="8e659-142">此服务行为添加到服务**behaviorConfiguarion**属性。</span><span class="sxs-lookup"><span data-stu-id="8e659-142">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e659-143">请参阅</span><span class="sxs-lookup"><span data-stu-id="8e659-143">See also</span></span>
- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="8e659-144">更改发送活动的缓存共享级别</span><span class="sxs-lookup"><span data-stu-id="8e659-144">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
