---
title: '&lt;list&gt; - C# 编程指南'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: b960349d26a4addb5f4723bd7aa3f19b07e5f4d2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241543"
---
# <a name="ltlistgt-c-programming-guide"></a>&lt;列表&gt;（C# 编程指南）
## <a name="syntax"></a>语法  
  
```xml  
<list type="bullet" | "number" | "table">  
    <listheader>  
        <term>term</term>  
        <description>description</description>  
    </listheader>  
    <item>  
        <term>term</term>  
        <description>description</description>  
    </item>  
</list>  
```  
  
#### <a name="parameters"></a>参数  
 `term`  
 要定义的术语，将在 `description` 中进行定义。  
  
 `description`  
 项目符号或编号列表中的项或 `term` 的定义。  
  
## <a name="remarks"></a>备注  
 \<listheader> 块用于定义表或定义列表的标题行。 定义表时，只需提供标题中的术语的项。  
  
 列表中的每个项均使用 \<item> 块指定。 创建定义列表时，需要同时指定 `term` 和 `description`。 但是，对于表、项目符号列表或编号列表，只需提供 `description` 的项。  
  
 列表或表可根据需要具有多个 \<item> 块。  
  
 使用 [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 进行编译可以将文档注释处理到文件中。  
  
## <a name="example"></a>示例  
 [!code-csharp[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## <a name="see-also"></a>请参阅

- [C# 编程指南](../../../csharp/programming-guide/index.md)  
- [建议的文档注释标记](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
