---
title: 使用 DataView 进行排序 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885b3b7b-51c1-42b3-bb29-b925f4f69a6f
ms.openlocfilehash: 2998de7dee34f9b5410bfe53988e0b7cfa797784
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634750"
---
# <a name="sorting-with-dataview-linq-to-dataset"></a><span data-ttu-id="a237b-102">使用 DataView 进行排序 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="a237b-102">Sorting with DataView (LINQ to DataSet)</span></span>
<span data-ttu-id="a237b-103">基于特定条件对数据进行排序，然后通过 UI 控件向客户端表示该数据的能力是数据绑定的一个重要特征。</span><span class="sxs-lookup"><span data-stu-id="a237b-103">The ability to sort data based on specific criteria and then present the data to a client through a UI control is an important aspect of data binding.</span></span> <span data-ttu-id="a237b-104"><xref:System.Data.DataView> 提供多种方式对数据进行排序并返回按指定排序条件排序的数据行。</span><span class="sxs-lookup"><span data-stu-id="a237b-104"><xref:System.Data.DataView> provides several ways to sort data and return data rows ordered by specific ordering criteria.</span></span> <span data-ttu-id="a237b-105">除了基于字符串的排序功能以外，<xref:System.Data.DataView> 还使您能够对排序条件使用语言集成查询（LINQ）表达式。</span><span class="sxs-lookup"><span data-stu-id="a237b-105">In addition to its string-based sorting capabilities, <xref:System.Data.DataView> also enables you to use Language-Integrated Query (LINQ) expressions for the sorting criteria.</span></span> <span data-ttu-id="a237b-106">LINQ 表达式允许执行比基于字符串的排序更复杂而功能更强大的排序操作。</span><span class="sxs-lookup"><span data-stu-id="a237b-106">LINQ expressions allow for much more complex and powerful sorting operations than string-based sorting.</span></span> <span data-ttu-id="a237b-107">本主题介绍这两种使用 <xref:System.Data.DataView> 的排序方法。</span><span class="sxs-lookup"><span data-stu-id="a237b-107">This topic describes both approaches to sorting using <xref:System.Data.DataView>.</span></span>  
  
## <a name="creating-dataview-from-a-query-with-sorting-information"></a><span data-ttu-id="a237b-108">通过具有排序信息的查询创建 DataView</span><span class="sxs-lookup"><span data-stu-id="a237b-108">Creating DataView from a Query with Sorting Information</span></span>  
 <span data-ttu-id="a237b-109">可以从 LINQ to DataSet 查询创建 <xref:System.Data.DataView> 对象。</span><span class="sxs-lookup"><span data-stu-id="a237b-109">A <xref:System.Data.DataView> object can be created from a LINQ to DataSet query.</span></span> <span data-ttu-id="a237b-110">如果查询包含 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.ThenBy%2A> 或 <xref:System.Linq.Enumerable.ThenByDescending%2A> 子句，则这些子句中的表达式将用作对 <xref:System.Data.DataView> 中的数据进行排序的基础。</span><span class="sxs-lookup"><span data-stu-id="a237b-110">If that query contains an <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.ThenBy%2A>, or <xref:System.Linq.Enumerable.ThenByDescending%2A> clause the expressions in these clauses are used as the basis for sorting the data in the <xref:System.Data.DataView>.</span></span> <span data-ttu-id="a237b-111">例如，如果查询包含 `Order By…` 和 `Then By…` 子句，则生成的 <xref:System.Data.DataView> 将按指定的两个列对数据进行排序。</span><span class="sxs-lookup"><span data-stu-id="a237b-111">For example, if the query contains the `Order By…`and `Then By…` clauses, the resulting <xref:System.Data.DataView> would order the data by both columns specified.</span></span>  
  
 <span data-ttu-id="a237b-112">基于表达式的排序具有比基于字符串的简单排序更强大、更复杂的排序功能。</span><span class="sxs-lookup"><span data-stu-id="a237b-112">Expression-based sorting offers more powerful and complex sorting than the simpler string-based sorting.</span></span> <span data-ttu-id="a237b-113">请注意，基于字符串和基于表达式的排序是互相排斥的。</span><span class="sxs-lookup"><span data-stu-id="a237b-113">Note that string-based and expression-based sorting are mutually exclusive.</span></span> <span data-ttu-id="a237b-114">如果在通过查询创建 <xref:System.Data.DataView.Sort%2A> 后设置基于字符串的 <xref:System.Data.DataView>，则会清除从查询推断的基于表达式的筛选，并且无法重置。</span><span class="sxs-lookup"><span data-stu-id="a237b-114">If the string-based <xref:System.Data.DataView.Sort%2A> is set after a <xref:System.Data.DataView> is created from a query, the expression-based filter inferred from the query is cleared and cannot be reset.</span></span>  
  
 <span data-ttu-id="a237b-115">创建 <xref:System.Data.DataView> 及修改任何排序或筛选信息时，均会生成 <xref:System.Data.DataView> 的索引。</span><span class="sxs-lookup"><span data-stu-id="a237b-115">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="a237b-116">通过在从其创建 <xref:System.Data.DataView> 的 LINQ to DataSet 查询中提供排序条件，并在以后不修改排序信息，可以获得最佳性能。</span><span class="sxs-lookup"><span data-stu-id="a237b-116">You get the best performance by supplying sorting criteria in the LINQ to DataSet query that the <xref:System.Data.DataView> is created from and not modifying the sorting information, later.</span></span> <span data-ttu-id="a237b-117">有关详细信息，请参阅[DataView 性能](dataview-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="a237b-117">For more information, see [DataView Performance](dataview-performance.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a237b-118">在大多数情况下，用于排序的表达式不应有副作用且必须是确定的。</span><span class="sxs-lookup"><span data-stu-id="a237b-118">In most cases, the expressions used for sorting should not have side effects and must be deterministic.</span></span> <span data-ttu-id="a237b-119">另外，表达式不应包含依赖于固定执行次数的任何逻辑，因为排序操作可能会执行任意次。</span><span class="sxs-lookup"><span data-stu-id="a237b-119">Also, the expressions should not contain any logic that depends on a set number of executions, because the sorting operations might be executed any number of times.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a237b-120">示例</span><span class="sxs-lookup"><span data-stu-id="a237b-120">Example</span></span>  
 <span data-ttu-id="a237b-121">下面的示例查询 SalesOrderHeader 表并按订单日期对返回的行排序，通过查询创建 <xref:System.Data.DataView>，并将 <xref:System.Data.DataView> 绑定到 <xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="a237b-121">The following example queries the SalesOrderHeader table and orders the returned rows by the order date; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby)]  
  
### <a name="example"></a><span data-ttu-id="a237b-122">示例</span><span class="sxs-lookup"><span data-stu-id="a237b-122">Example</span></span>  
 <span data-ttu-id="a237b-123">下面的示例查询 SalesOrderHeader 表并按总应付金额对返回的行排序，通过查询创建 <xref:System.Data.DataView>，并将 <xref:System.Data.DataView> 绑定到 <xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="a237b-123">The following example queries the SalesOrderHeader table and orders the returned row by total amount due; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderby2)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderBy2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderby2)]  
  
### <a name="example"></a><span data-ttu-id="a237b-124">示例</span><span class="sxs-lookup"><span data-stu-id="a237b-124">Example</span></span>  
 <span data-ttu-id="a237b-125">下面的示例查询 SalesOrderDetail 表并先按订单数量，然后按销售订单 ID 对返回的行排序，通过查询创建 <xref:System.Data.DataView>，并将 <xref:System.Data.DataView> 绑定到 <xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="a237b-125">The following example queries the SalesOrderDetail table and orders the returned rows by order quantity and then by sales order ID; creates a <xref:System.Data.DataView> from that query; and binds the <xref:System.Data.DataView> to a <xref:System.Windows.Forms.BindingSource>.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromqueryorderbythenby)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryOrderByThenBy](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromqueryorderbythenby)]  
  
## <a name="using-the-string-based-sort-property"></a><span data-ttu-id="a237b-126">使用基于字符串的排序属性</span><span class="sxs-lookup"><span data-stu-id="a237b-126">Using the String-Based Sort Property</span></span>  
 <span data-ttu-id="a237b-127"><xref:System.Data.DataView> 的基于字符串的排序功能仍适用于 LINQ to DataSet。</span><span class="sxs-lookup"><span data-stu-id="a237b-127">The string-based sorting functionality of <xref:System.Data.DataView> still works with LINQ to DataSet.</span></span> <span data-ttu-id="a237b-128">从 LINQ to DataSet 查询创建 <xref:System.Data.DataView> 后，可以使用 <xref:System.Data.DataView.Sort%2A> 属性来设置对 <xref:System.Data.DataView>的排序。</span><span class="sxs-lookup"><span data-stu-id="a237b-128">After a <xref:System.Data.DataView> has been created from a LINQ to DataSet query, you can use the <xref:System.Data.DataView.Sort%2A> property to set the sorting on the <xref:System.Data.DataView>.</span></span>  
  
 <span data-ttu-id="a237b-129">基于字符串和基于表达式的排序功能是互相排斥的。</span><span class="sxs-lookup"><span data-stu-id="a237b-129">The string-based and expression-based sorting functionality are mutually exclusive.</span></span> <span data-ttu-id="a237b-130">设置 <xref:System.Data.DataView.Sort%2A> 属性将清除从创建 <xref:System.Data.DataView> 的查询中继承的基于表达式的排序。</span><span class="sxs-lookup"><span data-stu-id="a237b-130">Setting the <xref:System.Data.DataView.Sort%2A> property will clear the expression-based sort inherited from the query that the <xref:System.Data.DataView> was created from.</span></span>  
  
 <span data-ttu-id="a237b-131">有关基于字符串的 <xref:System.Data.DataView.Sort%2A> 筛选的详细信息，请参阅对[数据进行排序和筛选](./dataset-datatable-dataview/sorting-and-filtering-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a237b-131">For more information about string-based <xref:System.Data.DataView.Sort%2A> filtering, see [Sorting and Filtering Data](./dataset-datatable-dataview/sorting-and-filtering-data.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="a237b-132">示例</span><span class="sxs-lookup"><span data-stu-id="a237b-132">Example</span></span>  
 <span data-ttu-id="a237b-133">下面的示例从 Contact 表创建 <xref:System.Data.DataView> 并先按姓氏以降序，然后按名字以升序对行进行排序：</span><span class="sxs-lookup"><span data-stu-id="a237b-133">The follow example creates a <xref:System.Data.DataView> from the Contact table and sorts the rows by last name in descending order, then first name in ascending order:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvstringsort)]
 [!code-vb[DP DataView Samples#LDVStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvstringsort)]  
  
### <a name="example"></a><span data-ttu-id="a237b-134">示例</span><span class="sxs-lookup"><span data-stu-id="a237b-134">Example</span></span>  
 <span data-ttu-id="a237b-135">下面的示例查询 Contact 表中以字母“S”开头的姓氏。</span><span class="sxs-lookup"><span data-stu-id="a237b-135">The following example queries the Contact table for last names that start with the letter "S".</span></span>  <span data-ttu-id="a237b-136">通过该查询创建 <xref:System.Data.DataView> 并将其绑定到 <xref:System.Windows.Forms.BindingSource> 对象。</span><span class="sxs-lookup"><span data-stu-id="a237b-136">A <xref:System.Data.DataView> is created from that query and bound to a <xref:System.Windows.Forms.BindingSource> object.</span></span>  
  
 [!code-csharp[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#createldvfromquerystringsort)]
 [!code-vb[DP DataView Samples#CreateLDVFromQueryStringSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#createldvfromquerystringsort)]  
  
## <a name="clearing-the-sort"></a><span data-ttu-id="a237b-137">清除排序</span><span class="sxs-lookup"><span data-stu-id="a237b-137">Clearing the Sort</span></span>  
 <span data-ttu-id="a237b-138">有关 <xref:System.Data.DataView> 的排序信息可以在使用 <xref:System.Data.DataView.Sort%2A> 属性设置后清除。</span><span class="sxs-lookup"><span data-stu-id="a237b-138">The sorting information on a <xref:System.Data.DataView> can be cleared after it has been set using the <xref:System.Data.DataView.Sort%2A> property.</span></span> <span data-ttu-id="a237b-139">清除 <xref:System.Data.DataView> 中的排序信息有两种方式：</span><span class="sxs-lookup"><span data-stu-id="a237b-139">There are two ways to clear the sorting information in <xref:System.Data.DataView>:</span></span>  
  
- <span data-ttu-id="a237b-140">将 <xref:System.Data.DataView.Sort%2A> 属性设置为 `null`。</span><span class="sxs-lookup"><span data-stu-id="a237b-140">Set the <xref:System.Data.DataView.Sort%2A> property to `null`.</span></span>  
  
- <span data-ttu-id="a237b-141">将 <xref:System.Data.DataView.Sort%2A> 属性设置为一个空字符串。</span><span class="sxs-lookup"><span data-stu-id="a237b-141">Set the <xref:System.Data.DataView.Sort%2A> property to an empty string.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a237b-142">示例</span><span class="sxs-lookup"><span data-stu-id="a237b-142">Example</span></span>  
 <span data-ttu-id="a237b-143">下面的示例通过查询创建一个 <xref:System.Data.DataView> 并通过将 <xref:System.Data.DataView.Sort%2A> 属性设置为空字符串清除排序。</span><span class="sxs-lookup"><span data-stu-id="a237b-143">The following example creates a <xref:System.Data.DataView> from a query and clears the sorting by setting the <xref:System.Data.DataView.Sort%2A> property to an empty string:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort)]
 [!code-vb[DP DataView Samples#LDVClearSort](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort)]  
  
### <a name="example"></a><span data-ttu-id="a237b-144">示例</span><span class="sxs-lookup"><span data-stu-id="a237b-144">Example</span></span>  
 <span data-ttu-id="a237b-145">下面的示例从 Contact 表创建 <xref:System.Data.DataView> 并将 <xref:System.Data.DataView.Sort%2A> 属性设置为按姓氏以降序排序。</span><span class="sxs-lookup"><span data-stu-id="a237b-145">The following example creates a <xref:System.Data.DataView> from the Contact table and sets the <xref:System.Data.DataView.Sort%2A> property to sort by last name in descending order.</span></span> <span data-ttu-id="a237b-146">然后通过将 <xref:System.Data.DataView.Sort%2A> 属性设置为 `null` 来清除排序信息：</span><span class="sxs-lookup"><span data-stu-id="a237b-146">The sorting information is then cleared by setting the <xref:System.Data.DataView.Sort%2A> property to `null`:</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvclearsort2)]
 [!code-vb[DP DataView Samples#LDVClearSort2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvclearsort2)]  
  
## <a name="see-also"></a><span data-ttu-id="a237b-147">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a237b-147">See also</span></span>

- [<span data-ttu-id="a237b-148">数据绑定和 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="a237b-148">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
- [<span data-ttu-id="a237b-149">使用 DataView 进行筛选</span><span class="sxs-lookup"><span data-stu-id="a237b-149">Filtering with DataView</span></span>](filtering-with-dataview-linq-to-dataset.md)
- <span data-ttu-id="a237b-150">[对数据进行排序](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="a237b-150">[Sorting Data](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb546145(v=vs.120))</span></span>
