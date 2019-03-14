---
title: 集运算 (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 169f7608409fcc0205a1f8edc69ee7a0b7785a51
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675506"
---
# <a name="set-operations-c"></a><span data-ttu-id="168c4-102">集运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="168c4-102">Set Operations (C#)</span></span>
<span data-ttu-id="168c4-103">LINQ 中的集运算是指根据相同或不同集合（或集）中是否存在等效元素来生成结果集的查询运算。</span><span class="sxs-lookup"><span data-stu-id="168c4-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="168c4-104">下节列出了执行集运算的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="168c4-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="168c4-105">方法</span><span class="sxs-lookup"><span data-stu-id="168c4-105">Methods</span></span>  
  
|<span data-ttu-id="168c4-106">方法名</span><span class="sxs-lookup"><span data-stu-id="168c4-106">Method Name</span></span>|<span data-ttu-id="168c4-107">说明</span><span class="sxs-lookup"><span data-stu-id="168c4-107">Description</span></span>|<span data-ttu-id="168c4-108">C# 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="168c4-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="168c4-109">详细信息</span><span class="sxs-lookup"><span data-stu-id="168c4-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="168c4-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="168c4-110">Distinct</span></span>|<span data-ttu-id="168c4-111">删除集合中的重复值。</span><span class="sxs-lookup"><span data-stu-id="168c4-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="168c4-112">不适用。</span><span class="sxs-lookup"><span data-stu-id="168c4-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="168c4-113">Except</span><span class="sxs-lookup"><span data-stu-id="168c4-113">Except</span></span>|<span data-ttu-id="168c4-114">返回差集，差集指位于一个集合但不位于另一个集合的元素。</span><span class="sxs-lookup"><span data-stu-id="168c4-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="168c4-115">不适用。</span><span class="sxs-lookup"><span data-stu-id="168c4-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="168c4-116">相交</span><span class="sxs-lookup"><span data-stu-id="168c4-116">Intersect</span></span>|<span data-ttu-id="168c4-117">返回交集，交集指同时出现在两个集合中的元素。</span><span class="sxs-lookup"><span data-stu-id="168c4-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="168c4-118">不适用。</span><span class="sxs-lookup"><span data-stu-id="168c4-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="168c4-119">联合</span><span class="sxs-lookup"><span data-stu-id="168c4-119">Union</span></span>|<span data-ttu-id="168c4-120">返回并集，并集指位于两个集合中任一集合的唯一的元素。</span><span class="sxs-lookup"><span data-stu-id="168c4-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="168c4-121">不适用。</span><span class="sxs-lookup"><span data-stu-id="168c4-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="168c4-122">比较集运算</span><span class="sxs-lookup"><span data-stu-id="168c4-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="168c4-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="168c4-123">Distinct</span></span>  
 <span data-ttu-id="168c4-124">下图演示字符序列上 <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> 方法的行为。</span><span class="sxs-lookup"><span data-stu-id="168c4-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="168c4-125">返回的序列包含输入序列的唯一元素。</span><span class="sxs-lookup"><span data-stu-id="168c4-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="168c4-126">![演示 Distinct&#40;&#41; 的行为的图。](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span><span class="sxs-lookup"><span data-stu-id="168c4-126">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="168c4-127">Except</span><span class="sxs-lookup"><span data-stu-id="168c4-127">Except</span></span>  
 <span data-ttu-id="168c4-128">下图演示 <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> 的行为。</span><span class="sxs-lookup"><span data-stu-id="168c4-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="168c4-129">返回的序列只包含位于第一个输入序列但不位于第二个输入序列的元素。</span><span class="sxs-lookup"><span data-stu-id="168c4-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="168c4-130">![显示 Except&#40;&#41; 操作的图形](./media/set-operations/except-behavior-graphic.png "显示 Except 的行为。")</span><span class="sxs-lookup"><span data-stu-id="168c4-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="168c4-131">相交</span><span class="sxs-lookup"><span data-stu-id="168c4-131">Intersect</span></span>  
 <span data-ttu-id="168c4-132">下图演示 <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> 的行为。</span><span class="sxs-lookup"><span data-stu-id="168c4-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="168c4-133">返回的序列包含两个输入序列共有的元素。</span><span class="sxs-lookup"><span data-stu-id="168c4-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="168c4-134">![显示两个序列的交集的图。](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span><span class="sxs-lookup"><span data-stu-id="168c4-134">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="168c4-135">联合</span><span class="sxs-lookup"><span data-stu-id="168c4-135">Union</span></span>  
 <span data-ttu-id="168c4-136">下图演示对两个字符序列执行的联合操作。</span><span class="sxs-lookup"><span data-stu-id="168c4-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="168c4-137">返回的序列包含两个输入序列的唯一元素。</span><span class="sxs-lookup"><span data-stu-id="168c4-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="168c4-138">![显示两个序列的联合的图。](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span><span class="sxs-lookup"><span data-stu-id="168c4-138">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="168c4-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="168c4-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="168c4-140">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="168c4-140">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="168c4-141">如何：组合和比较字符串集合 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="168c4-141">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="168c4-142">如何：查找两个列表之间的差集 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="168c4-142">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
