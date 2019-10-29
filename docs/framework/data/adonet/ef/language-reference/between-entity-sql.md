---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 611e90f362bbc0eac521e1e1998fb85200169c19
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039938"
---
# <a name="between-entity-sql"></a><span data-ttu-id="1a692-102">BETWEEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1a692-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="1a692-103">确定表达式的结果值是否在指定范围内。</span><span class="sxs-lookup"><span data-stu-id="1a692-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="1a692-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN 表达式的功能与 Transact-SQL BETWEEN 表达式相同。</span><span class="sxs-lookup"><span data-stu-id="1a692-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a692-105">语法</span><span class="sxs-lookup"><span data-stu-id="1a692-105">Syntax</span></span>  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="1a692-106">自变量</span><span class="sxs-lookup"><span data-stu-id="1a692-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="1a692-107">要测试是否在 `begin_expression` 和 `end_expression` 所定义的范围内的任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="1a692-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="1a692-108">`expression` 必须与 `begin_expression` 和 `end_expression` 的类型都相同。</span><span class="sxs-lookup"><span data-stu-id="1a692-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="1a692-109">任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="1a692-109">Any valid expression.</span></span> <span data-ttu-id="1a692-110">`begin_expression` 必须与 `expression` 和 `end_expression` 的类型都相同。</span><span class="sxs-lookup"><span data-stu-id="1a692-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="1a692-111">`begin_expression` 应小于 `end_expression`，否则返回值将取反。</span><span class="sxs-lookup"><span data-stu-id="1a692-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="1a692-112">任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="1a692-112">Any valid expression.</span></span> <span data-ttu-id="1a692-113">`end_expression` 必须与 `expression` 和 `begin_expression` 的类型都相同。</span><span class="sxs-lookup"><span data-stu-id="1a692-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="1a692-114">NOT</span><span class="sxs-lookup"><span data-stu-id="1a692-114">NOT</span></span>  
 <span data-ttu-id="1a692-115">指定对 BETWEEN 的结果取反。</span><span class="sxs-lookup"><span data-stu-id="1a692-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="1a692-116">AND</span><span class="sxs-lookup"><span data-stu-id="1a692-116">AND</span></span>  
 <span data-ttu-id="1a692-117">用作一个占位符，指示 `expression` 应该处于由 `begin_expression` 和 `end_expression` 指定的范围内。</span><span class="sxs-lookup"><span data-stu-id="1a692-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a692-118">返回值</span><span class="sxs-lookup"><span data-stu-id="1a692-118">Return Value</span></span>  
 <span data-ttu-id="1a692-119">如果 `true` 处于由 `expression` 和 `begin_expression` 指定的范围内，则为 `end_expression`；否则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="1a692-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="1a692-120">如果 `null` 为 `expression`，或者 `null` 或 `begin_expression` 为 `end_expression`，则返回 `null`。</span><span class="sxs-lookup"><span data-stu-id="1a692-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a692-121">备注</span><span class="sxs-lookup"><span data-stu-id="1a692-121">Remarks</span></span>  
 <span data-ttu-id="1a692-122">若要指定排他范围，请使用大于（>）和小于（<）运算符而不是 BETWEEN。</span><span class="sxs-lookup"><span data-stu-id="1a692-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a692-123">示例</span><span class="sxs-lookup"><span data-stu-id="1a692-123">Example</span></span>  
 <span data-ttu-id="1a692-124">下面的 Entity SQL 查询使用 BETWEEN 运算符确定一个表达式的结果值是否在指定范围内。</span><span class="sxs-lookup"><span data-stu-id="1a692-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="1a692-125">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="1a692-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="1a692-126">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="1a692-126">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="1a692-127">执行 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)中的过程。</span><span class="sxs-lookup"><span data-stu-id="1a692-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="1a692-128">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="1a692-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="1a692-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="1a692-129">See also</span></span>

- [<span data-ttu-id="1a692-130">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="1a692-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
