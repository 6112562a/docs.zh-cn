---
title: 如何：编写基于上下文查找元素的查询 (C#)
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: f6fd0a9dc0f2579185f2f72997f1d406a885c636
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710029"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="99650-102">如何：编写基于上下文查找元素的查询 (C#)</span><span class="sxs-lookup"><span data-stu-id="99650-102">How to: Write a Query that Finds Elements Based on Context (C#)</span></span>
<span data-ttu-id="99650-103">有时，您可能必须编写基于元素上下文选择元素的查询。</span><span class="sxs-lookup"><span data-stu-id="99650-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="99650-104">您可能需要基于前面或后面的同级元素进行筛选。</span><span class="sxs-lookup"><span data-stu-id="99650-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="99650-105">您可能需要基于子元素或上级元素进行筛选。</span><span class="sxs-lookup"><span data-stu-id="99650-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="99650-106">通过编写查询并在 `where` 子句中使用查询的结果可以实现此目的。</span><span class="sxs-lookup"><span data-stu-id="99650-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="99650-107">如果在测试值之前必须先测试空值，则更适合在 `let` 子句中执行查询，然后在 `where` 子句中使用查询结果。</span><span class="sxs-lookup"><span data-stu-id="99650-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99650-108">示例</span><span class="sxs-lookup"><span data-stu-id="99650-108">Example</span></span>  
 <span data-ttu-id="99650-109">下面的示例选择后面紧接 `p` 元素的所有 `ul` 元素。</span><span class="sxs-lookup"><span data-stu-id="99650-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants("p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name.LocalName == "ul"  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="99650-110">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="99650-110">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="99650-111">示例</span><span class="sxs-lookup"><span data-stu-id="99650-111">Example</span></span>  
 <span data-ttu-id="99650-112">下面的示例演示如何对命名空间中的 XML 进行同样的查询。</span><span class="sxs-lookup"><span data-stu-id="99650-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="99650-113">有关详细信息，请参阅[命名空间概述(LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="99650-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
XNamespace ad = "http://www.adatum.com";  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants(ad + "p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name == ad.GetName("ul")  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="99650-114">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="99650-114">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="99650-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="99650-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
