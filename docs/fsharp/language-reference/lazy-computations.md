---
title: 延迟计算
description: 了解如何F#延迟计算可以提高性能的应用程序和库。
ms.date: 05/16/2016
ms.openlocfilehash: 35f4a3f7a88ef1650497e0c943234b3574d13b38
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610068"
---
# <a name="lazy-computations"></a><span data-ttu-id="6f3e4-103">延迟计算</span><span class="sxs-lookup"><span data-stu-id="6f3e4-103">Lazy Computations</span></span>

<span data-ttu-id="6f3e4-104">*延迟计算*都不会立即开始，但改为计算时所需结果的计算。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-104">*Lazy computations* are computations that are not evaluated immediately, but are instead evaluated when the result is needed.</span></span> <span data-ttu-id="6f3e4-105">这可以帮助提高代码的性能。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-105">This can help to improve the performance of your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="6f3e4-106">语法</span><span class="sxs-lookup"><span data-stu-id="6f3e4-106">Syntax</span></span>

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a><span data-ttu-id="6f3e4-107">备注</span><span class="sxs-lookup"><span data-stu-id="6f3e4-107">Remarks</span></span>

<span data-ttu-id="6f3e4-108">在上述语法中，*表达式*是仅时结果是必需的将计算的代码并*标识符*是将结果存储的值。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-108">In the previous syntax, *expression* is code that is evaluated only when a result is required, and *identifier* is a value that stores the result.</span></span> <span data-ttu-id="6f3e4-109">值为类型[ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489)，其中的实际类型用于`'T`根据表达式的结果。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-109">The value is of type [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), where the actual type that is used for `'T` is determined from the result of the expression.</span></span>

<span data-ttu-id="6f3e4-110">延迟计算，可通过限制到仅需要结果时这种情况下计算的执行，从而提高性能。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-110">Lazy computations enable you to improve performance by restricting the execution of a computation to only those situations in which a result is needed.</span></span>

<span data-ttu-id="6f3e4-111">若要强制执行计算，则调用方法`Force`。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-111">To force the computation to be performed, you call the method `Force`.</span></span> <span data-ttu-id="6f3e4-112">`Force` 将导致执行要执行仅一次。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-112">`Force` causes the execution to be performed only one time.</span></span> <span data-ttu-id="6f3e4-113">对后续调用`Force`返回相同的结果，但不是执行任何代码。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-113">Subsequent calls to `Force` return the same result, but do not execute any code.</span></span>

<span data-ttu-id="6f3e4-114">下面的代码演示使用惰性计算和使用`Force`。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-114">The following code illustrates the use of lazy computation and the use of `Force`.</span></span> <span data-ttu-id="6f3e4-115">在此代码的类型`result`是`Lazy<int>`，并`Force`方法将返回`int`。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-115">In this code, the type of `result` is `Lazy<int>`, and the `Force` method returns an `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

<span data-ttu-id="6f3e4-116">延迟计算，但不是`Lazy`类型，还可用于序列。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-116">Lazy evaluation, but not the `Lazy` type, is also used for sequences.</span></span> <span data-ttu-id="6f3e4-117">有关详细信息，请参阅[序列](sequences.md)。</span><span class="sxs-lookup"><span data-stu-id="6f3e4-117">For more information, see [Sequences](sequences.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6f3e4-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="6f3e4-118">See also</span></span>

- [<span data-ttu-id="6f3e4-119">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="6f3e4-119">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="6f3e4-120">LazyExtensions 模块</span><span class="sxs-lookup"><span data-stu-id="6f3e4-120">LazyExtensions module</span></span>](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)