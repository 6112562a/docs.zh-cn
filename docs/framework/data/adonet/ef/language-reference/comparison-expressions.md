---
title: 比较表达式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: d0926bb1a0e35caa058f268f0a0c414e805a8674
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251174"
---
# <a name="comparison-expressions"></a><span data-ttu-id="a2b13-102">比较表达式</span><span class="sxs-lookup"><span data-stu-id="a2b13-102">Comparison Expressions</span></span>
<span data-ttu-id="a2b13-103">比较表达式检查常量值、属性值或方法结果是否等于、不等于、大于或小于另一个值。</span><span class="sxs-lookup"><span data-stu-id="a2b13-103">A comparison expression checks whether a constant value, property value, or method result is equal, not equal, greater than, or less than another value.</span></span> <span data-ttu-id="a2b13-104">如果特定比较对于 LINQ to Entities 无效，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="a2b13-104">If a particular comparison is not valid for LINQ to Entities, an exception will be thrown.</span></span> <span data-ttu-id="a2b13-105">所有比较（无论隐式和显式）都要求所有组件在数据源中是可比较的。</span><span class="sxs-lookup"><span data-stu-id="a2b13-105">All comparisons, both implicit and explicit, require that all components are comparable in the data source.</span></span> <span data-ttu-id="a2b13-106">比较表达式通常在 `Where` 子句中用于限制查询结果。</span><span class="sxs-lookup"><span data-stu-id="a2b13-106">Comparison expressions are frequently used in `Where` clauses for restricting the query results.</span></span>  
  
 <span data-ttu-id="a2b13-107">以下查询表达式语法示例演示一个查询，该查询返回销售订单编号等于“SO43663”的结果：</span><span class="sxs-lookup"><span data-stu-id="a2b13-107">The following example in query expression syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 <span data-ttu-id="a2b13-108">以下基于方法的查询语法示例演示一个查询，该查询返回销售订单编号等于“SO43663”的结果：</span><span class="sxs-lookup"><span data-stu-id="a2b13-108">The following example in method-based query syntax shows a query that returns results where the sales order number is equal to "SO43663":</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 <span data-ttu-id="a2b13-109">以下查询表达式语法示例演示一个查询，该查询返回发货日期等于“July 8, 2001”的销售订单信息：</span><span class="sxs-lookup"><span data-stu-id="a2b13-109">The following example in query expression syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 <span data-ttu-id="a2b13-110">以下基于方法的查询语法示例演示一个查询，该查询返回发货日期等于“July 8, 2001”的销售订单信息：</span><span class="sxs-lookup"><span data-stu-id="a2b13-110">The following example in method-based query syntax shows a query that returns sales order information where the ship date is equal to July 8, 2001:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 <span data-ttu-id="a2b13-111">生成常量的表达式在服务器上进行转换，不会尝试执行本地计算。</span><span class="sxs-lookup"><span data-stu-id="a2b13-111">Expressions that yield a constant are converted at the server, and no attempt to do local evaluation is performed.</span></span> <span data-ttu-id="a2b13-112">下面的示例在 `Where` 子句中使用生成常量的表达式。</span><span class="sxs-lookup"><span data-stu-id="a2b13-112">The following example uses an expression in the `Where` clause that yields a constant.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 <span data-ttu-id="a2b13-113">LINQ to Entities 不支持将用户类用作常量。</span><span class="sxs-lookup"><span data-stu-id="a2b13-113">LINQ to Entities does not support using a user class as a constant.</span></span> <span data-ttu-id="a2b13-114">但是，用户类上的属性引用被视为常量，将转换为命令目录树常量表达式并在数据源上执行。</span><span class="sxs-lookup"><span data-stu-id="a2b13-114">However, a property reference on a user class is considered a constant, and will be converted to a command tree constant expression and executed on the data source.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 <span data-ttu-id="a2b13-115">不支持返回常量表达式的方法。</span><span class="sxs-lookup"><span data-stu-id="a2b13-115">Methods that return a constant expression are not supported.</span></span> <span data-ttu-id="a2b13-116">下面的示例在 `Where` 子句中使用一个返回常量的方法。</span><span class="sxs-lookup"><span data-stu-id="a2b13-116">The following example contains a method in the `Where` clause that returns a constant.</span></span> <span data-ttu-id="a2b13-117">此示例将在运行时引发异常。</span><span class="sxs-lookup"><span data-stu-id="a2b13-117">This example will throw an exception at run time.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a><span data-ttu-id="a2b13-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="a2b13-118">See also</span></span>

- [<span data-ttu-id="a2b13-119">LINQ to Entities 查询中的表达式</span><span class="sxs-lookup"><span data-stu-id="a2b13-119">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
