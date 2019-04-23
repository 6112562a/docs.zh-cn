---
title: 基于方法的查询语法示例：筛选
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e40e314c-eb30-4f44-a054-41e511e35832
ms.openlocfilehash: 1064e4f8d4fce16d0505eb79b5e862be7c2e4ce6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111359"
---
# <a name="method-based-query-syntax-examples-filtering"></a><span data-ttu-id="6635e-102">基于方法的查询语法示例：筛选</span><span class="sxs-lookup"><span data-stu-id="6635e-102">Method-Based Query Syntax Examples: Filtering</span></span>
<span data-ttu-id="6635e-103">本主题中的示例演示如何使用`Where`并`Where…Contains`方法来查询[AdventureWorks 销售模型](https://archive.codeplex.com/?p=msftdbprodsamples)使用基于方法的查询语法。</span><span class="sxs-lookup"><span data-stu-id="6635e-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using method-based query syntax.</span></span> <span data-ttu-id="6635e-104">请注意，其中...`Contains`</span><span class="sxs-lookup"><span data-stu-id="6635e-104">Note, Where…`Contains`</span></span> <span data-ttu-id="6635e-105">不能使用作为的一部分[编译查询](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)。</span><span class="sxs-lookup"><span data-stu-id="6635e-105">cannot be used as a part of a [compiled query](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="6635e-106">这些示例中使用的 AdventureWorks 销售模型从 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 等表生成。</span><span class="sxs-lookup"><span data-stu-id="6635e-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6635e-107">本主题中的示例使用以下`using` / `Imports`语句：</span><span class="sxs-lookup"><span data-stu-id="6635e-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="6635e-108">Where</span><span class="sxs-lookup"><span data-stu-id="6635e-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="6635e-109">示例</span><span class="sxs-lookup"><span data-stu-id="6635e-109">Example</span></span>  
 <span data-ttu-id="6635e-110">以下示例返回所有联机订单。</span><span class="sxs-lookup"><span data-stu-id="6635e-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1_mq)]
 [!code-vb[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1_mq)]  
  
### <a name="example"></a><span data-ttu-id="6635e-111">示例</span><span class="sxs-lookup"><span data-stu-id="6635e-111">Example</span></span>  
 <span data-ttu-id="6635e-112">以下示例返回订单数量大于 2 且小于 6 的订单。</span><span class="sxs-lookup"><span data-stu-id="6635e-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2_mq)]
 [!code-vb[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2_mq)]  
  
### <a name="example"></a><span data-ttu-id="6635e-113">示例</span><span class="sxs-lookup"><span data-stu-id="6635e-113">Example</span></span>  
 <span data-ttu-id="6635e-114">以下示例返回所有红色产品。</span><span class="sxs-lookup"><span data-stu-id="6635e-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3_mq)]
 [!code-vb[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3_mq)]  
  
### <a name="example"></a><span data-ttu-id="6635e-115">示例</span><span class="sxs-lookup"><span data-stu-id="6635e-115">Example</span></span>  
 <span data-ttu-id="6635e-116">以下示例使用 `Where` 方法以查找在 2003 年 12 月 1 日之后生成的订单，然后使用 `order.SalesOrderDetail` 导航属性以获取每个订单的详细信息。</span><span class="sxs-lookup"><span data-stu-id="6635e-116">The following example uses the `Where` method to find orders that were made after December 1, 2003 and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty_mq)]
 [!code-vb[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty_mq)]  
  
## <a name="wherecontains"></a><span data-ttu-id="6635e-117">Where…Contains</span><span class="sxs-lookup"><span data-stu-id="6635e-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="6635e-118">示例</span><span class="sxs-lookup"><span data-stu-id="6635e-118">Example</span></span>  
 <span data-ttu-id="6635e-119">以下示例将一个数组用作 `Where…Contains` 子句的一部分，以查找 `ProductModelID` 与数组中的值匹配的所有产品。</span><span class="sxs-lookup"><span data-stu-id="6635e-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#3)]
 [!code-vb[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#3)]  
  
> [!NOTE]
>  <span data-ttu-id="6635e-120">作为 `Where…Contains` 子句中谓词的一部分，您可以使用 <xref:System.Array>、<xref:System.Collections.Generic.List%601> 或实现 <xref:System.Collections.Generic.IEnumerable%601> 接口的任何类型的集合。</span><span class="sxs-lookup"><span data-stu-id="6635e-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="6635e-121">还可以在 LINQ to Entities 查询中声明和初始化集合。</span><span class="sxs-lookup"><span data-stu-id="6635e-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="6635e-122">有关更多信息，请参见下一个示例。</span><span class="sxs-lookup"><span data-stu-id="6635e-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="6635e-123">示例</span><span class="sxs-lookup"><span data-stu-id="6635e-123">Example</span></span>  
 <span data-ttu-id="6635e-124">以下示例声明并初始化 `Where…Contains` 子句中的数组，以查找 `ProductModelID` 或 `Size` 与数组中的值匹配的所有产品。</span><span class="sxs-lookup"><span data-stu-id="6635e-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or a `Size` that matches a value in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#4)]
 [!code-vb[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6635e-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="6635e-125">See also</span></span>

- [<span data-ttu-id="6635e-126">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="6635e-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
