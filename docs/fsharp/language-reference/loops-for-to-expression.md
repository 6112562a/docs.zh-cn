---
title: 循环：for...to 表达式
description: 请参阅如何F#数据类型...为表达式用于在循环中循环访问一系列循环变量的值。
ms.date: 05/16/2016
ms.openlocfilehash: 5b7bb9bac659ddf1d457be1ce17e90a2593666de
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645238"
---
# <a name="loops-forto-expression"></a><span data-ttu-id="8200c-103">循环：for...to 表达式</span><span class="sxs-lookup"><span data-stu-id="8200c-103">Loops: for...to Expression</span></span>

<span data-ttu-id="8200c-104">`for...to`表达式用于在循环中循环访问一系列循环变量的值。</span><span class="sxs-lookup"><span data-stu-id="8200c-104">The `for...to` expression is used to iterate in a loop over a range of values of a loop variable.</span></span>

## <a name="syntax"></a><span data-ttu-id="8200c-105">语法</span><span class="sxs-lookup"><span data-stu-id="8200c-105">Syntax</span></span>

```fsharp
for identifier = start [ to | downto ] finish do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="8200c-106">备注</span><span class="sxs-lookup"><span data-stu-id="8200c-106">Remarks</span></span>

<span data-ttu-id="8200c-107">标识符的类型推断的类型从*启动*并*完成*表达式。</span><span class="sxs-lookup"><span data-stu-id="8200c-107">The type of the identifier is inferred from the type of the *start* and *finish* expressions.</span></span> <span data-ttu-id="8200c-108">这些表达式的类型必须是 32 位整数。</span><span class="sxs-lookup"><span data-stu-id="8200c-108">Types for these expressions must be 32-bit integers.</span></span>

<span data-ttu-id="8200c-109">尽管从技术上讲一个表达式，但`for...to`更像是命令性编程语言中的传统语句。</span><span class="sxs-lookup"><span data-stu-id="8200c-109">Although technically an expression, `for...to` is more like a traditional statement in an imperative programming language.</span></span> <span data-ttu-id="8200c-110">返回类型*正文表达式*必须是`unit`。</span><span class="sxs-lookup"><span data-stu-id="8200c-110">The return type for the *body-expression* must be `unit`.</span></span> <span data-ttu-id="8200c-111">下面的示例演示的各种用法`for...to`表达式。</span><span class="sxs-lookup"><span data-stu-id="8200c-111">The following examples show various uses of the `for...to` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5101.fs)]

<span data-ttu-id="8200c-112">上述代码的输出结果如下。</span><span class="sxs-lookup"><span data-stu-id="8200c-112">The output of the previous code is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
10 9 8 7 6 5 4 3 2 1
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

## <a name="see-also"></a><span data-ttu-id="8200c-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="8200c-113">See also</span></span>

- [<span data-ttu-id="8200c-114">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="8200c-114">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="8200c-115">循环：`for...in` 表达式</span><span class="sxs-lookup"><span data-stu-id="8200c-115">Loops: `for...in` Expression</span></span>](loops-for-in-expression.md)
- [<span data-ttu-id="8200c-116">循环：`while...do` 表达式</span><span class="sxs-lookup"><span data-stu-id="8200c-116">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
