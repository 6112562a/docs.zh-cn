---
title: 如何：计算中间值 (C#)
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 6fb04e1222563e557172edad7953c4646adafefd
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710177"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="e30bb-102">如何：计算中间值 (C#)</span><span class="sxs-lookup"><span data-stu-id="e30bb-102">How to: Calculate Intermediate Values (C#)</span></span>
<span data-ttu-id="e30bb-103">本示例演示如何计算可用于进行排序、筛选和选择的中间值。</span><span class="sxs-lookup"><span data-stu-id="e30bb-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e30bb-104">示例</span><span class="sxs-lookup"><span data-stu-id="e30bb-104">Example</span></span>  
 <span data-ttu-id="e30bb-105">下面的示例使用 `Let` 子句。</span><span class="sxs-lookup"><span data-stu-id="e30bb-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="e30bb-106">此示例使用下面的 XML 文档：[示例 XML 文件：数值数据 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="e30bb-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> extensions =  
    from el in root.Elements("Data")  
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="e30bb-107">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="e30bb-107">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="e30bb-108">示例</span><span class="sxs-lookup"><span data-stu-id="e30bb-108">Example</span></span>  
 <span data-ttu-id="e30bb-109">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="e30bb-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="e30bb-110">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="e30bb-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="e30bb-111">此示例使用下面的 XML 文档：[示例 XML 文件：命名空间中的数值数据](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="e30bb-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<decimal> extensions =  
    from el in root.Elements(ad + "Data")  
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="e30bb-112">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="e30bb-112">This code produces the following output:</span></span>  
  
```  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
