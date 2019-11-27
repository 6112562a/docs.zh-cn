---
title: '#Region 指令'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: 4cf9b103486378d001b588aa285f590980b51bb8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343791"
---
# <a name="region-directive"></a><span data-ttu-id="e3274-102">#Region 指令</span><span class="sxs-lookup"><span data-stu-id="e3274-102">#Region Directive</span></span>

<span data-ttu-id="e3274-103">折叠并隐藏 Visual Basic 文件中的代码段。</span><span class="sxs-lookup"><span data-stu-id="e3274-103">Collapses and hides sections of code in Visual Basic files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3274-104">语法</span><span class="sxs-lookup"><span data-stu-id="e3274-104">Syntax</span></span>  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a><span data-ttu-id="e3274-105">部件</span><span class="sxs-lookup"><span data-stu-id="e3274-105">Parts</span></span>  
  
|<span data-ttu-id="e3274-106">术语</span><span class="sxs-lookup"><span data-stu-id="e3274-106">Term</span></span>|<span data-ttu-id="e3274-107">Definition</span><span class="sxs-lookup"><span data-stu-id="e3274-107">Definition</span></span>|  
|---|---|  
|`identifier_string`|<span data-ttu-id="e3274-108">必需。</span><span class="sxs-lookup"><span data-stu-id="e3274-108">Required.</span></span> <span data-ttu-id="e3274-109">当区域处于折叠状态时充当区域标题的字符串。</span><span class="sxs-lookup"><span data-stu-id="e3274-109">String that acts as the title of a region when it is collapsed.</span></span> <span data-ttu-id="e3274-110">默认情况下，区域处于折叠状态。</span><span class="sxs-lookup"><span data-stu-id="e3274-110">Regions are collapsed by default.</span></span>|  
|`#End Region`|<span data-ttu-id="e3274-111">终止 `#Region` 块。</span><span class="sxs-lookup"><span data-stu-id="e3274-111">Terminates the `#Region` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3274-112">备注</span><span class="sxs-lookup"><span data-stu-id="e3274-112">Remarks</span></span>  

 <span data-ttu-id="e3274-113">使用 `#Region` 指令指定使用 Visual Studio Code 编辑器的大纲显示功能时要展开或折叠的代码块。</span><span class="sxs-lookup"><span data-stu-id="e3274-113">Use the `#Region` directive to specify a block of code to expand or collapse when using the outlining feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="e3274-114">您可以在其他区域中放置或*嵌套*区域，以将类似区域组合在一起。</span><span class="sxs-lookup"><span data-stu-id="e3274-114">You can place, or *nest*, regions within other regions to group similar regions together.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3274-115">示例</span><span class="sxs-lookup"><span data-stu-id="e3274-115">Example</span></span>  

 <span data-ttu-id="e3274-116">此示例使用 `#Region` 指令。</span><span class="sxs-lookup"><span data-stu-id="e3274-116">This example uses the `#Region` directive.</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e3274-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e3274-117">See also</span></span>

- [<span data-ttu-id="e3274-118">#If...Then...#Else 指令</span><span class="sxs-lookup"><span data-stu-id="e3274-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="e3274-119">大纲显示</span><span class="sxs-lookup"><span data-stu-id="e3274-119">Outlining</span></span>](/visualstudio/ide/outlining)
- [<span data-ttu-id="e3274-120">如何：折叠和隐藏代码节</span><span class="sxs-lookup"><span data-stu-id="e3274-120">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
