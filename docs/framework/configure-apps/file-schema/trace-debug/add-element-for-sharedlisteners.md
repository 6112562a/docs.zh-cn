---
title: '&lt;添加&gt;元素&lt;sharedListeners&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9e0a23411f4bc37a1e09460113d15f4861e0a190
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151156"
---
# <a name="ltaddgt-element-for-ltsharedlistenersgt"></a><span data-ttu-id="33c3f-102">&lt;添加&gt;元素&lt;sharedListeners&gt;</span><span class="sxs-lookup"><span data-stu-id="33c3f-102">&lt;add&gt; Element for &lt;sharedListeners&gt;</span></span>
<span data-ttu-id="33c3f-103">将侦听器添加到 `sharedListeners` 集合中。</span><span class="sxs-lookup"><span data-stu-id="33c3f-103">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="33c3f-104">`sharedListeners` 是侦听器的集合的任何[\<源 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)或[\<跟踪 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)可以引用。</span><span class="sxs-lookup"><span data-stu-id="33c3f-104">`sharedListeners` is a collection of listeners that any [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) can reference.</span></span>  <span data-ttu-id="33c3f-105">默认情况下，在侦听器`sharedListeners`集合未按放置`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="33c3f-105">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="33c3f-106">它们肯定会添加到名称[\<源 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)或[\<跟踪 >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)。</span><span class="sxs-lookup"><span data-stu-id="33c3f-106">They must be added by name to the [\<source>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) or [\<trace>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md).</span></span> <span data-ttu-id="33c3f-107">不能获取侦听器`sharedListeners`在运行时在代码中的集合。</span><span class="sxs-lookup"><span data-stu-id="33c3f-107">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  
  
 <span data-ttu-id="33c3f-108">\<configuration></span><span class="sxs-lookup"><span data-stu-id="33c3f-108">\<configuration></span></span>  
<span data-ttu-id="33c3f-109">&nbsp;&nbsp;\<system.diagnostics ></span><span class="sxs-lookup"><span data-stu-id="33c3f-109">&nbsp;&nbsp;\<system.diagnostics></span></span>  
<span data-ttu-id="33c3f-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners > 元素</span><span class="sxs-lookup"><span data-stu-id="33c3f-110">&nbsp;&nbsp;&nbsp;&nbsp;\<sharedListeners> Element</span></span>  
<span data-ttu-id="33c3f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<添加 ></span><span class="sxs-lookup"><span data-stu-id="33c3f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33c3f-112">语法</span><span class="sxs-lookup"><span data-stu-id="33c3f-112">Syntax</span></span>  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33c3f-113">特性和元素</span><span class="sxs-lookup"><span data-stu-id="33c3f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="33c3f-114">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="33c3f-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33c3f-115">特性</span><span class="sxs-lookup"><span data-stu-id="33c3f-115">Attributes</span></span>  
  
|<span data-ttu-id="33c3f-116">特性</span><span class="sxs-lookup"><span data-stu-id="33c3f-116">Attribute</span></span>|<span data-ttu-id="33c3f-117">描述</span><span class="sxs-lookup"><span data-stu-id="33c3f-117">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="33c3f-118">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="33c3f-118">Required attribute.</span></span><br /><br /> <span data-ttu-id="33c3f-119">指定用于将添加到的共享的侦听器的侦听器名称`Listeners`集合。</span><span class="sxs-lookup"><span data-stu-id="33c3f-119">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="33c3f-120">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="33c3f-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="33c3f-121">指定的侦听器的类型。</span><span class="sxs-lookup"><span data-stu-id="33c3f-121">Specifies the type of the listener.</span></span> <span data-ttu-id="33c3f-122">必须使用满足要求中指定的字符串[指定完全限定的类型名称](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="33c3f-122">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="33c3f-123">可选特性。</span><span class="sxs-lookup"><span data-stu-id="33c3f-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="33c3f-124">传递给构造函数为指定类的字符串。</span><span class="sxs-lookup"><span data-stu-id="33c3f-124">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="33c3f-125">可选特性。</span><span class="sxs-lookup"><span data-stu-id="33c3f-125">Optional attribute.</span></span><br/><br/><span data-ttu-id="33c3f-126">字符串表示形式的一个或多个<xref:System.Diagnostics.TraceOptions>枚举成员，指示要写入跟踪输出的数据。</span><span class="sxs-lookup"><span data-stu-id="33c3f-126">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="33c3f-127">由逗号分隔多个项。</span><span class="sxs-lookup"><span data-stu-id="33c3f-127">Multiple items are separated by commas.</span></span> <span data-ttu-id="33c3f-128">默认值为"None"。</span><span class="sxs-lookup"><span data-stu-id="33c3f-128">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="33c3f-129">子元素</span><span class="sxs-lookup"><span data-stu-id="33c3f-129">Child Elements</span></span>  
  
|<span data-ttu-id="33c3f-130">元素</span><span class="sxs-lookup"><span data-stu-id="33c3f-130">Element</span></span>|<span data-ttu-id="33c3f-131">描述</span><span class="sxs-lookup"><span data-stu-id="33c3f-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33c3f-132">\<filter></span><span class="sxs-lookup"><span data-stu-id="33c3f-132">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="33c3f-133">将筛选器添加到 `sharedListeners` 集合中的侦听器。</span><span class="sxs-lookup"><span data-stu-id="33c3f-133">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="33c3f-134">父元素</span><span class="sxs-lookup"><span data-stu-id="33c3f-134">Parent Elements</span></span>  
  
|<span data-ttu-id="33c3f-135">元素</span><span class="sxs-lookup"><span data-stu-id="33c3f-135">Element</span></span>|<span data-ttu-id="33c3f-136">描述</span><span class="sxs-lookup"><span data-stu-id="33c3f-136">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="33c3f-137">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="33c3f-137">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="33c3f-138">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="33c3f-138">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="33c3f-139">任何源或跟踪元素可以引用的侦听器集合。</span><span class="sxs-lookup"><span data-stu-id="33c3f-139">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33c3f-140">备注</span><span class="sxs-lookup"><span data-stu-id="33c3f-140">Remarks</span></span>  
 <span data-ttu-id="33c3f-141">.NET Framework 附带的侦听器类派生<xref:System.Diagnostics.TraceListener>类。</span><span class="sxs-lookup"><span data-stu-id="33c3f-141">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="33c3f-142">值`name`属性用于添加到的共享的侦听器`Listeners`集合以进行跟踪或跟踪源。</span><span class="sxs-lookup"><span data-stu-id="33c3f-142">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="33c3f-143">值为`initializeData`属性取决于您创建的侦听器类型。</span><span class="sxs-lookup"><span data-stu-id="33c3f-143">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="33c3f-144">并非所有的跟踪侦听器需要你指定`initializeData`。</span><span class="sxs-lookup"><span data-stu-id="33c3f-144">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33c3f-145">当你使用`initializeData`属性中，你可能会收到编译器警告"未声明 initializeData 属性。"</span><span class="sxs-lookup"><span data-stu-id="33c3f-145">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="33c3f-146">由于配置设置时根据的抽象基类进行验证，会出现此警告<xref:System.Diagnostics.TraceListener>，这不能识别`initializeData`属性。</span><span class="sxs-lookup"><span data-stu-id="33c3f-146">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="33c3f-147">通常情况下，可以忽略具有构造函数采用参数的跟踪侦听器实现此警告。</span><span class="sxs-lookup"><span data-stu-id="33c3f-147">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="33c3f-148">下表显示了随.NET Framework 中的跟踪侦听器，并说明的值及其`initializeData`属性。</span><span class="sxs-lookup"><span data-stu-id="33c3f-148">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="33c3f-149">跟踪侦听器类</span><span class="sxs-lookup"><span data-stu-id="33c3f-149">Trace listener class</span></span>|<span data-ttu-id="33c3f-150">initializeData 属性值</span><span class="sxs-lookup"><span data-stu-id="33c3f-150">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="33c3f-151">`useErrorStream`值<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>构造函数。</span><span class="sxs-lookup"><span data-stu-id="33c3f-151">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="33c3f-152">设置`initializeData`属性为"`true`"来写入跟踪和调试输出写入标准错误流中; 将其设置为"`false`"要写入到标准输出流。</span><span class="sxs-lookup"><span data-stu-id="33c3f-152">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="33c3f-153">文件的名称<xref:System.Diagnostics.DelimitedListTraceListener>写入。</span><span class="sxs-lookup"><span data-stu-id="33c3f-153">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="33c3f-154">现有事件日志源的名称。</span><span class="sxs-lookup"><span data-stu-id="33c3f-154">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="33c3f-155">文件的名称，<xref:System.Diagnostics.EventSchemaTraceListener>写入。</span><span class="sxs-lookup"><span data-stu-id="33c3f-155">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="33c3f-156">文件的名称，<xref:System.Diagnostics.TextWriterTraceListener>写入。</span><span class="sxs-lookup"><span data-stu-id="33c3f-156">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="33c3f-157">文件的名称，<xref:System.Diagnostics.XmlWriterTraceListener>写入。</span><span class="sxs-lookup"><span data-stu-id="33c3f-157">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="33c3f-158">配置文件</span><span class="sxs-lookup"><span data-stu-id="33c3f-158">Configuration File</span></span>  
 <span data-ttu-id="33c3f-159">计算机配置文件 (Machine.config) 和应用程序配置文件中，可以使用此元素。</span><span class="sxs-lookup"><span data-stu-id="33c3f-159">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33c3f-160">示例</span><span class="sxs-lookup"><span data-stu-id="33c3f-160">Example</span></span>  
 <span data-ttu-id="33c3f-161">下面的示例演示如何使用`<add>`元素添加<xref:System.Diagnostics.TextWriterTraceListener>`textListener`到`sharedListeners`集合。</span><span class="sxs-lookup"><span data-stu-id="33c3f-161">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="33c3f-162">`textListener` 按名称添加到`Listeners`跟踪源集合`TraceSourceApp`。</span><span class="sxs-lookup"><span data-stu-id="33c3f-162">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="33c3f-163">`textListener`侦听器将跟踪输出写入到文件 myListener.log。</span><span class="sxs-lookup"><span data-stu-id="33c3f-163">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a><span data-ttu-id="33c3f-164">请参阅</span><span class="sxs-lookup"><span data-stu-id="33c3f-164">See Also</span></span>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [<span data-ttu-id="33c3f-165">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="33c3f-165">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [<span data-ttu-id="33c3f-166">跟踪侦听器</span><span class="sxs-lookup"><span data-stu-id="33c3f-166">Trace Listeners</span></span>](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
