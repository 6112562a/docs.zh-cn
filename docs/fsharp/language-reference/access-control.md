---
title: 访问控制
description: 了解如何控制访问编程元素，如类型、 方法和函数，在F#编程语言。
ms.date: 05/16/2016
ms.openlocfilehash: 8db178b26f3beb6ce95bff84ccad9ac9e8c40ce7
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612799"
---
# <a name="access-control"></a><span data-ttu-id="6a2cc-103">访问控制</span><span class="sxs-lookup"><span data-stu-id="6a2cc-103">Access Control</span></span>

<span data-ttu-id="6a2cc-104">*访问控制*指声明哪些客户端可以使用特定程序元素，如类型、 方法和函数。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-104">*Access control* refers to declaring which clients can use certain program elements, such as types, methods, and functions.</span></span>

## <a name="basics-of-access-control"></a><span data-ttu-id="6a2cc-105">访问控制的基础知识</span><span class="sxs-lookup"><span data-stu-id="6a2cc-105">Basics of Access Control</span></span>

<span data-ttu-id="6a2cc-106">在F#，访问控制说明符`public`， `internal`，并`private`可以应用于模块、 类型、 方法、 值定义、 函数、 属性和显式字段。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-106">In F#, the access control specifiers `public`, `internal`, and `private` can be applied to modules, types, methods, value definitions, functions, properties, and explicit fields.</span></span>

- <span data-ttu-id="6a2cc-107">`public` 指示所有调用方可以访问该实体。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-107">`public` indicates that the entity can be accessed by all callers.</span></span>

- <span data-ttu-id="6a2cc-108">`internal` 指示该实体，可以访问只能从同一程序集。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-108">`internal` indicates that the entity can be accessed only from the same assembly.</span></span>

- <span data-ttu-id="6a2cc-109">`private` 指示该实体，可以访问只能从封闭类型或模块。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-109">`private` indicates that the entity can be accessed only from the enclosing type or module.</span></span>

> [!NOTE]
> <span data-ttu-id="6a2cc-110">访问说明符`protected`中不使用F#，但如果使用的在支持的语言中编写的类型是可以接受`protected`访问权限。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-110">The access specifier `protected` is not used in F#, although it is acceptable if you are using types authored in languages that do support `protected` access.</span></span> <span data-ttu-id="6a2cc-111">因此，如果重写受保护的方法，仍然只能在类及其后代中访问你的方法。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-111">Therefore, if you override a protected method, your method remains accessible only within the class and its descendents.</span></span>

<span data-ttu-id="6a2cc-112">一般情况下，该说明符放前的实体，除非名称`mutable`或`inline`使用说明符，它的访问控制说明符后显示。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-112">In general, the specifier is put in front of the name of the entity, except when a `mutable` or `inline` specifier is used, which appear after the access control specifier.</span></span>

<span data-ttu-id="6a2cc-113">如果使用没有访问说明符，则默认值是`public`，除`let`绑定类型，它们始终`private`的类型。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-113">If no access specifier is used, the default is `public`, except for `let` bindings in a type, which are always `private` to the type.</span></span>

<span data-ttu-id="6a2cc-114">中的签名F#提供用于控制对访问另一种机制F#程序元素。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-114">Signatures in F# provide another mechanism for controlling access to F# program elements.</span></span> <span data-ttu-id="6a2cc-115">签名时不需要的访问控制。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-115">Signatures are not required for access control.</span></span> <span data-ttu-id="6a2cc-116">有关详细信息，请参阅[签名](signatures.md)。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-116">For more information, see [Signatures](signatures.md).</span></span>

## <a name="rules-for-access-control"></a><span data-ttu-id="6a2cc-117">用于访问控制规则</span><span class="sxs-lookup"><span data-stu-id="6a2cc-117">Rules for Access Control</span></span>

<span data-ttu-id="6a2cc-118">访问控制是遵循以下规则：</span><span class="sxs-lookup"><span data-stu-id="6a2cc-118">Access control is subject to the following rules:</span></span>

- <span data-ttu-id="6a2cc-119">继承声明 (即，使用`inherit`指定基类的类)、 接口声明 （即，指定一个类实现的接口），和抽象成员始终具有与封闭类型相同的可访问性。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-119">Inheritance declarations (that is, the use of `inherit` to specify a base class for a class), interface declarations (that is, specifying that a class implements an interface), and abstract members always have the same accessibility as the enclosing type.</span></span> <span data-ttu-id="6a2cc-120">因此，这些构造不能用于访问控制说明符。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-120">Therefore, an access control specifier cannot be used on these constructs.</span></span>

- <span data-ttu-id="6a2cc-121">可区分联合中的各个用例可访问性取决于可区分联合本身的可访问性。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-121">Accessibility for individual cases in a discriminated union is determined by the accessibility of the discriminated union itself.</span></span> <span data-ttu-id="6a2cc-122">也就是说，属于特定联合用例是不少可访问性低于联合本身。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-122">That is, a particular union case is no less accessible than the union itself.</span></span>

- <span data-ttu-id="6a2cc-123">可访问性的每个字段的记录类型不能确定记录本身的可访问性。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-123">Accessibility for individual fields of a record type cannot is determined by the accessibility of the record itself.</span></span> <span data-ttu-id="6a2cc-124">也就是说，特定记录标签是不少可访问性低于记录本身。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-124">That is, a particular record label is no less accessible than the record itself.</span></span>

## <a name="example"></a><span data-ttu-id="6a2cc-125">示例</span><span class="sxs-lookup"><span data-stu-id="6a2cc-125">Example</span></span>

<span data-ttu-id="6a2cc-126">下面的代码演示如何使用访问控制说明符。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-126">The following code illustrates the use of access control specifiers.</span></span> <span data-ttu-id="6a2cc-127">在项目中，有两个文件`Module1.fs`和`Module2.fs`。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-127">There are two files in the project, `Module1.fs` and `Module2.fs`.</span></span> <span data-ttu-id="6a2cc-128">每个文件隐式是一个模块。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-128">Each file is implicitly a module.</span></span> <span data-ttu-id="6a2cc-129">因此，有两个模块`Module1`和`Module2`。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-129">Therefore, there are two modules, `Module1` and `Module2`.</span></span> <span data-ttu-id="6a2cc-130">在中定义的私有类型和内部类型`Module1`。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-130">A private type and an internal type are defined in `Module1`.</span></span> <span data-ttu-id="6a2cc-131">不能从访问私有类型`Module2`，但可以内部类型。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-131">The private type cannot be accessed from `Module2`, but the internal type can.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet1.fs)]

<span data-ttu-id="6a2cc-132">下面的代码测试中创建的类型的可访问性`Module1.fs`。</span><span class="sxs-lookup"><span data-stu-id="6a2cc-132">The following code tests the accessibility of the types created in `Module1.fs`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/access-control/snippet2.fs)]

## <a name="see-also"></a><span data-ttu-id="6a2cc-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="6a2cc-133">See also</span></span>

- [<span data-ttu-id="6a2cc-134">F# 语言参考</span><span class="sxs-lookup"><span data-stu-id="6a2cc-134">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="6a2cc-135">签名</span><span class="sxs-lookup"><span data-stu-id="6a2cc-135">Signatures</span></span>](signatures.md)