---
title: '&lt;dependentAssembly&gt;元素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5b0d3bfb7e4db2fec39f37c9fb794731cdf5bbc
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613292"
---
# <a name="ltdependentassemblygt-element"></a><span data-ttu-id="e78ad-102">&lt;dependentAssembly&gt;元素</span><span class="sxs-lookup"><span data-stu-id="e78ad-102">&lt;dependentAssembly&gt; Element</span></span>
<span data-ttu-id="e78ad-103">封装每个程序集的绑定策略和程序集位置。</span><span class="sxs-lookup"><span data-stu-id="e78ad-103">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="e78ad-104">使用一个`dependentAssembly`每个程序集的元素。</span><span class="sxs-lookup"><span data-stu-id="e78ad-104">Use one `dependentAssembly` element for each assembly.</span></span>  
  
 <span data-ttu-id="e78ad-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e78ad-105">\<configuration></span></span>  
<span data-ttu-id="e78ad-106">\<运行时 ></span><span class="sxs-lookup"><span data-stu-id="e78ad-106">\<runtime></span></span>  
<span data-ttu-id="e78ad-107">\<assemblyBinding ></span><span class="sxs-lookup"><span data-stu-id="e78ad-107">\<assemblyBinding></span></span>  
<span data-ttu-id="e78ad-108">\<dependentAssembly ></span><span class="sxs-lookup"><span data-stu-id="e78ad-108">\<dependentAssembly></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e78ad-109">语法</span><span class="sxs-lookup"><span data-stu-id="e78ad-109">Syntax</span></span>  
  
```xml  
<dependentAssembly>   
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e78ad-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="e78ad-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e78ad-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e78ad-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e78ad-112">特性</span><span class="sxs-lookup"><span data-stu-id="e78ad-112">Attributes</span></span>  
 <span data-ttu-id="e78ad-113">无。</span><span class="sxs-lookup"><span data-stu-id="e78ad-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e78ad-114">子元素</span><span class="sxs-lookup"><span data-stu-id="e78ad-114">Child Elements</span></span>  
  
|<span data-ttu-id="e78ad-115">元素</span><span class="sxs-lookup"><span data-stu-id="e78ad-115">Element</span></span>|<span data-ttu-id="e78ad-116">描述</span><span class="sxs-lookup"><span data-stu-id="e78ad-116">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="e78ad-117">包含有关程序集的标识信息。</span><span class="sxs-lookup"><span data-stu-id="e78ad-117">Contains identifying information about the assembly.</span></span> <span data-ttu-id="e78ad-118">此元素必须包括在每个`dependentAssembly`元素。</span><span class="sxs-lookup"><span data-stu-id="e78ad-118">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="e78ad-119">指定了运行时可以找到共享的程序集，如果计算机上未安装。</span><span class="sxs-lookup"><span data-stu-id="e78ad-119">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="e78ad-120">将一个程序集版本重定向到另一个版本。</span><span class="sxs-lookup"><span data-stu-id="e78ad-120">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="e78ad-121">指定是否在运行时应用此程序集发布者策略。</span><span class="sxs-lookup"><span data-stu-id="e78ad-121">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e78ad-122">父元素</span><span class="sxs-lookup"><span data-stu-id="e78ad-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e78ad-123">元素</span><span class="sxs-lookup"><span data-stu-id="e78ad-123">Element</span></span>|<span data-ttu-id="e78ad-124">描述</span><span class="sxs-lookup"><span data-stu-id="e78ad-124">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="e78ad-125">包含有关程序集版本重定向和程序集位置的信息。</span><span class="sxs-lookup"><span data-stu-id="e78ad-125">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="e78ad-126">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="e78ad-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e78ad-127">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="e78ad-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e78ad-128">示例</span><span class="sxs-lookup"><span data-stu-id="e78ad-128">Example</span></span>  
 <span data-ttu-id="e78ad-129">下面的示例演示如何封装两个程序集的程序集信息。</span><span class="sxs-lookup"><span data-stu-id="e78ad-129">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
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
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e78ad-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="e78ad-130">See Also</span></span>  
- [<span data-ttu-id="e78ad-131">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="e78ad-131">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="e78ad-132">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="e78ad-132">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="e78ad-133">重定向程序集版本</span><span class="sxs-lookup"><span data-stu-id="e78ad-133">Redirecting Assembly Versions</span></span>](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
