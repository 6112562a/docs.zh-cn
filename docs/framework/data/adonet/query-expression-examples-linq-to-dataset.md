---
title: 查询表达式示例 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: f743fbc7-faff-45e5-af1e-61577d87f0cc
ms.openlocfilehash: 98acbbc3b2271fac0d44728becdaffd09e5d28b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584709"
---
# <a name="query-expression-examples-linq-to-dataset"></a><span data-ttu-id="fb7ed-102">查询表达式示例 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="fb7ed-102">Query Expression Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="fb7ed-103">本节提供使用标准查询运算符的查询表达式语法的 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 编程示例。</span><span class="sxs-lookup"><span data-stu-id="fb7ed-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples in query expression syntax that use the standard query operators.</span></span> <span data-ttu-id="fb7ed-104"><xref:System.Data.DataSet>这些示例中使用通过使用填充`FillDataSet`方法中指定[加载数据到数据集](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)。</span><span class="sxs-lookup"><span data-stu-id="fb7ed-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="fb7ed-105">有关详细信息，请参阅[标准查询运算符概述](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)。</span><span class="sxs-lookup"><span data-stu-id="fb7ed-105">For more information, see [Standard Query Operators Overview](https://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fb7ed-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="fb7ed-106">In This Section</span></span>  
 [<span data-ttu-id="fb7ed-107">投影</span><span class="sxs-lookup"><span data-stu-id="fb7ed-107">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
 <span data-ttu-id="fb7ed-108">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法来查询 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="fb7ed-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="fb7ed-109">限制</span><span class="sxs-lookup"><span data-stu-id="fb7ed-109">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
 <span data-ttu-id="fb7ed-110">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Where%2A> 方法来查询 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="fb7ed-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="fb7ed-111">分区</span><span class="sxs-lookup"><span data-stu-id="fb7ed-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
 <span data-ttu-id="fb7ed-112">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Take%2A> 方法来查询 <xref:System.Data.DataSet> 并分隔结果。</span><span class="sxs-lookup"><span data-stu-id="fb7ed-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="fb7ed-113">订购</span><span class="sxs-lookup"><span data-stu-id="fb7ed-113">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="fb7ed-114">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A> 和 <xref:System.Linq.Enumerable.ThenByDescending%2A> 方法来查询 <xref:System.Data.DataSet> 并排序结果。</span><span class="sxs-lookup"><span data-stu-id="fb7ed-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="fb7ed-115">元素运算符</span><span class="sxs-lookup"><span data-stu-id="fb7ed-115">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
 <span data-ttu-id="fb7ed-116">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.First%2A> 和 <xref:System.Linq.Enumerable.ElementAt%2A> 方法来获取 <xref:System.Data.DataRow> 中的 <xref:System.Data.DataSet> 元素。</span><span class="sxs-lookup"><span data-stu-id="fb7ed-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="fb7ed-117">聚合运算符</span><span class="sxs-lookup"><span data-stu-id="fb7ed-117">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="fb7ed-118">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Sum%2A> 方法来查询 <xref:System.Data.DataSet> 并聚合数据。</span><span class="sxs-lookup"><span data-stu-id="fb7ed-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="fb7ed-119">联接运算符</span><span class="sxs-lookup"><span data-stu-id="fb7ed-119">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
 <span data-ttu-id="fb7ed-120">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 <xref:System.Linq.Enumerable.Join%2A> 方法来查询 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="fb7ed-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb7ed-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="fb7ed-121">See also</span></span>
- [<span data-ttu-id="fb7ed-122">基于方法的查询示例</span><span class="sxs-lookup"><span data-stu-id="fb7ed-122">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)
- [<span data-ttu-id="fb7ed-123">数据集特定的运算符示例</span><span class="sxs-lookup"><span data-stu-id="fb7ed-123">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)
- [<span data-ttu-id="fb7ed-124">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="fb7ed-124">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
