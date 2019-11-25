---
title: 聚合操作
ms.date: 07/20/2015
ms.assetid: 0f47e92c-5dd2-4007-baf4-c5fe5dc3b4a8
ms.openlocfilehash: 5c7f9344d379af2fed2a8f3d9f7c031c8ca00e8c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345780"
---
# <a name="aggregation-operations-visual-basic"></a><span data-ttu-id="3a343-102">Aggregation Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a343-102">Aggregation Operations (Visual Basic)</span></span>
<span data-ttu-id="3a343-103">聚合运算从值的集合中计算出单个值。</span><span class="sxs-lookup"><span data-stu-id="3a343-103">An aggregation operation computes a single value from a collection of values.</span></span> <span data-ttu-id="3a343-104">例如，从一个月累计的每日温度值计算出日平均温度值就是一个聚合运算。</span><span class="sxs-lookup"><span data-stu-id="3a343-104">An example of an aggregation operation is calculating the average daily temperature from a month's worth of daily temperature values.</span></span>  
  
 <span data-ttu-id="3a343-105">下图显示对数字序列进行两种不同聚合操作所得结果。</span><span class="sxs-lookup"><span data-stu-id="3a343-105">The following illustration shows the results of two different aggregation operations on a sequence of numbers.</span></span> <span data-ttu-id="3a343-106">第一个操作累加数字。</span><span class="sxs-lookup"><span data-stu-id="3a343-106">The first operation sums the numbers.</span></span> <span data-ttu-id="3a343-107">第二个操作返回序列中的最大值。</span><span class="sxs-lookup"><span data-stu-id="3a343-107">The second operation returns the maximum value in the sequence.</span></span>  
  
 ![显示 LINQ 聚合运算的插图。](./media/aggregation-operations/linq-aggregation-operations.png)  
  
 <span data-ttu-id="3a343-109">下节列出了执行聚合运算的标准查询运算符方法。</span><span class="sxs-lookup"><span data-stu-id="3a343-109">The standard query operator methods that perform aggregation operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a343-110">方法</span><span class="sxs-lookup"><span data-stu-id="3a343-110">Methods</span></span>  
  
|<span data-ttu-id="3a343-111">方法名</span><span class="sxs-lookup"><span data-stu-id="3a343-111">Method Name</span></span>|<span data-ttu-id="3a343-112">描述</span><span class="sxs-lookup"><span data-stu-id="3a343-112">Description</span></span>|<span data-ttu-id="3a343-113">Visual Basic Query Expression Syntax</span><span class="sxs-lookup"><span data-stu-id="3a343-113">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="3a343-114">详细信息</span><span class="sxs-lookup"><span data-stu-id="3a343-114">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="3a343-115">聚合</span><span class="sxs-lookup"><span data-stu-id="3a343-115">Aggregate</span></span>|<span data-ttu-id="3a343-116">对集合的值执行自定义聚合运算。</span><span class="sxs-lookup"><span data-stu-id="3a343-116">Performs a custom aggregation operation on the values of a collection.</span></span>|<span data-ttu-id="3a343-117">不适用。</span><span class="sxs-lookup"><span data-stu-id="3a343-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Aggregate%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3a343-118">平均值</span><span class="sxs-lookup"><span data-stu-id="3a343-118">Average</span></span>|<span data-ttu-id="3a343-119">计算值集合的平均值。</span><span class="sxs-lookup"><span data-stu-id="3a343-119">Calculates the average value of a collection of values.</span></span>|`Aggregate … In … Into Average()`|<xref:System.Linq.Enumerable.Average%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Average%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3a343-120">计数</span><span class="sxs-lookup"><span data-stu-id="3a343-120">Count</span></span>|<span data-ttu-id="3a343-121">对集合中元素计数，可选择仅对满足谓词函数的元素计数。</span><span class="sxs-lookup"><span data-stu-id="3a343-121">Counts the elements in a collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into Count()`|<xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Count%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3a343-122">LongCount</span><span class="sxs-lookup"><span data-stu-id="3a343-122">LongCount</span></span>|<span data-ttu-id="3a343-123">对大型集合中元素计数，可选择仅对满足谓词函数的元素计数。</span><span class="sxs-lookup"><span data-stu-id="3a343-123">Counts the elements in a large collection, optionally only those elements that satisfy a predicate function.</span></span>|`Aggregate … In … Into LongCount()`|<xref:System.Linq.Enumerable.LongCount%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.LongCount%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3a343-124">最大值</span><span class="sxs-lookup"><span data-stu-id="3a343-124">Max</span></span>|<span data-ttu-id="3a343-125">确定集合中的最大值。</span><span class="sxs-lookup"><span data-stu-id="3a343-125">Determines the maximum value in a collection.</span></span>|`Aggregate … In … Into Max()`|<xref:System.Linq.Enumerable.Max%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Max%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3a343-126">最小值</span><span class="sxs-lookup"><span data-stu-id="3a343-126">Min</span></span>|<span data-ttu-id="3a343-127">确定集合中的最小值。</span><span class="sxs-lookup"><span data-stu-id="3a343-127">Determines the minimum value in a collection.</span></span>|`Aggregate … In … Into Min()`|<xref:System.Linq.Enumerable.Min%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Min%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3a343-128">Sum</span><span class="sxs-lookup"><span data-stu-id="3a343-128">Sum</span></span>|<span data-ttu-id="3a343-129">对集合中的值求和。</span><span class="sxs-lookup"><span data-stu-id="3a343-129">Calculates the sum of the values in a collection.</span></span>|`Aggregate … In … Into Sum()`|<xref:System.Linq.Enumerable.Sum%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Sum%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="3a343-130">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="3a343-130">Query Expression Syntax Examples</span></span>  
  
### <a name="average"></a><span data-ttu-id="3a343-131">平均值</span><span class="sxs-lookup"><span data-stu-id="3a343-131">Average</span></span>  
 <span data-ttu-id="3a343-132">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span><span class="sxs-lookup"><span data-stu-id="3a343-132">The following code example uses the `Aggregate Into Average` clause in Visual Basic to calculate the average temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#1)]  
  
### <a name="count"></a><span data-ttu-id="3a343-133">计数</span><span class="sxs-lookup"><span data-stu-id="3a343-133">Count</span></span>  
 <span data-ttu-id="3a343-134">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span><span class="sxs-lookup"><span data-stu-id="3a343-134">The following code example uses the `Aggregate Into Count` clause in Visual Basic to count the number of values in an array that are greater than or equal to 80.</span></span>  
  
 [!code-vb[CsLINQAggregating#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#2)]  
  
### <a name="longcount"></a><span data-ttu-id="3a343-135">LongCount</span><span class="sxs-lookup"><span data-stu-id="3a343-135">LongCount</span></span>  
 <span data-ttu-id="3a343-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span><span class="sxs-lookup"><span data-stu-id="3a343-136">The following code example uses the `Aggregate Into LongCount` clause to count the number of values in an array.</span></span>  
  
 [!code-vb[CsLINQAggregating#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#3)]  
  
### <a name="max"></a><span data-ttu-id="3a343-137">最大值</span><span class="sxs-lookup"><span data-stu-id="3a343-137">Max</span></span>  
 <span data-ttu-id="3a343-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span><span class="sxs-lookup"><span data-stu-id="3a343-138">The following code example uses the `Aggregate Into Max` clause  to calculate the maximum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#4)]  
  
### <a name="min"></a><span data-ttu-id="3a343-139">最小值</span><span class="sxs-lookup"><span data-stu-id="3a343-139">Min</span></span>  
 <span data-ttu-id="3a343-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span><span class="sxs-lookup"><span data-stu-id="3a343-140">The following code example uses the `Aggregate Into Min` clause  to calculate the minimum temperature in an array of numbers that represent temperatures.</span></span>  
  
 [!code-vb[CsLINQAggregating#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#5)]  
  
### <a name="sum"></a><span data-ttu-id="3a343-141">Sum</span><span class="sxs-lookup"><span data-stu-id="3a343-141">Sum</span></span>  
 <span data-ttu-id="3a343-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span><span class="sxs-lookup"><span data-stu-id="3a343-142">The following code example uses the `Aggregate Into Sum` clause  to calculate the total expense amount from an array of values that represent expenses.</span></span>  
  
 [!code-vb[CsLINQAggregating#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAggregating/VB/Aggregating.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="3a343-143">请参阅</span><span class="sxs-lookup"><span data-stu-id="3a343-143">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="3a343-144">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a343-144">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="3a343-145">Aggregate 子句</span><span class="sxs-lookup"><span data-stu-id="3a343-145">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="3a343-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a343-146">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-compute-column-values-in-a-csv-text-file-linq.md)
- [<span data-ttu-id="3a343-147">如何：对数据进行计数、求和与求平均值计算</span><span class="sxs-lookup"><span data-stu-id="3a343-147">How to: Count, Sum, or Average Data</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-count-sum-or-average-data-by-using-linq.md)
- [<span data-ttu-id="3a343-148">如何：查找查询结果中的最小值或最大值</span><span class="sxs-lookup"><span data-stu-id="3a343-148">How to: Find the Minimum or Maximum Value in a Query Result</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)
- [<span data-ttu-id="3a343-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a343-149">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)
- [<span data-ttu-id="3a343-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a343-150">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)
