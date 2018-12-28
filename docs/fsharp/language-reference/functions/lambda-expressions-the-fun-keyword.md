---
title: Lambda 表达式：Fun 关键字
description: 了解如何使用F#增添些乐趣关键字来定义 lambda 表达式，这是一个匿名函数。
ms.date: 05/16/2016
ms.openlocfilehash: 6ad15173bb8643bff330e3ca3823cba5d43ad445
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614452"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="5398e-103">Lambda 表达式：Fun 关键字 (F#)</span><span class="sxs-lookup"><span data-stu-id="5398e-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="5398e-104">`fun`关键字用于定义 lambda 表达式，即匿名函数。</span><span class="sxs-lookup"><span data-stu-id="5398e-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>

## <a name="syntax"></a><span data-ttu-id="5398e-105">语法</span><span class="sxs-lookup"><span data-stu-id="5398e-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="5398e-106">备注</span><span class="sxs-lookup"><span data-stu-id="5398e-106">Remarks</span></span>

<span data-ttu-id="5398e-107">*参数列表*通常包含的名称和 （可选） 参数的类型。</span><span class="sxs-lookup"><span data-stu-id="5398e-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="5398e-108">一般来说，*参数列表*可以是组合的任何F#模式。</span><span class="sxs-lookup"><span data-stu-id="5398e-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="5398e-109">有关可能模式的完整列表，请参阅[模式匹配](../pattern-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="5398e-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="5398e-110">有效参数列表包含下面的示例。</span><span class="sxs-lookup"><span data-stu-id="5398e-110">Lists of valid parameters include the following examples.</span></span>

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

<span data-ttu-id="5398e-111">*表达式*是其中的最后一个表达式会生成一个返回值的函数的正文。</span><span class="sxs-lookup"><span data-stu-id="5398e-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="5398e-112">有效的 lambda 表达式的示例包括：</span><span class="sxs-lookup"><span data-stu-id="5398e-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a><span data-ttu-id="5398e-113">使用 Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="5398e-113">Using Lambda Expressions</span></span>

<span data-ttu-id="5398e-114">当你想要在列表或其他集合上执行操作并想要避免额外的工作的定义函数时，lambda 表达式时特别有用。</span><span class="sxs-lookup"><span data-stu-id="5398e-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="5398e-115">许多F#库函数采用函数值作为参数，并可能会特别方便，可以在这些情况下使用 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="5398e-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="5398e-116">下面的代码将 lambda 表达式应用于列表中的元素。</span><span class="sxs-lookup"><span data-stu-id="5398e-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="5398e-117">在这种情况下，匿名函数将 1 添加到列表中的每个元素。</span><span class="sxs-lookup"><span data-stu-id="5398e-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a><span data-ttu-id="5398e-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="5398e-118">See also</span></span>

- [<span data-ttu-id="5398e-119">函数</span><span class="sxs-lookup"><span data-stu-id="5398e-119">Functions</span></span>](index.md)