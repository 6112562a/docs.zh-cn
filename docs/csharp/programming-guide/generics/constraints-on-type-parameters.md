---
title: 类型参数约束 - C# 编程指南
ms.custom: seodec18
ms.date: 04/12/2018
helpviewer_keywords:
- generics [C#], type constraints
- type constraints [C#]
- type parameters [C#], constraints
- unbound type parameter [C#]
ms.openlocfilehash: 44ab9766bead15c97a1397ef1f47de75f72643a3
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423536"
---
# <a name="constraints-on-type-parameters-c-programming-guide"></a><span data-ttu-id="94934-102">类型参数的约束（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="94934-102">Constraints on type parameters (C# Programming Guide)</span></span>

<span data-ttu-id="94934-103">约束告知编译器类型参数必须具备的功能。</span><span class="sxs-lookup"><span data-stu-id="94934-103">Constraints inform the compiler about the capabilities a type argument must have.</span></span> <span data-ttu-id="94934-104">在没有任何约束的情况下，类型参数可以是任何类型。</span><span class="sxs-lookup"><span data-stu-id="94934-104">Without any constraints, the type argument could be any type.</span></span> <span data-ttu-id="94934-105">编译器只能假定 <xref:System.Object?displayProperty=nameWithType> 的成员，它是任何 .NET 类型的最终基类。</span><span class="sxs-lookup"><span data-stu-id="94934-105">The compiler can only assume the members of <xref:System.Object?displayProperty=nameWithType>, which is the ultimate base class for any .NET type.</span></span> <span data-ttu-id="94934-106">有关详细信息，请参阅[使用约束的原因](#why-use-constraints)。</span><span class="sxs-lookup"><span data-stu-id="94934-106">For more information, see [Why use constraints](#why-use-constraints).</span></span> <span data-ttu-id="94934-107">如果客户端代码尝试使用约束所不允许的类型来实例化类，则会产生编译时错误。</span><span class="sxs-lookup"><span data-stu-id="94934-107">If client code tries to instantiate your class by using a type that is not allowed by a constraint, the result is a compile-time error.</span></span> <span data-ttu-id="94934-108">通过使用 `where` 上下文关键字指定约束。</span><span class="sxs-lookup"><span data-stu-id="94934-108">Constraints are specified by using the `where` contextual keyword.</span></span> <span data-ttu-id="94934-109">下表列出了七种类型的约束：</span><span class="sxs-lookup"><span data-stu-id="94934-109">The following table lists the seven types of constraints:</span></span>

|<span data-ttu-id="94934-110">约束</span><span class="sxs-lookup"><span data-stu-id="94934-110">Constraint</span></span>|<span data-ttu-id="94934-111">说明</span><span class="sxs-lookup"><span data-stu-id="94934-111">Description</span></span>|
|----------------|-----------------|
|`where T : struct`|<span data-ttu-id="94934-112">类型参数必须是值类型。</span><span class="sxs-lookup"><span data-stu-id="94934-112">The type argument must be a value type.</span></span> <span data-ttu-id="94934-113">可以指定除 <xref:System.Nullable%601> 以外的任何值类型。</span><span class="sxs-lookup"><span data-stu-id="94934-113">Any value type except <xref:System.Nullable%601> can be specified.</span></span> <span data-ttu-id="94934-114">有关可以为 null 的类型的详细信息，请参阅[可以为 null 的类型](../nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="94934-114">For more information about nullable types, see [Nullable types](../nullable-types/index.md).</span></span>|
|`where T : class`|<span data-ttu-id="94934-115">类型参数必须是引用类型。</span><span class="sxs-lookup"><span data-stu-id="94934-115">The type argument must be a reference type.</span></span> <span data-ttu-id="94934-116">此约束还应用于任何类、接口、委托或数组类型。</span><span class="sxs-lookup"><span data-stu-id="94934-116">This constraint applies also to any class, interface, delegate, or array type.</span></span>|
|`where T : unmanaged`|<span data-ttu-id="94934-117">类型参数不能是引用类型，并且任何嵌套级别均不能包含任何引用类型成员。</span><span class="sxs-lookup"><span data-stu-id="94934-117">The type argument must not be a reference type and must not contain any reference type members at any level of nesting.</span></span>|
|`where T : new()`|<span data-ttu-id="94934-118">类型参数必须具有公共无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="94934-118">The type argument must have a public parameterless constructor.</span></span> <span data-ttu-id="94934-119">与其他约束一起使用时，`new()` 约束必须最后指定。</span><span class="sxs-lookup"><span data-stu-id="94934-119">When used together with other constraints, the `new()` constraint must be specified last.</span></span>|
|<span data-ttu-id="94934-120">`where T :` \<基类名> </span><span class="sxs-lookup"><span data-stu-id="94934-120">`where T :` *\<base class name>*</span></span>|<span data-ttu-id="94934-121">类型参数必须是指定的基类或派生自指定的基类。</span><span class="sxs-lookup"><span data-stu-id="94934-121">The type argument must be or derive from the specified base class.</span></span>|
|<span data-ttu-id="94934-122">`where T :` \<接口名称> </span><span class="sxs-lookup"><span data-stu-id="94934-122">`where T :` *\<interface name>*</span></span>|<span data-ttu-id="94934-123">类型参数必须是指定的接口或实现指定的接口。</span><span class="sxs-lookup"><span data-stu-id="94934-123">The type argument must be or implement the specified interface.</span></span> <span data-ttu-id="94934-124">可指定多个接口约束。</span><span class="sxs-lookup"><span data-stu-id="94934-124">Multiple interface constraints can be specified.</span></span> <span data-ttu-id="94934-125">约束接口也可以是泛型。</span><span class="sxs-lookup"><span data-stu-id="94934-125">The constraining interface can also be generic.</span></span>|
|`where T : U`|<span data-ttu-id="94934-126">为 T 提供的类型参数必须是为 U 提供的参数或派生自为 U 提供的参数。</span><span class="sxs-lookup"><span data-stu-id="94934-126">The type argument supplied for T must be or derive from the argument supplied for U.</span></span>|

<span data-ttu-id="94934-127">某些约束是互斥的。</span><span class="sxs-lookup"><span data-stu-id="94934-127">Some of the constraints are mutually exclusive.</span></span> <span data-ttu-id="94934-128">所有值类型必须具有可访问的无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="94934-128">All value types must have an accessible parameterless constructor.</span></span> <span data-ttu-id="94934-129">`struct` 约束包含 `new()` 约束，且 `new()` 约束不能与 `struct` 约束结合使用。</span><span class="sxs-lookup"><span data-stu-id="94934-129">The `struct` constraint implies the `new()` constraint and the `new()` constraint cannot be combined with the `struct` constraint.</span></span> <span data-ttu-id="94934-130">`unmanaged` 约束包含 `struct` 约束。</span><span class="sxs-lookup"><span data-stu-id="94934-130">The `unmanaged` constraint implies the `struct` constraint.</span></span> <span data-ttu-id="94934-131">`unmanaged` 约束不能与 `struct` 或 `new()` 约束结合使用。</span><span class="sxs-lookup"><span data-stu-id="94934-131">The `unmanaged` constraint cannot be combined with either the `struct` or `new()` constraints.</span></span>

## <a name="why-use-constraints"></a><span data-ttu-id="94934-132">使用约束的原因</span><span class="sxs-lookup"><span data-stu-id="94934-132">Why use constraints</span></span>

<span data-ttu-id="94934-133">通过约束类型参数，可以增加约束类型及其继承层次结构中的所有类型所支持的允许操作和方法调用的数量。</span><span class="sxs-lookup"><span data-stu-id="94934-133">By constraining the type parameter, you increase the number of allowable operations and method calls to those supported by the constraining type and all types in its inheritance hierarchy.</span></span> <span data-ttu-id="94934-134">设计泛型类或方法时，如果要对泛型成员执行除简单赋值之外的任何操作或调用 <xref:System.Object?displayProperty=nameWithType> 不支持的任何方法，则必须对该类型参数应用约束。</span><span class="sxs-lookup"><span data-stu-id="94934-134">When you design generic classes or methods, if you will be performing any operation on the generic members beyond simple assignment or calling any methods not supported by <xref:System.Object?displayProperty=nameWithType>, you will have to apply constraints to the type parameter.</span></span> <span data-ttu-id="94934-135">例如，基类约束告诉编译器，仅此类型的对象或派生自此类型的对象可用作类型参数。</span><span class="sxs-lookup"><span data-stu-id="94934-135">For example, the base class constraint tells the compiler that only objects of this type or derived from this type will be used as type arguments.</span></span> <span data-ttu-id="94934-136">编译器有了此保证后，就能够允许在泛型类中调用该类型的方法。</span><span class="sxs-lookup"><span data-stu-id="94934-136">Once the compiler has this guarantee, it can allow methods of that type to be called in the generic class.</span></span> <span data-ttu-id="94934-137">以下代码示例演示可通过应用基类约束添加到（[泛型介绍](introduction-to-generics.md)中的）`GenericList<T>` 类的功能。</span><span class="sxs-lookup"><span data-stu-id="94934-137">The following code example demonstrates the functionality you can add to the `GenericList<T>` class (in [Introduction to Generics](introduction-to-generics.md)) by applying a base class constraint.</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#9)]

<span data-ttu-id="94934-138">约束使泛型类能够使用 `Employee.Name` 属性。</span><span class="sxs-lookup"><span data-stu-id="94934-138">The constraint enables the generic class to use the `Employee.Name` property.</span></span> <span data-ttu-id="94934-139">约束指定类型 `T` 的所有项都保证是 `Employee` 对象或从 `Employee` 继承的对象。</span><span class="sxs-lookup"><span data-stu-id="94934-139">The constraint specifies that all items of type `T` are guaranteed to be either an `Employee` object or an object that inherits from `Employee`.</span></span>

<span data-ttu-id="94934-140">可以对同一类型参数应用多个约束，并且约束自身可以是泛型类型，如下所示：</span><span class="sxs-lookup"><span data-stu-id="94934-140">Multiple constraints can be applied to the same type parameter, and the constraints themselves can be generic types, as follows:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#10)]

<span data-ttu-id="94934-141">在应用 `where T : class` 约束时，请避免对类型参数使用 `==` 和 `!=` 运算符，因为这些运算符仅测试引用标识而不测试值相等性。</span><span class="sxs-lookup"><span data-stu-id="94934-141">When applying the `where T : class` constraint, avoid the `==` and `!=` operators on the type parameter because these operators will test for reference identity only, not for value equality.</span></span> <span data-ttu-id="94934-142">即使在用作参数的类型中重载这些运算符也会发生此行为。</span><span class="sxs-lookup"><span data-stu-id="94934-142">This behavior occurs even if these operators are overloaded in a type that is used as an argument.</span></span> <span data-ttu-id="94934-143">下面的代码说明了这一点；即使 <xref:System.String> 类重载 `==` 运算符，输出也为 false。</span><span class="sxs-lookup"><span data-stu-id="94934-143">The following code illustrates this point; the output is false even though the <xref:System.String> class overloads the `==` operator.</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#11)]

<span data-ttu-id="94934-144">编译器只知道 T 在编译时是引用类型，并且必须使用对所有引用类型都有效的默认运算符。</span><span class="sxs-lookup"><span data-stu-id="94934-144">The compiler only knows that T is a reference type at compile time and must use the default operators that are valid for all reference types.</span></span> <span data-ttu-id="94934-145">如果必须测试值相等性，建议同时应用 `where T : IEquatable<T>` 或 `where T : IComparable<T>` 约束，并在用于构造泛型类的任何类中实现该接口。</span><span class="sxs-lookup"><span data-stu-id="94934-145">If you must test for value equality, the recommended way is to also apply the `where T : IEquatable<T>` or `where T : IComparable<T>` constraint and implement the interface in any class that will be used to construct the generic class.</span></span>

## <a name="constraining-multiple-parameters"></a><span data-ttu-id="94934-146">约束多个参数</span><span class="sxs-lookup"><span data-stu-id="94934-146">Constraining multiple parameters</span></span>

<span data-ttu-id="94934-147">可以对多个参数应用多个约束，对一个参数应用多个约束，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="94934-147">You can apply constraints to multiple parameters, and multiple constraints to a single parameter, as shown in the following example:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#12)]

## <a name="unbounded-type-parameters"></a><span data-ttu-id="94934-148">未绑定的类型参数</span><span class="sxs-lookup"><span data-stu-id="94934-148">Unbounded type parameters</span></span>

 <span data-ttu-id="94934-149">没有约束的类型参数（如公共类 `SampleClass<T>{}` 中的 T）称为未绑定的类型参数。</span><span class="sxs-lookup"><span data-stu-id="94934-149">Type parameters that have no constraints, such as T in public class `SampleClass<T>{}`, are called unbounded type parameters.</span></span> <span data-ttu-id="94934-150">未绑定的类型参数具有以下规则：</span><span class="sxs-lookup"><span data-stu-id="94934-150">Unbounded type parameters have the following rules:</span></span>

- <span data-ttu-id="94934-151">不能使用 `!=` 和 `==` 运算符，因为无法保证具体的类型参数能支持这些运算符。</span><span class="sxs-lookup"><span data-stu-id="94934-151">The `!=` and `==` operators cannot be used because there is no guarantee that the concrete type argument will support these operators.</span></span>
- <span data-ttu-id="94934-152">可以在它们与 `System.Object` 之间来回转换，或将它们显式转换为任何接口类型。</span><span class="sxs-lookup"><span data-stu-id="94934-152">They can be converted to and from `System.Object` or explicitly converted to any interface type.</span></span>
- <span data-ttu-id="94934-153">可以将它们与 [null](../../language-reference/keywords/null.md) 进行比较。</span><span class="sxs-lookup"><span data-stu-id="94934-153">You can compare them to [null](../../language-reference/keywords/null.md).</span></span> <span data-ttu-id="94934-154">将未绑定的参数与 `null` 进行比较时，如果类型参数为值类型，则该比较将始终返回 false。</span><span class="sxs-lookup"><span data-stu-id="94934-154">If an unbounded parameter is compared to `null`, the comparison will always return false if the type argument is a value type.</span></span>

## <a name="type-parameters-as-constraints"></a><span data-ttu-id="94934-155">类型参数作为约束</span><span class="sxs-lookup"><span data-stu-id="94934-155">Type parameters as constraints</span></span>

<span data-ttu-id="94934-156">在具有自己类型参数的成员函数必须将该参数约束为包含类型的类型参数时，将泛型类型参数用作约束非常有用，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="94934-156">The use of a generic type parameter as a constraint is useful when a member function with its own type parameter has to constrain that parameter to the type parameter of the containing type, as shown in the following example:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#13)]

<span data-ttu-id="94934-157">在上述示例中，`T` 在 `Add` 方法的上下文中是一个类型约束，而在 `List` 类的上下文中是一个未绑定的类型参数。</span><span class="sxs-lookup"><span data-stu-id="94934-157">In the previous example, `T` is a type constraint in the context of the `Add` method, and an unbounded type parameter in the context of the `List` class.</span></span>

<span data-ttu-id="94934-158">类型参数还可在泛型类定义中用作约束。</span><span class="sxs-lookup"><span data-stu-id="94934-158">Type parameters can also be used as constraints in generic class definitions.</span></span> <span data-ttu-id="94934-159">必须在尖括号中声明该类型参数以及任何其他类型参数：</span><span class="sxs-lookup"><span data-stu-id="94934-159">The type parameter must be declared within the angle brackets together with any other type parameters:</span></span>

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#14)]

<span data-ttu-id="94934-160">类型参数作为泛型类的约束的作用非常有限，因为编译器除了假设类型参数派生自 `System.Object` 以外，不会做其他任何假设。</span><span class="sxs-lookup"><span data-stu-id="94934-160">The usefulness of type parameters as constraints with generic classes is limited because the compiler can assume nothing about the type parameter except that it derives from `System.Object`.</span></span> <span data-ttu-id="94934-161">如果要在两个类型参数之间强制继承关系，可以将类型参数用作泛型类的约束。</span><span class="sxs-lookup"><span data-stu-id="94934-161">Use type parameters as constraints on generic classes in scenarios in which you want to enforce an inheritance relationship between two type parameters.</span></span>

## <a name="unmanaged-constraint"></a><span data-ttu-id="94934-162">非托管约束</span><span class="sxs-lookup"><span data-stu-id="94934-162">Unmanaged constraint</span></span>

<span data-ttu-id="94934-163">从 C# 7.3 开始，可使用 `unmanaged` 约束来指定类型参数必须为“非托管类型”  。</span><span class="sxs-lookup"><span data-stu-id="94934-163">Beginning with C# 7.3, you can use the `unmanaged` constraint to specify that the type parameter must be an **unmanaged type**.</span></span> <span data-ttu-id="94934-164">“非托管类型”不是引用类型，且任何嵌套级别都不包含引用类型字段  。</span><span class="sxs-lookup"><span data-stu-id="94934-164">An **unmanaged type** is a type that is not a reference type and doesn't contain reference type fields at any level of nesting.</span></span> <span data-ttu-id="94934-165">通过 `unmanaged` 约束，用户能编写可重用例程，从而使用可作为内存块操作的类型，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="94934-165">The `unmanaged` constraint enables you to write reusable routines to work with types that can be manipulated as blocks of memory, as shown in the following example:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#15)]

<span data-ttu-id="94934-166">以上方法必须在 `unsafe` 上下文中编译，因为它并不是在已知的内置类型上使用 `sizeof` 运算符。</span><span class="sxs-lookup"><span data-stu-id="94934-166">The preceding method must be compiled in an `unsafe` context because it uses the `sizeof` operator on a type not known to be a built-in type.</span></span> <span data-ttu-id="94934-167">如果没有 `unmanaged` 约束，则 `sizeof` 运算符不可用。</span><span class="sxs-lookup"><span data-stu-id="94934-167">Without the `unmanaged` constraint, the `sizeof` operator is unavailable.</span></span>

## <a name="delegate-constraints"></a><span data-ttu-id="94934-168">委托约束</span><span class="sxs-lookup"><span data-stu-id="94934-168">Delegate constraints</span></span>

<span data-ttu-id="94934-169">同样从 C# 7.3 开始，可将 <xref:System.Delegate?displayProperty=nameWithType> 或 <xref:System.MulticastDelegate?displayProperty=nameWithType> 用作基类约束。</span><span class="sxs-lookup"><span data-stu-id="94934-169">Also beginning with C# 7.3, you can use <xref:System.Delegate?displayProperty=nameWithType> or <xref:System.MulticastDelegate?displayProperty=nameWithType> as a base class constraint.</span></span> <span data-ttu-id="94934-170">CLR 始终允许此约束，但 C# 语言不允许。</span><span class="sxs-lookup"><span data-stu-id="94934-170">The CLR always allowed this constraint, but the C# language disallowed it.</span></span> <span data-ttu-id="94934-171">使用 `System.Delegate` 约束，用户能够以类型安全的方式编写使用委托的代码。</span><span class="sxs-lookup"><span data-stu-id="94934-171">The `System.Delegate` constraint enables you to write code that works with delegates in a type-safe manner.</span></span> <span data-ttu-id="94934-172">以下代码定义了合并两个同类型委托的扩展方法：</span><span class="sxs-lookup"><span data-stu-id="94934-172">The following code defines an extension method that combines two delegates provided they are the same type:</span></span>

[!code-csharp[using the delegate constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#16)]

<span data-ttu-id="94934-173">可使用上述方法来合并相同类型的委托：</span><span class="sxs-lookup"><span data-stu-id="94934-173">You can use the above method to combine delegates that are the same type:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#17)]

<span data-ttu-id="94934-174">如果取消评论最后一行，它将不会编译。</span><span class="sxs-lookup"><span data-stu-id="94934-174">If you uncomment the last line, it won't compile.</span></span> <span data-ttu-id="94934-175">`first` 和 `test` 均为委托类型，但它们是不同的委托类型。</span><span class="sxs-lookup"><span data-stu-id="94934-175">Both `first` and `test` are delegate types, but they are different delegate types.</span></span>

## <a name="enum-constraints"></a><span data-ttu-id="94934-176">枚举约束</span><span class="sxs-lookup"><span data-stu-id="94934-176">Enum constraints</span></span>

<span data-ttu-id="94934-177">从 C# 7.3 开始，还可指定 <xref:System.Enum?displayProperty=nameWithType> 类型作为基类约束。</span><span class="sxs-lookup"><span data-stu-id="94934-177">Beginning in C# 7.3, you can also specify the <xref:System.Enum?displayProperty=nameWithType> type as a base class constraint.</span></span> <span data-ttu-id="94934-178">CLR 始终允许此约束，但 C# 语言不允许。</span><span class="sxs-lookup"><span data-stu-id="94934-178">The CLR always allowed this constraint, but the C# language disallowed it.</span></span> <span data-ttu-id="94934-179">使用 `System.Enum` 的泛型提供类型安全的编程，缓存使用 `System.Enum` 中静态方法的结果。</span><span class="sxs-lookup"><span data-stu-id="94934-179">Generics using `System.Enum` provide type-safe programming to cache results from using the static methods in `System.Enum`.</span></span> <span data-ttu-id="94934-180">以下示例查找枚举类型的所有有效的值，然后生成将这些值映射到其字符串表示形式的字典。</span><span class="sxs-lookup"><span data-stu-id="94934-180">The following sample finds all the valid values for an enum type, and then builds a dictionary that maps those values to its string representation.</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#18)]

<span data-ttu-id="94934-181">所用方法利用反射，这会对性能产生影响。</span><span class="sxs-lookup"><span data-stu-id="94934-181">The methods used make use of reflection, which has performance implications.</span></span> <span data-ttu-id="94934-182">可调用此方法来生成可缓存和重用的集合，而不是重复需要反射才能实施的调用。</span><span class="sxs-lookup"><span data-stu-id="94934-182">You can call this method to build a collection that is cached and reused rather than repeating the calls that require reflection.</span></span>

<span data-ttu-id="94934-183">如以下示例所示，可使用它来创建枚举并生成其值和名称的字典：</span><span class="sxs-lookup"><span data-stu-id="94934-183">You could use it as shown in the following sample to create an enum and build a dictionary of its values and names:</span></span>

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#19)]

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#20)]

## <a name="see-also"></a><span data-ttu-id="94934-184">请参阅</span><span class="sxs-lookup"><span data-stu-id="94934-184">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="94934-185">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="94934-185">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="94934-186">泛型介绍</span><span class="sxs-lookup"><span data-stu-id="94934-186">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="94934-187">泛型类</span><span class="sxs-lookup"><span data-stu-id="94934-187">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)
- [<span data-ttu-id="94934-188">new 约束</span><span class="sxs-lookup"><span data-stu-id="94934-188">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)
