---
title: 约束
description: 了解适用F#于泛型类型参数的约束，以指定泛型类型或函数中类型参数的要求。
ms.date: 05/16/2016
ms.openlocfilehash: 70a8bec1ad67d7e814cb7a96b1876bb22399c5e7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425017"
---
# <a name="constraints"></a><span data-ttu-id="d016c-103">约束</span><span class="sxs-lookup"><span data-stu-id="d016c-103">Constraints</span></span>

<span data-ttu-id="d016c-104">本主题介绍可应用于泛型类型参数以指定泛型类型或函数中类型参数的要求的约束。</span><span class="sxs-lookup"><span data-stu-id="d016c-104">This topic describes constraints that you can apply to generic type parameters to specify the requirements for a type argument in a generic type or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="d016c-105">语法</span><span class="sxs-lookup"><span data-stu-id="d016c-105">Syntax</span></span>

```fsharp
type-parameter-list when constraint1 [ and constraint2]
```

## <a name="remarks"></a><span data-ttu-id="d016c-106">备注</span><span class="sxs-lookup"><span data-stu-id="d016c-106">Remarks</span></span>

<span data-ttu-id="d016c-107">可以应用多个不同的约束，以限制可在泛型类型中使用的类型。</span><span class="sxs-lookup"><span data-stu-id="d016c-107">There are several different constraints you can apply to limit the types that can be used in a generic type.</span></span> <span data-ttu-id="d016c-108">下表列出并描述了这些约束。</span><span class="sxs-lookup"><span data-stu-id="d016c-108">The following table lists and describes these constraints.</span></span>

|<span data-ttu-id="d016c-109">约束</span><span class="sxs-lookup"><span data-stu-id="d016c-109">Constraint</span></span>|<span data-ttu-id="d016c-110">语法</span><span class="sxs-lookup"><span data-stu-id="d016c-110">Syntax</span></span>|<span data-ttu-id="d016c-111">描述</span><span class="sxs-lookup"><span data-stu-id="d016c-111">Description</span></span>|
|----------|------|-----------|
|<span data-ttu-id="d016c-112">类型约束</span><span class="sxs-lookup"><span data-stu-id="d016c-112">Type Constraint</span></span>|<span data-ttu-id="d016c-113">*类型参数*：&gt;*类型*</span><span class="sxs-lookup"><span data-stu-id="d016c-113">*type-parameter* :&gt; *type*</span></span>|<span data-ttu-id="d016c-114">提供的类型必须等于或派生自指定的类型，或者，如果类型是接口，则提供的类型必须实现接口。</span><span class="sxs-lookup"><span data-stu-id="d016c-114">The provided type must be equal to or derived from the type specified, or, if the type is an interface, the provided type must implement the interface.</span></span>|
|<span data-ttu-id="d016c-115">Null 约束</span><span class="sxs-lookup"><span data-stu-id="d016c-115">Null Constraint</span></span>|<span data-ttu-id="d016c-116">*类型-参数*： null</span><span class="sxs-lookup"><span data-stu-id="d016c-116">*type-parameter* : null</span></span>|<span data-ttu-id="d016c-117">提供的类型必须支持 null 文本。</span><span class="sxs-lookup"><span data-stu-id="d016c-117">The provided type must support the null literal.</span></span> <span data-ttu-id="d016c-118">这包括所有 .NET 对象类型，但F#不包括列表、元组、函数、类、记录或联合类型。</span><span class="sxs-lookup"><span data-stu-id="d016c-118">This includes all .NET object types but not F# list, tuple, function, class, record, or union types.</span></span>|
|<span data-ttu-id="d016c-119">显式成员约束</span><span class="sxs-lookup"><span data-stu-id="d016c-119">Explicit Member Constraint</span></span>|<span data-ttu-id="d016c-120">[（]*类型-参数*[或 .。。或*类型参数*）]：（*成员签名*）</span><span class="sxs-lookup"><span data-stu-id="d016c-120">[(]*type-parameter* [or ... or *type-parameter*)] : (*member-signature*)</span></span>|<span data-ttu-id="d016c-121">提供的类型自变量中至少有一个必须具有具有指定签名的成员;不用于常见用途。</span><span class="sxs-lookup"><span data-stu-id="d016c-121">At least one of the type arguments provided must have a member that has the specified signature; not intended for common use.</span></span> <span data-ttu-id="d016c-122">成员必须在类型或隐式类型扩展的一部分上显式定义为显式成员约束的有效目标。</span><span class="sxs-lookup"><span data-stu-id="d016c-122">Members must be either explicitly defined on the type or part of an implicit type extension to be valid targets for an Explicit Member Constraint.</span></span>|
|<span data-ttu-id="d016c-123">构造函数约束</span><span class="sxs-lookup"><span data-stu-id="d016c-123">Constructor Constraint</span></span>|<span data-ttu-id="d016c-124">*类型-参数*：（新的：单元&gt; "a"）</span><span class="sxs-lookup"><span data-stu-id="d016c-124">*type-parameter* : ( new : unit -&gt; 'a )</span></span>|<span data-ttu-id="d016c-125">提供的类型必须具有无参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="d016c-125">The provided type must have a parameterless constructor.</span></span>|
|<span data-ttu-id="d016c-126">值类型约束</span><span class="sxs-lookup"><span data-stu-id="d016c-126">Value Type Constraint</span></span>|<span data-ttu-id="d016c-127">： struct</span><span class="sxs-lookup"><span data-stu-id="d016c-127">: struct</span></span>|<span data-ttu-id="d016c-128">提供的类型必须是 .NET 值类型。</span><span class="sxs-lookup"><span data-stu-id="d016c-128">The provided type must be a .NET value type.</span></span>|
|<span data-ttu-id="d016c-129">引用类型约束</span><span class="sxs-lookup"><span data-stu-id="d016c-129">Reference Type Constraint</span></span>|<span data-ttu-id="d016c-130">： not struct</span><span class="sxs-lookup"><span data-stu-id="d016c-130">: not struct</span></span>|<span data-ttu-id="d016c-131">提供的类型必须是 .NET 引用类型。</span><span class="sxs-lookup"><span data-stu-id="d016c-131">The provided type must be a .NET reference type.</span></span>|
|<span data-ttu-id="d016c-132">枚举类型约束</span><span class="sxs-lookup"><span data-stu-id="d016c-132">Enumeration Type Constraint</span></span>|<span data-ttu-id="d016c-133">：枚举&lt;*基础类型*&gt;</span><span class="sxs-lookup"><span data-stu-id="d016c-133">: enum&lt;*underlying-type*&gt;</span></span>|<span data-ttu-id="d016c-134">提供的类型必须是具有指定基础类型的枚举类型;不用于常见用途。</span><span class="sxs-lookup"><span data-stu-id="d016c-134">The provided type must be an enumerated type that has the specified underlying type; not intended for common use.</span></span>|
|<span data-ttu-id="d016c-135">委托约束</span><span class="sxs-lookup"><span data-stu-id="d016c-135">Delegate Constraint</span></span>|<span data-ttu-id="d016c-136">：委托&lt;*元组-参数类型*、*返回类型*&gt;</span><span class="sxs-lookup"><span data-stu-id="d016c-136">: delegate&lt;*tuple-parameter-type*, *return-type*&gt;</span></span>|<span data-ttu-id="d016c-137">提供的类型必须是具有指定参数和返回值的委托类型;不用于常见用途。</span><span class="sxs-lookup"><span data-stu-id="d016c-137">The provided type must be a delegate type that has the specified arguments and return value; not intended for common use.</span></span>|
|<span data-ttu-id="d016c-138">比较约束</span><span class="sxs-lookup"><span data-stu-id="d016c-138">Comparison Constraint</span></span>|<span data-ttu-id="d016c-139">：比较</span><span class="sxs-lookup"><span data-stu-id="d016c-139">: comparison</span></span>|<span data-ttu-id="d016c-140">提供的类型必须支持比较。</span><span class="sxs-lookup"><span data-stu-id="d016c-140">The provided type must support comparison.</span></span>|
|<span data-ttu-id="d016c-141">相等约束</span><span class="sxs-lookup"><span data-stu-id="d016c-141">Equality Constraint</span></span>|<span data-ttu-id="d016c-142">：相等</span><span class="sxs-lookup"><span data-stu-id="d016c-142">: equality</span></span>|<span data-ttu-id="d016c-143">提供的类型必须支持相等性。</span><span class="sxs-lookup"><span data-stu-id="d016c-143">The provided type must support equality.</span></span>|
|<span data-ttu-id="d016c-144">非托管约束</span><span class="sxs-lookup"><span data-stu-id="d016c-144">Unmanaged Constraint</span></span>|<span data-ttu-id="d016c-145">：非托管</span><span class="sxs-lookup"><span data-stu-id="d016c-145">: unmanaged</span></span>|<span data-ttu-id="d016c-146">提供的类型必须是非托管类型。</span><span class="sxs-lookup"><span data-stu-id="d016c-146">The provided type must be an unmanaged type.</span></span> <span data-ttu-id="d016c-147">非托管类型是特定的基元类型（`sbyte`、`byte`、`char`、`nativeint`、`unativeint`、`float32`、`float`、`int16`、`uint16`、`int32`、`uint32`、`int64`、`uint64`或 `decimal`）、枚举类型、`nativeptr<_>`或非泛型结构，其字段为所有非托管类型。</span><span class="sxs-lookup"><span data-stu-id="d016c-147">Unmanaged types are either certain primitive types (`sbyte`, `byte`, `char`, `nativeint`, `unativeint`, `float32`, `float`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint64`, or `decimal`), enumeration types, `nativeptr<_>`, or a non-generic structure whose fields are all unmanaged types.</span></span>|

<span data-ttu-id="d016c-148">当你的代码必须使用在约束类型上可用的功能，而不是常规类型时，你必须添加约束。</span><span class="sxs-lookup"><span data-stu-id="d016c-148">You have to add a constraint when your code has to use a feature that is available on the constraint type but not on types in general.</span></span> <span data-ttu-id="d016c-149">例如，如果使用类型约束指定类类型，则可以在泛型函数或类型中使用该类的任意一个方法。</span><span class="sxs-lookup"><span data-stu-id="d016c-149">For example, if you use the type constraint to specify a class type, you can use any one of the methods of that class in the generic function or type.</span></span>

<span data-ttu-id="d016c-150">在显式编写类型参数时，有时需要指定约束，因为如果没有约束，编译器将无法验证你所使用的功能是否可用于在运行时为类型提供的任何类型参数.</span><span class="sxs-lookup"><span data-stu-id="d016c-150">Specifying constraints is sometimes required when writing type parameters explicitly, because without a constraint, the compiler has no way of verifying that the features that you are using will be available on any type that might be supplied at run time for the type parameter.</span></span>

<span data-ttu-id="d016c-151">在代码中F#使用的最常见约束是指定基类或接口的类型约束。</span><span class="sxs-lookup"><span data-stu-id="d016c-151">The most common constraints you use in F# code are type constraints that specify base classes or interfaces.</span></span> <span data-ttu-id="d016c-152">F#库使用其他约束来实现某些功能，如显式成员约束（用于实现算术运算符的运算符重载），主要是因为F#支持公共语言运行时支持的一组完整的约束。</span><span class="sxs-lookup"><span data-stu-id="d016c-152">The other constraints are either used by the F# library to implement certain functionality, such as the explicit member constraint, which is used to implement operator overloading for arithmetic operators, or are provided mainly because F# supports the complete set of constraints that is supported by the common language runtime.</span></span>

<span data-ttu-id="d016c-153">在类型推理过程中，编译器会自动推断某些约束。</span><span class="sxs-lookup"><span data-stu-id="d016c-153">During the type inference process, some constraints are inferred automatically by the compiler.</span></span> <span data-ttu-id="d016c-154">例如，如果在函数中使用 `+` 运算符，则编译器将对表达式中使用的变量类型推断显式成员约束。</span><span class="sxs-lookup"><span data-stu-id="d016c-154">For example, if you use the `+` operator in a function, the compiler infers an explicit member constraint on variable types that are used in the expression.</span></span>

<span data-ttu-id="d016c-155">下面的代码演示了一些约束声明：</span><span class="sxs-lookup"><span data-stu-id="d016c-155">The following code illustrates some constraint declarations:</span></span>

```fsharp
// Base Type Constraint
type Class1<'T when 'T :> System.Exception> =
class end

// Interface Type Constraint
type Class2<'T when 'T :> System.IComparable> =
class end

// Null constraint
type Class3<'T when 'T : null> =
class end

// Member constraint with instance member
type Class5<'T when 'T : (member Method1 : 'T -> int)> =
class end

// Member constraint with property
type Class6<'T when 'T : (member Property1 : int)> =
class end

// Constructor constraint
type Class7<'T when 'T : (new : unit -> 'T)>() =
member val Field = new 'T()

// Reference type constraint
type Class8<'T when 'T : not struct> =
class end

// Enumeration constraint with underlying value specified
type Class9<'T when 'T : enum<uint32>> =
class end

// 'T must implement IComparable, or be an array type with comparable
// elements, or be System.IntPtr or System.UIntPtr. Also, 'T must not have
// the NoComparison attribute.
type Class10<'T when 'T : comparison> =
class end

// 'T must support equality. This is true for any type that does not
// have the NoEquality attribute.
type Class11<'T when 'T : equality> =
class end

type Class12<'T when 'T : delegate<obj * System.EventArgs, unit>> =
class end

type Class13<'T when 'T : unmanaged> =
class end

// Member constraints with two type parameters
// Most often used with static type parameters in inline functions
let inline add(value1 : ^T when ^T : (static member (+) : ^T * ^T -> ^T), value2: ^T) =
value1 + value2

// ^T and ^U must support operator +
let inline heterogenousAdd(value1 : ^T when (^T or ^U) : (static member (+) : ^T * ^U -> ^T), value2 : ^U) =
value1 + value2

// If there are multiple constraints, use the and keyword to separate them.
type Class14<'T,'U when 'T : equality and 'U : equality> =
class end
```

## <a name="see-also"></a><span data-ttu-id="d016c-156">请参阅</span><span class="sxs-lookup"><span data-stu-id="d016c-156">See also</span></span>

- [<span data-ttu-id="d016c-157">泛型</span><span class="sxs-lookup"><span data-stu-id="d016c-157">Generics</span></span>](index.md)
- [<span data-ttu-id="d016c-158">约束</span><span class="sxs-lookup"><span data-stu-id="d016c-158">Constraints</span></span>](constraints.md)
