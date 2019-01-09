---
title: ULong 数据类型 (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.ulong
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- literal type characters [Visual Basic], UL
- ULong data type
- UL literal type characters [Visual Basic]
ms.assetid: 017e0702-774e-44ae-bedc-786b424ca84e
ms.openlocfilehash: d901dc6c0a11db1beb08be821aec4dc1179832ff
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148365"
---
# <a name="ulong-data-type-visual-basic"></a><span data-ttu-id="00fb5-102">ULong 数据类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00fb5-102">ULong data type (Visual Basic)</span></span>

<span data-ttu-id="00fb5-103">保存取值范围为 0 到 18446744073709551615 的无符号的 64 位 （8 字节） 整数 (多个 1.84 倍 10 ^19)。</span><span class="sxs-lookup"><span data-stu-id="00fb5-103">Holds unsigned 64-bit (8-byte) integers ranging in value from 0 through 18,446,744,073,709,551,615 (more than 1.84 times 10 ^ 19).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00fb5-104">备注</span><span class="sxs-lookup"><span data-stu-id="00fb5-104">Remarks</span></span>

<span data-ttu-id="00fb5-105">使用`ULong`数据类型来包含二进制数据太大， `UInteger`，或可能的最大无符号整数值。</span><span class="sxs-lookup"><span data-stu-id="00fb5-105">Use the `ULong` data type to contain binary data too large for `UInteger`, or the largest possible unsigned integer values.</span></span>  
  
<span data-ttu-id="00fb5-106">`ULong` 的默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="00fb5-106">The default value of `ULong` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="00fb5-107">文本分配</span><span class="sxs-lookup"><span data-stu-id="00fb5-107">Literal assignments</span></span>

<span data-ttu-id="00fb5-108">您可以声明并初始化`ULong`变量由将其分配十进制文本、 十六进制文本八进制文本，或 （Visual Basic 从 2017年开始） 二进制文本。</span><span class="sxs-lookup"><span data-stu-id="00fb5-108">You can declare and initialize a `ULong` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="00fb5-109">如果整数文本在 `ULong` 范围之外（即，如果它小于 <xref:System.UInt64.MinValue?displayProperty=nameWithType> 或大于 <xref:System.UInt64.MaxValue?displayProperty=nameWithType>），会发生编译错误。</span><span class="sxs-lookup"><span data-stu-id="00fb5-109">If the integer literal is outside the range of `ULong` (that is, if it is less than <xref:System.UInt64.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt64.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="00fb5-110">在以下示例中，表示为十进制、十六进制和二进制文本且等于 7,934,076,125 的整数被分配给 `ULong` 值。</span><span class="sxs-lookup"><span data-stu-id="00fb5-110">In the following example, integers equal to 7,934,076,125 that are represented as decimal, hexadecimal, and binary literals are assigned to `ULong` values.</span></span>
  
[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ULong)]

> [!NOTE] 
> <span data-ttu-id="00fb5-111">使用前缀`&h`或`&H`来表示十六进制文本前缀`&b`或`&B`来表示二进制文本和前缀`&o`或`&O`来表示八进制文本。</span><span class="sxs-lookup"><span data-stu-id="00fb5-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="00fb5-112">十进制文本没有前缀。</span><span class="sxs-lookup"><span data-stu-id="00fb5-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="00fb5-113">从 Visual Basic 2017 开始，你还可以使用下划线字符， `_`，作为数字分隔符，以增强可读性，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="00fb5-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[ULong](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#LongS)]

<span data-ttu-id="00fb5-114">从 Visual Basic 15.5 开始，你还可以使用下划线字符 (`_`) 作为前缀和十六进制、 二进制或八进制数字之间的前导分隔符。</span><span class="sxs-lookup"><span data-stu-id="00fb5-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="00fb5-115">例如：</span><span class="sxs-lookup"><span data-stu-id="00fb5-115">For example:</span></span>

```vb
Dim number As ULong = &H_F9AC_0326_1489_D68C
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="00fb5-116">此外可以包含数值`UL`或`ul`[键入字符](../../programming-guide/language-features/data-types/type-characters.md)来表示`ULong`数据类型，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="00fb5-116">Numeric literals can also include the `UL` or `ul` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `ULong` data type, as the following example shows.</span></span>

```vb
Dim number = &H_00_00_0A_96_2F_AC_14_D7ul
```

## <a name="programming-tips"></a><span data-ttu-id="00fb5-117">编程提示</span><span class="sxs-lookup"><span data-stu-id="00fb5-117">Programming tips</span></span>
  
-   <span data-ttu-id="00fb5-118">**负号。**</span><span class="sxs-lookup"><span data-stu-id="00fb5-118">**Negative Numbers.**</span></span> <span data-ttu-id="00fb5-119">因为`ULong`是无符号的类型，它不能表示为负数。</span><span class="sxs-lookup"><span data-stu-id="00fb5-119">Because `ULong` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="00fb5-120">如果使用一元负 (`-`) 运算符的表达式的计算结果为类型`ULong`，Visual Basic 将转换为表达式`Decimal`第一个。</span><span class="sxs-lookup"><span data-stu-id="00fb5-120">If you use the unary minus (`-`) operator on an expression that evaluates to type `ULong`, Visual Basic converts the expression to `Decimal` first.</span></span>  
  
-   <span data-ttu-id="00fb5-121">**CLS 遵从性。**</span><span class="sxs-lookup"><span data-stu-id="00fb5-121">**CLS Compliance.**</span></span> <span data-ttu-id="00fb5-122">`ULong`数据类型不属于[公共语言规范](https://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS)，因此符合 cls 的代码不能使用使用它的组件。</span><span class="sxs-lookup"><span data-stu-id="00fb5-122">The `ULong` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>  
  
-   <span data-ttu-id="00fb5-123">**互操作注意事项。**</span><span class="sxs-lookup"><span data-stu-id="00fb5-123">**Interop Considerations.**</span></span> <span data-ttu-id="00fb5-124">如果你与不是为.NET Framework 中，如自动化或 COM 对象，编写组件交互请记住，类型，如`ulong`可以在其他环境中具有不同的数据宽度 （32 位）。</span><span class="sxs-lookup"><span data-stu-id="00fb5-124">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `ulong` can have a different data width (32 bits) in other environments.</span></span> <span data-ttu-id="00fb5-125">如果您将 32 位自变量传递给此类组件，将其作为声明`UInteger`而不是`ULong`中托管的 Visual Basic 代码。</span><span class="sxs-lookup"><span data-stu-id="00fb5-125">If you are passing a 32-bit argument to such a component, declare it as `UInteger` instead of `ULong` in your managed Visual Basic code.</span></span>  
  
     <span data-ttu-id="00fb5-126">此外，自动化不支持在 Windows 95、 Windows 98、 Windows ME 或 Windows 2000 上 64 位整数。</span><span class="sxs-lookup"><span data-stu-id="00fb5-126">Furthermore, Automation does not support 64-bit integers on Windows 95, Windows 98, Windows ME, or Windows 2000.</span></span> <span data-ttu-id="00fb5-127">不能将传递一个 Visual Basic`ULong`到这些平台上自动化组件的参数。</span><span class="sxs-lookup"><span data-stu-id="00fb5-127">You cannot pass a Visual Basic `ULong` argument to an Automation component on these platforms.</span></span>  
  
-   <span data-ttu-id="00fb5-128">**扩大转换。**</span><span class="sxs-lookup"><span data-stu-id="00fb5-128">**Widening.**</span></span> <span data-ttu-id="00fb5-129">`ULong`数据类型加宽到`Decimal`， `Single`，和`Double`。</span><span class="sxs-lookup"><span data-stu-id="00fb5-129">The `ULong` data type widens to `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="00fb5-130">这意味着可以将转换`ULong`而不会遇到这些类型的任何<xref:System.OverflowException?displayProperty=nameWithType>错误。</span><span class="sxs-lookup"><span data-stu-id="00fb5-130">This means you can convert `ULong` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="00fb5-131">**类型字符。**</span><span class="sxs-lookup"><span data-stu-id="00fb5-131">**Type Characters.**</span></span> <span data-ttu-id="00fb5-132">追加文本类型字符`UL`为文本将其强制转换到`ULong`数据类型。</span><span class="sxs-lookup"><span data-stu-id="00fb5-132">Appending the literal type characters `UL` to a literal forces it to the `ULong` data type.</span></span> <span data-ttu-id="00fb5-133">`ULong` 有没有标识符类型字符。</span><span class="sxs-lookup"><span data-stu-id="00fb5-133">`ULong` has no identifier type character.</span></span>
  
-   <span data-ttu-id="00fb5-134">**Framework 类型。**</span><span class="sxs-lookup"><span data-stu-id="00fb5-134">**Framework Type.**</span></span> <span data-ttu-id="00fb5-135">.NET Framework 中的对应类型是 <xref:System.UInt64?displayProperty=nameWithType> 结构。</span><span class="sxs-lookup"><span data-stu-id="00fb5-135">The corresponding type in the .NET Framework is the <xref:System.UInt64?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00fb5-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="00fb5-136">See also</span></span>

 <xref:System.UInt64>  
 [<span data-ttu-id="00fb5-137">数据类型</span><span class="sxs-lookup"><span data-stu-id="00fb5-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="00fb5-138">类型转换函数</span><span class="sxs-lookup"><span data-stu-id="00fb5-138">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="00fb5-139">转换摘要</span><span class="sxs-lookup"><span data-stu-id="00fb5-139">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="00fb5-140">如何：调用需要使用无符号类型的 Windows 函数</span><span class="sxs-lookup"><span data-stu-id="00fb5-140">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="00fb5-141">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="00fb5-141">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
