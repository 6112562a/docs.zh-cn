---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 57f7c61d8e4de2a63708ef6d4437ca53de854af9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116857"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="4cd3b-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4cd3b-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="4cd3b-103">取消引用一个引用值，并生成该取消引用的结果。</span><span class="sxs-lookup"><span data-stu-id="4cd3b-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cd3b-104">语法</span><span class="sxs-lookup"><span data-stu-id="4cd3b-104">Syntax</span></span>  
  
```  
SELECT DEREF ( o.expression ) from Table as o;  
```  
  
## <a name="arguments"></a><span data-ttu-id="4cd3b-105">自变量</span><span class="sxs-lookup"><span data-stu-id="4cd3b-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4cd3b-106">任何返回集合的有效查询表达式。</span><span class="sxs-lookup"><span data-stu-id="4cd3b-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cd3b-107">返回值</span><span class="sxs-lookup"><span data-stu-id="4cd3b-107">Return Value</span></span>  
 <span data-ttu-id="4cd3b-108">引用的实体的值。</span><span class="sxs-lookup"><span data-stu-id="4cd3b-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cd3b-109">备注</span><span class="sxs-lookup"><span data-stu-id="4cd3b-109">Remarks</span></span>  
 <span data-ttu-id="4cd3b-110">DEREF 运算符取消引用一个引用值，并生成该取消引用的结果。</span><span class="sxs-lookup"><span data-stu-id="4cd3b-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="4cd3b-111">例如，如果`r`为 ref 类型引用\<T >，`Deref(r)`类型的表达式`T`生成的引用的实体`r`。</span><span class="sxs-lookup"><span data-stu-id="4cd3b-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="4cd3b-112">如果引用值为 Null，或无关联（即，引用的目标不存在），则 DEREF 运算符的结果为 Null。</span><span class="sxs-lookup"><span data-stu-id="4cd3b-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cd3b-113">示例</span><span class="sxs-lookup"><span data-stu-id="4cd3b-113">Example</span></span>  
 <span data-ttu-id="4cd3b-114">下面的 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查询使用 DEREF 运算符取消引用一个引用值，并生成该取消引用的结果。</span><span class="sxs-lookup"><span data-stu-id="4cd3b-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="4cd3b-115">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="4cd3b-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4cd3b-116">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="4cd3b-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4cd3b-117">按照中的过程[如何：执行返回 PrimitiveType 结果的查询](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="4cd3b-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="4cd3b-118">将以下查询作为参数传递给 ExecutePrimitiveTypeQuery 方法：</span><span class="sxs-lookup"><span data-stu-id="4cd3b-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#DEREF](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="4cd3b-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="4cd3b-119">See also</span></span>

- [<span data-ttu-id="4cd3b-120">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="4cd3b-120">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="4cd3b-121">REF</span><span class="sxs-lookup"><span data-stu-id="4cd3b-121">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)
- [<span data-ttu-id="4cd3b-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="4cd3b-122">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)
- [<span data-ttu-id="4cd3b-123">KEY</span><span class="sxs-lookup"><span data-stu-id="4cd3b-123">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)
- [<span data-ttu-id="4cd3b-124">可以为 NULL 的结构化类型</span><span class="sxs-lookup"><span data-stu-id="4cd3b-124">Nullable Structured Types</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/nullable-structured-types-entity-sql.md)
