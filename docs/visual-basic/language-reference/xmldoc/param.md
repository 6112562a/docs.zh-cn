---
title: '&lt;param&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: cc9ceccef8123d49d6267276e9dcb7be84f78a01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670675"
---
# <a name="ltparamgt-visual-basic"></a>&lt;param&gt; (Visual Basic)
定义的参数名称和说明。  
  
## <a name="syntax"></a>语法  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>参数  
 `name`  
 方法参数的名称。 用双引号 (" ") 将名称引起来。  
  
 `description`  
 参数的说明。  
  
## <a name="remarks"></a>备注  
 `<param>`标记应使用方法声明的注释，以描述一个方法的参数。  
  
 文本`<param>`标记将出现在以下位置：  
  
-   参数的 IntelliSense 信息。 有关详细信息，请参阅[使用 IntelliSense](/visualstudio/ide/using-intellisense)。  
  
-   对象浏览器。 有关详细信息，请参阅[查看代码的结构](/visualstudio/ide/viewing-the-structure-of-code)。  
  
 使用 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 进行编译可以将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 此示例使用`<param>`标记来描述`id`参数。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a>请参阅
- [XML 注释标记](../../../visual-basic/language-reference/xmldoc/index.md)
