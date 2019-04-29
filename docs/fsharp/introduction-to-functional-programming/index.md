---
title: F# 中的函数编程简介
description: 了解基础知识中的函数编程F#。
ms.date: 10/29/2018
ms.openlocfilehash: 84022e58c0f17b9e9875402c653c31e494e940da
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772783"
---
# <a name="introduction-to-functional-programming-in-f"></a><span data-ttu-id="9e2f6-103">F 中的函数编程简介\#</span><span class="sxs-lookup"><span data-stu-id="9e2f6-103">Introduction to Functional Programming in F\#</span></span>

<span data-ttu-id="9e2f6-104">函数编程是编程的一种样式的强调的函数和不可变数据使用。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-104">Functional programming is a style of programming that emphasizes the use of functions and immutable data.</span></span> <span data-ttu-id="9e2f6-105">类型化的函数编程是函数编程与结合使用时与静态类型，如F#。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-105">Typed functional programming is when functional programming is combined with static types, such as with F#.</span></span> <span data-ttu-id="9e2f6-106">一般情况下，在函数式编程强调了以下概念：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-106">In general, the following concepts are emphasized in functional programming:</span></span>

* <span data-ttu-id="9e2f6-107">为你使用的主构造函数</span><span class="sxs-lookup"><span data-stu-id="9e2f6-107">Functions as the primary constructs you use</span></span>
* <span data-ttu-id="9e2f6-108">而不是语句表达式</span><span class="sxs-lookup"><span data-stu-id="9e2f6-108">Expressions instead of statements</span></span>
* <span data-ttu-id="9e2f6-109">通过变量的不可变值</span><span class="sxs-lookup"><span data-stu-id="9e2f6-109">Immutable values over variables</span></span>
* <span data-ttu-id="9e2f6-110">通过命令性编程的声明性编程</span><span class="sxs-lookup"><span data-stu-id="9e2f6-110">Declarative programming over imperative programming</span></span>

<span data-ttu-id="9e2f6-111">本系列文章将探讨概念和模式中功能的编程使用F#。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-111">Throughout this series, you'll explore concepts and patterns in functional programming using F#.</span></span> <span data-ttu-id="9e2f6-112">此过程中，你将了解一些F#过。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-112">Along the way, you'll learn some F# too.</span></span>

## <a name="terminology"></a><span data-ttu-id="9e2f6-113">术语</span><span class="sxs-lookup"><span data-stu-id="9e2f6-113">Terminology</span></span>

<span data-ttu-id="9e2f6-114">函数编程，如其他编程范例中，附带了你最终需要了解的词汇。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-114">Functional programming, like other programming paradigms, comes with a vocabulary that you will eventually need to learn.</span></span> <span data-ttu-id="9e2f6-115">下面是您将看到所有时间的一些常见术语：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-115">Here are some common terms you'll see all of the time:</span></span>

* <span data-ttu-id="9e2f6-116">**函数**-函数是一个构造，它将生成在给定输入的输出。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-116">**Function** - A function is a construct that will produce an output when given an input.</span></span> <span data-ttu-id="9e2f6-117">更准确地讲，它_映射_从一个项设置为另一组。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-117">More formally, it _maps_ an item from one set to another set.</span></span> <span data-ttu-id="9e2f6-118">特别是使用操作的函数的多个数据集合时，此打击被提升到在许多方面，具体。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-118">This formalism is lifted into the concrete in many ways, especially when using functions that operate on collections of data.</span></span> <span data-ttu-id="9e2f6-119">它是最基本 （且重要） 中的功能性编程概念。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-119">It is the most basic (and important) concept in functional programming.</span></span> 
* <span data-ttu-id="9e2f6-120">**表达式**-表达式是所生成的值的代码中的构造。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-120">**Expression** - An expression is a construct in code that produces a value.</span></span> <span data-ttu-id="9e2f6-121">在F#，必须绑定或显式忽略此值。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-121">In F#, this value must be bound or explicitly ignored.</span></span> <span data-ttu-id="9e2f6-122">表达式可以不费力地替换为函数调用。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-122">An expression can be trivially replaced by a function call.</span></span>
* <span data-ttu-id="9e2f6-123">**纯度**-纯度是函数的属性，以便其返回值始终是相同的相同的参数，且其评估没有任何副作用。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-123">**Purity** - Purity is a property of a function such that its return value is always the same for the same arguments, and that its evaluation has no side effects.</span></span> <span data-ttu-id="9e2f6-124">纯函数完全取决于其参数。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-124">A pure function depends entirely on its arguments.</span></span>
* <span data-ttu-id="9e2f6-125">**引用透明度**-引用透明度是表达式的属性，以便它们可以被替换为相应的输出而不会影响程序的行为。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-125">**Referential Transparency** - Referential Transparency is a property of expressions such that they can be replaced with their output without affecting a program's behavior.</span></span>
* <span data-ttu-id="9e2f6-126">**不变性**的不可变性意味着值不能更改就地。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-126">**Immutability** - Immutability means that a value cannot be changed in-place.</span></span> <span data-ttu-id="9e2f6-127">这是与变量，可以更改在位置不同。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-127">This is in contrast with variables, which can change in place.</span></span>

## <a name="examples"></a><span data-ttu-id="9e2f6-128">示例</span><span class="sxs-lookup"><span data-stu-id="9e2f6-128">Examples</span></span>

<span data-ttu-id="9e2f6-129">下面的示例演示这些核心概念。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-129">The following examples demonstrate these core concepts.</span></span>

### <a name="functions"></a><span data-ttu-id="9e2f6-130">函数</span><span class="sxs-lookup"><span data-stu-id="9e2f6-130">Functions</span></span>

<span data-ttu-id="9e2f6-131">最基本的常用在函数式编程构造是函数。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-131">The most common and fundamental construct in functional programming is the function.</span></span> <span data-ttu-id="9e2f6-132">下面是将 1 添加到整数的简单函数：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-132">Here's a simple function that adds 1 to an integer:</span></span>

```fsharp
let addOne x = x + 1
```

<span data-ttu-id="9e2f6-133">其类型签名如下所示：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-133">Its type signature is as follows:</span></span>

```fsharp
val addOne: x:int -> int
```

<span data-ttu-id="9e2f6-134">签名可以读取，为"`addOne`接受`int`名为`x`，将产生`int`"。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-134">The signature can be read as, "`addOne` accepts an `int` named `x` and will produce an `int`".</span></span> <span data-ttu-id="9e2f6-135">更准确地讲`addOne`是_映射_到的一组整数之间的一组整数的值。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-135">More formally, `addOne` is _mapping_ a value from the set of integers to the set of integers.</span></span> <span data-ttu-id="9e2f6-136">`->`令牌表示此映射。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-136">The `->` token signifies this mapping.</span></span> <span data-ttu-id="9e2f6-137">在F#，则通常可在函数签名，了解有关它的功能查看。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-137">In F#, you can usually look at the function signature to get a sense for what it does.</span></span>

<span data-ttu-id="9e2f6-138">因此，为何重要的签名？</span><span class="sxs-lookup"><span data-stu-id="9e2f6-138">So, why is the signature important?</span></span> <span data-ttu-id="9e2f6-139">在类型化函数式编程的一个函数实现小于通常比实际类型签名重要 ！</span><span class="sxs-lookup"><span data-stu-id="9e2f6-139">In typed functional programming, the implementation of a function is often less important than the actual type signature!</span></span> <span data-ttu-id="9e2f6-140">这一事实，`addOne`添加到一个整数值 1 是在运行时，有趣，但当构造一个程序，这一事实，它接受并返回`int`是什么就是告知如何实际将使用此函数。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-140">The fact that `addOne` adds the value 1 to an integer is interesting at runtime, but when you are constructing a program, the fact that it accepts and returns an `int` is what informs how you will actually use this function.</span></span> <span data-ttu-id="9e2f6-141">此外，一旦您使用正确 （根据其类型签名） 的此函数，诊断任何问题可以仅在的正文内`addOne`函数。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-141">Furthermore, once you use this function correctly (with respect to its type signature), diagnosing any problems can be done only within the body of the `addOne` function.</span></span> <span data-ttu-id="9e2f6-142">这是类型化函数式编程力。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-142">This is the impetus behind typed functional programming.</span></span>

### <a name="expressions"></a><span data-ttu-id="9e2f6-143">表达式</span><span class="sxs-lookup"><span data-stu-id="9e2f6-143">Expressions</span></span>

<span data-ttu-id="9e2f6-144">表达式是计算出值的构造。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-144">Expressions are constructs that evaluate to a value.</span></span> <span data-ttu-id="9e2f6-145">与语句执行的操作，可以执行并发回一个值的操作被视为表达式。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-145">In contrast to statements, which perform an action, expressions can be thought of performing an action that gives back a value.</span></span> <span data-ttu-id="9e2f6-146">几乎总是以支持函数编程中的语句中使用表达式。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-146">Expressions are almost always used in favor of statements in functional programming.</span></span>

<span data-ttu-id="9e2f6-147">上一个函数，请考虑`addOne`。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-147">Consider the previous function, `addOne`.</span></span> <span data-ttu-id="9e2f6-148">正文`addOne`是一个表达式：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-148">The body of `addOne` is an expression:</span></span>

```fsharp
// 'x + 1' is an expression!
let addOne x = x + 1
```

<span data-ttu-id="9e2f6-149">它是此定义的结果类型的表达式的结果`addOne`函数。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-149">It is the result of this expression that defines the result type of the `addOne` function.</span></span> <span data-ttu-id="9e2f6-150">例如，构成此函数的表达式无法更改以是不同的类型，如`string`:</span><span class="sxs-lookup"><span data-stu-id="9e2f6-150">For example, the expression that makes up this function could be changed to be a different type, such as a `string`:</span></span>

```fsharp
let addOne x = x.ToString() + "1"
```

<span data-ttu-id="9e2f6-151">现在，函数的签名是：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-151">The signature of the function is now:</span></span>

```fsharp
val addOne: x:'a -> string
```

<span data-ttu-id="9e2f6-152">由于中的任何类型F#可以具有`ToString()`对它的类型调用`x`变得通用 (称为[自动泛化](../language-reference/generics/automatic-generalization.md))，和结果类型将是`string`。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-152">Since any type in F# can have `ToString()` called on it, the type of `x` has been made generic (called [Automatic Generalization](../language-reference/generics/automatic-generalization.md)), and the resultant type is a `string`.</span></span>

<span data-ttu-id="9e2f6-153">表达式不是只是函数的正文。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-153">Expressions are not just the bodies of functions.</span></span> <span data-ttu-id="9e2f6-154">您可以生成其他位置使用的值的表达式。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-154">You can have expressions that produce a value you use elsewhere.</span></span> <span data-ttu-id="9e2f6-155">一个是一种常见`if`:</span><span class="sxs-lookup"><span data-stu-id="9e2f6-155">A common one is `if`:</span></span>

```fsharp
// Checks if 'x' is odd by using the mod operator
let isOdd x = x % 2 <> 0

let addOneIfOdd input =
    let result =
        if isOdd input then
            input + 1
        else
            input

    result
```

<span data-ttu-id="9e2f6-156">`if`表达式会生成名为的值`result`。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-156">The `if` expression produces a value called `result`.</span></span> <span data-ttu-id="9e2f6-157">请注意，可以省略`result`完全，使`if`表达式主体的`addOneIfOdd`函数。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-157">Note that you could omit `result` entirely, making the `if` expression the body of the `addOneIfOdd` function.</span></span> <span data-ttu-id="9e2f6-158">需要记住有关表达式的关键一点是，它们生成值。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-158">The key thing to remember about expressions is that they produce a value.</span></span>

<span data-ttu-id="9e2f6-159">没有一种特殊类型， `unit`，当没有要返回内容时使用。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-159">There is a special type, `unit`, that is used when there is nothing to return.</span></span> <span data-ttu-id="9e2f6-160">例如，考虑此简单函数：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-160">For example, consider this simple function:</span></span>

```fsharp
let printString (str: string) =
    printfn "String is: %s" str
```

<span data-ttu-id="9e2f6-161">签名如下所示：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-161">The signature looks like this:</span></span>

```fsharp
val printString: str:string -> unit
```

<span data-ttu-id="9e2f6-162">`unit`类型表示不返回任何实际值。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-162">The `unit` type indicates that there is no actual value being returned.</span></span> <span data-ttu-id="9e2f6-163">这是很有用，有时必须例程"正常运行"尽管没有要返回该工作的值。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-163">This is useful when you have a routine that must "do work" despite having no value to return as a result of that work.</span></span>

<span data-ttu-id="9e2f6-164">这是与命令式编程中，到在其中等效`if`构造是一个语句，并生成值通常是与转变变量。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-164">This is in sharp contrast to imperative programming, where the equivalent `if` construct is a statement, and producing values is often done with mutating variables.</span></span> <span data-ttu-id="9e2f6-165">例如，在C#，可能会像这样编写的代码：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-165">For example, in C#, the code might be written like this:</span></span>

```csharp
bool IsOdd(int x) => x % 2 != 0;

int AddOneIfOdd(int input)
{
    var result = input;

    if (IsOdd(input))
    {
        result = input + 1;
    }

    return result;
}
```

<span data-ttu-id="9e2f6-166">值得注意的是C#和其他 C 风格语言支持[三元表达式](../../csharp/language-reference/operators/conditional-operator.md)，这样可以基于表达式的条件性编程。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-166">It's worth noting that C# and other C-style languages do support the [ternary expression](../../csharp/language-reference/operators/conditional-operator.md), which allows for expression-based conditional programming.</span></span>

<span data-ttu-id="9e2f6-167">在函数式编程，很难改变语句的值。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-167">In functional programming, it is rare to mutate values with statements.</span></span> <span data-ttu-id="9e2f6-168">虽然一些函数式语言支持语句和变化，但它不是通常在函数式编程中使用这些概念。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-168">Although some functional languages support statements and mutation, it is not common to use these concepts in functional programming.</span></span>

### <a name="pure-functions"></a><span data-ttu-id="9e2f6-169">纯函数</span><span class="sxs-lookup"><span data-stu-id="9e2f6-169">Pure functions</span></span>

<span data-ttu-id="9e2f6-170">如前面所述，纯函数是函数：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-170">As previously mentioned, pure functions are functions that:</span></span>

* <span data-ttu-id="9e2f6-171">计算结果始终为同一输入相同的值。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-171">Always evaluate to the same value for the same input.</span></span>
* <span data-ttu-id="9e2f6-172">有没有负面影响。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-172">Have no side effects.</span></span>

<span data-ttu-id="9e2f6-173">它是需要考虑在此上下文中的数学函数。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-173">It is helpful to think of mathematical functions in this context.</span></span> <span data-ttu-id="9e2f6-174">在数学中，函数只能依赖于其参数，但没有任何副作用。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-174">In mathematics, functions depend only on their arguments and do not have any side effects.</span></span> <span data-ttu-id="9e2f6-175">数学函数中`f(x) = x + 1`，值`f(x)`仅取决于值`x`。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-175">In the mathematical function `f(x) = x + 1`, the value of `f(x)` depends only on the value of `x`.</span></span> <span data-ttu-id="9e2f6-176">在函数式编程的纯函数是相同的方式。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-176">Pure functions in functional programming are the same way.</span></span>

<span data-ttu-id="9e2f6-177">在编写纯函数，函数必须只能依赖于其参数并不执行任何操作产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-177">When writing a pure function, the function must depend only on its arguments and not perform any action that results in a side effect.</span></span>

<span data-ttu-id="9e2f6-178">因为它取决于全局、 可变状态，下面是一个非纯函数的示例：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-178">Here is an example of a non-pure function because it depends on global, mutable state:</span></span>

```fsharp
let mutable value = 1

let addOneToValue x = x + value
```

<span data-ttu-id="9e2f6-179">`addOneToValue`函数是清楚地非纯，因为`value`可以具有不同的值多于 1 随时可能更改。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-179">The `addOneToValue` function is clearly impure, because `value` could be changed at any time to have a different value than 1.</span></span> <span data-ttu-id="9e2f6-180">具体取决于全局值的模式是避免在函数式编程。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-180">This pattern of depending on a global value is to be avoided in functional programming.</span></span>

<span data-ttu-id="9e2f6-181">下面是的非纯函数，另一个示例，因为它执行副作用：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-181">Here is another example of a non-pure function, because it performs a side effect:</span></span>

```fsharp
let addOneToValue x = 
    printfn "x is %d" x
    x + 1
```

<span data-ttu-id="9e2f6-182">尽管此函数不依赖于全局值，但它的值写入`x`到程序的输出。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-182">Although this function does not depend on a global value, it writes the value of `x` to the output of the program.</span></span> <span data-ttu-id="9e2f6-183">尽管没有任何问题本质上是执行此操作，但它意味着该函数不是纯。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-183">Although there is nothing inherently wrong with doing this, it does mean that the function is not pure.</span></span> <span data-ttu-id="9e2f6-184">如果您的程序的另一个部分依赖于外部程序，例如输出缓冲区的内容然后调用此函数会影响您的程序的其他部分。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-184">If another part of your program depends on something external to the program, such as the output buffer, then calling this function can affect that other part of your program.</span></span>

<span data-ttu-id="9e2f6-185">删除`printfn`语句使纯函数：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-185">Removing the `printfn` statement makes the function pure:</span></span>

```fsharp
let addOneToValue x = x + 1
```

<span data-ttu-id="9e2f6-186">尽管此函数本身不是_更好地_与早期版本相比`printfn`语句，它确实保证此函数的唯一用途是返回值。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-186">Although this function is not inherently _better_ than the previous version with the `printfn` statement, it does guarantee that all this function does is return a value.</span></span> <span data-ttu-id="9e2f6-187">多次调用此函数生成的结果相同： 它只是产生一个值。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-187">Calling this function any number of times produces the same result: it just produces a value.</span></span> <span data-ttu-id="9e2f6-188">由纯度给定可预测性是许多的功能性编程人员梦寐以求的目标。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-188">The predictability given by purity is something many functional programmers strive for.</span></span>

### <a name="immutability"></a><span data-ttu-id="9e2f6-189">不可变性</span><span class="sxs-lookup"><span data-stu-id="9e2f6-189">Immutability</span></span>

<span data-ttu-id="9e2f6-190">最后，类型化函数式编程的最基本的概念之一是不可变性。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-190">Finally, one of the most fundamental concepts of typed functional programming is immutability.</span></span> <span data-ttu-id="9e2f6-191">在F#，所有值都是默认固定不变。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-191">In F#, all values are immutable by default.</span></span> <span data-ttu-id="9e2f6-192">这意味着它们不能是就地转变，除非显式将其标记为可变。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-192">That means they cannot be mutated in-place unless you explicitly mark them as mutable.</span></span>

<span data-ttu-id="9e2f6-193">在实践中，使用不可变值意味着从，"我需要更改某些内容"更改为编程所用的方法，向"我需要生成新值"。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-193">In practice, working with immutable values means that you change your approach to programming from, "I need to change something", to "I need to produce a new value".</span></span>

<span data-ttu-id="9e2f6-194">例如，添加为值 1 表示生成新值，不改变现有从而：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-194">For example, adding 1 to a value means producing a new value, not mutating the existing one:</span></span>

```fsharp
let value = 1
let secondValue = value + 1
```

<span data-ttu-id="9e2f6-195">在F#，以下代码所示**不**改变`value`函数; 相反，它将执行相等性检查：</span><span class="sxs-lookup"><span data-stu-id="9e2f6-195">In F#, the following code does **not** mutate the `value` function; instead, it performs an equality check:</span></span>

```fsharp
let value = 1
value = value + 1 // Produces a 'bool' value!
```

<span data-ttu-id="9e2f6-196">一些函数式编程语言不在所有支持的变化。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-196">Some functional programming languages do not support mutation at all.</span></span> <span data-ttu-id="9e2f6-197">在F#，它受支持，但它不是值的默认行为。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-197">In F#, it is supported, but it is not the default behavior for values.</span></span>

<span data-ttu-id="9e2f6-198">甚至数据结构可以进一步扩展了这一概念。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-198">This concept extends even further to data structures.</span></span> <span data-ttu-id="9e2f6-199">在函数式编程，不可变数据结构如集 （和更多） 具有不同的实现，最初可能比预期。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-199">In functional programming, immutable data structures such as sets (and many more) have a different implementation than you might initially expect.</span></span> <span data-ttu-id="9e2f6-200">从概念上讲，内容如将项添加到一组不会更改集，它会生成_新_设置为已添加值。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-200">Conceptually, something like adding an item to a set does not change the set, it produces a _new_ set with the added value.</span></span> <span data-ttu-id="9e2f6-201">实际上，这是通常通过实现可用于有效地跟踪一个值，以便可以作为结果提供适当的表示形式的数据的不同的数据结构。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-201">Under the covers, this is often accomplished by a different data structure that allows for efficiently tracking a value so that the appropriate representation of the data can be given as a result.</span></span>

<span data-ttu-id="9e2f6-202">这种处理值和数据结构至关重要，因为它会强制您将修改内容，如同其创建该操作的新版本的任何操作。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-202">This style of working with values and data structures is critical, as it forces you to treat any operation that modifies something as if it creates a new version of that thing.</span></span> <span data-ttu-id="9e2f6-203">这允许诸如相等性和可比性等的项目为您的程序中保持一致。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-203">This allows for things like equality and comparability to be consistent in your programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9e2f6-204">后续步骤</span><span class="sxs-lookup"><span data-stu-id="9e2f6-204">Next steps</span></span>

<span data-ttu-id="9e2f6-205">下一步部分全面介绍函数，探索函数编程中使用它们的不同方式。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-205">The next section will thoroughly cover functions, exploring different ways you can use them in functional programming.</span></span>

<span data-ttu-id="9e2f6-206">[第一类函数](first-class-functions.md)探讨功能深，显示如何在不同上下文中使用它们。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-206">[First-class functions](first-class-functions.md) explores functions deeply, showing how you can use them in various contexts.</span></span>

## <a name="further-reading"></a><span data-ttu-id="9e2f6-207">其他阅读材料</span><span class="sxs-lookup"><span data-stu-id="9e2f6-207">Further reading</span></span>

<span data-ttu-id="9e2f6-208">[想就功能而言](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/)系列是另一个很好的资源，若要了解有关函数编程与F#。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-208">The [Thinking Functionally](https://fsharpforfunandprofit.com/posts/thinking-functionally-intro/) series is another great resource to learn about functional programming with F#.</span></span> <span data-ttu-id="9e2f6-209">它涵盖的功能性编程基础知识中以实用且易于理解的方式，使用F#功能来阐明这些概念。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-209">It covers fundamentals of functional programming in a pragmatic and easy-to-read way, using F# features to illustrate the concepts.</span></span>
