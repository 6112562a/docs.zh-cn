---
title: 如何查找前面紧邻的同级 (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 74c06201-0b1b-4b5e-b3ac-0092980614e6
ms.openlocfilehash: 1e5aece41021642d43b7f6f7b78bb105156ee4ee
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141001"
---
# <a name="how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml-c"></a><span data-ttu-id="2a2f0-102">如何查找前面紧邻的同级 (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="2a2f0-102">How to find the immediate preceding sibling (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="2a2f0-103">有时，您需要查找某一节点的前面紧邻同级。</span><span class="sxs-lookup"><span data-stu-id="2a2f0-103">Sometimes you want to find the immediate preceding sibling to a node.</span></span> <span data-ttu-id="2a2f0-104">由于与 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 相比，XPath 中前面紧邻轴的位置谓词的语义同，因此这是一个更值得关注的比较。</span><span class="sxs-lookup"><span data-stu-id="2a2f0-104">Due to the difference in the semantics of positional predicates for the preceding sibling axes in XPath as opposed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], this is one of the more interesting comparisons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a2f0-105">示例</span><span class="sxs-lookup"><span data-stu-id="2a2f0-105">Example</span></span>  
 <span data-ttu-id="2a2f0-106">在本示例中，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 查询使用 <xref:System.Linq.Enumerable.Last%2A> 运算符查找由 <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A> 返回的集合中的最后一个节点。</span><span class="sxs-lookup"><span data-stu-id="2a2f0-106">In this example, the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] query uses the <xref:System.Linq.Enumerable.Last%2A> operator to find the last node in the collection returned by <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A>.</span></span> <span data-ttu-id="2a2f0-107">相比之下，XPath 表达式使用值为 1 的谓词来查找前面紧邻的元素。</span><span class="sxs-lookup"><span data-stu-id="2a2f0-107">By contrast, the XPath expression uses a predicate with a value of 1 to find the immediately preceding element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
    @"<Root>  
    <Child1/>  
    <Child2/>  
    <Child3/>  
    <Child4/>  
</Root>");  
XElement child4 = root.Element("Child4");  
  
// LINQ to XML query  
XElement el1 =  
    child4  
    .ElementsBeforeSelf()  
    .Last();  
  
// XPath expression  
XElement el2 =  
    ((IEnumerable)child4  
                 .XPathEvaluate("preceding-sibling::*[1]"))  
                 .Cast<XElement>()  
                 .First();  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 <span data-ttu-id="2a2f0-108">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="2a2f0-108">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Child3 />  
```  
