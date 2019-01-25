---
title: 查询表达式语法示例：分区
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e41aed0-3be9-4f75-98de-860a85552a3c
ms.openlocfilehash: 24063d71326c432fcf16ba6924ed6d0963814d88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651144"
---
# <a name="query-expression-syntax-examples-partitioning"></a><span data-ttu-id="e9875-102">查询表达式语法示例：分区</span><span class="sxs-lookup"><span data-stu-id="e9875-102">Query Expression Syntax Examples: Partitioning</span></span>
<span data-ttu-id="e9875-103">本主题中的示例演示如何使用<xref:System.Linq.Enumerable.Skip%2A>并<xref:System.Linq.Enumerable.Take%2A>方法来查询[AdventureWorks 销售模型](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)使用查询表达式语法。</span><span class="sxs-lookup"><span data-stu-id="e9875-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using query expression syntax.</span></span> <span data-ttu-id="e9875-104">这些示例中使用的 AdventureWorks 销售模型从 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 等表生成。</span><span class="sxs-lookup"><span data-stu-id="e9875-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="e9875-105">本主题中的示例使用以下`using` / `Imports`语句：</span><span class="sxs-lookup"><span data-stu-id="e9875-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="skip"></a><span data-ttu-id="e9875-106">Skip</span><span class="sxs-lookup"><span data-stu-id="e9875-106">Skip</span></span>  
  
### <a name="example"></a><span data-ttu-id="e9875-107">示例</span><span class="sxs-lookup"><span data-stu-id="e9875-107">Example</span></span>  
 <span data-ttu-id="e9875-108">以下示例使用 <xref:System.Linq.Enumerable.Skip%2A> 方法以获取 Seattle 的前两个地址之外的所有地址。</span><span class="sxs-lookup"><span data-stu-id="e9875-108">The following example uses the <xref:System.Linq.Enumerable.Skip%2A> method to get all but the first two addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#SkipNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#skipnested)]
 [!code-vb[DP L2E Examples#SkipNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#skipnested)]  
  
## <a name="take"></a><span data-ttu-id="e9875-109">Take</span><span class="sxs-lookup"><span data-stu-id="e9875-109">Take</span></span>  
  
### <a name="example"></a><span data-ttu-id="e9875-110">示例</span><span class="sxs-lookup"><span data-stu-id="e9875-110">Example</span></span>  
 <span data-ttu-id="e9875-111">以下示例使用 <xref:System.Linq.Enumerable.Take%2A> 方法以获取 Seattle 的前三个地址。</span><span class="sxs-lookup"><span data-stu-id="e9875-111">The following example uses the <xref:System.Linq.Enumerable.Take%2A> method to get the first three addresses in Seattle.</span></span>  
  
 [!code-csharp[DP L2E Examples#TakeNested](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#takenested)]
 [!code-vb[DP L2E Examples#TakeNested](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#takenested)]  
  
## <a name="see-also"></a><span data-ttu-id="e9875-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="e9875-112">See also</span></span>
- [<span data-ttu-id="e9875-113">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="e9875-113">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
