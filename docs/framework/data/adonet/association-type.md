---
title: 关联类型
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 7fbdc0316b1f9fd0bb282fd466857b1426c41df1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583715"
---
# <a name="association-type"></a><span data-ttu-id="1e40f-102">关联类型</span><span class="sxs-lookup"><span data-stu-id="1e40f-102">association type</span></span>
<span data-ttu-id="1e40f-103">*关联类型*（也称为关联） 是用于描述实体数据模型 (EDM) 中的关系的基本构建块。</span><span class="sxs-lookup"><span data-stu-id="1e40f-103">An *association type* (also called an association) is the fundamental building block for describing relationships in the Entity Data Model (EDM).</span></span> <span data-ttu-id="1e40f-104">在概念模型中，关联表示两个之间的关系[实体类型](../../../../docs/framework/data/adonet/entity-type.md)(如`Customer`和`Order`)。</span><span class="sxs-lookup"><span data-stu-id="1e40f-104">In a conceptual model, an association represents a relationship between two [entity types](../../../../docs/framework/data/adonet/entity-type.md) (such as `Customer` and `Order`).</span></span> <span data-ttu-id="1e40f-105">在应用程序中，一个关联实例表示一个特定的关联（例如 `Customer` 实例与 `Order` 实例之间的关联）。</span><span class="sxs-lookup"><span data-stu-id="1e40f-105">In an application, an instance of an association represents a specific association (such as an association between an instance of `Customer` and an instance of `Order`).</span></span> <span data-ttu-id="1e40f-106">关联实例按逻辑分组在[关联集](../../../../docs/framework/data/adonet/association-set.md)。</span><span class="sxs-lookup"><span data-stu-id="1e40f-106">Association instances are logically grouped in an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span>  
  
 <span data-ttu-id="1e40f-107">关联定义包含以下信息：</span><span class="sxs-lookup"><span data-stu-id="1e40f-107">An association definition contains the following information:</span></span>  
  
- <span data-ttu-id="1e40f-108">唯一名称。</span><span class="sxs-lookup"><span data-stu-id="1e40f-108">A unique name.</span></span> <span data-ttu-id="1e40f-109">（必需）</span><span class="sxs-lookup"><span data-stu-id="1e40f-109">(Required)</span></span>  
  
- <span data-ttu-id="1e40f-110">两个[关联端](../../../../docs/framework/data/adonet/association-end.md)，一个用于在关系中每个实体类型。</span><span class="sxs-lookup"><span data-stu-id="1e40f-110">Two [association ends](../../../../docs/framework/data/adonet/association-end.md), one for each entity type in the relationship.</span></span> <span data-ttu-id="1e40f-111">（必需）</span><span class="sxs-lookup"><span data-stu-id="1e40f-111">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1e40f-112">关联不能表示两个以上的实体类型之间的关系。</span><span class="sxs-lookup"><span data-stu-id="1e40f-112">An association cannot represent a relationship among more than two entity types.</span></span> <span data-ttu-id="1e40f-113">但是，通过为每个关联端指定相同的实体类型，关联可以定义自身关系。</span><span class="sxs-lookup"><span data-stu-id="1e40f-113">An association can, however, define a self-relationship by specifying the same entity type for each of its association ends.</span></span>  
  
- <span data-ttu-id="1e40f-114">一个[引用完整性约束](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="1e40f-114">A [referential integrity constraint](../../../../docs/framework/data/adonet/referential-integrity-constraint.md).</span></span> <span data-ttu-id="1e40f-115">（可选）</span><span class="sxs-lookup"><span data-stu-id="1e40f-115">(Optional)</span></span>  
  
 <span data-ttu-id="1e40f-116">每个关联端必须指定[关联端重数](../../../../docs/framework/data/adonet/association-end-multiplicity.md)，该值指示关联的一端可以存在的实体类型实例数。</span><span class="sxs-lookup"><span data-stu-id="1e40f-116">Each association end must specify an [association end multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="1e40f-117">关联端重数可以具有值为一 (1) 零或一 (0..1) 或许多 (\*)。</span><span class="sxs-lookup"><span data-stu-id="1e40f-117">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span> <span data-ttu-id="1e40f-118">可以通过访问实体类型实例的关联某一端[导航属性](../../../../docs/framework/data/adonet/navigation-property.md)或如果在实体类型上公开了外键。</span><span class="sxs-lookup"><span data-stu-id="1e40f-118">Entity type instances at one end of an association can be accessed through [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) or foreign keys if they are exposed on an entity type.</span></span> <span data-ttu-id="1e40f-119">有关详细信息，请参阅[实体数据模型：外键](../../../../docs/framework/data/adonet/foreign-key-property.md)。</span><span class="sxs-lookup"><span data-stu-id="1e40f-119">For more information, see [Entity Data Model: Foreign Keys](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e40f-120">示例</span><span class="sxs-lookup"><span data-stu-id="1e40f-120">Example</span></span>  
 <span data-ttu-id="1e40f-121">下图显示了一个具有两个关联的概念模型：`PublishedBy` 和 `WrittenBy`。</span><span class="sxs-lookup"><span data-stu-id="1e40f-121">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="1e40f-122">`PublishedBy` 关联的关联端是 `Book` 和 `Publisher` 实体类型。</span><span class="sxs-lookup"><span data-stu-id="1e40f-122">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="1e40f-123">多重性`Publisher`最终为一 (1) 和重数`Book`最终为多个 (\*)，指示，出版商可以出版很多书而一本书只能由一个出版商出版。</span><span class="sxs-lookup"><span data-stu-id="1e40f-123">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![具有三个实体类型的示例模型](./media/association-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="1e40f-125">[ADO.NET 实体框架](../../../../docs/framework/data/adonet/ef/index.md)使用称为概念性架构定义语言的特定于域的语言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="1e40f-125">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="1e40f-126">下面的 CSDL 定义了上图中显示的 `PublishedBy` 关联：</span><span class="sxs-lookup"><span data-stu-id="1e40f-126">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="1e40f-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="1e40f-127">See also</span></span>

- [<span data-ttu-id="1e40f-128">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="1e40f-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="1e40f-129">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="1e40f-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
