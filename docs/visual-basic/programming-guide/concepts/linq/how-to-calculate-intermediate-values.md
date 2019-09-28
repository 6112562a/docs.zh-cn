---
title: 如何：计算中间值（Visual Basic）
ms.date: 07/20/2015
ms.assetid: 933a97b2-dfe7-4f4d-94ad-e6e20df84abd
ms.openlocfilehash: 63067c42da37d71ad0fc5488c68d296ac7589aec
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352904"
---
# <a name="how-to-calculate-intermediate-values-visual-basic"></a><span data-ttu-id="ae23e-102">如何：计算中间值（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="ae23e-102">How to: Calculate Intermediate Values (Visual Basic)</span></span>
<span data-ttu-id="ae23e-103">本示例演示如何计算可用于进行排序、筛选和选择的中间值。</span><span class="sxs-lookup"><span data-stu-id="ae23e-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae23e-104">示例</span><span class="sxs-lookup"><span data-stu-id="ae23e-104">Example</span></span>  
 <span data-ttu-id="ae23e-105">下面的示例使用 `Let` 子句。</span><span class="sxs-lookup"><span data-stu-id="ae23e-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="ae23e-106">本示例使用下面的 XML 文档：[示例 XML 文件：数值数据 (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="ae23e-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim extensions As IEnumerable(Of Decimal) = _  
    From el In root.<Data> _  
    Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
    Where extension > 25 _  
    Order By extension _  
    Select extension  
For Each ex As Decimal In extensions  
    Console.WriteLine(ex)  
Next  
```  
  
 <span data-ttu-id="ae23e-107">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="ae23e-107">This code produces the following output:</span></span>  
  
```console  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="ae23e-108">示例</span><span class="sxs-lookup"><span data-stu-id="ae23e-108">Example</span></span>  
 <span data-ttu-id="ae23e-109">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="ae23e-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="ae23e-110">有关详细信息，请参阅[命名空间概述（LINQ to XML）（Visual Basic）](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="ae23e-110">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="ae23e-111">本示例使用下面的 XML 文档：[示例 XML 文件：命名空间中的数值数据](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="ae23e-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```vb  
Imports <xmlns="http://www.adatum.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = XElement.Load("DataInNamespace.xml")  
        Dim extensions As IEnumerable(Of Decimal) = _  
            From el In root.<Data> _  
            Let extension = CDec(el.<Quantity>.Value) * CDec(el.<Price>.Value) _  
            Where extension > 25 _  
            Order By extension _  
            Select extension  
        For Each ex As Decimal In extensions  
            Console.WriteLine(ex)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="ae23e-112">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="ae23e-112">This code produces the following output:</span></span>  
  
```console  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae23e-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="ae23e-113">See also</span></span>

- [<span data-ttu-id="ae23e-114">基本查询（LINQ to XML）（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="ae23e-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
