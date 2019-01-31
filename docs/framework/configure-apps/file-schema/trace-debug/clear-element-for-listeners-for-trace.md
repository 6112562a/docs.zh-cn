---
title: <clear> 的 <listeners> 的 <trace> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: b199f24a2c1e1c8154c0ec22bef6367e5ba0ec26
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262596"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="b0450-102">\<清除 > 元素\<侦听器 > 为\<跟踪 ></span><span class="sxs-lookup"><span data-stu-id="b0450-102">\<clear> Element for \<listeners> for \<trace></span></span>
<span data-ttu-id="b0450-103">清除跟踪的 `Listeners` 集合。</span><span class="sxs-lookup"><span data-stu-id="b0450-103">Clears the `Listeners` collection for trace.</span></span>  
  
 <span data-ttu-id="b0450-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b0450-104">\<configuration></span></span>  
<span data-ttu-id="b0450-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="b0450-105">\<system.diagnostics></span></span>  
<span data-ttu-id="b0450-106">\<trace></span><span class="sxs-lookup"><span data-stu-id="b0450-106">\<trace></span></span>  
<span data-ttu-id="b0450-107">\<listeners></span><span class="sxs-lookup"><span data-stu-id="b0450-107">\<listeners></span></span>  
<span data-ttu-id="b0450-108">\<clear></span><span class="sxs-lookup"><span data-stu-id="b0450-108">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0450-109">语法</span><span class="sxs-lookup"><span data-stu-id="b0450-109">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0450-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="b0450-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b0450-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b0450-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0450-112">特性</span><span class="sxs-lookup"><span data-stu-id="b0450-112">Attributes</span></span>  
 <span data-ttu-id="b0450-113">无。</span><span class="sxs-lookup"><span data-stu-id="b0450-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b0450-114">子元素</span><span class="sxs-lookup"><span data-stu-id="b0450-114">Child Elements</span></span>  
 <span data-ttu-id="b0450-115">无。</span><span class="sxs-lookup"><span data-stu-id="b0450-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0450-116">父元素</span><span class="sxs-lookup"><span data-stu-id="b0450-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b0450-117">元素</span><span class="sxs-lookup"><span data-stu-id="b0450-117">Element</span></span>|<span data-ttu-id="b0450-118">描述</span><span class="sxs-lookup"><span data-stu-id="b0450-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b0450-119">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="b0450-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b0450-120">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="b0450-120">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="b0450-121">包含用于收集、存储和路由跟踪消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="b0450-121">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="b0450-122">包含用于收集、 存储和路由消息的侦听器。</span><span class="sxs-lookup"><span data-stu-id="b0450-122">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="b0450-123">侦听器将跟踪输出定向到适当的目标。</span><span class="sxs-lookup"><span data-stu-id="b0450-123">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0450-124">备注</span><span class="sxs-lookup"><span data-stu-id="b0450-124">Remarks</span></span>  
 <span data-ttu-id="b0450-125">`<clear>`元素中移除所有侦听器从`Listeners`跟踪的集合。</span><span class="sxs-lookup"><span data-stu-id="b0450-125">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="b0450-126">可以使用`<clear>`元素之前使用`<add>`元素为特定集合中没有任何其他活动的侦听器。</span><span class="sxs-lookup"><span data-stu-id="b0450-126">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="b0450-127">您可以清除`Listeners`以编程方式调用集合<xref:System.Diagnostics.TraceListenerCollection.Clear%2A>方法<xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType>属性 (`System.Diagnostics.Trace.Listeners.Clear()`)。</span><span class="sxs-lookup"><span data-stu-id="b0450-127">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="b0450-128">计算机配置文件 (Machine.config) 和应用程序配置文件中，可以使用此元素。</span><span class="sxs-lookup"><span data-stu-id="b0450-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0450-129">`<clear>`元素中移除<xref:System.Diagnostics.DefaultTraceListener>从`Listeners`集合中，更改的行为<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>， <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>， <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>，和<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="b0450-129">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="b0450-130">调用`Assert`或`Fail`方法通常会显示一个消息框中。</span><span class="sxs-lookup"><span data-stu-id="b0450-130">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="b0450-131">但是，消息框如果不显示<xref:System.Diagnostics.DefaultTraceListener>不在`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="b0450-131">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0450-132">示例</span><span class="sxs-lookup"><span data-stu-id="b0450-132">Example</span></span>  
 <span data-ttu-id="b0450-133">下面的示例演示如何使用`<clear>`之前使用的元素`<add>`元素添加侦听器`console`到`Listeners`跟踪的集合。</span><span class="sxs-lookup"><span data-stu-id="b0450-133">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="b0450-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="b0450-134">See also</span></span>
- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="b0450-135">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="b0450-135">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [<span data-ttu-id="b0450-136">\<remove></span><span class="sxs-lookup"><span data-stu-id="b0450-136">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="b0450-137">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="b0450-137">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
