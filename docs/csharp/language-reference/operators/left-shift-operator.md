---
title: '&lt;&lt; 运算符 - C# 参考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: bd52d86c6ab84364d242e594054cfdd03dcc7e66
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241731"
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt; 运算符（C# 参考）
左移运算符 (`<<`) 将第一个操作数向左移动第二个操作数指定的位数。 第二个操作数的类型必须为 [int](../../../csharp/language-reference/keywords/int.md) 或预定义隐式数值转换为 `int` 的类型。  
  
## <a name="remarks"></a>备注  
 如果第一个操作数是 [int](../../../csharp/language-reference/keywords/int.md) 或 [uint](../../../csharp/language-reference/keywords/uint.md)（32 位数），则移位计数由第二个操作数的低序五位给定。 也就是说，实际的移位计数为 0 到 31 位。  
  
 如果第一个操作数是 [long](../../../csharp/language-reference/keywords/long.md) 或 [ulong](../../../csharp/language-reference/keywords/ulong.md)（64 位数），则移位计数由第二个操作数的低序六位给定。 也就是说，实际的移位计数为 0 到 63 位。  
  
 将丢弃移位后不在第一个操作数类型范围内的任何高序位，低序空位补零。 移位操作从不导致溢位。  
  
 用户定义的类型可以重载 `<<` 运算符（参阅[运算符](../../../csharp/language-reference/keywords/operator.md)）；第一个操作数的类型必须是用户定义的类型，第二个操作数的类型必须是 `int`。 重载二元运算符时，也会隐式重载相应的赋值运算符（若有）。  
  
## <a name="example"></a>示例  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a>注释  
 请注意，`i<<1` 和 `i<<33` 的结果相同，因为 1 和 33 的低序五位相同。  
  
## <a name="see-also"></a>请参阅

- [C# 参考](../../../csharp/language-reference/index.md)  
- [C# 编程指南](../../../csharp/programming-guide/index.md)  
- [C# 运算符](../../../csharp/language-reference/operators/index.md)
