---
title: EXCEPT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 69cc23e5-3f8f-4b49-b20e-2f84ff11c80d
ms.openlocfilehash: 32c8c418056231e98696eb8f4e9cb372d6c5740c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089453"
---
# <a name="except-entity-sql"></a><span data-ttu-id="ee22b-102">EXCEPT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ee22b-102">EXCEPT (Entity SQL)</span></span>
<span data-ttu-id="ee22b-103">返回由 EXCEPT 操作数左侧的查询表达式返回而不由 EXCEPT 操作数右侧的查询表达式返回的任何非重复值的集合。</span><span class="sxs-lookup"><span data-stu-id="ee22b-103">Returns a collection of any distinct values from the query expression to the left of the EXCEPT operand that are not also returned from the query expression to the right of the EXCEPT operand.</span></span> <span data-ttu-id="ee22b-104">所有表达式都必须与 `expression`一样属于同一类型或属于公共基类型或派生类型。</span><span class="sxs-lookup"><span data-stu-id="ee22b-104">All expressions must be of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee22b-105">语法</span><span class="sxs-lookup"><span data-stu-id="ee22b-105">Syntax</span></span>  
  
```  
expression EXCEPT expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="ee22b-106">自变量</span><span class="sxs-lookup"><span data-stu-id="ee22b-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="ee22b-107">返回一个集合以与从其他查询表达式返回的集合进行比较的任何有效查询表达式。</span><span class="sxs-lookup"><span data-stu-id="ee22b-107">Any valid query expression that returns a collection to compare with the collection returned from another query expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee22b-108">返回值</span><span class="sxs-lookup"><span data-stu-id="ee22b-108">Return Value</span></span>  
 <span data-ttu-id="ee22b-109">与 `expression`具有相同类型或属于公共基类型或派生类型的一个集合。</span><span class="sxs-lookup"><span data-stu-id="ee22b-109">A collection of the same type or of a common base or derived type as `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee22b-110">备注</span><span class="sxs-lookup"><span data-stu-id="ee22b-110">Remarks</span></span>  
 <span data-ttu-id="ee22b-111">EXCEPT 是 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集运算符之一。</span><span class="sxs-lookup"><span data-stu-id="ee22b-111">EXCEPT is one of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span> <span data-ttu-id="ee22b-112">所有 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集运算符都是从左到右进行求值。</span><span class="sxs-lookup"><span data-stu-id="ee22b-112">All [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators are evaluated from left to right.</span></span> <span data-ttu-id="ee22b-113">下表显示 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 集运算符的优先级。</span><span class="sxs-lookup"><span data-stu-id="ee22b-113">The following table shows the precedence of the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] set operators.</span></span>  
  
|<span data-ttu-id="ee22b-114">优先级</span><span class="sxs-lookup"><span data-stu-id="ee22b-114">Precedence</span></span>|<span data-ttu-id="ee22b-115">运算符</span><span class="sxs-lookup"><span data-stu-id="ee22b-115">Operators</span></span>|  
|----------------|---------------|  
|<span data-ttu-id="ee22b-116">最高</span><span class="sxs-lookup"><span data-stu-id="ee22b-116">Highest</span></span>|<span data-ttu-id="ee22b-117">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="ee22b-117">INTERSECT</span></span>|  
||<span data-ttu-id="ee22b-118">UNION</span><span class="sxs-lookup"><span data-stu-id="ee22b-118">UNION</span></span><br /><br /> <span data-ttu-id="ee22b-119">UNION ALL</span><span class="sxs-lookup"><span data-stu-id="ee22b-119">UNION ALL</span></span>|  
||<span data-ttu-id="ee22b-120">EXCEPT</span><span class="sxs-lookup"><span data-stu-id="ee22b-120">EXCEPT</span></span>|  
|<span data-ttu-id="ee22b-121">最低</span><span class="sxs-lookup"><span data-stu-id="ee22b-121">Lowest</span></span>|<span data-ttu-id="ee22b-122">EXISTS</span><span class="sxs-lookup"><span data-stu-id="ee22b-122">EXISTS</span></span><br /><br /> <span data-ttu-id="ee22b-123">OVERLAPS</span><span class="sxs-lookup"><span data-stu-id="ee22b-123">OVERLAPS</span></span><br /><br /> <span data-ttu-id="ee22b-124">FLATTEN</span><span class="sxs-lookup"><span data-stu-id="ee22b-124">FLATTEN</span></span><br /><br /> <span data-ttu-id="ee22b-125">SET</span><span class="sxs-lookup"><span data-stu-id="ee22b-125">SET</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ee22b-126">示例</span><span class="sxs-lookup"><span data-stu-id="ee22b-126">Example</span></span>  
 <span data-ttu-id="ee22b-127">以下 Entity SQL 查询使用 EXCEPT 运算符以返回从两个查询表达式返回的任何非重复值的集合。</span><span class="sxs-lookup"><span data-stu-id="ee22b-127">The following Entity SQL query uses the EXCEPT operator to return a collection of any distinct values from two query expressions.</span></span> <span data-ttu-id="ee22b-128">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="ee22b-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ee22b-129">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="ee22b-129">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="ee22b-130">按照中的过程[如何：执行返回 StructuralType 结果的查询](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="ee22b-130">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="ee22b-131">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="ee22b-131">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#EXCEPT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#except)]  
  
## <a name="see-also"></a><span data-ttu-id="ee22b-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="ee22b-132">See also</span></span>

- [<span data-ttu-id="ee22b-133">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="ee22b-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
