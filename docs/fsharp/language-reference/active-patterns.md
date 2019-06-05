---
title: 活动模式
description: 了解如何使用活动模式以定义细分输入的数据中的命名的分区F#编程语言。
ms.date: 05/16/2016
ms.openlocfilehash: 25ab255574390d3761fe788aeb413c8ee04fda2a
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690406"
---
# <a name="active-patterns"></a><span data-ttu-id="aaff4-103">活动模式</span><span class="sxs-lookup"><span data-stu-id="aaff4-103">Active Patterns</span></span>

<span data-ttu-id="aaff4-104">*活动模式*使您能够定义细分输入的数据的已命名的分区，以便可以在模式匹配表达式，就像可区分联合使用这些名称。</span><span class="sxs-lookup"><span data-stu-id="aaff4-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="aaff4-105">可使用活动模式以自定义方式为每个分区分解数据。</span><span class="sxs-lookup"><span data-stu-id="aaff4-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="aaff4-106">语法</span><span class="sxs-lookup"><span data-stu-id="aaff4-106">Syntax</span></span>

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a><span data-ttu-id="aaff4-107">备注</span><span class="sxs-lookup"><span data-stu-id="aaff4-107">Remarks</span></span>

<span data-ttu-id="aaff4-108">在上述语法中，标识符是由表示的输入数据的分区的名称*自变量*，或者，换而言之，子集的所有值的参数集的名称。</span><span class="sxs-lookup"><span data-stu-id="aaff4-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="aaff4-109">活动的模式定义中可以有最多七个分区。</span><span class="sxs-lookup"><span data-stu-id="aaff4-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="aaff4-110">*表达式*描述要将数据分解到的窗体。</span><span class="sxs-lookup"><span data-stu-id="aaff4-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="aaff4-111">活动的模式定义可用于定义用于确定哪些已命名分区根据参数属于给定的值的规则。</span><span class="sxs-lookup"><span data-stu-id="aaff4-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="aaff4-112">(| 和 |) 符号嘿*香蕉夹*并创建此类型的 let 绑定的函数调用*活动的识别器*。</span><span class="sxs-lookup"><span data-stu-id="aaff4-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="aaff4-113">作为示例，请考虑以下活动的模式的参数。</span><span class="sxs-lookup"><span data-stu-id="aaff4-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="aaff4-114">在模式匹配表达式，如以下示例所示，可以使用活动的模式。</span><span class="sxs-lookup"><span data-stu-id="aaff4-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="aaff4-115">此程序的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="aaff4-115">The output of this program is as follows:</span></span>

```
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="aaff4-116">活动模式的另一个用途是将分解在多个方面，例如当同一基础数据具有各种可能的表示形式的数据类型。</span><span class="sxs-lookup"><span data-stu-id="aaff4-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="aaff4-117">例如，`Color`对象无法分解为一表示形式，RGB 或 HSB 表示形式。</span><span class="sxs-lookup"><span data-stu-id="aaff4-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="aaff4-118">上面的程序中的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="aaff4-118">The output of the above program is as follows:</span></span>

```
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

<span data-ttu-id="aaff4-119">结合使用，这两种方式使用活动模式的分区，您将数据分解为适当的形式为和最方便的计算窗体中的相应数据执行适当的计算。</span><span class="sxs-lookup"><span data-stu-id="aaff4-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="aaff4-120">生成的模式匹配表达式使数据能够编写得非常易读，极大地简化了潜在的复杂分支和数据分析代码的简便方式。</span><span class="sxs-lookup"><span data-stu-id="aaff4-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="aaff4-121">部分活动模式</span><span class="sxs-lookup"><span data-stu-id="aaff4-121">Partial Active Patterns</span></span>

<span data-ttu-id="aaff4-122">有时，您需要进行分区仅输入空间的一部分。</span><span class="sxs-lookup"><span data-stu-id="aaff4-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="aaff4-123">在这种情况下，您编写一组的部分模式，其中匹配一些输入，但无法匹配其他输入。</span><span class="sxs-lookup"><span data-stu-id="aaff4-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="aaff4-124">始终不会生成值的活动模式被称为*分部活动模式*; 它们具有返回值将是选项类型。</span><span class="sxs-lookup"><span data-stu-id="aaff4-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="aaff4-125">若要定义部分活动模式，您可以使用通配符字符 (\_) 模式在香蕉夹内的列表的末尾。</span><span class="sxs-lookup"><span data-stu-id="aaff4-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="aaff4-126">下面的代码演示如何使用部分活动模式。</span><span class="sxs-lookup"><span data-stu-id="aaff4-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="aaff4-127">上一示例的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="aaff4-127">The output of the previous example is as follows:</span></span>

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="aaff4-128">当使用部分活动模式时，有时单项选择可以是不连续或互斥的但它们不需要。</span><span class="sxs-lookup"><span data-stu-id="aaff4-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="aaff4-129">在以下示例中，模式正方形和多维数据集的模式不是连续的因为一些数字是平方和多维数据集，例如 64。</span><span class="sxs-lookup"><span data-stu-id="aaff4-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="aaff4-130">以下程序使用 AND 模式合并的正方形和立方体的模式。</span><span class="sxs-lookup"><span data-stu-id="aaff4-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="aaff4-131">它打印最大 1000 是同时平方和多维数据集，以及是只有多维数据集的所有整数。</span><span class="sxs-lookup"><span data-stu-id="aaff4-131">It print out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span> 

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="aaff4-132">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="aaff4-132">The output is as follows:</span></span>

```
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="aaff4-133">参数化活动模式</span><span class="sxs-lookup"><span data-stu-id="aaff4-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="aaff4-134">活动模式始终采用至少一个参数为要匹配的项，但也可能会采用其他参数，这种情况下名称*参数化活动模式*适用。</span><span class="sxs-lookup"><span data-stu-id="aaff4-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="aaff4-135">其他参数，可进行专用化的常规模式。</span><span class="sxs-lookup"><span data-stu-id="aaff4-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="aaff4-136">例如，使用正则表达式分析字符串通常的活动模式包括正则表达式作为一个额外的参数，如下面的代码，还会使用部分活动模式中所示`Integer`在前面的代码示例中定义。</span><span class="sxs-lookup"><span data-stu-id="aaff4-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="aaff4-137">在此示例中，提供有关各种日期格式中使用正则表达式的字符串以自定义常规 ParseRegex 活动模式。</span><span class="sxs-lookup"><span data-stu-id="aaff4-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="aaff4-138">使用整数活动模式以匹配的字符串转换为可传递给 DateTime 构造函数的整数。</span><span class="sxs-lookup"><span data-stu-id="aaff4-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="aaff4-139">上述代码的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="aaff4-139">The output of the previous code is as follows:</span></span>

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="aaff4-140">活动模式不会限制仅用于模式匹配表达式，也可以让绑定上使用它们。</span><span class="sxs-lookup"><span data-stu-id="aaff4-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="aaff4-141">上述代码的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="aaff4-141">The output of the previous code is as follows:</span></span>

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="aaff4-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="aaff4-142">See also</span></span>

- [<span data-ttu-id="aaff4-143">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="aaff4-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="aaff4-144">match 表达式</span><span class="sxs-lookup"><span data-stu-id="aaff4-144">Match Expressions</span></span>](match-expressions.md)
