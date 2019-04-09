---
title: Entity Type — 实体类型
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: 026b0aef7cf2de8fe222721191afa459859701ee
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108259"
---
# <a name="entity-type"></a><span data-ttu-id="ecec2-102">Entity Type — 实体类型</span><span class="sxs-lookup"><span data-stu-id="ecec2-102">entity type</span></span>
<span data-ttu-id="ecec2-103">*实体类型*是用于描述实体数据模型 (EDM) 使用的数据结构的基本构建块。</span><span class="sxs-lookup"><span data-stu-id="ecec2-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="ecec2-104">在概念模型中，实体类型表示顶级概念（例如客户或订单）的结构。</span><span class="sxs-lookup"><span data-stu-id="ecec2-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="ecec2-105">实体类型是实体类型实例的模板。</span><span class="sxs-lookup"><span data-stu-id="ecec2-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="ecec2-106">每个模板都包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="ecec2-106">Each template contains the following information:</span></span>  
  
-   <span data-ttu-id="ecec2-107">唯一名称。</span><span class="sxs-lookup"><span data-stu-id="ecec2-107">A unique name.</span></span> <span data-ttu-id="ecec2-108">（必选。）</span><span class="sxs-lookup"><span data-stu-id="ecec2-108">(Required.)</span></span>  
  
-   <span data-ttu-id="ecec2-109">[实体键](../../../../docs/framework/data/adonet/entity-key.md)由一个或多个属性定义。</span><span class="sxs-lookup"><span data-stu-id="ecec2-109">An [entity key](../../../../docs/framework/data/adonet/entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="ecec2-110">（必选。）</span><span class="sxs-lookup"><span data-stu-id="ecec2-110">(Required.)</span></span>  
  
-   <span data-ttu-id="ecec2-111">数据中的窗体[属性](../../../../docs/framework/data/adonet/property.md)。</span><span class="sxs-lookup"><span data-stu-id="ecec2-111">Data in the form of [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="ecec2-112">（可选）。</span><span class="sxs-lookup"><span data-stu-id="ecec2-112">(Optional.)</span></span>  
  
-   <span data-ttu-id="ecec2-113">[导航属性](../../../../docs/framework/data/adonet/navigation-property.md)，用于从一个导航[最终](../../../../docs/framework/data/adonet/association-end.md)的[关联](../../../../docs/framework/data/adonet/association-type.md)到另一端。</span><span class="sxs-lookup"><span data-stu-id="ecec2-113">[Navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) that allow for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="ecec2-114">（可选）</span><span class="sxs-lookup"><span data-stu-id="ecec2-114">(Optional)</span></span>  
  
 <span data-ttu-id="ecec2-115">在应用程序中，实体类型的实例表示一个特定对象（例如特定客户或订单）。</span><span class="sxs-lookup"><span data-stu-id="ecec2-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="ecec2-116">实体类型的每个实例必须具有一个唯一[实体键](../../../../docs/framework/data/adonet/entity-key.md)内[实体集](../../../../docs/framework/data/adonet/entity-set.md)。</span><span class="sxs-lookup"><span data-stu-id="ecec2-116">Each instance of an entity type must have a unique [entity key](../../../../docs/framework/data/adonet/entity-key.md) within an [entity set](../../../../docs/framework/data/adonet/entity-set.md).</span></span>  
  
 <span data-ttu-id="ecec2-117">只有两个实体类型实例的类型相同且其实体键的值也相同时，才认为它们是相等的。</span><span class="sxs-lookup"><span data-stu-id="ecec2-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecec2-118">示例</span><span class="sxs-lookup"><span data-stu-id="ecec2-118">Example</span></span>  
 <span data-ttu-id="ecec2-119">下图显示了一个具有三个实体类型的概念模型：`Book`、`Publisher` 和 `Author`：</span><span class="sxs-lookup"><span data-stu-id="ecec2-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 ![具有三个实体类型的示例模型](./media/entity-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="ecec2-121">请注意，构成其实体键的每个实体类型的属性均用“(Key)”标示出来。</span><span class="sxs-lookup"><span data-stu-id="ecec2-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="ecec2-122">[ADO.NET 实体框架](../../../../docs/framework/data/adonet/ef/index.md)使用称为概念性架构定义语言的特定于域的语言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="ecec2-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="ecec2-123">下面的 CSDL 定义了上图中显示的 `Book` 实体类型。</span><span class="sxs-lookup"><span data-stu-id="ecec2-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="ecec2-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="ecec2-124">See also</span></span>

- [<span data-ttu-id="ecec2-125">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="ecec2-125">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="ecec2-126">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="ecec2-126">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
- [<span data-ttu-id="ecec2-127">facet</span><span class="sxs-lookup"><span data-stu-id="ecec2-127">facet</span></span>](../../../../docs/framework/data/adonet/facet.md)
