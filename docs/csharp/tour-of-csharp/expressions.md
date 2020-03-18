---
title: C# 表达式 - C# 语言介绍
description: 表达式、操作数和运算符是 C# 语言的构建基块
ms.date: 02/27/2020
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 209b5da01cd7539f2bd97023f40fd149910b6f1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159151"
---
# <a name="expressions"></a>表达式

*表达式*是在*操作数*和*运算符*的基础之上构造而成。 表达式的运算符指明了向操作数应用的运算。 运算符的示例包括 `+`、`-`、`*`、`/` 和 `new`。 操作数的示例包括文本、字段、局部变量和表达式。

如果表达式包含多个运算符，那么运算符的*优先级*决定了各个运算符的计算顺序。 例如，表达式 `x + y * z` 相当于计算 `x + (y * z)`，因为 `*` 运算符的优先级高于 `+` 运算符。

如果操作数两边的两个运算符的优先级相同，那么运算符的*结合性*决定了运算的执行顺序：

* 除了赋值运算符和 null 合并运算符之外，所有二元运算符均为左结合  运算符，即从左向右执行运算。 例如， `x + y + z` 将计算为 `(x + y) + z`。
* 赋值运算符、null 合并 `??` 和 `??=` 运算符和条件运算符 `?:` 为右结合  运算符，即从右向左执行运算。 例如， `x = y = z` 将计算为 `x = (y = z)`。

可以使用括号控制优先级和结合性。 例如，`x + y * z` 先计算 `y` 乘 `z`，并将结果与 `x` 相加，而 `(x + y) * z` 则先计算 `x` 加 `y`，然后将结果与 `z` 相乘。

大部分运算符可[*重载*](../language-reference/operators/operator-overloading.md)。 借助运算符重载，可以为一个或两个操作数为用户定义类或结构类型的运算指定用户定义运算符实现代码。

C# 提供多个运算符用于执行[算术](../language-reference/operators/arithmetic-operators.md)、[逻辑](../language-reference/operators/boolean-logical-operators.md)、[按位和移位](../language-reference/operators/bitwise-and-shift-operators.md)运算以及[相等](../language-reference/operators/equality-operators.md)和[排序](../language-reference/operators/comparison-operators.md)比较。

要了解按优先级排序的完整 C# 运算符列表，请参阅 [C# 运算符](../language-reference/operators/index.md)。

> [!div class="step-by-step"]
> [上一页](types-and-variables.md)
> [下一页](statements.md)
