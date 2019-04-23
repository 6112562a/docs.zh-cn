---
title: < = （小于或等于） (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: 7a65984da22d125bdbdd5cfadb5a2051fa3dafdc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304761"
---
# <a name="-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="92304-102">\<=（小于或等于）(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="92304-102">\<= (Less Than or Equal To) (Entity SQL)</span></span>
<span data-ttu-id="92304-103">比较两个表达式以确定左侧表达式的值是否小于或等于右侧表达式的值。</span><span class="sxs-lookup"><span data-stu-id="92304-103">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92304-104">语法</span><span class="sxs-lookup"><span data-stu-id="92304-104">Syntax</span></span>  
  
```  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="92304-105">自变量</span><span class="sxs-lookup"><span data-stu-id="92304-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="92304-106">任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="92304-106">Any valid expression.</span></span> <span data-ttu-id="92304-107">两个表达式都必须具有可隐式转换的数据类型。</span><span class="sxs-lookup"><span data-stu-id="92304-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="92304-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="92304-108">Result Types</span></span>  
 <span data-ttu-id="92304-109">如果左侧表达式的值小于或等于右侧表达式的值，则为`true` ；否则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="92304-109">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92304-110">示例</span><span class="sxs-lookup"><span data-stu-id="92304-110">Example</span></span>  
 <span data-ttu-id="92304-111">下面的 Entity SQL 查询使用 <= 比较运算符比较两个表达式，以确定左侧表达式的值是否小于或等于右侧表达式的值。</span><span class="sxs-lookup"><span data-stu-id="92304-111">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="92304-112">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="92304-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="92304-113">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="92304-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="92304-114">按照中的过程[如何：执行返回 StructuralType 结果的查询](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)。</span><span class="sxs-lookup"><span data-stu-id="92304-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="92304-115">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="92304-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LESS_OR_EQUALS](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="92304-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="92304-116">See also</span></span>

- [<span data-ttu-id="92304-117">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="92304-117">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
