---
title: '&lt;= 运算符 - C# 参考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
ms.openlocfilehash: 950ba3fc02e015f2574d123d1fd9adc116aae045
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243447"
---
# <a name="lt-operator-c-reference"></a>&lt;= 运算符（C# 参考）
所有数值和枚举类型定义“小于或等于”关系运算符 (`<=`)，如果第一个操作数小于或等于第二个操作数，此运算符返回 `true`，否则返回 `false`。  
  
## <a name="remarks"></a>备注  
 用户定义的类型可以重载 `<=` 运算符。 有关详细信息，请参阅[运算符](../../../csharp/language-reference/keywords/operator.md)。 如果已重载 `<=`，则必须同时重载 [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md)。 对整数类型的操作通常可用于枚举。  
  
## <a name="example"></a>示例  
 [!code-csharp[csRefOperators#32](../../../csharp/language-reference/operators/codesnippet/CSharp/less-than-equal-operator_1.cs)]  
  
## <a name="see-also"></a>请参阅

- [C# 参考](../../../csharp/language-reference/index.md)  
- [C# 编程指南](../../../csharp/programming-guide/index.md)  
- [C# 运算符](../../../csharp/language-reference/operators/index.md)  
- [explicit](../../../csharp/language-reference/keywords/explicit.md)
