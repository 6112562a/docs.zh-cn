---
title: WordprocessingML 文档的形状 (C#)
ms.date: 07/20/2015
ms.assetid: 3791b5e0-c502-469b-bb75-a7bf6fdd0a94
ms.openlocfilehash: 58c028fed465f45fdcf8f63f2119eb8e8b201e32
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732676"
---
# <a name="shape-of-wordprocessingml-documents-c"></a><span data-ttu-id="f2ab3-102">WordprocessingML 文档的形状 (C#)</span><span class="sxs-lookup"><span data-stu-id="f2ab3-102">Shape of WordprocessingML Documents (C#)</span></span>
<span data-ttu-id="f2ab3-103">本主题介绍 WordprocessingML 文档的 XML 形状。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-103">This topic introduces the XML shape of a WordprocessingML document.</span></span>  
  
## <a name="microsoft-office-formats"></a><span data-ttu-id="f2ab3-104">Microsoft Office 格式</span><span class="sxs-lookup"><span data-stu-id="f2ab3-104">Microsoft Office Formats</span></span>  
 <span data-ttu-id="f2ab3-105">2007 Microsoft Office 系统的本机文件格式为 Office Open XML（通常称为 Open XML）。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-105">The native file format for the 2007 Microsoft Office system is Office Open XML (commonly called Open XML).</span></span> <span data-ttu-id="f2ab3-106">Open XML 是一种基于 XML 的格式（Ecma 标准），当前即将通过 ISO-IEC 标准流程。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-106">Open XML is an XML-based format that an Ecma standard and is currently going through the ISO-IEC standards process.</span></span> <span data-ttu-id="f2ab3-107">Open XML 中用于文字处理文件的标记语言称为 WordprocessingML。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-107">The markup language for word processing files within Open XML is called WordprocessingML.</span></span> <span data-ttu-id="f2ab3-108">本教程使用 WordprocessingML 源文件作为示例的输入。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-108">This tutorial uses WordprocessingML source files as input for the examples.</span></span>  
  
 <span data-ttu-id="f2ab3-109">如果使用 Microsoft Office 2003，则在已安装适用于 Word、Excel 和 PowerPoint 2007 文件格式的 Microsoft Office 兼容包的情况下，可以将文档保存为 Office Open XML 格式。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-109">If you are using Microsoft Office 2003, you can save documents in the Office Open XML format if you have installed the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="the-shape-of-wordprocessingml-documents"></a><span data-ttu-id="f2ab3-110">WordprocessingML 文档的形状</span><span class="sxs-lookup"><span data-stu-id="f2ab3-110">The Shape of WordprocessingML Documents</span></span>  
 <span data-ttu-id="f2ab3-111">首先要了解的是 WordprocessingML 文档的形状。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-111">The first thing to understand is the shape of WordprocessingML documents.</span></span> <span data-ttu-id="f2ab3-112">WordprocessingML 文档包含一个正文元素（称为 `w:body`），该元素包含文档的各个段落。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-112">A WordprocessingML document contains a body element (named `w:body`) that contains the paragraphs of the document.</span></span> <span data-ttu-id="f2ab3-113">每个段落包含一个或多个文本域（称为 `w:r`）。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-113">Each paragraph contains one or more text runs (named `w:r`).</span></span> <span data-ttu-id="f2ab3-114">每个文本域包含一个或多个文本块（称为 `w:t`）。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-114">Each text run contains one or more text pieces (named `w:t`).</span></span>  
  
 <span data-ttu-id="f2ab3-115">下面是一个非常简单的 WordprocessingML 文档：</span><span class="sxs-lookup"><span data-stu-id="f2ab3-115">The following is a very simple WordprocessingML document:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<w:document  
xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
xmlns:o="urn:schemas-microsoft-com:office:office"  
xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
xmlns:v="urn:schemas-microsoft-com:vml"  
xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
xmlns:w10="urn:schemas-microsoft-com:office:word"  
xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is a paragraph.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00E22EB6"  
         w:rsidRDefault="00E22EB6">  
      <w:r>  
        <w:t>This is another paragraph.</w:t>  
      </w:r>  
    </w:p>  
  </w:body>  
</w:document>  
```  
  
 <span data-ttu-id="f2ab3-116">此文档包含两个段落。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-116">This document contains two paragraphs.</span></span> <span data-ttu-id="f2ab3-117">这两个段落都包含单个文本域，每个文本域都包含单个文本块。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-117">They both contain a single text run, and each text run contains a single text piece.</span></span>  
  
 <span data-ttu-id="f2ab3-118">查看 XML 格式的 WordprocessingML 文档内容的最简单方式是使用 Microsoft Word 创建一个 XML 文档，保存该文档，然后运行下面的程序，将该 XML 打印到控制台。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-118">The easiest way to see the contents of a WordprocessingML document in XML form is to create one using Microsoft Word, save it, and then run the following program that prints the XML to the console.</span></span>  
  
 <span data-ttu-id="f2ab3-119">本示例使用 WindowsBase 程序集中的类。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-119">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="f2ab3-120">它使用 <xref:System.IO.Packaging?displayProperty=nameWithType> 命名空间中的类型。</span><span class="sxs-lookup"><span data-stu-id="f2ab3-120">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
const string documentRelationshipType =  
  "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
const string wordmlNamespace =  
  "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
XNamespace w = wordmlNamespace;  
  
using (Package wdPackage = Package.Open("SampleDoc.docx", FileMode.Open, FileAccess.Read))  
{  
    PackageRelationship relationship =  
        wdPackage  
        .GetRelationshipsByType(documentRelationshipType)  
        .FirstOrDefault();  
    if (relationship != null)  
    {  
        Uri documentUri =  
            PackUriHelper.ResolvePartUri(  
                new Uri("/", UriKind.Relative),  
                relationship.TargetUri);  
        PackagePart documentPart = wdPackage.GetPart(documentUri);  
  
        //  Get the officeDocument part from the package.  
        //  Load the XML in the part into an XDocument instance.  
        XDocument xdoc =  
            XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
        Console.WriteLine(xdoc.Root);  
    }  
}  
```  
  
## <a name="external-resources"></a><span data-ttu-id="f2ab3-121">外部资源</span><span class="sxs-lookup"><span data-stu-id="f2ab3-121">External resources</span></span>

- [<span data-ttu-id="f2ab3-122">介绍 Office (2007) Open XML 文件格式</span><span class="sxs-lookup"><span data-stu-id="f2ab3-122">Introducing the Office (2007) Open XML File Formats</span></span>](https://docs.microsoft.com/previous-versions/office/developer/office-2007/aa338205%28v=office.12%29)
- <span data-ttu-id="f2ab3-123">[Overview of WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)（WordprocessingML 概述）</span><span class="sxs-lookup"><span data-stu-id="f2ab3-123">[Overview of WordprocessingML](https://docs.microsoft.com/previous-versions/office/developer/office-2003/aa212812%28v=office.11%29)</span></span>
- [<span data-ttu-id="f2ab3-124">WordProcessingML 文件剖析</span><span class="sxs-lookup"><span data-stu-id="f2ab3-124">Anatomy of a WordProcessingML File</span></span>](http://officeopenxml.com/anatomyofOOXML.php)
- [<span data-ttu-id="f2ab3-125">WordprocessingML 简介</span><span class="sxs-lookup"><span data-stu-id="f2ab3-125">Introduction to WordprocessingML</span></span>](https://ericwhite.com/blog/introduction-to-wordprocessingml-series/)

## <a name="see-also"></a><span data-ttu-id="f2ab3-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="f2ab3-126">See also</span></span>

- [<span data-ttu-id="f2ab3-127">教程：操作 WordprocessingML 文档中的内容 (C#)</span><span class="sxs-lookup"><span data-stu-id="f2ab3-127">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](./shape-of-wordprocessingml-documents.md)
