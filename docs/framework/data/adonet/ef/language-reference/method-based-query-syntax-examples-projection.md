---
title: 基于方法的查询语法示例：投影
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 505491fa-5920-43ce-8a96-c25389e125d8
ms.openlocfilehash: c1cad442ba2e6d2567c2e4936d7d8b3cd49b0424
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152409"
---
# <a name="method-based-query-syntax-examples-projection"></a><span data-ttu-id="020ba-102">基于方法的查询语法示例：投影</span><span class="sxs-lookup"><span data-stu-id="020ba-102">Method-Based Query Syntax Examples: Projection</span></span>
<span data-ttu-id="020ba-103">本主题中的示例演示如何使用<xref:System.Linq.Enumerable.Select%2A>并<xref:System.Linq.Enumerable.SelectMany%2A>方法来查询[AdventureWorks 销售模型](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)使用基于方法的查询语法。</span><span class="sxs-lookup"><span data-stu-id="020ba-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) using method-based query syntax.</span></span> <span data-ttu-id="020ba-104">这些示例中使用的 AdventureWorks 销售模型从 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 等表生成。</span><span class="sxs-lookup"><span data-stu-id="020ba-104">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="020ba-105">本主题中的示例使用以下`using` / `Imports`语句：</span><span class="sxs-lookup"><span data-stu-id="020ba-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="020ba-106">选择</span><span class="sxs-lookup"><span data-stu-id="020ba-106">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="020ba-107">示例</span><span class="sxs-lookup"><span data-stu-id="020ba-107">Example</span></span>  
 <span data-ttu-id="020ba-108">以下示例使用 <xref:System.Linq.Queryable.Select%2A> 方法以将 `Product.Name` 和 `Product.ProductID` 属性投影到一系列匿名类型。</span><span class="sxs-lookup"><span data-stu-id="020ba-108">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
### <a name="example"></a><span data-ttu-id="020ba-109">示例</span><span class="sxs-lookup"><span data-stu-id="020ba-109">Example</span></span>  
 <span data-ttu-id="020ba-110">以下示例使用 <xref:System.Linq.Enumerable.Select%2A> 方法以只返回一系列产品名称。</span><span class="sxs-lookup"><span data-stu-id="020ba-110">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2_mq)]
 [!code-vb[DP L2E Examples#SelectSimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="020ba-111">SelectMany</span><span class="sxs-lookup"><span data-stu-id="020ba-111">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="020ba-112">示例</span><span class="sxs-lookup"><span data-stu-id="020ba-112">Example</span></span>  
 <span data-ttu-id="020ba-113">以下示例使用 <xref:System.Linq.Enumerable.SelectMany%2A> 方法以选择 `TotalDue` 低于 500.00 的所有订单。</span><span class="sxs-lookup"><span data-stu-id="020ba-113">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="020ba-114">示例</span><span class="sxs-lookup"><span data-stu-id="020ba-114">Example</span></span>  
 <span data-ttu-id="020ba-115">以下示例使用 <xref:System.Linq.Enumerable.SelectMany%2A> 方法以选择在 2002 年 10 月 1 或此日期之后发出的所有订单。</span><span class="sxs-lookup"><span data-stu-id="020ba-115">The following example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="020ba-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="020ba-116">See Also</span></span>  
 [<span data-ttu-id="020ba-117">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="020ba-117">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
