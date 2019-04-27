---
title: 创建源 Office Open XML 文档 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 61ccd6fb-0c47-4075-afdf-5b5021330f21
ms.openlocfilehash: 83cb7d0a325e11c9669f1331e57bed7bf09f27c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923417"
---
# <a name="creating-the-source-office-open-xml-document-visual-basic"></a><span data-ttu-id="e604b-102">创建源 Office Open XML 文档 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e604b-102">Creating the Source Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="e604b-103">本主题演示如何创建本教程其他示例中使用的 Office Open XML WordprocessingML 文档。</span><span class="sxs-lookup"><span data-stu-id="e604b-103">This topic shows how to create the Office Open XML WordprocessingML document that the other examples in this tutorial use.</span></span> <span data-ttu-id="e604b-104">如果您按照这些说明操作，您的输出结果将与每个示例中提供的输出相匹配。</span><span class="sxs-lookup"><span data-stu-id="e604b-104">If you follow these instructions, your output will match the output provided in each example.</span></span>  
  
 <span data-ttu-id="e604b-105">不过，本教程中的示例可以使用任何有效的 WordprocessingML 文档。</span><span class="sxs-lookup"><span data-stu-id="e604b-105">However, the examples in this tutorial will work with any valid WordprocessingML document.</span></span>  
  
 <span data-ttu-id="e604b-106">若要创建本教程使用的文档，必须安装 Microsoft Office 2007 或更高版本，或者具有 Microsoft Office Word、Excel 和 PowerPoint 2007 文件格式兼容包的 Microsoft Office 2003。</span><span class="sxs-lookup"><span data-stu-id="e604b-106">To create the document that this tutorial uses, you must either have Microsoft Office 2007 or later installed, or you must have Microsoft Office 2003 with the Microsoft Office Compatibility Pack for Word, Excel, and PowerPoint 2007 File Formats.</span></span>  
  
## <a name="creating-the-wordprocessingml-document"></a><span data-ttu-id="e604b-107">创建 WordprocessingML 文档</span><span class="sxs-lookup"><span data-stu-id="e604b-107">Creating the WordprocessingML Document</span></span>  
  
#### <a name="to-create-the-wordprocessingml-document"></a><span data-ttu-id="e604b-108">创建 WordprocessingML 文档</span><span class="sxs-lookup"><span data-stu-id="e604b-108">To create the WordprocessingML document</span></span>  
  
1. <span data-ttu-id="e604b-109">创建一个新的 Microsoft Word 文档。</span><span class="sxs-lookup"><span data-stu-id="e604b-109">Create a new Microsoft Word document.</span></span>  
  
2. <span data-ttu-id="e604b-110">将以下文本粘贴到新文档中：</span><span class="sxs-lookup"><span data-stu-id="e604b-110">Paste the following text into the new document:</span></span>  
  
    ```  
    Parsing WordprocessingML with LINQ to XML  
  
    The following example prints to the console.  
  
    Imports System  
  
    Class Program  
        Public Shared  Sub Main(ByVal args() As String)  
            Console.WriteLine("Hello World")  
        End Sub  
    End Class  
  
    This example produces the following output:  
  
    Hello World  
    ```  
  
3. <span data-ttu-id="e604b-111">用“标题 1”样式格式化第一行。</span><span class="sxs-lookup"><span data-stu-id="e604b-111">Format the first line with the style "Heading 1".</span></span>  
  
4. <span data-ttu-id="e604b-112">选择包含 Visual Basic 代码的行。</span><span class="sxs-lookup"><span data-stu-id="e604b-112">Select the lines that contain the Visual Basic code.</span></span> <span data-ttu-id="e604b-113">第一行以 `Imports` 关键字开头。</span><span class="sxs-lookup"><span data-stu-id="e604b-113">The first line starts with the `Imports` keyword.</span></span> <span data-ttu-id="e604b-114">最后一行是"End Class"。</span><span class="sxs-lookup"><span data-stu-id="e604b-114">The last line is "End Class".</span></span> <span data-ttu-id="e604b-115">用 courier 字体格式化这些行。</span><span class="sxs-lookup"><span data-stu-id="e604b-115">Format the lines with the courier font.</span></span> <span data-ttu-id="e604b-116">用新样式格式化这些行并将新样式命名为“Code”。</span><span class="sxs-lookup"><span data-stu-id="e604b-116">Format them with a new style, and name the new style "Code".</span></span>  
  
5. <span data-ttu-id="e604b-117">最后，选择包含输出的整个行，并用 `Code` 样式格式化该行。</span><span class="sxs-lookup"><span data-stu-id="e604b-117">Finally, select the entire line that contains the output, and format it with the `Code` style.</span></span>  
  
6. <span data-ttu-id="e604b-118">保存文档，并将其命名为 SampleDoc.docx。</span><span class="sxs-lookup"><span data-stu-id="e604b-118">Save the document, and name it SampleDoc.docx.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e604b-119">如果使用的是 Microsoft Word 2003，请在“保存类型”下拉列表中选择“Word 2007 文档”。</span><span class="sxs-lookup"><span data-stu-id="e604b-119">If you are using Microsoft Word 2003, select **Word 2007 Document** in the **Save as Type** drop-down list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e604b-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="e604b-120">See also</span></span>

- [<span data-ttu-id="e604b-121">教程：操作 WordprocessingML 文档 (Visual Basic 中) 中的内容</span><span class="sxs-lookup"><span data-stu-id="e604b-121">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
