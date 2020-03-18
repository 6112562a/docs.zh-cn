---
title: 如何查找父级的属性 (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: dbef9d89-a5c4-431f-80cc-7a2ebf323f86
ms.openlocfilehash: bfe7554a5c767adde5e7170c8e1ea0537155f6df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141174"
---
# <a name="how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml-c"></a>如何查找父级的属性 (XPath-LINQ to XML) (C#)

本主题演示如何定位到父元素并查找其属性。

XPath 表达式为：

`../@id`

## <a name="example"></a>示例

此示例首先查找 `Author` 元素。 然后，查找父元素的 `id` 属性。

本示例使用以下 XML 文档：[示例 XML 文件：图书 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)。

```csharp
XDocument books = XDocument.Load("Books.xml");

XElement author =
    books
    .Root
    .Element("Book")
    .Element("Author");

// LINQ to XML query
XAttribute att1 =
    author
    .Parent
    .Attribute("id");

// XPath expression
XAttribute att2 = ((IEnumerable)author.XPathEvaluate("../@id")).Cast<XAttribute>().First();

if (att1 == att2)
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
Console.WriteLine(att1);
```

该示例产生下面的输出：

```output
Results are identical
id="bk101"
```
