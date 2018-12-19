---
title: '[] 运算符 - C# 参考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 3e2ce5c4b74cbf79e00410791ffcc31368f78648
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243993"
---
# <a name="-operator-c-reference"></a>[] 运算符（C# 参考）
方括号 (`[]`) 可用于数组、索引器和属性。 还可用于指针。  
  
## <a name="remarks"></a>备注  
 数组类型是后接 `[]` 的类型：  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 若要访问数组的元素，请使用方括号将所需元素的索引括起来：  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 如果数组索引超出范围，则会引发异常。  
  
 不能重载数组索引运算符；但类型可以定义采用一个或多个参数的索引器。 索引器参数括在方括号内，这一点与数组索引类似，但可以将索引器参数声明为任何类型，这一点与数组索引不同，后者必须为整型。  
  
 例如，.NET Framework 定义 `Hashtable` 类型，该类型将任意类型的键和值关联在一起：  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 方括号还用于指定[属性](../../../csharp/programming-guide/concepts/attributes/index.md)：  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 可以使用方括号来指定指针索引：  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 不执行边界检查。  
  
## <a name="c-language-specification"></a>C# 语言规范  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>请参阅

- [C# 参考](../../../csharp/language-reference/index.md)  
- [C# 编程指南](../../../csharp/programming-guide/index.md)  
- [C# 运算符](../../../csharp/language-reference/operators/index.md)  
- [数组](../../../csharp/programming-guide/arrays/index.md)  
- [索引器](../../../csharp/programming-guide/indexers/index.md)  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
- [fixed 语句](../../../csharp/language-reference/keywords/fixed-statement.md)
