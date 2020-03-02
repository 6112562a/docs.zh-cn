---
title: C# 表达式 - C# 语言介绍
description: 表达式、操作数和运算符是 C# 语言的构建基块
ms.date: 02/27/2020
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 209b5da01cd7539f2bd97023f40fd149910b6f1d
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159151"
---
# <a name="expressions"></a><span data-ttu-id="b2ad6-103">表达式</span><span class="sxs-lookup"><span data-stu-id="b2ad6-103">Expressions</span></span>

<span data-ttu-id="b2ad6-104">*表达式*是在*操作数*和*运算符*的基础之上构造而成。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="b2ad6-105">表达式的运算符指明了向操作数应用的运算。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="b2ad6-106">运算符的示例包括 `+`、`-`、`*`、`/` 和 `new`。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="b2ad6-107">操作数的示例包括文本、字段、局部变量和表达式。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="b2ad6-108">如果表达式包含多个运算符，那么运算符的*优先级*决定了各个运算符的计算顺序。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="b2ad6-109">例如，表达式 `x + y * z` 相当于计算 `x + (y * z)`，因为 `*` 运算符的优先级高于 `+` 运算符。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="b2ad6-110">如果操作数两边的两个运算符的优先级相同，那么运算符的*结合性*决定了运算的执行顺序：</span><span class="sxs-lookup"><span data-stu-id="b2ad6-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

* <span data-ttu-id="b2ad6-111">除了赋值运算符和 null 合并运算符之外，所有二元运算符均为左结合  运算符，即从左向右执行运算。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-111">Except for the assignment and null-coalescing operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="b2ad6-112">例如，`x + y + z` 将计算为 `(x + y) + z`。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
* <span data-ttu-id="b2ad6-113">赋值运算符、null 合并 `??` 和 `??=` 运算符和条件运算符 `?:` 为右结合  运算符，即从右向左执行运算。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-113">The assignment operators, the null-coalescing `??` and `??=` operators, and the conditional operator `?:` are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="b2ad6-114">例如，`x = y = z` 将计算为 `x = (y = z)`。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="b2ad6-115">可以使用括号控制优先级和结合性。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="b2ad6-116">例如，`x + y * z` 先计算 `y` 乘 `z`，并将结果与 `x` 相加，而 `(x + y) * z` 则先计算 `x` 加 `y`，然后将结果与 `z` 相乘。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="b2ad6-117">大部分运算符可[*重载*](../language-reference/operators/operator-overloading.md)。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-117">Most operators can be [*overloaded*](../language-reference/operators/operator-overloading.md).</span></span> <span data-ttu-id="b2ad6-118">借助运算符重载，可以为一个或两个操作数为用户定义类或结构类型的运算指定用户定义运算符实现代码。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="b2ad6-119">C# 提供多个运算符用于执行[算术](../language-reference/operators/arithmetic-operators.md)、[逻辑](../language-reference/operators/boolean-logical-operators.md)、[按位和移位](../language-reference/operators/bitwise-and-shift-operators.md)运算以及[相等](../language-reference/operators/equality-operators.md)和[排序](../language-reference/operators/comparison-operators.md)比较。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-119">C# provides a number of operators to perform [arithmetic](../language-reference/operators/arithmetic-operators.md), [logical](../language-reference/operators/boolean-logical-operators.md), [bitwise and shift](../language-reference/operators/bitwise-and-shift-operators.md) operations and [equality](../language-reference/operators/equality-operators.md) and [order](../language-reference/operators/comparison-operators.md) comparisons.</span></span>

<span data-ttu-id="b2ad6-120">要了解按优先级排序的完整 C# 运算符列表，请参阅 [C# 运算符](../language-reference/operators/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b2ad6-120">For the complete list of C# operators ordered by precedence level, see [C# operators](../language-reference/operators/index.md).</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="b2ad6-121">[上一页](types-and-variables.md)
> [下一页](statements.md)</span><span class="sxs-lookup"><span data-stu-id="b2ad6-121">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
