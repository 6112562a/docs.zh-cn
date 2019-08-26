---
title: 检索段落的文本 (C#)
ms.date: 07/20/2015
ms.assetid: 127d635e-e559-408f-90c8-2bb621ca50ac
ms.openlocfilehash: 88a7e82a7d27048ce3f901e6e9d50b8737797adb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591086"
---
# <a name="retrieving-the-text-of-the-paragraphs-c"></a><span data-ttu-id="ade42-102">检索段落的文本 (C#)</span><span class="sxs-lookup"><span data-stu-id="ade42-102">Retrieving the Text of the Paragraphs (C#)</span></span>
<span data-ttu-id="ade42-103">此示例以上一个示例[检索段落及其样式 (C#)](./retrieving-the-paragraphs-and-their-styles.md) 为基础。</span><span class="sxs-lookup"><span data-stu-id="ade42-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (C#)](./retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="ade42-104">这个新示例将每个段落的文本作为字符串进行检索。</span><span class="sxs-lookup"><span data-stu-id="ade42-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="ade42-105">为检索文本，此示例另外添加了一个查询，该查询循环访问匿名类型的集合，并通过添加新成员 `Text` 对一个匿名类型的新集合进行投影。</span><span class="sxs-lookup"><span data-stu-id="ade42-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="ade42-106">该示例使用 <xref:System.Linq.Enumerable.Aggregate%2A> 标准查询运算符将多个字符串串联为一个字符串。</span><span class="sxs-lookup"><span data-stu-id="ade42-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="ade42-107">这种方法（即首先投影到一个匿名类型集合，然后使用该集合投影到一个新的匿名类型集合）是一种既常用又有效的方法。</span><span class="sxs-lookup"><span data-stu-id="ade42-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="ade42-108">此查询在编写时本来可以不投影到第一个匿名类型。</span><span class="sxs-lookup"><span data-stu-id="ade42-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="ade42-109">但是因为使用迟缓计算，即使这样做也并不会过多占用额外的处理能力。</span><span class="sxs-lookup"><span data-stu-id="ade42-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="ade42-110">此方法在堆上创建更多生存时间很短的对象，但这并不会显著降低性能。</span><span class="sxs-lookup"><span data-stu-id="ade42-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="ade42-111">当然，可以只编写一个查询，使之包含检索段落、每个段落的样式以及每个段落的文本这些功能。</span><span class="sxs-lookup"><span data-stu-id="ade42-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="ade42-112">但是，将一个比较复杂的查询分解成多个查询通常很有好处，因为这样产生的代码更加模块化，更易于维护。</span><span class="sxs-lookup"><span data-stu-id="ade42-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="ade42-113">而且，如果需要重用查询的某一部分，使用此方式编写的查询更容易重构。</span><span class="sxs-lookup"><span data-stu-id="ade42-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="ade42-114">这些链接在一起的查询使用的处理模型在[教程：将查询链接在一起 (C#)](./tutorial-chaining-queries-together.md) 中有详细的讨论。</span><span class="sxs-lookup"><span data-stu-id="ade42-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Chaining Queries Together (C#)](./tutorial-chaining-queries-together.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ade42-115">示例</span><span class="sxs-lookup"><span data-stu-id="ade42-115">Example</span></span>  
 <span data-ttu-id="ade42-116">本示例处理一个 WordprocessingML 文档，它确定元素节点、样式名称和每个段落的文本。</span><span class="sxs-lookup"><span data-stu-id="ade42-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="ade42-117">本示例以本教程中前面的一些示例为基础构建。</span><span class="sxs-lookup"><span data-stu-id="ade42-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="ade42-118">下面代码中的注释标识出了这个新查询。</span><span class="sxs-lookup"><span data-stu-id="ade42-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="ade42-119">有关创建此示例的源文档的说明，请参阅[创建源 Office Open XML 文档 (C#)](./creating-the-source-office-open-xml-document.md)。</span><span class="sxs-lookup"><span data-stu-id="ade42-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="ade42-120">本示例使用 WindowsBase 程序集中的类。</span><span class="sxs-lookup"><span data-stu-id="ade42-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="ade42-121">它使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空间中的类型。</span><span class="sxs-lookup"><span data-stu-id="ade42-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string fileName = "SampleDoc.docx";  
  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string stylesRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
XDocument xDoc = null;  
XDocument styleDoc = null;  
  
using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship docPackageRelationship =  
      wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault();  
    if (docPackageRelationship != null)  
    {  
        Uri documentUri = PackUriHelper.ResolvePartUri(new Uri("/", UriKind.Relative),  
          docPackageRelationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Load the document XML in the part into an XDocument instance.  
        xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
        //  Find the styles part. There will only be one.  
        PackageRelationship styleRelation =  
          documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault();  
        if (styleRelation != null)  
        {  
            Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
            PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
            //  Load the style XML in the part into an XDocument instance.  
            styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
        }  
    }  
}  
  
string defaultStyle =   
    (string)(  
        from style in styleDoc.Root.Elements(w + "style")  
        where (string)style.Attribute(w + "type") == "paragraph"&&  
              (string)style.Attribute(w + "default") == "1"  
              select style  
    ).First().Attribute(w + "styleId");  
  
// Find all paragraphs in the document.  
var paragraphs =  
    from para in xDoc  
                 .Root  
                 .Element(w + "body")  
                 .Descendants(w + "p")  
    let styleNode = para  
                    .Elements(w + "pPr")  
                    .Elements(w + "pStyle")  
                    .FirstOrDefault()  
    select new  
    {  
        ParagraphNode = para,  
        StyleName = styleNode != null ?  
            (string)styleNode.Attribute(w + "val") :  
            defaultStyle  
    };  
  
// Following is the new query that retrieves the text of  
// each paragraph.  
var paraWithText =  
    from para in paragraphs  
    select new  
    {  
        ParagraphNode = para.ParagraphNode,  
        StyleName = para.StyleName,  
        Text = para  
               .ParagraphNode  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .Aggregate(  
                   new StringBuilder(),  
                   (s, i) => s.Append((string)i),  
                   s => s.ToString()  
               )  
    };  
  
foreach (var p in paraWithText)  
    Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
```  
  
 <span data-ttu-id="ade42-122">当此示例应用于[创建源 Office Open XML 文档 (C#)](./creating-the-source-office-open-xml-document.md) 中说明的文档时，会生成以下输出。</span><span class="sxs-lookup"><span data-stu-id="ade42-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md).</span></span>  
  
```  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a><span data-ttu-id="ade42-123">后续步骤</span><span class="sxs-lookup"><span data-stu-id="ade42-123">Next Steps</span></span>  
 <span data-ttu-id="ade42-124">下面的示例演示如何使用扩展方法而不是 <xref:System.Linq.Enumerable.Aggregate%2A> 将多个字符串串联为一个字符串。</span><span class="sxs-lookup"><span data-stu-id="ade42-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="ade42-125">使用扩展方法重构 (C#)</span><span class="sxs-lookup"><span data-stu-id="ade42-125">Refactoring Using an Extension Method (C#)</span></span>](./refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="ade42-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="ade42-126">See also</span></span>

- [<span data-ttu-id="ade42-127">教程：操作 WordprocessingML 文档中的内容 (C#)</span><span class="sxs-lookup"><span data-stu-id="ade42-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="ade42-128">LINQ to XML 中的延迟执行和迟缓计算 (C#)</span><span class="sxs-lookup"><span data-stu-id="ade42-128">Deferred Execution and Lazy Evaluation in LINQ to XML (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
