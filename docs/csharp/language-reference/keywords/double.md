---
title: double 关键字 - C# 参考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- double
- double_CSharpKeyword
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
ms.openlocfilehash: 3c0fbe4f03edb829321971831c47f669d75f4d8c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240367"
---
# <a name="double-c-reference"></a><span data-ttu-id="b0cfe-102">double（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="b0cfe-102">double (C# Reference)</span></span>

<span data-ttu-id="b0cfe-103">`double` 关键字表示存储 64 位浮点值的简单类型。</span><span class="sxs-lookup"><span data-stu-id="b0cfe-103">The `double` keyword signifies a simple type that stores 64-bit floating-point values.</span></span> <span data-ttu-id="b0cfe-104">下表显示了 `double` 类型的精度和大致范围。</span><span class="sxs-lookup"><span data-stu-id="b0cfe-104">The following table shows the precision and approximate range for the `double` type.</span></span>

|<span data-ttu-id="b0cfe-105">类型</span><span class="sxs-lookup"><span data-stu-id="b0cfe-105">Type</span></span>|<span data-ttu-id="b0cfe-106">大致范围</span><span class="sxs-lookup"><span data-stu-id="b0cfe-106">Approximate range</span></span>|<span data-ttu-id="b0cfe-107">精度</span><span class="sxs-lookup"><span data-stu-id="b0cfe-107">Precision</span></span>|<span data-ttu-id="b0cfe-108">.NET 类型</span><span class="sxs-lookup"><span data-stu-id="b0cfe-108">.NET type</span></span>|
|----------|-----------------------|---------------|-------------------------|
|`double`|<span data-ttu-id="b0cfe-109">±5.0 × 10<sup>−324</sup> 到 ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="b0cfe-109">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="b0cfe-110">大约 15-17 位数字</span><span class="sxs-lookup"><span data-stu-id="b0cfe-110">~15-17 digits</span></span>|<xref:System.Double?displayProperty=nameWithType>|

## <a name="literals"></a><span data-ttu-id="b0cfe-111">文本</span><span class="sxs-lookup"><span data-stu-id="b0cfe-111">Literals</span></span>

<span data-ttu-id="b0cfe-112">默认情况下，赋值运算符右侧的实数被视为 `double`。</span><span class="sxs-lookup"><span data-stu-id="b0cfe-112">By default, a real numeric literal on the right side of the assignment operator is treated as `double`.</span></span> <span data-ttu-id="b0cfe-113">但是，如果希望整数被视为 `double`，可使用后缀 d 或 D，例如：</span><span class="sxs-lookup"><span data-stu-id="b0cfe-113">However, if you want an integer number to be treated as `double`, use the suffix d or D, for example:</span></span>

```csharp
double x = 3D;
```

## <a name="conversions"></a><span data-ttu-id="b0cfe-114">转换</span><span class="sxs-lookup"><span data-stu-id="b0cfe-114">Conversions</span></span>

<span data-ttu-id="b0cfe-115">可以在表达式中混合使用数值整型和浮点类型。</span><span class="sxs-lookup"><span data-stu-id="b0cfe-115">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="b0cfe-116">在这种情况下，整数类型将转换为浮点类型。</span><span class="sxs-lookup"><span data-stu-id="b0cfe-116">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="b0cfe-117">根据以下规则对表达式求值：</span><span class="sxs-lookup"><span data-stu-id="b0cfe-117">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="b0cfe-118">如果其中一个浮点类型是 `double`，该表达式在关系比较和相等比较中求值类型为 `double` 或 [bool](../../../csharp/language-reference/keywords/bool.md)。</span><span class="sxs-lookup"><span data-stu-id="b0cfe-118">If one of the floating-point types is `double`, the expression evaluates to `double`, or to [bool](../../../csharp/language-reference/keywords/bool.md) in relational comparisons and comparisons for equality.</span></span>

- <span data-ttu-id="b0cfe-119">如果表达式中没有 `double` 类型，则表达式在关系比较和相等比较中求值类型为[float](../../../csharp/language-reference/keywords/float.md) 或 [bool](../../../csharp/language-reference/keywords/bool.md)。</span><span class="sxs-lookup"><span data-stu-id="b0cfe-119">If there is no `double` type in the expression, it evaluates to [float](../../../csharp/language-reference/keywords/float.md), or to [bool](../../../csharp/language-reference/keywords/bool.md) in relational comparisons and comparisons for equality.</span></span>

 <span data-ttu-id="b0cfe-120">浮点表达式可以包含下列值集：</span><span class="sxs-lookup"><span data-stu-id="b0cfe-120">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="b0cfe-121">正零和负零。</span><span class="sxs-lookup"><span data-stu-id="b0cfe-121">Positive and negative zero.</span></span>

- <span data-ttu-id="b0cfe-122">正无穷大和负无穷大。</span><span class="sxs-lookup"><span data-stu-id="b0cfe-122">Positive and negative infinity.</span></span>

- <span data-ttu-id="b0cfe-123">非数字值 (NaN)。</span><span class="sxs-lookup"><span data-stu-id="b0cfe-123">Not-a-Number value (NaN).</span></span>

- <span data-ttu-id="b0cfe-124">一组有限的非零值。</span><span class="sxs-lookup"><span data-stu-id="b0cfe-124">The finite set of nonzero values.</span></span>

<span data-ttu-id="b0cfe-125">有关这些值的详细信息，请参阅 [IEEE](https://www.ieee.org) 网站中提供的二进制浮点算术的 IEEE 标准。</span><span class="sxs-lookup"><span data-stu-id="b0cfe-125">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) Web site.</span></span>

## <a name="example"></a><span data-ttu-id="b0cfe-126">示例</span><span class="sxs-lookup"><span data-stu-id="b0cfe-126">Example</span></span>

<span data-ttu-id="b0cfe-127">在下面的示例中，将 [int](../../../csharp/language-reference/keywords/int.md)、[short](../../../csharp/language-reference/keywords/short.md)、[float](../../../csharp/language-reference/keywords/float.md) 和 `double` 相加可得出 `double` 结果。</span><span class="sxs-lookup"><span data-stu-id="b0cfe-127">In the following example, an [int](../../../csharp/language-reference/keywords/int.md), a [short](../../../csharp/language-reference/keywords/short.md), a [float](../../../csharp/language-reference/keywords/float.md), and a `double` are added together giving a `double` result.</span></span>

[!code-csharp[csrefKeywordsTypes#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="b0cfe-128">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="b0cfe-128">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b0cfe-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="b0cfe-129">See Also</span></span>

- [<span data-ttu-id="b0cfe-130">C# 参考</span><span class="sxs-lookup"><span data-stu-id="b0cfe-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b0cfe-131">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="b0cfe-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b0cfe-132">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="b0cfe-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="b0cfe-133">默认值表</span><span class="sxs-lookup"><span data-stu-id="b0cfe-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
- [<span data-ttu-id="b0cfe-134">内置类型表</span><span class="sxs-lookup"><span data-stu-id="b0cfe-134">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="b0cfe-135">浮点型表</span><span class="sxs-lookup"><span data-stu-id="b0cfe-135">Floating-Point Types Table</span></span>](../../../csharp/language-reference/keywords/floating-point-types-table.md)  
- [<span data-ttu-id="b0cfe-136">隐式数值转换表</span><span class="sxs-lookup"><span data-stu-id="b0cfe-136">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
- [<span data-ttu-id="b0cfe-137">显式数值转换表</span><span class="sxs-lookup"><span data-stu-id="b0cfe-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
