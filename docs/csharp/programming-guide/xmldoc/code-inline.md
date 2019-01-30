---
title: '&lt;c&gt; - C# 编程指南'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: b789b95c5e23534fb36613ac9203f146b265a98d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54640974"
---
# <a name="ltcgt-c-programming-guide"></a>&lt;c&gt;（C# 编程指南）
## <a name="syntax"></a>语法  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a>参数  
 `text`  
 要指示为代码的文本。  
  
## <a name="remarks"></a>备注  
 使用 \<c> 标记可以指示应将说明内的文本标记为代码。 使用 [\<code>](../../../csharp/programming-guide/xmldoc/code.md) 指示作为代码的多行文本。  
  
 使用 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 进行编译可以将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 [!code-csharp[csProgGuideDocComments#2](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/code-inline_1.cs)]  
  
## <a name="see-also"></a>请参阅

- [C# 编程指南](../../../csharp/programming-guide/index.md)
- [建议的文档注释标记](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
