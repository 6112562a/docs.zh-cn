---
title: 在 Visual Basic 中操作 XML
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], manipulating XML
- Visual Basic code, XML
- XML [Visual Basic], manipulating
ms.assetid: da32cffb-198d-41b1-9af3-260fe32e3b7d
ms.openlocfilehash: 70ba038a2bdf4bde092ef6beecf32ac9ad5cbba1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506896"
---
# <a name="manipulating-xml-in-visual-basic"></a><span data-ttu-id="af061-102">在 Visual Basic 中操作 XML</span><span class="sxs-lookup"><span data-stu-id="af061-102">Manipulating XML in Visual Basic</span></span>
<span data-ttu-id="af061-103">可以使用*XML 文本*从外部源如字符串、 文件或流加载 XML。</span><span class="sxs-lookup"><span data-stu-id="af061-103">You can use *XML literals* to load XML from an external source such as a string, file, or stream.</span></span> <span data-ttu-id="af061-104">然后，可以使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]操作 XML，并使用[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]查询的 XML。</span><span class="sxs-lookup"><span data-stu-id="af061-104">You can then use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to manipulate the XML and use [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] to query the XML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af061-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="af061-105">In This Section</span></span>  
 [<span data-ttu-id="af061-106">如何：从文件、 字符串或 Stream 加载 XML</span><span class="sxs-lookup"><span data-stu-id="af061-106">How to: Load XML from a File, String, or Stream</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-load-xml-from-a-file-string-or-stream.md)  
 <span data-ttu-id="af061-107">演示如何以 XML 加载到<xref:System.Xml.Linq.XDocument>或<xref:System.Xml.Linq.XElement>从文本文件、 字符串或流的对象。</span><span class="sxs-lookup"><span data-stu-id="af061-107">Demonstrates how to load XML into an <xref:System.Xml.Linq.XDocument> or <xref:System.Xml.Linq.XElement> object from a text file, string, or stream.</span></span>  
  
 [<span data-ttu-id="af061-108">如何：使用 LINQ 转换 XML</span><span class="sxs-lookup"><span data-stu-id="af061-108">How to: Transform XML by Using LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-transform-xml-by-using-linq.md)  
 <span data-ttu-id="af061-109">演示如何将转换的内容<xref:System.Xml.Linq.XDocument>成新的 XML 文档对象。</span><span class="sxs-lookup"><span data-stu-id="af061-109">Demonstrates how to transform the contents of an <xref:System.Xml.Linq.XDocument> object into a new XML document.</span></span>  
  
 [<span data-ttu-id="af061-110">如何：修改 XML 文本</span><span class="sxs-lookup"><span data-stu-id="af061-110">How to: Modify XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-modify-xml-literals.md)  
 <span data-ttu-id="af061-111">演示如何修改元素、 属性和 XML 文本中的值。</span><span class="sxs-lookup"><span data-stu-id="af061-111">Demonstrates how to modify the elements, attributes, and values in an XML literal.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="af061-112">相关章节</span><span class="sxs-lookup"><span data-stu-id="af061-112">Related Sections</span></span>  
 [<span data-ttu-id="af061-113">XML 轴属性</span><span class="sxs-lookup"><span data-stu-id="af061-113">XML Axis Properties</span></span>](../../../../visual-basic/language-reference/xml-axis/index.md)  
 <span data-ttu-id="af061-114">提供指向介绍了各种 XML 访问属性的部分。</span><span class="sxs-lookup"><span data-stu-id="af061-114">Provides links to sections that describe the various XML access properties.</span></span>  
  
 [<span data-ttu-id="af061-115">Visual Basic 中的 LINQ to XML 概述</span><span class="sxs-lookup"><span data-stu-id="af061-115">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 <span data-ttu-id="af061-116">介绍了使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="af061-116">Provides an introduction to using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
 [<span data-ttu-id="af061-117">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="af061-117">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 <span data-ttu-id="af061-118">提供介绍如何在 Visual Basic 中使用 XML 文本。</span><span class="sxs-lookup"><span data-stu-id="af061-118">Provides an introduction to using XML literals in Visual Basic.</span></span>  
  
 [<span data-ttu-id="af061-119">在 Visual Basic 中访问 XML</span><span class="sxs-lookup"><span data-stu-id="af061-119">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 <span data-ttu-id="af061-120">演示如何访问部分的 XML 元素或在 Visual Basic 中的文档。</span><span class="sxs-lookup"><span data-stu-id="af061-120">Demonstrates how to access parts of an XML element or document in Visual Basic.</span></span>  
  
 [<span data-ttu-id="af061-121">XML</span><span class="sxs-lookup"><span data-stu-id="af061-121">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 <span data-ttu-id="af061-122">提供指向介绍如何使用的部分[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]在 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="af061-122">Provides links to sections that describe how to use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af061-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="af061-123">See also</span></span>
- [<span data-ttu-id="af061-124">XML</span><span class="sxs-lookup"><span data-stu-id="af061-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="af061-125">LINQ</span><span class="sxs-lookup"><span data-stu-id="af061-125">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="af061-126">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="af061-126">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
