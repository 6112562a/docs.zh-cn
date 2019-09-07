---
title: <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560dd0bb-f9fb-423c-8857-2101a3654b06
ms.openlocfilehash: 368b37f3ff10b660260ddd5735c70b8d72063e11
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398701"
---
# <a name="participants"></a><span data-ttu-id="fcf2b-101">\<participants></span><span class="sxs-lookup"><span data-stu-id="fcf2b-101">\<participants></span></span>
<span data-ttu-id="fcf2b-102">配置一列跟踪参与者，它们侦听直接从运行时发出的跟踪记录，并按照它们的任何方式处理这些记录。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-102">Configure a list of tracking participants that listen to the tracking records being emitted from the runtime directly and process them in whatever way they are configured.</span></span> <span data-ttu-id="fcf2b-103">这包括写入特定输出（例如，文件、控制台、ETW）、处理/聚合记录或可能需要的任何其他组合。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-103">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="fcf2b-104">有关工作流跟踪和跟踪参与者的详细信息，请参阅[工作流跟踪和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)跟踪和[跟踪参与者](../../../windows-workflow-foundation/tracking-participants.md)。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-104">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
<span data-ttu-id="fcf2b-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fcf2b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fcf2b-106">&nbsp;&nbsp;[ **\<主板.>** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="fcf2b-106">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="fcf2b-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<跟踪 >** ](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="fcf2b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="fcf2b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<参与者 >**</span><span class="sxs-lookup"><span data-stu-id="fcf2b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<participants>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcf2b-109">语法</span><span class="sxs-lookup"><span data-stu-id="fcf2b-109">Syntax</span></span>  
  
```xml
<tracking>
  <participants>
    <add name="String" 
         profileName="String" 
         type="String" />
  </participants>
</tracking>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcf2b-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="fcf2b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fcf2b-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcf2b-112">特性</span><span class="sxs-lookup"><span data-stu-id="fcf2b-112">Attributes</span></span>  
 <span data-ttu-id="fcf2b-113">无。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fcf2b-114">子元素</span><span class="sxs-lookup"><span data-stu-id="fcf2b-114">Child Elements</span></span>  
  
|<span data-ttu-id="fcf2b-115">元素</span><span class="sxs-lookup"><span data-stu-id="fcf2b-115">Element</span></span>|<span data-ttu-id="fcf2b-116">描述</span><span class="sxs-lookup"><span data-stu-id="fcf2b-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fcf2b-117">\<add></span><span class="sxs-lookup"><span data-stu-id="fcf2b-117">\<add></span></span>](add-of-participants.md)|<span data-ttu-id="fcf2b-118">包含跟踪参与者的设置。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-118">Contains settings for a tracking participant.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fcf2b-119">父元素</span><span class="sxs-lookup"><span data-stu-id="fcf2b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="fcf2b-120">元素</span><span class="sxs-lookup"><span data-stu-id="fcf2b-120">Element</span></span>|<span data-ttu-id="fcf2b-121">描述</span><span class="sxs-lookup"><span data-stu-id="fcf2b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fcf2b-122">\<tracking></span><span class="sxs-lookup"><span data-stu-id="fcf2b-122">\<tracking></span></span>](tracking.md)|<span data-ttu-id="fcf2b-123">表示一个配置节，用于定义工作流服务的跟踪设置。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-123">Represents a configuration section for defining tracking settings for a workflow service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcf2b-124">备注</span><span class="sxs-lookup"><span data-stu-id="fcf2b-124">Remarks</span></span>  
 <span data-ttu-id="fcf2b-125">跟踪参与者用于获取从工作流发出的跟踪数据并将其存储在不同的媒体中。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="fcf2b-126">同样，也可以在跟踪参与者中执行对跟踪记录的任何后续处理。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="fcf2b-127">多个跟踪参与者可同时使用跟踪事件。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="fcf2b-128">每个跟踪参与者都可与不同的跟踪配置文件关联。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="fcf2b-129">提供了将跟踪记录写入 ETW 会话的标准跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="fcf2b-130">通过在配置文件中添加特定于跟踪的行为，可以对工作流服务配置参与者。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="fcf2b-131">通过启用 ETW 跟踪参与者，可以在事件查看器中查看跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="fcf2b-132">如果这不能满足您的需求，您还可以编写自定义跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcf2b-133">示例</span><span class="sxs-lookup"><span data-stu-id="fcf2b-133">Example</span></span>  
 <span data-ttu-id="fcf2b-134">下面的配置示例演示在 Web.config 文件中配置的标准 ETW 跟踪参与者。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="fcf2b-135">Etw 跟踪参与者用于将跟踪记录写入 etw 的提供程序 Id 在 "  **\<诊断 >** " 部分中定义。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the **\<diagnostics>** section.</span></span> <span data-ttu-id="fcf2b-136">跟踪参与者具有一个与其关联的配置文件，用来指定跟踪参与者已订阅的跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="fcf2b-137">这由 **profileName** 的属性 **\<添加>** 元素。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-137">This is defined by the **profileName** attribute of the **\<add>** element.</span></span> <span data-ttu-id="fcf2b-138">定义这些后，跟踪参与者将添加到 **\<etwTracking >** 服务行为。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-138">Once these are defined, the Tracking Participant is added to the **\<etwTracking>** service behavior.</span></span> <span data-ttu-id="fcf2b-139">这会将所选跟踪参与者添加到工作流实例的扩展中，以便它们开始接收跟踪记录。</span><span class="sxs-lookup"><span data-stu-id="fcf2b-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml
<configuration>   
  <system.web>   
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>   
  </system.web>   
  <system.serviceModel>   
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />                
    <tracking>   
      <participants>   
        <add name="EtwTrackingParticipant"   
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"   
             profileName="HealthMonitoring_Tracking_Profile"/>   
      </participants>   
    </tracking>   
    <behaviors>   
      <serviceBehaviors>   
        <behavior>   
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>   
      </serviceBehaviors>   
    </behaviors>   
  </system.serviceModel>   
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fcf2b-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="fcf2b-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="fcf2b-141">工作流跟踪</span><span class="sxs-lookup"><span data-stu-id="fcf2b-141">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="fcf2b-142">跟踪参与者</span><span class="sxs-lookup"><span data-stu-id="fcf2b-142">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
