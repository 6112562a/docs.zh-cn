---
title: 结构 - C# 编程指南
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 3f19d0485939e1923c479c1c9fdeb06572a11e14
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240380"
---
# <a name="structs-c-programming-guide"></a>结构（C# 编程指南）

通过使用[结构](../../language-reference/keywords/struct.md)关键字来定义结构，例如：  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
结构与类的大部分语法相同。 结构名称必须是有效的 C# [标识符名称](../inside-a-program/identifier-names.md)。 结构在以下方面比类的限制更多：  
  
- 在结构声明中，除非将字段声明为 const 或 static，否则无法初始化。  
- 结构不能声明默认构造函数（没有参数的构造函数）或终结器。  
- 结构在分配时进行复制。 将结构分配给新变量时，将复制所有数据，并且对新副本所做的任何修改不会更改原始副本的数据。 在处理值类型的集合（如 `Dictionary<string, myStruct>`）时，请务必记住这一点。  
- 结构是值类型，不同于类，类是引用类型。  
- 与类不同，无需使用 `new` 运算符即可对结构进行实例化。  
- 结构可以声明具有参数的构造函数。 
- 一个结构无法继承自另一个结构或类，并且它不能为类的基类。 所有结构都直接继承自 <xref:System.ValueType>，后者继承自 <xref:System.Object>。  
- 结构可以实现接口。  
- 结构可用作可以为 null 的类型，并且可以向其分配一个 null 值。  
  
## <a name="related-sections"></a>相关章节  

更多相关信息：  
  
- [使用结构](using-structs.md)
- [构造函数](constructors.md)
- [可以为 null 的类型](../nullable-types/index.md)
- [如何：了解向方法传递结构与类引用的区别](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [如何：在结构之间实现用户定义的转换](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a>请参阅

- [C# 编程指南](../index.md)
- [类和结构](index.md)
- [类](classes.md)
- [标识符名称](../inside-a-program/identifier-names.md)
