---
title: 委托
description: 了解如何在使用中的委托F#。
ms.date: 05/16/2016
ms.openlocfilehash: 0596b67530b0399df41dffdf855a07bce2bf4761
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641972"
---
# <a name="delegates"></a><span data-ttu-id="30ec4-103">委托</span><span class="sxs-lookup"><span data-stu-id="30ec4-103">Delegates</span></span>

<span data-ttu-id="30ec4-104">一个委托作为一个对象表示一个函数调用。</span><span class="sxs-lookup"><span data-stu-id="30ec4-104">A delegate represents a function call as an object.</span></span> <span data-ttu-id="30ec4-105">在F#，你通常应使用函数的值来表示作为一类值; 函数但是，委托在.NET Framework 中使用，因此时，需要与所希望的 Api 进行互操作。</span><span class="sxs-lookup"><span data-stu-id="30ec4-105">In F#, you ordinarily should use function values to represent functions as first-class values; however, delegates are used in the .NET Framework and so are needed when you interoperate with APIs that expect them.</span></span> <span data-ttu-id="30ec4-106">可能还会使用它们时从其他.NET Framework 语言创作库设计用于使用。</span><span class="sxs-lookup"><span data-stu-id="30ec4-106">They may also be used when authoring libraries designed for use from other .NET Framework languages.</span></span>

## <a name="syntax"></a><span data-ttu-id="30ec4-107">语法</span><span class="sxs-lookup"><span data-stu-id="30ec4-107">Syntax</span></span>

```fsharp
type delegate-typename = delegate of type1 -> type2
```

## <a name="remarks"></a><span data-ttu-id="30ec4-108">备注</span><span class="sxs-lookup"><span data-stu-id="30ec4-108">Remarks</span></span>

<span data-ttu-id="30ec4-109">在上述语法中，`type1`表示的参数类型和`type2`表示返回类型。</span><span class="sxs-lookup"><span data-stu-id="30ec4-109">In the previous syntax, `type1` represents the argument type or types and `type2` represents the return type.</span></span> <span data-ttu-id="30ec4-110">由自变量类型`type1`会自动进行扩充。</span><span class="sxs-lookup"><span data-stu-id="30ec4-110">The argument types that are represented by `type1` are automatically curried.</span></span> <span data-ttu-id="30ec4-111">这表明，如果目标函数的参数会进行扩充，使用元组形式的此类型和已在元组形式的参数的带括号的元组。</span><span class="sxs-lookup"><span data-stu-id="30ec4-111">This suggests that for this type you use a tuple form if the arguments of the target function are curried, and a parenthesized tuple for arguments that are already in the tuple form.</span></span> <span data-ttu-id="30ec4-112">自动科中删除一组括号，离开匹配的目标方法的元组参数。</span><span class="sxs-lookup"><span data-stu-id="30ec4-112">The automatic currying removes a set of parentheses, leaving a tuple argument that matches the target method.</span></span> <span data-ttu-id="30ec4-113">请参阅中每种情况下应使用的语法的代码示例。</span><span class="sxs-lookup"><span data-stu-id="30ec4-113">Refer to the code example for the syntax you should use in each case.</span></span>

<span data-ttu-id="30ec4-114">可以将委托附加到F#函数的值以及静态或实例方法。</span><span class="sxs-lookup"><span data-stu-id="30ec4-114">Delegates can be attached to F# function values, and static or instance methods.</span></span> <span data-ttu-id="30ec4-115">F#可以直接作为要委托构造函数自变量传递函数值。</span><span class="sxs-lookup"><span data-stu-id="30ec4-115">F# function values can be passed directly as arguments to delegate constructors.</span></span> <span data-ttu-id="30ec4-116">对于静态方法，使用的类和方法名称构造委托。</span><span class="sxs-lookup"><span data-stu-id="30ec4-116">For a static method, you construct the delegate by using the name of the class and the method.</span></span> <span data-ttu-id="30ec4-117">对于实例方法，需要提供的对象实例和一个自变量中的方法。</span><span class="sxs-lookup"><span data-stu-id="30ec4-117">For an instance method, you provide the object instance and method in one argument.</span></span> <span data-ttu-id="30ec4-118">在这两种情况下，成员访问运算符 (`.`) 使用。</span><span class="sxs-lookup"><span data-stu-id="30ec4-118">In both cases, the member access operator (`.`) is used.</span></span>

<span data-ttu-id="30ec4-119">`Invoke`委托类型的方法调用封装的函数。</span><span class="sxs-lookup"><span data-stu-id="30ec4-119">The `Invoke` method on the delegate type calls the encapsulated function.</span></span> <span data-ttu-id="30ec4-120">此外，还可以引用不带括号的 Invoke 方法名称作为函数值传递委托。</span><span class="sxs-lookup"><span data-stu-id="30ec4-120">Also, delegates can be passed as function values by referencing the Invoke method name without the parentheses.</span></span>

<span data-ttu-id="30ec4-121">下面的代码演示用于创建表示在类中的各种方法的委托的语法。</span><span class="sxs-lookup"><span data-stu-id="30ec4-121">The following code shows the syntax for creating delegates that represent various methods in a class.</span></span> <span data-ttu-id="30ec4-122">具体取决于的方法是静态方法或实例方法，以及是否有元组形式或扩充窗体中的自变量，声明和赋值委托语法是稍有不同。</span><span class="sxs-lookup"><span data-stu-id="30ec4-122">Depending on whether the method is a static method or an instance method, and whether it has arguments in the tuple form or the curried form, the syntax for declaring and assigning the delegate is a little different.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4201.fs)]

<span data-ttu-id="30ec4-123">下面的代码显示了一些可以在使用委托的不同方法。</span><span class="sxs-lookup"><span data-stu-id="30ec4-123">The following code shows some of the different ways you can work with delegates.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4202.fs)]

<span data-ttu-id="30ec4-124">前面的代码示例的输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="30ec4-124">The output of the previous code example is as follows.</span></span>

```console
aaaaa
bbbbb
ccccc
[|"aaa"; "bbb"|]
```

## <a name="see-also"></a><span data-ttu-id="30ec4-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="30ec4-125">See also</span></span>

- [<span data-ttu-id="30ec4-126">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="30ec4-126">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="30ec4-127">参数和自变量</span><span class="sxs-lookup"><span data-stu-id="30ec4-127">Parameters and Arguments</span></span>](parameters-and-arguments.md)
- [<span data-ttu-id="30ec4-128">事件</span><span class="sxs-lookup"><span data-stu-id="30ec4-128">Events</span></span>](members/events.md)
