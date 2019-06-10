---
title: 向 XML 树添加元素、属性和节点 (C#)
ms.date: 07/20/2015
ms.assetid: db911e4f-40aa-499a-9500-a9763bb6df56
ms.openlocfilehash: fee03dd2ba0818778afb3447e8930a2c2567b067
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486236"
---
# <a name="adding-elements-attributes-and-nodes-to-an-xml-tree-c"></a><span data-ttu-id="d1954-102">向 XML 树添加元素、属性和节点 (C#)</span><span class="sxs-lookup"><span data-stu-id="d1954-102">Adding Elements, Attributes, and Nodes to an XML Tree (C#)</span></span>
<span data-ttu-id="d1954-103">可以向现有的 XML 树中添加内容（包括元素、属性、注释、处理指令、文本和 CDATA）。</span><span class="sxs-lookup"><span data-stu-id="d1954-103">You can add content (elements, attributes, comments, processing instructions, text, and CDATA) to an existing XML tree.</span></span>  
  
## <a name="methods-for-adding-content"></a><span data-ttu-id="d1954-104">添加内容的方法</span><span class="sxs-lookup"><span data-stu-id="d1954-104">Methods for Adding Content</span></span>  
 <span data-ttu-id="d1954-105">下面的方法将子内容添加到 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 中：</span><span class="sxs-lookup"><span data-stu-id="d1954-105">The following methods add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="d1954-106">方法</span><span class="sxs-lookup"><span data-stu-id="d1954-106">Method</span></span>|<span data-ttu-id="d1954-107">说明</span><span class="sxs-lookup"><span data-stu-id="d1954-107">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="d1954-108">在 <xref:System.Xml.Linq.XContainer> 的子内容的末尾添加内容。</span><span class="sxs-lookup"><span data-stu-id="d1954-108">Adds content at the end of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="d1954-109">在 <xref:System.Xml.Linq.XContainer> 的子内容的开头添加内容。</span><span class="sxs-lookup"><span data-stu-id="d1954-109">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
  
 <span data-ttu-id="d1954-110">下面的方法将内容添加为 <xref:System.Xml.Linq.XNode> 的同级节点。</span><span class="sxs-lookup"><span data-stu-id="d1954-110">The following methods add content as sibling nodes of an <xref:System.Xml.Linq.XNode>.</span></span> <span data-ttu-id="d1954-111">向其中添加同级内容的最常见的节点是 <xref:System.Xml.Linq.XElement>，不过你也可以将有效的同级内容添加到其他类型的节点，例如 <xref:System.Xml.Linq.XText> 或 <xref:System.Xml.Linq.XComment>。</span><span class="sxs-lookup"><span data-stu-id="d1954-111">The most common node to which you add sibling content is <xref:System.Xml.Linq.XElement>, although you can add valid sibling content to other types of nodes such as <xref:System.Xml.Linq.XText> or <xref:System.Xml.Linq.XComment>.</span></span>  
  
|<span data-ttu-id="d1954-112">方法</span><span class="sxs-lookup"><span data-stu-id="d1954-112">Method</span></span>|<span data-ttu-id="d1954-113">说明</span><span class="sxs-lookup"><span data-stu-id="d1954-113">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="d1954-114">在 <xref:System.Xml.Linq.XNode> 后面添加内容。</span><span class="sxs-lookup"><span data-stu-id="d1954-114">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="d1954-115">在 <xref:System.Xml.Linq.XNode> 前面添加内容。</span><span class="sxs-lookup"><span data-stu-id="d1954-115">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d1954-116">示例</span><span class="sxs-lookup"><span data-stu-id="d1954-116">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d1954-117">说明</span><span class="sxs-lookup"><span data-stu-id="d1954-117">Description</span></span>  
 <span data-ttu-id="d1954-118">下面的示例创建两个 XML 树，然后修改其中一个树。</span><span class="sxs-lookup"><span data-stu-id="d1954-118">The following example creates two XML trees, and then modifies one of the trees.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d1954-119">代码</span><span class="sxs-lookup"><span data-stu-id="d1954-119">Code</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",   
    new XElement("Element1", 1),  
    new XElement("Element2", 2),  
    new XElement("Element3", 3),  
    new XElement("Element4", 4),  
    new XElement("Element5", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child2", 2),  
    new XElement("Child3", 3),  
    new XElement("Child4", 4),  
    new XElement("Child5", 5)  
);  
xmlTree.Add(new XElement("NewChild", "new content"));  
xmlTree.Add(  
    from el in srcTree.Elements()  
    where (int)el > 3  
    select el  
);  
// Even though Child9 does not exist in srcTree, the following statement will not  
// throw an exception, and nothing will be added to xmlTree.  
xmlTree.Add(srcTree.Element("Child9"));  
Console.WriteLine(xmlTree);  
```  
  
### <a name="comments"></a><span data-ttu-id="d1954-120">注释</span><span class="sxs-lookup"><span data-stu-id="d1954-120">Comments</span></span>  
 <span data-ttu-id="d1954-121">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="d1954-121">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>1</Child1>  
  <Child2>2</Child2>  
  <Child3>3</Child3>  
  <Child4>4</Child4>  
  <Child5>5</Child5>  
  <NewChild>new content</NewChild>  
  <Element4>4</Element4>  
  <Element5>5</Element5>  
</Root>  
```  
  