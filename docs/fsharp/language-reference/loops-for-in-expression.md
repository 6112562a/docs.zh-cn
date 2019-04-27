---
title: 循环：for...in 表达式
description: 请参阅如何F#数据类型...在表达式中循环构造用于循环访问的可枚举集合中的模式匹配。
ms.date: 05/16/2016
ms.openlocfilehash: adaf448a49cf53c63c41f9156d40ee5d1ad3caeb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024438"
---
# <a name="loops-forin-expression"></a><span data-ttu-id="082f3-103">循环：for...in 表达式</span><span class="sxs-lookup"><span data-stu-id="082f3-103">Loops: for...in Expression</span></span>

<span data-ttu-id="082f3-104">此循环构造用于循环访问的可枚举集合，如范围表达式、 序列、 列表、 数组或支持枚举的其他构造中的模式匹配。</span><span class="sxs-lookup"><span data-stu-id="082f3-104">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>

## <a name="syntax"></a><span data-ttu-id="082f3-105">语法</span><span class="sxs-lookup"><span data-stu-id="082f3-105">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="082f3-106">备注</span><span class="sxs-lookup"><span data-stu-id="082f3-106">Remarks</span></span>

<span data-ttu-id="082f3-107">`for...in`表达式可以比作`for each`其他.NET 语言中的语句因为它用于循环访问的可枚举集合中的值。</span><span class="sxs-lookup"><span data-stu-id="082f3-107">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="082f3-108">但是，`for...in`还支持模式匹配集合，而不仅仅是迭代不通过对整个集合。</span><span class="sxs-lookup"><span data-stu-id="082f3-108">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="082f3-109">可以指定的可枚举的表达式，作为可枚举集合，或通过使用`..`运算符，为上一种整型类型的范围。</span><span class="sxs-lookup"><span data-stu-id="082f3-109">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="082f3-110">可枚举集合包括列表、 序列、 数组、 集、 映射和等等。</span><span class="sxs-lookup"><span data-stu-id="082f3-110">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="082f3-111">实现的任何类型`System.Collections.IEnumerable`可用。</span><span class="sxs-lookup"><span data-stu-id="082f3-111">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="082f3-112">当使用表示范围`..`运算符，可以使用以下语法。</span><span class="sxs-lookup"><span data-stu-id="082f3-112">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="082f3-113">*启动*...</span><span class="sxs-lookup"><span data-stu-id="082f3-113">*start* ..</span></span> <span data-ttu-id="082f3-114">*finish*</span><span class="sxs-lookup"><span data-stu-id="082f3-114">*finish*</span></span>

<span data-ttu-id="082f3-115">此外可以使用一种包括名为增量*跳过*，如下面的代码。</span><span class="sxs-lookup"><span data-stu-id="082f3-115">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="082f3-116">*启动*...</span><span class="sxs-lookup"><span data-stu-id="082f3-116">*start* ..</span></span> <span data-ttu-id="082f3-117">*skip* ..</span><span class="sxs-lookup"><span data-stu-id="082f3-117">*skip* ..</span></span> <span data-ttu-id="082f3-118">*finish*</span><span class="sxs-lookup"><span data-stu-id="082f3-118">*finish*</span></span>

<span data-ttu-id="082f3-119">时使用整数范围和简单的计数器变量作为一种模式，典型的行为是计数器变量递增 1 上的每个迭代，但如果该范围包含跳过值，此计数器递增的 skip 值改为。</span><span class="sxs-lookup"><span data-stu-id="082f3-119">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="082f3-120">在模式匹配的值还可在正文的表达式。</span><span class="sxs-lookup"><span data-stu-id="082f3-120">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="082f3-121">下面的代码示例说明如何使用`for...in`表达式。</span><span class="sxs-lookup"><span data-stu-id="082f3-121">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="082f3-122">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="082f3-122">The output is as follows.</span></span>

```
1
5
100
450
788
```

<span data-ttu-id="082f3-123">下面的示例演示如何循环访问序列，以及如何使用元组模式而不是简单的变量。</span><span class="sxs-lookup"><span data-stu-id="082f3-123">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="082f3-124">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="082f3-124">The output is as follows.</span></span>

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

<span data-ttu-id="082f3-125">下面的示例演示如何在简单的整数范围内循环。</span><span class="sxs-lookup"><span data-stu-id="082f3-125">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="082f3-126">Function1 的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="082f3-126">The output of function1 is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="082f3-127">下面的示例演示如何循环访问一系列具有 skip 值为 2，其中包括每个其他元素的范围。</span><span class="sxs-lookup"><span data-stu-id="082f3-127">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="082f3-128">输出`function2`如下所示。</span><span class="sxs-lookup"><span data-stu-id="082f3-128">The output of `function2` is as follows.</span></span>

```
1 3 5 7 9
```

<span data-ttu-id="082f3-129">下面的示例演示如何使用字符范围。</span><span class="sxs-lookup"><span data-stu-id="082f3-129">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="082f3-130">输出`function3`如下所示。</span><span class="sxs-lookup"><span data-stu-id="082f3-130">The output of `function3` is as follows.</span></span>

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="082f3-131">下面的示例演示如何使用反向迭代负的 skip 值。</span><span class="sxs-lookup"><span data-stu-id="082f3-131">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="082f3-132">输出`function4`如下所示。</span><span class="sxs-lookup"><span data-stu-id="082f3-132">The output of `function4` is as follows.</span></span>

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="082f3-133">开始和结束范围也可以是表达式，如函数，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="082f3-133">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="082f3-134">输出`function5`与此输入如下所示。</span><span class="sxs-lookup"><span data-stu-id="082f3-134">The output of `function5` with this input is as follows.</span></span>

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="082f3-135">下一个示例演示如何使用通配符字符 (\_) 元素在循环中的不需要时。</span><span class="sxs-lookup"><span data-stu-id="082f3-135">The next example shows the use of a wildcard character (\_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="082f3-136">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="082f3-136">The output is as follows.</span></span>

```
Number of elements in list1: 5
```

<span data-ttu-id="082f3-137">`Note` 可以使用`for...in`在序列表达式和其他计算表达式，这种情况下的自定义的版本`for...in`使用表达式。</span><span class="sxs-lookup"><span data-stu-id="082f3-137">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="082f3-138">有关详细信息，请参阅[序列](sequences.md)，[异步工作流](asynchronous-workflows.md)，并[计算表达式](computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="082f3-138">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="082f3-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="082f3-139">See also</span></span>

- [<span data-ttu-id="082f3-140">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="082f3-140">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="082f3-141">循环：`for...to` 表达式</span><span class="sxs-lookup"><span data-stu-id="082f3-141">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
- [<span data-ttu-id="082f3-142">循环：`while...do` 表达式</span><span class="sxs-lookup"><span data-stu-id="082f3-142">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)