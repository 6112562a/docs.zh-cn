---
title: 分部方法 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 62efd8b47fb565316b417a65e1b0fe37e40786c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713217"
---
# <a name="partial-method-c-reference"></a>分部方法（C# 参考）

分部方法在分部类型的一部分中定义了签名，并在该类型的另一部分中定义了实现。 通过分部方法，类设计器可提供与事件处理程序类似的方法挂钩，以便开发者决定是否实现。 如果开发者不提供实现，则编译器在编译时删除签名。 以下条件适用于分部方法：

- 分部类型各部分中的签名必须匹配。

- 方法必须返回 void。

- 不允许使用访问修饰符。 分部方法是隐式专用的。

下列示例显示在分部类的两个部分中定义的分部方法：

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

有关详细信息，请参阅[分部类和方法](../../programming-guide/classes-and-structs/partial-classes-and-methods.md)。

## <a name="see-also"></a>另请参阅

- [C# 参考](../index.md)
- [分部类型](partial-type.md)
