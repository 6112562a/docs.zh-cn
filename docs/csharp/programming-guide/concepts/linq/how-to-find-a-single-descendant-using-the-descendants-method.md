---
title: 如何：使用 Descendants 方法查找单个后代 (C#)
ms.date: 07/20/2015
ms.assetid: 6f735be9-0293-4680-8007-ca9d96bfebed
ms.openlocfilehash: 726c89b8fdd3df774de2d7ac9a824f2b3769d404
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "68709968"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-c"></a><span data-ttu-id="f64f7-102">如何：使用 Descendants 方法查找单个后代 (C#)</span><span class="sxs-lookup"><span data-stu-id="f64f7-102">How to: Find a Single Descendant Using the Descendants Method (C#)</span></span>
<span data-ttu-id="f64f7-103">可以使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 轴方法快速编写代码来查找名称唯一的单个元素。</span><span class="sxs-lookup"><span data-stu-id="f64f7-103">You can use the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis method to quickly write code to find a single uniquely named element.</span></span> <span data-ttu-id="f64f7-104">如果想要查找具有特定名称的特定后代，则此技术特别有用。</span><span class="sxs-lookup"><span data-stu-id="f64f7-104">This technique is especially useful when you want to find a particular descendant with a specific name.</span></span> <span data-ttu-id="f64f7-105">虽然可以编写代码以导航到需要的元素，但使用 <xref:System.Xml.Linq.XContainer.Descendants%2A> 轴编写代码通常更快更容易。</span><span class="sxs-lookup"><span data-stu-id="f64f7-105">You could write the code to navigate to the desired element, but it is often faster and easier to write the code using the <xref:System.Xml.Linq.XContainer.Descendants%2A> axis.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f64f7-106">示例</span><span class="sxs-lookup"><span data-stu-id="f64f7-106">Example</span></span>  
 <span data-ttu-id="f64f7-107">本示例使用 <xref:System.Linq.Enumerable.First%2A> 标准查询运算符。</span><span class="sxs-lookup"><span data-stu-id="f64f7-107">This example uses the <xref:System.Linq.Enumerable.First%2A> standard query operator.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <GrandChild1>GC1 Value</GrandChild1>  
  </Child1>  
  <Child2>  
    <GrandChild2>GC2 Value</GrandChild2>  
  </Child2>  
  <Child3>  
    <GrandChild3>GC3 Value</GrandChild3>  
  </Child3>  
  <Child4>  
    <GrandChild4>GC4 Value</GrandChild4>  
  </Child4>  
</Root>");  
string grandChild3 = (string)  
    (from el in root.Descendants("GrandChild3")  
    select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="f64f7-108">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="f64f7-108">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
  
## <a name="example"></a><span data-ttu-id="f64f7-109">示例</span><span class="sxs-lookup"><span data-stu-id="f64f7-109">Example</span></span>  
 <span data-ttu-id="f64f7-110">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="f64f7-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="f64f7-111">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="f64f7-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<aw:Root xmlns:aw='http://www.adventure-works.com'>  
  <aw:Child1>  
    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
  </aw:Child1>  
  <aw:Child2>  
    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
  </aw:Child2>  
  <aw:Child3>  
    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
  </aw:Child3>  
  <aw:Child4>  
    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
  </aw:Child4>  
</aw:Root>");  
XNamespace aw = "http://www.adventure-works.com";  
string grandChild3 = (string)  
    (from el in root.Descendants(aw + "GrandChild3")  
     select el).First();  
Console.WriteLine(grandChild3);  
```  
  
 <span data-ttu-id="f64f7-112">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="f64f7-112">This code produces the following output:</span></span>  
  
```  
GC3 Value  
```  
