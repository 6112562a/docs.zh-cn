---
title: LINQ to XML 与DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 6ab775cc259fd3a337358bca2da6055d7b1ea6bd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596964"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="5af42-102">LINQ to XML 与DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="5af42-102">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="5af42-103">本节说明 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 和当前主导 XML 编程 API（W3C 文档对象模型 (DOM)）之间的主要区别。</span><span class="sxs-lookup"><span data-stu-id="5af42-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="5af42-104">构造 XML 树的新方式</span><span class="sxs-lookup"><span data-stu-id="5af42-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="5af42-105">在 W3C DOM 中，应当从下至上生成 XML 树；即先创建文档，然后创建元素，再将元素添加到文档。</span><span class="sxs-lookup"><span data-stu-id="5af42-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="5af42-106">例如，下面是使用 DOM 的 Microsoft 实现 <xref:System.Xml.XmlDocument> 创建 XML 树的典型方式：</span><span class="sxs-lookup"><span data-stu-id="5af42-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
XmlElement phone1 = doc.CreateElement("Phone");  
phone1.SetAttribute("Type", "Home");  
phone1.InnerText = "206-555-0144";          
XmlElement phone2 = doc.CreateElement("Phone");  
phone2.SetAttribute("Type", "Work");  
phone2.InnerText = "425-555-0145";          
XmlElement street1 = doc.CreateElement("Street1");          
street1.InnerText = "123 Main St";  
XmlElement city = doc.CreateElement("City");  
city.InnerText = "Mercer Island";  
XmlElement state = doc.CreateElement("State");  
state.InnerText = "WA";  
XmlElement postal = doc.CreateElement("Postal");  
postal.InnerText = "68042";  
XmlElement address = doc.CreateElement("Address");  
address.AppendChild(street1);  
address.AppendChild(city);  
address.AppendChild(state);  
address.AppendChild(postal);  
XmlElement contact = doc.CreateElement("Contact");  
contact.AppendChild(name);  
contact.AppendChild(phone1);  
contact.AppendChild(phone2);  
contact.AppendChild(address);  
XmlElement contacts = doc.CreateElement("Contacts");  
contacts.AppendChild(contact);  
doc.AppendChild(contacts);  
```  
  
 <span data-ttu-id="5af42-107">这种编码方式不会提供很多有关 XML 树结构的可视信息。</span><span class="sxs-lookup"><span data-stu-id="5af42-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5af42-108">支持用此方法创建 XML 树，但也支持另一种方法，即函数构造。</span><span class="sxs-lookup"><span data-stu-id="5af42-108">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="5af42-109">函数构造使用 <xref:System.Xml.Linq.XElement> 和 <xref:System.Xml.Linq.XAttribute> 构造函数生成 XML 树。</span><span class="sxs-lookup"><span data-stu-id="5af42-109">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="5af42-110">下面演示如何通过使用 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 功能性构造法构造相同的 XML 树：</span><span class="sxs-lookup"><span data-stu-id="5af42-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144",   
                new XAttribute("Type", "Home")),  
            new XElement("phone", "425-555-0145",  
                new XAttribute("Type", "Work")),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 <span data-ttu-id="5af42-111">请注意，缩进用于构造 XML 树的代码可显示基础 XML 的结构。</span><span class="sxs-lookup"><span data-stu-id="5af42-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="5af42-112">有关详细信息，请参阅[创建 XML 树 (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="5af42-112">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="5af42-113">直接使用 XML 元素</span><span class="sxs-lookup"><span data-stu-id="5af42-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="5af42-114">在使用 XML 编程时，主要关注的通常是 XML 元素，也可能关注属性。</span><span class="sxs-lookup"><span data-stu-id="5af42-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="5af42-115">在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，可以直接使用 XML 元素和属性。</span><span class="sxs-lookup"><span data-stu-id="5af42-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="5af42-116">例如，可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="5af42-116">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="5af42-117">创建 XML 元素而根本不使用文档对象。</span><span class="sxs-lookup"><span data-stu-id="5af42-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="5af42-118">当必须使用 XML 树的片段时，这可简化编程。</span><span class="sxs-lookup"><span data-stu-id="5af42-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="5af42-119">直接从 XML 文件加载 `T:System.Xml.Linq.XElement` 对象。</span><span class="sxs-lookup"><span data-stu-id="5af42-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="5af42-120">将 `T:System.Xml.Linq.XElement` 对象序列化为文件或流。</span><span class="sxs-lookup"><span data-stu-id="5af42-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="5af42-121">比较而言，W3C DOM 中的 XML 文档用作 XML 树的逻辑容器。</span><span class="sxs-lookup"><span data-stu-id="5af42-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="5af42-122">在 DOM 中，必须在 XML 文档的上下文中创建 XML 节点，包括元素和属性。</span><span class="sxs-lookup"><span data-stu-id="5af42-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="5af42-123">下面是在 DOM 中创建一个 name 元素的代码片段：</span><span class="sxs-lookup"><span data-stu-id="5af42-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="5af42-124">如果要跨多个文档使用某个元素，则必须跨文档导入节点。</span><span class="sxs-lookup"><span data-stu-id="5af42-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5af42-125">避免了这一复杂操作。</span><span class="sxs-lookup"><span data-stu-id="5af42-125">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="5af42-126">使用 LINQ to XML 时，仅在文档的根级别添加注释或处理说明时，才需使用 <xref:System.Xml.Linq.XDocument> 类。</span><span class="sxs-lookup"><span data-stu-id="5af42-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="5af42-127">名称和命名空间的简化处理</span><span class="sxs-lookup"><span data-stu-id="5af42-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="5af42-128">处理名称、命名空间和命名空间前缀通常是 XML 编程的复杂部分。</span><span class="sxs-lookup"><span data-stu-id="5af42-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5af42-129">完全不需要处理命名空间前缀，从而简化了名称和命名空间。</span><span class="sxs-lookup"><span data-stu-id="5af42-129">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="5af42-130">可以轻松控制命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="5af42-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="5af42-131">但如果您决定不显式控制命名空间前缀，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 将会在序列化过程中分配命名空间前缀（如果需要）或使用默认命名空间进行序列化（如果不需要）。</span><span class="sxs-lookup"><span data-stu-id="5af42-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="5af42-132">如果使用默认命名空间，则生成的文档中将没有命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="5af42-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="5af42-133">有关详细信息，请参阅[使用 XML 命名空间 (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="5af42-133">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="5af42-134">DOM 的另一个问题是它不允许您更改节点的名称。</span><span class="sxs-lookup"><span data-stu-id="5af42-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="5af42-135">您必须创建新节点并将所有子节点复制到此节点，从而会失去原始节点标识。</span><span class="sxs-lookup"><span data-stu-id="5af42-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5af42-136">允许对节点设置 <xref:System.Xml.Linq.XName> 属性，因此可避免此问题。</span><span class="sxs-lookup"><span data-stu-id="5af42-136">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="5af42-137">对加载 XML 的静态方法支持</span><span class="sxs-lookup"><span data-stu-id="5af42-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5af42-138">允许您通过使用静态方法而不是实例方法来加载 XML。</span><span class="sxs-lookup"><span data-stu-id="5af42-138">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="5af42-139">这简化了加载和分析。</span><span class="sxs-lookup"><span data-stu-id="5af42-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="5af42-140">有关详细信息，请参阅[如何：从文件加载 XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)。</span><span class="sxs-lookup"><span data-stu-id="5af42-140">For more information, see [How to: Load XML from a File (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="5af42-141">移除对 DTD 构造的支持</span><span class="sxs-lookup"><span data-stu-id="5af42-141">Removal of Support for DTD Constructs</span></span>  
 <span data-ttu-id="5af42-142">通过移除对实体和实体引用的支持，[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 进一步简化了 XML 编程。</span><span class="sxs-lookup"><span data-stu-id="5af42-142">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="5af42-143">实体因管理复杂而很少使用。</span><span class="sxs-lookup"><span data-stu-id="5af42-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="5af42-144">移除对它们的支持可提高性能并简化编程接口。</span><span class="sxs-lookup"><span data-stu-id="5af42-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="5af42-145">在填充 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 树时，会展开所有 DTD 实体。</span><span class="sxs-lookup"><span data-stu-id="5af42-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="5af42-146">对片段的支持</span><span class="sxs-lookup"><span data-stu-id="5af42-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5af42-147">未提供 `XmlDocumentFragment` 类的等效项。</span><span class="sxs-lookup"><span data-stu-id="5af42-147">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="5af42-148">但在很多情况下，`XmlDocumentFragment` 概念都可以通过执行类型化为<xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XNode> 或 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement> 的查询来进行处理。</span><span class="sxs-lookup"><span data-stu-id="5af42-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="5af42-149">对 XPathNavigator 的支持</span><span class="sxs-lookup"><span data-stu-id="5af42-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5af42-150">通过 <xref:System.Xml.XPath.XPathNavigator> 命名空间中的扩展方法提供对 <xref:System.Xml.XPath?displayProperty=nameWithType> 的支持。</span><span class="sxs-lookup"><span data-stu-id="5af42-150">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="5af42-151">有关更多信息，请参见<xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5af42-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="5af42-152">对空白和缩进的支持</span><span class="sxs-lookup"><span data-stu-id="5af42-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5af42-153">处理空白的方式比 DOM 更简单。</span><span class="sxs-lookup"><span data-stu-id="5af42-153">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="5af42-154">一种常用情况是读取缩进的 XML，在内存中创建一个没有任何空白文本节点（即不保留空白）的 XML 树，对该 XML 执行某些操作，然后保存带缩进的 XML。</span><span class="sxs-lookup"><span data-stu-id="5af42-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="5af42-155">在序列化带格式的 XML 时，只保留 XML 树中有意义的空白。</span><span class="sxs-lookup"><span data-stu-id="5af42-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="5af42-156">这是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的默认行为。</span><span class="sxs-lookup"><span data-stu-id="5af42-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="5af42-157">另一个常见的情况是读取和修改已经有意缩进的 XML。</span><span class="sxs-lookup"><span data-stu-id="5af42-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="5af42-158">您可能不想以任何方式更改这种缩进。</span><span class="sxs-lookup"><span data-stu-id="5af42-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="5af42-159">在 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中，可以通过在加载或解析 XML 时保留空白，并在序列化 XML 时禁用格式设置来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="5af42-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5af42-160">将空白存储为 <xref:System.Xml.Linq.XText> 节点，而不像 DOM 那样具有专门的 <xref:System.Xml.XmlNodeType.Whitespace> 节点类型。</span><span class="sxs-lookup"><span data-stu-id="5af42-160">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="5af42-161">对批注的支持</span><span class="sxs-lookup"><span data-stu-id="5af42-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5af42-162">元素支持可扩展的批注集。</span><span class="sxs-lookup"><span data-stu-id="5af42-162">elements support an extensible set of annotations.</span></span> <span data-ttu-id="5af42-163">这对于跟踪有关元素的杂项信息（如架构信息、关于元素是否绑定到 UI 的信息或应用程序特定的任何其他信息）很有用。</span><span class="sxs-lookup"><span data-stu-id="5af42-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="5af42-164">有关详细信息，请参阅 [LINQ to XML 批注](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-annotations.md)。</span><span class="sxs-lookup"><span data-stu-id="5af42-164">For more information, see [LINQ to XML Annotations](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="5af42-165">对架构信息的支持</span><span class="sxs-lookup"><span data-stu-id="5af42-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5af42-166">通过 <xref:System.Xml.Schema?displayProperty=nameWithType> 命名空间中的扩展方法提供对 XSD 验证的支持。</span><span class="sxs-lookup"><span data-stu-id="5af42-166">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="5af42-167">你可以验证 XML 树是否符合 XSD。</span><span class="sxs-lookup"><span data-stu-id="5af42-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="5af42-168">你可以用架构验证后信息集 (PSVI) 填充 XML 树。</span><span class="sxs-lookup"><span data-stu-id="5af42-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="5af42-169">有关详细信息，请参阅[如何：使用 XSD 进行验证](../../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) 和 <xref:System.Xml.Schema.Extensions>。</span><span class="sxs-lookup"><span data-stu-id="5af42-169">For more information, see [How to: Validate Using XSD](../../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5af42-170">请参阅</span><span class="sxs-lookup"><span data-stu-id="5af42-170">See also</span></span>

- [<span data-ttu-id="5af42-171">入门 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="5af42-171">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
