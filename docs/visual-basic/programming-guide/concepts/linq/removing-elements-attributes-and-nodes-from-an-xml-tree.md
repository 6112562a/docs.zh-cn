---
title: 从 XML 树中移除元素、特性和节点
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: 4cce1eff469c1f737e18b88cce30155547d9f11b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348956"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="7a494-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a494-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="7a494-103">可以修改 XML 树，移除元素、属性和其他类型的节点。</span><span class="sxs-lookup"><span data-stu-id="7a494-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="7a494-104">从 XML 文档中移除单个元素或单个属性的操作非常简单。</span><span class="sxs-lookup"><span data-stu-id="7a494-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="7a494-105">但是，若要移除多个元素或属性的集合，则应首先将一个集合具体化为一个列表，然后从该列表中删除相应元素或属性。</span><span class="sxs-lookup"><span data-stu-id="7a494-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="7a494-106">最好的方法是使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 扩展方法，该方法可以实现此操作。</span><span class="sxs-lookup"><span data-stu-id="7a494-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="7a494-107">这么做的主要原因在于，从 XML 树检索的大多数集合都是用延迟执行生成的。</span><span class="sxs-lookup"><span data-stu-id="7a494-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="7a494-108">如果不首先将集合具体化为列表，或者不使用扩展方法，则可能会遇到某类 Bug。</span><span class="sxs-lookup"><span data-stu-id="7a494-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="7a494-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7a494-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="7a494-110">下列方法可以从 XML 树中移除节点和属性。</span><span class="sxs-lookup"><span data-stu-id="7a494-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="7a494-111">方法</span><span class="sxs-lookup"><span data-stu-id="7a494-111">Method</span></span>|<span data-ttu-id="7a494-112">描述</span><span class="sxs-lookup"><span data-stu-id="7a494-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="7a494-113">从父节点中移除 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="7a494-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="7a494-114">从 <xref:System.Xml.Linq.XContainer> 中移除子节点。</span><span class="sxs-lookup"><span data-stu-id="7a494-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="7a494-115">从 <xref:System.Xml.Linq.XElement> 中移除内容和属性。</span><span class="sxs-lookup"><span data-stu-id="7a494-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="7a494-116">移除 <xref:System.Xml.Linq.XElement> 的属性。</span><span class="sxs-lookup"><span data-stu-id="7a494-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="7a494-117">如果传递 `null` 作为值，则移除该属性。</span><span class="sxs-lookup"><span data-stu-id="7a494-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="7a494-118">如果传递 `null` 作为值，则移除该子元素。</span><span class="sxs-lookup"><span data-stu-id="7a494-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="7a494-119">从父节点中移除 <xref:System.Xml.Linq.XNode>。</span><span class="sxs-lookup"><span data-stu-id="7a494-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="7a494-120">从父元素中移除源集合中的每个属性或元素。</span><span class="sxs-lookup"><span data-stu-id="7a494-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7a494-121">示例</span><span class="sxs-lookup"><span data-stu-id="7a494-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7a494-122">描述</span><span class="sxs-lookup"><span data-stu-id="7a494-122">Description</span></span>  
 <span data-ttu-id="7a494-123">此示例演示三种移除元素的方法。</span><span class="sxs-lookup"><span data-stu-id="7a494-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="7a494-124">第一种，移除单个元素。</span><span class="sxs-lookup"><span data-stu-id="7a494-124">First, it removes a single element.</span></span> <span data-ttu-id="7a494-125">第二种，检索元素的集合，使用 <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 运算符将它们具体化，然后移除集合。</span><span class="sxs-lookup"><span data-stu-id="7a494-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="7a494-126">最后一种，检索元素的集合，使用 <xref:System.Xml.Linq.Extensions.Remove%2A> 扩展方法移除元素。</span><span class="sxs-lookup"><span data-stu-id="7a494-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="7a494-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="7a494-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="7a494-128">代码</span><span class="sxs-lookup"><span data-stu-id="7a494-128">Code</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1/>  
            <GrandChild2/>  
            <GrandChild3/>  
        </Child1>  
        <Child2>  
            <GrandChild4/>  
            <GrandChild5/>  
            <GrandChild6/>  
        </Child2>  
        <Child3>  
            <GrandChild7/>  
            <GrandChild8/>  
            <GrandChild9/>  
        </Child3>  
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
```  
  
### <a name="comments"></a><span data-ttu-id="7a494-129">注释</span><span class="sxs-lookup"><span data-stu-id="7a494-129">Comments</span></span>  
 <span data-ttu-id="7a494-130">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="7a494-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 <span data-ttu-id="7a494-131">请注意，第一个孙元素已从 `Child1` 中移除。</span><span class="sxs-lookup"><span data-stu-id="7a494-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="7a494-132">所有孙元素都已从 `Child2` 和 `Child3` 中移除。</span><span class="sxs-lookup"><span data-stu-id="7a494-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a494-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="7a494-133">See also</span></span>

- [<span data-ttu-id="7a494-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a494-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
