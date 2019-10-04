---
title: 标准查询运算符转换
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a60c30fa-1e68-45fe-b984-f6abb9ede40e
ms.openlocfilehash: af22b6a895fef8037eb5c069ffb7cb23d1333531
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833682"
---
# <a name="standard-query-operator-translation"></a><span data-ttu-id="a679a-102">标准查询运算符转换</span><span class="sxs-lookup"><span data-stu-id="a679a-102">Standard Query Operator Translation</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a679a-103">将标准查询运算符转换为 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="a679a-103">translates Standard Query Operators to SQL commands.</span></span> <span data-ttu-id="a679a-104">数据库的查询处理器决定了 SQL 转换的执行语义。</span><span class="sxs-lookup"><span data-stu-id="a679a-104">The query processor of the database determines the execution semantics of SQL translation.</span></span>

<span data-ttu-id="a679a-105">标准查询运算符是针对*序列*定义的。</span><span class="sxs-lookup"><span data-stu-id="a679a-105">Standard Query Operators are defined against *sequences*.</span></span> <span data-ttu-id="a679a-106">序列按顺序*排序*，并依赖于序列的每个元素的引用标识。</span><span class="sxs-lookup"><span data-stu-id="a679a-106">A sequence is *ordered* and relies on reference identity for each element of the sequence.</span></span> <span data-ttu-id="a679a-107">有关详细信息，请参阅[标准查询运算符概述C#（）](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)或[标准查询运算符概述（Visual Basic）](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a679a-107">For more information, see [Standard Query Operators Overview (C#)](../../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

<span data-ttu-id="a679a-108">SQL 主要处理*值的无序集*。</span><span class="sxs-lookup"><span data-stu-id="a679a-108">SQL deals primarily with *unordered sets of values*.</span></span> <span data-ttu-id="a679a-109">排序通常是显式声明的后续处理操作，应用于查询的最终结果而不是中间结果。</span><span class="sxs-lookup"><span data-stu-id="a679a-109">Ordering is typically an explicitly stated, post-processing operation that is applied to the final result of a query rather than to intermediate results.</span></span> <span data-ttu-id="a679a-110">标识由值定义。</span><span class="sxs-lookup"><span data-stu-id="a679a-110">Identity is defined by values.</span></span> <span data-ttu-id="a679a-111">出于此原因，可以理解 SQL 查询来处理多重集（*包*），而不是*设置*。</span><span class="sxs-lookup"><span data-stu-id="a679a-111">For this reason, SQL queries are understood to deal with multisets (*bags*) instead of *sets*.</span></span>

<span data-ttu-id="a679a-112">以下各段介绍了标准查询运算符与其针对用于 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 SQL Server 提供程序的 SQL 转换结果之间的差异。</span><span class="sxs-lookup"><span data-stu-id="a679a-112">The following paragraphs describe the differences between the Standard Query Operators and their SQL translation for the SQL Server provider for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

## <a name="operator-support"></a><span data-ttu-id="a679a-113">运算符支持</span><span class="sxs-lookup"><span data-stu-id="a679a-113">Operator Support</span></span>

### <a name="concat"></a><span data-ttu-id="a679a-114">Concat</span><span class="sxs-lookup"><span data-stu-id="a679a-114">Concat</span></span>

<span data-ttu-id="a679a-115"><xref:System.Linq.Enumerable.Concat%2A> 方法是为有序多重集定义的，其中接收方的顺序与自变量的顺序相同。</span><span class="sxs-lookup"><span data-stu-id="a679a-115">The <xref:System.Linq.Enumerable.Concat%2A> method is defined for ordered multisets where the order of the receiver and the order of the argument are the same.</span></span> <span data-ttu-id="a679a-116"><xref:System.Linq.Enumerable.Concat%2A> 的作用等效于对多重集执行 `UNION ALL`，紧接着再执行常见排序。</span><span class="sxs-lookup"><span data-stu-id="a679a-116"><xref:System.Linq.Enumerable.Concat%2A> works as `UNION ALL` over the multisets followed by the common order.</span></span>

<span data-ttu-id="a679a-117">在产生结果前，最后一步是在 SQL 中排序。</span><span class="sxs-lookup"><span data-stu-id="a679a-117">The final step is ordering in SQL before results are produced.</span></span> <span data-ttu-id="a679a-118"><xref:System.Linq.Enumerable.Concat%2A> 不保留其自变量的顺序。</span><span class="sxs-lookup"><span data-stu-id="a679a-118"><xref:System.Linq.Enumerable.Concat%2A> does not preserve the order of its arguments.</span></span> <span data-ttu-id="a679a-119">为确保顺序合适，您必须显式对 <xref:System.Linq.Enumerable.Concat%2A> 的结果进行排序。</span><span class="sxs-lookup"><span data-stu-id="a679a-119">To ensure appropriate ordering, you must explicitly order the results of <xref:System.Linq.Enumerable.Concat%2A>.</span></span>

### <a name="intersect-except-union"></a><span data-ttu-id="a679a-120">Intersect、Except、Union</span><span class="sxs-lookup"><span data-stu-id="a679a-120">Intersect, Except, Union</span></span>

<span data-ttu-id="a679a-121"><xref:System.Linq.Enumerable.Intersect%2A> 和 <xref:System.Linq.Enumerable.Except%2A> 方法仅对集合而言是定义完善的。</span><span class="sxs-lookup"><span data-stu-id="a679a-121">The <xref:System.Linq.Enumerable.Intersect%2A> and <xref:System.Linq.Enumerable.Except%2A> methods are well defined only on sets.</span></span> <span data-ttu-id="a679a-122">针对多重集的语义尚未定义。</span><span class="sxs-lookup"><span data-stu-id="a679a-122">The semantics for multisets is undefined.</span></span>

<span data-ttu-id="a679a-123"><xref:System.Linq.Enumerable.Union%2A> 方法是为多重集定义的，定义为多重集的无序串联（实际上是 SQL 中的 UNION ALL 子句的执行结果）。</span><span class="sxs-lookup"><span data-stu-id="a679a-123">The <xref:System.Linq.Enumerable.Union%2A> method is defined for multisets as the unordered concatenation of the multisets (effectively the result of the UNION ALL clause in SQL).</span></span>

### <a name="take-skip"></a><span data-ttu-id="a679a-124">Take、Skip</span><span class="sxs-lookup"><span data-stu-id="a679a-124">Take, Skip</span></span>

<span data-ttu-id="a679a-125"><xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 方法仅对*有序集*定义良好。</span><span class="sxs-lookup"><span data-stu-id="a679a-125"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> methods are well defined only against *ordered sets*.</span></span> <span data-ttu-id="a679a-126">未定义针对无序集或多重集的语义。</span><span class="sxs-lookup"><span data-stu-id="a679a-126">The semantics for unordered sets or multisets are undefined.</span></span>

> [!NOTE]
> <span data-ttu-id="a679a-127"><xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 用在针对 SQL Server 2000 的查询中时存在一定的限制。</span><span class="sxs-lookup"><span data-stu-id="a679a-127"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="a679a-128">有关详细信息，请参阅[疑难解答](troubleshooting.md)中的 "跳过并使用 SQL Server 2000" 条目。</span><span class="sxs-lookup"><span data-stu-id="a679a-128">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

<span data-ttu-id="a679a-129">由于 SQL 中的排序存在限制，因此 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会设法将这些方法的参数的排序操作移到相应方法的结果中进行。</span><span class="sxs-lookup"><span data-stu-id="a679a-129">Because of limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of these methods to the result of the method.</span></span> <span data-ttu-id="a679a-130">例如，请考虑下面这个 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查询：</span><span class="sxs-lookup"><span data-stu-id="a679a-130">For example, consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query:</span></span>

[!code-csharp[DLinqSQOTranslation#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#1)]
[!code-vb[DLinqSQOTranslation#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#1)]

<span data-ttu-id="a679a-131">为此代码生成的 SQL 会将排序移到结尾，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a679a-131">The generated SQL for this code moves the ordering to the end, as follows:</span></span>

```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],
FROM [Customers] AS [t0]
WHERE (NOT (EXISTS(
    SELECT NULL AS [EMPTY]
    FROM (
        SELECT TOP 1 [t1].[CustomerID]
        FROM [Customers] AS [t1]
        WHERE [t1].[City] = @p0
        ORDER BY [t1].[CustomerID]
        ) AS [t2]
    WHERE [t0].[CustomerID] = [t2].[CustomerID]
    ))) AND ([t0].[City] = @p1)
ORDER BY [t0].[CustomerID]
```

<span data-ttu-id="a679a-132">显而易见，当 <xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 链接在一起时，所有指定的排序必须一致。</span><span class="sxs-lookup"><span data-stu-id="a679a-132">It becomes obvious that all the specified ordering must be consistent when <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are chained together.</span></span> <span data-ttu-id="a679a-133">否则，结果将是不确定的。</span><span class="sxs-lookup"><span data-stu-id="a679a-133">Otherwise, the results are undefined.</span></span>

<span data-ttu-id="a679a-134">对于非负的、基于标准查询运算符规范的整型常量参数，<xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 都是定义完善的。</span><span class="sxs-lookup"><span data-stu-id="a679a-134">Both <xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> are well-defined for non-negative, constant integral arguments based on the Standard Query Operator specification.</span></span>

### <a name="operators-with-no-translation"></a><span data-ttu-id="a679a-135">不进行转换的运算符</span><span class="sxs-lookup"><span data-stu-id="a679a-135">Operators with No Translation</span></span>

<span data-ttu-id="a679a-136">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 不对以下方法进行转换。</span><span class="sxs-lookup"><span data-stu-id="a679a-136">The following methods are not translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="a679a-137">最常见的原因是无序多重集与序列之间存在差异。</span><span class="sxs-lookup"><span data-stu-id="a679a-137">The most common reason is the difference between unordered multisets and sequences.</span></span>

|<span data-ttu-id="a679a-138">运算符</span><span class="sxs-lookup"><span data-stu-id="a679a-138">Operators</span></span>|<span data-ttu-id="a679a-139">阐释</span><span class="sxs-lookup"><span data-stu-id="a679a-139">Rationale</span></span>|
|---------------|---------------|
|<span data-ttu-id="a679a-140"><xref:System.Linq.Enumerable.TakeWhile%2A>， <xref:System.Linq.Enumerable.SkipWhile%2A></span><span class="sxs-lookup"><span data-stu-id="a679a-140"><xref:System.Linq.Enumerable.TakeWhile%2A>, <xref:System.Linq.Enumerable.SkipWhile%2A></span></span>|<span data-ttu-id="a679a-141">SQL 查询是对多重集执行的，而不是对序列执行的。</span><span class="sxs-lookup"><span data-stu-id="a679a-141">SQL queries operate on multisets, not on sequences.</span></span> <span data-ttu-id="a679a-142">`ORDER BY` 必须是最后一个应用于结果的子句。</span><span class="sxs-lookup"><span data-stu-id="a679a-142">`ORDER BY` must be the last clause applied to the results.</span></span> <span data-ttu-id="a679a-143">因此，不存在适用于这两个方法的通用转换。</span><span class="sxs-lookup"><span data-stu-id="a679a-143">For this reason, there is no general-purpose translation for these two methods.</span></span>|
|<xref:System.Linq.Enumerable.Reverse%2A>|<span data-ttu-id="a679a-144">此方法的转换对于有序集而言是可行的，但目前 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 未对它进行转换。</span><span class="sxs-lookup"><span data-stu-id="a679a-144">Translation of this method is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="a679a-145"><xref:System.Linq.Enumerable.Last%2A>， <xref:System.Linq.Enumerable.LastOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="a679a-145"><xref:System.Linq.Enumerable.Last%2A>, <xref:System.Linq.Enumerable.LastOrDefault%2A></span></span>|<span data-ttu-id="a679a-146">这些方法的转换对于有序集而言是可行的，但目前 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 未对它们进行转换。</span><span class="sxs-lookup"><span data-stu-id="a679a-146">Translation of these methods is possible for an ordered set but is not currently translated by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>|
|<span data-ttu-id="a679a-147"><xref:System.Linq.Enumerable.ElementAt%2A>， <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span><span class="sxs-lookup"><span data-stu-id="a679a-147"><xref:System.Linq.Enumerable.ElementAt%2A>, <xref:System.Linq.Enumerable.ElementAtOrDefault%2A></span></span>|<span data-ttu-id="a679a-148">SQL 查询是对多重集执行的，而不是对可建立索引的序列执行的。</span><span class="sxs-lookup"><span data-stu-id="a679a-148">SQL queries operate on multisets, not on indexable sequences.</span></span>|
|<span data-ttu-id="a679a-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A>（带默认参数的重载）</span><span class="sxs-lookup"><span data-stu-id="a679a-149"><xref:System.Linq.Enumerable.DefaultIfEmpty%2A> (overload with default arg)</span></span>|<span data-ttu-id="a679a-150">一般而言，无法为任意元组指定默认值。</span><span class="sxs-lookup"><span data-stu-id="a679a-150">In general, a default value cannot be specified for an arbitrary tuple.</span></span> <span data-ttu-id="a679a-151">在某些情况下，可以通过外部联接为元组指定 Null 值。</span><span class="sxs-lookup"><span data-stu-id="a679a-151">Null values for tuples are possible in some cases through outer joins.</span></span>|

## <a name="expression-translation"></a><span data-ttu-id="a679a-152">表达式转换</span><span class="sxs-lookup"><span data-stu-id="a679a-152">Expression Translation</span></span>

### <a name="null-semantics"></a><span data-ttu-id="a679a-153">Null 语义</span><span class="sxs-lookup"><span data-stu-id="a679a-153">Null semantics</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a679a-154">不会将 null 比较语义施加在 SQL 上。</span><span class="sxs-lookup"><span data-stu-id="a679a-154">does not impose null comparison semantics on SQL.</span></span> <span data-ttu-id="a679a-155">比较运算符在语法上被转换为其 SQL 等效项。</span><span class="sxs-lookup"><span data-stu-id="a679a-155">Comparison operators are syntactically translated to their SQL equivalents.</span></span> <span data-ttu-id="a679a-156">因此，该语义反映了由服务器或连接设置定义的 SQL 语义。</span><span class="sxs-lookup"><span data-stu-id="a679a-156">For this reason, the semantics reflect SQL semantics that are defined by server or connection settings.</span></span> <span data-ttu-id="a679a-157">例如，在默认 SQL Server 设置下，两个 null 值被视为不相等，但您可以更改这些设置以更改语义。</span><span class="sxs-lookup"><span data-stu-id="a679a-157">For example, two null values are considered unequal under default SQL Server settings, but you can change the settings to change the semantics.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a679a-158">在转换查询时不考虑服务器设置。</span><span class="sxs-lookup"><span data-stu-id="a679a-158">does not consider server settings when it translates queries.</span></span>

<span data-ttu-id="a679a-159">对文本型 null 的比较被转换为相应的 SQL 版本（`is null` 或 `is not null`）。</span><span class="sxs-lookup"><span data-stu-id="a679a-159">A comparison with the literal null is translated to the appropriate SQL version (`is null` or `is not null`).</span></span>

<span data-ttu-id="a679a-160">排序规则中的 `null` 值是由 SQL Server 定义的。</span><span class="sxs-lookup"><span data-stu-id="a679a-160">The value of `null` in collation is defined by SQL Server.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a679a-161">不会更改排序规则。</span><span class="sxs-lookup"><span data-stu-id="a679a-161">does not change the collation.</span></span>

### <a name="aggregates"></a><span data-ttu-id="a679a-162">聚合</span><span class="sxs-lookup"><span data-stu-id="a679a-162">Aggregates</span></span>

<span data-ttu-id="a679a-163">使用标准查询运算符的聚合方法 <xref:System.Linq.Enumerable.Sum%2A> 计算空序列或只包含 null 的序列时，所得结果为零。</span><span class="sxs-lookup"><span data-stu-id="a679a-163">The Standard Query Operator aggregate method <xref:System.Linq.Enumerable.Sum%2A> evaluates to zero for an empty sequence or for a sequence that contains only nulls.</span></span> <span data-ttu-id="a679a-164">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，SQL 的语义保持不变，并且使用 <xref:System.Linq.Enumerable.Sum%2A> 计算空序列或只包含 null 的序列时，所得结果为 `null` 而非零。</span><span class="sxs-lookup"><span data-stu-id="a679a-164">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the semantics of SQL are left unchanged, and <xref:System.Linq.Enumerable.Sum%2A> evaluates to `null` instead of zero for an empty sequence or for a sequence that contains only nulls.</span></span>

<span data-ttu-id="a679a-165">针对中间结果的 SQL 限制适用于 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的聚合。</span><span class="sxs-lookup"><span data-stu-id="a679a-165">SQL limitations on intermediate results apply to aggregates in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="a679a-166">32 位整型量的 <xref:System.Linq.Enumerable.Sum%2A> 不是使用 64 位结果计算的。</span><span class="sxs-lookup"><span data-stu-id="a679a-166">The <xref:System.Linq.Enumerable.Sum%2A> of 32-bit integer quantities is not computed by using 64-bit results.</span></span> <span data-ttu-id="a679a-167">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 转换 <xref:System.Linq.Enumerable.Sum%2A> 时，可能会发生溢出，即使对于内存中的对应序列，标准查询运算符的实现不会造成溢出，仍存在这种可能性。</span><span class="sxs-lookup"><span data-stu-id="a679a-167">Overflow might occur for a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Sum%2A>, even if the Standard Query Operator implementation does not cause an overflow for the corresponding in-memory sequence.</span></span>

<span data-ttu-id="a679a-168">同样，使用经 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 转换后的 <xref:System.Linq.Enumerable.Average%2A> 计算整数值时，所得结果的数据类型为 `integer`，而非 `double`。</span><span class="sxs-lookup"><span data-stu-id="a679a-168">Likewise, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of <xref:System.Linq.Enumerable.Average%2A> of integer values is computed as an `integer`, not as a `double`.</span></span>

### <a name="entity-arguments"></a><span data-ttu-id="a679a-169">实体自变量</span><span class="sxs-lookup"><span data-stu-id="a679a-169">Entity Arguments</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a679a-170">允许在 <xref:System.Linq.Enumerable.GroupBy%2A> 和 <xref:System.Linq.Enumerable.OrderBy%2A> 方法中使用实体类型。</span><span class="sxs-lookup"><span data-stu-id="a679a-170">enables entity types to be used in the <xref:System.Linq.Enumerable.GroupBy%2A> and <xref:System.Linq.Enumerable.OrderBy%2A> methods.</span></span> <span data-ttu-id="a679a-171">在这些运算符的转换过程中，使用一种类型的自变量被视为等效于指定该类型的所有成员。</span><span class="sxs-lookup"><span data-stu-id="a679a-171">In the translation of these operators, the use of an argument of a type is considered to be the equivalent to specifying all members of that type.</span></span> <span data-ttu-id="a679a-172">例如，下面的代码是等效的：</span><span class="sxs-lookup"><span data-stu-id="a679a-172">For example, the following code is equivalent:</span></span>

[!code-csharp[DLinqSQOTranslation#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#2)]
[!code-vb[DLinqSQOTranslation#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#2)]

### <a name="equatable--comparable-arguments"></a><span data-ttu-id="a679a-173">可相等/可比较自变量</span><span class="sxs-lookup"><span data-stu-id="a679a-173">Equatable / Comparable Arguments</span></span>

<span data-ttu-id="a679a-174">在以下方法的实现中，要求自变量相等：</span><span class="sxs-lookup"><span data-stu-id="a679a-174">Equality of arguments is required in the implementation of the following methods:</span></span>

- <xref:System.Linq.Enumerable.Contains%2A>

- <xref:System.Linq.Enumerable.Skip%2A>

- <xref:System.Linq.Enumerable.Union%2A>

- <xref:System.Linq.Enumerable.Intersect%2A>

- <xref:System.Linq.Enumerable.Except%2A>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a679a-175">支持*平面*参数的相等性和比较，但不支持或包含序列的参数。</span><span class="sxs-lookup"><span data-stu-id="a679a-175">supports equality and comparison for *flat* arguments, but not for arguments that are or contain sequences.</span></span> <span data-ttu-id="a679a-176">平参数是一种能映射到 SQL 行的类型。</span><span class="sxs-lookup"><span data-stu-id="a679a-176">A flat argument is a type that can be mapped to a SQL row.</span></span> <span data-ttu-id="a679a-177">可以静态方式确定不包含序列的一个或多个实体类型的投影被视为平参数。</span><span class="sxs-lookup"><span data-stu-id="a679a-177">A projection of one or more entity types that can be statically determined not to contain a sequence is considered a flat argument.</span></span>

<span data-ttu-id="a679a-178">下面是平面参数的示例：</span><span class="sxs-lookup"><span data-stu-id="a679a-178">The following are examples of flat arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#3](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#3)]
[!code-vb[DLinqSQOTranslation#3](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#3)]

<span data-ttu-id="a679a-179">下面是非平面（分层）参数的示例：</span><span class="sxs-lookup"><span data-stu-id="a679a-179">The following are examples of non-flat (hierarchical) arguments:</span></span>

[!code-csharp[DLinqSQOTranslation#4](~/samples/snippets/csharp/VS_Snippets_Data/DLinqSQOTranslation/cs/Program.cs#4)]
[!code-vb[DLinqSQOTranslation#4](~/samples/snippets/visualbasic/VS_Snippets_Data/DLinqSQOTranslation/vb/Module1.vb#4)]

### <a name="visual-basic-function-translation"></a><span data-ttu-id="a679a-180">Visual Basic 函数转换</span><span class="sxs-lookup"><span data-stu-id="a679a-180">Visual Basic Function Translation</span></span>

<span data-ttu-id="a679a-181">Visual Basic 编译器使用的以下 Helper 函数转换为对应的 SQL 运算符和函数：</span><span class="sxs-lookup"><span data-stu-id="a679a-181">The following helper functions that are used by the Visual Basic compiler are translated to corresponding SQL operators and functions:</span></span>

- `CompareString`

- `DateTime.Compare`

- `Decimal.Compare`

- `IIf (in Microsoft.VisualBasic.Interaction)`

<span data-ttu-id="a679a-182">转换方法：</span><span class="sxs-lookup"><span data-stu-id="a679a-182">Conversion methods:</span></span>

|||||
|-|-|-|-|
|<span data-ttu-id="a679a-183">ToBoolean</span><span class="sxs-lookup"><span data-stu-id="a679a-183">ToBoolean</span></span>|<span data-ttu-id="a679a-184">ToSByte</span><span class="sxs-lookup"><span data-stu-id="a679a-184">ToSByte</span></span>|<span data-ttu-id="a679a-185">ToByte</span><span class="sxs-lookup"><span data-stu-id="a679a-185">ToByte</span></span>|<span data-ttu-id="a679a-186">ToChar</span><span class="sxs-lookup"><span data-stu-id="a679a-186">ToChar</span></span>|
|<span data-ttu-id="a679a-187">ToCharArrayRankOne</span><span class="sxs-lookup"><span data-stu-id="a679a-187">ToCharArrayRankOne</span></span>|<span data-ttu-id="a679a-188">ToDate</span><span class="sxs-lookup"><span data-stu-id="a679a-188">ToDate</span></span>|<span data-ttu-id="a679a-189">ToDecimal</span><span class="sxs-lookup"><span data-stu-id="a679a-189">ToDecimal</span></span>|<span data-ttu-id="a679a-190">ToDouble</span><span class="sxs-lookup"><span data-stu-id="a679a-190">ToDouble</span></span>|
|<span data-ttu-id="a679a-191">ToInteger</span><span class="sxs-lookup"><span data-stu-id="a679a-191">ToInteger</span></span>|<span data-ttu-id="a679a-192">ToUInteger</span><span class="sxs-lookup"><span data-stu-id="a679a-192">ToUInteger</span></span>|<span data-ttu-id="a679a-193">ToLong</span><span class="sxs-lookup"><span data-stu-id="a679a-193">ToLong</span></span>|<span data-ttu-id="a679a-194">ToULong</span><span class="sxs-lookup"><span data-stu-id="a679a-194">ToULong</span></span>|
|<span data-ttu-id="a679a-195">ToShort</span><span class="sxs-lookup"><span data-stu-id="a679a-195">ToShort</span></span>|<span data-ttu-id="a679a-196">ToUShort</span><span class="sxs-lookup"><span data-stu-id="a679a-196">ToUShort</span></span>|<span data-ttu-id="a679a-197">ToSingle</span><span class="sxs-lookup"><span data-stu-id="a679a-197">ToSingle</span></span>|<span data-ttu-id="a679a-198">ToString</span><span class="sxs-lookup"><span data-stu-id="a679a-198">ToString</span></span>|

## <a name="inheritance-support"></a><span data-ttu-id="a679a-199">层次结构支持</span><span class="sxs-lookup"><span data-stu-id="a679a-199">Inheritance Support</span></span>

### <a name="inheritance-mapping-restrictions"></a><span data-ttu-id="a679a-200">继承映射限制</span><span class="sxs-lookup"><span data-stu-id="a679a-200">Inheritance Mapping Restrictions</span></span>

<span data-ttu-id="a679a-201">有关详细信息，请参阅[如何：映射继承层次结构 @ no__t。</span><span class="sxs-lookup"><span data-stu-id="a679a-201">For more information, see [How to: Map Inheritance Hierarchies](how-to-map-inheritance-hierarchies.md).</span></span>

### <a name="inheritance-in-queries"></a><span data-ttu-id="a679a-202">查询中的继承</span><span class="sxs-lookup"><span data-stu-id="a679a-202">Inheritance in Queries</span></span>

<span data-ttu-id="a679a-203">仅支持在投影中使用 C# 强制转换。</span><span class="sxs-lookup"><span data-stu-id="a679a-203">C# casts are supported only in projection.</span></span> <span data-ttu-id="a679a-204">在其他地方使用的强制转换不会进行转换且会被忽略。</span><span class="sxs-lookup"><span data-stu-id="a679a-204">Casts that are used elsewhere are not translated and are ignored.</span></span> <span data-ttu-id="a679a-205">除 SQL 函数名以外，SQL 确实仅执行公共语言运行库 (CLR) <xref:System.Convert> 的等效项。</span><span class="sxs-lookup"><span data-stu-id="a679a-205">Aside from SQL function names, SQL really only performs the equivalent of the common language runtime (CLR) <xref:System.Convert>.</span></span> <span data-ttu-id="a679a-206">也就是说，SQL 可以将一种类型的值更改为另一类型。</span><span class="sxs-lookup"><span data-stu-id="a679a-206">That is, SQL can change the value of one type to another.</span></span> <span data-ttu-id="a679a-207">CLR 强制转换不存在等效项，这是因为不存在这样的概念：重新解释与另一类型的位相同的位。</span><span class="sxs-lookup"><span data-stu-id="a679a-207">There is no equivalent of CLR cast because there is no concept of reinterpreting the same bits as those of another type.</span></span> <span data-ttu-id="a679a-208">正因如此，C# 强制转换只能在本地使用。</span><span class="sxs-lookup"><span data-stu-id="a679a-208">That is why a C# cast works only locally.</span></span> <span data-ttu-id="a679a-209">它无法以远程方式使用。</span><span class="sxs-lookup"><span data-stu-id="a679a-209">It is not remoted.</span></span>

<span data-ttu-id="a679a-210">运算符 `is` 和 `as` 以及 `GetType` 方法并不限于 `Select` 运算符。</span><span class="sxs-lookup"><span data-stu-id="a679a-210">The operators, `is` and `as`, and the `GetType` method are not restricted to the `Select` operator.</span></span> <span data-ttu-id="a679a-211">它们还可以用在其他查询运算符中。</span><span class="sxs-lookup"><span data-stu-id="a679a-211">They can be used in other query operators also.</span></span>

## <a name="sql-server-2008-support"></a><span data-ttu-id="a679a-212">SQL Server 2008 支持</span><span class="sxs-lookup"><span data-stu-id="a679a-212">SQL Server 2008 Support</span></span>

<span data-ttu-id="a679a-213">从 .NET Framework 3.5 SP1 开始，LINQ to SQL 支持映射到在 SQL Server 2008 中引入的新的日期和时间类型。</span><span class="sxs-lookup"><span data-stu-id="a679a-213">Starting with the .NET Framework 3.5 SP1, LINQ to SQL supports mapping to new date and time types introduced with SQL Server 2008.</span></span> <span data-ttu-id="a679a-214">但是，对于您可以在操作映射到这些新类型的值时使用的 LINQ to SQL 查询运算符有一些限制。</span><span class="sxs-lookup"><span data-stu-id="a679a-214">But, there are some limitations to the LINQ to SQL query operators that you can use when operating against values mapped to these new types.</span></span>

### <a name="unsupported-query-operators"></a><span data-ttu-id="a679a-215">不支持的查询运算符</span><span class="sxs-lookup"><span data-stu-id="a679a-215">Unsupported Query Operators</span></span>

<span data-ttu-id="a679a-216">映射到新的 SQL Server 日期和时间类型的值不支持下面的查询运算符：`DATETIME2`、`DATE`、`TIME` 和 `DATETIMEOFFSET`。</span><span class="sxs-lookup"><span data-stu-id="a679a-216">The following query operators are not supported on values mapped to the new SQL Server date and time types: `DATETIME2`, `DATE`, `TIME`, and `DATETIMEOFFSET`.</span></span>

- `Aggregate`

- `Average`

- `LastOrDefault`

- `OfType`

- `Sum`

<span data-ttu-id="a679a-217">有关映射到这些 SQL Server 日期和时间类型的详细信息，请参阅[SQL-CLR 类型映射](sql-clr-type-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="a679a-217">For more information about mapping to these SQL Server date and time types, see [SQL-CLR Type Mapping](sql-clr-type-mapping.md).</span></span>

## <a name="sql-server-2005-support"></a><span data-ttu-id="a679a-218">SQL Server 2005 支持</span><span class="sxs-lookup"><span data-stu-id="a679a-218">SQL Server 2005 Support</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a679a-219">不支持以下 SQL Server 2005 功能：</span><span class="sxs-lookup"><span data-stu-id="a679a-219">does not support the following SQL Server 2005 features:</span></span>

- <span data-ttu-id="a679a-220">为 SQL CLR 编写的存储过程。</span><span class="sxs-lookup"><span data-stu-id="a679a-220">Stored procedures written for SQL CLR.</span></span>

- <span data-ttu-id="a679a-221">用户定义的类型。</span><span class="sxs-lookup"><span data-stu-id="a679a-221">User-defined type.</span></span>

- <span data-ttu-id="a679a-222">XML 查询功能。</span><span class="sxs-lookup"><span data-stu-id="a679a-222">XML query features.</span></span>

## <a name="sql-server-2000-support"></a><span data-ttu-id="a679a-223">SQL Server 2000 支持</span><span class="sxs-lookup"><span data-stu-id="a679a-223">SQL Server 2000 Support</span></span>

<span data-ttu-id="a679a-224">以下 SQL Server 2000 限制（与 Microsoft SQL Server 2005 相比）影响 @no__t 0 支持。</span><span class="sxs-lookup"><span data-stu-id="a679a-224">The following SQL Server 2000 limitations (compared to Microsoft SQL Server 2005) affect [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] support.</span></span>

### <a name="cross-apply-and-outer-apply-operators"></a><span data-ttu-id="a679a-225">Cross Apply 和 Outer Apply 运算符</span><span class="sxs-lookup"><span data-stu-id="a679a-225">Cross Apply and Outer Apply Operators</span></span>

<span data-ttu-id="a679a-226">这些运算符在 SQL Server 2000 中不可用。</span><span class="sxs-lookup"><span data-stu-id="a679a-226">These operators are not available in SQL Server 2000.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a679a-227">设法通过一系列的重写来将它们替换为适当的联接。</span><span class="sxs-lookup"><span data-stu-id="a679a-227">tries a series of rewrites to replace them with appropriate joins.</span></span>

<span data-ttu-id="a679a-228">`Cross Apply` 和 `Outer Apply` 是为关系导航生成的。</span><span class="sxs-lookup"><span data-stu-id="a679a-228">`Cross Apply` and `Outer Apply` are generated for relationship navigations.</span></span> <span data-ttu-id="a679a-229">可以进行这种重写的查询集定义不完善。</span><span class="sxs-lookup"><span data-stu-id="a679a-229">The set of queries for which such rewrites are possible is not well defined.</span></span> <span data-ttu-id="a679a-230">出于此原因，SQL Server 2000 支持的最小查询集是不涉及关系导航的集。</span><span class="sxs-lookup"><span data-stu-id="a679a-230">For this reason, the minimal set of queries that is supported for SQL Server 2000 is the set that does not involve relationship navigation.</span></span>

### <a name="text--ntext"></a><span data-ttu-id="a679a-231">text / ntext</span><span class="sxs-lookup"><span data-stu-id="a679a-231">text / ntext</span></span>

<span data-ttu-id="a679a-232">数据类型 `text` @ no__t-1 @ no__t-2 不能用于针对 Microsoft SQL Server 2005 支持的 @no__t 3 @ no__t @ @ no__t 的某些查询操作。</span><span class="sxs-lookup"><span data-stu-id="a679a-232">Data types `text` / `ntext` cannot be used in certain query operations against `varchar(max)` / `nvarchar(max)`, which are supported by Microsoft SQL Server 2005.</span></span>

<span data-ttu-id="a679a-233">不存在解决此限制的方法。</span><span class="sxs-lookup"><span data-stu-id="a679a-233">No resolution is available for this limitation.</span></span> <span data-ttu-id="a679a-234">具体而言，您不能对包含映射到 `Distinct()` 或 `text` 列的成员的任何结果使用 `ntext`。</span><span class="sxs-lookup"><span data-stu-id="a679a-234">Specifically, you cannot use `Distinct()` on any result that contains members that are mapped to `text` or `ntext` columns.</span></span>

### <a name="behavior-triggered-by-nested-queries"></a><span data-ttu-id="a679a-235">由嵌套查询触发的行为</span><span class="sxs-lookup"><span data-stu-id="a679a-235">Behavior Triggered by Nested Queries</span></span>

<span data-ttu-id="a679a-236">SQL Server 2000 （到 SP4）联编程序具有由嵌套查询触发的一些特性。</span><span class="sxs-lookup"><span data-stu-id="a679a-236">SQL Server 2000 (through SP4) binder has some idiosyncrasies that are triggered by nested queries.</span></span> <span data-ttu-id="a679a-237">触发这些特性的 SQL 查询集定义不完善。</span><span class="sxs-lookup"><span data-stu-id="a679a-237">The set of SQL queries that triggers these idiosyncrasies is not well defined.</span></span> <span data-ttu-id="a679a-238">因此，您不能定义可能会引发 SQL Server 异常的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查询集。</span><span class="sxs-lookup"><span data-stu-id="a679a-238">For this reason, you cannot define the set of [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries that might cause SQL Server exceptions.</span></span>

### <a name="skip-and-take-operators"></a><span data-ttu-id="a679a-239">Skip 和 Take 运算符</span><span class="sxs-lookup"><span data-stu-id="a679a-239">Skip and Take Operators</span></span>

<span data-ttu-id="a679a-240"><xref:System.Linq.Enumerable.Take%2A> 和 <xref:System.Linq.Enumerable.Skip%2A> 用在针对 SQL Server 2000 的查询中时存在一定的限制。</span><span class="sxs-lookup"><span data-stu-id="a679a-240"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="a679a-241">有关详细信息，请参阅[疑难解答](troubleshooting.md)中的 "跳过并使用 SQL Server 2000" 条目。</span><span class="sxs-lookup"><span data-stu-id="a679a-241">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="object-materialization"></a><span data-ttu-id="a679a-242">对象具体化</span><span class="sxs-lookup"><span data-stu-id="a679a-242">Object Materialization</span></span>

<span data-ttu-id="a679a-243">具体化过程用一个或多个 SQL 查询返回的行创建 CLR 对象。</span><span class="sxs-lookup"><span data-stu-id="a679a-243">Materialization creates CLR objects from rows that are returned by one or more SQL queries.</span></span>

- <span data-ttu-id="a679a-244">以下调用作为具体化的一部分在*本地执行*：</span><span class="sxs-lookup"><span data-stu-id="a679a-244">The following calls are *executed locally* as a part of materialization:</span></span>

  - <span data-ttu-id="a679a-245">构造函数</span><span class="sxs-lookup"><span data-stu-id="a679a-245">Constructors</span></span>

  - <span data-ttu-id="a679a-246">投影中的 `ToString` 方法</span><span class="sxs-lookup"><span data-stu-id="a679a-246">`ToString` methods in projections</span></span>

  - <span data-ttu-id="a679a-247">投影中的类型强制转换</span><span class="sxs-lookup"><span data-stu-id="a679a-247">Type casts in projections</span></span>

- <span data-ttu-id="a679a-248">执行 <xref:System.Linq.Enumerable.AsEnumerable%2A> 方法的方法在*本地执行*。</span><span class="sxs-lookup"><span data-stu-id="a679a-248">Methods that follow the <xref:System.Linq.Enumerable.AsEnumerable%2A> method are *executed locally*.</span></span> <span data-ttu-id="a679a-249">此方法不会导致直接执行。</span><span class="sxs-lookup"><span data-stu-id="a679a-249">This method does not cause immediate execution.</span></span>

- <span data-ttu-id="a679a-250">您可以将 `struct` 用作查询结果的返回类型或结果类型的成员。</span><span class="sxs-lookup"><span data-stu-id="a679a-250">You can use a `struct` as the return type of a query result or as a member of the result type.</span></span> <span data-ttu-id="a679a-251">实体需要变成类。</span><span class="sxs-lookup"><span data-stu-id="a679a-251">Entities are required to be classes.</span></span> <span data-ttu-id="a679a-252">匿名类型具体化为类的实例，但命名结构（非实体）可在投影中使用。</span><span class="sxs-lookup"><span data-stu-id="a679a-252">Anonymous types are materialized as class instances, but named structs (non-entities) can be used in projection.</span></span>

- <span data-ttu-id="a679a-253">查询结果的返回类型的成员可以为 <xref:System.Linq.IQueryable%601> 类型。</span><span class="sxs-lookup"><span data-stu-id="a679a-253">A member of the return type of a query result can be of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="a679a-254">它具体化为本地集合。</span><span class="sxs-lookup"><span data-stu-id="a679a-254">It is materialized as a local collection.</span></span>

- <span data-ttu-id="a679a-255">下面的方法导致*直接具体化*将方法应用到的序列：</span><span class="sxs-lookup"><span data-stu-id="a679a-255">The following methods cause the *immediate materialization* of the sequence that the methods are applied to:</span></span>

  - <xref:System.Linq.Enumerable.ToList%2A>

  - <xref:System.Linq.Enumerable.ToDictionary%2A>

  - <xref:System.Linq.Enumerable.ToArray%2A>

## <a name="see-also"></a><span data-ttu-id="a679a-256">请参阅</span><span class="sxs-lookup"><span data-stu-id="a679a-256">See also</span></span>

- [<span data-ttu-id="a679a-257">引用</span><span class="sxs-lookup"><span data-stu-id="a679a-257">Reference</span></span>](reference.md)
- [<span data-ttu-id="a679a-258">返回或跳过序列中的元素</span><span class="sxs-lookup"><span data-stu-id="a679a-258">Return Or Skip Elements in a Sequence</span></span>](return-or-skip-elements-in-a-sequence.md)
- [<span data-ttu-id="a679a-259">连接两个序列</span><span class="sxs-lookup"><span data-stu-id="a679a-259">Concatenate Two Sequences</span></span>](concatenate-two-sequences.md)
- [<span data-ttu-id="a679a-260">返回两个序列之间的差集</span><span class="sxs-lookup"><span data-stu-id="a679a-260">Return the Set Difference Between Two Sequences</span></span>](return-the-set-difference-between-two-sequences.md)
- [<span data-ttu-id="a679a-261">返回两个序列的交集</span><span class="sxs-lookup"><span data-stu-id="a679a-261">Return the Set Intersection of Two Sequences</span></span>](return-the-set-intersection-of-two-sequences.md)
- [<span data-ttu-id="a679a-262">返回两个序列的并集</span><span class="sxs-lookup"><span data-stu-id="a679a-262">Return the Set Union of Two Sequences</span></span>](return-the-set-union-of-two-sequences.md)
