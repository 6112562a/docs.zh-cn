---
title: 如何：查找命名空间中的元素 (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: cae1c4ac-6cd5-46cf-9b1c-bd85bc9b7ea9
ms.openlocfilehash: d85426cf7a7073c35b51157e59687e2b3bcdcf8a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253683"
---
# <a name="how-to-find-elements-in-a-namespace-xpath-linq-to-xml-c"></a><span data-ttu-id="a7b76-102">如何：查找命名空间中的元素 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a7b76-102">How to: Find Elements in a Namespace (XPath-LINQ to XML) (C#)</span></span>

<span data-ttu-id="a7b76-103">XPath 表达式可以在特定命名空间中查找节点。</span><span class="sxs-lookup"><span data-stu-id="a7b76-103">XPath expressions can find nodes in a particular namespace.</span></span> <span data-ttu-id="a7b76-104">XPath 表达式使用命名空间前缀来指定命名空间。</span><span class="sxs-lookup"><span data-stu-id="a7b76-104">XPath expressions use namespace prefixes for specifying namespaces.</span></span> <span data-ttu-id="a7b76-105">若要分析包含命名空间前缀的 XPath 表达式，必须向实现 <xref:System.Xml.IXmlNamespaceResolver> 的 XPath 方法传递一个对象。</span><span class="sxs-lookup"><span data-stu-id="a7b76-105">To parse an XPath expression that contains namespace prefixes, you must pass an object to the XPath methods that implements <xref:System.Xml.IXmlNamespaceResolver>.</span></span> <span data-ttu-id="a7b76-106">本示例使用 <xref:System.Xml.XmlNamespaceManager>。</span><span class="sxs-lookup"><span data-stu-id="a7b76-106">This example uses <xref:System.Xml.XmlNamespaceManager>.</span></span>

<span data-ttu-id="a7b76-107">XPath 表达式为：</span><span class="sxs-lookup"><span data-stu-id="a7b76-107">The XPath expression is:</span></span>

`./aw:*`

## <a name="example"></a><span data-ttu-id="a7b76-108">示例</span><span class="sxs-lookup"><span data-stu-id="a7b76-108">Example</span></span>

<span data-ttu-id="a7b76-109">下面的示例读取包含两个命名空间的 XML 树。</span><span class="sxs-lookup"><span data-stu-id="a7b76-109">The following example reads an XML tree that contains two namespaces.</span></span> <span data-ttu-id="a7b76-110">它使用 <xref:System.Xml.XmlReader> 来读取 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="a7b76-110">It uses an <xref:System.Xml.XmlReader> to read the XML document.</span></span> <span data-ttu-id="a7b76-111">然后获取 <xref:System.Xml.XmlNameTable> 中的 <xref:System.Xml.XmlReader> 和 <xref:System.Xml.XmlNamespaceManager> 中的 <xref:System.Xml.XmlNameTable>。</span><span class="sxs-lookup"><span data-stu-id="a7b76-111">It then gets an <xref:System.Xml.XmlNameTable> from the <xref:System.Xml.XmlReader>, and an <xref:System.Xml.XmlNamespaceManager> from the <xref:System.Xml.XmlNameTable>.</span></span> <span data-ttu-id="a7b76-112">示例在选择元素时使用 <xref:System.Xml.XmlNamespaceManager>。</span><span class="sxs-lookup"><span data-stu-id="a7b76-112">It uses the <xref:System.Xml.XmlNamespaceManager> when selecting elements.</span></span>

```csharp
XmlReader reader = XmlReader.Create("ConsolidatedPurchaseOrders.xml");
XElement root = XElement.Load(reader);
XmlNameTable nameTable = reader.NameTable;
XmlNamespaceManager namespaceManager = new XmlNamespaceManager(nameTable);
namespaceManager.AddNamespace("aw", "http://www.adventure-works.com");
IEnumerable<XElement> list1 = root.XPathSelectElements("./aw:*", namespaceManager);
IEnumerable<XElement> list2 =
    from el in root.Elements()
    where el.Name.Namespace == "http://www.adventure-works.com"
    select el;
if (list1.Count() == list2.Count() &&
        list1.Intersect(list2).Count() == list1.Count())
    Console.WriteLine("Results are identical");
else
    Console.WriteLine("Results differ");
foreach (XElement el in list2)
    Console.WriteLine(el);
```

<span data-ttu-id="a7b76-113">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="a7b76-113">This example produces the following output:</span></span>

```output
Results are identical
<aw:PurchaseOrder PONumber="11223" Date="2000-01-15" xmlns:aw="http://www.adventure-works.com">
    <aw:ShippingAddress>
      <aw:Name>Chris Preston</aw:Name>
      <aw:Street>123 Main St.</aw:Street>
      <aw:City>Seattle</aw:City>
      <aw:State>WA</aw:State>
      <aw:Zip>98113</aw:Zip>
      <aw:Country>USA</aw:Country>
    </aw:ShippingAddress>
    <aw:BillingAddress>
      <aw:Name>Chris Preston</aw:Name>
      <aw:Street>123 Main St.</aw:Street>
      <aw:City>Seattle</aw:City>
      <aw:State>WA</aw:State>
      <aw:Zip>98113</aw:Zip>
      <aw:Country>USA</aw:Country>
    </aw:BillingAddress>
    <aw:DeliveryInstructions>Ship only complete order.</aw:DeliveryInstructions>
    <aw:Item PartNum="LIT-01">
      <aw:ProductID>Litware Networking Card</aw:ProductID>
      <aw:Qty>1</aw:Qty>
      <aw:Price>20.99</aw:Price>
    </aw:Item>
    <aw:Item PartNum="LIT-25">
      <aw:ProductID>Litware 17in LCD Monitor</aw:ProductID>
      <aw:Qty>1</aw:Qty>
      <aw:Price>199.99</aw:Price>
    </aw:Item>
  </aw:PurchaseOrder>
```
