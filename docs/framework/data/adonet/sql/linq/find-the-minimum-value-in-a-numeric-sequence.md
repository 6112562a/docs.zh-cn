---
title: 查找数值序列中的最小值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 78203093-f242-4572-9b31-9495b10926aa
ms.openlocfilehash: d8aee43f13ec92f649b4df20505ac56c336fe07a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793832"
---
# <a name="find-the-minimum-value-in-a-numeric-sequence"></a><span data-ttu-id="23f40-102">查找数值序列中的最小值</span><span class="sxs-lookup"><span data-stu-id="23f40-102">Find the Minimum Value in a Numeric Sequence</span></span>
<span data-ttu-id="23f40-103">使用 <xref:System.Linq.Enumerable.Min%2A> 运算符可返回数值序列中的最小值。</span><span class="sxs-lookup"><span data-stu-id="23f40-103">Use the <xref:System.Linq.Enumerable.Min%2A> operator to return the minimum value from a sequence of numeric values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23f40-104">示例</span><span class="sxs-lookup"><span data-stu-id="23f40-104">Example</span></span>  
 <span data-ttu-id="23f40-105">下面的示例查找所有产品的最低单价。</span><span class="sxs-lookup"><span data-stu-id="23f40-105">The following example finds the lowest unit price of any product.</span></span>  
  
 <span data-ttu-id="23f40-106">如果您对 Northwind 示例数据库运行此查询，则输出为：`2.5000`。</span><span class="sxs-lookup"><span data-stu-id="23f40-106">If you run this query against the Northwind sample database, the output is: `2.5000`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#9)]
 [!code-vb[DLinqQueryExamples#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="23f40-107">示例</span><span class="sxs-lookup"><span data-stu-id="23f40-107">Example</span></span>  
 <span data-ttu-id="23f40-108">下面的示例查找所有订单的最低运费额。</span><span class="sxs-lookup"><span data-stu-id="23f40-108">The following example finds the lowest freight amount for any order.</span></span>  
  
 <span data-ttu-id="23f40-109">如果您对 Northwind 示例数据库运行此查询，则输出为：`0.0200`。</span><span class="sxs-lookup"><span data-stu-id="23f40-109">If you run this query against the Northwind sample database, the output is: `0.0200`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#10)]
 [!code-vb[DLinqQueryExamples#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="23f40-110">示例</span><span class="sxs-lookup"><span data-stu-id="23f40-110">Example</span></span>  
 <span data-ttu-id="23f40-111">下面的示例使用 Min 查找每个类别中单价最低的 `Products`。</span><span class="sxs-lookup"><span data-stu-id="23f40-111">The following example uses Min to find the `Products` that have the lowest unit price in each category.</span></span> <span data-ttu-id="23f40-112">输出按类别排列。</span><span class="sxs-lookup"><span data-stu-id="23f40-112">The output is arranged by category.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#11](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#11)]
 [!code-vb[DLinqQueryExamples#11](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#11)]  
  
 <span data-ttu-id="23f40-113">如果您对 Northwind 示例数据库运行上一个查询，所得到的结果将与如下内容类似：</span><span class="sxs-lookup"><span data-stu-id="23f40-113">If you run the previous query against the Northwind sample database, your results will resemble the following:</span></span>  
  
 `1`  
  
 `Guaraná Fantástica`  
  
 `2`  
  
 `Aniseed Syrup`  
  
 `3`  
  
 `Teatime Chocolate Biscuits`  
  
 `4`  
  
 `Geitost`  
  
 `5`  
  
 `Filo Mix`  
  
 `6`  
  
 `Tourtière`  
  
 `7`  
  
 `Longlife Tofu`  
  
 `8`  
  
 `Konbu`  
  
## <a name="see-also"></a><span data-ttu-id="23f40-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="23f40-114">See also</span></span>

- [<span data-ttu-id="23f40-115">聚合查询</span><span class="sxs-lookup"><span data-stu-id="23f40-115">Aggregate Queries</span></span>](aggregate-queries.md)
- [<span data-ttu-id="23f40-116">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="23f40-116">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
