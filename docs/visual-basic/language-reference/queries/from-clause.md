---
title: From 子句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryFrom
- vb.QueryFromIn
- vb.QueryFromLet
helpviewer_keywords:
- queries [Visual Basic], From
- From clause [Visual Basic]
- From statement [Visual Basic]
ms.assetid: 83e3665e-68a0-4540-a3a3-3d777a0f95d5
ms.openlocfilehash: b18ef2f291e20d8a150972a980ba063377b0bc3a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839608"
---
# <a name="from-clause-visual-basic"></a><span data-ttu-id="e97dc-102">From 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e97dc-102">From Clause (Visual Basic)</span></span>
<span data-ttu-id="e97dc-103">指定一个或多个范围变量和查询的集合。</span><span class="sxs-lookup"><span data-stu-id="e97dc-103">Specifies one or more range variables and a collection to query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e97dc-104">语法</span><span class="sxs-lookup"><span data-stu-id="e97dc-104">Syntax</span></span>  
  
```  
From element [ As type ] In collection [ _ ]  
  [, element2 [ As type2 ] In collection2 [, ... ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="e97dc-105">部件</span><span class="sxs-lookup"><span data-stu-id="e97dc-105">Parts</span></span>  
  
|<span data-ttu-id="e97dc-106">术语</span><span class="sxs-lookup"><span data-stu-id="e97dc-106">Term</span></span>|<span data-ttu-id="e97dc-107">定义</span><span class="sxs-lookup"><span data-stu-id="e97dc-107">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="e97dc-108">必需。</span><span class="sxs-lookup"><span data-stu-id="e97dc-108">Required.</span></span> <span data-ttu-id="e97dc-109">一个*范围变量*用于循环访问集合的元素。</span><span class="sxs-lookup"><span data-stu-id="e97dc-109">A *range variable* used to iterate through the elements of the collection.</span></span> <span data-ttu-id="e97dc-110">范围变量用于引用的每个成员`collection`根据循环访问查询`collection`。</span><span class="sxs-lookup"><span data-stu-id="e97dc-110">A range variable is used to refer to each member of the `collection` as the query iterates through the `collection`.</span></span> <span data-ttu-id="e97dc-111">必须是可枚举类型。</span><span class="sxs-lookup"><span data-stu-id="e97dc-111">Must be an enumerable type.</span></span>|  
|`type`|<span data-ttu-id="e97dc-112">可选。</span><span class="sxs-lookup"><span data-stu-id="e97dc-112">Optional.</span></span> <span data-ttu-id="e97dc-113">`element` 的类型。</span><span class="sxs-lookup"><span data-stu-id="e97dc-113">The type of `element`.</span></span> <span data-ttu-id="e97dc-114">如果没有`type`指定的类型`element`从推断`collection`。</span><span class="sxs-lookup"><span data-stu-id="e97dc-114">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="e97dc-115">必需。</span><span class="sxs-lookup"><span data-stu-id="e97dc-115">Required.</span></span> <span data-ttu-id="e97dc-116">表示要查询的集合。</span><span class="sxs-lookup"><span data-stu-id="e97dc-116">Refers to the collection to be queried.</span></span> <span data-ttu-id="e97dc-117">必须是可枚举类型。</span><span class="sxs-lookup"><span data-stu-id="e97dc-117">Must be an enumerable type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e97dc-118">备注</span><span class="sxs-lookup"><span data-stu-id="e97dc-118">Remarks</span></span>  
 <span data-ttu-id="e97dc-119">`From`子句用于标识源数据中的查询以及用于在源集合中引用的元素的变量。</span><span class="sxs-lookup"><span data-stu-id="e97dc-119">The `From` clause is used to identify the source data for a query and the variables that are used to refer to an element from the source collection.</span></span> <span data-ttu-id="e97dc-120">这些变量称为*范围变量*。</span><span class="sxs-lookup"><span data-stu-id="e97dc-120">These variables are called *range variables*.</span></span> <span data-ttu-id="e97dc-121">`From`子句是必需的查询，除非当`Aggregate`子句用于确定某个查询仅返回聚合结果。</span><span class="sxs-lookup"><span data-stu-id="e97dc-121">The `From` clause is required for a query, except when the `Aggregate` clause is used to identify a query that returns only aggregated results.</span></span> <span data-ttu-id="e97dc-122">有关详细信息，请参阅[Aggregate 子句](../../../visual-basic/language-reference/queries/aggregate-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="e97dc-122">For more information, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="e97dc-123">可以指定多个`From`查询来标识要联接的多个集合中的子句。</span><span class="sxs-lookup"><span data-stu-id="e97dc-123">You can specify multiple `From` clauses in a query to identify multiple collections to be joined.</span></span> <span data-ttu-id="e97dc-124">如果指定多个集合，独立，循环，或如果它们彼此联接它们。</span><span class="sxs-lookup"><span data-stu-id="e97dc-124">When multiple collections are specified, they are iterated over independently, or you can join them if they are related.</span></span> <span data-ttu-id="e97dc-125">您可以通过使用隐式联接集合`Select`子句，或通过使用显式`Join`或`Group Join`子句。</span><span class="sxs-lookup"><span data-stu-id="e97dc-125">You can join collections implicitly by using the `Select` clause, or explicitly by using the `Join` or `Group Join` clauses.</span></span> <span data-ttu-id="e97dc-126">作为替代方法，您可以指定多个范围变量和集合中单个`From`子句中，每个相关的范围变量和由逗号分隔开的集合。</span><span class="sxs-lookup"><span data-stu-id="e97dc-126">As an alternative, you can specify multiple range variables and collections in a single `From` clause, with each related range variable and collection separated from the others by a comma.</span></span> <span data-ttu-id="e97dc-127">下面的代码示例显示了有关这两个语法选项`From`子句。</span><span class="sxs-lookup"><span data-stu-id="e97dc-127">The following code example shows both syntax options for the `From` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#21)]  
  
 <span data-ttu-id="e97dc-128">`From`子句定义的查询，这是类似的作用域范围`For`循环。</span><span class="sxs-lookup"><span data-stu-id="e97dc-128">The `From` clause defines the scope of a query, which is similar to the scope of a `For` loop.</span></span> <span data-ttu-id="e97dc-129">因此，每个`element`查询的作用域中的范围变量必须具有唯一的名称。</span><span class="sxs-lookup"><span data-stu-id="e97dc-129">Therefore, each `element` range variable in the scope of a query must have a unique name.</span></span> <span data-ttu-id="e97dc-130">因为你可以指定多个`From`子句的查询，后续`From`子句可以引用中的范围变量`From`子句，或它们在早期的范围变量可以引用`From`子句。</span><span class="sxs-lookup"><span data-stu-id="e97dc-130">Because you can specify multiple `From` clauses for a query, subsequent `From` clauses can refer to range variables in the `From` clause, or they can refer to range variables in a previous `From` clause.</span></span> <span data-ttu-id="e97dc-131">例如，下面的示例演示嵌套`From`子句中的第二个子句的集合基于第一个子句中的范围变量的属性。</span><span class="sxs-lookup"><span data-stu-id="e97dc-131">For example, the following example shows a nested `From` clause where the collection in the second clause is based on a property of the range variable in the first clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#22)]  
  
 <span data-ttu-id="e97dc-132">每个`From`子句可以后跟其他查询子句以优化查询的任意组合。</span><span class="sxs-lookup"><span data-stu-id="e97dc-132">Each `From` clause can be followed by any combination of additional query clauses to refine the query.</span></span> <span data-ttu-id="e97dc-133">可以按以下方式来优化查询：</span><span class="sxs-lookup"><span data-stu-id="e97dc-133">You can refine the query in the following ways:</span></span>  
  
-   <span data-ttu-id="e97dc-134">通过使用隐式组合多个集合`From`并`Select`子句，或通过使用显式`Join`或`Group Join`子句。</span><span class="sxs-lookup"><span data-stu-id="e97dc-134">Combine multiple collections implicitly by using the `From` and `Select` clauses, or explicitly by using the `Join` or `Group Join` clauses.</span></span>  
  
-   <span data-ttu-id="e97dc-135">使用`Where`子句来筛选查询结果。</span><span class="sxs-lookup"><span data-stu-id="e97dc-135">Use the `Where` clause to filter the query result.</span></span>  
  
-   <span data-ttu-id="e97dc-136">对结果进行排序通过使用`Order By`子句。</span><span class="sxs-lookup"><span data-stu-id="e97dc-136">Sort the result by using the `Order By` clause.</span></span>  
  
-   <span data-ttu-id="e97dc-137">通过将类似的结果组合在一起`Group By`子句。</span><span class="sxs-lookup"><span data-stu-id="e97dc-137">Group similar results together by using the `Group By` clause.</span></span>  
  
-   <span data-ttu-id="e97dc-138">使用`Aggregate`子句，以标识要针对整个查询结果计算的聚合函数。</span><span class="sxs-lookup"><span data-stu-id="e97dc-138">Use the `Aggregate` clause to identify aggregate functions to evaluate for the whole query result.</span></span>  
  
-   <span data-ttu-id="e97dc-139">使用`Let`子句引入迭代变量的值由而不是集合的表达式。</span><span class="sxs-lookup"><span data-stu-id="e97dc-139">Use the `Let` clause to introduce an iteration variable whose value is determined by an expression instead of a collection.</span></span>  
  
-   <span data-ttu-id="e97dc-140">使用`Distinct`子句忽略重复的查询结果。</span><span class="sxs-lookup"><span data-stu-id="e97dc-140">Use the `Distinct` clause to ignore duplicate query results.</span></span>  
  
-   <span data-ttu-id="e97dc-141">标识要通过使用返回的结果的部分`Skip`， `Take`， `Skip While`，和`Take While`子句。</span><span class="sxs-lookup"><span data-stu-id="e97dc-141">Identify parts of the result to return by using the `Skip`, `Take`, `Skip While`, and `Take While` clauses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e97dc-142">示例</span><span class="sxs-lookup"><span data-stu-id="e97dc-142">Example</span></span>  
 <span data-ttu-id="e97dc-143">下面的查询中使用表达式`From`子句来声明范围变量`cust`每个`Customer`对象中`customers`集合。</span><span class="sxs-lookup"><span data-stu-id="e97dc-143">The following query expression uses a `From` clause to declare a range variable `cust` for each `Customer` object in the `customers` collection.</span></span> <span data-ttu-id="e97dc-144">`Where`子句使用的范围变量将输出限制为客户，从指定的区域。</span><span class="sxs-lookup"><span data-stu-id="e97dc-144">The `Where` clause uses the range variable to restrict the output to customers from the specified region.</span></span> <span data-ttu-id="e97dc-145">`For Each`循环显示查询结果中的每个客户的公司名称。</span><span class="sxs-lookup"><span data-stu-id="e97dc-145">The `For Each` loop displays the company name for each customer in the query result.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="e97dc-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="e97dc-146">See also</span></span>

- [<span data-ttu-id="e97dc-147">查询</span><span class="sxs-lookup"><span data-stu-id="e97dc-147">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="e97dc-148">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="e97dc-148">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="e97dc-149">For Each...Next 语句</span><span class="sxs-lookup"><span data-stu-id="e97dc-149">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="e97dc-150">For...Next 语句</span><span class="sxs-lookup"><span data-stu-id="e97dc-150">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="e97dc-151">Select 子句</span><span class="sxs-lookup"><span data-stu-id="e97dc-151">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="e97dc-152">Where 子句</span><span class="sxs-lookup"><span data-stu-id="e97dc-152">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="e97dc-153">Aggregate 子句</span><span class="sxs-lookup"><span data-stu-id="e97dc-153">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="e97dc-154">Distinct 子句</span><span class="sxs-lookup"><span data-stu-id="e97dc-154">Distinct Clause</span></span>](../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="e97dc-155">Join 子句</span><span class="sxs-lookup"><span data-stu-id="e97dc-155">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="e97dc-156">Group Join 子句</span><span class="sxs-lookup"><span data-stu-id="e97dc-156">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="e97dc-157">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="e97dc-157">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="e97dc-158">Let 子句</span><span class="sxs-lookup"><span data-stu-id="e97dc-158">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="e97dc-159">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="e97dc-159">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="e97dc-160">Take 子句</span><span class="sxs-lookup"><span data-stu-id="e97dc-160">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="e97dc-161">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="e97dc-161">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="e97dc-162">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="e97dc-162">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
