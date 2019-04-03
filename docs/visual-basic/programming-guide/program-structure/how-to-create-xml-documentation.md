---
title: 如何：在 Visual Basic 中创建 XML 文档
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 2f32847c1b3a0fdf1892d6b423bb33783b6bdfe3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814583"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a><span data-ttu-id="a9e56-102">如何：在 Visual Basic 中创建 XML 文档</span><span class="sxs-lookup"><span data-stu-id="a9e56-102">How to: Create XML Documentation in Visual Basic</span></span>
<span data-ttu-id="a9e56-103">此示例演示如何将 XML 文档注释添加到你的代码。</span><span class="sxs-lookup"><span data-stu-id="a9e56-103">This example shows how to add XML documentation comments to your code.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a><span data-ttu-id="a9e56-104">若要创建的类型或成员的 XML 文档</span><span class="sxs-lookup"><span data-stu-id="a9e56-104">To create XML documentation for a type or member</span></span>  
  
1.  <span data-ttu-id="a9e56-105">在中**代码编辑器**，将光标放置在你想要创建文档的类型或成员上面的行上。</span><span class="sxs-lookup"><span data-stu-id="a9e56-105">In the **Code Editor**, position your cursor on the line above the type or member for which you want to create documentation.</span></span>  
  
2.  <span data-ttu-id="a9e56-106">类型`'''`（三个非单引号）。</span><span class="sxs-lookup"><span data-stu-id="a9e56-106">Type `'''` (three single-quotation marks).</span></span>  
  
     <span data-ttu-id="a9e56-107">在添加对类型或成员的 XML 主干**代码编辑器**。</span><span class="sxs-lookup"><span data-stu-id="a9e56-107">An XML skeleton for the type or member is added in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="a9e56-108">添加相应的标记之间的描述性信息。</span><span class="sxs-lookup"><span data-stu-id="a9e56-108">Add descriptive information between the appropriate tags.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9e56-109">如果添加 XML 文档块中的其他行，每行必须以`'''`。</span><span class="sxs-lookup"><span data-stu-id="a9e56-109">If you add additional lines within the XML documentation block, each line must begin with `'''`.</span></span>  
  
4.  <span data-ttu-id="a9e56-110">添加新的 XML 文档注释中使用的类型或成员的其他代码。</span><span class="sxs-lookup"><span data-stu-id="a9e56-110">Add additional code that uses the type or member with the new XML documentation comments.</span></span>  
  
     <span data-ttu-id="a9e56-111">IntelliSense 将显示从文本\<摘要 > 标记的类型或成员。</span><span class="sxs-lookup"><span data-stu-id="a9e56-111">IntelliSense displays the text from the \<summary> tag for the type or member.</span></span>  
  
5.  <span data-ttu-id="a9e56-112">编译代码，生成包含文档注释的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="a9e56-112">Compile the code to generate an XML file containing the documentation comments.</span></span> <span data-ttu-id="a9e56-113">有关详细信息，请参阅 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。</span><span class="sxs-lookup"><span data-stu-id="a9e56-113">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9e56-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="a9e56-114">See also</span></span>

- [<span data-ttu-id="a9e56-115">使用 XML 记录代码</span><span class="sxs-lookup"><span data-stu-id="a9e56-115">Documenting Your Code with XML</span></span>](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [<span data-ttu-id="a9e56-116">XML 注释标记</span><span class="sxs-lookup"><span data-stu-id="a9e56-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
- [<span data-ttu-id="a9e56-117">/doc</span><span class="sxs-lookup"><span data-stu-id="a9e56-117">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)
