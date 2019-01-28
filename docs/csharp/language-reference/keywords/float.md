---
title: float 关键字 - C# 参考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
ms.openlocfilehash: 6bf8043b97d23fdb91ca5798ed46cdea783bad7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514115"
---
# <a name="float-c-reference"></a><span data-ttu-id="030ec-102">float（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="030ec-102">float (C# Reference)</span></span>

<span data-ttu-id="030ec-103">`float` 关键字表示存储 32 位浮点值的简单类型。</span><span class="sxs-lookup"><span data-stu-id="030ec-103">The `float` keyword signifies a simple type that stores 32-bit floating-point values.</span></span> <span data-ttu-id="030ec-104">下表显示了 `float` 类型的精度和大致范围。</span><span class="sxs-lookup"><span data-stu-id="030ec-104">The following table shows the precision and approximate range for the `float` type.</span></span>

|<span data-ttu-id="030ec-105">类型</span><span class="sxs-lookup"><span data-stu-id="030ec-105">Type</span></span>|<span data-ttu-id="030ec-106">大致范围</span><span class="sxs-lookup"><span data-stu-id="030ec-106">Approximate range</span></span>|<span data-ttu-id="030ec-107">精度</span><span class="sxs-lookup"><span data-stu-id="030ec-107">Precision</span></span>|<span data-ttu-id="030ec-108">.NET 类型</span><span class="sxs-lookup"><span data-stu-id="030ec-108">.NET type</span></span>|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|<span data-ttu-id="030ec-109">±1.5 x 10<sup>−45</sup> 至 ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="030ec-109">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="030ec-110">大约 6-9 位数字</span><span class="sxs-lookup"><span data-stu-id="030ec-110">~6-9 digits</span></span>|<xref:System.Single?displayProperty=nameWithType>|  

## <a name="literals"></a><span data-ttu-id="030ec-111">文本</span><span class="sxs-lookup"><span data-stu-id="030ec-111">Literals</span></span>

<span data-ttu-id="030ec-112">默认情况下，赋值运算符右侧的实数被视为 [double](double.md)。</span><span class="sxs-lookup"><span data-stu-id="030ec-112">By default, a real numeric literal on the right side of the assignment operator is treated as [double](double.md).</span></span> <span data-ttu-id="030ec-113">因此，若要初始化浮点型变量，请使用后缀 `f` 或 `F`，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="030ec-113">Therefore, to initialize a float variable, use the suffix `f` or `F`, as in the following example:</span></span>

```csharp
float x = 3.5F;
```

<span data-ttu-id="030ec-114">如果不在前面的声明中使用后缀，则会收到编译错误，因为你正尝试将 [double](double.md) 值存储到 `float` 变量。</span><span class="sxs-lookup"><span data-stu-id="030ec-114">If you do not use the suffix in the previous declaration, you will get a compilation error because you are trying to store a [double](double.md) value into a `float` variable.</span></span>

## <a name="conversions"></a><span data-ttu-id="030ec-115">转换</span><span class="sxs-lookup"><span data-stu-id="030ec-115">Conversions</span></span>

<span data-ttu-id="030ec-116">可以在表达式中混合使用数值整型和浮点类型。</span><span class="sxs-lookup"><span data-stu-id="030ec-116">You can mix numeric integral types and floating-point types in an expression.</span></span> <span data-ttu-id="030ec-117">在这种情况下，整数类型将转换为浮点类型。</span><span class="sxs-lookup"><span data-stu-id="030ec-117">In this case, the integral types are converted to floating-point types.</span></span> <span data-ttu-id="030ec-118">根据以下规则对表达式求值：</span><span class="sxs-lookup"><span data-stu-id="030ec-118">The evaluation of the expression is performed according to the following rules:</span></span>

- <span data-ttu-id="030ec-119">如果其中一个浮点类型是 [double](double.md)，该表达式在关系比较或相等比较中求值类型为 [double](double.md) 或 [bool](bool.md)。</span><span class="sxs-lookup"><span data-stu-id="030ec-119">If one of the floating-point types is [double](double.md), the expression evaluates to [double](double.md), or to [bool](bool.md) in relational comparisons or comparisons for equality.</span></span>

- <span data-ttu-id="030ec-120">如果表达式中没有 [double](double.md) 类型，则表达式在关系比较或相等比较中求值类型为 `float` 或 [bool](bool.md)。</span><span class="sxs-lookup"><span data-stu-id="030ec-120">If there is no [double](double.md) type in the expression, the expression evaluates to `float`, or to [bool](bool.md) in relational comparisons or comparisons for equality.</span></span>

<span data-ttu-id="030ec-121">浮点表达式可以包含下列值集：</span><span class="sxs-lookup"><span data-stu-id="030ec-121">A floating-point expression can contain the following sets of values:</span></span>

- <span data-ttu-id="030ec-122">正和负零</span><span class="sxs-lookup"><span data-stu-id="030ec-122">Positive and negative zero</span></span>

- <span data-ttu-id="030ec-123">正和负无穷大</span><span class="sxs-lookup"><span data-stu-id="030ec-123">Positive and negative infinity</span></span>

- <span data-ttu-id="030ec-124">非数字值 (NaN)</span><span class="sxs-lookup"><span data-stu-id="030ec-124">Not-a-Number value (NaN)</span></span>

- <span data-ttu-id="030ec-125">一组有限的非零值</span><span class="sxs-lookup"><span data-stu-id="030ec-125">The finite set of nonzero values</span></span>

<span data-ttu-id="030ec-126">有关这些值的详细信息，请参阅 [IEEE](https://www.ieee.org) 网站中提供的二进制浮点算术的 IEEE 标准。</span><span class="sxs-lookup"><span data-stu-id="030ec-126">For more information about these values, see IEEE Standard for Binary Floating-Point Arithmetic, available on the [IEEE](https://www.ieee.org) website.</span></span>

## <a name="example"></a><span data-ttu-id="030ec-127">示例</span><span class="sxs-lookup"><span data-stu-id="030ec-127">Example</span></span>

<span data-ttu-id="030ec-128">在下面的示例中，提供 `float` 结果的数学表达式中包含 [int](int.md)、[short](short.md) 和 `float`。</span><span class="sxs-lookup"><span data-stu-id="030ec-128">In the following example, an [int](int.md), a [short](short.md), and a `float` are included in a mathematical expression giving a `float` result.</span></span> <span data-ttu-id="030ec-129">（请记住，`float` 是 <xref:System.Single?displayProperty=nameWithType> 类型的别名。）请注意，表达式中没有任何 [double](double.md)。</span><span class="sxs-lookup"><span data-stu-id="030ec-129">(Remember that `float` is an alias for the <xref:System.Single?displayProperty=nameWithType> type.) Notice that there is no [double](double.md) in the expression.</span></span>

[!code-csharp[csrefKeywordsTypes#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#13)]

## <a name="c-language-specification"></a><span data-ttu-id="030ec-130">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="030ec-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="030ec-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="030ec-131">See also</span></span>

- <xref:System.Single>
- [<span data-ttu-id="030ec-132">C# 参考</span><span class="sxs-lookup"><span data-stu-id="030ec-132">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="030ec-133">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="030ec-133">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="030ec-134">强制转换和类型转换</span><span class="sxs-lookup"><span data-stu-id="030ec-134">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="030ec-135">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="030ec-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="030ec-136">整型表</span><span class="sxs-lookup"><span data-stu-id="030ec-136">Integral Types Table</span></span>](integral-types-table.md)
- [<span data-ttu-id="030ec-137">内置类型表</span><span class="sxs-lookup"><span data-stu-id="030ec-137">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="030ec-138">隐式数值转换表</span><span class="sxs-lookup"><span data-stu-id="030ec-138">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="030ec-139">显式数值转换表</span><span class="sxs-lookup"><span data-stu-id="030ec-139">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
