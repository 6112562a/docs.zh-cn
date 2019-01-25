---
title: 如何：查找子元素 (XPATH-LINQ to XML) 的列表 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2868abfd-9f7b-412a-9cb5-f643f0fed146
ms.openlocfilehash: 4ff9e5f1dc1d1b6c9ac1674434bcb2bc4c57ffde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625092"
---
# <a name="how-to-find-a-list-of-child-elements-xpath-linq-to-xml-visual-basic"></a><span data-ttu-id="12e67-102">如何：查找子元素 (XPATH-LINQ to XML) 的列表 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12e67-102">How to: Find a List of Child Elements (XPath-LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="12e67-103">本主题将 XPath 子元素轴与 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> 轴进行比较。</span><span class="sxs-lookup"><span data-stu-id="12e67-103">This topic compares the XPath child elements axis to the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axis.</span></span>  
  
 <span data-ttu-id="12e67-104">XPath 表达式为：`./*`</span><span class="sxs-lookup"><span data-stu-id="12e67-104">The XPath expression is: `./*`</span></span>  
  
## <a name="example"></a><span data-ttu-id="12e67-105">示例</span><span class="sxs-lookup"><span data-stu-id="12e67-105">Example</span></span>  
 <span data-ttu-id="12e67-106">本示例查找 `Address` 元素的所有子元素。</span><span class="sxs-lookup"><span data-stu-id="12e67-106">This example finds all of the child elements of the `Address` element.</span></span>  
  
 <span data-ttu-id="12e67-107">本示例使用下面的 XML 文档：[示例 XML 文件：多个采购订单 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="12e67-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
```vb  
Dim cpo As XDocument = XDocument.Load("PurchaseOrders.xml")  
Dim po As XElement = cpo.Root.<PurchaseOrder>.<Address>.FirstOrDefault  
  
' LINQ to XML query  
Dim list1 As IEnumerable(Of XElement) = po.Elements()  
  
' XPath expression  
Dim list2 As IEnumerable(Of XElement) = po.XPathSelectElements("./*")  
  
If (list1.Count() = list2.Count()) AndAlso _  
    (list1.Intersect(list2).Count() = list1.Count()) Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
For Each el As XElement In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="12e67-108">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="12e67-108">This example produces the following output:</span></span>  
  
```  
Results are identical  
<Name>Ellen Adams</Name>  
<Street>123 Maple Street</Street>  
<City>Mill Valley</City>  
<State>CA</State>  
<Zip>10999</Zip>  
<Country>USA</Country>  
```  
  
## <a name="see-also"></a><span data-ttu-id="12e67-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="12e67-109">See also</span></span>
- [<span data-ttu-id="12e67-110">LINQ to XML 针对 XPath 用户 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12e67-110">LINQ to XML for XPath Users (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
