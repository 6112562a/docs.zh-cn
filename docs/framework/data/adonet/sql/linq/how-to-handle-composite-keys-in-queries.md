---
title: 如何：处理查询中的复合键
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 0ee0bda8c3ee46cb6e08ee415def68a4a9832617
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523476"
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="75fc4-102">如何：处理查询中的复合键</span><span class="sxs-lookup"><span data-stu-id="75fc4-102">How to: Handle Composite Keys in Queries</span></span>
<span data-ttu-id="75fc4-103">有些运算符只能带一个自变量。</span><span class="sxs-lookup"><span data-stu-id="75fc4-103">Some operators can take only one argument.</span></span> <span data-ttu-id="75fc4-104">如果你的自变量必须包含数据库中的多个列，则你必须创建一个匿名类型来表示这种组合。</span><span class="sxs-lookup"><span data-stu-id="75fc4-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75fc4-105">示例</span><span class="sxs-lookup"><span data-stu-id="75fc4-105">Example</span></span>  
 <span data-ttu-id="75fc4-106">下面的示例显示了调用 `GroupBy` 运算符的查询，此运算符只能带一个 `key` 自变量。</span><span class="sxs-lookup"><span data-stu-id="75fc4-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="75fc4-107">示例</span><span class="sxs-lookup"><span data-stu-id="75fc4-107">Example</span></span>  
 <span data-ttu-id="75fc4-108">联接也属于这种情况，如下例中所示：</span><span class="sxs-lookup"><span data-stu-id="75fc4-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="75fc4-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="75fc4-109">See also</span></span>
- [<span data-ttu-id="75fc4-110">查询概念</span><span class="sxs-lookup"><span data-stu-id="75fc4-110">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
