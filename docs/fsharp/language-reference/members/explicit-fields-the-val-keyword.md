---
title: 显式字段：Val 关键字
description: 了解如何F#值关键字用于声明类或结构类型中存储一个值，而不初始化该类型的位置。
ms.date: 05/16/2016
ms.openlocfilehash: 492541f6eeba94d2177e92de935fa524b9def567
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/22/2018
ms.locfileid: "53773622"
---
# <a name="explicit-fields-the-val-keyword"></a><span data-ttu-id="0277b-103">显式字段：Val 关键字</span><span class="sxs-lookup"><span data-stu-id="0277b-103">Explicit Fields: The val Keyword</span></span>

<span data-ttu-id="0277b-104">`val` 关键字用于声明在类或结构类型中存储一个值（但不初始化该值）的位置。</span><span class="sxs-lookup"><span data-stu-id="0277b-104">The `val` keyword is used to declare a location to store a value in a class or structure type, without initializing it.</span></span> <span data-ttu-id="0277b-105">在这种方式中声明的存储位置称为*显式字段*。</span><span class="sxs-lookup"><span data-stu-id="0277b-105">Storage locations declared in this manner are called *explicit fields*.</span></span> <span data-ttu-id="0277b-106">`val` 关键字的另一个用法是结合 `member` 关键字来声明一个自动实现的属性。</span><span class="sxs-lookup"><span data-stu-id="0277b-106">Another use of the `val` keyword is in conjunction with the `member` keyword to declare an auto-implemented property.</span></span> <span data-ttu-id="0277b-107">有关自动实现的属性的详细信息，请参阅[属性](properties.md)。</span><span class="sxs-lookup"><span data-stu-id="0277b-107">For more information on auto-implemented properties, see [Properties](properties.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="0277b-108">语法</span><span class="sxs-lookup"><span data-stu-id="0277b-108">Syntax</span></span>

```fsharp
val [ mutable ] [ access-modifier ] field-name : type-name
```

## <a name="remarks"></a><span data-ttu-id="0277b-109">备注</span><span class="sxs-lookup"><span data-stu-id="0277b-109">Remarks</span></span>

<span data-ttu-id="0277b-110">在类或结构类型中定义字段的通常方式是使用 `let` 绑定。</span><span class="sxs-lookup"><span data-stu-id="0277b-110">The usual way to define fields in a class or structure type is to use a `let` binding.</span></span> <span data-ttu-id="0277b-111">但是，`let` 绑定必须初始化为类构造函数的一部分，而这并不总是可能、有必要或必需实现的。</span><span class="sxs-lookup"><span data-stu-id="0277b-111">However, `let` bindings must be initialized as part of the class constructor, which is not always possible, necessary, or desirable.</span></span> <span data-ttu-id="0277b-112">当你需要一个未初始化的字段时，可以使用 `val` 关键。</span><span class="sxs-lookup"><span data-stu-id="0277b-112">You can use the `val` keyword when you want a field that is uninitialized.</span></span>

<span data-ttu-id="0277b-113">显式字段可以为静态或非静态的。</span><span class="sxs-lookup"><span data-stu-id="0277b-113">Explicit fields can be static or non-static.</span></span> <span data-ttu-id="0277b-114">*访问修饰符*可以是`public`， `private`，或`internal`。</span><span class="sxs-lookup"><span data-stu-id="0277b-114">The *access-modifier* can be `public`, `private`, or `internal`.</span></span> <span data-ttu-id="0277b-115">默认情况下，显式字段是公共的。</span><span class="sxs-lookup"><span data-stu-id="0277b-115">By default, explicit fields are public.</span></span> <span data-ttu-id="0277b-116">这不同于类中的 `let` 绑定，后者始终是私有的。</span><span class="sxs-lookup"><span data-stu-id="0277b-116">This differs from `let` bindings in classes, which are always private.</span></span>

<span data-ttu-id="0277b-117">[DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58)需要在具有主构造函数的类类型中的显式字段上设置属性。</span><span class="sxs-lookup"><span data-stu-id="0277b-117">The [DefaultValue](https://msdn.microsoft.com/library/a3a3307b-8c05-441e-b109-245511614d58) attribute is required on explicit fields in class types that have a primary constructor.</span></span> <span data-ttu-id="0277b-118">此特性指定该字段被初始化为零。</span><span class="sxs-lookup"><span data-stu-id="0277b-118">This attribute specifies that the field is initialized to zero.</span></span> <span data-ttu-id="0277b-119">字段的类型必须支持零初始化。</span><span class="sxs-lookup"><span data-stu-id="0277b-119">The type of the field must support zero-initialization.</span></span> <span data-ttu-id="0277b-120">如果一个类型为以下类型之一，则该类型支持零初始化：</span><span class="sxs-lookup"><span data-stu-id="0277b-120">A type supports zero-initialization if it is one of the following:</span></span>

- <span data-ttu-id="0277b-121">具有零值的基元类型。</span><span class="sxs-lookup"><span data-stu-id="0277b-121">A primitive type that has a zero value.</span></span>

- <span data-ttu-id="0277b-122">一种支持 Null 值作为标准值、异常值或值表示形式的类型。</span><span class="sxs-lookup"><span data-stu-id="0277b-122">A type that supports a null value, either as a normal value, as an abnormal value, or as a representation of a value.</span></span> <span data-ttu-id="0277b-123">这包括类、元组、记录、函数、接口、.NET 引用类型、`unit` 类型以及可区分联合类型。</span><span class="sxs-lookup"><span data-stu-id="0277b-123">This includes classes, tuples, records, functions, interfaces, .NET reference types, the `unit` type, and discriminated union types.</span></span>

- <span data-ttu-id="0277b-124">一个 .NET 值类型。</span><span class="sxs-lookup"><span data-stu-id="0277b-124">A .NET value type.</span></span>

- <span data-ttu-id="0277b-125">一种结构，其字段均支持默认值零。</span><span class="sxs-lookup"><span data-stu-id="0277b-125">A structure whose fields all support a default zero value.</span></span>

<span data-ttu-id="0277b-126">例如，称为 `someField` 的不可变字段具有一个 .NET 编译表示形式的支持字段，该字段名为 `someField@`，你可以使用名为 `someField` 的属性访问存储值。</span><span class="sxs-lookup"><span data-stu-id="0277b-126">For example, an immutable field called `someField` has a backing field in the .NET compiled representation with the name `someField@`, and you access the stored value using a property named `someField`.</span></span>

<span data-ttu-id="0277b-127">对于可变字段，.NET 编译的表示形式是一个 .NET 字段。</span><span class="sxs-lookup"><span data-stu-id="0277b-127">For a mutable field, the .NET compiled representation is a .NET field.</span></span>

>[!WARNING]
<span data-ttu-id="0277b-128">`Note` .NET Framework 命名空间`System.ComponentModel`包含具有相同名称的属性。</span><span class="sxs-lookup"><span data-stu-id="0277b-128">`Note` The .NET Framework namespace `System.ComponentModel` contains an attribute that has the same name.</span></span> <span data-ttu-id="0277b-129">有关该属性的信息，请参见 `System.ComponentModel.DefaultValueAttribute`。</span><span class="sxs-lookup"><span data-stu-id="0277b-129">For information about this attribute, see `System.ComponentModel.DefaultValueAttribute`.</span></span>

<span data-ttu-id="0277b-130">以下代码展示了显式字段的用法，作为对比，还展示了具有主构造函数的类中的 `let` 绑定。</span><span class="sxs-lookup"><span data-stu-id="0277b-130">The following code shows the use of explicit fields and, for comparison, a `let` binding in a class that has a primary constructor.</span></span> <span data-ttu-id="0277b-131">注意：与 `let` 字段绑定的 `myInt1` 是私有的。</span><span class="sxs-lookup"><span data-stu-id="0277b-131">Note that the `let`-bound field `myInt1` is private.</span></span> <span data-ttu-id="0277b-132">当从成员方法引用与 `let` 字段绑定的 `myInt1` 时，不需要自我标识符 `this`。</span><span class="sxs-lookup"><span data-stu-id="0277b-132">When the `let`-bound field `myInt1` is referenced from a member method, the self identifier `this` is not required.</span></span> <span data-ttu-id="0277b-133">但如果要引用显式字段 `myInt2` 和 `myString`，则需要自我标识符。</span><span class="sxs-lookup"><span data-stu-id="0277b-133">But when you are referencing the explicit fields `myInt2` and `myString`, the self identifier is required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6701.fs)]

<span data-ttu-id="0277b-134">输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="0277b-134">The output is as follows:</span></span>

```
11 12 abc
30 def
```

<span data-ttu-id="0277b-135">以下代码展示了不具有主构造函数的类中的显式字段的用法。</span><span class="sxs-lookup"><span data-stu-id="0277b-135">The following code shows the use of explicit fields in a class that does not have a primary constructor.</span></span> <span data-ttu-id="0277b-136">在该例中，不需要 `DefaultValue` 特性，但所有字段必须在为该类型定义的构造函数中进行初始化。</span><span class="sxs-lookup"><span data-stu-id="0277b-136">In this case, the `DefaultValue` attribute is not required, but all the fields must be initialized in the constructors that are defined for the type.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6702.fs)]

<span data-ttu-id="0277b-137">输出为 `35 22`。</span><span class="sxs-lookup"><span data-stu-id="0277b-137">The output is `35 22`.</span></span>

<span data-ttu-id="0277b-138">以下代码展示了结构中显式字段的用法。</span><span class="sxs-lookup"><span data-stu-id="0277b-138">The following code shows the use of explicit fields in a structure.</span></span> <span data-ttu-id="0277b-139">由于结构是值类型，它自动具有默认构造函数，该函数将其字段的值设置为零。</span><span class="sxs-lookup"><span data-stu-id="0277b-139">Because a structure is a value type, it automatically has a default constructor that sets the values of its fields to zero.</span></span> <span data-ttu-id="0277b-140">因此，不需要 `DefaultValue` 特性。</span><span class="sxs-lookup"><span data-stu-id="0277b-140">Therefore, the `DefaultValue` attribute is not required.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6703.fs)]

<span data-ttu-id="0277b-141">输出为 `11 xyz`。</span><span class="sxs-lookup"><span data-stu-id="0277b-141">The output is `11 xyz`.</span></span>

<span data-ttu-id="0277b-142">**请注意**，如果要初始化您的结构与`mutable`字段而无需`mutable`关键字，将工作分配给您的结构，它将被放弃之后立即分配的副本上。</span><span class="sxs-lookup"><span data-stu-id="0277b-142">**Beware**, if you are going to initialize your structure with `mutable` fields without `mutable` keyword, your assignments will work on a copy of the structure which will be discarded right after assignment.</span></span> <span data-ttu-id="0277b-143">因此不会更改您的结构。</span><span class="sxs-lookup"><span data-stu-id="0277b-143">Therefore your structure won't change.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet6704.fs)]

<span data-ttu-id="0277b-144">显式字段不适用于例程使用。</span><span class="sxs-lookup"><span data-stu-id="0277b-144">Explicit fields are not intended for routine use.</span></span> <span data-ttu-id="0277b-145">通常，在可能的情况下，应在类中使用 `let` 绑定，而不是显式字段。</span><span class="sxs-lookup"><span data-stu-id="0277b-145">In general, when possible you should use a `let` binding in a class instead of an explicit field.</span></span> <span data-ttu-id="0277b-146">显式字段在某些互操作性方案中十分有用，例如，当需要定义一个结构，该结构将用在对本机 API 的平台调用中，或用在 COM 互操作方案中。</span><span class="sxs-lookup"><span data-stu-id="0277b-146">Explicit fields are useful in certain interoperability scenarios, such as when you need to define a structure that will be used in a platform invoke call to a native API, or in COM interop scenarios.</span></span> <span data-ttu-id="0277b-147">有关详细信息，请参阅[外部函数](../functions/external-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="0277b-147">For more information, see [External Functions](../functions/external-functions.md).</span></span> <span data-ttu-id="0277b-148">另一种要用到显式字段的情况是当使用 F# 代码生成器时，该生成器会发出不具有主构造函数的类。</span><span class="sxs-lookup"><span data-stu-id="0277b-148">Another situation in which an explicit field might be necessary is when you are working with an F# code generator which emits classes without a primary constructor.</span></span> <span data-ttu-id="0277b-149">显式字段对于线程静态变量或类似的构造而言也十分有用。</span><span class="sxs-lookup"><span data-stu-id="0277b-149">Explicit fields are also useful for thread-static variables or similar constructs.</span></span> <span data-ttu-id="0277b-150">有关详细信息，请参阅 `System.ThreadStaticAttribute` 。</span><span class="sxs-lookup"><span data-stu-id="0277b-150">For more information, see `System.ThreadStaticAttribute`.</span></span>

<span data-ttu-id="0277b-151">当关键字 `member val` 在一个类型定义中同时出现，它就是一个自动实现属性的定义。</span><span class="sxs-lookup"><span data-stu-id="0277b-151">When the keywords `member val` appear together in a type definition, it is a definition of an automatically implemented property.</span></span> <span data-ttu-id="0277b-152">有关更多信息，请参见 [属性](properties.md)中定义的接口的私有 C++ 特定实现。</span><span class="sxs-lookup"><span data-stu-id="0277b-152">For more information, see [Properties](properties.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0277b-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="0277b-153">See also</span></span>

- [<span data-ttu-id="0277b-154">属性</span><span class="sxs-lookup"><span data-stu-id="0277b-154">Properties</span></span>](properties.md)
- [<span data-ttu-id="0277b-155">成员</span><span class="sxs-lookup"><span data-stu-id="0277b-155">Members</span></span>](index.md)
- [<span data-ttu-id="0277b-156">类中的 `let` 绑定</span><span class="sxs-lookup"><span data-stu-id="0277b-156">`let` Bindings in Classes</span></span>](let-bindings-in-classes.md)