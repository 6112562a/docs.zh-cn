---
title: 序列 (F#)
description: 了解如何使用 F# 序列，当具有较大，有序数据集合，但不一定希望使用的所有元素。
ms.date: 05/16/2016
ms.openlocfilehash: cfe8d1e350a8ac46b7700c12aa84d250f8b35855
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2018
ms.locfileid: "48838894"
---
# <a name="sequences"></a><span data-ttu-id="c6e00-103">序列</span><span class="sxs-lookup"><span data-stu-id="c6e00-103">Sequences</span></span>

> [!NOTE]
<span data-ttu-id="c6e00-104">本文中的 API 参考链接将转至 MSDN。</span><span class="sxs-lookup"><span data-stu-id="c6e00-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="c6e00-105">Docs.microsoft.com API 参考尚未完成。</span><span class="sxs-lookup"><span data-stu-id="c6e00-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="c6e00-106">一个*序列*是以逻辑序列的元素类型相同的所有。</span><span class="sxs-lookup"><span data-stu-id="c6e00-106">A *sequence* is a logical series of elements all of one type.</span></span> <span data-ttu-id="c6e00-107">当具有较大，有序数据集合，但一定不希望使用的所有元素时，序列是特别有用。</span><span class="sxs-lookup"><span data-stu-id="c6e00-107">Sequences are particularly useful when you have a large, ordered collection of data but do not necessarily expect to use all of the elements.</span></span> <span data-ttu-id="c6e00-108">各序列元素计算仅为所需，因此，序列可以提供更好的性能比中在不使用的所有元素的情况下的列表。</span><span class="sxs-lookup"><span data-stu-id="c6e00-108">Individual sequence elements are computed only as required, so a sequence can provide better performance than a list in situations in which not all the elements are used.</span></span> <span data-ttu-id="c6e00-109">序列由`seq<'T>`类型，即别名为`System.Collections.Generic.IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="c6e00-109">Sequences are represented by the `seq<'T>` type, which is an alias for `System.Collections.Generic.IEnumerable`.</span></span> <span data-ttu-id="c6e00-110">因此，任何.NET Framework 类型实现`System.IEnumerable`可作为一个序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-110">Therefore, any .NET Framework type that implements `System.IEnumerable` can be used as a sequence.</span></span> <span data-ttu-id="c6e00-111">[Seq 模块](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)对涉及多个序列的操作提供支持。</span><span class="sxs-lookup"><span data-stu-id="c6e00-111">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) provides support for manipulations involving sequences.</span></span>

## <a name="sequence-expressions"></a><span data-ttu-id="c6e00-112">序列表达式</span><span class="sxs-lookup"><span data-stu-id="c6e00-112">Sequence Expressions</span></span>

<span data-ttu-id="c6e00-113">一个*序列表达式*是表达式的计算结果为一个序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-113">A *sequence expression* is an expression that evaluates to a sequence.</span></span> <span data-ttu-id="c6e00-114">序列表达式可以采用多种形式。</span><span class="sxs-lookup"><span data-stu-id="c6e00-114">Sequence expressions can take a number of forms.</span></span> <span data-ttu-id="c6e00-115">最简单的形式指定的范围。</span><span class="sxs-lookup"><span data-stu-id="c6e00-115">The simplest form specifies a range.</span></span> <span data-ttu-id="c6e00-116">例如，`seq { 1 .. 5 }`创建一个序列，其中包含五个元素，其中包括 1 和 5 的终结点。</span><span class="sxs-lookup"><span data-stu-id="c6e00-116">For example, `seq { 1 .. 5 }` creates a sequence that contains five elements, including the endpoints 1 and 5.</span></span> <span data-ttu-id="c6e00-117">你可以还指定增量 （或减少） 之间两个双句点。</span><span class="sxs-lookup"><span data-stu-id="c6e00-117">You can also specify an increment (or decrement) between two double periods.</span></span> <span data-ttu-id="c6e00-118">例如，以下代码创建的一系列为 10 的倍数。</span><span class="sxs-lookup"><span data-stu-id="c6e00-118">For example, the following code creates the sequence of multiples of 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

<span data-ttu-id="c6e00-119">序列表达式由 F# 表达式生成的序列的值组成。</span><span class="sxs-lookup"><span data-stu-id="c6e00-119">Sequence expressions are made up of F# expressions that produce values of the sequence.</span></span> <span data-ttu-id="c6e00-120">可以使用`yield`关键字来生成将成为序列的一部分的值。</span><span class="sxs-lookup"><span data-stu-id="c6e00-120">They can use the `yield` keyword to produce values that become part of the sequence.</span></span>

<span data-ttu-id="c6e00-121">以下是一个示例。</span><span class="sxs-lookup"><span data-stu-id="c6e00-121">Following is an example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

<span data-ttu-id="c6e00-122">可以使用`->`而不是运算符`yield`，在这种情况下可以省略`do`关键字，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="c6e00-122">You can use the `->` operator instead of `yield`, in which case you can omit the `do` keyword, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

<span data-ttu-id="c6e00-123">下面的代码生成到一个数组，表示网格以及索引的坐标对的列表。</span><span class="sxs-lookup"><span data-stu-id="c6e00-123">The following code generates a list of coordinate pairs along with an index into an array that represents the grid.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

<span data-ttu-id="c6e00-124">`if`序列中使用的表达式是一个筛选器。</span><span class="sxs-lookup"><span data-stu-id="c6e00-124">An `if` expression used in a sequence is a filter.</span></span> <span data-ttu-id="c6e00-125">例如，若要生成的序列只包含质数，假设您有一个函数`isprime`类型的`int -> bool`，按如下所示构造序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-125">For example, to generate a sequence of only prime numbers, assuming that you have a function `isprime` of type `int -> bool`, construct the sequence as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

<span data-ttu-id="c6e00-126">当你使用`yield`或`->`迭代，在每次迭代应生成序列的单个元素。</span><span class="sxs-lookup"><span data-stu-id="c6e00-126">When you use `yield` or `->` in an iteration, each iteration is expected to generate a single element of the sequence.</span></span> <span data-ttu-id="c6e00-127">如果每次迭代都会生成一系列元素，使用`yield!`。</span><span class="sxs-lookup"><span data-stu-id="c6e00-127">If each iteration produces a sequence of elements, use `yield!`.</span></span> <span data-ttu-id="c6e00-128">在这种情况下，每个迭代上生成的元素连在一起可生成最终的序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-128">In that case, the elements generated on each iteration are concatenated to produce the final sequence.</span></span>

<span data-ttu-id="c6e00-129">你可以组合在一起在序列表达式中的多个表达式。</span><span class="sxs-lookup"><span data-stu-id="c6e00-129">You can combine multiple expressions together in a sequence expression.</span></span> <span data-ttu-id="c6e00-130">通过每个表达式生成的元素会连接在一起。</span><span class="sxs-lookup"><span data-stu-id="c6e00-130">The elements generated by each expression are concatenated together.</span></span> <span data-ttu-id="c6e00-131">有关示例，请参阅本主题的"示例"部分。</span><span class="sxs-lookup"><span data-stu-id="c6e00-131">For an example, see the "Examples" section of this topic.</span></span>

## <a name="examples"></a><span data-ttu-id="c6e00-132">示例</span><span class="sxs-lookup"><span data-stu-id="c6e00-132">Examples</span></span>

<span data-ttu-id="c6e00-133">第一个示例使用序列表达式包含迭代、 筛选器和 yield 来生成一个数组。</span><span class="sxs-lookup"><span data-stu-id="c6e00-133">The first example uses a sequence expression that contains an iteration, a filter, and a yield to generate an array.</span></span> <span data-ttu-id="c6e00-134">此代码将打印一系列 1 和 100 到控制台之间的素数。</span><span class="sxs-lookup"><span data-stu-id="c6e00-134">This code prints a sequence of prime numbers between 1 and 100 to the console.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

<span data-ttu-id="c6e00-135">下面的代码使用`yield`若要创建的两个因素和产品组成的三个元素，元组组成的乘法表。</span><span class="sxs-lookup"><span data-stu-id="c6e00-135">The following code uses `yield` to create a multiplication table that consists of tuples of three elements, each consisting of two factors and the product.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

<span data-ttu-id="c6e00-136">下面的示例演示如何将`yield!`合并各个序列合并为单一的最后一个序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-136">The following example demonstrates the use of `yield!` to combine individual sequences into a single final sequence.</span></span> <span data-ttu-id="c6e00-137">在这种情况下，每个二进制树中的子树的序列被串联的递归函数以生成最终的序列中。</span><span class="sxs-lookup"><span data-stu-id="c6e00-137">In this case, the sequences for each subtree in a binary tree are concatenated in a recursive function to produce the final sequence.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a><span data-ttu-id="c6e00-138">使用序列</span><span class="sxs-lookup"><span data-stu-id="c6e00-138">Using Sequences</span></span>

<span data-ttu-id="c6e00-139">序列支持许多相同的功能[列出了](lists.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e00-139">Sequences support many of the same functions as [lists](lists.md).</span></span> <span data-ttu-id="c6e00-140">序列还支持分组，然后通过使用键生成函数计算等操作。</span><span class="sxs-lookup"><span data-stu-id="c6e00-140">Sequences also support operations such as grouping and counting by using key-generating functions.</span></span> <span data-ttu-id="c6e00-141">序列还支持更多的不同函数的提取子序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-141">Sequences also support more diverse functions for extracting subsequences.</span></span>

<span data-ttu-id="c6e00-142">多种数据类型，例如列表、 数组、 集和地图隐式是序列，因为它们是可枚举集合。</span><span class="sxs-lookup"><span data-stu-id="c6e00-142">Many data types, such as lists, arrays, sets, and maps are implicitly sequences because they are enumerable collections.</span></span> <span data-ttu-id="c6e00-143">将序列作为参数适用于任何常见的 F# 数据类型，除了为实现任何.NET Framework 数据类型的函数`System.Collections.Generic.IEnumerable<'T>`。</span><span class="sxs-lookup"><span data-stu-id="c6e00-143">A function that takes a sequence as an argument works with any of the common F# data types, in addition to any .NET Framework data type that implements `System.Collections.Generic.IEnumerable<'T>`.</span></span> <span data-ttu-id="c6e00-144">使用列表作为参数，它只能使用列表的函数相反。</span><span class="sxs-lookup"><span data-stu-id="c6e00-144">Contrast this to a function that takes a list as an argument, which can only take lists.</span></span> <span data-ttu-id="c6e00-145">类型`seq<'T>`是类型缩写`IEnumerable<'T>`。</span><span class="sxs-lookup"><span data-stu-id="c6e00-145">The type `seq<'T>` is a type abbreviation for `IEnumerable<'T>`.</span></span> <span data-ttu-id="c6e00-146">这意味着，任何实现泛型的类型`System.Collections.Generic.IEnumerable<'T>`，其中包括数组、 列表、 设置，并在 F# 中，并还大多数.NET Framework 集合类型，映射是与兼容`seq`类型并可以在一个序列的任何地方。</span><span class="sxs-lookup"><span data-stu-id="c6e00-146">This means that any type that implements the generic `System.Collections.Generic.IEnumerable<'T>`, which includes arrays, lists, sets, and maps in F#, and also most .NET Framework collection types, is compatible with the `seq` type and can be used wherever a sequence is expected.</span></span>

## <a name="module-functions"></a><span data-ttu-id="c6e00-147">模块函数</span><span class="sxs-lookup"><span data-stu-id="c6e00-147">Module Functions</span></span>

<span data-ttu-id="c6e00-148">[Seq 模块](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)中[Microsoft.FSharp.Collections 命名空间](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f)包含用于使用序列函数。</span><span class="sxs-lookup"><span data-stu-id="c6e00-148">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) in the [Microsoft.FSharp.Collections namespace](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) contains functions for working with sequences.</span></span> <span data-ttu-id="c6e00-149">这些函数使用于列表、 数组、 映射和集，因为所有这些类型是可枚举的并且因此会被视为序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-149">These functions work with lists, arrays, maps, and sets as well, because all of those types are enumerable, and therefore can be treated as sequences.</span></span>

## <a name="creating-sequences"></a><span data-ttu-id="c6e00-150">创建序列</span><span class="sxs-lookup"><span data-stu-id="c6e00-150">Creating Sequences</span></span>

<span data-ttu-id="c6e00-151">如前面所述，使用序列表达式，或使用某些功能，可以创建序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-151">You can create sequences by using sequence expressions, as described previously, or by using certain functions.</span></span>

<span data-ttu-id="c6e00-152">可以通过创建一个空序列[Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)，也可以通过使用创建的只是一个指定的元素序列[Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7)。</span><span class="sxs-lookup"><span data-stu-id="c6e00-152">You can create an empty sequence by using [Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), or you can create a sequence of just one specified element by using [Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

<span data-ttu-id="c6e00-153">可以使用[Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576)来创建其元素通过使用你提供的函数创建的序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-153">You can use [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) to create a sequence for which the elements are created by using a function that you provide.</span></span> <span data-ttu-id="c6e00-154">此外提供序列的大小。</span><span class="sxs-lookup"><span data-stu-id="c6e00-154">You also provide a size for the sequence.</span></span> <span data-ttu-id="c6e00-155">此函数则类似[List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)，只不过直到循环访问序列，不会创建元素。</span><span class="sxs-lookup"><span data-stu-id="c6e00-155">This function is just like [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), except that the elements are not created until you iterate through the sequence.</span></span> <span data-ttu-id="c6e00-156">下面的代码演示如何使用`Seq.init`。</span><span class="sxs-lookup"><span data-stu-id="c6e00-156">The following code illustrates the use of `Seq.init`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

<span data-ttu-id="c6e00-157">输出为</span><span class="sxs-lookup"><span data-stu-id="c6e00-157">The output is</span></span>

```
0 10 20 30 40
```

<span data-ttu-id="c6e00-158">通过使用[Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99)并[Seq.ofList&#60;不&#62;函数](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d)，可以从数组和列表创建序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-158">By using [Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) and [Seq.ofList&#60;'T&#62; Function](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), you can create sequences from arrays and lists.</span></span> <span data-ttu-id="c6e00-159">但是，您也可以将数组和列表成序列通过使用转换运算符。</span><span class="sxs-lookup"><span data-stu-id="c6e00-159">However, you can also convert arrays and lists to sequences by using a cast operator.</span></span> <span data-ttu-id="c6e00-160">这两种技术如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="c6e00-160">Both techniques are shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

<span data-ttu-id="c6e00-161">通过使用[Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)，可以从弱类型化的集合，如中所定义创建序列`System.Collections`。</span><span class="sxs-lookup"><span data-stu-id="c6e00-161">By using [Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), you can create a sequence from a weakly typed collection, such as those defined in `System.Collections`.</span></span> <span data-ttu-id="c6e00-162">此类弱类型化的集合具有元素类型`System.Object`并使用非泛型枚举`System.Collections.Generic.IEnumerable&#96;1`类型。</span><span class="sxs-lookup"><span data-stu-id="c6e00-162">Such weakly typed collections have the element type `System.Object` and are enumerated by using the non-generic `System.Collections.Generic.IEnumerable&#96;1` type.</span></span> <span data-ttu-id="c6e00-163">下面的代码演示如何使用`Seq.cast`转换`System.Collections.ArrayList`为一个序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-163">The following code illustrates the use of `Seq.cast` to convert an `System.Collections.ArrayList` into a sequence.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

<span data-ttu-id="c6e00-164">您可以通过使用定义无限序列[Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef)函数。</span><span class="sxs-lookup"><span data-stu-id="c6e00-164">You can define infinite sequences by using the [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) function.</span></span> <span data-ttu-id="c6e00-165">此类的序列时，你提供的元素的索引从生成的每个元素的函数。</span><span class="sxs-lookup"><span data-stu-id="c6e00-165">For such a sequence, you provide a function that generates each element from the index of the element.</span></span> <span data-ttu-id="c6e00-166">无限序列都可能由于迟缓计算;可以根据需要通过调用指定函数创建元素。</span><span class="sxs-lookup"><span data-stu-id="c6e00-166">Infinite sequences are possible because of lazy evaluation; elements are created as needed by calling the function that you specify.</span></span> <span data-ttu-id="c6e00-167">下面的代码示例生成一系列交替出现的连续整数的平方的倒数浮点数，在此情况下无限的序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-167">The following code example produces an infinite sequence of floating point numbers, in this case the alternating series of reciprocals of squares of successive integers.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

<span data-ttu-id="c6e00-168">[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21)从使用一个状态和转换以生成序列中的每个后续元素的计算函数生成的序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-168">[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generates a sequence from a computation function that takes a state and transforms it to produce each subsequent element in the sequence.</span></span> <span data-ttu-id="c6e00-169">状态为只是一个值，该值用于计算每个元素，并根据计算每个元素可以更改。</span><span class="sxs-lookup"><span data-stu-id="c6e00-169">The state is just a value that is used to compute each element, and can change as each element is computed.</span></span> <span data-ttu-id="c6e00-170">第二个参数`Seq.unfold`是用于启动序列的初始值。</span><span class="sxs-lookup"><span data-stu-id="c6e00-170">The second argument to `Seq.unfold` is the initial value that is used to start the sequence.</span></span> <span data-ttu-id="c6e00-171">`Seq.unfold` 使用状态时，这样就可以通过返回终止序列选项类型`None`值。</span><span class="sxs-lookup"><span data-stu-id="c6e00-171">`Seq.unfold` uses an option type for the state, which enables you to terminate the sequence by returning the `None` value.</span></span> <span data-ttu-id="c6e00-172">下面的代码演示的序列，两个示例`seq1`并`fib`，生成的`unfold`操作。</span><span class="sxs-lookup"><span data-stu-id="c6e00-172">The following code shows two examples of sequences, `seq1` and `fib`, that are generated by an `unfold` operation.</span></span> <span data-ttu-id="c6e00-173">第一种`seq1`，是只具有最多 100 个数字的简单序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-173">The first, `seq1`, is just a simple sequence with numbers up to 100.</span></span> <span data-ttu-id="c6e00-174">第二类是`fib`，使用`unfold`计算斐波那契序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-174">The second, `fib`, uses `unfold` to compute the Fibonacci sequence.</span></span> <span data-ttu-id="c6e00-175">斐波那契序列中的每个元素是前两个斐波那契数字的总和，因为状态值将为元组组成的序列中前两个数字。</span><span class="sxs-lookup"><span data-stu-id="c6e00-175">Because each element in the Fibonacci sequence is the sum of the previous two Fibonacci numbers, the state value is a tuple that consists of the previous two numbers in the sequence.</span></span> <span data-ttu-id="c6e00-176">初始值是`(1,1)`，序列中的前两个数字。</span><span class="sxs-lookup"><span data-stu-id="c6e00-176">The initial value is `(1,1)`, the first two numbers in the sequence.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

<span data-ttu-id="c6e00-177">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="c6e00-177">The output is as follows:</span></span>

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

<span data-ttu-id="c6e00-178">下面的代码是使用此处所述来生成和计算无限序列的值的序列模块函数的许多示例。</span><span class="sxs-lookup"><span data-stu-id="c6e00-178">The following code is an example that uses many of the sequence module functions described here to generate and compute the values of infinite sequences.</span></span> <span data-ttu-id="c6e00-179">代码可能需要几分钟才能运行。</span><span class="sxs-lookup"><span data-stu-id="c6e00-179">The code might take a few minutes to run.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a><span data-ttu-id="c6e00-180">搜索和查找元素</span><span class="sxs-lookup"><span data-stu-id="c6e00-180">Searching and Finding Elements</span></span>

<span data-ttu-id="c6e00-181">序列支持适用于列表的功能： [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1)， [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565)， [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8)， [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3)， [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d)， [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)，和[Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)。</span><span class="sxs-lookup"><span data-stu-id="c6e00-181">Sequences support functionality available with lists: [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), and [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).</span></span> <span data-ttu-id="c6e00-182">这些函数可用于序列的版本的计算结果最多要搜索的元素序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-182">The versions of these functions that are available for sequences evaluate the sequence only up to the element that is being searched for.</span></span> <span data-ttu-id="c6e00-183">有关示例，请参阅[列出了](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)。</span><span class="sxs-lookup"><span data-stu-id="c6e00-183">For examples, see [Lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span>

## <a name="obtaining-subsequences"></a><span data-ttu-id="c6e00-184">获取子序列</span><span class="sxs-lookup"><span data-stu-id="c6e00-184">Obtaining Subsequences</span></span>

<span data-ttu-id="c6e00-185">[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770)并[Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395)是否与相应的函数，只不过筛选和选择才会计算序列元素的列表，可类似。</span><span class="sxs-lookup"><span data-stu-id="c6e00-185">[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) and [Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) are like the corresponding functions that are available for lists, except that the filtering and choosing does not occur until the sequence elements are evaluated.</span></span>

<span data-ttu-id="c6e00-186">[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244)从另一个序列，创建一个序列，但限制为指定数量的元素序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-186">[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) creates a sequence from another sequence, but limits the sequence to a specified number of elements.</span></span> <span data-ttu-id="c6e00-187">[Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596)创建包含指定的数量的元素序列的开始一个新序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-187">[Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) creates a new sequence that contains only a specified number of elements from the start of a sequence.</span></span> <span data-ttu-id="c6e00-188">如果有更少元素序列中的指定若要充分，比`Seq.take`引发`System.InvalidOperationException`。</span><span class="sxs-lookup"><span data-stu-id="c6e00-188">If there are fewer elements in the sequence than you specify to take, `Seq.take` throws a `System.InvalidOperationException`.</span></span> <span data-ttu-id="c6e00-189">之间的差异`Seq.take`并`Seq.truncate`在于`Seq.truncate`数少于指定的元素数是否未生成错误。</span><span class="sxs-lookup"><span data-stu-id="c6e00-189">The difference between `Seq.take` and `Seq.truncate` is that `Seq.truncate` does not produce an error if the number of elements is fewer than the number you specify.</span></span>

<span data-ttu-id="c6e00-190">下面的代码显示了的行为和之间的差异`Seq.truncate`和`Seq.take`。</span><span class="sxs-lookup"><span data-stu-id="c6e00-190">The following code shows the behavior of and differences between `Seq.truncate` and `Seq.take`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

<span data-ttu-id="c6e00-191">输出中，会发生错误之前，如下所示。</span><span class="sxs-lookup"><span data-stu-id="c6e00-191">The output, before the error occurs, is as follows.</span></span>

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

<span data-ttu-id="c6e00-192">通过使用[Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92)，可以指定的谓词函数 （布尔函数），并创建从另一个序列的谓词是为其原始序列中的这些元素组成的序列`true`，但停止谓词为其返回的第一个元素之前`false`。</span><span class="sxs-lookup"><span data-stu-id="c6e00-192">By using [Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), you can specify a predicate function (a Boolean function) and create a sequence from another sequence made up of those elements of the original sequence for which the predicate is `true`, but stop before the first element for which the predicate returns `false`.</span></span> <span data-ttu-id="c6e00-193">[Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1)返回跳过指定的数目的另一个序列中的第一个元素，并返回剩余元素的序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-193">[Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) returns a sequence that skips a specified number of the first elements of another sequence and returns the remaining elements.</span></span> <span data-ttu-id="c6e00-194">[Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16)返回，只要该谓词返回跳过另一个序列中的第一个元素的序列`true`，然后返回剩余元素，谓词为其返回的第一个元素开始`false`.</span><span class="sxs-lookup"><span data-stu-id="c6e00-194">[Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) returns a sequence that skips the first elements of another sequence as long as the predicate returns `true`, and then returns the remaining elements, starting with the first element for which the predicate returns `false`.</span></span>

<span data-ttu-id="c6e00-195">下面的代码示例演示的行为和之间的差异`Seq.takeWhile`， `Seq.skip`，和`Seq.skipWhile`。</span><span class="sxs-lookup"><span data-stu-id="c6e00-195">The following code example illustrates the behavior of and differences between `Seq.takeWhile`, `Seq.skip`, and `Seq.skipWhile`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

<span data-ttu-id="c6e00-196">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c6e00-196">The output is as follows.</span></span>

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a><span data-ttu-id="c6e00-197">转换序列</span><span class="sxs-lookup"><span data-stu-id="c6e00-197">Transforming Sequences</span></span>

<span data-ttu-id="c6e00-198">[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1)创建新的序列的输入序列中的连续的元素分组到元组。</span><span class="sxs-lookup"><span data-stu-id="c6e00-198">[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) creates a new sequence in which successive elements of the input sequence are grouped into tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

<span data-ttu-id="c6e00-199">[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744)类似于`Seq.pairwise`，只不过而不是生成的元组序列，它会生成一系列包含相邻元素的副本的数组 (*窗口*) 的序列中。</span><span class="sxs-lookup"><span data-stu-id="c6e00-199">[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) is like `Seq.pairwise`, except that instead of producing a sequence of tuples, it produces a sequence of arrays that contain copies of adjacent elements (a *window*) from the sequence.</span></span> <span data-ttu-id="c6e00-200">每个数组中指定所需的相邻元素的数目。</span><span class="sxs-lookup"><span data-stu-id="c6e00-200">You specify the number of adjacent elements you want in each array.</span></span>

<span data-ttu-id="c6e00-201">以下代码示例演示了 `Seq.windowed` 的用法。</span><span class="sxs-lookup"><span data-stu-id="c6e00-201">The following code example demonstrates the use of `Seq.windowed`.</span></span> <span data-ttu-id="c6e00-202">在这种情况下的窗口中的元素数为 3。</span><span class="sxs-lookup"><span data-stu-id="c6e00-202">In this case the number of elements in the window is 3.</span></span> <span data-ttu-id="c6e00-203">该示例使用`printSeq`，前面的代码示例中定义。</span><span class="sxs-lookup"><span data-stu-id="c6e00-203">The example uses `printSeq`, which is defined in the previous code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet180.fs)]

<span data-ttu-id="c6e00-204">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c6e00-204">The output is as follows.</span></span>

<span data-ttu-id="c6e00-205">初始序列：</span><span class="sxs-lookup"><span data-stu-id="c6e00-205">Initial sequence:</span></span>

```
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a><span data-ttu-id="c6e00-206">包含多个序列的操作</span><span class="sxs-lookup"><span data-stu-id="c6e00-206">Operations with Multiple Sequences</span></span>

<span data-ttu-id="c6e00-207">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4)并[Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16)采用两个或三个序列并生成的元组序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-207">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) and [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) take two or three sequences and produce a sequence of tuples.</span></span> <span data-ttu-id="c6e00-208">这些函数如下所示的相应的函数可用于[列出了](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)。</span><span class="sxs-lookup"><span data-stu-id="c6e00-208">These functions are like the corresponding functions available for [lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span> <span data-ttu-id="c6e00-209">没有相应功能用于将一个序列分为两个或多个序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-209">There is no corresponding functionality to separate one sequence into two or more sequences.</span></span> <span data-ttu-id="c6e00-210">如果您需要一个序列，此功能，将序列转换为列表，并使用[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)。</span><span class="sxs-lookup"><span data-stu-id="c6e00-210">If you need this functionality for a sequence, convert the sequence to a list and use [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

## <a name="sorting-comparing-and-grouping"></a><span data-ttu-id="c6e00-211">排序、 比较和分组</span><span class="sxs-lookup"><span data-stu-id="c6e00-211">Sorting, Comparing, and Grouping</span></span>

<span data-ttu-id="c6e00-212">可以对列表的排序函数也适用于序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-212">The sorting functions supported for lists also work with sequences.</span></span> <span data-ttu-id="c6e00-213">这包括[Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e)并[Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f)。</span><span class="sxs-lookup"><span data-stu-id="c6e00-213">This includes [Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) and [Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f).</span></span> <span data-ttu-id="c6e00-214">这些函数循环访问整个序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-214">These functions iterate through the whole sequence.</span></span>

<span data-ttu-id="c6e00-215">通过比较两个序列[Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f)函数。</span><span class="sxs-lookup"><span data-stu-id="c6e00-215">You compare two sequences by using the [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) function.</span></span> <span data-ttu-id="c6e00-216">该函数将连续的元素进行比较，并停止时遇到的第一个不相等对。</span><span class="sxs-lookup"><span data-stu-id="c6e00-216">The function compares successive elements in turn, and stops when it encounters the first unequal pair.</span></span> <span data-ttu-id="c6e00-217">比较并不影响任何其他元素。</span><span class="sxs-lookup"><span data-stu-id="c6e00-217">Any additional elements do not contribute to the comparison.</span></span>

<span data-ttu-id="c6e00-218">以下代码显示了 `Seq.compareWith` 的用法。</span><span class="sxs-lookup"><span data-stu-id="c6e00-218">The following code shows the use of `Seq.compareWith`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

<span data-ttu-id="c6e00-219">在前面的代码，计算和检查，仅第一个元素，结果是-1。</span><span class="sxs-lookup"><span data-stu-id="c6e00-219">In the previous code, only the first element is computed and examined, and the result is -1.</span></span>

<span data-ttu-id="c6e00-220">[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f)将生成名为的值的函数*密钥*的每个元素。</span><span class="sxs-lookup"><span data-stu-id="c6e00-220">[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) takes a function that generates a value called a *key* for each element.</span></span> <span data-ttu-id="c6e00-221">通过对每个元素调用此函数的每个元素生成一个密钥。</span><span class="sxs-lookup"><span data-stu-id="c6e00-221">A key is generated for each element by calling this function on each element.</span></span> <span data-ttu-id="c6e00-222">`Seq.countBy` 然后返回一个序列，其中包含的项的值，并生成密钥的每个值的元素数的计数。</span><span class="sxs-lookup"><span data-stu-id="c6e00-222">`Seq.countBy` then returns a sequence that contains the key values, and a count of the number of elements that generated each value of the key.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

<span data-ttu-id="c6e00-223">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c6e00-223">The output is as follows.</span></span>

```
(1, 34) (2, 33) (0, 33)
```

<span data-ttu-id="c6e00-224">前面的输出显示有 34 个元素生成的项 1，对原始序列的 33 个值生成密钥 2 和 33 个值生成的键 0。</span><span class="sxs-lookup"><span data-stu-id="c6e00-224">The previous output shows that there were 34 elements of the original sequence that produced the key 1, 33 values that produced the key 2, and 33 values that produced the key 0.</span></span>

<span data-ttu-id="c6e00-225">可以通过调用组序列的元素[Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd)。</span><span class="sxs-lookup"><span data-stu-id="c6e00-225">You can group elements of a sequence by calling [Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd).</span></span> <span data-ttu-id="c6e00-226">`Seq.groupBy` 采用序列和生成的密钥从元素的函数。</span><span class="sxs-lookup"><span data-stu-id="c6e00-226">`Seq.groupBy` takes a sequence and a function that generates a key from an element.</span></span> <span data-ttu-id="c6e00-227">对序列的每个元素执行函数。</span><span class="sxs-lookup"><span data-stu-id="c6e00-227">The function is executed on each element of the sequence.</span></span> <span data-ttu-id="c6e00-228">`Seq.groupBy` 返回元组，其中每个元组的第一个元素是键，第二个是一系列生成该键的元素的序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-228">`Seq.groupBy` returns a sequence of tuples, where the first element of each tuple is the key and the second is a sequence of elements that produce that key.</span></span>

<span data-ttu-id="c6e00-229">下面的代码示例演示如何使用`Seq.groupBy`进行分区成三组具有不同的密钥值 0、 1 和 2 的从 1 到 100 的数字序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-229">The following code example shows the use of `Seq.groupBy` to partition the sequence of numbers from 1 to 100 into three groups that have the distinct key values 0, 1, and 2.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

<span data-ttu-id="c6e00-230">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c6e00-230">The output is as follows.</span></span>

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

<span data-ttu-id="c6e00-231">可以创建一个序列，其中通过调用来消除重复元素[Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401)。</span><span class="sxs-lookup"><span data-stu-id="c6e00-231">You can create a sequence that eliminates duplicate elements by calling [Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401).</span></span> <span data-ttu-id="c6e00-232">也可以使用[Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75)，其将调用每个元素的键生成函数。</span><span class="sxs-lookup"><span data-stu-id="c6e00-232">Or you can use [Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), which takes a key-generating function to be called on each element.</span></span> <span data-ttu-id="c6e00-233">所产生的序列包含具有唯一键; 对原始序列的元素更高版本生成的早期元素有重复的键的元素将被丢弃。</span><span class="sxs-lookup"><span data-stu-id="c6e00-233">The resulting sequence contains elements of the original sequence that have unique keys; later elements that produce a duplicate key to an earlier element are discarded.</span></span>

<span data-ttu-id="c6e00-234">下面的代码示例演示如何使用`Seq.distinct`。</span><span class="sxs-lookup"><span data-stu-id="c6e00-234">The following code example illustrates the use of `Seq.distinct`.</span></span> <span data-ttu-id="c6e00-235">`Seq.distinct` 通过生成序列表示二进制数字，然后显示仅非重复元素为 0 和 1 所示。</span><span class="sxs-lookup"><span data-stu-id="c6e00-235">`Seq.distinct` is demonstrated by generating sequences that represent binary numbers, and then showing that the only distinct elements are 0 and 1.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

<span data-ttu-id="c6e00-236">下面的代码演示`Seq.distinctBy`开始使用一个序列，其中包含负数和正数和使用绝对值函数作为键生成函数。</span><span class="sxs-lookup"><span data-stu-id="c6e00-236">The following code demonstrates `Seq.distinctBy` by starting with a sequence that contains negative and positive numbers and using the absolute value function as the key-generating function.</span></span> <span data-ttu-id="c6e00-237">缺少对应的负号在序列中，因为负号前面顺序显示，因此选择而不是具有相同的绝对的正号的所有正号所产生的序列。值或项。</span><span class="sxs-lookup"><span data-stu-id="c6e00-237">The resulting sequence is missing all the positive numbers that correspond to the negative numbers in the sequence, because the negative numbers appear earlier in the sequence and therefore are selected instead of the positive numbers that have the same absolute value, or key.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a><span data-ttu-id="c6e00-238">在 Readonly 和缓存的序列</span><span class="sxs-lookup"><span data-stu-id="c6e00-238">Readonly and Cached Sequences</span></span>

<span data-ttu-id="c6e00-239">[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7)创建序列的只读副本。</span><span class="sxs-lookup"><span data-stu-id="c6e00-239">[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) creates a read-only copy of a sequence.</span></span> <span data-ttu-id="c6e00-240">`Seq.readonly` 有读写集合，如数组，并且你不想要修改原始集合时很有用。</span><span class="sxs-lookup"><span data-stu-id="c6e00-240">`Seq.readonly` is useful when you have a read-write collection, such as an array, and you do not want to modify the original collection.</span></span> <span data-ttu-id="c6e00-241">此函数可用于保留数据封装。</span><span class="sxs-lookup"><span data-stu-id="c6e00-241">This function can be used to preserve data encapsulation.</span></span> <span data-ttu-id="c6e00-242">在下面的代码示例中，创建包含数组的类型。</span><span class="sxs-lookup"><span data-stu-id="c6e00-242">In the following code example, a type that contains an array is created.</span></span> <span data-ttu-id="c6e00-243">属性公开的数组，但而不是返回一个数组，它将返回一个序列，其中通过使用从该数组创建`Seq.readonly`。</span><span class="sxs-lookup"><span data-stu-id="c6e00-243">A property exposes the array, but instead of returning an array, it returns a sequence that is created from the array by using `Seq.readonly`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

<span data-ttu-id="c6e00-244">[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0)创建序列的存储的版本。</span><span class="sxs-lookup"><span data-stu-id="c6e00-244">[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) creates a stored version of a sequence.</span></span> <span data-ttu-id="c6e00-245">使用`Seq.cache`以避免重新计算的序列，或如果你具有多个线程使用一个序列，但您必须确保每个元素执行操作时只进行一次。</span><span class="sxs-lookup"><span data-stu-id="c6e00-245">Use `Seq.cache` to avoid reevaluation of a sequence, or when you have multiple threads that use a sequence, but you must make sure that each element is acted upon only one time.</span></span> <span data-ttu-id="c6e00-246">如果您正由多个线程的序列，可以有一个线程的枚举，并计算原始序列的值，剩余线程可以使用缓存的序列。</span><span class="sxs-lookup"><span data-stu-id="c6e00-246">When you have a sequence that is being used by multiple threads, you can have one thread that enumerates and computes the values for the original sequence, and remaining threads can use the cached sequence.</span></span>

## <a name="performing-computations-on-sequences"></a><span data-ttu-id="c6e00-247">对序列执行计算</span><span class="sxs-lookup"><span data-stu-id="c6e00-247">Performing Computations on Sequences</span></span>

<span data-ttu-id="c6e00-248">简单的算术运算与其类似的列表，如[Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8)， [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a)， [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8)， [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)，依次类推。</span><span class="sxs-lookup"><span data-stu-id="c6e00-248">Simple arithmetic operations are like those of lists, such as [Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1), and so on.</span></span>

<span data-ttu-id="c6e00-249">[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3)， [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)，和[Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e)是否与所提供的列表的相应函数类似。</span><span class="sxs-lookup"><span data-stu-id="c6e00-249">[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), and [Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) are like the corresponding functions that are available for lists.</span></span> <span data-ttu-id="c6e00-250">序列支持列出了支持这些函数的完整的变体的子集。</span><span class="sxs-lookup"><span data-stu-id="c6e00-250">Sequences support a subset of the full variations of these functions that lists support.</span></span> <span data-ttu-id="c6e00-251">有关详细信息和示例，请参阅[列出了](lists.md)。</span><span class="sxs-lookup"><span data-stu-id="c6e00-251">For more information and examples, see [Lists](lists.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6e00-252">请参阅</span><span class="sxs-lookup"><span data-stu-id="c6e00-252">See also</span></span>

- [<span data-ttu-id="c6e00-253">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="c6e00-253">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c6e00-254">F# 类型</span><span class="sxs-lookup"><span data-stu-id="c6e00-254">F# Types</span></span>](fsharp-types.md)
