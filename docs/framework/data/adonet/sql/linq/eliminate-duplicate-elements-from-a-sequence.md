---
title: 从序列中消除重复的元素
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: 49138e9b130b1a2137b5e9e779875d6107972578
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032586"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a>从序列中消除重复的元素
使用 <xref:System.Linq.Queryable.Distinct%2A> 运算符可从序列中消除重复元素。  
  
## <a name="example"></a>示例  
 下面的示例使用 <xref:System.Linq.Queryable.Distinct%2A> 来选择有客户的唯一城市序列。  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a>请参阅

- [查询示例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
