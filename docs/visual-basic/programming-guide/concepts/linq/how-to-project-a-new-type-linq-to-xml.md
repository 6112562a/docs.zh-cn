---
title: 如何：投影新类型（LINQ to XML）（Visual Basic）
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: 64b563c57406caae7869905c417db9e6439e6157
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318374"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a><span data-ttu-id="4c19c-102">如何：投影新类型（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4c19c-102">How to: Project a New Type (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="4c19c-103">本节中的其他示例已演示了一些查询，这些查询以 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>、<xref:System.Collections.Generic.IEnumerable%601> 的 `string` 和 <xref:System.Collections.Generic.IEnumerable%601> 的 `int` 的形式返回结果。</span><span class="sxs-lookup"><span data-stu-id="4c19c-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="4c19c-104">这些是常见结果类型，但它们不是对所有情况都适用。</span><span class="sxs-lookup"><span data-stu-id="4c19c-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="4c19c-105">在很多情况下，会希望查询返回其他类型的 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="4c19c-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c19c-106">示例</span><span class="sxs-lookup"><span data-stu-id="4c19c-106">Example</span></span>  
 <span data-ttu-id="4c19c-107">此示例演示如何在 `Select` 子句中实例化对象。</span><span class="sxs-lookup"><span data-stu-id="4c19c-107">This example shows how to instantiate objects in the `Select` clause.</span></span> <span data-ttu-id="4c19c-108">代码首先定义一个具有一个构造函数的新类，然后修改 `Select` 语句，使该表达式成为新类的新实例。</span><span class="sxs-lookup"><span data-stu-id="4c19c-108">The code first defines a new class with a constructor, and then modifies the `Select` statement so that the expression is a new instance of the new class.</span></span>  
  
 <span data-ttu-id="4c19c-109">本示例使用以下 XML 文档：[示例 XML 文件：典型采购订单 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="4c19c-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
```vb  
Public Class NameQty  
    Public name As String  
    Public qty As Integer  
    Public Sub New(ByVal n As String, ByVal q As Integer)  
        name = n  
        qty = q  
    End Sub  
End Class  
  
Public Class Program  
    Shared Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
  
        Dim nqList As IEnumerable(Of NameQty) = _  
            From n In po...<Item> _  
            Select New NameQty( _  
                n.<ProductName>.Value, CInt(n.<Quantity>.Value))  
  
        For Each n As NameQty In nqList  
            Console.WriteLine(n.name & ":" & n.qty)  
        Next  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="4c19c-110">此示例使用在主题 how [to：检索单个子元素（LINQ to XML）（Visual Basic）](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)中引入的 `M:System.Xml.Linq.XElement.Element` 方法。</span><span class="sxs-lookup"><span data-stu-id="4c19c-110">This example uses the `M:System.Xml.Linq.XElement.Element` method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="4c19c-111">还使用强制转换来检索 `M:System.Xml.Linq.XElement.Element` 方法返回的元素值。</span><span class="sxs-lookup"><span data-stu-id="4c19c-111">It also uses casts to retrieve the values of the elements that are returned by the `M:System.Xml.Linq.XElement.Element` method.</span></span>  
  
 <span data-ttu-id="4c19c-112">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="4c19c-112">This example produces the following output:</span></span>  
  
```console  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a><span data-ttu-id="4c19c-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="4c19c-113">See also</span></span>

- [<span data-ttu-id="4c19c-114">投影和转换（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="4c19c-114">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
