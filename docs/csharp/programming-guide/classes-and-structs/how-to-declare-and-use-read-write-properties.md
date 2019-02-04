---
title: 如何：声明和使用读/写属性 - C# 编程指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 792c3a8f1b02f36775edb84bdf7f1ff296630fea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725280"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a>如何：声明和使用读/写属性（C# 编程指南）
属性提供了公共数据成员的便利性，且不会产生未受保护、不可控制和未经验证地访问对象的数据的风险。 这通过访问器实现：从基础数据成员中赋值和检索值的特殊方法。 [set](../../../csharp/language-reference/keywords/set.md) 访问器可分配数据成员，[get](../../../csharp/language-reference/keywords/get.md) 访问器检索数据成员值。  
  
 此示例演示具有两个属性的 `Person` 类：`Name`（字符串）和 `Age`（整型）。 这两个属性均提供 `get` 和 `set` 访问器，因此它们被视为读/写属性。  
  
## <a name="example"></a>示例  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a>可靠编程  
 在前面的示例中，`Name` 和 `Age` 属性为 [public](../../../csharp/language-reference/keywords/public.md)，同时包含 `get` 和 `set` 访问器。 这使得任何对象均可读取和写入这些属性。 但是，有时需要排除其中的一个访问器。 例如，省略 `set` 访问器可使属性为只读：  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 或者，可以公开一个访问器，但使另一个访问器为私有或受保护。 有关详细信息，请参阅[非对称性访问器可访问性](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)。  
  
 声明属性后，便可使用这些属性，就像它们是类的字段一样。 在获取和设置属性的值时，这允许一种非常自然的语法，如以下语句所示：  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 请注意，在属性 `set` 方法中，特殊的 `value` 变量为可用。 此变量包含用户指定的值，例如：  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 请注意在 `Person` 对象上递增 `Age` 属性的简洁语法：  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 如果将单独的 `set` 和 `get` 方法用于模型属性，则等效的代码可能如下所示：  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 `ToString` 方法在此示例中被重写：  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 请注意，`ToString` 未显式用于程序中。 默认情况下，通过 `WriteLine` 调用对其进行调用。  
  
## <a name="see-also"></a>请参阅

- [C# 编程指南](../../../csharp/programming-guide/index.md)
- [属性](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [类和结构](../../../csharp/programming-guide/classes-and-structs/index.md)
