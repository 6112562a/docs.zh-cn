---
title: 如何：在 PLINQ 中指定合并选项
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use merge options
ms.assetid: 0f33b527-e91a-4550-a39a-e63e396fd831
ms.openlocfilehash: e98ede3664a8815c60a490239a789c69fa557895
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588561"
---
# <a name="how-to-specify-merge-options-in-plinq"></a>如何：在 PLINQ 中指定合并选项
此示例展示了如何指定应用于 PLINQ 查询中所有后续运算符的合并选项。 虽然无需显式设置合并选项，但这样做可以提升性能。 若要详细了解合并选项，请参阅 [PLINQ 中的合并选项](../../../docs/standard/parallel-programming/merge-options-in-plinq.md)。  
  
> [!WARNING]
> 本示例旨在演示用法，运行速度可能不如等效的顺序 LINQ to Objects 查询快。 若要详细了解加速，请参阅[了解 PLINQ 中的加速](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)。  
  
## <a name="example"></a>示例  
 下面的示例展示了合并选项在基本方案中的行为，此方案包含无序源，并将高成本函数应用于每个元素。  
  
 [!code-csharp[PLINQ#23](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#23)]
 [!code-vb[PLINQ#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#23)]  
  
 如果 <xref:System.Linq.ParallelMergeOptions.AutoBuffered> 选项在第一个元素生成前导致不利延迟发生，请尝试使用 <xref:System.Linq.ParallelMergeOptions.NotBuffered> 选项，更快更顺畅地生成结果元素。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Linq.ParallelMergeOptions>
- [并行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
