---
title: C# 7.2 中的新增功能
description: C# 7.2 中的新增功能概述。
ms.date: 08/16/2017
ms.openlocfilehash: 7febefb81bbea6f24690adb05488ad6a18bbf552
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75694590"
---
# <a name="whats-new-in-c-72"></a>C# 7.2 中的新增功能

C# 7.2 又是一个单点版本，它增添了大量有用的功能。
此版本的一项主要功能是避免不必要的复制或分配，进而更有效地处理值类型。

其余功能很微小，但值得拥有。

C# 7.2 使用[语言版本选择](../language-reference/configure-language-version.md)配置元素来选择编译器语言版本。

此版本中新增的语言功能包括：

- [编写安全高效代码的技巧](#safe-efficient-code-enhancements)
  - 结合了多项语法改进，可使用引用语义处理值类型。
- [非尾随命名参数](#non-trailing-named-arguments)
  - 命名的参数可后接位置参数。
- [数值文字中的前导下划线](#leading-underscores-in-numeric-literals)
  - 数值文字现可在任何打印数字前放置前导下划线。
- [`private protected` 访问修饰符](#private-protected-access-modifier)
  - `private protected` 访问修饰符允许访问同一程序集中的派生类。
- [条件 `ref` 表达式](#conditional-ref-expressions)
  - 现在可以引用条件表达式 (`?:`) 的结果。

本文的其余部分概述了每个功能。 你将了解每项功能背后的原理。 将了解语法。 可以使用 `dotnet try` 全局工具在环境中浏览这些功能：

1. 安装 [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) 全局工具。
1. 克隆 [dotnet/try-samples](https://github.com/dotnet/try-samples) 存储库。
1. 将当前目录设置为 try-samples 存储库的 csharp7 子目录   。
1. 运行 `dotnet try`。

## <a name="safe-efficient-code-enhancements"></a>安全高效的代码的增强功能

利用 7.2 中引入的语言功能，可在使用引用语义时处理值类型。 它们旨在尽量减少值类型的复制，而不造成与引用类型使用相关的内存分配，进而提升性能。 功能包括：

- 针对实参的 `in` 修饰符，指定形参通过引用传递，但不通过调用方法修改。 将 `in` 修饰符添加到参数是[源兼容的更改](version-update-considerations.md#source-compatible-changes)。
- 针对方法返回的 `ref readonly` 修饰符，指示方法通过引用返回其值，但不允许写入该对象。 如果向某个值赋予返回值，则添加 `ref readonly` 修饰符是[源兼容的更改](version-update-considerations.md#source-compatible-changes)。 将 `readonly` 修饰符添加到现有的 `ref` 返回语句是[不兼容的更改](version-update-considerations.md#incompatible-changes)。 它要求调用方更新 `ref` 本地变量的声明以包含 `readonly` 修饰符。
- `readonly struct` 声明，指示结构不可变，且应作为 `in` 参数传递到其成员方法。 将 `readonly` 修饰符添加到现有的结构声明是[二进制兼容的更改](version-update-considerations.md#binary-compatible-changes)。
- `ref struct` 声明，指示结构类型直接访问托管的内存，且必须始终分配有堆栈。 将 `ref` 修饰符添加到现有 `struct` 声明是[不兼容的更改](version-update-considerations.md#incompatible-changes)。 `ref struct` 不能是类的成员，也不能用于可能在堆上分配的其他位置。

可以在[编写安全高效的代码](../write-safe-efficient-code.md)中详细了解所有这些更改。

## <a name="non-trailing-named-arguments"></a>非尾随命名参数

方法调用现可使用位于位置参数前面的命名参数（若这些命名参数的位置正确）。 有关详细信息，请参阅[命名参数和可选参数](../programming-guide/classes-and-structs/named-and-optional-arguments.md)。

## <a name="leading-underscores-in-numeric-literals"></a>数值文字中的前导下划线

C# 7.0 中实现了对数字分隔符的支持，但这不允许文字值的第一个字符是 `_`。 十六进制文本和二进制文件现可以 `_` 开头。

例如：

```csharp
int binaryValue = 0b_0101_0101;
```

## <a name="private-protected-access-modifier"></a>*private protected* 访问修饰符

新的复合访问修饰符：`private protected` 指示可通过包含同一程序集中声明的类或派生类来访问成员。 虽然 `protected internal` 允许通过同一程序集中的类或派生类进行访问，但 `private protected` 限制对同一程序集中声明的派生类的访问。

有关详细信息，请参阅语言参考中的[访问修饰符](../language-reference/keywords/access-modifiers.md)。

## <a name="conditional-ref-expressions"></a>条件 `ref` 表达式

最后，条件表达式可能生成 ref 结果而不是值。 例如，你将编写以下内容以检索对两个数组之一中第一个元素的引用：

```csharp
ref var r = ref (arr != null ? ref arr[0] : ref otherArr[0]);
```

变量 `r` 是对 `arr` 或 `otherArr` 中第一个值的引用。

有关详细信息，请参阅语言参考中的[条件运算符 (?:)](../language-reference/operators/conditional-operator.md)。
