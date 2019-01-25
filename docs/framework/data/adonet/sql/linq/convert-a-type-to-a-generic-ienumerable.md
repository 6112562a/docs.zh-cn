---
title: 将某一类型转换为泛型 IEnumerable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 64774fb5-7447-4296-ad3b-8a94346f99a1
ms.openlocfilehash: d1f4c1c4a561c893b5846e6ae0b08b2d78c3589d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509579"
---
# <a name="convert-a-type-to-a-generic-ienumerable"></a><span data-ttu-id="a5f81-102">将某一类型转换为泛型 IEnumerable</span><span class="sxs-lookup"><span data-stu-id="a5f81-102">Convert a Type to a Generic IEnumerable</span></span>
<span data-ttu-id="a5f81-103">使用 <xref:System.Linq.Enumerable.AsEnumerable%2A> 可返回类型化为泛型 `IEnumerable` 的自变量。</span><span class="sxs-lookup"><span data-stu-id="a5f81-103">Use <xref:System.Linq.Enumerable.AsEnumerable%2A> to return the argument typed as a generic `IEnumerable`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5f81-104">示例</span><span class="sxs-lookup"><span data-stu-id="a5f81-104">Example</span></span>  
 <span data-ttu-id="a5f81-105">在此示例中，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]（使用默认泛型 `Query`）会尝试将查询转换为 SQL 并在服务器上执行。</span><span class="sxs-lookup"><span data-stu-id="a5f81-105">In this example, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (using the default generic `Query`) would try to convert the query to SQL and execute it on the server.</span></span> <span data-ttu-id="a5f81-106">但 `where` 子句引用用户定义的客户端方法 (`isValidProduct`)，此方法无法转换为 SQL。</span><span class="sxs-lookup"><span data-stu-id="a5f81-106">But the `where` clause references a user-defined client-side method (`isValidProduct`), which cannot be converted to SQL.</span></span>  
  
 <span data-ttu-id="a5f81-107">解决方法是指定 <xref:System.Collections.Generic.IEnumerable%601> 的客户端泛型 `where` 实现以替换泛型 <xref:System.Linq.IQueryable%601>。</span><span class="sxs-lookup"><span data-stu-id="a5f81-107">The solution is to specify the client-side generic <xref:System.Collections.Generic.IEnumerable%601> implementation of `where` to replace the generic <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="a5f81-108">可通过调用 <xref:System.Linq.Enumerable.AsEnumerable%2A> 运算符来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="a5f81-108">You do this by invoking the <xref:System.Linq.Enumerable.AsEnumerable%2A> operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#46](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#46)]
 [!code-vb[DLinqQueryExamples#46](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="a5f81-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="a5f81-109">See also</span></span>
- [<span data-ttu-id="a5f81-110">查询示例</span><span class="sxs-lookup"><span data-stu-id="a5f81-110">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
