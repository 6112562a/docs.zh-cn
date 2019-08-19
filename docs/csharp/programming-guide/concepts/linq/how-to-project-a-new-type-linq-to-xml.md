---
title: 如何：投影新类型 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 48145cf9-1e0b-4e73-bbfd-28fc04800dc4
ms.openlocfilehash: 2bb521d1445dcecdad8b9c7b28bed90e1e38c8e8
ms.sourcegitcommit: d98fdb087d9c8aba7d2cb93fe4b4ee35a2308cee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/14/2019
ms.locfileid: "69012928"
---
# <a name="how-to-project-a-new-type-linq-to-xml-c"></a><span data-ttu-id="c4b08-102">如何：投影新类型 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c4b08-102">How to: Project a New Type (LINQ to XML) (C#)</span></span>

<span data-ttu-id="c4b08-103">本节中的其他示例已演示了一些查询，这些查询以 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>、<xref:System.Collections.Generic.IEnumerable%601> 的 `string` 和 <xref:System.Collections.Generic.IEnumerable%601> 的 `int` 的形式返回结果。</span><span class="sxs-lookup"><span data-stu-id="c4b08-103">Other examples in this section have shown queries that return results as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> of `string`, and <xref:System.Collections.Generic.IEnumerable%601> of `int`.</span></span> <span data-ttu-id="c4b08-104">这些是常见结果类型，但它们不是对所有情况都适用。</span><span class="sxs-lookup"><span data-stu-id="c4b08-104">These are common result types, but they are not appropriate for every scenario.</span></span> <span data-ttu-id="c4b08-105">在很多情况下，会希望查询返回其他类型的 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="c4b08-105">In many cases you will want your queries to return an <xref:System.Collections.Generic.IEnumerable%601> of some other type.</span></span>

## <a name="example"></a><span data-ttu-id="c4b08-106">示例</span><span class="sxs-lookup"><span data-stu-id="c4b08-106">Example</span></span>

<span data-ttu-id="c4b08-107">此示例演示如何在 `select` 子句中实例化对象。</span><span class="sxs-lookup"><span data-stu-id="c4b08-107">This example shows how to instantiate objects in the `select` clause.</span></span> <span data-ttu-id="c4b08-108">代码首先定义一个具有一个构造函数的新类，然后修改 `select` 语句，使该表达式成为新类的新实例。</span><span class="sxs-lookup"><span data-stu-id="c4b08-108">The code first defines a new class with a constructor, and then modifies the `select` statement so that the expression is a new instance of the new class.</span></span>

<span data-ttu-id="c4b08-109">此示例使用下面的 XML 文档：[示例 XML 文件：典型采购订单 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md)。</span><span class="sxs-lookup"><span data-stu-id="c4b08-109">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>

```csharp
class NameQty 
{
    public string name;
    public int qty;
    public NameQty(string n, int q)
    {
        name = n;
        qty = q; 
    }
};

class Program {
    public static void Main() 
    {
        XElement po = XElement.Load("PurchaseOrder.xml");
  
        IEnumerable<NameQty> nqList =
            from n in po.Descendants("Item")
            select new NameQty(
                    (string)n.Element("ProductName"),
                    (int)n.Element("Quantity")
                );
  
        foreach (NameQty n in nqList)
            Console.WriteLine(n.name + ":" + n.qty);
    }
}
```

<span data-ttu-id="c4b08-110">本示例使用 <xref:System.Xml.Linq.XContainer.Element%2A> 方法，该方法在主题[如何：检索单个子元素 (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).中有介绍。</span><span class="sxs-lookup"><span data-stu-id="c4b08-110">This example uses the <xref:System.Xml.Linq.XContainer.Element%2A> method that was introduced in the topic [How to: Retrieve a Single Child Element (LINQ to XML) (C#)](how-to-retrieve-a-single-child-element-linq-to-xml.md).</span></span> <span data-ttu-id="c4b08-111">还使用强制转换来检索 <xref:System.Xml.Linq.XContainer.Element%2A> 方法返回的元素值。</span><span class="sxs-lookup"><span data-stu-id="c4b08-111">It also uses casts to retrieve the values of the elements that are returned by the <xref:System.Xml.Linq.XContainer.Element%2A> method.</span></span>  

<span data-ttu-id="c4b08-112">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="c4b08-112">This example produces the following output:</span></span>

```console
Lawnmower:1
Baby Monitor:2
```
