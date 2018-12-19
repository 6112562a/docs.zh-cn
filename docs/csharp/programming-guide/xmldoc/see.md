---
title: '&lt;see&gt; - C# 编程指南'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 1e799c975fe21dd2dd0354a9d658a271ded5fc2c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235679"
---
# <a name="ltseegt-c-programming-guide"></a>&lt;see&gt;（C# 编程指南）
## <a name="syntax"></a>语法  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>参数  
 cref = " `member`"  
 对可从当前编译环境调用的成员或字段的引用。 编译器检查是否存在给定的码位元素，并将 `member` 传递到输出 XML 中的元素名称。将 member 放在双引号 (" ") 中。  
  
## <a name="remarks"></a>备注  
 通过 \<see> 标记可以从文本内指定链接。 使用 [\<seealso>](../../../csharp/programming-guide/xmldoc/seealso.md) 指示文本应该放在“另请参阅”部分中。 使用 [cref 属性](../../../csharp/programming-guide/xmldoc/cref-attribute.md)创建指向代码元素的文档页的内部超链接。  
  
 使用 [-doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 进行编译以便将文档注释处理到文件中。  
  
 下面的示例展示摘要部分中的 \<see> 标记。  
  
 [!code-csharp[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## <a name="see-also"></a>请参阅

- [C# 编程指南](../../../csharp/programming-guide/index.md)  
- [建议的文档注释标记](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
