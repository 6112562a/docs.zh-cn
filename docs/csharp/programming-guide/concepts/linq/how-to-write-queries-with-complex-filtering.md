---
title: 如何：编写使用复杂筛选的查询 (C#)
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 08c1e124542e6d7e4c728102b2aa7fb4a804794c
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710045"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a><span data-ttu-id="09e3a-102">如何：编写使用复杂筛选的查询 (C#)</span><span class="sxs-lookup"><span data-stu-id="09e3a-102">How to: Write Queries with Complex Filtering (C#)</span></span>
<span data-ttu-id="09e3a-103">有时，您需要编写使用复杂筛选器的 LINQ to XML 查询。</span><span class="sxs-lookup"><span data-stu-id="09e3a-103">Sometimes you want to write LINQ to XML queries with complex filters.</span></span> <span data-ttu-id="09e3a-104">例如，您可能必须查找其子元素具有特定名称和值的所有元素。</span><span class="sxs-lookup"><span data-stu-id="09e3a-104">For example, you might have to find all elements that have a child element with a particular name and value.</span></span> <span data-ttu-id="09e3a-105">本主题提供一个编写使用复杂筛选的查询的示例。</span><span class="sxs-lookup"><span data-stu-id="09e3a-105">This topic gives an example of writing a query with complex filtering.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09e3a-106">示例</span><span class="sxs-lookup"><span data-stu-id="09e3a-106">Example</span></span>  
 <span data-ttu-id="09e3a-107">本示例演示如何查找具有 `PurchaseOrder` 属性等于“Shipping”的子 `Address` 元素和等于“NY”的子 `Type` 元素的所有 `State` 元素。</span><span class="sxs-lookup"><span data-stu-id="09e3a-107">This example shows how to find all `PurchaseOrder` elements that have a child `Address` element that has a `Type` attribute equal to "Shipping" and a child `State` element equal to "NY".</span></span> <span data-ttu-id="09e3a-108">示例在 `Where` 子句中使用嵌套查询，如果集合中有任何元素，则 `Any` 运算符返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="09e3a-108">It uses a nested query in the `Where` clause, and the `Any` operator returns `true` if the collection has any elements in it.</span></span> <span data-ttu-id="09e3a-109">有关使用基于方法的查询语法的信息，请参阅 [LINQ 中的查询语法和方法语法](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="09e3a-109">For information about using method-based query syntax, see [Query Syntax and Method Syntax in LINQ](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
 <span data-ttu-id="09e3a-110">此示例使用下面的 XML 文档：[示例 XML 文件：多个采购订单 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="09e3a-110">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="09e3a-111">有关 `Any` 运算符的详细信息，请参阅[限定符运算 (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="09e3a-111">For more information about the `Any` operator, see [Quantifier Operations (C#)](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where   
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="09e3a-112">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="09e3a-112">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="example"></a><span data-ttu-id="09e3a-113">示例</span><span class="sxs-lookup"><span data-stu-id="09e3a-113">Example</span></span>  
 <span data-ttu-id="09e3a-114">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="09e3a-114">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="09e3a-115">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="09e3a-115">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="09e3a-116">此示例使用下面的 XML 文档：[示例 XML 文件：命名空间中的多个采购订单](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="09e3a-116">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 <span data-ttu-id="09e3a-117">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="09e3a-117">This code produces the following output:</span></span>  
  
```  
99505  
```  
  
## <a name="see-also"></a><span data-ttu-id="09e3a-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="09e3a-118">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="09e3a-119">投影运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="09e3a-119">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
- [<span data-ttu-id="09e3a-120">限定符运算 (C#)</span><span class="sxs-lookup"><span data-stu-id="09e3a-120">Quantifier Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/quantifier-operations.md)
