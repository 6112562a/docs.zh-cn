---
title: '@ - C# 参考'
ms.date: 02/09/2017
f1_keywords:
- '@_CSharpKeyword'
- '@'
helpviewer_keywords:
- '@ special character [C#]'
- '@ language element [C#]'
ms.assetid: 89bc7e53-85f5-478a-866d-1cca003c4e8c
ms.openlocfilehash: b37f77273e767a5e5292e7707933892f57811d2a
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291766"
---
# <a name="-c-reference"></a><span data-ttu-id="6133a-102">@（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="6133a-102">@ (C# Reference)</span></span>

<span data-ttu-id="6133a-103">`@` 特殊字符用作原义标识符。</span><span class="sxs-lookup"><span data-stu-id="6133a-103">The `@` special character serves as a verbatim identifier.</span></span> <span data-ttu-id="6133a-104">它具有以下用途：</span><span class="sxs-lookup"><span data-stu-id="6133a-104">It can be used in the following ways:</span></span>

1. <span data-ttu-id="6133a-105">使 C# 关键字用作标识符。</span><span class="sxs-lookup"><span data-stu-id="6133a-105">To enable C# keywords to be used as identifiers.</span></span> <span data-ttu-id="6133a-106">`@` 字符可作为代码元素的前缀，编译器将把此代码元素解释为标识符而非 C# 关键字。</span><span class="sxs-lookup"><span data-stu-id="6133a-106">The `@` character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.</span></span> <span data-ttu-id="6133a-107">下面的示例使用 `@` 字符定义其在 `for` 循环中使用的名为 `for` 的标识符。</span><span class="sxs-lookup"><span data-stu-id="6133a-107">The following example uses the `@` character to define an identifier named `for` that it uses in a `for` loop.</span></span>

   [!code-csharp[verbatim1](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#1)]

1. <span data-ttu-id="6133a-108">指示将原义解释字符串。</span><span class="sxs-lookup"><span data-stu-id="6133a-108">To indicate that a string literal is to be interpreted verbatim.</span></span> <span data-ttu-id="6133a-109">`@` 字符在此实例中定义原义标识符  。</span><span class="sxs-lookup"><span data-stu-id="6133a-109">The `@` character in this instance defines a *verbatim string literal*.</span></span> <span data-ttu-id="6133a-110">简单转义序列（如代表反斜杠的 `"\\"`）、十六进制转义序列（如代表大写字母 A 的 `"\x0041"`）和 Unicode 转义序列（如代表大写字母 A 的 `"\u0041"`）都将按字面解释。</span><span class="sxs-lookup"><span data-stu-id="6133a-110">Simple escape sequences (such as `"\\"` for a backslash), hexadecimal escape sequences (such as `"\x0041"` for an uppercase A), and Unicode escape sequences (such as `"\u0041"` for an uppercase A) are interpreted literally.</span></span> <span data-ttu-id="6133a-111">只有引号转义序列 (`""`) 不会按字面解释；因为它生成一个双引号。</span><span class="sxs-lookup"><span data-stu-id="6133a-111">Only a quote escape sequence (`""`) is not interpreted literally; it produces one double quotation mark.</span></span> <span data-ttu-id="6133a-112">此外，如果是逐字[内插字符串](interpolated.md)，大括号转义序列（`{{` 和 `}}`）不按字面解释；它们会生成单个大括号字符。</span><span class="sxs-lookup"><span data-stu-id="6133a-112">Additionally, in case of a verbatim [interpolated string](interpolated.md) brace escape sequences (`{{` and `}}`) are not interpreted literally; they produce single brace characters.</span></span> <span data-ttu-id="6133a-113">下面的示例分别使用常规字符串和原义字符串定义两个相同的文件路径。</span><span class="sxs-lookup"><span data-stu-id="6133a-113">The following example defines two identical file paths, one by using a regular string literal and the other by using a verbatim string literal.</span></span> <span data-ttu-id="6133a-114">这是原义字符串的较常见用法之一。</span><span class="sxs-lookup"><span data-stu-id="6133a-114">This is one of the more common uses of verbatim string literals.</span></span>

   [!code-csharp[verbatim2](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#2)]

   <span data-ttu-id="6133a-115">下面的示例演示定义包含相同字符序列的常规字符串和原义字符串的效果。</span><span class="sxs-lookup"><span data-stu-id="6133a-115">The following example illustrates the effect of defining a regular string literal and a verbatim string literal that contain identical character sequences.</span></span>

   [!code-csharp[verbatim3](../../../../samples/snippets/csharp/language-reference/keywords/verbatim1.cs#3)]

1. <span data-ttu-id="6133a-116">使编译器在命名冲突的情况下区分两种属性。</span><span class="sxs-lookup"><span data-stu-id="6133a-116">To enable the compiler to distinguish between attributes in cases of a naming conflict.</span></span> <span data-ttu-id="6133a-117">属性是派生自 <xref:System.Attribute> 的类。</span><span class="sxs-lookup"><span data-stu-id="6133a-117">An attribute is a class that derives from <xref:System.Attribute>.</span></span> <span data-ttu-id="6133a-118">其类型名称通常包含后缀 **Attribute**，但编译器不会强制进行此转换。</span><span class="sxs-lookup"><span data-stu-id="6133a-118">Its type name typically includes the suffix **Attribute**, although the compiler does not enforce this convention.</span></span> <span data-ttu-id="6133a-119">随后可在代码中按其完整类型名称（例如 `[InfoAttribute]`）或短名称（例如 `[Info]`）引用此属性。</span><span class="sxs-lookup"><span data-stu-id="6133a-119">The attribute can then be referenced in code either by its full type name (for example, `[InfoAttribute]` or its shortened name (for example, `[Info]`).</span></span> <span data-ttu-id="6133a-120">但是，如果两个短名称相同，并且一个类型名称包含 **Attribute** 后缀而另一类型名称不包含，则会出现命名冲突。</span><span class="sxs-lookup"><span data-stu-id="6133a-120">However, a naming conflict occurs if two shortened attribute type names are identical, and one type name includes the **Attribute** suffix but the other does not.</span></span> <span data-ttu-id="6133a-121">例如，由于编译器无法确定将 `Info` 还是 `InfoAttribute` 属性应用于 `Example` 类，因此下面的代码无法编译。</span><span class="sxs-lookup"><span data-stu-id="6133a-121">For example, the following code fails to compile because the compiler cannot determine whether the `Info` or `InfoAttribute` attribute is applied to the `Example` class.</span></span> <span data-ttu-id="6133a-122">有关详细信息，请参阅 [CS1614](../compiler-messages/cs1614.md)。</span><span class="sxs-lookup"><span data-stu-id="6133a-122">See [CS1614](../compiler-messages/cs1614.md) for more information.</span></span>

   [!code-csharp[verbatim4](../../../../samples/snippets/csharp/language-reference/keywords/verbatim2.cs#1)]

## <a name="see-also"></a><span data-ttu-id="6133a-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="6133a-123">See also</span></span>

- [<span data-ttu-id="6133a-124">C# 参考</span><span class="sxs-lookup"><span data-stu-id="6133a-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6133a-125">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="6133a-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6133a-126">C# 特殊字符</span><span class="sxs-lookup"><span data-stu-id="6133a-126">C# Special Characters</span></span>](./index.md)
