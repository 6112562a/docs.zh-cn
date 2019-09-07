---
title: 查询表达式语法示例：分组
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d83d7c0-b3be-4c92-a630-25cd1285de31
ms.openlocfilehash: c9876c72a03f7827ec4b28d78f06ed372460caff
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398456"
---
# <a name="query-expression-syntax-examples-grouping"></a><span data-ttu-id="58d1a-102">查询表达式语法示例：分组</span><span class="sxs-lookup"><span data-stu-id="58d1a-102">Query Expression Syntax Examples: Grouping</span></span>
<span data-ttu-id="58d1a-103">本主题中的示例演示如何使用`GroupBy`方法通过使用查询表达式语法来查询[AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)。</span><span class="sxs-lookup"><span data-stu-id="58d1a-103">The examples in this topic demonstrate how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="58d1a-104">这些示例中使用的 AdventureWorks 销售模型从 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 等表生成。</span><span class="sxs-lookup"><span data-stu-id="58d1a-104">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="58d1a-105">本主题中的示例使用以下`using` / `Imports`语句：</span><span class="sxs-lookup"><span data-stu-id="58d1a-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="58d1a-106">示例</span><span class="sxs-lookup"><span data-stu-id="58d1a-106">Example</span></span>  
 <span data-ttu-id="58d1a-107">以下示例返回按邮政编码分组的 `Address` 对象。</span><span class="sxs-lookup"><span data-stu-id="58d1a-107">The following example returns `Address` objects grouped by postal code.</span></span> <span data-ttu-id="58d1a-108">这些结果将投影到一个匿名类型。</span><span class="sxs-lookup"><span data-stu-id="58d1a-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3)]
 [!code-vb[DP L2E Examples#GroupBySimple3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3)]  
  
## <a name="example"></a><span data-ttu-id="58d1a-109">示例</span><span class="sxs-lookup"><span data-stu-id="58d1a-109">Example</span></span>  
 <span data-ttu-id="58d1a-110">以下示例返回按联系人姓氏的第一个字母分组的 `Contact` 对象。</span><span class="sxs-lookup"><span data-stu-id="58d1a-110">The following example returns `Contact` objects grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="58d1a-111">这些结果还可以按姓氏的第一个字母进行排序，并投影到一个匿名类型。</span><span class="sxs-lookup"><span data-stu-id="58d1a-111">The results are also sorted by the first letter of last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2)]
 [!code-vb[DP L2E Examples#GroupBySimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2)]  
  
## <a name="example"></a><span data-ttu-id="58d1a-112">示例</span><span class="sxs-lookup"><span data-stu-id="58d1a-112">Example</span></span>  
 <span data-ttu-id="58d1a-113">下面的示例返回按客户 ID 分组的 `SalesOrderHeader` 对象。</span><span class="sxs-lookup"><span data-stu-id="58d1a-113">The following example returns `SalesOrderHeader` objects grouped by customer ID.</span></span> <span data-ttu-id="58d1a-114">同时还返回每个客户的销售数量。</span><span class="sxs-lookup"><span data-stu-id="58d1a-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount)]
 [!code-vb[DP L2E Examples#GroupByCount](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount)]  
  
## <a name="see-also"></a><span data-ttu-id="58d1a-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="58d1a-115">See also</span></span>

- [<span data-ttu-id="58d1a-116">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="58d1a-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
