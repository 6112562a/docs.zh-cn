---
title: 结构 - C# 指南
description: 了解结构类型及其创建方式
ms.date: 10/12/2016
ms.technology: csharp-fundamentals
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 10971dc1a0b2c9d64ac8766734b3f6f630aa3ccf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423114"
---
# <a name="structs"></a><span data-ttu-id="2ac74-103">结构</span><span class="sxs-lookup"><span data-stu-id="2ac74-103">Structs</span></span>

<span data-ttu-id="2ac74-104">结构  是一个值类型。</span><span class="sxs-lookup"><span data-stu-id="2ac74-104">A *struct* is a value type.</span></span> <span data-ttu-id="2ac74-105">创建结构时，分配给结构的变量保留结构的实际数据。</span><span class="sxs-lookup"><span data-stu-id="2ac74-105">When a struct is created, the variable to which the struct is assigned holds the struct's actual data.</span></span> <span data-ttu-id="2ac74-106">将结构分配给新变量时，会复制结构。</span><span class="sxs-lookup"><span data-stu-id="2ac74-106">When the struct is assigned to a new variable, it is copied.</span></span> <span data-ttu-id="2ac74-107">因此，新变量和原始变量包含相同数据的副本（共两个）。</span><span class="sxs-lookup"><span data-stu-id="2ac74-107">The new variable and the original variable therefore contain two separate copies of the same data.</span></span> <span data-ttu-id="2ac74-108">对一个副本所做的更改不会影响另一个副本。</span><span class="sxs-lookup"><span data-stu-id="2ac74-108">Changes made to one copy do not affect the other copy.</span></span>

<span data-ttu-id="2ac74-109">值类型变量直接包含它们的值，这意味着在声明变量的任何上下文中内联分配内存。</span><span class="sxs-lookup"><span data-stu-id="2ac74-109">Value type variables directly contain their values, which means that the memory is allocated inline in whatever context the variable is declared.</span></span> <span data-ttu-id="2ac74-110">对于值类型变量，没有单独的堆分配或垃圾回收开销。</span><span class="sxs-lookup"><span data-stu-id="2ac74-110">There is no separate heap allocation or garbage collection overhead for value-type variables.</span></span>  
  
<span data-ttu-id="2ac74-111">值类型分为两类：[结构](./language-reference/keywords/struct.md)和[枚举](./language-reference/keywords/enum.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac74-111">There are two categories of value types: [struct](./language-reference/keywords/struct.md) and [enum](./language-reference/keywords/enum.md).</span></span>  
  
<span data-ttu-id="2ac74-112">内置数值类型是结构，包含可以访问的属性和方法：</span><span class="sxs-lookup"><span data-stu-id="2ac74-112">The built-in numeric types are structs, and they have properties and methods that you can access:</span></span>  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
<span data-ttu-id="2ac74-113">不过，可以声明数值类型并向其赋值，就像它们是简单的非聚合类型一样：</span><span class="sxs-lookup"><span data-stu-id="2ac74-113">But you declare and assign values to them as if they were simple non-aggregate types:</span></span>  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
<span data-ttu-id="2ac74-114">例如，值类型为“密封”  ，这意味着不能从 <xref:System.Int32> 派生类型，并且不能将结构定义为从任何用户定义的类或结构继承，因为结构只能从 <xref:System.ValueType> 继承。</span><span class="sxs-lookup"><span data-stu-id="2ac74-114">Value types are *sealed*, which means, for example, that you cannot derive a type from <xref:System.Int32>, and you cannot define a struct to inherit from any user-defined class or struct because a struct can only inherit from <xref:System.ValueType>.</span></span> <span data-ttu-id="2ac74-115">但是，一个结构可以实现一个或多个接口。</span><span class="sxs-lookup"><span data-stu-id="2ac74-115">However, a struct can implement one or more interfaces.</span></span> <span data-ttu-id="2ac74-116">可将结构类型强制转换为接口类型；这将导致“装箱”  操作，以将结构包装在托管堆上的引用类型对象内。</span><span class="sxs-lookup"><span data-stu-id="2ac74-116">You can cast a struct type to an interface type; this causes a *boxing* operation to wrap the struct inside a reference type object on the managed heap.</span></span> <span data-ttu-id="2ac74-117">当将值类型传递到接受 <xref:System.Object> 作为输入参数的方法时，将发生装箱操作。</span><span class="sxs-lookup"><span data-stu-id="2ac74-117">Boxing operations occur when you pass a value type to a method that takes an <xref:System.Object> as an input parameter.</span></span> <span data-ttu-id="2ac74-118">有关详细信息，请参阅[装箱和取消装箱](./programming-guide/types/boxing-and-unboxing.md )。</span><span class="sxs-lookup"><span data-stu-id="2ac74-118">For more information, see [Boxing and Unboxing](./programming-guide/types/boxing-and-unboxing.md ).</span></span>  
  
<span data-ttu-id="2ac74-119">使用 [struct](./language-reference/keywords/struct.md) 关键字可以创建你自己的自定义值类型。</span><span class="sxs-lookup"><span data-stu-id="2ac74-119">You use the [struct](./language-reference/keywords/struct.md) keyword to create your own custom value types.</span></span> <span data-ttu-id="2ac74-120">结构通常用作一小组相关变量的容器，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="2ac74-120">Typically, a struct is used as a container for a small set of related variables, as shown in the following example:</span></span>  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
<span data-ttu-id="2ac74-121">有关 .NET Framework 中的值类型的详细信息，请参阅[通用类型系统](../standard/common-type-system.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac74-121">For more information about value types in the .NET Framework, see [Common Type System](../standard/common-type-system.md).</span></span>  
    
<span data-ttu-id="2ac74-122">结构与类具有许多相同的语法，但结构比类受到的限制更多：</span><span class="sxs-lookup"><span data-stu-id="2ac74-122">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
- <span data-ttu-id="2ac74-123">在结构声明中，除非将字段声明为 `const` 或 `static`，否则无法初始化。</span><span class="sxs-lookup"><span data-stu-id="2ac74-123">Within a struct declaration, fields cannot be initialized unless they are declared as `const` or `static`.</span></span>  
  
- <span data-ttu-id="2ac74-124">结构不能声明无参数构造函数（没有参数的构造函数）或终结器。</span><span class="sxs-lookup"><span data-stu-id="2ac74-124">A struct cannot declare a parameterless constructor (a constructor without parameters) or a finalizer.</span></span>  
  
- <span data-ttu-id="2ac74-125">结构在分配时进行复制。</span><span class="sxs-lookup"><span data-stu-id="2ac74-125">Structs are copied on assignment.</span></span> <span data-ttu-id="2ac74-126">将结构分配给新变量时，将复制所有数据，并且对新副本所做的任何修改不会更改原始副本的数据。</span><span class="sxs-lookup"><span data-stu-id="2ac74-126">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="2ac74-127">使用值类型的集合（如 Dictionary<string, myStruct>）时，请务必记住这一点。</span><span class="sxs-lookup"><span data-stu-id="2ac74-127">This is important to remember when working with collections of value types such as Dictionary<string, myStruct>.</span></span>  
  
- <span data-ttu-id="2ac74-128">结构是值类型，而类是引用类型。</span><span class="sxs-lookup"><span data-stu-id="2ac74-128">Structs are value types and classes are reference types.</span></span>  
  
- <span data-ttu-id="2ac74-129">与类不同，无需使用 `new` 运算符即可对结构进行实例化。</span><span class="sxs-lookup"><span data-stu-id="2ac74-129">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
- <span data-ttu-id="2ac74-130">结构可以声明具有参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="2ac74-130">Structs can declare constructors that have parameters.</span></span>  
  
- <span data-ttu-id="2ac74-131">一个结构无法继承自另一个结构或类，并且它不能为类的基类。</span><span class="sxs-lookup"><span data-stu-id="2ac74-131">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="2ac74-132">所有结构都直接继承自 <xref:System.ValueType>，后者继承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="2ac74-132">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
  
- <span data-ttu-id="2ac74-133">结构可以实现接口。</span><span class="sxs-lookup"><span data-stu-id="2ac74-133">A struct can implement interfaces.</span></span>

## <a name="literal-values"></a><span data-ttu-id="2ac74-134">文本值</span><span class="sxs-lookup"><span data-stu-id="2ac74-134">Literal values</span></span>

<span data-ttu-id="2ac74-135">在 C# 中，文本值从编译器接收类型。</span><span class="sxs-lookup"><span data-stu-id="2ac74-135">In C#, literal values receive a type from the compiler.</span></span> <span data-ttu-id="2ac74-136">可以通过在数字末尾追加一个字母来指定数字文本应采用的类型。</span><span class="sxs-lookup"><span data-stu-id="2ac74-136">You can specify how a numeric literal should be typed by appending a letter to the end of the number.</span></span> <span data-ttu-id="2ac74-137">例如，若要指定应按浮点数来处理值 4.56，则在该数字后追加一个“f”或“F”：`4.56f`。</span><span class="sxs-lookup"><span data-stu-id="2ac74-137">For example, to specify that the value 4.56 should be treated as a float, append an "f" or "F" after the number: `4.56f`.</span></span> <span data-ttu-id="2ac74-138">如果没有追加字母，编译器将推断该文本的 `double` 类型。</span><span class="sxs-lookup"><span data-stu-id="2ac74-138">If no letter is appended, the compiler will infer the `double` type for the literal.</span></span> <span data-ttu-id="2ac74-139">若要详细了解可以使用字母后缀指定哪些类型，请参阅[值类型](./language-reference/keywords/value-types.md)中的各个类型参考页。</span><span class="sxs-lookup"><span data-stu-id="2ac74-139">For more information about which types can be specified with letter suffixes, see the reference pages for individual types in [Value Types](./language-reference/keywords/value-types.md).</span></span>  
  
<span data-ttu-id="2ac74-140">由于文本已类型化，且所有类型最终都是从 <xref:System.Object> 派生，因此可以编写和编译如下所示的代码：</span><span class="sxs-lookup"><span data-stu-id="2ac74-140">Because literals are typed, and all types derive ultimately from <xref:System.Object>, you can write and compile code such as the following:</span></span>  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

<span data-ttu-id="2ac74-141">最后两个示例演示 C# 7.0 中引入的语言功能。</span><span class="sxs-lookup"><span data-stu-id="2ac74-141">The last two examples demonstrate language features introduced in C# 7.0.</span></span> <span data-ttu-id="2ac74-142">第一个示例演示可使用下划线字符作为数值文本内的数字分隔符  。</span><span class="sxs-lookup"><span data-stu-id="2ac74-142">The first allows you to use an underscore character as a *digit separator* inside numeric literals.</span></span> <span data-ttu-id="2ac74-143">可将它们放在数字中的任意位置，从而提高可读性。</span><span class="sxs-lookup"><span data-stu-id="2ac74-143">You can put them wherever you want between digits to improve readability.</span></span> <span data-ttu-id="2ac74-144">不会对值产生影响。</span><span class="sxs-lookup"><span data-stu-id="2ac74-144">They have no effect on the value.</span></span>

<span data-ttu-id="2ac74-145">第二个示例演示二进制文本  ，使用二进制文本可直接指定位模式，无需使用十六进制表示法。</span><span class="sxs-lookup"><span data-stu-id="2ac74-145">The second demonstrates *binary literals*, which allow you to specify bit patterns directly instead of using hexadecimal notation.</span></span>

## <a name="nullable-value-types"></a><span data-ttu-id="2ac74-146">可以为 null 的值类型</span><span class="sxs-lookup"><span data-stu-id="2ac74-146">Nullable value types</span></span>

<span data-ttu-id="2ac74-147">普通值类型不能具有 [null](language-reference/keywords/null.md) 值。</span><span class="sxs-lookup"><span data-stu-id="2ac74-147">Ordinary value types cannot have a value of [null](language-reference/keywords/null.md).</span></span> <span data-ttu-id="2ac74-148">不过，可以在类型后面附加 `?`，创建可以为 null 的值类型。</span><span class="sxs-lookup"><span data-stu-id="2ac74-148">However, you can create nullable value types by affixing a `?` after the type.</span></span> <span data-ttu-id="2ac74-149">例如，`int?` 是还可以包含值 [null](./language-reference/keywords/null.md) 的 `int` 类型。</span><span class="sxs-lookup"><span data-stu-id="2ac74-149">For example, `int?` is an `int` type that can also have the value [null](./language-reference/keywords/null.md).</span></span> <span data-ttu-id="2ac74-150">可以为 null 的值类型是泛型结构类型 <xref:System.Nullable%601> 的实例。</span><span class="sxs-lookup"><span data-stu-id="2ac74-150">Nullable value types are instances of the generic struct type <xref:System.Nullable%601>.</span></span> <span data-ttu-id="2ac74-151">在将数据传入和传出数据库（数值可能为 NULL 或未定义）时，可为空的值类型特别有用。</span><span class="sxs-lookup"><span data-stu-id="2ac74-151">Nullable value types are especially useful when you are passing data to and from databases in which numeric values might be null or undefined.</span></span> <span data-ttu-id="2ac74-152">有关详细信息，请参阅[可以为 null 的值类型](programming-guide/nullable-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2ac74-152">For more information, see [Nullable value types](programming-guide/nullable-types/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2ac74-153">请参阅</span><span class="sxs-lookup"><span data-stu-id="2ac74-153">See also</span></span>

- [<span data-ttu-id="2ac74-154">类</span><span class="sxs-lookup"><span data-stu-id="2ac74-154">Classes</span></span>](programming-guide/classes-and-structs/classes.md)
- [<span data-ttu-id="2ac74-155">基本类型</span><span class="sxs-lookup"><span data-stu-id="2ac74-155">Basic Types</span></span>](basic-types.md)
