---
title: 从数值序列中返回平均值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ee3b8673-a2e7-4b2d-9b5c-4972ff9e665d
ms.openlocfilehash: 8d6f5f76787c1110e91b245a3dd2425450b4db7e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781396"
---
# <a name="return-the-average-value-from-a-numeric-sequence"></a><span data-ttu-id="49612-102">从数值序列中返回平均值</span><span class="sxs-lookup"><span data-stu-id="49612-102">Return the Average Value From a Numeric Sequence</span></span>
<span data-ttu-id="49612-103"><xref:System.Linq.Enumerable.Average%2A> 运算符用于计算数值序列的平均值。</span><span class="sxs-lookup"><span data-stu-id="49612-103">The <xref:System.Linq.Enumerable.Average%2A> operator computes the average of a sequence of numeric values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49612-104">使用经 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 转换后的 `Average` 计算整数值时，所得结果的数据类型为 integer，而非 double。</span><span class="sxs-lookup"><span data-stu-id="49612-104">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translation of `Average` of integer values is computed as an integer, not as a double.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49612-105">示例</span><span class="sxs-lookup"><span data-stu-id="49612-105">Example</span></span>  
 <span data-ttu-id="49612-106">下面的示例返回 `Freight` 表中 `Orders` 值的平均值。</span><span class="sxs-lookup"><span data-stu-id="49612-106">The following example returns the average of `Freight` values in the `Orders` table.</span></span>  
  
 <span data-ttu-id="49612-107">从 Northwind 示例数据库中得到的结果将为 `78.2442`。</span><span class="sxs-lookup"><span data-stu-id="49612-107">Results from the sample Northwind database would be `78.2442`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#1)]
 [!code-vb[DLinqQueryExamples#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="49612-108">示例</span><span class="sxs-lookup"><span data-stu-id="49612-108">Example</span></span>  
 <span data-ttu-id="49612-109">下面的示例返回 `Products` 表中所有 `Products` 的平均单价。</span><span class="sxs-lookup"><span data-stu-id="49612-109">The following example returns the average of the unit price of all `Products` in the `Products` table.</span></span>  
  
 <span data-ttu-id="49612-110">从 Northwind 示例数据库中得到的结果将为 `28.8663`。</span><span class="sxs-lookup"><span data-stu-id="49612-110">Results from the sample Northwind database would be `28.8663`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#2)]
 [!code-vb[DLinqQueryExamples#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="49612-111">示例</span><span class="sxs-lookup"><span data-stu-id="49612-111">Example</span></span>  
 <span data-ttu-id="49612-112">下面的示例使用 `Average` 运算符查找其单价高于其所属类别的平均单价的那些 `Products`。</span><span class="sxs-lookup"><span data-stu-id="49612-112">The following example uses the `Average` operator to find those `Products` whose unit price is higher than the average unit price of the category it belongs to.</span></span> <span data-ttu-id="49612-113">此示例随后会按组显示结果。</span><span class="sxs-lookup"><span data-stu-id="49612-113">The example then displays the results in groups.</span></span>  
  
 <span data-ttu-id="49612-114">请注意，此示例需要使用 C# 中的 `var` 关键字，这是因为返回类型为匿名类型。</span><span class="sxs-lookup"><span data-stu-id="49612-114">Note that this example requires the use of the `var` keyword in C#, because the return type is anonymous.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#3)]
 [!code-vb[DLinqQueryExamples#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#3)]  
  
 <span data-ttu-id="49612-115">如果您对 Northwind 示例数据库运行此查询，所得到的结果应与如下内容类似：</span><span class="sxs-lookup"><span data-stu-id="49612-115">If you run this query against the Northwind sample database, the results should resemble of the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `Ipoh Coffee`  
  
 `2`  
  
 `Grandma's Boysenberry Spread`  
  
 `Northwoods Cranberry Sauce`  
  
 `Sirop d'érable`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `Gumbär Gummibärchen`  
  
 `Schoggi Schokolade`  
  
 `Tarte au sucre`  
  
 `4`  
  
 `Queso Manchego La Pastora`  
  
 `Mascarpone Fabioli`  
  
 `Raclette Courdavault`  
  
 `Camembert Pierrot`  
  
 `Gudbrandsdalsost`  
  
 `Mozzarella di Giovanni`  
  
 `5`  
  
 `Gustaf's Knäckebröd`  
  
 `Gnocchi di nonna Alice`  
  
 `Wimmers gute Semmelknödel`  
  
 `6`  
  
 `Mishi Kobe Niku`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Rössle Sauerkraut`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Ikura`  
  
 `Carnarvon Tigers`  
  
 `Nord-Ost Matjeshering`  
  
 `Gravad lax`  
  
## <a name="see-also"></a><span data-ttu-id="49612-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="49612-116">See also</span></span>

- [<span data-ttu-id="49612-117">聚合查询</span><span class="sxs-lookup"><span data-stu-id="49612-117">Aggregate Queries</span></span>](aggregate-queries.md)
