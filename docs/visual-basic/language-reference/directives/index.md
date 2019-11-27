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
# <a name="directives-visual-basic"></a>指令 (Visual Basic)

本节中的主题记录 Visual Basic 源代码编译器指令。  
  
## <a name="in-this-section"></a>本节内容  

 [#Const 指令](../../../visual-basic/language-reference/directives/const-directive.md)--定义编译器常量  
  
 [#ExternalSource 指令](../../../visual-basic/language-reference/directives/externalsource-directive.md)--指示源行与源外部的文本之间的映射  
  
 [#If .。。Then ... #Else 指令](../../../visual-basic/language-reference/directives/if-then-else-directives.md)-编译选定的代码块  
  
 [#Region 指令](../../../visual-basic/language-reference/directives/region-directive.md)--折叠和隐藏 Visual Studio 编辑器中的代码段  
  
 **#Disable，#Enable** --针对代码区域禁用和启用特定警告。  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 还可以禁用和启用以逗号分隔的警告代码列表。  
  
## <a name="related-sections"></a>相关章节  

 [Visual Basic 语言参考](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)
