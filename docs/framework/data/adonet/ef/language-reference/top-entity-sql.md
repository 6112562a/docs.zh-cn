---
title: TOP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: e7c6cf6b67dc3af29f7ca8fb22af419235a9b833
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351640"
---
# <a name="top-entity-sql"></a><span data-ttu-id="ace4e-102">TOP (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ace4e-102">TOP (Entity SQL)</span></span>

<span data-ttu-id="ace4e-103">SELECT 子句可以在可选的 ALL/DISTINCT 修饰符之后具有可选的 TOP 子子句。</span><span class="sxs-lookup"><span data-stu-id="ace4e-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="ace4e-104">TOP 子子句指定查询结果中将只返回第一组行。</span><span class="sxs-lookup"><span data-stu-id="ace4e-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>

## <a name="syntax"></a><span data-ttu-id="ace4e-105">语法</span><span class="sxs-lookup"><span data-stu-id="ace4e-105">Syntax</span></span>

```
[ TOP (n) ]
```

## <a name="arguments"></a><span data-ttu-id="ace4e-106">自变量</span><span class="sxs-lookup"><span data-stu-id="ace4e-106">Arguments</span></span>

<span data-ttu-id="ace4e-107">`n` 指定要返回的行数的数值表达式。</span><span class="sxs-lookup"><span data-stu-id="ace4e-107">`n` The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="ace4e-108">`n` 可以是单个数值或单个参数。</span><span class="sxs-lookup"><span data-stu-id="ace4e-108">`n` could be a single numeric literal or a single parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="ace4e-109">备注</span><span class="sxs-lookup"><span data-stu-id="ace4e-109">Remarks</span></span>

<span data-ttu-id="ace4e-110">TOP 表达式必须是单个数值或单个参数。</span><span class="sxs-lookup"><span data-stu-id="ace4e-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="ace4e-111">如果使用一个常量文本，则该文本类型必须可隐式提升为 Edm.Int64（字节、int16、int32 或 int64，或映射到可提升为 Edm.Int64 的类型的任何提供程序类型），并且其值必须大于或等于零。</span><span class="sxs-lookup"><span data-stu-id="ace4e-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="ace4e-112">否则，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="ace4e-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="ace4e-113">如果将一个参数用作表达式，则该参数类型也必须可隐式提升为 Edm.Int64，但由于参数值是后期绑定的，因此在编译过程中不会对实际参数值进行任何验证。</span><span class="sxs-lookup"><span data-stu-id="ace4e-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>

<span data-ttu-id="ace4e-114">下面是常量 TOP 表达式的示例：</span><span class="sxs-lookup"><span data-stu-id="ace4e-114">The following is an example of constant TOP expression:</span></span>

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

<span data-ttu-id="ace4e-115">以下是参数化 TOP 表达式的示例：</span><span class="sxs-lookup"><span data-stu-id="ace4e-115">The following is an example of parameterized TOP expression:</span></span>

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

<span data-ttu-id="ace4e-116">除非对查询进行排序，否则 TOP 具有不确定性。</span><span class="sxs-lookup"><span data-stu-id="ace4e-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="ace4e-117">如果需要确定的结果，请在 [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) 子句中使用 [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) 和 [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) 子子句。</span><span class="sxs-lookup"><span data-stu-id="ace4e-117">If you require a deterministic result, use the [SKIP](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md) and [LIMIT](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md) sub-clauses in the [ORDER BY](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="ace4e-118">TOP 和 SKIP/LIMIT 是互斥的。</span><span class="sxs-lookup"><span data-stu-id="ace4e-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>

## <a name="example"></a><span data-ttu-id="ace4e-119">示例</span><span class="sxs-lookup"><span data-stu-id="ace4e-119">Example</span></span>

<span data-ttu-id="ace4e-120">以下 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查询使用 TOP 指定要从查询结果中返回的最上面一行。</span><span class="sxs-lookup"><span data-stu-id="ace4e-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="ace4e-121">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="ace4e-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ace4e-122">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="ace4e-122">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="ace4e-123">按照中的过程[如何：执行返回 StructuralType 结果的查询](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="ace4e-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="ace4e-124">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="ace4e-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

    [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]

## <a name="see-also"></a><span data-ttu-id="ace4e-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="ace4e-125">See also</span></span>

- [<span data-ttu-id="ace4e-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="ace4e-126">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [<span data-ttu-id="ace4e-127">SKIP</span><span class="sxs-lookup"><span data-stu-id="ace4e-127">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [<span data-ttu-id="ace4e-128">LIMIT</span><span class="sxs-lookup"><span data-stu-id="ace4e-128">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [<span data-ttu-id="ace4e-129">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="ace4e-129">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)
- [<span data-ttu-id="ace4e-130">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="ace4e-130">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
