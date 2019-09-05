---
title: 从命令目录树生成 SQL - 最佳做法
ms.date: 03/30/2017
ms.assetid: 71ef6a24-4c4f-4254-af3a-ffc0d855b0a8
ms.openlocfilehash: 366e27f8c8a04c5d2507ab37459ad6d5abc255ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251576"
---
# <a name="generating-sql-from-command-trees---best-practices"></a><span data-ttu-id="4e1fa-102">从命令目录树生成 SQL - 最佳做法</span><span class="sxs-lookup"><span data-stu-id="4e1fa-102">Generating SQL from Command Trees - Best Practices</span></span>

<span data-ttu-id="4e1fa-103">输出查询命令目录树高度模拟可使用 SQL 表示的查询。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-103">Output query command trees closely model queries expressible in SQL.</span></span> <span data-ttu-id="4e1fa-104">但是，对于提供程序编写者而言，从输出命令目录树生成 SQL 还是存在一些常见的难题。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-104">However, there are certain common challenges for provider writers when generating SQL from an output command tree.</span></span> <span data-ttu-id="4e1fa-105">本主题讨论这些难题。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-105">This topic discusses these challenges.</span></span> <span data-ttu-id="4e1fa-106">在下一主题中，示例提供程序将演示如何解决这些难题。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-106">In the next topic, the sample provider shows how to address these challenges.</span></span>

## <a name="group-dbexpression-nodes-in-a-sql-select-statement"></a><span data-ttu-id="4e1fa-107">对 SQL SELECT 语句中的 DbExpression Nodes 进行分组</span><span class="sxs-lookup"><span data-stu-id="4e1fa-107">Group DbExpression Nodes in a SQL SELECT Statement</span></span>

<span data-ttu-id="4e1fa-108">典型的 SQL 语句具有以下形式的嵌套结构：</span><span class="sxs-lookup"><span data-stu-id="4e1fa-108">A typical SQL statement has a nested structure of the following shape:</span></span>

```sql
SELECT …
FROM …
WHERE …
GROUP BY …
ORDER BY …
```

<span data-ttu-id="4e1fa-109">一个或多个子句可能为空。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-109">One or more clauses may be empty.</span></span>  <span data-ttu-id="4e1fa-110">在任何行中都可能会出现嵌套的 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-110">A nested SELECT statement could occur in any of the lines.</span></span>

<span data-ttu-id="4e1fa-111">查询命令目录树到 SQL SELECT 语句可能的转换会针对每个关系运算符产生一个子查询。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-111">A possible translation of a query command tree into a SQL SELECT statement would produce one subquery for every relational operator.</span></span> <span data-ttu-id="4e1fa-112">然而，这会导致一些难于读取的不必要的子查询。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-112">However, that would lead to unnecessary nested subqueries that would be difficult to read.</span></span>  <span data-ttu-id="4e1fa-113">对于某些数据存储，查询的性能可能会很差。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-113">On some data stores, the query may perform poorly.</span></span>

<span data-ttu-id="4e1fa-114">例如，考虑下面的查询命令目录树</span><span class="sxs-lookup"><span data-stu-id="4e1fa-114">As an example, consider the following query command tree</span></span>

```
Project (
a.x,
   a = Filter(
      b.y = 5,
      b = Scan("TableA")
   )
)
```

<span data-ttu-id="4e1fa-115">低效率的转换会产生：</span><span class="sxs-lookup"><span data-stu-id="4e1fa-115">An inefficient translation would produce:</span></span>

```sql
SELECT a.x
FROM (   SELECT *
         FROM TableA as b
         WHERE b.y = 5) as a
```

<span data-ttu-id="4e1fa-116">请注意，每个关系表达式节点都成为一个新的 SQL SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-116">Note that every relational expression node becomes a new SQL SELECT statement.</span></span>

<span data-ttu-id="4e1fa-117">因此，在保持正确的同时，一定要将尽可能多的表达式节点聚合到单个 SQL SELECT 语句中。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-117">Therefore, it is important to aggregate as many expression nodes as possible into a single SQL SELECT statement while preserving correctness.</span></span>

<span data-ttu-id="4e1fa-118">上面的示例的此类聚合的结果为：</span><span class="sxs-lookup"><span data-stu-id="4e1fa-118">The result of such aggregation for the example presented above would be:</span></span>

```sql
SELECT b.x
FROM TableA as b
WHERE b.y = 5
```

## <a name="flatten-joins-in-a-sql-select-statement"></a><span data-ttu-id="4e1fa-119">平展 SQL SELECT 语句中的联接</span><span class="sxs-lookup"><span data-stu-id="4e1fa-119">Flatten Joins in a SQL SELECT Statement</span></span>

<span data-ttu-id="4e1fa-120">将多个节点聚合成单个 SQL SELECT 语句的一种情况是将多个联接表达式聚合成单个 SQL SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-120">One case of aggregating multiple nodes into a single SQL SELECT statement is aggregating multiple join expressions into a single SQL SELECT statement.</span></span> <span data-ttu-id="4e1fa-121">DbJoinExpression 表示两个输入之间的单一联接。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-121">DbJoinExpression represents a single join between two inputs.</span></span> <span data-ttu-id="4e1fa-122">但是，作为单个 SQL SELECT 语句的一部分，可以指定多个联接。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-122">However, as part of a single SQL SELECT statement, more than one join can be specified.</span></span> <span data-ttu-id="4e1fa-123">在这种情况下，将按指定的顺序执行这些联接。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-123">In that case the joins are performed in the order specified.</span></span>

<span data-ttu-id="4e1fa-124">左侧刺联接（显示为另一个联接的左侧子级的联接）可以更加轻松地平展成单个 SQL SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-124">Left spine joins, (joins that appear as a left child of another join) can be more easily flattened into a single SQL SELECT statement.</span></span> <span data-ttu-id="4e1fa-125">例如，考虑以下查询命令目录树：</span><span class="sxs-lookup"><span data-stu-id="4e1fa-125">For example, consider the following query command tree:</span></span>

```
InnerJoin(
   a = LeftOuterJoin(
   b = Extent("TableA")
   c = Extent("TableB")
   ON b.y = c.x ),
   d = Extent("TableC")
   ON a.b.y = d.z
)
```

<span data-ttu-id="4e1fa-126">这可以正确地转换成：</span><span class="sxs-lookup"><span data-stu-id="4e1fa-126">This can be correctly translated into:</span></span>

```sql
SELECT *
FROM TableA as b
LEFT OUTER JOIN TableB as c ON b.y = c.x
INNER JOIN TableC as d ON b.y = d.z
```

<span data-ttu-id="4e1fa-127">但是，非左侧刺联接无法轻松地平展，而且您也不应尝试去平展它们。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-127">However, non-left spine joins cannot easily be flattened, and you should not try to flatten them.</span></span> <span data-ttu-id="4e1fa-128">例如，以下查询命令目录树中的联接：</span><span class="sxs-lookup"><span data-stu-id="4e1fa-128">For example, the joins in the following query command tree:</span></span>

```
InnerJoin(
   a = Extent("TableA")
   b = LeftOuterJoin(
   c = Extent("TableB")
   d = Extent("TableC")
   ON c.y = d.x),
   ON a.z = b.c.y
)
```

<span data-ttu-id="4e1fa-129">将转换成一个包含子查询的 SQL SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-129">Would be translated to a SQL SELECT statement with a sub-query.</span></span>

```sql
SELECT *
FROM TableA as a
INNER JOIN (SELECT *
   FROM TableB as c
   LEFT OUTER JOIN TableC as d
   ON c.y = d.x) as b
ON b.y = d.z
```

## <a name="input-alias-redirecting"></a><span data-ttu-id="4e1fa-130">输入别名重定向</span><span class="sxs-lookup"><span data-stu-id="4e1fa-130">Input Alias Redirecting</span></span>

<span data-ttu-id="4e1fa-131">为了解释输入别名重定向，请先考虑关系表达式的结构，如 DbFilterExpression、DbProjectExpression、DbCrossJoinExpression、DbJoinExpression、DbSortExpression、DbGroupByExpression、DbApplyExpression 和 DbSkipExpression。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-131">To explain input alias redirecting, consider the structure of the relational expressions, such as DbFilterExpression, DbProjectExpression, DbCrossJoinExpression, DbJoinExpression, DbSortExpression, DbGroupByExpression, DbApplyExpression, and DbSkipExpression.</span></span>

<span data-ttu-id="4e1fa-132">上述每种类型都具有一个或多个用于描述输入集合的 Input 属性，并且每个输入都对应一个绑定变量，用于在集合遍历期间表示该输入的每个元素。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-132">Each of these types has one or more Input properties that describe an input collection, and a binding variable corresponding to each input is used to represent each element of that input during a collection traversal.</span></span> <span data-ttu-id="4e1fa-133">当引用输入元素时（例如在 DbFilterExpression 的 Predicate 属性中或者在 DbProjectExpression 的 Projection 属性中），将使用相应的绑定变量。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-133">The binding variable is used when referring to the input element, for example in the Predicate property of a DbFilterExpression or the Projection property of a DbProjectExpression.</span></span>

<span data-ttu-id="4e1fa-134">在将更多的关系表达式节点聚合成单个 SQL SELECT 语句，并在计算一个作为关系表达式的一部分的表达式（例如 DbProjectExpression 的 Projection 属性的一部分）时，它所使用的绑定变量可能与输入的别名不相同，这是因为多个表达式绑定必须重定向到一个范围。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-134">When aggregating more relational expression nodes into a single SQL SELECT statement, and evaluating an expression that is part of a relational expression (for example part of the Projection property of a DbProjectExpression) the binding variable that it uses may not be the same as the alias of the input, as multiple expression bindings would have to be redirected to a single extent.</span></span>  <span data-ttu-id="4e1fa-135">这个问题称作“别名重命名”。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-135">This problem is called alias renaming.</span></span>

<span data-ttu-id="4e1fa-136">考虑本主题中的第一个示例。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-136">Consider the first example in this topic.</span></span> <span data-ttu-id="4e1fa-137">如果进行自然转换并转换 Projection a.x (DbPropertyExpression(a, x))，正确做法是将其转换为 `a.x`，因为我们已为输入提供别名“a”来匹配绑定变量。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-137">If doing the naïve translation and translating the Projection a.x (DbPropertyExpression(a, x)), it is correct to translate it into `a.x` because we have aliased the input as "a" to match the binding variable.</span></span>  <span data-ttu-id="4e1fa-138">但是，在将两个节点聚合成单个 SQL SELECT 语句时，需要将相同的 DbPropertyExpression 转换为 `b.x`，因为输入的别名已改为“b”。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-138">However, when aggregating both the nodes into a single SQL SELECT statement, you need to translate the same DbPropertyExpression into `b.x`, as the input has been aliased with "b".</span></span>

## <a name="join-alias-flattening"></a><span data-ttu-id="4e1fa-139">联接别名平展</span><span class="sxs-lookup"><span data-stu-id="4e1fa-139">Join Alias Flattening</span></span>

<span data-ttu-id="4e1fa-140">与输出命令目录树中的任何其他关系表达式不同，DbJoinExpression 输出一个结果类型，该结果类型是一个由两列组成的行，每一列都对应一个输入。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-140">Unlike any other relational expression in an output command tree, the DbJoinExpression outputs a result type that is a row consisting of two columns, each of which corresponds to one of the inputs.</span></span> <span data-ttu-id="4e1fa-141">当生成 DbPropertyExpression 以访问源自某个联接的标量属性时，该属性将超过另一个 DbPropertyExpression。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-141">When a DbPropertyExpression is built to access a scalar property originating from a join, it is over another DbPropertyExpression.</span></span>

<span data-ttu-id="4e1fa-142">示例包括示例 2 中的“a.b.y”和示例 3 中的“b.c.y”。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-142">Examples include "a.b.y" in example 2 and "b.c.y" in example 3.</span></span> <span data-ttu-id="4e1fa-143">但是，在对应的 SQL 语句中这些内容称为“b.y”。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-143">However in the corresponding SQL statements these are referred as "b.y".</span></span> <span data-ttu-id="4e1fa-144">这一重新设定别名问题称为“联接别名平展”。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-144">This re-aliasing is called join alias flattening.</span></span>

## <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="4e1fa-145">列名和范围别名重命名</span><span class="sxs-lookup"><span data-stu-id="4e1fa-145">Column Name and Extent Alias Renaming</span></span>

<span data-ttu-id="4e1fa-146">如果必须使用预测完成具有一个联接的 SQL SELECT 查询，则当枚举输入中的所有参与列时，可能会发生名称冲突，因为多个输入可能具有相同的列名。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-146">If a SQL SELECT query that has a join has to be completed with a projection, when enumerating all the participating columns from the inputs, a name collision may occur, as more than one input may have the same column name.</span></span> <span data-ttu-id="4e1fa-147">为同名列使用不同的名称可避免名称冲突。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-147">Use a different name for the column to avoid the collision.</span></span>

<span data-ttu-id="4e1fa-148">此外，当平展联接时，参与的表（或子查询）可能存在互相冲突的别名，这种情况下需要进行重命名。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-148">Also, when flattening joins, participating tables (or subqueries) may have colliding aliases in which case these need to be renamed.</span></span>

## <a name="avoid-select-"></a><span data-ttu-id="4e1fa-149">避免 SELECT \*</span><span class="sxs-lookup"><span data-stu-id="4e1fa-149">Avoid SELECT \*</span></span>

<span data-ttu-id="4e1fa-150">不要使用 `SELECT *` 从基表中进行选择。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-150">Do not use `SELECT *` to select from base tables.</span></span> <span data-ttu-id="4e1fa-151">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]应用程序中的存储模型只能包含数据库表中的列的子集。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-151">The storage model in an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] application may only include a subset of the columns that are in the database table.</span></span> <span data-ttu-id="4e1fa-152">在这种情况下，`SELECT *` 可能产生不正确的结果。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-152">In this case, `SELECT *` may produce an incorrect result.</span></span> <span data-ttu-id="4e1fa-153">替代方法是，应通过使用参与的表达式的结果类型中的列名，指定所有参与的列。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-153">Instead, you should specify all participating columns by using the column names from the result type of the participating expressions.</span></span>

## <a name="reuse-of-expressions"></a><span data-ttu-id="4e1fa-154">重用表达式</span><span class="sxs-lookup"><span data-stu-id="4e1fa-154">Reuse of Expressions</span></span>

<span data-ttu-id="4e1fa-155">在由[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]传递的查询命令目录树中可以重用表达式。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-155">Expressions may be reused in the query command tree passed by the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="4e1fa-156">不要假定每个表达式在查询命令目录树中仅出现一次。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-156">Do not assume that each expression appears only once in the query command tree.</span></span>

## <a name="mapping-primitive-types"></a><span data-ttu-id="4e1fa-157">映射基元类型</span><span class="sxs-lookup"><span data-stu-id="4e1fa-157">Mapping Primitive Types</span></span>

<span data-ttu-id="4e1fa-158">在将概念 (EDM) 类型映射到提供程序类型时，应映射到最宽的类型 (Int32)，以便适合所有可能的值。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-158">When mapping conceptual (EDM) types to provider types, you should map to the widest type (Int32) so that all possible values fit.</span></span> <span data-ttu-id="4e1fa-159">另外，请避免映射到不能用于许多操作的类型（例如 BLOB 类型）（例如， `ntext`在 SQL Server 中）。</span><span class="sxs-lookup"><span data-stu-id="4e1fa-159">Also, avoid mapping to types that cannot be used for many operations, like BLOB types (for example, `ntext` in SQL Server).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e1fa-160">请参阅</span><span class="sxs-lookup"><span data-stu-id="4e1fa-160">See also</span></span>

- [<span data-ttu-id="4e1fa-161">SQL 生成</span><span class="sxs-lookup"><span data-stu-id="4e1fa-161">SQL Generation</span></span>](sql-generation.md)
