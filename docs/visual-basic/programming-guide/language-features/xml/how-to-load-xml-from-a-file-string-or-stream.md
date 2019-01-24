---
title: 如何：从文件、 字符串或 Stream (Visual Basic) 加载 XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], loading
- LINQ to XML [Visual Basic], loading XML from files
ms.assetid: 2b02dcec-4cca-4575-b4ad-89ceb87b984c
ms.openlocfilehash: b660900c1ac29e40eeed36b1e07326dfbcf69ec8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492736"
---
# <a name="how-to-load-xml-from-a-file-string-or-stream-visual-basic"></a><span data-ttu-id="16593-102">如何：从文件、 字符串或 Stream (Visual Basic) 加载 XML</span><span class="sxs-lookup"><span data-stu-id="16593-102">How to: Load XML from a File, String, or Stream (Visual Basic)</span></span>
<span data-ttu-id="16593-103">您可以创建[XML 文本](../../../../visual-basic/language-reference/xml-literals/index.md)和通过使用几种方法使用从外部源如文件、 字符串或流的内容填充它们。</span><span class="sxs-lookup"><span data-stu-id="16593-103">You can create [XML Literals](../../../../visual-basic/language-reference/xml-literals/index.md) and populate them with the contents from an external source such as a file, a string, or a stream by using several methods.</span></span> <span data-ttu-id="16593-104">以下示例中显示了这些方法。</span><span class="sxs-lookup"><span data-stu-id="16593-104">These methods are shown in the following examples.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-load-xml-from-a-file"></a><span data-ttu-id="16593-105">若要从文件加载 XML</span><span class="sxs-lookup"><span data-stu-id="16593-105">To load XML from a file</span></span>  
  
-   <span data-ttu-id="16593-106">填充 XML 文本，如<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>对象从一个文件，使用`Load`方法。</span><span class="sxs-lookup"><span data-stu-id="16593-106">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a file, use the `Load` method.</span></span> <span data-ttu-id="16593-107">此方法可以将文件路径、 文本流或 XML 流作为输入。</span><span class="sxs-lookup"><span data-stu-id="16593-107">This method can take a file path, text stream, or XML stream as input.</span></span>  
  
     <span data-ttu-id="16593-108">下面的代码示例演示如何使用<xref:System.Xml.Linq.XDocument.Load%28System.String%29>方法来填充<xref:System.Xml.Linq.XDocument>使用 XML 文本文件中的对象。</span><span class="sxs-lookup"><span data-stu-id="16593-108">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Load%28System.String%29> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a text file.</span></span>  
  
     [!code-vb[VbXMLSamples#43](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_1.vb)]  
  
### <a name="to-load-xml-from-a-string"></a><span data-ttu-id="16593-109">若要从字符串加载 XML</span><span class="sxs-lookup"><span data-stu-id="16593-109">To load XML from a string</span></span>  
  
-   <span data-ttu-id="16593-110">填充 XML 文本，如<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>对象从一个字符串，可以使用`Parse`方法。</span><span class="sxs-lookup"><span data-stu-id="16593-110">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a string, you can use the `Parse` method.</span></span>  
  
     <span data-ttu-id="16593-111">下面的代码示例演示如何使用<xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType>方法来填充<xref:System.Xml.Linq.XDocument>使用 XML 字符串中的对象。</span><span class="sxs-lookup"><span data-stu-id="16593-111">The following code example shows the use of the <xref:System.Xml.Linq.XDocument.Parse%28System.String%29?displayProperty=nameWithType> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from a string.</span></span>  
  
     [!code-vb[VbXMLSamples#47](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_2.vb)]  
  
### <a name="to-load-xml-from-a-stream"></a><span data-ttu-id="16593-112">若要从流加载 XML</span><span class="sxs-lookup"><span data-stu-id="16593-112">To load XML from a stream</span></span>  
  
-   <span data-ttu-id="16593-113">填充 XML 文本，如<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>对象从流中，可以使用`Load`方法或<xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="16593-113">To populate an XML literal such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object from a stream, you can use the `Load` method or the <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="16593-114">下面的代码示例演示如何使用<xref:System.Xml.Linq.XNode.ReadFrom%2A>方法来填充<xref:System.Xml.Linq.XDocument>对象与 XML 从 XML 流。</span><span class="sxs-lookup"><span data-stu-id="16593-114">The following code example shows the use of the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method to populate an <xref:System.Xml.Linq.XDocument> object with XML from an XML stream.</span></span>  
  
 [!code-vb[VbXMLSamples#46](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-load-xml-from-a-file-string-or-stream_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="16593-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="16593-115">See also</span></span>
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.ReadFrom%2A?displayProperty=nameWithType>
- [<span data-ttu-id="16593-116">XML 文本</span><span class="sxs-lookup"><span data-stu-id="16593-116">XML Literals</span></span>](../../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="16593-117">XML</span><span class="sxs-lookup"><span data-stu-id="16593-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="16593-118">在 Visual Basic 中操控 XML</span><span class="sxs-lookup"><span data-stu-id="16593-118">Manipulating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/manipulating-xml.md)
