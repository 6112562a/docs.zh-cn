---
title: '&lt;assemblyIdentity&gt;元素&lt;运行时&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/assemblyIdentity
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assemblyIdentity
helpviewer_keywords:
- <assemblyIdentity> element
- container tags, <assemblyIdentity> element
- assemblyIdentity element
ms.assetid: cea4d187-6398-4da4-af09-c1abc6a349c1
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b32e0da554622eb84b5569b5a1db04447fdc2940
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612551"
---
# <a name="ltassemblyidentitygt-element-for-ltruntimegt"></a><span data-ttu-id="4fe48-102">&lt;assemblyIdentity&gt;元素&lt;运行时&gt;</span><span class="sxs-lookup"><span data-stu-id="4fe48-102">&lt;assemblyIdentity&gt; Element for &lt;runtime&gt;</span></span>
<span data-ttu-id="4fe48-103">包含有关程序集的标识信息。</span><span class="sxs-lookup"><span data-stu-id="4fe48-103">Contains identifying information about the assembly.</span></span>  
  
 <span data-ttu-id="4fe48-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="4fe48-104">\<configuration></span></span>  
<span data-ttu-id="4fe48-105">\<运行时 ></span><span class="sxs-lookup"><span data-stu-id="4fe48-105">\<runtime></span></span>  
<span data-ttu-id="4fe48-106">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="4fe48-106">\<assemblyBinding></span></span>  
<span data-ttu-id="4fe48-107">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="4fe48-107">\<dependentAssembly></span></span>  
<span data-ttu-id="4fe48-108">\<assemblyIdentity ></span><span class="sxs-lookup"><span data-stu-id="4fe48-108">\<assemblyIdentity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe48-109">语法</span><span class="sxs-lookup"><span data-stu-id="4fe48-109">Syntax</span></span>  
  
```xml  
   <assemblyIdentity    
name="assembly name"  
publicKeyToken="public key token"  
culture="assembly culture"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fe48-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4fe48-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4fe48-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4fe48-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fe48-112">特性</span><span class="sxs-lookup"><span data-stu-id="4fe48-112">Attributes</span></span>  
  
|<span data-ttu-id="4fe48-113">特性</span><span class="sxs-lookup"><span data-stu-id="4fe48-113">Attribute</span></span>|<span data-ttu-id="4fe48-114">描述</span><span class="sxs-lookup"><span data-stu-id="4fe48-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="4fe48-115">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="4fe48-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="4fe48-116">程序集的名称</span><span class="sxs-lookup"><span data-stu-id="4fe48-116">The name of the assembly</span></span>|  
|`culture`|<span data-ttu-id="4fe48-117">可选特性。</span><span class="sxs-lookup"><span data-stu-id="4fe48-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4fe48-118">一个字符串，指定的语言和国家/地区的程序集。</span><span class="sxs-lookup"><span data-stu-id="4fe48-118">A string that specifies the language and country/region of the assembly.</span></span>|  
|`publicKeyToken`|<span data-ttu-id="4fe48-119">可选特性。</span><span class="sxs-lookup"><span data-stu-id="4fe48-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4fe48-120">一个十六进制值，该值指定程序集的强名称。</span><span class="sxs-lookup"><span data-stu-id="4fe48-120">A hexadecimal value that specifies the strong name of the assembly.</span></span>|  
|`processorArchitecture`|<span data-ttu-id="4fe48-121">可选特性。</span><span class="sxs-lookup"><span data-stu-id="4fe48-121">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4fe48-122">为包含特定于处理器的代码程序集指定的处理器体系结构的值"x86"、"amd64"、"msil"或"ia64"之一。</span><span class="sxs-lookup"><span data-stu-id="4fe48-122">One of the values "x86", "amd64", "msil", or "ia64", specifying the processor architecture for an assembly that contains processor-specific code.</span></span> <span data-ttu-id="4fe48-123">值不区分大小写。</span><span class="sxs-lookup"><span data-stu-id="4fe48-123">The values are not case-sensitive.</span></span> <span data-ttu-id="4fe48-124">如果该属性分配任何其他值，则整个`<assemblyIdentity>`元素将被忽略。</span><span class="sxs-lookup"><span data-stu-id="4fe48-124">If the attribute is assigned any other value, the entire `<assemblyIdentity>` element is ignored.</span></span> <span data-ttu-id="4fe48-125">请参阅 <xref:System.Reflection.ProcessorArchitecture>。</span><span class="sxs-lookup"><span data-stu-id="4fe48-125">See <xref:System.Reflection.ProcessorArchitecture>.</span></span>|  
  
## <a name="processorarchitecture-attribute"></a><span data-ttu-id="4fe48-126">processorArchitecture 属性</span><span class="sxs-lookup"><span data-stu-id="4fe48-126">processorArchitecture Attribute</span></span>  
  
|<span data-ttu-id="4fe48-127">值</span><span class="sxs-lookup"><span data-stu-id="4fe48-127">Value</span></span>|<span data-ttu-id="4fe48-128">描述</span><span class="sxs-lookup"><span data-stu-id="4fe48-128">Description</span></span>|  
|-----------|-----------------|  
|`amd64`|<span data-ttu-id="4fe48-129">AMD x86-64 体系结构仅。</span><span class="sxs-lookup"><span data-stu-id="4fe48-129">AMD x86-64 architecture only.</span></span>|  
|`ia64`|<span data-ttu-id="4fe48-130">Intel Itanium 体系结构仅。</span><span class="sxs-lookup"><span data-stu-id="4fe48-130">Intel Itanium architecture only.</span></span>|  
|`msil`|<span data-ttu-id="4fe48-131">不特定于处理器和每字位数。</span><span class="sxs-lookup"><span data-stu-id="4fe48-131">Neutral with respect to processor and bits-per-word.</span></span>|  
|`x86`|<span data-ttu-id="4fe48-132">32 位 x86 处理器，位于本机或在 Windows 上的 64 位平台上的 Windows (WOW) 环境中。</span><span class="sxs-lookup"><span data-stu-id="4fe48-132">A 32-bit x86 processor, either native or in the Windows on Windows (WOW) environment on a 64-bit platform.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fe48-133">子元素</span><span class="sxs-lookup"><span data-stu-id="4fe48-133">Child Elements</span></span>  
 <span data-ttu-id="4fe48-134">无。</span><span class="sxs-lookup"><span data-stu-id="4fe48-134">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4fe48-135">父元素</span><span class="sxs-lookup"><span data-stu-id="4fe48-135">Parent Elements</span></span>  
  
|<span data-ttu-id="4fe48-136">元素</span><span class="sxs-lookup"><span data-stu-id="4fe48-136">Element</span></span>|<span data-ttu-id="4fe48-137">描述</span><span class="sxs-lookup"><span data-stu-id="4fe48-137">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="4fe48-138">包含有关程序集版本重定向和程序集位置的信息。</span><span class="sxs-lookup"><span data-stu-id="4fe48-138">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="4fe48-139">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="4fe48-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`dependentAssembly`|<span data-ttu-id="4fe48-140">封装每个程序集的绑定策略和程序集位置。</span><span class="sxs-lookup"><span data-stu-id="4fe48-140">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="4fe48-141">使用一个`<dependentAssembly>`每个程序集的元素。</span><span class="sxs-lookup"><span data-stu-id="4fe48-141">Use one `<dependentAssembly>` element for each assembly.</span></span>|  
|`runtime`|<span data-ttu-id="4fe48-142">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="4fe48-142">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fe48-143">备注</span><span class="sxs-lookup"><span data-stu-id="4fe48-143">Remarks</span></span>  
 <span data-ttu-id="4fe48-144">每个 **\<dependentAssembly >** 元素必须有一个 **\<assemblyIdentity >** 子元素。</span><span class="sxs-lookup"><span data-stu-id="4fe48-144">Every **\<dependentAssembly>** element must have one **\<assemblyIdentity>** child element.</span></span>  
  
 <span data-ttu-id="4fe48-145">如果`processorArchitecture`属性是否存在、`<assemblyIdentity>`元素仅适用于具有相应的处理器体系结构的程序集。</span><span class="sxs-lookup"><span data-stu-id="4fe48-145">If the `processorArchitecture` attribute is present, the `<assemblyIdentity>` element applies only to the assembly with the corresponding processor architecture.</span></span> <span data-ttu-id="4fe48-146">如果`processorArchitecture`属性不存在，`<assemblyIdentity>`元素可以将应用于具有任何处理器体系结构的程序集。</span><span class="sxs-lookup"><span data-stu-id="4fe48-146">If the `processorArchitecture` attribute is not present, the `<assemblyIdentity>` element can apply to an assembly with any processor architecture.</span></span>  
  
 <span data-ttu-id="4fe48-147">下面的示例显示了两个程序集具有相同名称的针对两个不同两个处理器的体系结构，且其版本不维护同步配置文件。当应用程序执行 x86 平台第一个`<assemblyIdentity>`元素得到应用，另一个被忽略。</span><span class="sxs-lookup"><span data-stu-id="4fe48-147">The following example shows a configuration file for two assemblies with the same name that target two different two processor architectures, and whose versions have not been maintained in synch. When the application executes on the x86 platform the first `<assemblyIdentity>` element applies and the other is ignored.</span></span> <span data-ttu-id="4fe48-148">如果应用程序在非 x86 或 ia64 平台上执行，都将被忽略。</span><span class="sxs-lookup"><span data-stu-id="4fe48-148">If the application executes on a platform other than x86 or ia64, both are ignored.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"  
                  processorArchitecture="x86" />  
            <bindingRedirect oldVersion= "1.0.0.0"   
                  newVersion="1.1.0.0" />  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="MyAssembly"  
                  publicKeyToken="14a739be0244c389"  
                  culture="neutral"   
                  processorArchitecture="ia64" />  
            <bindingRedirect oldVersion="1.0.0.0"   
                  newVersion="2.0.0.0" />  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="4fe48-149">如果配置文件包含`<assemblyIdentity>`元素没有`processorArchitecture`属性，并且不包含相匹配的平台，而无需元素的元素`processorArchitecture`使用属性。</span><span class="sxs-lookup"><span data-stu-id="4fe48-149">If a configuration file contains an `<assemblyIdentity>` element with no `processorArchitecture` attribute, and does not contain an element that matches the platform, the element without the `processorArchitecture` attribute is used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fe48-150">示例</span><span class="sxs-lookup"><span data-stu-id="4fe48-150">Example</span></span>  
 <span data-ttu-id="4fe48-151">下面的示例演示如何提供有关程序集信息。</span><span class="sxs-lookup"><span data-stu-id="4fe48-151">The following example shows how to provide information about an assembly.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4fe48-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="4fe48-152">See Also</span></span>  
- [<span data-ttu-id="4fe48-153">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="4fe48-153">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="4fe48-154">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="4fe48-154">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="4fe48-155">重定向程序集版本</span><span class="sxs-lookup"><span data-stu-id="4fe48-155">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
