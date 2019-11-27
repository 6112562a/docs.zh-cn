---
title: 指令
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: d76e10ad5ce8ad3accdc84f97146e0816048d8f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343804"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="85013-102">指令 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85013-102">Directives (Visual Basic)</span></span>

<span data-ttu-id="85013-103">本节中的主题记录 Visual Basic 源代码编译器指令。</span><span class="sxs-lookup"><span data-stu-id="85013-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="85013-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="85013-104">In This Section</span></span>  

 <span data-ttu-id="85013-105">[#Const 指令](../../../visual-basic/language-reference/directives/const-directive.md)--定义编译器常量</span><span class="sxs-lookup"><span data-stu-id="85013-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="85013-106">[#ExternalSource 指令](../../../visual-basic/language-reference/directives/externalsource-directive.md)--指示源行与源外部的文本之间的映射</span><span class="sxs-lookup"><span data-stu-id="85013-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="85013-107">[#If .。。Then ... #Else 指令](../../../visual-basic/language-reference/directives/if-then-else-directives.md)-编译选定的代码块</span><span class="sxs-lookup"><span data-stu-id="85013-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="85013-108">[#Region 指令](../../../visual-basic/language-reference/directives/region-directive.md)--折叠和隐藏 Visual Studio 编辑器中的代码段</span><span class="sxs-lookup"><span data-stu-id="85013-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="85013-109">**#Disable，#Enable** --针对代码区域禁用和启用特定警告。</span><span class="sxs-lookup"><span data-stu-id="85013-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="85013-110">还可以禁用和启用以逗号分隔的警告代码列表。</span><span class="sxs-lookup"><span data-stu-id="85013-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="85013-111">相关章节</span><span class="sxs-lookup"><span data-stu-id="85013-111">Related Sections</span></span>  

 [<span data-ttu-id="85013-112">Visual Basic 语言参考</span><span class="sxs-lookup"><span data-stu-id="85013-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="85013-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85013-113">Visual Basic</span></span>](../../../visual-basic/index.md)
