---
title: 如何：查找命名空间中的所有节点 (C#)
ms.date: 07/20/2015
ms.assetid: 3a38b913-a53e-4d0e-a19d-8782bffd3364
ms.openlocfilehash: f8a6f33084417e0dd489002eaa5d2de509e30d39
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253788"
---
# <a name="how-to-find-all-nodes-in-a-namespace-c"></a><span data-ttu-id="50675-102">如何：查找命名空间中的所有节点 (C#)</span><span class="sxs-lookup"><span data-stu-id="50675-102">How to: Find All Nodes in a Namespace (C#)</span></span>
<span data-ttu-id="50675-103">您可以对每个元素或属性的命名空间进行筛选，以便查找该特定命名空间中的所有节点。</span><span class="sxs-lookup"><span data-stu-id="50675-103">You can filter on the namespace of each element or attribute to find all nodes in that particular namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50675-104">示例</span><span class="sxs-lookup"><span data-stu-id="50675-104">Example</span></span>  
 <span data-ttu-id="50675-105">下面的示例创建一个包含两个命名空间的 XML 树。</span><span class="sxs-lookup"><span data-stu-id="50675-105">The following example creates an XML tree with two namespaces.</span></span> <span data-ttu-id="50675-106">然后循环访问该树并将打印其中一个命名空间中所有元素和属性的名称。</span><span class="sxs-lookup"><span data-stu-id="50675-106">It then iterates through the tree and prints the names of all the elements and attributes in one of those namespaces.</span></span>  
  
```csharp  
string markup = @"<aw:Root xmlns:aw='http://www.adventure-works.com' xmlns:fc='www.fourthcoffee.com'>  
  <fc:Child1>abc</fc:Child1>  
  <fc:Child2>def</fc:Child2>  
  <aw:Child3>ghi</aw:Child3>  
  <fc:Child4>  
    <fc:GrandChild1>jkl</fc:GrandChild1>  
    <aw:GrandChild2>mno</aw:GrandChild2>  
  </fc:Child4>  
</aw:Root>";  
XElement xmlTree = XElement.Parse(markup);  
Console.WriteLine("Nodes in the http://www.adventure-works.com namespace");  
IEnumerable<XElement> awElements =  
    from el in xmlTree.Descendants()  
    where el.Name.Namespace == "http://www.adventure-works.com"  
    select el;  
foreach (XElement el in awElements)  
    Console.WriteLine(el.Name.ToString());  
```  
  
 <span data-ttu-id="50675-107">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="50675-107">This code produces the following output:</span></span>  
  
```output  
Nodes in the http://www.adventure-works.com namespace  
{http://www.adventure-works.com}Child3  
{http://www.adventure-works.com}GrandChild2  
```  
  
## <a name="example"></a><span data-ttu-id="50675-108">示例</span><span class="sxs-lookup"><span data-stu-id="50675-108">Example</span></span>  
 <span data-ttu-id="50675-109">下面的查询所访问的 XML 文件包含两个位于不同命名空间中的采购订单。</span><span class="sxs-lookup"><span data-stu-id="50675-109">The XML file accessed by the following query contains purchase orders in two different namespaces.</span></span> <span data-ttu-id="50675-110">该查询只用其中一个命名空间中的元素创建一个新树。</span><span class="sxs-lookup"><span data-stu-id="50675-110">The query creates a new tree with just the elements in one of the namespaces.</span></span>  
  
 <span data-ttu-id="50675-111">此示例使用下面的 XML 文档：[示例 XML 文件：合并采购单](./sample-xml-file-consolidated-purchase-orders.md)。</span><span class="sxs-lookup"><span data-stu-id="50675-111">This example uses the following XML document: [Sample XML File: Consolidated Purchase Orders](./sample-xml-file-consolidated-purchase-orders.md).</span></span>  
  
```csharp  
XDocument cpo = XDocument.Load("ConsolidatedPurchaseOrders.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement newTree = new XElement("Root",  
    from el in cpo.Root.Elements()  
    where el.Name.Namespace == aw  
    select el  
);  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="50675-112">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="50675-112">This code produces the following output:</span></span>  
  
```xml  
<Root>  
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
</Root>  
```  
