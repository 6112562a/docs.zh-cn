---
title: <filter> 元素<add>为 <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 2bef729f179b41509d3c0381b26e38e364dbf86b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120739"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="89db5-102">\<筛选器 > 元素\<添加 > 为\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="89db5-102">\<filter> Element for \<add> for \<sharedListeners></span></span>
<span data-ttu-id="89db5-103">将筛选器添加到 `sharedListeners` 集合中的侦听器。</span><span class="sxs-lookup"><span data-stu-id="89db5-103">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  
  
 <span data-ttu-id="89db5-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="89db5-104">\<configuration></span></span>  
<span data-ttu-id="89db5-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="89db5-105">\<system.diagnostics></span></span>  
<span data-ttu-id="89db5-106">\<sharedListeners > 元素</span><span class="sxs-lookup"><span data-stu-id="89db5-106">\<sharedListeners> Element</span></span>  
<span data-ttu-id="89db5-107">\<add></span><span class="sxs-lookup"><span data-stu-id="89db5-107">\<add></span></span>  
<span data-ttu-id="89db5-108">\<filter></span><span class="sxs-lookup"><span data-stu-id="89db5-108">\<filter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89db5-109">语法</span><span class="sxs-lookup"><span data-stu-id="89db5-109">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"   
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89db5-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="89db5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="89db5-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="89db5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89db5-112">特性</span><span class="sxs-lookup"><span data-stu-id="89db5-112">Attributes</span></span>  
  
|<span data-ttu-id="89db5-113">特性</span><span class="sxs-lookup"><span data-stu-id="89db5-113">Attribute</span></span>|<span data-ttu-id="89db5-114">描述</span><span class="sxs-lookup"><span data-stu-id="89db5-114">Description</span></span>|  
|---------------|-----------------|  
|**<span data-ttu-id="89db5-115">类型</span><span class="sxs-lookup"><span data-stu-id="89db5-115">type</span></span>**|<span data-ttu-id="89db5-116">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="89db5-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="89db5-117">指定筛选器的类型。</span><span class="sxs-lookup"><span data-stu-id="89db5-117">Specifies the type of the filter.</span></span> <span data-ttu-id="89db5-118">可以使用仅该类型的完整名称 (格式为<xref:System.Type.FullName%2A?displayProperty=nameWithType>属性)，也可以使用完全限定的类型名称包括程序集信息 (格式为<xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>属性)。</span><span class="sxs-lookup"><span data-stu-id="89db5-118">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="89db5-119">有关创建完全限定的类型名称的信息，请参阅[指定完全限定的类型名称](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="89db5-119">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|**<span data-ttu-id="89db5-120">initializeData</span><span class="sxs-lookup"><span data-stu-id="89db5-120">initializeData</span></span>**|<span data-ttu-id="89db5-121">可选特性。</span><span class="sxs-lookup"><span data-stu-id="89db5-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="89db5-122">传递给构造函数为指定类的字符串。</span><span class="sxs-lookup"><span data-stu-id="89db5-122">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89db5-123">子元素</span><span class="sxs-lookup"><span data-stu-id="89db5-123">Child Elements</span></span>  
 <span data-ttu-id="89db5-124">无。</span><span class="sxs-lookup"><span data-stu-id="89db5-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89db5-125">父元素</span><span class="sxs-lookup"><span data-stu-id="89db5-125">Parent Elements</span></span>  
  
|<span data-ttu-id="89db5-126">元素</span><span class="sxs-lookup"><span data-stu-id="89db5-126">Element</span></span>|<span data-ttu-id="89db5-127">描述</span><span class="sxs-lookup"><span data-stu-id="89db5-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="89db5-128">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="89db5-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="89db5-129">指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。</span><span class="sxs-lookup"><span data-stu-id="89db5-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="89db5-130">任何源或跟踪元素可以引用的侦听器集合。</span><span class="sxs-lookup"><span data-stu-id="89db5-130">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="89db5-131">将侦听器添加到**sharedListeners**集合。</span><span class="sxs-lookup"><span data-stu-id="89db5-131">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89db5-132">备注</span><span class="sxs-lookup"><span data-stu-id="89db5-132">Remarks</span></span>  
 <span data-ttu-id="89db5-133">如果在中定义一个侦听器`<add>`的元素`<sharedListeners>`元素中，应在定义该侦听器的筛选器`<filter>`的子元素`<add>`元素。</span><span class="sxs-lookup"><span data-stu-id="89db5-133">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="89db5-134">计算机配置文件 (Machine.config) 和应用程序配置文件中，可以使用此元素。</span><span class="sxs-lookup"><span data-stu-id="89db5-134">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89db5-135">示例</span><span class="sxs-lookup"><span data-stu-id="89db5-135">Example</span></span>  
 <span data-ttu-id="89db5-136">下面的示例演示如何使用`<filter>`元素添加到跟踪侦听器的筛选器`console`中`sharedListeners`集合。</span><span class="sxs-lookup"><span data-stu-id="89db5-136">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"   
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"   
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="89db5-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="89db5-137">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="89db5-138">跟踪和调试设置架构</span><span class="sxs-lookup"><span data-stu-id="89db5-138">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
