---
title: LINQ to XML 中的延迟执行和延迟计算
ms.date: 07/20/2015
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
ms.openlocfilehash: 8e94b9133a2d2dd287fba91600c94460a5204b2c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346410"
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)
实现查询和轴操作通常是为了使用延迟执行。 本主题解释延迟执行的要求和优点，以及某些实现注意事项。  
  
## <a name="deferred-execution"></a>延迟执行  
 延迟执行意味着表达式的计算延迟，直到真正需要其实现值为止。 当必须操作大型数据集合，特别是在包含一系列链接的查询或操作的程序中操作时，延迟执行可以大大改善性能。 在最佳情况下，延迟执行只允许对源集合的单个循环访问。  
  
 LINQ 技术广泛应用了延迟执行，包括在核心 <xref:System.Linq?displayProperty=nameWithType> 类的成员和不同 LINQ 命名空间中的扩展方法（如 <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>）中使用。  
  
## <a name="eager-vs-lazy-evaluation"></a>积极与迟缓计算  
 当您编写实现延迟执行的方法时，还必须确定是使用迟缓计算还是积极计算来实现该方法。  
  
- 在迟缓计算中，每次调用迭代器时都会处理源集合的一个元素。 这是实现迭代器的典型方式。  
  
- 在积极计算中，第一次调用迭代器时就会对整个集合进行处理。 还可能需要源集合的临时副本。 例如，<xref:System.Linq.Enumerable.OrderBy%2A> 方法必须在返回第一个元素前对整个集合进行排序。  
  
 迟缓计算通常产生更好的性能，因为它将系统开销处理平均分配到整个集合的计算中，并将临时数据的使用降至最低。 当然，对于某些操作，除了具体化中间结果之外，再没有其他选择。  
  
## <a name="next-steps"></a>后续步骤  
 本教程的下一个主题将解释延迟执行：  
  
- [Deferred Execution Example (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>请参阅

- [Tutorial: Deferred Execution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)
- [Concepts and Terminology (Functional Transformation) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)
- [Aggregation Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
