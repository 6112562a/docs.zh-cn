---
title: '&lt;Thread_UseAllCpuGroups&gt;元素'
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a3984d594d0739d4b8f2b7b165aab434e10ab80
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611004"
---
# <a name="ltthreaduseallcpugroupsgt-element"></a><span data-ttu-id="6603d-102">&lt;Thread_UseAllCpuGroups&gt;元素</span><span class="sxs-lookup"><span data-stu-id="6603d-102">&lt;Thread_UseAllCpuGroups&gt; Element</span></span>
<span data-ttu-id="6603d-103">指定运行时是否跨所有 CPU 组分发托管的线程。</span><span class="sxs-lookup"><span data-stu-id="6603d-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>  
  
 <span data-ttu-id="6603d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6603d-104">\<configuration></span></span>  
<span data-ttu-id="6603d-105">\<运行时 ></span><span class="sxs-lookup"><span data-stu-id="6603d-105">\<runtime></span></span>  
<span data-ttu-id="6603d-106"><Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="6603d-106"><Thread_UseAllCpuGroups></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6603d-107">语法</span><span class="sxs-lookup"><span data-stu-id="6603d-107">Syntax</span></span>  
  
```xml
<Thread_UseAllCpuGroups    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6603d-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="6603d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6603d-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6603d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6603d-110">特性</span><span class="sxs-lookup"><span data-stu-id="6603d-110">Attributes</span></span>  
  
|<span data-ttu-id="6603d-111">特性</span><span class="sxs-lookup"><span data-stu-id="6603d-111">Attribute</span></span>|<span data-ttu-id="6603d-112">描述</span><span class="sxs-lookup"><span data-stu-id="6603d-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6603d-113">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="6603d-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="6603d-114">指定运行时是否跨所有 CPU 组分发托管的线程。</span><span class="sxs-lookup"><span data-stu-id="6603d-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6603d-115">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="6603d-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="6603d-116">值</span><span class="sxs-lookup"><span data-stu-id="6603d-116">Value</span></span>|<span data-ttu-id="6603d-117">描述</span><span class="sxs-lookup"><span data-stu-id="6603d-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="6603d-118">在运行时不会跨多个 CPU 组分发托管的线程。</span><span class="sxs-lookup"><span data-stu-id="6603d-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="6603d-119">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="6603d-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="6603d-120">在运行时将托管的线程分布到多个 CPU 组，如果计算机有多个 CPU 组和[ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)启用元素。</span><span class="sxs-lookup"><span data-stu-id="6603d-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6603d-121">子元素</span><span class="sxs-lookup"><span data-stu-id="6603d-121">Child Elements</span></span>  
 <span data-ttu-id="6603d-122">无。</span><span class="sxs-lookup"><span data-stu-id="6603d-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6603d-123">父元素</span><span class="sxs-lookup"><span data-stu-id="6603d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6603d-124">元素</span><span class="sxs-lookup"><span data-stu-id="6603d-124">Element</span></span>|<span data-ttu-id="6603d-125">描述</span><span class="sxs-lookup"><span data-stu-id="6603d-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6603d-126">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="6603d-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6603d-127">包含有关程序集绑定和垃圾回收的信息。</span><span class="sxs-lookup"><span data-stu-id="6603d-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6603d-128">备注</span><span class="sxs-lookup"><span data-stu-id="6603d-128">Remarks</span></span>  
 <span data-ttu-id="6603d-129">当一台计算机具有多个 CPU 组时，启用此元素会导致运行时的所有 CPU 组分发托管的线程。</span><span class="sxs-lookup"><span data-stu-id="6603d-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="6603d-130">若要使用此功能，还必须启用[ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)元素，该扩展到所有 CPU 组的垃圾回收并将考虑在内时创建和平衡堆的所有核心元素。</span><span class="sxs-lookup"><span data-stu-id="6603d-130">To use this feature, you must also enable the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="6603d-131">启用[ \<GCCpuGroup >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)元素需要启用[ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="6603d-131">Enabling the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element requires enabling the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span></span> <span data-ttu-id="6603d-132">如果未启用这些元素，则启用`<Thread_UseAllCpuGroups>`元素不起作用。</span><span class="sxs-lookup"><span data-stu-id="6603d-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6603d-133">示例</span><span class="sxs-lookup"><span data-stu-id="6603d-133">Example</span></span>  
 <span data-ttu-id="6603d-134">下面的示例演示如何启用对多个 CPU 组的支持。</span><span class="sxs-lookup"><span data-stu-id="6603d-134">The following example shows how to enable support for multiple CPU groups.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <Thread_UseAllCpuGroups enabled="true"/>  
      <GCCpuGroup enabled="true"/>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6603d-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="6603d-135">See Also</span></span>  
- [<span data-ttu-id="6603d-136">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="6603d-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="6603d-137">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="6603d-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="6603d-138">\<GCCpuGroup > 元素</span><span class="sxs-lookup"><span data-stu-id="6603d-138">\<GCCpuGroup> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
