---
title: 如何：使用分组创建层次结构 (C#)
ms.date: 07/20/2015
ms.assetid: 0213d59e-5f76-438c-9cab-4bf11f7b971d
ms.openlocfilehash: bd2e8ab9fb0ed1fee68cb51d2d032b202b14ba88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560849"
---
# <a name="how-to-create-hierarchy-using-grouping-c"></a><span data-ttu-id="666d7-102">如何：使用分组创建层次结构 (C#)</span><span class="sxs-lookup"><span data-stu-id="666d7-102">How to: Create Hierarchy Using Grouping (C#)</span></span>
<span data-ttu-id="666d7-103">本示例演示如何将数据分组，再基于分组生成 XML。</span><span class="sxs-lookup"><span data-stu-id="666d7-103">This example shows how to group data, and then generate XML based on the grouping.</span></span>  
  
## <a name="example"></a><span data-ttu-id="666d7-104">示例</span><span class="sxs-lookup"><span data-stu-id="666d7-104">Example</span></span>  
 <span data-ttu-id="666d7-105">本示例首先按类别对数据分组，再生成新的 XML 文件，其中的 XML 层次结构反映了分组。</span><span class="sxs-lookup"><span data-stu-id="666d7-105">This example first groups data by a category, then generates a new XML file in which the XML hierarchy reflects the grouping.</span></span>  
  
 <span data-ttu-id="666d7-106">本示例使用下面的 XML 文档：[示例 XML 文件：数值数据 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="666d7-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement doc = XElement.Load("Data.xml");  
var newData =  
    new XElement("Root",  
        from data in doc.Elements("Data")  
        group data by (string)data.Element("Category") into groupedData  
        select new XElement("Group",  
            new XAttribute("ID", groupedData.Key),  
            from g in groupedData  
            select new XElement("Data",  
                g.Element("Quantity"),  
                g.Element("Price")  
            )  
        )  
    );  
Console.WriteLine(newData);  
```  
  
 <span data-ttu-id="666d7-107">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="666d7-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Group ID="A">  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>24.50</Price>  
    </Data>  
    <Data>  
      <Quantity>5</Quantity>  
      <Price>4.95</Price>  
    </Data>  
    <Data>  
      <Quantity>3</Quantity>  
      <Price>66.00</Price>  
    </Data>  
    <Data>  
      <Quantity>15</Quantity>  
      <Price>29.00</Price>  
    </Data>  
  </Group>  
  <Group ID="B">  
    <Data>  
      <Quantity>1</Quantity>  
      <Price>89.99</Price>  
    </Data>  
    <Data>  
      <Quantity>10</Quantity>  
      <Price>.99</Price>  
    </Data>  
    <Data>  
      <Quantity>8</Quantity>  
      <Price>6.99</Price>  
    </Data>  
  </Group>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="666d7-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="666d7-108">See also</span></span>

- [<span data-ttu-id="666d7-109">高级查询技术 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="666d7-109">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
