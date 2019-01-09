---
title: '&lt;policyImporter&gt;'
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 22d90ff9d0cd5325300cf42437836f075cbf8c31
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148482"
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="739d1-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="739d1-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="739d1-103">指定一个策略导入程序，用于控制有关绑定的自定义策略断言的导入。</span><span class="sxs-lookup"><span data-stu-id="739d1-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="739d1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="739d1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="739d1-105">\<客户端 ></span><span class="sxs-lookup"><span data-stu-id="739d1-105">\<client></span></span>  
<span data-ttu-id="739d1-106">\<元数据 ></span><span class="sxs-lookup"><span data-stu-id="739d1-106">\<metadata></span></span>  
<span data-ttu-id="739d1-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="739d1-107">\<policyImporters></span></span>  
<span data-ttu-id="739d1-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="739d1-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="739d1-109">语法</span><span class="sxs-lookup"><span data-stu-id="739d1-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="739d1-110">特性和元素</span><span class="sxs-lookup"><span data-stu-id="739d1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="739d1-111">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="739d1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="739d1-112">特性</span><span class="sxs-lookup"><span data-stu-id="739d1-112">Attributes</span></span>  
  
|<span data-ttu-id="739d1-113">特性</span><span class="sxs-lookup"><span data-stu-id="739d1-113">Attribute</span></span>|<span data-ttu-id="739d1-114">描述</span><span class="sxs-lookup"><span data-stu-id="739d1-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="739d1-115">此元素的类型。</span><span class="sxs-lookup"><span data-stu-id="739d1-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="739d1-116">子元素</span><span class="sxs-lookup"><span data-stu-id="739d1-116">Child Elements</span></span>  
 <span data-ttu-id="739d1-117">无</span><span class="sxs-lookup"><span data-stu-id="739d1-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="739d1-118">父元素</span><span class="sxs-lookup"><span data-stu-id="739d1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="739d1-119">元素</span><span class="sxs-lookup"><span data-stu-id="739d1-119">Element</span></span>|<span data-ttu-id="739d1-120">描述</span><span class="sxs-lookup"><span data-stu-id="739d1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="739d1-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="739d1-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="739d1-122">指定用于控制有关绑定的自定义策略断言的导入的所有策略导入程序。</span><span class="sxs-lookup"><span data-stu-id="739d1-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="739d1-123">备注</span><span class="sxs-lookup"><span data-stu-id="739d1-123">Remarks</span></span>  
 <span data-ttu-id="739d1-124">策略导入程序用于搜索有关绑定功能的自定义策略断言，并附加一个实现断言所需功能的自定义绑定元素。</span><span class="sxs-lookup"><span data-stu-id="739d1-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="739d1-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="739d1-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="739d1-126">WCF 客户端配置</span><span class="sxs-lookup"><span data-stu-id="739d1-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="739d1-127">客户端</span><span class="sxs-lookup"><span data-stu-id="739d1-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
