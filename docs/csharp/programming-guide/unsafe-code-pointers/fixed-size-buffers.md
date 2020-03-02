---
title: 固定大小的缓冲区 - C# 编程指南
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 9005c425badc5a4ed74e6af3447e563daf61229e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627794"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="353cf-102">固定大小的缓冲区（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="353cf-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="353cf-103">在 C# 中，可以使用 [fixed](../../language-reference/keywords/fixed-statement.md) 语句来创建在数据结构中具有固定大小的数组的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="353cf-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="353cf-104">当编写与其他语言或平台的数据源进行互操作的方法时，固定大小的缓冲区很有用。</span><span class="sxs-lookup"><span data-stu-id="353cf-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="353cf-105">固定的数组可以采用允许用于常规结构成员的任何属性或修饰符。</span><span class="sxs-lookup"><span data-stu-id="353cf-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="353cf-106">唯一的限制是数组类型必须为 `bool`、`byte`、`char`、`short`、`int`, `long`、`sbyte`、`ushort`、`uint`、`ulong`、`float` 或 `double`。</span><span class="sxs-lookup"><span data-stu-id="353cf-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="353cf-107">备注</span><span class="sxs-lookup"><span data-stu-id="353cf-107">Remarks</span></span>

<span data-ttu-id="353cf-108">在安全代码中，包含数组的 C# 结构不包含该数组元素。</span><span class="sxs-lookup"><span data-stu-id="353cf-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="353cf-109">而该结构包含对元素的引用。</span><span class="sxs-lookup"><span data-stu-id="353cf-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="353cf-110">当在[不安全的](../../language-reference/keywords/unsafe.md)代码块中使用数组时，可以在[结构](../../language-reference/builtin-types/struct.md)中嵌入该固定大小的数组。</span><span class="sxs-lookup"><span data-stu-id="353cf-110">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="353cf-111">以下 `struct` 的大小为 8 字节。</span><span class="sxs-lookup"><span data-stu-id="353cf-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="353cf-112">`pathName` 数组是引用：</span><span class="sxs-lookup"><span data-stu-id="353cf-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="353cf-113">`struct` 可以在不安全代码中包含嵌入的数组。</span><span class="sxs-lookup"><span data-stu-id="353cf-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="353cf-114">在下面的示例中，`fixedBuffer` 数组具有固定的大小。</span><span class="sxs-lookup"><span data-stu-id="353cf-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="353cf-115">使用 `fixed` 语句建立指向第一个元素的指针。</span><span class="sxs-lookup"><span data-stu-id="353cf-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="353cf-116">通过此指针访问数组的元素。</span><span class="sxs-lookup"><span data-stu-id="353cf-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="353cf-117">`fixed` 语句将 `fixedBuffer` 实例字段固定到内存中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="353cf-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="353cf-118">包含 128 个元素的 `char` 数组的大小为 256 个字节。</span><span class="sxs-lookup"><span data-stu-id="353cf-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="353cf-119">固定大小的 [char](../../language-reference/builtin-types/char.md) 缓冲区每个字符始终占用两个字节，而不考虑编码。</span><span class="sxs-lookup"><span data-stu-id="353cf-119">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="353cf-120">甚至在将 char 缓冲区封送到 API 方法或具有 `CharSet = CharSet.Auto` 或 `CharSet = CharSet.Ansi` 的结构时，这也为 true。</span><span class="sxs-lookup"><span data-stu-id="353cf-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="353cf-121">有关更多信息，请参见<xref:System.Runtime.InteropServices.CharSet>。</span><span class="sxs-lookup"><span data-stu-id="353cf-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="353cf-122">前面的示例演示访问未固定的 `fixed` 字段，此功能从 C# 7.3 开始提供。</span><span class="sxs-lookup"><span data-stu-id="353cf-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="353cf-123">另一常见的固定大小的数组是 [bool](../../language-reference/builtin-types/bool.md) 数组。</span><span class="sxs-lookup"><span data-stu-id="353cf-123">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="353cf-124">`bool` 数组中的元素大小始终为一个字节。</span><span class="sxs-lookup"><span data-stu-id="353cf-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="353cf-125">`bool` 数组不适用于创建位数组或缓冲区。</span><span class="sxs-lookup"><span data-stu-id="353cf-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="353cf-126">除了通过使用 [stackalloc](../../language-reference/operators/stackalloc.md) 创建的内存外，C# 编译器和公共语言运行时 (CLR) 不执行任何安全缓冲区溢出检查。</span><span class="sxs-lookup"><span data-stu-id="353cf-126">Except for memory created by using [stackalloc](../../language-reference/operators/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="353cf-127">与所有不安全代码一样，请谨慎使用。</span><span class="sxs-lookup"><span data-stu-id="353cf-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="353cf-128">不安全的缓冲区与常规数组的区别体现在以下方面：</span><span class="sxs-lookup"><span data-stu-id="353cf-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="353cf-129">只能在不安全的上下文中使用不安全的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="353cf-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="353cf-130">不安全的缓冲区始终是矢量或一维数组。</span><span class="sxs-lookup"><span data-stu-id="353cf-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="353cf-131">数组的声明应包括计数，如 `char id[8]`。</span><span class="sxs-lookup"><span data-stu-id="353cf-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="353cf-132">不能使用 `char id[]`。</span><span class="sxs-lookup"><span data-stu-id="353cf-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="353cf-133">在不安全的上下文中，不安全的缓冲区只能是结构的实例字段。</span><span class="sxs-lookup"><span data-stu-id="353cf-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="353cf-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="353cf-134">See also</span></span>

- [<span data-ttu-id="353cf-135">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="353cf-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="353cf-136">不安全代码和指针</span><span class="sxs-lookup"><span data-stu-id="353cf-136">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="353cf-137">fixed 语句</span><span class="sxs-lookup"><span data-stu-id="353cf-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="353cf-138">互操作性</span><span class="sxs-lookup"><span data-stu-id="353cf-138">Interoperability</span></span>](../interop/index.md)
