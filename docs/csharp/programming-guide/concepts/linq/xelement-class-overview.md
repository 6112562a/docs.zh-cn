---
title: XElement 类概述 (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 6a93dd4bdaf16fddff800b08b0f3146ecb63f9b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167889"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="65fb7-102">XElement 类概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="65fb7-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="65fb7-103"><xref:System.Xml.Linq.XElement> 类是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的基础类之一。</span><span class="sxs-lookup"><span data-stu-id="65fb7-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="65fb7-104">它表示一个 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="65fb7-104">It represents an XML element.</span></span> <span data-ttu-id="65fb7-105">可以使用该类创建元素；更改元素内容；添加、更改或删除子元素；向元素中添加属性；或以文本格式序列化元素内容。</span><span class="sxs-lookup"><span data-stu-id="65fb7-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="65fb7-106">还可以与 <xref:System.Xml?displayProperty=nameWithType> 中的其他类（例如 <xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 和 <xref:System.Xml.Xsl.XslCompiledTransform>）进行互操作。</span><span class="sxs-lookup"><span data-stu-id="65fb7-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
<span data-ttu-id="65fb7-107">本主题描述 <xref:System.Xml.Linq.XElement> 类提供的功能。</span><span class="sxs-lookup"><span data-stu-id="65fb7-107">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
## <a name="constructing-xml-trees"></a><span data-ttu-id="65fb7-108">构造 XML 树</span><span class="sxs-lookup"><span data-stu-id="65fb7-108">Constructing XML Trees</span></span>  
 <span data-ttu-id="65fb7-109">可以使用各种方式构造 XML 树，包括以下方式：</span><span class="sxs-lookup"><span data-stu-id="65fb7-109">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="65fb7-110">可以在代码中构造 XML 树。</span><span class="sxs-lookup"><span data-stu-id="65fb7-110">You can construct an XML tree in code.</span></span> <span data-ttu-id="65fb7-111">有关详细信息，请参阅[创建 XML 树 (C#)](./linq-to-xml-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="65fb7-111">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
- <span data-ttu-id="65fb7-112">可以从包括 <xref:System.IO.TextReader>、文本文件或 Web 地址 (URL) 在内的各种源解析 XML。</span><span class="sxs-lookup"><span data-stu-id="65fb7-112">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="65fb7-113">有关详细信息，请参阅[解析 XML (C#)](./how-to-parse-a-string.md)。</span><span class="sxs-lookup"><span data-stu-id="65fb7-113">For more information, see [Parsing XML (C#)](./how-to-parse-a-string.md).</span></span>  
  
- <span data-ttu-id="65fb7-114">可以使用 <xref:System.Xml.XmlReader> 来填充树。</span><span class="sxs-lookup"><span data-stu-id="65fb7-114">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="65fb7-115">有关详细信息，请参阅 <xref:System.Xml.Linq.XNode.ReadFrom%2A>。</span><span class="sxs-lookup"><span data-stu-id="65fb7-115">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="65fb7-116">如果您有一个可以将内容写入 <xref:System.Xml.XmlWriter> 的模块，则可以使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 方法来创建编写器，将该编写器传递到该模块，然后使用写入 <xref:System.Xml.XmlWriter> 的内容来填充 XML 树。</span><span class="sxs-lookup"><span data-stu-id="65fb7-116">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="65fb7-117">但是，创建 XML 树的最常见的方法如下：</span><span class="sxs-lookup"><span data-stu-id="65fb7-117">However, the most common way to create an XML tree is as follows:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="65fb7-118">另一个创建 XML 树的十分常用的方法是使用 LINQ 查询的结果来填充 XML 树，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="65fb7-118">Another very common technique for creating an XML tree involves using the results of a LINQ query to populate an XML tree, as shown in the following example:</span></span>  
  
```csharp  
XElement srcTree = new XElement("Root",  
    new XElement("Element", 1),  
    new XElement("Element", 2),  
    new XElement("Element", 3),  
    new XElement("Element", 4),  
    new XElement("Element", 5)  
);  
XElement xmlTree = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    from el in srcTree.Elements()  
    where (int)el > 2  
    select el  
);  
Console.WriteLine(xmlTree);  
```  
  
 <span data-ttu-id="65fb7-119">该示例产生下面的输出：</span><span class="sxs-lookup"><span data-stu-id="65fb7-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a><span data-ttu-id="65fb7-120">序列化 XML 树</span><span class="sxs-lookup"><span data-stu-id="65fb7-120">Serializing XML Trees</span></span>  
 <span data-ttu-id="65fb7-121">可以将 XML 树序列化为 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="65fb7-121">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="65fb7-122">有关详细信息，请参阅[序列化 XML 树 (C#)](./preserving-white-space-while-serializing.md)。</span><span class="sxs-lookup"><span data-stu-id="65fb7-122">For more information, see [Serializing XML Trees (C#)](./preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="65fb7-123">通过轴方法检索 XML 数据</span><span class="sxs-lookup"><span data-stu-id="65fb7-123">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="65fb7-124">可以使用轴方法检索属性、子元素、子代元素和上级元素。</span><span class="sxs-lookup"><span data-stu-id="65fb7-124">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="65fb7-125">LINQ 查询对轴方法进行操作，并提供了多种灵活而有效的方法导航和处理 XML 树。</span><span class="sxs-lookup"><span data-stu-id="65fb7-125">LINQ queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="65fb7-126">有关详细信息，请参阅 [LINQ to XML 轴 (C#)](./linq-to-xml-axes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="65fb7-126">For more information, see [LINQ to XML Axes (C#)](./linq-to-xml-axes-overview.md).</span></span>  
  
## <a name="querying-xml-trees"></a><span data-ttu-id="65fb7-127">查询 XML 树</span><span class="sxs-lookup"><span data-stu-id="65fb7-127">Querying XML Trees</span></span>  
 <span data-ttu-id="65fb7-128">可以编写从 XML 树提取数据的 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="65fb7-128">You can write LINQ queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="65fb7-129">有关详细信息，请参阅[查询 XML 树 (C#)](./how-to-find-an-element-with-a-specific-attribute.md)。</span><span class="sxs-lookup"><span data-stu-id="65fb7-129">For more information, see [Querying XML Trees (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span></span>  
  
## <a name="modifying-xml-trees"></a><span data-ttu-id="65fb7-130">修改 XML 树</span><span class="sxs-lookup"><span data-stu-id="65fb7-130">Modifying XML Trees</span></span>  
 <span data-ttu-id="65fb7-131">可以通过各种方式修改元素，例如更改元素的内容或属性。</span><span class="sxs-lookup"><span data-stu-id="65fb7-131">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="65fb7-132">还可以从元素的父级移除元素。</span><span class="sxs-lookup"><span data-stu-id="65fb7-132">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="65fb7-133">有关详细信息，请参阅[修改 XML 树 (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="65fb7-133">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65fb7-134">另请参阅</span><span class="sxs-lookup"><span data-stu-id="65fb7-134">See also</span></span>

- [<span data-ttu-id="65fb7-135">LINQ to XML 编程概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="65fb7-135">LINQ to XML Programming Overview (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
