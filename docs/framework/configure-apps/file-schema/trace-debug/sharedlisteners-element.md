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
ms.openlocfilehash: 41cabcbce13409b0842cbbd625028b51d32d59d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926974"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="2c474-102">\<sharedListeners > 元素</span><span class="sxs-lookup"><span data-stu-id="2c474-102">\<sharedListeners> Element</span></span>
<span data-ttu-id="2c474-103">包含任何源或跟踪元素可以引用的侦听器。</span><span class="sxs-lookup"><span data-stu-id="2c474-103">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="2c474-104">默认情况下, 这些侦听器不会接收任何跟踪, 而且不能在运行时检索这些侦听器。</span><span class="sxs-lookup"><span data-stu-id="2c474-104">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="2c474-105">可以按名称将标识为共享侦听器的侦听器添加到源或跟踪。</span><span class="sxs-lookup"><span data-stu-id="2c474-105">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
 <span data-ttu-id="2c474-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2c474-106">\<configuration></span></span>  
<span data-ttu-id="2c474-107">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="2c474-107">\<system.diagnostics></span></span>  
<span data-ttu-id="2c474-108">\<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="2c474-108">\<sharedListeners></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c474-109">语法</span><span class="sxs-lookup"><span data-stu-id="2c474-109">Syntax</span></span>  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c474-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="2c474-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2c474-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2c474-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c474-112">特性</span><span class="sxs-lookup"><span data-stu-id="2c474-112">Attributes</span></span>  
 <span data-ttu-id="2c474-113">无。</span><span class="sxs-lookup"><span data-stu-id="2c474-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2c474-114">子元素</span><span class="sxs-lookup"><span data-stu-id="2c474-114">Child Elements</span></span>  
  
|<span data-ttu-id="2c474-115">元素</span><span class="sxs-lookup"><span data-stu-id="2c474-115">Element</span></span>|<span data-ttu-id="2c474-116">描述</span><span class="sxs-lookup"><span data-stu-id="2c474-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c474-117">\<add></span><span class="sxs-lookup"><span data-stu-id="2c474-117">\<add></span></span>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="2c474-118">将侦听器添加到 `sharedListeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="2c474-118">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c474-119">父元素</span><span class="sxs-lookup"><span data-stu-id="2c474-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2c474-120">元素</span><span class="sxs-lookup"><span data-stu-id="2c474-120">Element</span></span>|<span data-ttu-id="2c474-121">描述</span><span class="sxs-lookup"><span data-stu-id="2c474-121">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="2c474-122">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="2c474-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="2c474-123">为 ASP.NET 配置节指定根元素。</span><span class="sxs-lookup"><span data-stu-id="2c474-123">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c474-124">备注</span><span class="sxs-lookup"><span data-stu-id="2c474-124">Remarks</span></span>  
 <span data-ttu-id="2c474-125">将侦听器添加到共享侦听器集合并不会使其成为活动侦听器。</span><span class="sxs-lookup"><span data-stu-id="2c474-125">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="2c474-126">还必须将其添加到跟踪源或跟踪, 方法是将其添加到`Listeners`跟踪元素的集合。</span><span class="sxs-lookup"><span data-stu-id="2c474-126">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="2c474-127">.NET Framework 中的侦听器类派生自<xref:System.Diagnostics.TraceListener>类。</span><span class="sxs-lookup"><span data-stu-id="2c474-127">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="2c474-128">此元素可在计算机配置文件 (Machine.config) 和应用程序配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="2c474-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c474-129">示例</span><span class="sxs-lookup"><span data-stu-id="2c474-129">Example</span></span>  
 <span data-ttu-id="2c474-130">下面的示例演示`<sharedListeners>`如何使用元素将侦听器`console`添加到`Listeners` <xref:System.Diagnostics.TraceSource>和<xref:System.Diagnostics.Trace>类的集合。</span><span class="sxs-lookup"><span data-stu-id="2c474-130">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="2c474-131">控制台跟踪侦听器通过对<xref:System.Diagnostics.TraceSource>或<xref:System.Diagnostics.Trace>的调用将跟踪信息写入控制台。</span><span class="sxs-lookup"><span data-stu-id="2c474-131">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c474-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="2c474-132">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="2c474-133">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="2c474-133">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2c474-134">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="2c474-134">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
