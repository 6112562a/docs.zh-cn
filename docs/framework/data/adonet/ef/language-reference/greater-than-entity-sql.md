---
title: '> （大于）（实体 SQL）'
ms.date: 03/30/2017
ms.assetid: 4cea865c-677c-4b06-99a1-010f2ae2394a
ms.openlocfilehash: 0b57f36681575ccbe3239220e89804c804f13f39
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250888"
---
# <a name="-greater-than-entity-sql"></a><span data-ttu-id="82c68-102">> （大于）（实体 SQL）</span><span class="sxs-lookup"><span data-stu-id="82c68-102">> (Greater Than) (Entity SQL)</span></span>
<span data-ttu-id="82c68-103">比较两个表达式以确定左侧表达式的值是否大于右侧表达式的值。</span><span class="sxs-lookup"><span data-stu-id="82c68-103">Compares two expressions to determine whether the left expression has a value greater than the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82c68-104">语法</span><span class="sxs-lookup"><span data-stu-id="82c68-104">Syntax</span></span>  
  
```  
expression > expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="82c68-105">自变量</span><span class="sxs-lookup"><span data-stu-id="82c68-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="82c68-106">任何有效表达式。</span><span class="sxs-lookup"><span data-stu-id="82c68-106">Any valid expression.</span></span> <span data-ttu-id="82c68-107">两个表达式都必须具有可隐式转换的数据类型。</span><span class="sxs-lookup"><span data-stu-id="82c68-107">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="82c68-108">结果类型</span><span class="sxs-lookup"><span data-stu-id="82c68-108">Result Types</span></span>  
 <span data-ttu-id="82c68-109">如果左侧表达式的值大于右侧表达式的值，则为`true` ；否则为 `false`。</span><span class="sxs-lookup"><span data-stu-id="82c68-109">`true` if the left expression has a value greater than the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82c68-110">示例</span><span class="sxs-lookup"><span data-stu-id="82c68-110">Example</span></span>  
 <span data-ttu-id="82c68-111">下面的 Entity SQL 查询使用 > 比较运算符比较两个表达式，以确定左侧表达式的值是否大于右侧表达式的值。</span><span class="sxs-lookup"><span data-stu-id="82c68-111">The following Entity SQL query uses > comparison operator to compare two expressions to determine whether the left expression has a value greater than the right expression.</span></span> <span data-ttu-id="82c68-112">此查询基于 AdventureWorks 销售模型。</span><span class="sxs-lookup"><span data-stu-id="82c68-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="82c68-113">若要编译并运行此查询，请执行下列步骤：</span><span class="sxs-lookup"><span data-stu-id="82c68-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="82c68-114">[按照如何：执行返回 StructuralType 结果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查询。</span><span class="sxs-lookup"><span data-stu-id="82c68-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="82c68-115">将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="82c68-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#GREATER](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#greater)]  
  
## <a name="see-also"></a><span data-ttu-id="82c68-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="82c68-116">See also</span></span>

- [<span data-ttu-id="82c68-117">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="82c68-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
