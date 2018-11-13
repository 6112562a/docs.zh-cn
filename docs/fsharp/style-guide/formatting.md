---
title: F# 代码格式设置准则
description: 了解有关格式设置 F# 代码的指导原则。
ms.date: 05/14/2018
ms.openlocfilehash: 0d7d2d1771710db55bf990f3a06079b2aec48fd7
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/02/2018
ms.locfileid: "43858000"
---
# <a name="f-code-formatting-guidelines"></a><span data-ttu-id="6a884-103">F# 代码格式设置准则</span><span class="sxs-lookup"><span data-stu-id="6a884-103">F# code formatting guidelines</span></span>

<span data-ttu-id="6a884-104">本文提供有关如何设置代码格式，使 F# 代码的指导原则：</span><span class="sxs-lookup"><span data-stu-id="6a884-104">This article offers guidelines for how to format your code so that your F# code is:</span></span>

* <span data-ttu-id="6a884-105">通常以更清晰的形式查看</span><span class="sxs-lookup"><span data-stu-id="6a884-105">Generally viewed as more legible</span></span>
* <span data-ttu-id="6a884-106">符合应用的 Visual Studio 中的工具和其他编辑器格式设置约定</span><span class="sxs-lookup"><span data-stu-id="6a884-106">Is in accordance with conventions applied by formatting tools in Visual Studio and other editors</span></span>
* <span data-ttu-id="6a884-107">类似于其他代码联机</span><span class="sxs-lookup"><span data-stu-id="6a884-107">Similar to other code online</span></span>

<span data-ttu-id="6a884-108">这些指导基于[F# 格式设置约定的全面指南](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md)通过[Anh Dung Phan](https://github.com/dungpa)。</span><span class="sxs-lookup"><span data-stu-id="6a884-108">These guidelines are based on [A comprehensive guide to F# Formatting Conventions](https://github.com/dungpa/fantomas/blob/master/docs/FormattingConventions.md) by [Anh-Dung Phan](https://github.com/dungpa).</span></span>

## <a name="general-rules-for-indentation"></a><span data-ttu-id="6a884-109">缩进的一般规则</span><span class="sxs-lookup"><span data-stu-id="6a884-109">General rules for indentation</span></span>

<span data-ttu-id="6a884-110">F# 默认情况下使用有意义的空白。</span><span class="sxs-lookup"><span data-stu-id="6a884-110">F# uses significant white space by default.</span></span> <span data-ttu-id="6a884-111">以下指南旨在提供指导如何能够同时处理这可以施加一些挑战。</span><span class="sxs-lookup"><span data-stu-id="6a884-111">The following guidelines are intended to provide guidance as to how to juggle some challenges this can impose.</span></span>

### <a name="using-spaces"></a><span data-ttu-id="6a884-112">使用的空间</span><span class="sxs-lookup"><span data-stu-id="6a884-112">Using spaces</span></span>

<span data-ttu-id="6a884-113">需要缩进时，您必须使用空格，不是制表符。</span><span class="sxs-lookup"><span data-stu-id="6a884-113">When indentation is required, you must use spaces, not tabs.</span></span> <span data-ttu-id="6a884-114">至少一个空间是必需的。</span><span class="sxs-lookup"><span data-stu-id="6a884-114">At least one space is required.</span></span> <span data-ttu-id="6a884-115">你的组织可以创建以指定要用于缩进; 的空格数的编码标准典型的缩进发生每个级别的缩进的两个、 三个或四个空格。</span><span class="sxs-lookup"><span data-stu-id="6a884-115">Your organization can create coding standards to specify the number of spaces to use for indentation; two, three or four spaces of indentation at each level where indentation occurs is typical.</span></span>

<span data-ttu-id="6a884-116">**我们建议每个缩进的 4 个空格。**</span><span class="sxs-lookup"><span data-stu-id="6a884-116">**We recommend 4 spaces per indentation.**</span></span>

<span data-ttu-id="6a884-117">也就是说，缩进的程序是一个主观问题。</span><span class="sxs-lookup"><span data-stu-id="6a884-117">That said, indentation of programs is a subjective matter.</span></span> <span data-ttu-id="6a884-118">变体是好的但应遵循的第一个规则*缩进的一致性*。</span><span class="sxs-lookup"><span data-stu-id="6a884-118">Variations are OK, but the first rule you should follow is *consistency of indentation*.</span></span> <span data-ttu-id="6a884-119">选择一种普遍接受的缩进样式，并在整个代码库系统地使用它。</span><span class="sxs-lookup"><span data-stu-id="6a884-119">Choose a generally accepted style of indentation and use it systematically throughout your codebase.</span></span>

## <a name="formatting-blank-lines"></a><span data-ttu-id="6a884-120">格式设置的空行</span><span class="sxs-lookup"><span data-stu-id="6a884-120">Formatting blank lines</span></span>

* <span data-ttu-id="6a884-121">单独顶级函数和类定义包含两个空白行。</span><span class="sxs-lookup"><span data-stu-id="6a884-121">Separate top-level function and class definitions with two blank lines.</span></span>
* <span data-ttu-id="6a884-122">方法定义的类的内部由一个空行分隔。</span><span class="sxs-lookup"><span data-stu-id="6a884-122">Method definitions inside a class are separated by a single blank line.</span></span>
* <span data-ttu-id="6a884-123">可能会 （谨慎） 使用额外的空白行到单独的组相关的函数。</span><span class="sxs-lookup"><span data-stu-id="6a884-123">Extra blank lines may be used (sparingly) to separate groups of related functions.</span></span> <span data-ttu-id="6a884-124">一系列相关一行式命令 （例如，一组虚拟实现） 之间，可以忽略空白行。</span><span class="sxs-lookup"><span data-stu-id="6a884-124">Blank lines may be omitted between a bunch of related one-liners (for example, a set of dummy implementations).</span></span>
* <span data-ttu-id="6a884-125">使用空白行在函数中，尽量少，以指示逻辑部分。</span><span class="sxs-lookup"><span data-stu-id="6a884-125">Use blank lines in functions, sparingly, to indicate logical sections.</span></span>

## <a name="formatting-comments"></a><span data-ttu-id="6a884-126">格式设置的注释</span><span class="sxs-lookup"><span data-stu-id="6a884-126">Formatting comments</span></span>

<span data-ttu-id="6a884-127">通常将多个双斜杠注释为首 ML 样式块注释。</span><span class="sxs-lookup"><span data-stu-id="6a884-127">Generally prefer multiple double-slash comments over ML-style block comments.</span></span>

```fsharp
// Prefer this style of comments when you want
// to express written ideas on multiple lines.

(*
    ML-style comments are fine, but not a .NET-ism.
    They are useful when needing to modify multi-line comments, though.
*)
```

<span data-ttu-id="6a884-128">内联注释应的首字母大写。</span><span class="sxs-lookup"><span data-stu-id="6a884-128">Inline comments should capitalize the first letter.</span></span>

```fsharp
let f x = x + 1 // Increment by one.
```

## <a name="naming-conventions"></a><span data-ttu-id="6a884-129">命名约定</span><span class="sxs-lookup"><span data-stu-id="6a884-129">Naming conventions</span></span>

### <a name="use-camelcase-for-class-bound-expression-bound-and-pattern-bound-values-and-functions"></a><span data-ttu-id="6a884-130">使用驼峰式大小写的类绑定、 表达式绑定和绑定模式的值和函数</span><span class="sxs-lookup"><span data-stu-id="6a884-130">Use camelCase for class-bound, expression-bound and pattern-bound values and functions</span></span>

<span data-ttu-id="6a884-131">通常，并接受的 F# 样式的所有名称使用驼峰式大小写绑定为本地变量或在模式匹配和函数定义。</span><span class="sxs-lookup"><span data-stu-id="6a884-131">It is common and accepted F# style to use camelCase for all names bound as local variables or in pattern matches and function definitions.</span></span>

```fsharp
// OK
let addIAndJ i j = i + j

// Bad
let addIAndJ I J = I+J

// Bad
let AddIAndJ i j = i + j
```

<span data-ttu-id="6a884-132">本地绑定类中的函数还应使用驼峰式大小写。</span><span class="sxs-lookup"><span data-stu-id="6a884-132">Locally-bound functions in classes should also use camelCase.</span></span>

```fsharp
type MyClass() =

    let doSomething () =

    let firstResult = ...

    let secondResult = ...

    member x.Result = doSomething()
```

### <a name="use-camelcase-for-module-bound-public-functions"></a><span data-ttu-id="6a884-133">有关绑定到模块的公共函数使用驼峰式大小写</span><span class="sxs-lookup"><span data-stu-id="6a884-133">Use camelCase for module-bound public functions</span></span>

<span data-ttu-id="6a884-134">当模块绑定函数是一个公共 API 的一部分时，它应使用驼峰式大小写：</span><span class="sxs-lookup"><span data-stu-id="6a884-134">When a module-bound function is part of a public API, it should use camelCase:</span></span>

```fsharp
module MyAPI =
    let publicFunctionOne param1 param2 param2 = ...

    let publicFunctionTwo param1 param2 param3 = ...
```

### <a name="use-camelcase-for-internal-and-private-module-bound-values-and-functions"></a><span data-ttu-id="6a884-135">使用驼峰式大小写的内部和专用模块绑定值和函数</span><span class="sxs-lookup"><span data-stu-id="6a884-135">Use camelCase for internal and private module-bound values and functions</span></span>

<span data-ttu-id="6a884-136">对于专用模块绑定值，其中包括使用驼峰式大小写：</span><span class="sxs-lookup"><span data-stu-id="6a884-136">Use camelCase for private module-bound values, including the following:</span></span>

* <span data-ttu-id="6a884-137">在脚本中的即席函数</span><span class="sxs-lookup"><span data-stu-id="6a884-137">Ad hoc functions in scripts</span></span>

* <span data-ttu-id="6a884-138">值组成的模块或类型的内部实现</span><span class="sxs-lookup"><span data-stu-id="6a884-138">Values making up the internal implementation of a module or type</span></span>

```fsharp
let emailMyBossTheLatestResults =
    ...
```

### <a name="use-camelcase-for-parameters"></a><span data-ttu-id="6a884-139">对参数使用驼峰式大小写</span><span class="sxs-lookup"><span data-stu-id="6a884-139">Use camelCase for parameters</span></span>

<span data-ttu-id="6a884-140">所有参数应都使用驼峰式大小写，根据.NET 命名约定。</span><span class="sxs-lookup"><span data-stu-id="6a884-140">All parameters should use camelCase in accordance with .NET naming conventions.</span></span>

```fsharp
module MyModule =
    let myFunction paramOne paramTwo = ...

type MyClass() =
    member this.MyMethod(paramOne, paramTwo) = ...
```

### <a name="use-pascalcase-for-modules"></a><span data-ttu-id="6a884-141">模块使用 pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="6a884-141">Use PascalCase for modules</span></span>

<span data-ttu-id="6a884-142">（顶级、 内部、 专用、 嵌套） 的所有模块都应都使用 pascal 命名法。</span><span class="sxs-lookup"><span data-stu-id="6a884-142">All modules (top-level, internal, private, nested) should use PascalCase.</span></span>

```fsharp
module MyTopLevelModule

module Helpers =
    module private SuperHelpers =
        ...

    ...
```

### <a name="use-pascalcase-for-type-declarations-members-and-labels"></a><span data-ttu-id="6a884-143">类型声明、 成员和标签的使用 pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="6a884-143">Use PascalCase for type declarations, members, and labels</span></span>

<span data-ttu-id="6a884-144">类、 接口、 结构、 枚举、 委托、 记录和可区分的联合所有的命名应当使用 pascal 命名法。</span><span class="sxs-lookup"><span data-stu-id="6a884-144">Classes, interfaces, structs, enumerations, delegates, records, and discriminated unions should all be named with PascalCase.</span></span> <span data-ttu-id="6a884-145">类型和标签的记录和可区分的联合中的成员还应使用 pascal 命名法。</span><span class="sxs-lookup"><span data-stu-id="6a884-145">Members within types and labels for records and discriminated unions should also use PascalCase.</span></span>

```fsharp
type IMyInterface =
    abstract Something: int

type MyClass() =
    member this.MyMethod(x, y) = x + y

type MyRecord = { IntVal: int; StringVal: string }

type SchoolPerson =
    | Professor
    | Student
    | Advisor
    | Administrator
```

### <a name="use-pascalcase-for-constructs-intrinsic-to-net"></a><span data-ttu-id="6a884-146">为.NET 中的内部构造使用 pascal 命名法</span><span class="sxs-lookup"><span data-stu-id="6a884-146">Use PascalCase for constructs intrinsic to .NET</span></span>

<span data-ttu-id="6a884-147">命名空间、 异常、 事件和项目 /`.dll`名称还应使用 pascal 命名法。</span><span class="sxs-lookup"><span data-stu-id="6a884-147">Namespaces, exceptions, events, and project/`.dll` names should also use PascalCase.</span></span> <span data-ttu-id="6a884-148">不仅这会使来自其他.NET 语言的消耗感觉更自然向使用者，也是与你可能会遇到的.NET 命名约定保持一致。</span><span class="sxs-lookup"><span data-stu-id="6a884-148">Not only does this make consumption from other .NET languages feel more natural to consumers, it's also consistent with .NET naming conventions that you are likely to encounter.</span></span>

### <a name="avoid-underscores-in-names"></a><span data-ttu-id="6a884-149">避免在名称中的下划线</span><span class="sxs-lookup"><span data-stu-id="6a884-149">Avoid underscores in names</span></span>

<span data-ttu-id="6a884-150">从历史上看，一些 F# 库具有名称中使用下划线。</span><span class="sxs-lookup"><span data-stu-id="6a884-150">Historically, some F# libraries have used underscores in names.</span></span> <span data-ttu-id="6a884-151">但是，这是不能再广受认可，部分原因是因为它与.NET 命名约定冲突。</span><span class="sxs-lookup"><span data-stu-id="6a884-151">However, this is no longer widely accepted, partly because it clashes with .NET naming conventions.</span></span> <span data-ttu-id="6a884-152">不过，某些 F# 程序员出于历史原因，很大程度、 一定程度上使用下划线和容差和方面非常重要。</span><span class="sxs-lookup"><span data-stu-id="6a884-152">That said, some F# programmers use underscores heavily, partly for historical reasons, and tolerance and respect is important.</span></span> <span data-ttu-id="6a884-153">但是，请注意样式通常会不喜欢的其他用户可以选择要使用它。</span><span class="sxs-lookup"><span data-stu-id="6a884-153">However, be aware that the style is often disliked by others who have a choice about whether to use it.</span></span>

<span data-ttu-id="6a884-154">一些例外情况包括与本机组件交互下划线很常见。</span><span class="sxs-lookup"><span data-stu-id="6a884-154">Some exceptions includes interoperating with native components, where underscores are very common.</span></span>

### <a name="use-standard-f-operators"></a><span data-ttu-id="6a884-155">使用标准 F# 运算符</span><span class="sxs-lookup"><span data-stu-id="6a884-155">Use standard F# operators</span></span>

<span data-ttu-id="6a884-156">以下运算符在 F# 标准库中定义，应使用而不是定义等效项。</span><span class="sxs-lookup"><span data-stu-id="6a884-156">The following operators are defined in the F# standard library and should be used instead of defining equivalents.</span></span> <span data-ttu-id="6a884-157">建议使用这些运算符，因为它往往会使代码更具可读性且惯用。</span><span class="sxs-lookup"><span data-stu-id="6a884-157">Using these operators is recommended as it tends to make code more readable and idiomatic.</span></span> <span data-ttu-id="6a884-158">具有背景的 OCaml 或其他功能的编程语言的开发人员可能习惯于不同编程惯例。</span><span class="sxs-lookup"><span data-stu-id="6a884-158">Developers with a background in OCaml or other functional programming language may be accustomed to different idioms.</span></span> <span data-ttu-id="6a884-159">以下列表总结了建议的 F# 运算符。</span><span class="sxs-lookup"><span data-stu-id="6a884-159">The following list summarizes the recommended F# operators.</span></span>

```fsharp
x |> f // Forward pipeline
f >> g // Forward composition
x |> ignore // Discard away a value
x + y // Overloaded addition (including string concatenation)
x - y // Overloaded subtraction
x * y // Overloaded multiplication
x / y // Overloaded division
x % y // Overloaded modulus
x && y // Lazy/short-cut "and"
x || y // Lazy/short-cut "or"
x <<< y // Bitwise left shift
x >>> y // Bitwise right shift
x ||| y // Bitwise or, also for working with “flags” enumeration
x &&& y // Bitwise and, also for working with “flags” enumeration
x ^^^ y // Bitwise xor, also for working with “flags” enumeration
```

### <a name="use-prefix-syntax-for-generics-foot-in-preference-to-postfix-syntax-t-foo"></a><span data-ttu-id="6a884-160">前缀语法用于泛型 (`Foo<T>`) 优先于后缀语法 (`T Foo`)</span><span class="sxs-lookup"><span data-stu-id="6a884-160">Use prefix syntax for generics (`Foo<T>`) in preference to postfix syntax (`T Foo`)</span></span>

<span data-ttu-id="6a884-161">F# 继承这两个后缀机器学习的样式命名泛型类型 (例如， `int list`) 以及.NET 样式的前缀 (例如， `list<int>`)。</span><span class="sxs-lookup"><span data-stu-id="6a884-161">F# inherits both the postfix ML style of naming generic types (for example, `int list`) as well as the prefix .NET style (for example, `list<int>`).</span></span> <span data-ttu-id="6a884-162">.NET 样式，除了四种特定类型为首选项：</span><span class="sxs-lookup"><span data-stu-id="6a884-162">Prefer the .NET style, except for four specific types:</span></span>

1. <span data-ttu-id="6a884-163">对于 F# 列表，请使用后缀形式：`int list`而非`list<int>`。</span><span class="sxs-lookup"><span data-stu-id="6a884-163">For F# Lists, use the postfix form: `int list` rather than `list<int>`.</span></span>
2. <span data-ttu-id="6a884-164">对于 F# 选项，请使用后缀形式：`int option`而非`option<int>`。</span><span class="sxs-lookup"><span data-stu-id="6a884-164">For F# Options, use the postfix form: `int option` rather than `option<int>`.</span></span>
3. <span data-ttu-id="6a884-165">对于 F# 数组，使用语法名称`int[]`而非`int array`或`array<int>`。</span><span class="sxs-lookup"><span data-stu-id="6a884-165">For F# arrays, use the syntactic name `int[]` rather than `int array` or `array<int>`.</span></span>
4. <span data-ttu-id="6a884-166">对于引用单元格，请使用`int ref`而非`ref<int>`或`Ref<int>`。</span><span class="sxs-lookup"><span data-stu-id="6a884-166">For Reference Cells, use `int ref` rather than `ref<int>` or `Ref<int>`.</span></span>

<span data-ttu-id="6a884-167">对于所有其他类型，请使用前缀形式。</span><span class="sxs-lookup"><span data-stu-id="6a884-167">For all other types, use the prefix form.</span></span>

## <a name="formatting-tuples"></a><span data-ttu-id="6a884-168">格式设置的元组</span><span class="sxs-lookup"><span data-stu-id="6a884-168">Formatting tuples</span></span>

<span data-ttu-id="6a884-169">元组实例化应该是用圆括号括起来，和中分隔的逗号应后跟一个空格，例如： `(1, 2)`， `(x, y, z)`。</span><span class="sxs-lookup"><span data-stu-id="6a884-169">A tuple instantiation should be parenthesized, and the delimiting commas within should be followed by a single space, for example: `(1, 2)`, `(x, y, z)`.</span></span>

<span data-ttu-id="6a884-170">它通常被接受以忽略在模式匹配的元组中的括号：</span><span class="sxs-lookup"><span data-stu-id="6a884-170">It is commonly accepted to omit parentheses in pattern matching of tuples:</span></span>

```fsharp
let (x, y) = z // Destructuring
let x, y = z // OK

// OK
match x, y with
| 1, _ -> 0
| x, 1 -> 0
| x, y -> 1
```

## <a name="formatting-discriminated-union-declarations"></a><span data-ttu-id="6a884-171">格式设置可区分联合声明</span><span class="sxs-lookup"><span data-stu-id="6a884-171">Formatting discriminated union declarations</span></span>

<span data-ttu-id="6a884-172">缩进`|`由 4 个空格的类型定义中：</span><span class="sxs-lookup"><span data-stu-id="6a884-172">Indent `|` in type definition by 4 spaces:</span></span>

```fsharp
// OK
type Volume =
    | Liter of float
    | FluidOunce of float
    | ImperialPint of float

// Not OK
type Volume =
| Liter of float
| USPint of float
| ImperialPint of float
```

## <a name="formatting-discriminated-unions"></a><span data-ttu-id="6a884-173">格式设置可区分联合</span><span class="sxs-lookup"><span data-stu-id="6a884-173">Formatting discriminated unions</span></span>

<span data-ttu-id="6a884-174">将拆分到多个行的实例化的可区分联合应为包含的数据提供具有缩进的新作用域：</span><span class="sxs-lookup"><span data-stu-id="6a884-174">Instantiated Discriminated Unions that split across multiple lines should give contained data a new scope with indentation:</span></span>

```fsharp
let tree1 =
    BinaryNode
        (BinaryNode(BinaryValue 1, BinaryValue 2),
         BinaryNode(BinaryValue 3, BinaryValue 4))
```

<span data-ttu-id="6a884-175">右括号还可以在新的一行：</span><span class="sxs-lookup"><span data-stu-id="6a884-175">The closing parenthesis can also be on a new line:</span></span>

```fsharp
let tree1 =
    BinaryNode(
        BinaryNode(BinaryValue 1, BinaryValue 2),
        BinaryNode(BinaryValue 3, BinaryValue 4)
    )
```

## <a name="formatting-record-declarations"></a><span data-ttu-id="6a884-176">格式设置的记录声明</span><span class="sxs-lookup"><span data-stu-id="6a884-176">Formatting record declarations</span></span>

<span data-ttu-id="6a884-177">缩进`{`类型中定义由 4 空格和同一行上开始的字段列表：</span><span class="sxs-lookup"><span data-stu-id="6a884-177">Indent `{` in type definition by 4 spaces and start the field list on the same line:</span></span>

```fsharp
// OK
type PostalAddress =
    { Address: string
      City: string
      Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City

// Not OK
type PostalAddress =
  { Address: string
    City: string
    Zip: string }
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
    
// Unusual in F#
type PostalAddress =
    { 
        Address: string
        City: string
        Zip: string
    }
```

<span data-ttu-id="6a884-178">将打开标记放置在同一行并在新行的结束标记也是没问题，但请注意，需要使用[详细语法](../language-reference/verbose-syntax.md)来定义成员 (`with`关键字):</span><span class="sxs-lookup"><span data-stu-id="6a884-178">Placing the opening token on the same line and the closing token on a new line is also fine, but be aware that you need to use the [verbose syntax](../language-reference/verbose-syntax.md) to define members (the `with` keyword):</span></span>

```fsharp
//  OK, but verbose syntax required
type PostalAddress = { 
    Address: string
    City: string
    Zip: string
} with
    member x.ZipAndCity = sprintf "%s %s" x.Zip x.City
```

## <a name="formatting-records"></a><span data-ttu-id="6a884-179">格式设置的记录</span><span class="sxs-lookup"><span data-stu-id="6a884-179">Formatting records</span></span>

<span data-ttu-id="6a884-180">可以在一行中编写短记录：</span><span class="sxs-lookup"><span data-stu-id="6a884-180">Short records can be written in one line:</span></span>

```fsharp
let point = { X = 1.0; Y = 0.0 }
```

<span data-ttu-id="6a884-181">较长的记录标签应使用新行：</span><span class="sxs-lookup"><span data-stu-id="6a884-181">Records that are longer should use new lines for labels:</span></span>

```fsharp
let rainbow =
    { Boss = "Jeffrey"
      Lackeys = ["Zippy"; "George"; "Bungle"] }
```

<span data-ttu-id="6a884-182">将打开标记放置在同一行并在新行的结束标记，还没问题：</span><span class="sxs-lookup"><span data-stu-id="6a884-182">Placing the opening token on the same line and the closing token on a new line is also fine:</span></span>

```fsharp
let rainbow = {
    Boss1 = "Jeffrey"
    Boss2 = "Jeffrey"
    Boss3 = "Jeffrey"
    Boss4 = "Jeffrey"
    Boss5 = "Jeffrey"
    Boss6 = "Jeffrey"
    Boss7 = "Jeffrey"
    Boss8 = "Jeffrey"
    Lackeys = ["Zippy"; "George"; "Bungle"]
}
```

<span data-ttu-id="6a884-183">相同的规则适用于列表和数组元素。</span><span class="sxs-lookup"><span data-stu-id="6a884-183">The same rules apply for list and array elements.</span></span>

## <a name="formatting-lists-and-arrays"></a><span data-ttu-id="6a884-184">格式设置的列表和数组</span><span class="sxs-lookup"><span data-stu-id="6a884-184">Formatting lists and arrays</span></span>

<span data-ttu-id="6a884-185">编写`x :: l`与周围的空格`::`运算符 (`::`为中缀运算符，因此由空格括起来) 和`[1; 2; 3]`(`;`是分隔符，因此跟一个空格)。</span><span class="sxs-lookup"><span data-stu-id="6a884-185">Write `x :: l` with spaces around the `::` operator (`::` is an infix operator, hence surrounded by spaces) and `[1; 2; 3]` (`;` is a delimiter, hence followed by a space).</span></span>

<span data-ttu-id="6a884-186">始终使用两个不同的大括号类似于运算符之间至少一个空格。</span><span class="sxs-lookup"><span data-stu-id="6a884-186">Always use at least one space between two distinct brace-like operators.</span></span> <span data-ttu-id="6a884-187">例如，将保留之间有空格`[`和一个`{`。</span><span class="sxs-lookup"><span data-stu-id="6a884-187">For example, leave a space between a `[` and a `{`.</span></span>

```fsharp
// OK
[ { IngredientName = "Green beans"; Quantity = 250 }
  { IngredientName = "Pine nuts"; Quantity = 250 }
  { IngredientName = "Feta cheese"; Quantity = 250 }
  { IngredientName = "Olive oil"; Quantity = 10 }
  { IngredientName = "Lemon"; Quantity = 1 } ]

// Not OK
[{ IngredientName = "Green beans"; Quantity = 250 }
 { IngredientName = "Pine nuts"; Quantity = 250 }
 { IngredientName = "Feta cheese"; Quantity = 250 }
 { IngredientName = "Olive oil"; Quantity = 10 }
 { IngredientName = "Lemon"; Quantity = 1 }]
```

<span data-ttu-id="6a884-188">列表和拆分到多个行的数组记录一样遵循类似的规则：</span><span class="sxs-lookup"><span data-stu-id="6a884-188">Lists and arrays that split across multiple lines follow a similar rule as records do:</span></span>

```fsharp
let pascalsTriangle = [|
    [|1|]
    [|1; 1|]
    [|1; 2; 1|]
    [|1; 3; 3; 1|]
    [|1; 4; 6; 4; 1|]
    [|1; 5; 10; 10; 5; 1|]
    [|1; 6; 15; 20; 15; 6; 1|]
    [|1; 7; 21; 35; 35; 21; 7; 1|]
    [|1; 8; 28; 56; 70; 56; 28; 8; 1|]
|]
```

## <a name="formatting-if-expressions"></a><span data-ttu-id="6a884-189">如果格式设置表达式</span><span class="sxs-lookup"><span data-stu-id="6a884-189">Formatting if expressions</span></span>

<span data-ttu-id="6a884-190">条件语句的缩进取决于把它们组合起来的表达式的大小。</span><span class="sxs-lookup"><span data-stu-id="6a884-190">Indentation of conditionals depends on the sizes of the expressions that make them up.</span></span> <span data-ttu-id="6a884-191">如果`cond`，`e1`和`e2`简短，只需将它们写在同一行中：</span><span class="sxs-lookup"><span data-stu-id="6a884-191">If `cond`, `e1` and `e2` are short, simply write them on one line:</span></span>

```fsharp
if cond then e1 else e2
```

<span data-ttu-id="6a884-192">如果任一`cond`，`e1`或`e2`更长时间，但不多的行：</span><span class="sxs-lookup"><span data-stu-id="6a884-192">If either `cond`, `e1` or `e2` are longer, but not multi-line:</span></span>

```fsharp
if cond
then e1
else e2
```

<span data-ttu-id="6a884-193">如果是多行的任何表达式：</span><span class="sxs-lookup"><span data-stu-id="6a884-193">If any of the expressions are multi-line:</span></span>

```fsharp
if cond then
    e1
else
    e2
```

<span data-ttu-id="6a884-194">使用多个条件语句`elif`并`else`都在同一作用域为缩进`if`:</span><span class="sxs-lookup"><span data-stu-id="6a884-194">Multiple conditionals with `elif` and `else` are indented at the same scope as the `if`:</span></span>

```fsharp
if cond1 then e1
elif cond2 then e2
elif cond3 then e3
else e4
```

### <a name="pattern-matching-constructs"></a><span data-ttu-id="6a884-195">模式匹配构造</span><span class="sxs-lookup"><span data-stu-id="6a884-195">Pattern matching constructs</span></span>

<span data-ttu-id="6a884-196">使用`|`无缩进匹配项的每个子句。</span><span class="sxs-lookup"><span data-stu-id="6a884-196">Use a `|` for each clause of a match with no indentation.</span></span> <span data-ttu-id="6a884-197">如果表达式很短，则可以考虑使用单独的一行，如果每一子表达式也非常简单。</span><span class="sxs-lookup"><span data-stu-id="6a884-197">If the expression is short, you can consider using a single line if each subexpression is also simple.</span></span>

```fsharp
// OK
match l with
| { him = x; her = "Posh" } :: tail -> _
| _ :: tail -> findDavid tail
| [] -> failwith "Couldn't find David"

// Not OK
match l with
    | { him = x; her = "Posh" } :: tail -> _
    | _ :: tail -> findDavid tail
    | [] -> failwith "Couldn't find David"
```

<span data-ttu-id="6a884-198">如果在模式匹配箭头右侧的表达式太大，则将其移动到以下行，缩进一个步骤，从`match` / `|`。</span><span class="sxs-lookup"><span data-stu-id="6a884-198">If the expression on the right of the pattern matching arrow is too large, move it to the following line, indented one step from the `match`/`|`.</span></span>

```fsharp
match lam with
| Var v -> 1
| Abs(x, body) ->
    1 + sizeLambda body
| App(lam1, lam2) ->
    sizeLambda lam1 + sizeLambda lam2

```

<span data-ttu-id="6a884-199">模式匹配的匿名函数，通过启动`function`，应通常不缩进太远。</span><span class="sxs-lookup"><span data-stu-id="6a884-199">Pattern matching of anonymous functions, starting by `function`, should generally not indent too far.</span></span> <span data-ttu-id="6a884-200">例如，按如下所示缩进一个作用域是没问题：</span><span class="sxs-lookup"><span data-stu-id="6a884-200">For example, indenting one scope as follows is fine:</span></span>

```fsharp
lambdaList
|> List.map (function
    | Abs(x, body) -> 1 + sizeLambda 0 body
    | App(lam1, lam2) -> sizeLambda (sizeLambda 0 lam1) lam2
    | Var v -> 1)
```

<span data-ttu-id="6a884-201">通过定义的函数中的模式匹配`let`或`let rec`应在启动后的缩进的 4 个空格`let`，即使`function`使用关键字：</span><span class="sxs-lookup"><span data-stu-id="6a884-201">Pattern matching in functions defined by `let` or `let rec` should be indented 4 spaces after starting of `let`, even if `function` keyword is used:</span></span>

```fsharp
let rec sizeLambda acc = function
    | Abs(x, body) -> sizeLambda (succ acc) body
    | App(lam1, lam2) -> sizeLambda (sizeLambda acc lam1) lam2
    | Var v -> succ acc
```

<span data-ttu-id="6a884-202">我们不建议对齐箭头。</span><span class="sxs-lookup"><span data-stu-id="6a884-202">We do not recommend aligning arrows.</span></span>

## <a name="formatting-trywith-expressions"></a><span data-ttu-id="6a884-203">格式设置 try / with 表达式</span><span class="sxs-lookup"><span data-stu-id="6a884-203">Formatting try/with expressions</span></span>

<span data-ttu-id="6a884-204">模式匹配异常类型应为相同的级别缩进`with`。</span><span class="sxs-lookup"><span data-stu-id="6a884-204">Pattern matching on the exception type should be indented at the same level as `with`.</span></span>

```fsharp
try
    if System.DateTime.Now.Second % 3 = 0 then
        raise (new System.Exception())
    else
        raise (new System.ApplicationException())
with
| :? System.ApplicationException ->
    printfn "A second that was not a multiple of 3"
| _ ->
    printfn "A second that was a multiple of 3"
```

## <a name="formatting-function-parameter-application"></a><span data-ttu-id="6a884-205">格式设置函数参数应用程序</span><span class="sxs-lookup"><span data-stu-id="6a884-205">Formatting function parameter application</span></span>

<span data-ttu-id="6a884-206">一般情况下，大多数函数参数应用程序可在同一行。</span><span class="sxs-lookup"><span data-stu-id="6a884-206">In general, most function parameter application is done on the same line.</span></span>

<span data-ttu-id="6a884-207">如果你想要应用到新行上的函数的参数，将它们缩进按一个作用域。</span><span class="sxs-lookup"><span data-stu-id="6a884-207">If you wish to apply parameters to a function on a new line, indent them by one scope.</span></span>

```fsharp
// OK
sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
sprintf
     "\t%s - %i\n\r"
     x.IngredientName x.Quantity

// OK
let printVolumes x =
    printf "Volume in liters = %f, in us pints = %f, in imperial = %f"
        (convertVolumeToLiter x)
        (convertVolumeUSPint x)
        (convertVolumeImperialPint x)
```

<span data-ttu-id="6a884-208">适用的 lambda 表达式作为函数参数相同的准则。</span><span class="sxs-lookup"><span data-stu-id="6a884-208">The same guidelines apply for lambda expressions as function arguments.</span></span> <span data-ttu-id="6a884-209">如果 lambda 表达式，主体的主体可以拥有另一个行，缩进一个作用域</span><span class="sxs-lookup"><span data-stu-id="6a884-209">If the body of a lambda expression, the body can have another line, indented by one scope</span></span>

```fsharp
let printListWithOffset a list1 =
    List.iter
        (fun elem -> printfn "%d" (a + elem))
        list1

// OK if lambda body is long enough
let printListWithOffset a list1 =
    List.iter
        (fun elem ->
            printfn "%d" (a + elem))
        list1
```

<span data-ttu-id="6a884-210">但是，如果 lambda 表达式的主体是多个行，请考虑一下分离到单独的函数而不是具有多行构造为单个参数应用于函数。</span><span class="sxs-lookup"><span data-stu-id="6a884-210">However, if the body of a lambda expression is more than one line, consider factoring it out into a separate function rather than have a multi-line construct applied as a single argument to a function.</span></span>

### <a name="formatting-infix-operators"></a><span data-ttu-id="6a884-211">格式设置中缀运算符</span><span class="sxs-lookup"><span data-stu-id="6a884-211">Formatting infix operators</span></span>

<span data-ttu-id="6a884-212">由空格的单独运算符。</span><span class="sxs-lookup"><span data-stu-id="6a884-212">Separate operators by spaces.</span></span> <span data-ttu-id="6a884-213">是此规则的例外明显`!`和`.`运算符。</span><span class="sxs-lookup"><span data-stu-id="6a884-213">Obvious exceptions to this rule are the `!` and `.` operators.</span></span>

<span data-ttu-id="6a884-214">中缀表达式是同一列上的配置列表确定:</span><span class="sxs-lookup"><span data-stu-id="6a884-214">Infix expressions are OK to lineup on same column:</span></span>

```fsharp
acc +
(sprintf "\t%s - %i\n\r"
     x.IngredientName x.Quantity)

let function1 arg1 arg2 arg3 arg4 =
    arg1 + arg2 +
    arg3 + arg4
```

### <a name="formatting-pipeline-operators"></a><span data-ttu-id="6a884-215">格式设置管道运算符</span><span class="sxs-lookup"><span data-stu-id="6a884-215">Formatting pipeline operators</span></span>

<span data-ttu-id="6a884-216">管道`|>`运算符应发送到下对它们进行操作的表达式。</span><span class="sxs-lookup"><span data-stu-id="6a884-216">Pipeline `|>` operators should go underneath the expressions they operate on.</span></span>

```fsharp
// Preferred approach
let methods2 =
    System.AppDomain.CurrentDomain.GetAssemblies()
    |> List.ofArray
    |> List.map (fun assm -> assm.GetTypes())
    |> Array.concat
    |> List.ofArray
    |> List.map (fun t -> t.GetMethods())
    |> Array.concat

// Not OK
let methods2 = System.AppDomain.CurrentDomain.GetAssemblies()
            |> List.ofArray
            |> List.map (fun assm -> assm.GetTypes())
            |> Array.concat
            |> List.ofArray
            |> List.map (fun t -> t.GetMethods())
            |> Array.concat
```

### <a name="formatting-modules"></a><span data-ttu-id="6a884-217">格式设置模块</span><span class="sxs-lookup"><span data-stu-id="6a884-217">Formatting modules</span></span>

<span data-ttu-id="6a884-218">本地模块中的代码必须将缩进，相对于该模块，但顶级模块中的代码不应缩进。</span><span class="sxs-lookup"><span data-stu-id="6a884-218">Code in a local module must be indented relative to the module, but code in a top-level module should not be indented.</span></span> <span data-ttu-id="6a884-219">Namespace 元素无需将缩进。</span><span class="sxs-lookup"><span data-stu-id="6a884-219">Namespace elements do not have to be indented.</span></span>

```fsharp
// A is a top-level module.
module A

let function1 a b = a - b * b
```

```fsharp
// A1 and A2 are local modules.
module A1 =
    let function1 a b = a*a + b*b

module A2 =
    let function2 a b = a*a - b*b
```

### <a name="formatting-object-expressions-and-interfaces"></a><span data-ttu-id="6a884-220">格式设置对象表达式和接口</span><span class="sxs-lookup"><span data-stu-id="6a884-220">Formatting object expressions and interfaces</span></span>

<span data-ttu-id="6a884-221">应使用相同的方式对齐对象表达式和接口`member`要缩进后 4 个空格。</span><span class="sxs-lookup"><span data-stu-id="6a884-221">Object expressions and interfaces should be aligned in the same way with `member` being indented after 4 spaces.</span></span>

```fsharp
let comparer =
    { new IComparer<string> with
          member x.Compare(s1, s2) =
              let rev (s : String) =
                  new String (Array.rev (s.ToCharArray()))
              let reversed = rev s1
              reversed.CompareTo (rev s2) }
```

### <a name="formatting-white-space-in-expressions"></a><span data-ttu-id="6a884-222">格式表达式中的空白区域</span><span class="sxs-lookup"><span data-stu-id="6a884-222">Formatting white space in expressions</span></span>

<span data-ttu-id="6a884-223">避免在 F# 表达式中的多余空白。</span><span class="sxs-lookup"><span data-stu-id="6a884-223">Avoid extraneous white space in F# expressions.</span></span>

```fsharp
// OK
spam (ham.[1])

// Not OK
spam ( ham.[ 1 ] )
```

<span data-ttu-id="6a884-224">命名的参数也不应具有空间周围`=`:</span><span class="sxs-lookup"><span data-stu-id="6a884-224">Named arguments should also not have space surrounding the `=`:</span></span>

```fsharp
// OK
let makeStreamReader x = new System.IO.StreamReader(path=x)

// Not OK
let makeStreamReader x = new System.IO.StreamReader(path = x)
```
