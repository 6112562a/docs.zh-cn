---
title: 对象表达式
description: 了解如何使用F#对象表达式时您想要避免额外的代码和开销所需创建一个新命名类型。
ms.date: 05/16/2016
ms.openlocfilehash: cb15983543fde2459c589b3de2554575d73db686
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613916"
---
# <a name="object-expressions"></a><span data-ttu-id="73593-103">对象表达式</span><span class="sxs-lookup"><span data-stu-id="73593-103">Object Expressions</span></span>

<span data-ttu-id="73593-104">*对象表达式*是表达式，它创建动态创建的匿名对象类型的新实例可基于现有基类型、 接口或接口集。</span><span class="sxs-lookup"><span data-stu-id="73593-104">An *object expression* is an expression that creates a new instance of a dynamically created, anonymous object type that is based on an existing base type, interface, or set of interfaces.</span></span>

## <a name="syntax"></a><span data-ttu-id="73593-105">语法</span><span class="sxs-lookup"><span data-stu-id="73593-105">Syntax</span></span>

```fsharp
// When typename is a class:
{ new typename [type-params]arguments with
    member-definitions
    [ additional-interface-definitions ]
}
// When typename is not a class:
{ new typename [generic-type-args] with
    member-definitions
    [ additional-interface-definitions ]
}
```

## <a name="remarks"></a><span data-ttu-id="73593-106">备注</span><span class="sxs-lookup"><span data-stu-id="73593-106">Remarks</span></span>

<span data-ttu-id="73593-107">在上述语法中， *typename*表示现有的类类型或接口类型。</span><span class="sxs-lookup"><span data-stu-id="73593-107">In the previous syntax, the *typename* represents an existing class type or interface type.</span></span> <span data-ttu-id="73593-108">*类型-params*介绍了可选的泛型类型参数。</span><span class="sxs-lookup"><span data-stu-id="73593-108">*type-params* describes the optional generic type parameters.</span></span> <span data-ttu-id="73593-109">*自变量*仅用于类类型，需要构造函数参数。</span><span class="sxs-lookup"><span data-stu-id="73593-109">The *arguments* are used only for class types, which require constructor parameters.</span></span> <span data-ttu-id="73593-110">*成员定义*替代基类方法，或从基类或接口的抽象方法的实现。</span><span class="sxs-lookup"><span data-stu-id="73593-110">The *member-definitions* are overrides of base class methods, or implementations of abstract methods from either a base class or an interface.</span></span>

<span data-ttu-id="73593-111">下面的示例演示了多种不同类型的对象表达式。</span><span class="sxs-lookup"><span data-stu-id="73593-111">The following example illustrates several different types of object expressions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4301.fs)]

## <a name="using-object-expressions"></a><span data-ttu-id="73593-112">使用对象表达式</span><span class="sxs-lookup"><span data-stu-id="73593-112">Using Object Expressions</span></span>

<span data-ttu-id="73593-113">当你想要避免额外的代码和创建所需的新命名类型的开销时，您可以使用对象表达式。</span><span class="sxs-lookup"><span data-stu-id="73593-113">You use object expressions when you want to avoid the extra code and overhead that is required to create a new, named type.</span></span> <span data-ttu-id="73593-114">如果您使用对象表达式在程序中创建的类型的数量降至最低，可以减少代码的行数，并防止不必要的迅速普及的类型。</span><span class="sxs-lookup"><span data-stu-id="73593-114">If you use object expressions to minimize the number of types created in a program, you can reduce the number of lines of code and prevent the unnecessary proliferation of types.</span></span> <span data-ttu-id="73593-115">而不是创建多个类型只是为了处理特定情况下，可以使用自定义现有类型或为手头的特定情况提供适当的接口实现的对象表达式。</span><span class="sxs-lookup"><span data-stu-id="73593-115">Instead of creating many types just to handle specific situations, you can use an object expression that customizes an existing type or provides an appropriate implementation of an interface for the specific case at hand.</span></span>

## <a name="see-also"></a><span data-ttu-id="73593-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="73593-116">See also</span></span>

- [<span data-ttu-id="73593-117">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="73593-117">F# Language Reference</span></span>](index.md)