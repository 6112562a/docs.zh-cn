---
title: <add> 的 <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e2a2e26099f2d31116e4a89297fc1ac984c480d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920079"
---
# <a name="add-of-namespacetable"></a><span data-ttu-id="561d8-102">\<添加 namespaceTable > \<的 ></span><span class="sxs-lookup"><span data-stu-id="561d8-102">\<add> of \<namespaceTable></span></span>
<span data-ttu-id="561d8-103">表示一个配置元素，此元素包含随后可在 XPath 筛选器中用于路由的前缀映射的命名空间。</span><span class="sxs-lookup"><span data-stu-id="561d8-103">Represents a configuration element that contains a namespace to prefix mapping that can then be used in XPath filters for routing.</span></span>  
  
 <span data-ttu-id="561d8-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="561d8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="561d8-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="561d8-105">\<routing></span></span>  
<span data-ttu-id="561d8-106">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="561d8-106">\<namespaceTable></span></span>  
<span data-ttu-id="561d8-107">\<add></span><span class="sxs-lookup"><span data-stu-id="561d8-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="561d8-108">语法</span><span class="sxs-lookup"><span data-stu-id="561d8-108">Syntax</span></span>  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="561d8-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="561d8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="561d8-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="561d8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="561d8-111">特性</span><span class="sxs-lookup"><span data-stu-id="561d8-111">Attributes</span></span>  
  
|<span data-ttu-id="561d8-112">特性</span><span class="sxs-lookup"><span data-stu-id="561d8-112">Attribute</span></span>|<span data-ttu-id="561d8-113">描述</span><span class="sxs-lookup"><span data-stu-id="561d8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="561d8-114">namespace</span><span class="sxs-lookup"><span data-stu-id="561d8-114">namespace</span></span>|<span data-ttu-id="561d8-115">一个包含命名空间的字符串。</span><span class="sxs-lookup"><span data-stu-id="561d8-115">A string containing the namespace.</span></span>|  
|<span data-ttu-id="561d8-116">prefix</span><span class="sxs-lookup"><span data-stu-id="561d8-116">prefix</span></span>|<span data-ttu-id="561d8-117">一个包含此命名空间的前缀的字符串。</span><span class="sxs-lookup"><span data-stu-id="561d8-117">A string containing the prefix for this namespace.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="561d8-118">子元素</span><span class="sxs-lookup"><span data-stu-id="561d8-118">Child Elements</span></span>  
 <span data-ttu-id="561d8-119">无。</span><span class="sxs-lookup"><span data-stu-id="561d8-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="561d8-120">父元素</span><span class="sxs-lookup"><span data-stu-id="561d8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="561d8-121">元素</span><span class="sxs-lookup"><span data-stu-id="561d8-121">Element</span></span>|<span data-ttu-id="561d8-122">描述</span><span class="sxs-lookup"><span data-stu-id="561d8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="561d8-123">\<namespaceTable></span><span class="sxs-lookup"><span data-stu-id="561d8-123">\<namespaceTable></span></span>](namespacetable.md)|<span data-ttu-id="561d8-124">表示用于定义一组元素的配置节，这些元素包含随后可在 XPath 筛选器中用于路由的前缀映射的命名空间。</span><span class="sxs-lookup"><span data-stu-id="561d8-124">Represents a configuration section for defining a set of elements that contain namespace to prefix mappings that can then be used in XPath filters for routing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="561d8-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="561d8-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
