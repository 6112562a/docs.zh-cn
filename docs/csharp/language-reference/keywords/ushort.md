---
title: ushort 关键字 - C# 参考
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: 934e25576a8a24c176a54ec6af984459b513fe5a
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614450"
---
# <a name="ushort-c-reference"></a><span data-ttu-id="59d19-102">ushort（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="59d19-102">ushort (C# Reference)</span></span>

<span data-ttu-id="59d19-103">`ushort` 关键字表示一种整型数据类型，该类型根据下表显示的大小和范围存储值。</span><span class="sxs-lookup"><span data-stu-id="59d19-103">The `ushort` keyword indicates an integral data type that stores values according to the size and range shown in the following table.</span></span>

|<span data-ttu-id="59d19-104">类型</span><span class="sxs-lookup"><span data-stu-id="59d19-104">Type</span></span>|<span data-ttu-id="59d19-105">范围</span><span class="sxs-lookup"><span data-stu-id="59d19-105">Range</span></span>|<span data-ttu-id="59d19-106">大小</span><span class="sxs-lookup"><span data-stu-id="59d19-106">Size</span></span>|<span data-ttu-id="59d19-107">.NET 类型</span><span class="sxs-lookup"><span data-stu-id="59d19-107">.NET type</span></span>|
|----------|-----------|----------|-------------------------|
|`ushort`|<span data-ttu-id="59d19-108">0 到 65,535</span><span class="sxs-lookup"><span data-stu-id="59d19-108">0 to 65,535</span></span>|<span data-ttu-id="59d19-109">无符号 16 位整数</span><span class="sxs-lookup"><span data-stu-id="59d19-109">Unsigned 16-bit integer</span></span>|<xref:System.UInt16?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="59d19-110">文本</span><span class="sxs-lookup"><span data-stu-id="59d19-110">Literals</span></span>

<span data-ttu-id="59d19-111">可以通过为其分配十进制文本、十六进制文本或（从 C# 7.0 开始）二进制文本来声明和初始化 `ushort` 变量。</span><span class="sxs-lookup"><span data-stu-id="59d19-111">You can declare and initialize a `ushort` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7.0) a binary literal to it.</span></span> <span data-ttu-id="59d19-112">如果整数文本在 `ushort` 范围之外（即，如果它小于 <xref:System.UInt16.MinValue?displayProperty=nameWithType> 或大于 <xref:System.UInt16.MaxValue?displayProperty=nameWithType>），会发生编译错误。</span><span class="sxs-lookup"><span data-stu-id="59d19-112">If the integer literal is outside the range of `ushort` (that is, if it is less than <xref:System.UInt16.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), a compilation error occurs.</span></span>

<span data-ttu-id="59d19-113">在以下示例中，等于 65,034、表示为十进制、十六进制和二进制文本的整数从 [int](int.md) 隐式转换为 `ushort` 值。</span><span class="sxs-lookup"><span data-stu-id="59d19-113">In the following example, integers equal to 65,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](int.md) to `ushort` values.</span></span>

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]

> [!NOTE]
> <span data-ttu-id="59d19-114">使用前缀 `0x` 或 `0X` 表示十六进制文本，使用前缀 `0b` 或 `0B` 表示二进制文本。</span><span class="sxs-lookup"><span data-stu-id="59d19-114">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="59d19-115">十进制文本没有前缀。</span><span class="sxs-lookup"><span data-stu-id="59d19-115">Decimal literals have no prefix.</span></span>

<span data-ttu-id="59d19-116">从 C# 7.0 开始，添加了一些功能以增强可读性：</span><span class="sxs-lookup"><span data-stu-id="59d19-116">Starting with C# 7.0, a couple of features have been added to enhance readability:</span></span>

- <span data-ttu-id="59d19-117">C# 7.0 允许将下划线字符 (`_`) 用作数字分隔符。</span><span class="sxs-lookup"><span data-stu-id="59d19-117">C# 7.0 allows the usage of the underscore character, `_`, as a digit separator.</span></span>
- <span data-ttu-id="59d19-118">C# 7.2 允许将 `_` 用作二进制或十六进制文本的数字分隔符，位于前缀之后。</span><span class="sxs-lookup"><span data-stu-id="59d19-118">C# 7.2 allows `_` to be used as a digit separator for a binary or hexadecimal literal, after the prefix.</span></span> <span data-ttu-id="59d19-119">十进制文本不能够有前导下划线。</span><span class="sxs-lookup"><span data-stu-id="59d19-119">A decimal literal isn't permitted to have a leading underscore.</span></span>

<span data-ttu-id="59d19-120">下面是一些示例。</span><span class="sxs-lookup"><span data-stu-id="59d19-120">Some examples are shown below.</span></span>

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]

## <a name="compiler-overload-resolution"></a><span data-ttu-id="59d19-121">编译器重载解析</span><span class="sxs-lookup"><span data-stu-id="59d19-121">Compiler overload resolution</span></span>

<span data-ttu-id="59d19-122">调用重载方法时必须使用强制转换。</span><span class="sxs-lookup"><span data-stu-id="59d19-122">A cast must be used when you call overloaded methods.</span></span> <span data-ttu-id="59d19-123">以下面使用 `ushort` 和 [int](int.md) 参数的重载方法为例：</span><span class="sxs-lookup"><span data-stu-id="59d19-123">Consider, for example, the following overloaded methods that use `ushort` and [int](int.md) parameters:</span></span>

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ushort s) {}
```

<span data-ttu-id="59d19-124">使用 `ushort` 强制转换可保证调用正确的类型，例如：</span><span class="sxs-lookup"><span data-stu-id="59d19-124">Using the `ushort` cast guarantees that the correct type is called, for example:</span></span>

```csharp
// Calls the method with the int parameter:
SampleMethod(5);
// Calls the method with the ushort parameter:
SampleMethod((ushort)5);
```

## <a name="conversions"></a><span data-ttu-id="59d19-125">转换</span><span class="sxs-lookup"><span data-stu-id="59d19-125">Conversions</span></span>

<span data-ttu-id="59d19-126">存在从 `ushort` 到 [int](int.md)、[uint](uint.md)、[long](long.md)、[ulong](ulong.md)、[float](float.md)、[double](double.md) 或 [decimal](decimal.md) 的预定义隐式转换。</span><span class="sxs-lookup"><span data-stu-id="59d19-126">There is a predefined implicit conversion from `ushort` to [int](int.md), [uint](uint.md), [long](long.md), [ulong](ulong.md), [float](float.md), [double](double.md), or [decimal](decimal.md).</span></span>

<span data-ttu-id="59d19-127">存在从 [byte](byte.md) 或 [char](char.md) 到 `ushort` 的预定义隐式转换。</span><span class="sxs-lookup"><span data-stu-id="59d19-127">There is a predefined implicit conversion from [byte](byte.md) or [char](char.md) to `ushort`.</span></span> <span data-ttu-id="59d19-128">其他情况下必须使用强制转换来执行显式转换。</span><span class="sxs-lookup"><span data-stu-id="59d19-128">Otherwise a cast must be used to perform an explicit conversion.</span></span> <span data-ttu-id="59d19-129">以下面两个 `ushort` 变量 `x` 和 `y` 为例：</span><span class="sxs-lookup"><span data-stu-id="59d19-129">Consider, for example, the following two `ushort` variables `x` and `y`:</span></span>

```csharp
ushort x = 5, y = 12;
```

<span data-ttu-id="59d19-130">以下赋值语句会生成一个编译错误，原因是赋值运算符右侧的算术表达式在默认情况下的计算结果为 `int`。</span><span class="sxs-lookup"><span data-stu-id="59d19-130">The following assignment statement will produce a compilation error, because the arithmetic expression on the right side of the assignment operator evaluates to `int` by default.</span></span>

```csharp
ushort z = x + y;   // Error: conversion from int to ushort
```

<span data-ttu-id="59d19-131">若要解决此问题，请使用强制转换：</span><span class="sxs-lookup"><span data-stu-id="59d19-131">To fix this problem, use a cast:</span></span>

```csharp
ushort z = (ushort)(x + y);   // OK: explicit conversion
```

<span data-ttu-id="59d19-132">但是，在目标变量具有相同或更大的存储大小时，可以使用下列语句：</span><span class="sxs-lookup"><span data-stu-id="59d19-132">It is possible though to use the following statements, where the destination variable has the same storage size or a larger storage size:</span></span>

```csharp
int m = x + y;
long n = x + y;
```

<span data-ttu-id="59d19-133">另请注意，不存在从浮点类型到 `ushort` 类型的隐式转换。</span><span class="sxs-lookup"><span data-stu-id="59d19-133">Notice also that there is no implicit conversion from floating-point types to `ushort`.</span></span> <span data-ttu-id="59d19-134">例如，除非使用显式强制转换，否则以下语句将生成编译器错误：</span><span class="sxs-lookup"><span data-stu-id="59d19-134">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>

```csharp
// Error -- no implicit conversion from double:
ushort x = 3.0;
// OK -- explicit conversion:
ushort y = (ushort)3.0;
```

<span data-ttu-id="59d19-135">有关兼用浮点类型和整型类型的算术表达式的信息，请参阅 [float](float.md) 和 [double](double.md)。</span><span class="sxs-lookup"><span data-stu-id="59d19-135">For information about arithmetic expressions with mixed floating-point types and integral types, see [float](float.md) and [double](double.md).</span></span>

<span data-ttu-id="59d19-136">有关隐式数值转换规则的详细信息，请参阅[隐式数值转换表](implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="59d19-136">For more information about implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="59d19-137">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="59d19-137">C# language specification</span></span>

<span data-ttu-id="59d19-138">有关详细信息，请参阅 [C# 语言规范](../language-specification/index.md)中的[整型类型](~/_csharplang/spec/types.md#integral-types)。</span><span class="sxs-lookup"><span data-stu-id="59d19-138">For more information, see [Integral types](~/_csharplang/spec/types.md#integral-types) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="59d19-139">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="59d19-139">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="59d19-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="59d19-140">See also</span></span>

- <xref:System.UInt16>
- [<span data-ttu-id="59d19-141">C# 参考</span><span class="sxs-lookup"><span data-stu-id="59d19-141">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="59d19-142">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="59d19-142">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="59d19-143">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="59d19-143">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="59d19-144">整型表</span><span class="sxs-lookup"><span data-stu-id="59d19-144">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="59d19-145">内置类型表</span><span class="sxs-lookup"><span data-stu-id="59d19-145">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="59d19-146">隐式数值转换表</span><span class="sxs-lookup"><span data-stu-id="59d19-146">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="59d19-147">显式数值转换表</span><span class="sxs-lookup"><span data-stu-id="59d19-147">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
