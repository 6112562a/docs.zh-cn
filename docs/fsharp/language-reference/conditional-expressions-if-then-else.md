---
title: '条件表达式: if .。。then .。。其它'
description: 了解如何编写中F#的条件表达式来执行不同的代码分支。
ms.date: 05/16/2016
ms.openlocfilehash: 825149bf296eded3cc2b4d8847ba4d82bea40cdc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630394"
---
# <a name="conditional-expressions-ifthenelse"></a><span data-ttu-id="964e6-103">条件表达式:`if...then...else`</span><span class="sxs-lookup"><span data-stu-id="964e6-103">Conditional Expressions: `if...then...else`</span></span>

<span data-ttu-id="964e6-104">`if...then...else`表达式运行不同的代码分支, 还根据给定的布尔表达式计算出不同的值。</span><span class="sxs-lookup"><span data-stu-id="964e6-104">The `if...then...else` expression runs different branches of code and also evaluates to a different value depending on the Boolean expression given.</span></span>

## <a name="syntax"></a><span data-ttu-id="964e6-105">语法</span><span class="sxs-lookup"><span data-stu-id="964e6-105">Syntax</span></span>

```fsharp
if boolean-expression then expression1 [ else expression2 ]
```

## <a name="remarks"></a><span data-ttu-id="964e6-106">备注</span><span class="sxs-lookup"><span data-stu-id="964e6-106">Remarks</span></span>

<span data-ttu-id="964e6-107">在前面的语法中  , 如果布尔表达式的计算结果为`true`, 则表达式1将运行;*否则, 表达式*2 将运行。</span><span class="sxs-lookup"><span data-stu-id="964e6-107">In the previous syntax, *expression1* runs when the Boolean expression evaluates to `true`; otherwise, *expression2* runs.</span></span>

<span data-ttu-id="964e6-108">与其他语言不同, `if...then...else`构造是一个表达式, 而不是语句。</span><span class="sxs-lookup"><span data-stu-id="964e6-108">Unlike in other languages, the `if...then...else` construct is an expression, not a statement.</span></span> <span data-ttu-id="964e6-109">这意味着它会生成一个值, 该值是执行的分支中最后一个表达式的值。</span><span class="sxs-lookup"><span data-stu-id="964e6-109">That means that it produces a value, which is the value of the last expression in the branch that executes.</span></span> <span data-ttu-id="964e6-110">每个分支中生成的值的类型必须匹配。</span><span class="sxs-lookup"><span data-stu-id="964e6-110">The types of the values produced in each branch must match.</span></span> <span data-ttu-id="964e6-111">如果没有显式`else`分支, 则其类型为`unit`。</span><span class="sxs-lookup"><span data-stu-id="964e6-111">If there is no explicit `else` branch, its type is `unit`.</span></span> <span data-ttu-id="964e6-112">因此, 如果`then`分支的类型是以外的任何类型`unit` `else` , 则必须具有具有相同返回类型的分支。</span><span class="sxs-lookup"><span data-stu-id="964e6-112">Therefore, if the type of the `then` branch is any type other than `unit`, there must be an `else` branch with the same return type.</span></span> <span data-ttu-id="964e6-113">将表达式`if...then...else`链接在一起时, 可以使用关键字`elif`而不`else if`是; 它们是等效的。</span><span class="sxs-lookup"><span data-stu-id="964e6-113">When chaining `if...then...else` expressions together, you can use the keyword `elif` instead of `else if`; they are equivalent.</span></span>

## <a name="example"></a><span data-ttu-id="964e6-114">示例</span><span class="sxs-lookup"><span data-stu-id="964e6-114">Example</span></span>

<span data-ttu-id="964e6-115">下面的示例演示如何使用`if...then...else`表达式。</span><span class="sxs-lookup"><span data-stu-id="964e6-115">The following example illustrates how to use the `if...then...else` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4501.fs)]

```
10 is less than 20
What is your name? John
How old are you? 9
You are only 9 years old and already learning F#? Wow!
```

## <a name="see-also"></a><span data-ttu-id="964e6-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="964e6-116">See also</span></span>

- [<span data-ttu-id="964e6-117">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="964e6-117">F# Language Reference</span></span>](index.md)
