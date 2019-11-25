---
title: 分析 XML
ms.date: 07/20/2015
ms.assetid: 5bcbd7e2-d9f1-4c8f-80d6-39915fe17bd1
ms.openlocfilehash: 49e77c4f4df27daa96eba4f7a8aa161a667b7271
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353170"
---
# <a name="parsing-xml-visual-basic"></a><span data-ttu-id="8a055-102">Parsing XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a055-102">Parsing XML (Visual Basic)</span></span>
<span data-ttu-id="8a055-103">本节中的主题介绍如何分析 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="8a055-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a055-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="8a055-104">In This Section</span></span>  
  
|<span data-ttu-id="8a055-105">主题</span><span class="sxs-lookup"><span data-stu-id="8a055-105">Topic</span></span>|<span data-ttu-id="8a055-106">描述</span><span class="sxs-lookup"><span data-stu-id="8a055-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="8a055-107">How to: Parse a String (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a055-107">How to: Parse a String (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-parse-a-string.md)|<span data-ttu-id="8a055-108">演示如何分析字符串从而创建 XML 树。</span><span class="sxs-lookup"><span data-stu-id="8a055-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="8a055-109">How to: Load XML from a File (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a055-109">How to: Load XML from a File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md)|<span data-ttu-id="8a055-110">演示如何使用 <xref:System.Xml.Linq.XElement.Load%2A> 方法从 URI 加载 XML。</span><span class="sxs-lookup"><span data-stu-id="8a055-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="8a055-111">在加载或分析 XML 时保留空白</span><span class="sxs-lookup"><span data-stu-id="8a055-111">Preserving White Space while Loading or Parsing XML</span></span>](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-loading-or-parsing-xml.md)|<span data-ttu-id="8a055-112">介绍如何在加载 XML 树时控制 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 的空白行为。</span><span class="sxs-lookup"><span data-stu-id="8a055-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="8a055-113">How to: Catch Parsing Errors (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a055-113">How to: Catch Parsing Errors (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-catch-parsing-errors.md)|<span data-ttu-id="8a055-114">演示如何检测格式不正确或无效的 XML。</span><span class="sxs-lookup"><span data-stu-id="8a055-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="8a055-115">How to: Create a Tree from an XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a055-115">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="8a055-116">演示如何从 <xref:System.Xml.XmlReader> 直接创建 XML 树。</span><span class="sxs-lookup"><span data-stu-id="8a055-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="8a055-117">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a055-117">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="8a055-118">演示如何使用 <xref:System.Xml.XmlReader> 对 XML 片段进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="8a055-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="8a055-119">如果必须处理很大的 XML 文件，将整个 XML 树加载到内存可能不可行。</span><span class="sxs-lookup"><span data-stu-id="8a055-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="8a055-120">这时，可以对 XML 片段进行流式处理。</span><span class="sxs-lookup"><span data-stu-id="8a055-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8a055-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="8a055-121">See also</span></span>

- [<span data-ttu-id="8a055-122">Creating XML Trees (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a055-122">Creating XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
