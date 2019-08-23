---
title: <CompatSortNLSVersion> 元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3a348ac8da855e458b6208c51f9c51b48da3134
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927453"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="304ec-102">\<CompatSortNLSVersion > 元素</span><span class="sxs-lookup"><span data-stu-id="304ec-102">\<CompatSortNLSVersion> Element</span></span>
<span data-ttu-id="304ec-103">指定在执行字符串比较时，运行时应使用旧排序顺序。</span><span class="sxs-lookup"><span data-stu-id="304ec-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
 <span data-ttu-id="304ec-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="304ec-104">\<configuration></span></span>  
<span data-ttu-id="304ec-105">\<运行时 ></span><span class="sxs-lookup"><span data-stu-id="304ec-105">\<runtime></span></span>  
<span data-ttu-id="304ec-106">\<CompatSortNLSVersion > 元素</span><span class="sxs-lookup"><span data-stu-id="304ec-106">\<CompatSortNLSVersion> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="304ec-107">语法</span><span class="sxs-lookup"><span data-stu-id="304ec-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="304ec-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="304ec-108">Attributes and Elements</span></span>  
 <span data-ttu-id="304ec-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="304ec-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="304ec-110">特性</span><span class="sxs-lookup"><span data-stu-id="304ec-110">Attributes</span></span>  
  
|<span data-ttu-id="304ec-111">特性</span><span class="sxs-lookup"><span data-stu-id="304ec-111">Attribute</span></span>|<span data-ttu-id="304ec-112">描述</span><span class="sxs-lookup"><span data-stu-id="304ec-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="304ec-113">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="304ec-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="304ec-114">指定要使用其排序顺序的区域设置 ID。</span><span class="sxs-lookup"><span data-stu-id="304ec-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="304ec-115">enabled 特性</span><span class="sxs-lookup"><span data-stu-id="304ec-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="304ec-116">值</span><span class="sxs-lookup"><span data-stu-id="304ec-116">Value</span></span>|<span data-ttu-id="304ec-117">描述</span><span class="sxs-lookup"><span data-stu-id="304ec-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="304ec-118">4096</span><span class="sxs-lookup"><span data-stu-id="304ec-118">4096</span></span>|<span data-ttu-id="304ec-119">表示备选排序顺序的区域设置 ID。</span><span class="sxs-lookup"><span data-stu-id="304ec-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="304ec-120">在这种情况下, 4096 表示 .NET Framework 3.5 及更早版本的排序顺序。</span><span class="sxs-lookup"><span data-stu-id="304ec-120">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="304ec-121">子元素</span><span class="sxs-lookup"><span data-stu-id="304ec-121">Child Elements</span></span>  
 <span data-ttu-id="304ec-122">无。</span><span class="sxs-lookup"><span data-stu-id="304ec-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="304ec-123">父元素</span><span class="sxs-lookup"><span data-stu-id="304ec-123">Parent Elements</span></span>  
  
|<span data-ttu-id="304ec-124">元素</span><span class="sxs-lookup"><span data-stu-id="304ec-124">Element</span></span>|<span data-ttu-id="304ec-125">描述</span><span class="sxs-lookup"><span data-stu-id="304ec-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="304ec-126">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="304ec-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="304ec-127">包含有关运行时初始化选项的信息。</span><span class="sxs-lookup"><span data-stu-id="304ec-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="304ec-128">备注</span><span class="sxs-lookup"><span data-stu-id="304ec-128">Remarks</span></span>  
 <span data-ttu-id="304ec-129">由于 .NET Framework 4 中的<xref:System.Globalization.CompareInfo?displayProperty=nameWithType>类执行的字符串比较、排序和大小写操作符合 Unicode 5.1 标准, 因此<xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType>和<xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType>等字符串比较方法的结果可能不同于.NET Framework 的以前版本。</span><span class="sxs-lookup"><span data-stu-id="304ec-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="304ec-130">如果你的应用程序依赖于旧行为, 则可以通过在应用程序配置文件中包括`<CompatSortNLSVersion>`元素, 来还原 .NET Framework 3.5 及更早版本中使用的字符串比较和排序规则。</span><span class="sxs-lookup"><span data-stu-id="304ec-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="304ec-131">还原旧的字符串比较和排序规则还要求 sort00001000.dll 动态链接库在本地系统上可用。</span><span class="sxs-lookup"><span data-stu-id="304ec-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="304ec-132">此外，通过在创建应用程序域时将字符串“NetFx40_Legacy20SortingBehavior”传递到 <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> 方法，可以在特定的应用程序域中使用旧的字符串排序和比较规则。</span><span class="sxs-lookup"><span data-stu-id="304ec-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="304ec-133">示例</span><span class="sxs-lookup"><span data-stu-id="304ec-133">Example</span></span>  
 <span data-ttu-id="304ec-134">下面的示例实例化两个 <xref:System.String> 对象，并调用 <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法以通过使用当前区域性的约定对它们进行比较。</span><span class="sxs-lookup"><span data-stu-id="304ec-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="304ec-135">在 .NET Framework 4 上运行该示例时, 它会显示以下输出。</span><span class="sxs-lookup"><span data-stu-id="304ec-135">When you run the example on the .NET Framework 4, it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="304ec-136">这与你在 .NET Framework 3.5 上运行示例时显示的输出完全不同。</span><span class="sxs-lookup"><span data-stu-id="304ec-136">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5.</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="304ec-137">但是, 如果将下面的配置文件添加到示例的目录中, 然后在 .NET Framework 4 上运行此示例, 则输出将与示例在 .NET Framework 3.5 上运行时所生成的输出相同。</span><span class="sxs-lookup"><span data-stu-id="304ec-137">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="304ec-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="304ec-138">See also</span></span>

- [<span data-ttu-id="304ec-139">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="304ec-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="304ec-140">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="304ec-140">Configuration File Schema</span></span>](../index.md)
