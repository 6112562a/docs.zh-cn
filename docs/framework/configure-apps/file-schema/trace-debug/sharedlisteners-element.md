---
title: <sharedListeners> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 69f15cc9583b397017ac30a0c567914495867c18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153316"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="cdab2-102">\<共享侦听器>元素</span><span class="sxs-lookup"><span data-stu-id="cdab2-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="cdab2-103">包含任何源或跟踪元素可以引用的侦听器。</span><span class="sxs-lookup"><span data-stu-id="cdab2-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="cdab2-104">默认情况下，这些侦听器不会接收任何跟踪，并且无法在运行时检索这些侦听器。</span><span class="sxs-lookup"><span data-stu-id="cdab2-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="cdab2-105">标识为共享侦听器的侦听器可以按名称添加到源或跟踪中。</span><span class="sxs-lookup"><span data-stu-id="cdab2-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[<span data-ttu-id="cdab2-106">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="cdab2-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="cdab2-107">&nbsp;&nbsp;[**\<系统.诊断>**](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="cdab2-107">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="cdab2-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<共享侦听器>**</span><span class="sxs-lookup"><span data-stu-id="cdab2-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdab2-109">语法</span><span class="sxs-lookup"><span data-stu-id="cdab2-109">Syntax</span></span>  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdab2-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cdab2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cdab2-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cdab2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdab2-112">属性</span><span class="sxs-lookup"><span data-stu-id="cdab2-112">Attributes</span></span>  
 <span data-ttu-id="cdab2-113">无。</span><span class="sxs-lookup"><span data-stu-id="cdab2-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cdab2-114">子元素</span><span class="sxs-lookup"><span data-stu-id="cdab2-114">Child Elements</span></span>  
  
|<span data-ttu-id="cdab2-115">元素</span><span class="sxs-lookup"><span data-stu-id="cdab2-115">Element</span></span>|<span data-ttu-id="cdab2-116">说明</span><span class="sxs-lookup"><span data-stu-id="cdab2-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdab2-117">\<添加></span><span class="sxs-lookup"><span data-stu-id="cdab2-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="cdab2-118">将侦听器添加到 `sharedListeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="cdab2-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cdab2-119">父元素</span><span class="sxs-lookup"><span data-stu-id="cdab2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="cdab2-120">元素</span><span class="sxs-lookup"><span data-stu-id="cdab2-120">Element</span></span>|<span data-ttu-id="cdab2-121">说明</span><span class="sxs-lookup"><span data-stu-id="cdab2-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="cdab2-122">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="cdab2-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="cdab2-123">为 ASP.NET 配置节指定根元素。</span><span class="sxs-lookup"><span data-stu-id="cdab2-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdab2-124">备注</span><span class="sxs-lookup"><span data-stu-id="cdab2-124">Remarks</span></span>  
 <span data-ttu-id="cdab2-125">将侦听器添加到共享侦听器集合不会使其成为活动侦听器。</span><span class="sxs-lookup"><span data-stu-id="cdab2-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="cdab2-126">仍必须通过将其添加到该跟踪元素`Listeners`的集合并将其添加到跟踪源或跟踪中。</span><span class="sxs-lookup"><span data-stu-id="cdab2-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="cdab2-127">.NET 框架中的侦听器类派生自<xref:System.Diagnostics.TraceListener>类。</span><span class="sxs-lookup"><span data-stu-id="cdab2-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="cdab2-128">此元素可用于计算机配置文件 （Machine.config） 和应用程序配置文件。</span><span class="sxs-lookup"><span data-stu-id="cdab2-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdab2-129">示例</span><span class="sxs-lookup"><span data-stu-id="cdab2-129">Example</span></span>  
 <span data-ttu-id="cdab2-130">下面的示例演示如何使用`<sharedListeners>`元素将侦听器`console`添加到 和`Listeners`<xref:System.Diagnostics.TraceSource><xref:System.Diagnostics.Trace>类的集合。</span><span class="sxs-lookup"><span data-stu-id="cdab2-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="cdab2-131">控制台跟踪侦听器通过调用<xref:System.Diagnostics.TraceSource>或<xref:System.Diagnostics.Trace>向 向 控制台写入跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="cdab2-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="cdab2-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cdab2-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="cdab2-133">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="cdab2-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="cdab2-134">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="cdab2-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
