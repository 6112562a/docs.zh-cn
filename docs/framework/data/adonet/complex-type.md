---
title: Complex Type — 复杂类型
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: 9d63660c441192bbc9ecb48bb3a86030b46461cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879999"
---
# <a name="complex-type"></a><span data-ttu-id="d016f-102">Complex Type — 复杂类型</span><span class="sxs-lookup"><span data-stu-id="d016f-102">complex type</span></span>
<span data-ttu-id="d016f-103">一个*复杂类型*是用于定义上的丰富结构化属性的模板[实体类型](../../../../docs/framework/data/adonet/entity-type.md)或其他复杂类型。</span><span class="sxs-lookup"><span data-stu-id="d016f-103">A *complex type* is a template for defining rich, structured properties on [entity types](../../../../docs/framework/data/adonet/entity-type.md) or on other complex types.</span></span> <span data-ttu-id="d016f-104">每个模板都包含以下内容：</span><span class="sxs-lookup"><span data-stu-id="d016f-104">Each template contains the following:</span></span>  
  
-   <span data-ttu-id="d016f-105">唯一名称。</span><span class="sxs-lookup"><span data-stu-id="d016f-105">A unique name.</span></span> <span data-ttu-id="d016f-106">（必需）</span><span class="sxs-lookup"><span data-stu-id="d016f-106">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d016f-107">复杂类型的名称不能与同一命名空间中的实体类型的名称相同。</span><span class="sxs-lookup"><span data-stu-id="d016f-107">The name of a complex type cannot be the same as an entity type name within the same namespace.</span></span>  
  
-   <span data-ttu-id="d016f-108">一个或多个窗体中的数据[属性](../../../../docs/framework/data/adonet/property.md)。</span><span class="sxs-lookup"><span data-stu-id="d016f-108">Data in the form of one or more [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="d016f-109">（可选）。</span><span class="sxs-lookup"><span data-stu-id="d016f-109">(Optional.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d016f-110">复杂类型的属性可以是另一个复杂类型。</span><span class="sxs-lookup"><span data-stu-id="d016f-110">A property of a complex type can be another complex type.</span></span>  
  
 <span data-ttu-id="d016f-111">复杂类型与实体类型相似，因为复杂类型可以以基元类型属性或其他复杂类型的形式携带数据负载。</span><span class="sxs-lookup"><span data-stu-id="d016f-111">A complex type is similar to an entity type in that a complex type can carry a data payload in the form of primitive type properties or other complex types.</span></span> <span data-ttu-id="d016f-112">但是，在复杂类型与实体类型之间仍存在着一些重要区别：</span><span class="sxs-lookup"><span data-stu-id="d016f-112">However, there are some key differences between complex types and entity types:</span></span>  
  
-   <span data-ttu-id="d016f-113">复杂类型没有标识，因此不能独立存在。</span><span class="sxs-lookup"><span data-stu-id="d016f-113">Complex types do not have identities and therefore cannot exist independently.</span></span> <span data-ttu-id="d016f-114">复杂类型只能作为实体类型或其他复杂类型的属性而存在。</span><span class="sxs-lookup"><span data-stu-id="d016f-114">Complex types can only exist as properties on entity types or other complex types.</span></span>  
  
-   <span data-ttu-id="d016f-115">复杂类型不能参与[关联](../../../../docs/framework/data/adonet/association-type.md)。</span><span class="sxs-lookup"><span data-stu-id="d016f-115">Complex types cannot participate in [associations](../../../../docs/framework/data/adonet/association-type.md).</span></span> <span data-ttu-id="d016f-116">关联的任一端都不能是复杂类型，因此[导航属性](../../../../docs/framework/data/adonet/navigation-property.md)不能为复杂类型定义。</span><span class="sxs-lookup"><span data-stu-id="d016f-116">Neither end of an association can be a complex type, and therefore [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) cannot be defined on complex types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d016f-117">示例</span><span class="sxs-lookup"><span data-stu-id="d016f-117">Example</span></span>  
 <span data-ttu-id="d016f-118">[ADO.NET 实体框架](../../../../docs/framework/data/adonet/ef/index.md)使用称为概念性架构定义语言的特定于域的语言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="d016f-118">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="d016f-119">下面的 CSDL 定义了一个复杂类型 Address，它具有基元类型属性 `StreetAddress`、`City`、`StateOrProvince`、`Country` 和 `PostalCode`。</span><span class="sxs-lookup"><span data-stu-id="d016f-119">The following CSDL defines a complex type, Address, with the primitive type properties `StreetAddress`, `City`, `StateOrProvince`, `Country`, and `PostalCode`.</span></span>  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 <span data-ttu-id="d016f-120">若要将复杂类型 `Address`（如上所示）定义为某个实体类型的属性，必须在实体类型定义中声明该属性类型。</span><span class="sxs-lookup"><span data-stu-id="d016f-120">To define the complex type `Address` (above) as a property on an entity type, you must declare the property type in the entity type definition.</span></span> <span data-ttu-id="d016f-121">下面的 CSDL 将 `Address` 属性声明为实体类型 (Publisher) 的复杂类型：</span><span class="sxs-lookup"><span data-stu-id="d016f-121">The following CSDL declares the `Address` property as a complex type on an entity type (Publisher):</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a><span data-ttu-id="d016f-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="d016f-122">See also</span></span>

- [<span data-ttu-id="d016f-123">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="d016f-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="d016f-124">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="d016f-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
