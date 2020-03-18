---
title: 执行分组联接（C# 中的 LINQ）
description: 了解如何使用 C# 中的 LINQ 执行分组联接。
ms.date: 12/01/2016
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: dfb75b55336d8ca486d5f10b187e955d20cd06fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "61689133"
---
# <a name="perform-grouped-joins"></a><span data-ttu-id="b634c-103">执行分组联接</span><span class="sxs-lookup"><span data-stu-id="b634c-103">Perform grouped joins</span></span>

<span data-ttu-id="b634c-104">分组联接对于生成分层数据结构十分有用。</span><span class="sxs-lookup"><span data-stu-id="b634c-104">The group join is useful for producing hierarchical data structures.</span></span> <span data-ttu-id="b634c-105">它将第一个集合中的每个元素与第二个集合中的一组相关元素进行配对。</span><span class="sxs-lookup"><span data-stu-id="b634c-105">It pairs each element from the first collection with a set of correlated elements from the second collection.</span></span>

<span data-ttu-id="b634c-106">例如，一个名为 `Student` 的类或关系数据库表可能包含两个字段：`Id` 和 `Name`。</span><span class="sxs-lookup"><span data-stu-id="b634c-106">For example, a class or a relational database table named `Student` might contain two fields: `Id` and `Name`.</span></span> <span data-ttu-id="b634c-107">另一个名为 `Course` 的类或关系数据库表可能包含两个字段：`StudentId` 和 `CourseTitle`。</span><span class="sxs-lookup"><span data-stu-id="b634c-107">A second class or relational database table named `Course` might contain two fields: `StudentId` and `CourseTitle`.</span></span> <span data-ttu-id="b634c-108">这两个数据源的分组联接（基于匹配 `Student.Id` 和 `Course.StudentId`）会对具有 `Student` 对象集合（可能为空）的每个 `Course` 进行分组。</span><span class="sxs-lookup"><span data-stu-id="b634c-108">A group join of these two data sources, based on matching `Student.Id` and `Course.StudentId`, would group each `Student` with a collection of `Course` objects (which might be empty).</span></span>

> [!NOTE]
> <span data-ttu-id="b634c-109">第一个集合的每个元素都会出现在分组联接的结果集中（无论是否在第二个集合中找到关联元素）。</span><span class="sxs-lookup"><span data-stu-id="b634c-109">Each element of the first collection appears in the result set of a group join regardless of whether correlated elements are found in the second collection.</span></span> <span data-ttu-id="b634c-110">在未找到任何相关元素的情况下，该元素的相关元素序列为空。</span><span class="sxs-lookup"><span data-stu-id="b634c-110">In the case where no correlated elements are found, the sequence of correlated elements for that element is empty.</span></span> <span data-ttu-id="b634c-111">因此，结果选择器有权访问第一个集合的每个元素。</span><span class="sxs-lookup"><span data-stu-id="b634c-111">The result selector therefore has access to every element of the first collection.</span></span> <span data-ttu-id="b634c-112">这与非分组联接中的结果选择器不同，后者无法访问第一个集合中在第二个集合中没有匹配项的元素。</span><span class="sxs-lookup"><span data-stu-id="b634c-112">This differs from the result selector in a non-group join, which cannot access elements from the first collection that have no match in the second collection.</span></span>

<span data-ttu-id="b634c-113">本文的第一个示例演示如何执行分组联接。</span><span class="sxs-lookup"><span data-stu-id="b634c-113">The first example in this article shows you how to perform a group join.</span></span> <span data-ttu-id="b634c-114">第二个示例演示如何使用分组联接创建 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="b634c-114">The second example shows you how to use a group join to create XML elements.</span></span>

## <a name="example---group-join"></a><span data-ttu-id="b634c-115">示例 - 分组联接</span><span class="sxs-lookup"><span data-stu-id="b634c-115">Example - Group join</span></span>

<span data-ttu-id="b634c-116">下面的示例基于与 `Person` 属性匹配的 `Pet`，来执行类型 `Person` 和 `Pet.Owner` 的对象的分组联接。</span><span class="sxs-lookup"><span data-stu-id="b634c-116">The following example performs a group join of objects of type `Person` and `Pet` based on the `Person` matching the `Pet.Owner` property.</span></span> <span data-ttu-id="b634c-117">与非分组联接（会为每个匹配生成元素对）不同，分组联接只为第一个集合的每个元素生成一个结果对象（在此示例中为 `Person` 对象）。</span><span class="sxs-lookup"><span data-stu-id="b634c-117">Unlike a non-group join, which would produce a pair of elements for each match, the group join produces only one resulting object for each element of the first collection, which in this example is a `Person` object.</span></span> <span data-ttu-id="b634c-118">第二个集合中的对应元素（在此示例中为 `Pet` 对象）会分组到集合中。</span><span class="sxs-lookup"><span data-stu-id="b634c-118">The corresponding elements from the second collection, which in this example are `Pet` objects, are grouped into a collection.</span></span> <span data-ttu-id="b634c-119">最后，结果选择器函数会为每个匹配都创建一种匿名类型，其中包含 `Person.FirstName` 和 `Pet` 对象集合。</span><span class="sxs-lookup"><span data-stu-id="b634c-119">Finally, the result selector function creates an anonymous type for each match that consists of `Person.FirstName` and a collection of `Pet` objects.</span></span>

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a><span data-ttu-id="b634c-120">示例 - 用于创建 XML 的分组联接</span><span class="sxs-lookup"><span data-stu-id="b634c-120">Example - Group join to create XML</span></span>

<span data-ttu-id="b634c-121">分组联接非常适合于使用 LINQ to XML 创建 XML。</span><span class="sxs-lookup"><span data-stu-id="b634c-121">Group joins are ideal for creating XML by using LINQ to XML.</span></span> <span data-ttu-id="b634c-122">下面的示例类似于上面的示例，不过结果选择器函数不会创建匿名类型，而是创建表示联接对象的 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="b634c-122">The following example is similar to the previous example except that instead of creating anonymous types, the result selector function creates XML elements that represent the joined objects.</span></span>

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a><span data-ttu-id="b634c-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b634c-123">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [<span data-ttu-id="b634c-124">执行内部联接</span><span class="sxs-lookup"><span data-stu-id="b634c-124">Perform inner joins</span></span>](perform-inner-joins.md)
- [<span data-ttu-id="b634c-125">执行左外部联接</span><span class="sxs-lookup"><span data-stu-id="b634c-125">Perform left outer joins</span></span>](perform-left-outer-joins.md)
- [<span data-ttu-id="b634c-126">匿名类型</span><span class="sxs-lookup"><span data-stu-id="b634c-126">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)
