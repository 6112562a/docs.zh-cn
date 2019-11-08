---
title: 实体数据模型
ms.date: 03/30/2017
ms.assetid: 2dda3d5b-4582-4ba0-a91d-fcd7a1498137
ms.openlocfilehash: ed834c57104e9f03ac337f6c1d30a0498bd42a06
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738409"
---
# <a name="entity-data-model"></a><span data-ttu-id="c550c-102">实体数据模型</span><span class="sxs-lookup"><span data-stu-id="c550c-102">Entity Data Model</span></span>
<span data-ttu-id="c550c-103">实体数据模型 (EDM) 是一组描述数据结构（而不管其存储形式如何）的概念。</span><span class="sxs-lookup"><span data-stu-id="c550c-103">The Entity Data Model (EDM) is a set of concepts that describe the structure of data, regardless of its stored form.</span></span> <span data-ttu-id="c550c-104">EDM 借自于 Peter Chen 于 1976 年所描述的实体关系模型，但它是在实体关系模型基础上构建的并扩展了其传统用途。</span><span class="sxs-lookup"><span data-stu-id="c550c-104">The EDM borrows from the Entity-Relationship Model described by Peter Chen in 1976, but it also builds on the Entity-Relationship Model and extends its traditional uses.</span></span>  
  
 <span data-ttu-id="c550c-105">EDM 解决了以多种形式存储的数据所带来的难题。</span><span class="sxs-lookup"><span data-stu-id="c550c-105">The EDM addresses the challenges that arise from having data stored in many forms.</span></span> <span data-ttu-id="c550c-106">例如，假设某项业务将数据存储在关系数据库、文本文件、XML 文件、电子表格和报表中。</span><span class="sxs-lookup"><span data-stu-id="c550c-106">For example, consider a business that stores data in relational databases, text files, XML files, spreadsheets, and reports.</span></span> <span data-ttu-id="c550c-107">这在数据建模、应用程序设计和数据访问方面会带来很大的难题。</span><span class="sxs-lookup"><span data-stu-id="c550c-107">This presents significant challenges in data modeling, application design, and data access.</span></span> <span data-ttu-id="c550c-108">当设计面向对象的应用程序时，其困难在于如何编写高效的、可维护的代码而不必牺牲数据访问、存储和可扩展性方面的高效性。</span><span class="sxs-lookup"><span data-stu-id="c550c-108">When designing a data-oriented application, the challenge is to write efficient and maintainable code without sacrificing efficient data access, storage, and scalability.</span></span> <span data-ttu-id="c550c-109">当数据具有关系结构时，其在数据访问、存储和可扩展性方面会非常高效，但编写高效的、可维护的代码则变得非常困难。</span><span class="sxs-lookup"><span data-stu-id="c550c-109">When data has a relational structure, data access, storage, and scalability are very efficient, but writing efficient and maintainable code becomes more difficult.</span></span> <span data-ttu-id="c550c-110">当数据具有对象结构时，上述关系恰好相反：编写高效的、可维护的代码要以牺牲数据访问、存储和可扩展性方面的高效性为代价。</span><span class="sxs-lookup"><span data-stu-id="c550c-110">When data has an object structure, the trade-offs are reversed: Writing efficient and maintainable code comes at the cost of efficient data access, storage, and scalability.</span></span> <span data-ttu-id="c550c-111">即使可以在这些优劣方面找到最佳平衡，但是当将数据从一种形式转变为另一种形式时又会引发新的难题。</span><span class="sxs-lookup"><span data-stu-id="c550c-111">Even if the right balance between these trade-offs can be found, new challenges arise when data is moved from one form to another.</span></span> <span data-ttu-id="c550c-112">实体数据模型通过以独立于任何存储架构的实体和关系的方式描述数据结构解决了这些难题。</span><span class="sxs-lookup"><span data-stu-id="c550c-112">The Entity Data Model addresses these challenges by describing the structure of data in terms of entities and relationships that are independent of any storage schema.</span></span> <span data-ttu-id="c550c-113">这使得数据的存储形式与应用程序设计和开发变得不相关。</span><span class="sxs-lookup"><span data-stu-id="c550c-113">This makes the stored form of data irrelevant to application design and development.</span></span> <span data-ttu-id="c550c-114">此外，由于实体和关系描述的是数据在应用程序中使用时的结构（而不是其存储形式），因此它们会随应用程序的演变而演变。</span><span class="sxs-lookup"><span data-stu-id="c550c-114">And, because entities and relationships describe the structure of data as it is used in an application (not its stored form), they can evolve as an application evolves.</span></span>  
  
 <span data-ttu-id="c550c-115">`conceptual model`是实体和关系的数据结构的特定表示形式，通常用实现 EDM 概念的域特定语言 (DSL) 定义。</span><span class="sxs-lookup"><span data-stu-id="c550c-115">A `conceptual model` is a specific representation of the structure of data as entities and relationships, and is generally defined in a domain-specific language (DSL) that implements the concepts of the EDM.</span></span> <span data-ttu-id="c550c-116">[概念性架构定义语言（CSDL）](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)是一种域特定语言的示例。</span><span class="sxs-lookup"><span data-stu-id="c550c-116">[Conceptual schema definition language (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec) is an example of such a domain-specific language.</span></span> <span data-ttu-id="c550c-117">可以将概念模型中描述的实体和关系视为对应用程序中的对象和关联的一种抽象表述。</span><span class="sxs-lookup"><span data-stu-id="c550c-117">Entities and relationships described in a conceptual model can be thought of as abstractions of objects and associations in an application.</span></span> <span data-ttu-id="c550c-118">这使得开发人员可以专注于概念模型而不必考虑存储架构，从而在编写代码时更多关注高效性和可维护性。</span><span class="sxs-lookup"><span data-stu-id="c550c-118">This allows developers to focus on the conceptual model without concern for the storage schema, and allows them to write code with efficiency and maintainability in mind.</span></span> <span data-ttu-id="c550c-119">与此同时，存储架构设计者可以专注于数据访问、存储和可扩展性方面的高效性。</span><span class="sxs-lookup"><span data-stu-id="c550c-119">Meanwhile storage schema designers can focus on the efficiency of data access, storage, and scalability.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c550c-120">本节内容</span><span class="sxs-lookup"><span data-stu-id="c550c-120">In This Section</span></span>  
 <span data-ttu-id="c550c-121">本节中的主题描述实体数据模型的概念。</span><span class="sxs-lookup"><span data-stu-id="c550c-121">Topics in this section describe the concepts of the Entity Data Model.</span></span> <span data-ttu-id="c550c-122">实现 EDM 的任何 DSL 都应包含这里描述的概念。</span><span class="sxs-lookup"><span data-stu-id="c550c-122">Any DSL that implements the EDM should include the concepts described here.</span></span> <span data-ttu-id="c550c-123">请注意， [ADO.NET 实体框架](./ef/index.md)使用 CSDL 来定义概念模型。</span><span class="sxs-lookup"><span data-stu-id="c550c-123">Note that the [ADO.NET Entity Framework](./ef/index.md) uses CSDL to define conceptual models.</span></span> <span data-ttu-id="c550c-124">有关详细信息，请参阅 [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)。</span><span class="sxs-lookup"><span data-stu-id="c550c-124">For more information, see [CSDL Specification](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec).</span></span>  
  
 [<span data-ttu-id="c550c-125">实体数据模型关键概念</span><span class="sxs-lookup"><span data-stu-id="c550c-125">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)  
  
 [<span data-ttu-id="c550c-126">实体数据模型：命名空间</span><span class="sxs-lookup"><span data-stu-id="c550c-126">Entity Data Model: Namespaces</span></span>](entity-data-model-namespaces.md)  
  
 [<span data-ttu-id="c550c-127">实体数据模型：基元数据类型</span><span class="sxs-lookup"><span data-stu-id="c550c-127">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)  
  
 [<span data-ttu-id="c550c-128">实体数据模型：继承</span><span class="sxs-lookup"><span data-stu-id="c550c-128">Entity Data Model: Inheritance</span></span>](entity-data-model-inheritance.md)  
  
 [<span data-ttu-id="c550c-129">关联端</span><span class="sxs-lookup"><span data-stu-id="c550c-129">association end</span></span>](association-end.md)  
  
 [<span data-ttu-id="c550c-130">关联端重数</span><span class="sxs-lookup"><span data-stu-id="c550c-130">association end multiplicity</span></span>](association-end-multiplicity.md)  
  
 [<span data-ttu-id="c550c-131">关联集</span><span class="sxs-lookup"><span data-stu-id="c550c-131">association set</span></span>](association-set.md)  
  
 [<span data-ttu-id="c550c-132">关联集端</span><span class="sxs-lookup"><span data-stu-id="c550c-132">association set end</span></span>](association-set-end.md)  
  
 [<span data-ttu-id="c550c-133">关联类型</span><span class="sxs-lookup"><span data-stu-id="c550c-133">association type</span></span>](association-type.md)  
  
 [<span data-ttu-id="c550c-134">复杂类型</span><span class="sxs-lookup"><span data-stu-id="c550c-134">complex type</span></span>](complex-type.md)  
  
 [<span data-ttu-id="c550c-135">实体容器</span><span class="sxs-lookup"><span data-stu-id="c550c-135">entity container</span></span>](entity-container.md)  
  
 [<span data-ttu-id="c550c-136">实体键</span><span class="sxs-lookup"><span data-stu-id="c550c-136">entity key</span></span>](entity-key.md)  
  
 [<span data-ttu-id="c550c-137">实体集</span><span class="sxs-lookup"><span data-stu-id="c550c-137">entity set</span></span>](entity-set.md)  
  
 [<span data-ttu-id="c550c-138">实体类型</span><span class="sxs-lookup"><span data-stu-id="c550c-138">entity type</span></span>](entity-type.md)  
  
 [<span data-ttu-id="c550c-139">facet</span><span class="sxs-lookup"><span data-stu-id="c550c-139">facet</span></span>](facet.md)  
  
 [<span data-ttu-id="c550c-140">外键属性</span><span class="sxs-lookup"><span data-stu-id="c550c-140">foreign key property</span></span>](foreign-key-property.md)  
  
 [<span data-ttu-id="c550c-141">模型声明函数</span><span class="sxs-lookup"><span data-stu-id="c550c-141">model-declared function</span></span>](model-declared-function.md)  
  
 [<span data-ttu-id="c550c-142">模型定义函数</span><span class="sxs-lookup"><span data-stu-id="c550c-142">model-defined function</span></span>](model-defined-function.md)  
  
 [<span data-ttu-id="c550c-143">导航属性</span><span class="sxs-lookup"><span data-stu-id="c550c-143">navigation property</span></span>](navigation-property.md)  
  
 [<span data-ttu-id="c550c-144">属性</span><span class="sxs-lookup"><span data-stu-id="c550c-144">property</span></span>](property.md)  
  
 [<span data-ttu-id="c550c-145">引用完整性约束</span><span class="sxs-lookup"><span data-stu-id="c550c-145">referential integrity constraint</span></span>](referential-integrity-constraint.md)  
  
## <a name="see-also"></a><span data-ttu-id="c550c-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="c550c-146">See also</span></span>

- <span data-ttu-id="c550c-147">[ADO.NET 实体数据模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c550c-147">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="c550c-148">[.edmx 文件概述](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c550c-148">[.edmx File Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="c550c-149">CSDL 规范</span><span class="sxs-lookup"><span data-stu-id="c550c-149">CSDL Specification</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
