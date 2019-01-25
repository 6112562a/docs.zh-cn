---
title: 聚合规范函数
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: f65557703070a43f586a668903d049a374ef70d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708969"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="a73d6-102">聚合规范函数</span><span class="sxs-lookup"><span data-stu-id="a73d6-102">Aggregate Canonical Functions</span></span>

<span data-ttu-id="a73d6-103">聚合是缩减一系列输入值（例如，缩减为单个值）的表达式。</span><span class="sxs-lookup"><span data-stu-id="a73d6-103">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="a73d6-104">聚合通常与 SELECT 表达式的 GROUP BY 子句一起使用，对于可以使用聚合的位置存在一些约束。</span><span class="sxs-lookup"><span data-stu-id="a73d6-104">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggegate-entity-sql-canonical-functions"></a><span data-ttu-id="a73d6-105">Aggegate Entity SQL 规范函数</span><span class="sxs-lookup"><span data-stu-id="a73d6-105">Aggegate Entity SQL canonical functions</span></span>

<span data-ttu-id="a73d6-106">下面是聚合的 Entity SQL 规范函数。</span><span class="sxs-lookup"><span data-stu-id="a73d6-106">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="a73d6-107">Avg(expression)</span><span class="sxs-lookup"><span data-stu-id="a73d6-107">Avg(expression)</span></span>

<span data-ttu-id="a73d6-108">返回非 null 值的平均值。</span><span class="sxs-lookup"><span data-stu-id="a73d6-108">Returns the average of the non-null values.</span></span>

<span data-ttu-id="a73d6-109">**参数**</span><span class="sxs-lookup"><span data-stu-id="a73d6-109">**Arguments**</span></span>

<span data-ttu-id="a73d6-110">`Int32`， `Int64`， `Double`，和`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="a73d6-110">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="a73d6-111">**返回值**</span><span class="sxs-lookup"><span data-stu-id="a73d6-111">**Return Value**</span></span>

<span data-ttu-id="a73d6-112">类型`expression`，或`null`所有输入的值是否为`null`值。</span><span class="sxs-lookup"><span data-stu-id="a73d6-112">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="a73d6-113">**示例**</span><span class="sxs-lookup"><span data-stu-id="a73d6-113">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)] 
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="a73d6-114">BigCount(expression)</span><span class="sxs-lookup"><span data-stu-id="a73d6-114">BigCount(expression)</span></span>

<span data-ttu-id="a73d6-115">返回包含 null 值和重复值的聚合的大小。</span><span class="sxs-lookup"><span data-stu-id="a73d6-115">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="a73d6-116">**参数**</span><span class="sxs-lookup"><span data-stu-id="a73d6-116">**Arguments**</span></span>

<span data-ttu-id="a73d6-117">任何类型。</span><span class="sxs-lookup"><span data-stu-id="a73d6-117">Any type.</span></span>

<span data-ttu-id="a73d6-118">**返回值**</span><span class="sxs-lookup"><span data-stu-id="a73d6-118">**Return Value**</span></span>

<span data-ttu-id="a73d6-119">一个 `Int64`。</span><span class="sxs-lookup"><span data-stu-id="a73d6-119">An `Int64`.</span></span>

<span data-ttu-id="a73d6-120">**示例**</span><span class="sxs-lookup"><span data-stu-id="a73d6-120">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)] 
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="a73d6-121">Count(expression)</span><span class="sxs-lookup"><span data-stu-id="a73d6-121">Count(expression)</span></span> 

<span data-ttu-id="a73d6-122">返回包含 null 值和重复值的聚合的大小。</span><span class="sxs-lookup"><span data-stu-id="a73d6-122">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="a73d6-123">**参数**</span><span class="sxs-lookup"><span data-stu-id="a73d6-123">**Arguments**</span></span>

<span data-ttu-id="a73d6-124">任何类型。</span><span class="sxs-lookup"><span data-stu-id="a73d6-124">Any type.</span></span>

<span data-ttu-id="a73d6-125">**返回值**</span><span class="sxs-lookup"><span data-stu-id="a73d6-125">**Return Value**</span></span>

<span data-ttu-id="a73d6-126">一个 `Int32`。</span><span class="sxs-lookup"><span data-stu-id="a73d6-126">An `Int32`.</span></span>

<span data-ttu-id="a73d6-127">**示例**</span><span class="sxs-lookup"><span data-stu-id="a73d6-127">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="a73d6-128">Max(expression)</span><span class="sxs-lookup"><span data-stu-id="a73d6-128">Max(expression)</span></span>

<span data-ttu-id="a73d6-129">返回非 null 值的最大值。</span><span class="sxs-lookup"><span data-stu-id="a73d6-129">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="a73d6-130">**参数**</span><span class="sxs-lookup"><span data-stu-id="a73d6-130">**Arguments**</span></span>

<span data-ttu-id="a73d6-131">`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。</span><span class="sxs-lookup"><span data-stu-id="a73d6-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="a73d6-132">**返回值**</span><span class="sxs-lookup"><span data-stu-id="a73d6-132">**Return Value**</span></span>

<span data-ttu-id="a73d6-133">类型`expression`，或`null`所有输入的值是否为`null`值。</span><span class="sxs-lookup"><span data-stu-id="a73d6-133">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="a73d6-134">**示例**</span><span class="sxs-lookup"><span data-stu-id="a73d6-134">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="a73d6-135">Min(expression)</span><span class="sxs-lookup"><span data-stu-id="a73d6-135">Min(expression)</span></span>

<span data-ttu-id="a73d6-136">返回非 null 值的最小值。</span><span class="sxs-lookup"><span data-stu-id="a73d6-136">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="a73d6-137">**参数**</span><span class="sxs-lookup"><span data-stu-id="a73d6-137">**Arguments**</span></span>

<span data-ttu-id="a73d6-138">`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。</span><span class="sxs-lookup"><span data-stu-id="a73d6-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="a73d6-139">**返回值**</span><span class="sxs-lookup"><span data-stu-id="a73d6-139">**Return Value**</span></span>

<span data-ttu-id="a73d6-140">类型`expression`，或`null`所有输入的值是否为`null`值。</span><span class="sxs-lookup"><span data-stu-id="a73d6-140">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="a73d6-141">**示例**</span><span class="sxs-lookup"><span data-stu-id="a73d6-141">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="a73d6-142">StDev(expression)</span><span class="sxs-lookup"><span data-stu-id="a73d6-142">StDev(expression)</span></span>

<span data-ttu-id="a73d6-143">返回非 null 值的标准偏差。</span><span class="sxs-lookup"><span data-stu-id="a73d6-143">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="a73d6-144">**参数**</span><span class="sxs-lookup"><span data-stu-id="a73d6-144">**Arguments**</span></span>

<span data-ttu-id="a73d6-145">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="a73d6-145">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="a73d6-146">**返回值**</span><span class="sxs-lookup"><span data-stu-id="a73d6-146">**Return Value**</span></span>

<span data-ttu-id="a73d6-147">`Double`。</span><span class="sxs-lookup"><span data-stu-id="a73d6-147">A `Double`.</span></span> <span data-ttu-id="a73d6-148">如果所有输入值均为 `Null` 值，则为 `null`。</span><span class="sxs-lookup"><span data-stu-id="a73d6-148">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="a73d6-149">**示例**</span><span class="sxs-lookup"><span data-stu-id="a73d6-149">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="a73d6-150">StDevP(expression)</span><span class="sxs-lookup"><span data-stu-id="a73d6-150">StDevP(expression)</span></span>

<span data-ttu-id="a73d6-151">返回所有值的总体标准偏差。</span><span class="sxs-lookup"><span data-stu-id="a73d6-151">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="a73d6-152">**参数**</span><span class="sxs-lookup"><span data-stu-id="a73d6-152">**Arguments**</span></span>

<span data-ttu-id="a73d6-153">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="a73d6-153">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="a73d6-154">**返回值**</span><span class="sxs-lookup"><span data-stu-id="a73d6-154">**Return Value**</span></span>

<span data-ttu-id="a73d6-155">一个`Double`，或`null`所有输入的值是否为`null`值。</span><span class="sxs-lookup"><span data-stu-id="a73d6-155">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="a73d6-156">**示例**</span><span class="sxs-lookup"><span data-stu-id="a73d6-156">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="a73d6-157">Sum(expression)</span><span class="sxs-lookup"><span data-stu-id="a73d6-157">Sum(expression)</span></span>

<span data-ttu-id="a73d6-158">返回非 null 值的总和。</span><span class="sxs-lookup"><span data-stu-id="a73d6-158">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="a73d6-159">**参数**</span><span class="sxs-lookup"><span data-stu-id="a73d6-159">**Arguments**</span></span>

<span data-ttu-id="a73d6-160">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="a73d6-160">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="a73d6-161">**返回值**</span><span class="sxs-lookup"><span data-stu-id="a73d6-161">**Return Value**</span></span>

<span data-ttu-id="a73d6-162">一个`Double`，或`null`所有输入的值是否为`null`值。</span><span class="sxs-lookup"><span data-stu-id="a73d6-162">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="a73d6-163">**示例**</span><span class="sxs-lookup"><span data-stu-id="a73d6-163">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="a73d6-164">Var(expression)</span><span class="sxs-lookup"><span data-stu-id="a73d6-164">Var(expression)</span></span>

<span data-ttu-id="a73d6-165">返回所有非 Null 值的方差。</span><span class="sxs-lookup"><span data-stu-id="a73d6-165">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="a73d6-166">**参数**</span><span class="sxs-lookup"><span data-stu-id="a73d6-166">**Arguments**</span></span>

<span data-ttu-id="a73d6-167">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="a73d6-167">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="a73d6-168">**返回值**</span><span class="sxs-lookup"><span data-stu-id="a73d6-168">**Return Value**</span></span>

<span data-ttu-id="a73d6-169">一个`Double`，或`null`所有输入的值是否为`null`值。</span><span class="sxs-lookup"><span data-stu-id="a73d6-169">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="a73d6-170">**示例**</span><span class="sxs-lookup"><span data-stu-id="a73d6-170">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="a73d6-171">VarP(expression)</span><span class="sxs-lookup"><span data-stu-id="a73d6-171">VarP(expression)</span></span>

<span data-ttu-id="a73d6-172">返回所有非 Null 值的总体方差。</span><span class="sxs-lookup"><span data-stu-id="a73d6-172">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="a73d6-173">**参数**</span><span class="sxs-lookup"><span data-stu-id="a73d6-173">**Arguments**</span></span>

<span data-ttu-id="a73d6-174">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="a73d6-174">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="a73d6-175">**返回值**</span><span class="sxs-lookup"><span data-stu-id="a73d6-175">**Return Value**</span></span>

<span data-ttu-id="a73d6-176">一个`Double`，或`null`所有输入的值是否为`null`值。</span><span class="sxs-lookup"><span data-stu-id="a73d6-176">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="a73d6-177">**示例**</span><span class="sxs-lookup"><span data-stu-id="a73d6-177">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)] 

<span data-ttu-id="a73d6-178">Microsoft SQL 客户端托管提供程序中提供了等效功能。</span><span class="sxs-lookup"><span data-stu-id="a73d6-178">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="a73d6-179">有关详细信息，请参阅[用于实体框架函数的 SqlClient](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="a73d6-179">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="a73d6-180">基于集合的聚合</span><span class="sxs-lookup"><span data-stu-id="a73d6-180">Collection-based aggregates</span></span>

<span data-ttu-id="a73d6-181">基于集合的聚合（集合函数）针对集合而运行并返回值。</span><span class="sxs-lookup"><span data-stu-id="a73d6-181">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="a73d6-182">例如如果 ORDERS 是所有订单的集合，则可以计算最早的发货日期，用以下表达式：</span><span class="sxs-lookup"><span data-stu-id="a73d6-182">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="a73d6-183">将在当前环境名称解析范围内计算基于集合的聚合内的表达式。</span><span class="sxs-lookup"><span data-stu-id="a73d6-183">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="a73d6-184">基于组的聚合</span><span class="sxs-lookup"><span data-stu-id="a73d6-184">Group-based aggregates</span></span>

<span data-ttu-id="a73d6-185">基于组的聚合将按照 GROUP BY 子句定义的方式对组进行计算。</span><span class="sxs-lookup"><span data-stu-id="a73d6-185">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="a73d6-186">对于结果中的每个组，将使用每个组中的元素作为聚合计算的输入来计算单独的聚合。</span><span class="sxs-lookup"><span data-stu-id="a73d6-186">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="a73d6-187">当在 select 表达式中使用 group-by 子句时，在投影或 order-by 子句中只存在分组表达式名称、聚合或常量表达式。</span><span class="sxs-lookup"><span data-stu-id="a73d6-187">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="a73d6-188">以下示例计算每种产品的平均订购数量：</span><span class="sxs-lookup"><span data-stu-id="a73d6-188">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol 
  group by ol.Product as p
```

<span data-ttu-id="a73d6-189">它是可以在 SELECT 表达式中包含的基于组的聚合没有显式 group-by 子句。</span><span class="sxs-lookup"><span data-stu-id="a73d6-189">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="a73d6-190">在这种情况下，所有元素被都视为单个组。</span><span class="sxs-lookup"><span data-stu-id="a73d6-190">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="a73d6-191">这是等效的指定基于常数的分组。</span><span class="sxs-lookup"><span data-stu-id="a73d6-191">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="a73d6-192">例如，请看下面的表达式：</span><span class="sxs-lookup"><span data-stu-id="a73d6-192">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="a73d6-193">此表达式等效于以下表达式：</span><span class="sxs-lookup"><span data-stu-id="a73d6-193">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="a73d6-194">将在 WHERE 子句表达式可见的名称解析范围内计算基于组的聚合中的表达式。</span><span class="sxs-lookup"><span data-stu-id="a73d6-194">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="a73d6-195">如[!INCLUDE[tsql](../../../../../../includes/tsql-md.md)]，基于组的聚合也可以指定 ALL 或 DISTINCT 修饰符。</span><span class="sxs-lookup"><span data-stu-id="a73d6-195">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="a73d6-196">如果指定 DISTINCT 修饰符，则将从聚合输入集合中消除重复项，然后计算聚合。</span><span class="sxs-lookup"><span data-stu-id="a73d6-196">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="a73d6-197">如果指定 ALL 修饰符（或者未指定修饰符），则不执行重复项消除。</span><span class="sxs-lookup"><span data-stu-id="a73d6-197">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>  

## <a name="see-also"></a><span data-ttu-id="a73d6-198">请参阅</span><span class="sxs-lookup"><span data-stu-id="a73d6-198">See also</span></span>

- [<span data-ttu-id="a73d6-199">规范函数</span><span class="sxs-lookup"><span data-stu-id="a73d6-199">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
