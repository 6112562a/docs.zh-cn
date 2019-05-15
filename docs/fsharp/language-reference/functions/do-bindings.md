---
title: do 绑定
description: 了解如何F#do 绑定用于执行代码而无需定义的函数或值。
ms.date: 05/16/2016
ms.openlocfilehash: 0755e36912fc4e5a645e55eb4bee5c730a56cadf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641917"
---
# <a name="do-bindings"></a><span data-ttu-id="7400c-103">do 绑定</span><span class="sxs-lookup"><span data-stu-id="7400c-103">do Bindings</span></span>

<span data-ttu-id="7400c-104">一个`do`绑定用于执行代码而无需定义的函数或值。</span><span class="sxs-lookup"><span data-stu-id="7400c-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="7400c-105">此外，不要绑定可以是在类中使用，请参阅[`do`类中的绑定](../members/do-bindings-in-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="7400c-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="7400c-106">语法</span><span class="sxs-lookup"><span data-stu-id="7400c-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="7400c-107">备注</span><span class="sxs-lookup"><span data-stu-id="7400c-107">Remarks</span></span>

<span data-ttu-id="7400c-108">使用`do`绑定时要执行独立于函数或值定义的代码。</span><span class="sxs-lookup"><span data-stu-id="7400c-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="7400c-109">中的表达式`do`绑定必须返回`unit`。</span><span class="sxs-lookup"><span data-stu-id="7400c-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="7400c-110">中的顶级代码`do`初始化模块时执行绑定。</span><span class="sxs-lookup"><span data-stu-id="7400c-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="7400c-111">关键字`do`是可选的。</span><span class="sxs-lookup"><span data-stu-id="7400c-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="7400c-112">特性可以应用于顶级`do`绑定。</span><span class="sxs-lookup"><span data-stu-id="7400c-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="7400c-113">例如，如果程序使用 COM 互操作，你可能想要应用`STAThread`属性到你的程序。</span><span class="sxs-lookup"><span data-stu-id="7400c-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="7400c-114">要做到这一点上使用属性`do`绑定，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="7400c-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]

## <a name="see-also"></a><span data-ttu-id="7400c-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="7400c-115">See also</span></span>

- [<span data-ttu-id="7400c-116">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="7400c-116">F# Language Reference</span></span>](../index.md)
- [<span data-ttu-id="7400c-117">函数</span><span class="sxs-lookup"><span data-stu-id="7400c-117">Functions</span></span>](index.md)
