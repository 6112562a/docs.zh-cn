---
title: C# 6 中的新增功能 - C# 指南
description: 了解 C# 版本 6 中的新增功能
ms.date: 09/22/2016
ms.assetid: 4d879f69-f889-4d3f-a781-75194e143400
ms.openlocfilehash: 6aa070d54bb1b571d4fa51538b0521a554073cbc
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146734"
---
# <a name="whats-new-in-c-6"></a><span data-ttu-id="cfa34-103">C# 6 中的新增功能</span><span class="sxs-lookup"><span data-stu-id="cfa34-103">What's New in C# 6</span></span>

<span data-ttu-id="cfa34-104">C# 6.0 版本包含许多可提高开发人员工作效率的功能。</span><span class="sxs-lookup"><span data-stu-id="cfa34-104">The 6.0 release of C# contained many features that improve productivity for developers.</span></span> <span data-ttu-id="cfa34-105">此版本中的功能包括：</span><span class="sxs-lookup"><span data-stu-id="cfa34-105">Features in this release include:</span></span>

* <span data-ttu-id="cfa34-106">[只读自动属性](#read-only-auto-properties)：</span><span class="sxs-lookup"><span data-stu-id="cfa34-106">[Read-only auto-properties](#read-only-auto-properties):</span></span>
    - <span data-ttu-id="cfa34-107">可以创建只能在构造函数中设置的只读自动属性。</span><span class="sxs-lookup"><span data-stu-id="cfa34-107">You can create read-only auto-properties that can be set only in constructors.</span></span>
* <span data-ttu-id="cfa34-108">[自动属性初始化表达式](#auto-property-initializers)：</span><span class="sxs-lookup"><span data-stu-id="cfa34-108">[Auto-property initializers](#auto-property-initializers):</span></span>
    - <span data-ttu-id="cfa34-109">可以编写初始化表达式来设置自动属性的初始值。</span><span class="sxs-lookup"><span data-stu-id="cfa34-109">You can write initialization expressions to set the initial value of an auto-property.</span></span>
* <span data-ttu-id="cfa34-110">[Expression-bodied 函数成员](#expression-bodied-function-members)：</span><span class="sxs-lookup"><span data-stu-id="cfa34-110">[Expression-bodied function members](#expression-bodied-function-members):</span></span>
    - <span data-ttu-id="cfa34-111">可以使用 lambda 表达式创建单行方法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-111">You can author one-line methods using lambda expressions.</span></span>
* <span data-ttu-id="cfa34-112">[using static](#using-static)：</span><span class="sxs-lookup"><span data-stu-id="cfa34-112">[using static](#using-static):</span></span>
    - <span data-ttu-id="cfa34-113">可以将单个类的所有方法导入当前命名空间。</span><span class="sxs-lookup"><span data-stu-id="cfa34-113">You can import all the methods of a single class into the current namespace.</span></span>
* <span data-ttu-id="cfa34-114">[NULL 条件运算符](#null-conditional-operators)：</span><span class="sxs-lookup"><span data-stu-id="cfa34-114">[Null-conditional operators](#null-conditional-operators):</span></span>
    - <span data-ttu-id="cfa34-115">可以简洁、安全地访问对象的成员，同时仍能使用 null 条件运算符检查 null。</span><span class="sxs-lookup"><span data-stu-id="cfa34-115">You can concisely and safely access members of an object while still checking for null with the null conditional operator.</span></span>
* <span data-ttu-id="cfa34-116">[字符串内插](#string-interpolation)：</span><span class="sxs-lookup"><span data-stu-id="cfa34-116">[String interpolation](#string-interpolation):</span></span>
    - <span data-ttu-id="cfa34-117">可以使用内联表达式（而不是位置参数）编写字符串格式设置表达式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-117">You can write string formatting expressions using inline expressions instead of positional arguments.</span></span>
* <span data-ttu-id="cfa34-118">[异常筛选器](#exception-filters)：</span><span class="sxs-lookup"><span data-stu-id="cfa34-118">[Exception filters](#exception-filters):</span></span>
    - <span data-ttu-id="cfa34-119">可以基于异常或其他程序状态的属性捕获表达式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-119">You can catch expressions based on properties of the exception or other program state.</span></span> 
* <span data-ttu-id="cfa34-120">[`nameof` 表达式](#the-nameof-expression)：</span><span class="sxs-lookup"><span data-stu-id="cfa34-120">[The `nameof` expression](#the-nameof-expression):</span></span>
    - <span data-ttu-id="cfa34-121">可以让编译器生成符号的字符串表示形式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-121">You can let the compiler generate string representations of symbols.</span></span>
* <span data-ttu-id="cfa34-122">[Catch 和 Finally 块中的 Await](#await-in-catch-and-finally-blocks)：</span><span class="sxs-lookup"><span data-stu-id="cfa34-122">[await in catch and finally blocks](#await-in-catch-and-finally-blocks):</span></span>
    - <span data-ttu-id="cfa34-123">可以在先前不允许使用 `await` 表达式的位置使用它们。</span><span class="sxs-lookup"><span data-stu-id="cfa34-123">You can use `await` expressions in locations that previously disallowed them.</span></span>
* <span data-ttu-id="cfa34-124">[索引初始化表达式](#index-initializers)：</span><span class="sxs-lookup"><span data-stu-id="cfa34-124">[Index initializers](#index-initializers):</span></span>
    - <span data-ttu-id="cfa34-125">可以为关联容器及序列容器创建初始化表达式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-125">You can author initialization expressions for associative containers as well as sequence containers.</span></span>
* <span data-ttu-id="cfa34-126">[集合初始值设定项的扩展方法](#extension-add-methods-in-collection-initializers)：</span><span class="sxs-lookup"><span data-stu-id="cfa34-126">[Extension methods for collection initializers](#extension-add-methods-in-collection-initializers):</span></span>
    - <span data-ttu-id="cfa34-127">除成员方法以外，集合初始值设定项还可以依赖可访问的扩展方法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-127">Collection initializers can rely on accessible extension methods, in addition to member methods.</span></span>
* <span data-ttu-id="cfa34-128">[改进了重载解析](#improved-overload-resolution)：</span><span class="sxs-lookup"><span data-stu-id="cfa34-128">[Improved overload resolution](#improved-overload-resolution):</span></span>
    - <span data-ttu-id="cfa34-129">先前生成了不明确的方法调用的某些构造现在可以正确解析。</span><span class="sxs-lookup"><span data-stu-id="cfa34-129">Some constructs that previously generated ambiguous method calls now resolve correctly.</span></span>
* <span data-ttu-id="cfa34-130">[`deterministic` 编译器选项](#deterministic-compiler-output)：</span><span class="sxs-lookup"><span data-stu-id="cfa34-130">[`deterministic` compiler option](#deterministic-compiler-output):</span></span>
    - <span data-ttu-id="cfa34-131">该确定性的编译器选项确保同一源的后续编译生成同样的二进制输出内容。</span><span class="sxs-lookup"><span data-stu-id="cfa34-131">The deterministic compiler option ensures that subsequent compilations of the same source generate the same binary output.</span></span>

<span data-ttu-id="cfa34-132">这些功能的总体效果是让你编写的代码更简洁、更具可读性。</span><span class="sxs-lookup"><span data-stu-id="cfa34-132">The overall effect of these features is that you write more concise code that is also more readable.</span></span> <span data-ttu-id="cfa34-133">该语法不像许多常见做法那样繁琐。</span><span class="sxs-lookup"><span data-stu-id="cfa34-133">The syntax contains less ceremony for many common practices.</span></span> <span data-ttu-id="cfa34-134">可以更轻松地看出设计意图。</span><span class="sxs-lookup"><span data-stu-id="cfa34-134">It's easier to see the design intent with less ceremony.</span></span> <span data-ttu-id="cfa34-135">好好了解这些功能有助于你提高工作效率、编写更具可读性的代码，并更专注于核心功能而不是语言的构造。</span><span class="sxs-lookup"><span data-stu-id="cfa34-135">Learn these features well, and you'll be more productive, write more readable code, and concentrate more on your core features than on the constructs of the language.</span></span>

<span data-ttu-id="cfa34-136">此主题的其余部分提供有关上述每种功能的详细信息。</span><span class="sxs-lookup"><span data-stu-id="cfa34-136">The remainder of this topic provides details on each of these features.</span></span>

## <a name="auto-property-enhancements"></a><span data-ttu-id="cfa34-137">自动属性增强功能</span><span class="sxs-lookup"><span data-stu-id="cfa34-137">Auto-property enhancements</span></span>

<span data-ttu-id="cfa34-138">通过自动实现属性的语法（通常称为“自动属性”），可轻松创建具有简单 get 和 set 访问器的属性：</span><span class="sxs-lookup"><span data-stu-id="cfa34-138">The syntax for automatically implemented properties (usually referred to as 'auto-properties') made it very easy to create properties that had simple get and set accessors:</span></span>

[!code-csharp[ClassicAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicAutoProperty)]

<span data-ttu-id="cfa34-139">但是，这种简单的语法限制了你可以使用自动属性支持的设计类型。</span><span class="sxs-lookup"><span data-stu-id="cfa34-139">However, this simple syntax limited the kinds of designs you could support using auto-properties.</span></span> <span data-ttu-id="cfa34-140">C# 6 改进了自动属性功能，以便用户可以在更多方案中使用它们。</span><span class="sxs-lookup"><span data-stu-id="cfa34-140">C# 6 improves the auto-properties capabilities so that you can use them in more scenarios.</span></span> <span data-ttu-id="cfa34-141">无需频繁地求助于手动声明和操纵支持字段的更详细的语法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-141">You won't need to fall back on the more verbose syntax of declaring and manipulating the backing field by hand so often.</span></span>

<span data-ttu-id="cfa34-142">新语法可处理适用于只读属性的方案以及初始化自动属性后的变量存储的方案。</span><span class="sxs-lookup"><span data-stu-id="cfa34-142">The new syntax addresses scenarios for read-only properties, and for initializing the variable storage behind an auto-property.</span></span>

### <a name="read-only-auto-properties"></a><span data-ttu-id="cfa34-143">只读自动属性</span><span class="sxs-lookup"><span data-stu-id="cfa34-143">Read-only auto-properties</span></span>

<span data-ttu-id="cfa34-144">只读自动属性提供了更简洁的语法来创建不可变类型。</span><span class="sxs-lookup"><span data-stu-id="cfa34-144">*Read-only auto-properties* provide a more concise syntax to create immutable types.</span></span> <span data-ttu-id="cfa34-145">在 C# 的早期版本中，创建不可变类型的最直接方法是声明专用资源库：</span><span class="sxs-lookup"><span data-stu-id="cfa34-145">The closest you could get to immutable types in earlier versions of C# was to declare private setters:</span></span>

[!code-csharp[ClassicReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/oldcode.cs#ClassicReadOnlyAutoProperty)]
 
<span data-ttu-id="cfa34-146">使用此语法，编译器并不能确保类型是不可变的。</span><span class="sxs-lookup"><span data-stu-id="cfa34-146">Using this syntax, the compiler doesn't ensure that the type really is immutable.</span></span> <span data-ttu-id="cfa34-147">它仅强制规定不会从类外部的任何代码修改 `FirstName` 和 `LastName` 属性。</span><span class="sxs-lookup"><span data-stu-id="cfa34-147">It only enforces that the `FirstName` and `LastName` properties are not modified from any code outside the class.</span></span>

<span data-ttu-id="cfa34-148">只读自动属性实现真正的只读行为。</span><span class="sxs-lookup"><span data-stu-id="cfa34-148">Read-only auto-properties enable true read-only behavior.</span></span> <span data-ttu-id="cfa34-149">你声明仅具有 get 访问器的自动属性：</span><span class="sxs-lookup"><span data-stu-id="cfa34-149">You declare the auto-property with only a get accessor:</span></span>

[!code-csharp[ReadOnlyAutoProperty](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoProperty)]

<span data-ttu-id="cfa34-150">`FirstName` 和 `LastName` 属性只能在构造函数的主体中设置：</span><span class="sxs-lookup"><span data-stu-id="cfa34-150">The `FirstName` and `LastName` properties can be set only in the body of a constructor:</span></span>

[!code-csharp[ReadOnlyAutoPropertyConstructor](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadOnlyAutoPropertyConstructor)]

<span data-ttu-id="cfa34-151">尝试在另一种方法中设置 `LastName` 会生成 `CS0200` 编译错误：</span><span class="sxs-lookup"><span data-stu-id="cfa34-151">Trying to set `LastName` in another method generates a `CS0200` compilation error:</span></span>

```csharp
public class Student
{
    public string LastName { get;  }

    public void ChangeName(string newLastName)
    {
        // Generates CS0200: Property or indexer cannot be assigned to -- it is read only
        LastName = newLastName;
    }
}
```

<span data-ttu-id="cfa34-152">此功能实现用于创建不可变类型和使用更简洁且方便的自动属性语法的真正语言支持。</span><span class="sxs-lookup"><span data-stu-id="cfa34-152">This feature enables true language support for creating immutable types and using the more concise and convenient auto-property syntax.</span></span>

<span data-ttu-id="cfa34-153">如果添加此语法不会删除可访问的方法，则为[二进制兼容的更改](version-update-considerations.md#binary-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="cfa34-153">If adding this syntax does not remove an accessible method, it is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>

### <a name="auto-property-initializers"></a><span data-ttu-id="cfa34-154">自动属性初始化表达式</span><span class="sxs-lookup"><span data-stu-id="cfa34-154">Auto-property initializers</span></span>

<span data-ttu-id="cfa34-155">自动属性初始值设定项可让你在属性声明中声明自动属性的初始值。</span><span class="sxs-lookup"><span data-stu-id="cfa34-155">*Auto-property initializers* let you declare the initial value for an auto-property as part of the property declaration.</span></span>  <span data-ttu-id="cfa34-156">在早期版本中，这些属性需要具有资源库，你需要使用该资源库来初始化支持字段使用的数据存储。</span><span class="sxs-lookup"><span data-stu-id="cfa34-156">In earlier versions, these properties would need to have setters and you would need to use that setter to initialize the data storage used by the backing field.</span></span> <span data-ttu-id="cfa34-157">对于包含姓名和学生成绩列表的学生，请考虑此类：</span><span class="sxs-lookup"><span data-stu-id="cfa34-157">Consider this class for a student that contains the name and a list of the student's grades:</span></span>

[!code-csharp[Student](../../../samples/snippets/csharp/new-in-6/oldcode.cs#Student)]
 
<span data-ttu-id="cfa34-158">随着此类的增长，你可以包含其他构造函数。</span><span class="sxs-lookup"><span data-stu-id="cfa34-158">As this class grows, you may include other constructors.</span></span> <span data-ttu-id="cfa34-159">每个构造函数都需要初始化 Grades 属性，否则将引入错误。</span><span class="sxs-lookup"><span data-stu-id="cfa34-159">Each constructor needs to initialize the Grades property, or you'll introduce errors.</span></span>

<span data-ttu-id="cfa34-160">通过 C# 6，可为自动属性声明中的自动属性所使用的存储分配初始值：</span><span class="sxs-lookup"><span data-stu-id="cfa34-160">C# 6 enables you to assign an initial value for the storage used by an auto-property in the auto-property declaration:</span></span>

[!code-csharp[Initialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#Initialization)]

<span data-ttu-id="cfa34-161">`Grades` 成员在声明它的位置处被初始化。</span><span class="sxs-lookup"><span data-stu-id="cfa34-161">The `Grades` member is initialized where it is declared.</span></span> <span data-ttu-id="cfa34-162">这样，就能更容易地仅执行一次初始化。</span><span class="sxs-lookup"><span data-stu-id="cfa34-162">That makes it easier to perform the initialization exactly once.</span></span> <span data-ttu-id="cfa34-163">初始化是属性声明的一部分，可更轻松地将存储分配等同于 `Student` 对象的公用接口。</span><span class="sxs-lookup"><span data-stu-id="cfa34-163">The initialization is part of the property declaration, making it easier to equate the storage allocation with public interface for `Student` objects.</span></span>

<span data-ttu-id="cfa34-164">属性初始化表达式可与只读属性（如上所示）以及读/写属性（如下所示）一起使用。</span><span class="sxs-lookup"><span data-stu-id="cfa34-164">Property Initializers can be used with read-only properties, as shown above, and with read/write properties as well, as shown here.</span></span>

[!code-csharp[ReadWriteInitialization](../../../samples/snippets/csharp/new-in-6/newcode.cs#ReadWriteInitialization)]

## <a name="expression-bodied-function-members"></a><span data-ttu-id="cfa34-165">Expression-bodied 函数成员</span><span class="sxs-lookup"><span data-stu-id="cfa34-165">Expression-bodied function members</span></span>

<span data-ttu-id="cfa34-166">我们编写的很多成员的主体只包含一条可以表示为表达式的语句。</span><span class="sxs-lookup"><span data-stu-id="cfa34-166">The body of a lot of members that we write consist of only one statement that can be represented as an expression.</span></span> <span data-ttu-id="cfa34-167">可通过改为编写 expression-bodied 成员来简化该语法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-167">You can reduce that syntax by writing an expression-bodied member instead.</span></span> <span data-ttu-id="cfa34-168">这适用于方法和只读属性。</span><span class="sxs-lookup"><span data-stu-id="cfa34-168">It works for methods and read-only properties.</span></span> <span data-ttu-id="cfa34-169">例如，重写 `ToString()` 通常是理想之选：</span><span class="sxs-lookup"><span data-stu-id="cfa34-169">For example, an override of `ToString()` is often a great candidate:</span></span>

[!code-csharp[ToStringExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#ToStringExpressionMember)]

<span data-ttu-id="cfa34-170">还可以在只读属性中使用 expression-bodied 成员：</span><span class="sxs-lookup"><span data-stu-id="cfa34-170">You can also use expression-bodied members in read-only properties as well:</span></span>

[!code-csharp[FullNameExpressionMember](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="cfa34-171">将现有成员更改为 expression bodied 成员是[二进制兼容的更改](version-update-considerations.md#binary-compatible-changes)。</span><span class="sxs-lookup"><span data-stu-id="cfa34-171">Changing an existing member to an expression bodied member is a [binary compatible change](version-update-considerations.md#binary-compatible-changes).</span></span>


## <a name="using-static"></a><span data-ttu-id="cfa34-172">using static</span><span class="sxs-lookup"><span data-stu-id="cfa34-172">using static</span></span>

<span data-ttu-id="cfa34-173">using static 增强功能可用于导入单个类的静态方法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-173">The *using static* enhancement enables you to import the static methods of a single class.</span></span> <span data-ttu-id="cfa34-174">以前，`using` 语句将所有类型导入命名空间中。</span><span class="sxs-lookup"><span data-stu-id="cfa34-174">Previously, the `using` statement imported all types in a namespace.</span></span> 

<span data-ttu-id="cfa34-175">通常，我们在整个代码中使用类的静态方法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-175">Often we use a class' static methods throughout our code.</span></span> <span data-ttu-id="cfa34-176">重复键入类名可能会导致代码的含义难以理解。</span><span class="sxs-lookup"><span data-stu-id="cfa34-176">Repeatedly typing the class name can obscure the meaning of your code.</span></span> <span data-ttu-id="cfa34-177">一个常见的例子是当你编写执行许多数值计算的类时。</span><span class="sxs-lookup"><span data-stu-id="cfa34-177">A common example is when you write classes that perform many numeric calculations.</span></span>
<span data-ttu-id="cfa34-178">你的代码中将充满 <xref:System.Math.Sin%2A>、<xref:System.Math.Sqrt%2A> 以及对 <xref:System.Math> 类中不同方法的其他调用。</span><span class="sxs-lookup"><span data-stu-id="cfa34-178">Your code will be littered with <xref:System.Math.Sin%2A>, <xref:System.Math.Sqrt%2A> and other calls to different methods in the <xref:System.Math> class.</span></span> <span data-ttu-id="cfa34-179">新的 `using static` 语法可以使这些类更简洁、更易读。</span><span class="sxs-lookup"><span data-stu-id="cfa34-179">The new `using static` syntax can make these classes much cleaner to read.</span></span> <span data-ttu-id="cfa34-180">指定要使用的类：</span><span class="sxs-lookup"><span data-stu-id="cfa34-180">You specify the class you're using:</span></span>

[!code-csharp[UsingStaticMath](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticMath)]

<span data-ttu-id="cfa34-181">现在，可以使用 <xref:System.Math> 类中的任何静态方法而不必限定 <xref:System.Math> 类。</span><span class="sxs-lookup"><span data-stu-id="cfa34-181">And now, you can use any static method in the <xref:System.Math> class without qualifying the <xref:System.Math> class.</span></span> <span data-ttu-id="cfa34-182"><xref:System.Math> 类是此功能的一个很好的用例，因为它不包含任何实例方法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-182">The <xref:System.Math> class is a great use case for this feature because it does not contain any instance methods.</span></span> <span data-ttu-id="cfa34-183">还可以使用 `using static` 为具有静态和实例方法的类导入类的静态方法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-183">You can also use `using static` to import a class' static methods for a class that has both static and instance methods.</span></span> <span data-ttu-id="cfa34-184">最有用的示例之一是 <xref:System.String>：</span><span class="sxs-lookup"><span data-stu-id="cfa34-184">One of the most useful examples is <xref:System.String>:</span></span>

[!code-csharp[UsingStatic](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStatic)]

> [!NOTE]
> <span data-ttu-id="cfa34-185">在 static using 语句中必须使用完全限定的类名 `System.String`。</span><span class="sxs-lookup"><span data-stu-id="cfa34-185">You must use the fully qualified class name, `System.String` in a static using statement.</span></span> <span data-ttu-id="cfa34-186">而不能使用 `string` 关键字。</span><span class="sxs-lookup"><span data-stu-id="cfa34-186">You cannot use the `string` keyword instead.</span></span> 

<span data-ttu-id="cfa34-187">现在可以调用 <xref:System.String> 类中定义的静态方法，而不必将这些方法限定为该类的成员：</span><span class="sxs-lookup"><span data-stu-id="cfa34-187">You can now call static methods defined in the <xref:System.String> class without qualifying those methods as members of that class:</span></span>

[!code-csharp[UsingStaticString](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticString)]

<span data-ttu-id="cfa34-188">`static using` 功能和扩展方法以有趣的方式进行交互，并且该语言设计包含一些特定处理这些交互的规则。</span><span class="sxs-lookup"><span data-stu-id="cfa34-188">The `static using` feature and extension methods interact in interesting ways, and the language design included some rules that specifically address those interactions.</span></span> <span data-ttu-id="cfa34-189">目标是尽可能减少现有基本代码（包括你的基本代码）中发生重大更改的可能性。</span><span class="sxs-lookup"><span data-stu-id="cfa34-189">The goal is to minimize any chances of breaking changes in existing codebases, including yours.</span></span>

<span data-ttu-id="cfa34-190">仅在使用扩展方法调用语法调用扩展方法（而不是作为静态方法调用）时，扩展方法才在范围内。</span><span class="sxs-lookup"><span data-stu-id="cfa34-190">Extension methods are only in scope when called using the extension method invocation syntax, not when called as a static method.</span></span>
<span data-ttu-id="cfa34-191">你在 LINQ 查询中会经常看到这种情况。</span><span class="sxs-lookup"><span data-stu-id="cfa34-191">You'll often see this in LINQ queries.</span></span> <span data-ttu-id="cfa34-192">可以通过导入 <xref:System.Linq.Enumerable> 来导入 LINQ 模式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-192">You can import the LINQ pattern by importing <xref:System.Linq.Enumerable>.</span></span>

[!code-csharp[UsingStaticLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#usingStaticLinq)]

<span data-ttu-id="cfa34-193">这将导入 <xref:System.Linq.Enumerable> 类中的所有方法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-193">This imports all the methods in the <xref:System.Linq.Enumerable> class.</span></span>
<span data-ttu-id="cfa34-194">但是，扩展方法仅在作为扩展方法调用时才在范围内。</span><span class="sxs-lookup"><span data-stu-id="cfa34-194">However, the extension methods are only in scope when called as extension methods.</span></span> <span data-ttu-id="cfa34-195">如果使用静态方法语法调用扩展方法，则它们不在范围内：</span><span class="sxs-lookup"><span data-stu-id="cfa34-195">They are not in scope if they are called using the static method syntax:</span></span>

[!code-csharp[UsingStaticLinqMethod](../../../samples/snippets/csharp/new-in-6/newcode.cs#UsingStaticLinkMethod)]

<span data-ttu-id="cfa34-196">这个决定是因为扩展方法通常使用扩展方法调用表达式来调用。</span><span class="sxs-lookup"><span data-stu-id="cfa34-196">This decision is because extension methods are typically called using extension method invocation expressions.</span></span> <span data-ttu-id="cfa34-197">在使用静态方法调用语法调用它们的罕见情况下，是为了解析多义性。</span><span class="sxs-lookup"><span data-stu-id="cfa34-197">In the rare case where they are called using the static method call syntax it is to resolve ambiguity.</span></span>
<span data-ttu-id="cfa34-198">在调用中要求使用类名似乎是比较明智的做法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-198">Requiring the class name as part of the invocation seems wise.</span></span>

<span data-ttu-id="cfa34-199">`static using` 还有最后一项功能。</span><span class="sxs-lookup"><span data-stu-id="cfa34-199">There's one last feature of `static using`.</span></span> <span data-ttu-id="cfa34-200">`static using` 指令还可以导入任何嵌套的类型。</span><span class="sxs-lookup"><span data-stu-id="cfa34-200">The `static using` directive also imports any nested types.</span></span> <span data-ttu-id="cfa34-201">这样，你可以引用任何嵌套的类型，而无需限定。</span><span class="sxs-lookup"><span data-stu-id="cfa34-201">That enables you to reference any nested types without qualification.</span></span>

## <a name="null-conditional-operators"></a><span data-ttu-id="cfa34-202">Null 条件运算符</span><span class="sxs-lookup"><span data-stu-id="cfa34-202">Null-conditional operators</span></span>

<span data-ttu-id="cfa34-203">Null 值使代码变得复杂。</span><span class="sxs-lookup"><span data-stu-id="cfa34-203">Null values complicate code.</span></span> <span data-ttu-id="cfa34-204">需要检查变量的每个访问，以确保没有取消对 `null` 的引用。</span><span class="sxs-lookup"><span data-stu-id="cfa34-204">You need to check every access of variables to ensure you are not dereferencing `null`.</span></span> <span data-ttu-id="cfa34-205">Null 条件运算符使这些检查更轻松、更流畅。</span><span class="sxs-lookup"><span data-stu-id="cfa34-205">The *null conditional operator* makes those checks much easier and fluid.</span></span>

<span data-ttu-id="cfa34-206">只需将成员访问 `.` 替换为 `?.`：</span><span class="sxs-lookup"><span data-stu-id="cfa34-206">Simply replace the member access `.` with `?.`:</span></span>

[!code-csharp[NullConditional](../../../samples/snippets/csharp/new-in-6/program.cs#NullConditional)]

<span data-ttu-id="cfa34-207">在前面的示例中，如果 Person 对象是 `null`，则将变量 `first` 赋值为 `null`。</span><span class="sxs-lookup"><span data-stu-id="cfa34-207">In the preceding example, the variable `first` is assigned `null` if the person object is `null`.</span></span> <span data-ttu-id="cfa34-208">否则，它将被分配 `FirstName` 属性的值。</span><span class="sxs-lookup"><span data-stu-id="cfa34-208">Otherwise, it gets assigned the value of the `FirstName` property.</span></span> <span data-ttu-id="cfa34-209">最重要的是，`?.` 意味着当 `person` 变量为 `null` 时，此行代码不会生成 `NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="cfa34-209">Most importantly, the `?.` means that this line of code does not generate a `NullReferenceException` when the `person` variable is `null`.</span></span> <span data-ttu-id="cfa34-210">它会短路并生成 `null`。</span><span class="sxs-lookup"><span data-stu-id="cfa34-210">Instead, it short-circuits and produces `null`.</span></span>

<span data-ttu-id="cfa34-211">此外，请注意，无论 `person` 的值是什么，此表达式均返回 `string`。</span><span class="sxs-lookup"><span data-stu-id="cfa34-211">Also, note that this expression returns a `string`, regardless of the value of `person`.</span></span>
<span data-ttu-id="cfa34-212">在短路的情况下，键入返回的 `null` 值以匹配整个表达式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-212">In the case of short circuiting, the `null` value returned is typed to match the full expression.</span></span>

<span data-ttu-id="cfa34-213">通常，可以将此构造与 null 合并运算符一起使用，以在其中一个属性为 `null` 时分配默认值：</span><span class="sxs-lookup"><span data-stu-id="cfa34-213">You can often use this construct with the *null coalescing* operator to assign default values when one of the properties are `null`:</span></span>

[!code-csharp[NullCoalescing](../../../samples/snippets/csharp/new-in-6/program.cs#NullCoalescing)]

<span data-ttu-id="cfa34-214">`?.` 运算符的右侧操作数不仅限于属性或字段。</span><span class="sxs-lookup"><span data-stu-id="cfa34-214">The right hand side operand of the `?.` operator is not limited to properties or fields.</span></span>
<span data-ttu-id="cfa34-215">还可以将其用于有条件地调用方法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-215">You can also use it to conditionally invoke methods.</span></span> <span data-ttu-id="cfa34-216">具有 null 条件运算符的成员函数的最常见用法是用于安全地调用可能为 `null` 的委托（或事件处理程序）。</span><span class="sxs-lookup"><span data-stu-id="cfa34-216">The most common use of member functions with the null conditional operator is to safely invoke delegates (or event handlers) that may be `null`.</span></span>  <span data-ttu-id="cfa34-217">方法是使用 `?.` 运算符调用该委托的 `Invoke` 方法来访问成员。</span><span class="sxs-lookup"><span data-stu-id="cfa34-217">You'll do this by calling the delegate's `Invoke` method using the `?.` operator to access the member.</span></span> <span data-ttu-id="cfa34-218">可以在</span><span class="sxs-lookup"><span data-stu-id="cfa34-218">You can see an example in the</span></span>  
<span data-ttu-id="cfa34-219">[委托模式](../delegates-patterns.md#handling-null-delegates)主题中看到一个示例。</span><span class="sxs-lookup"><span data-stu-id="cfa34-219">[delegate patterns](../delegates-patterns.md#handling-null-delegates) topic.</span></span>

<span data-ttu-id="cfa34-220">`?.` 运算符的规则确保运算符的左侧仅计算一次。</span><span class="sxs-lookup"><span data-stu-id="cfa34-220">The rules of the `?.` operator ensure that the left-hand side of the operator is evaluated only once.</span></span> <span data-ttu-id="cfa34-221">这很重要，它可实现许多语法，包括使用事件处理程序的示例。</span><span class="sxs-lookup"><span data-stu-id="cfa34-221">This is important and enables many idioms, including the example using event handlers.</span></span> <span data-ttu-id="cfa34-222">让我们从事件处理程序的使用开始。</span><span class="sxs-lookup"><span data-stu-id="cfa34-222">Let's start with the event handler usage.</span></span> <span data-ttu-id="cfa34-223">在以前的 C# 版本中，建议编写与下面类似的代码：</span><span class="sxs-lookup"><span data-stu-id="cfa34-223">In previous versions of C#, you were encouraged to write code like this:</span></span>

```csharp
var handler = this.SomethingHappened;
if (handler != null)
    handler(this, eventArgs);
```

<span data-ttu-id="cfa34-224">它的推荐度高于以下较简单的语法：</span><span class="sxs-lookup"><span data-stu-id="cfa34-224">This was preferred over a simpler syntax:</span></span>

```csharp
// Not recommended
if (this.SomethingHappened != null)
    this.SomethingHappened(this, eventArgs);
```

> [!IMPORTANT]
> <span data-ttu-id="cfa34-225">前一个示例引入了一个争用条件。</span><span class="sxs-lookup"><span data-stu-id="cfa34-225">The preceding example introduces a race condition.</span></span> <span data-ttu-id="cfa34-226">在针对 `null` 进行检查时，`SomethingHappened` 事件可能具有订阅服务器，在引发该事件之前这些订阅服务器可能已被删除。</span><span class="sxs-lookup"><span data-stu-id="cfa34-226">The `SomethingHappened` event may have subscribers when checked against `null`, and those subscribers may have been removed before the event is raised.</span></span> <span data-ttu-id="cfa34-227">这会导致引发 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="cfa34-227">That would cause a <xref:System.NullReferenceException> to be thrown.</span></span>

<span data-ttu-id="cfa34-228">在第二个版本中，`SomethingHappened` 事件处理程序在测试时可能为非 null，但如果其他代码删除处理程序，则在调用事件处理程序时，它可能仍为 null。</span><span class="sxs-lookup"><span data-stu-id="cfa34-228">In this second version, the `SomethingHappened` event handler might be non-null when tested, but if other code removes a handler, it could still be null when the event handler was called.</span></span>

<span data-ttu-id="cfa34-229">编译器生成 `?.` 运算符的代码，以确保 `?.` 表达式的左侧 (`this.SomethingHappened`) 计算一次，并且缓存结果：</span><span class="sxs-lookup"><span data-stu-id="cfa34-229">The compiler generates code for the `?.` operator that ensures the left side (`this.SomethingHappened`) of the `?.` expression is evaluated once, and the result is cached:</span></span>

```csharp
// preferred in C# 6:
this.SomethingHappened?.Invoke(this, eventArgs);
```

<span data-ttu-id="cfa34-230">通过确保左侧仅计算一次，可在 `?.` 的左侧使用任何表达式（包括方法调用）。即使它们具有副作用，但因为只计算一次，所以副作用只产生一次 。</span><span class="sxs-lookup"><span data-stu-id="cfa34-230">Ensuring that the left side is evaluated only once also enables you to use any expression, including method calls, on the left side of the `?.` Even if these have side-effects, they are evaluated once, so the side effects occur only once.</span></span> <span data-ttu-id="cfa34-231">可以在有关[事件](../events-overview.md#language-support-for-events)的内容中看到一个示例。</span><span class="sxs-lookup"><span data-stu-id="cfa34-231">You can see an example in our content on [events](../events-overview.md#language-support-for-events).</span></span>

## <a name="string-interpolation"></a><span data-ttu-id="cfa34-232">字符串内插</span><span class="sxs-lookup"><span data-stu-id="cfa34-232">String interpolation</span></span>

<span data-ttu-id="cfa34-233">C# 6 包含新语法，用于从字符串和嵌入的表达式编写字符串，可以通过计算这些字符串来生成其他字符串值。</span><span class="sxs-lookup"><span data-stu-id="cfa34-233">C# 6 contains new syntax for composing strings from a string and embedded expressions that are evaluated to produce other string values.</span></span>

<span data-ttu-id="cfa34-234">传统上，需要在类似 <xref:System.String.Format%2A?displayProperty=nameWithType> 的方法中使用位置参数：</span><span class="sxs-lookup"><span data-stu-id="cfa34-234">Traditionally, you needed to use positional parameters in a method like <xref:System.String.Format%2A?displayProperty=nameWithType>:</span></span>

[!code-csharp[stringFormat](../../../samples/snippets/csharp/new-in-6/oldcode.cs#stringFormat)]

<span data-ttu-id="cfa34-235">使用 C# 6，新的[字符串内插](../language-reference/tokens/interpolated.md)功能可以在字符串中嵌入表达式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-235">With C# 6, the new [string interpolation](../language-reference/tokens/interpolated.md) feature enables you to embed the expressions in a string.</span></span> <span data-ttu-id="cfa34-236">只需在字符串前面加上 `$`：</span><span class="sxs-lookup"><span data-stu-id="cfa34-236">Simply preface the string with `$`:</span></span>

[!code-csharp[stringInterpolation](../../../samples/snippets/csharp/new-in-6/newcode.cs#FullNameExpressionMember)]

<span data-ttu-id="cfa34-237">本示例使用替代表达式的属性表达式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-237">This example uses property expressions for the substituted expressions.</span></span> <span data-ttu-id="cfa34-238">可以扩展此语法以使用任何表达式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-238">You can expand on this syntax to use any expression.</span></span> <span data-ttu-id="cfa34-239">例如，可以在内插过程中计算学生的成绩平均值：</span><span class="sxs-lookup"><span data-stu-id="cfa34-239">For example, you could compute a student's grade point average as part of the interpolation:</span></span>

[!code-csharp[stringInterpolationExpression](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationExpression)]

<span data-ttu-id="cfa34-240">运行前面的示例，你会发现 `Grades.Average()` 的输出的小数位数可能比你需要的多。</span><span class="sxs-lookup"><span data-stu-id="cfa34-240">Running the preceding example, you would find that the output for `Grades.Average()` might have more decimal places than you would like.</span></span> <span data-ttu-id="cfa34-241">字符串内插语法支持可使用前面的格式设置方法的所有格式字符串。</span><span class="sxs-lookup"><span data-stu-id="cfa34-241">The string interpolation syntax supports all the format strings available using earlier formatting methods.</span></span> <span data-ttu-id="cfa34-242">在大括号内指定格式字符串。</span><span class="sxs-lookup"><span data-stu-id="cfa34-242">You specify the format string inside the braces.</span></span> <span data-ttu-id="cfa34-243">在要设置格式的表达式后面添加 `:`：</span><span class="sxs-lookup"><span data-stu-id="cfa34-243">Add a `:` following the expression to format:</span></span>

[!code-csharp[stringInterpolationFormat](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationFormat)]

<span data-ttu-id="cfa34-244">上一行代码将 `Grades.Average()` 的值格式设置为具有两位小数的浮点数。</span><span class="sxs-lookup"><span data-stu-id="cfa34-244">The preceding line of code formats the value for `Grades.Average()` as a floating-point number with two decimal places.</span></span>

<span data-ttu-id="cfa34-245">`:` 始终解释为要设置格式的表达式和格式字符串之间的分隔符。</span><span class="sxs-lookup"><span data-stu-id="cfa34-245">The `:` is always interpreted as the separator between the expression being formatted and the format string.</span></span> <span data-ttu-id="cfa34-246">当表达式以另一种方式（如[条件运算符](../language-reference/operators/conditional-operator.md)）使用 `:` 时，这可能会产生问题：</span><span class="sxs-lookup"><span data-stu-id="cfa34-246">This can introduce problems when your expression uses a `:` in another way, such as a [conditional operator](../language-reference/operators/conditional-operator.md):</span></span>

```csharp
public string GetGradePointPercentages() =>
    $"Name: {LastName}, {FirstName}. G.P.A: {Grades.Any() ? Grades.Average() : double.NaN:F2}";
```

<span data-ttu-id="cfa34-247">在上一示例中，`:` 解析为格式字符串的开头，而不是条件运算符的一部分。</span><span class="sxs-lookup"><span data-stu-id="cfa34-247">In the preceding example, the `:` is parsed as the beginning of the format string, not part of the conditional operator.</span></span> <span data-ttu-id="cfa34-248">在发生此问题的所有情况下，可以用括号将表达式括起来，强制编译器按照你的意图解释该表达式：</span><span class="sxs-lookup"><span data-stu-id="cfa34-248">In all cases where this happens, surround the expression with parentheses to force the compiler to interpret the expression as you intend:</span></span>

[!code-csharp[stringInterpolationConditional](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationConditional)]

<span data-ttu-id="cfa34-249">对可以放在大括号之间的表达式没有任何限制。</span><span class="sxs-lookup"><span data-stu-id="cfa34-249">There aren't any limitations on the expressions you can place between the braces.</span></span> <span data-ttu-id="cfa34-250">可以在内插字符串中执行复杂的 LINQ 查询，以执行计算并显示结果：</span><span class="sxs-lookup"><span data-stu-id="cfa34-250">You can execute a complex LINQ query inside an interpolated string to perform computations and display the result:</span></span>

[!code-csharp[stringInterpolationLinq](../../../samples/snippets/csharp/new-in-6/newcode.cs#stringInterpolationLinq)]

<span data-ttu-id="cfa34-251">可以从此示例中看出，甚至可以将字符串内插表达式嵌套在另一个字符串内插表达式中。</span><span class="sxs-lookup"><span data-stu-id="cfa34-251">You can see from this sample that you can even nest a string interpolation expression inside another string interpolation expression.</span></span> <span data-ttu-id="cfa34-252">此示例在生产代码中很有可能比你想的更加复杂。</span><span class="sxs-lookup"><span data-stu-id="cfa34-252">This example is very likely more complex than you would want in production code.</span></span>
<span data-ttu-id="cfa34-253">但它说明了该功能的范围。</span><span class="sxs-lookup"><span data-stu-id="cfa34-253">Rather, it is illustrative of the breadth of the feature.</span></span> <span data-ttu-id="cfa34-254">任何 C# 表达式都可以放置在内插字符串的大括号之间。</span><span class="sxs-lookup"><span data-stu-id="cfa34-254">Any C# expression can be placed between the curly braces of an interpolated string.</span></span>

<span data-ttu-id="cfa34-255">若要开始使用字符串内插，请阅读 [C# 中的字符串内插](../tutorials/intro-to-csharp/interpolated-strings.yml)交互式教程。</span><span class="sxs-lookup"><span data-stu-id="cfa34-255">To get started with string interpolation, check the [String interpolation in C#](../tutorials/intro-to-csharp/interpolated-strings.yml) interactive tutorial.</span></span>

### <a name="string-interpolation-and-specific-cultures"></a><span data-ttu-id="cfa34-256">字符串内插和特定区域性</span><span class="sxs-lookup"><span data-stu-id="cfa34-256">String interpolation and specific cultures</span></span>

<span data-ttu-id="cfa34-257">前面部分中显示的所有示例使用执行代码的计算机上的当前区域性设置字符串格式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-257">All the examples shown in the preceding section format the strings using the current culture on the machine where the code executes.</span></span> <span data-ttu-id="cfa34-258">通常，可能需要使用特定区域性设置生成的字符串的格式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-258">Often you may need to format the string produced using a specific culture.</span></span>
<span data-ttu-id="cfa34-259">为此，请利用通过字符串内插生成的对象可以隐式转换为 <xref:System.FormattableString?displayProperty=nameWithType> 这一事实。</span><span class="sxs-lookup"><span data-stu-id="cfa34-259">To do that use the fact that the object produced by a string interpolation can be implicitly converted to <xref:System.FormattableString?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="cfa34-260"><xref:System.FormattableString> 实例包含组合格式字符串，以及在将其转换为字符串之前评估表达式的结果。</span><span class="sxs-lookup"><span data-stu-id="cfa34-260">The <xref:System.FormattableString> instance contains the composite format string, and the results of evaluating the expressions before converting them to strings.</span></span> <span data-ttu-id="cfa34-261">在设置字符串的格式时，可以使用 <xref:System.FormattableString.ToString(System.IFormatProvider)> 方法指定区域性。</span><span class="sxs-lookup"><span data-stu-id="cfa34-261">Use the <xref:System.FormattableString.ToString(System.IFormatProvider)> method to specify the culture when formatting a string.</span></span> <span data-ttu-id="cfa34-262">例如，以下示例使用德国区域性生成字符串。</span><span class="sxs-lookup"><span data-stu-id="cfa34-262">For example, the following example produces a string using German culture.</span></span> <span data-ttu-id="cfa34-263">（它使用“,”字符作为小数分隔符，使用“.”字符作为千位分隔符。）</span><span class="sxs-lookup"><span data-stu-id="cfa34-263">(It uses the ',' character for the decimal separator, and the '.' character as the thousands separator.)</span></span>

```csharp
FormattableString str = $"Average grade is {s.Grades.Average()}";
var gradeStr = str.ToString(new System.Globalization.CultureInfo("de-DE"));
```

<span data-ttu-id="cfa34-264">有关详细信息，请参阅[字符串内插](../language-reference/tokens/interpolated.md)一文和 [C# 中的字符串内插](../tutorials/string-interpolation.md)教程。</span><span class="sxs-lookup"><span data-stu-id="cfa34-264">For more information, see the [String interpolation](../language-reference/tokens/interpolated.md) article and the [String interpolation in C#](../tutorials/string-interpolation.md) tutorial.</span></span>

## <a name="exception-filters"></a><span data-ttu-id="cfa34-265">异常筛选器</span><span class="sxs-lookup"><span data-stu-id="cfa34-265">Exception filters</span></span>

<span data-ttu-id="cfa34-266">C# 6 中的另一个新功能是异常筛选器。</span><span class="sxs-lookup"><span data-stu-id="cfa34-266">Another new feature in C# 6 is *exception filters*.</span></span> <span data-ttu-id="cfa34-267">异常筛选器是确定何时应该应用给定的 catch 子句的子句。</span><span class="sxs-lookup"><span data-stu-id="cfa34-267">Exception Filters are clauses that determine when a given catch clause should be applied.</span></span>
<span data-ttu-id="cfa34-268">如果用于异常筛选器的表达式计算结果为 `true`，则 catch 子句将对异常执行正常处理。</span><span class="sxs-lookup"><span data-stu-id="cfa34-268">If the expression used for an exception filter evaluates to `true`, the catch clause performs its normal processing on an exception.</span></span> <span data-ttu-id="cfa34-269">如果表达式计算结果为 `false`，则将跳过 `catch` 子句。</span><span class="sxs-lookup"><span data-stu-id="cfa34-269">If the expression evaluates to `false`, then the `catch` clause is skipped.</span></span>

<span data-ttu-id="cfa34-270">一种用途是检查有关异常的信息，以确定 `catch` 子句是否可以处理该异常：</span><span class="sxs-lookup"><span data-stu-id="cfa34-270">One use is to examine information about an exception to determine if a `catch` clause can process the exception:</span></span>

[!code-csharp[ExceptionFilter](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilter)]

<span data-ttu-id="cfa34-271">由异常筛选器生成的代码提供了有关已引发且未处理的异常的更好信息。</span><span class="sxs-lookup"><span data-stu-id="cfa34-271">The code generated by exception filters provides better information about an exception that is thrown and not processed.</span></span> <span data-ttu-id="cfa34-272">在将异常筛选器添加到语言之前，需要创建如下所示的代码：</span><span class="sxs-lookup"><span data-stu-id="cfa34-272">Before exception filters were added to the language, you would need to create code like the following:</span></span>

[!code-csharp[ExceptionFilterOld](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#ExceptionFilterOld)]

<span data-ttu-id="cfa34-273">这两个示例中，引发异常的点发生了更改。</span><span class="sxs-lookup"><span data-stu-id="cfa34-273">The point where the exception is thrown changes between these two examples.</span></span>
<span data-ttu-id="cfa34-274">在前一个代码中，使用了 `throw` 子句，对故障转储的任何堆栈跟踪分析或检查都将显示异常是从 catch 子句中的 `throw` 语句引发的。</span><span class="sxs-lookup"><span data-stu-id="cfa34-274">In the previous code, where a `throw` clause is used, any stack trace analysis or examination of crash dumps will show that the exception was thrown from the `throw` statement in your catch clause.</span></span> <span data-ttu-id="cfa34-275">实际的异常对象将包含原始调用堆栈，但是在此引发点与原始引发点位置之间的调用堆栈中的任何变量的所有其他信息已丢失。</span><span class="sxs-lookup"><span data-stu-id="cfa34-275">The actual exception object will contain the original call stack, but all other information about any variables in the call stack between this throw point and the location of the original throw point has been lost.</span></span> 

<span data-ttu-id="cfa34-276">对比使用异常筛选器的代码的处理方式：异常筛选器表达式的计算结果为 `false`。</span><span class="sxs-lookup"><span data-stu-id="cfa34-276">Contrast that with how the code using an exception filter is processed: the exception filter expression evaluates to `false`.</span></span> <span data-ttu-id="cfa34-277">因此，执行决不会进入 `catch` 子句。</span><span class="sxs-lookup"><span data-stu-id="cfa34-277">Therefore, execution never enters the `catch` clause.</span></span> <span data-ttu-id="cfa34-278">因为 `catch` 子句不会执行，不会发生堆栈展开。</span><span class="sxs-lookup"><span data-stu-id="cfa34-278">Because the `catch` clause does not execute, no stack unwinding takes place.</span></span> <span data-ttu-id="cfa34-279">这表示将保留原始引发位置，以用于以后将会发生的任何调试活动。</span><span class="sxs-lookup"><span data-stu-id="cfa34-279">That means the original throw location is preserved for any debugging activities that would take place later.</span></span>

<span data-ttu-id="cfa34-280">每当需要评估异常的字段或属性，而不是仅仅依赖异常类型时，请使用异常筛选器保留更多调试信息。</span><span class="sxs-lookup"><span data-stu-id="cfa34-280">Whenever you need to evaluate fields or properties of an exception, instead of relying solely on the exception type, use an exception filter to preserve more debugging information.</span></span>

<span data-ttu-id="cfa34-281">使用异常筛选器的另一种推荐模式是将其用于日志记录例程。</span><span class="sxs-lookup"><span data-stu-id="cfa34-281">Another recommended pattern with exception filters is to use them for logging routines.</span></span> <span data-ttu-id="cfa34-282">这种用法还会利用当异常筛选器计算结果为 `false` 时，保留异常引发点的方式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-282">This usage also leverages the manner in which the exception throw point is preserved when an exception filter evaluates to `false`.</span></span>

<span data-ttu-id="cfa34-283">日志记录方法将是这样一种方法：其参数为无条件返回 `false` 的异常：</span><span class="sxs-lookup"><span data-stu-id="cfa34-283">A logging method would be a method whose argument is the exception that unconditionally returns `false`:</span></span>

[!code-csharp[ExceptionFilterLogging](../../../samples/snippets/csharp/new-in-6/ExceptionFilterHelpers.cs#ExceptionFilterLogging)]

<span data-ttu-id="cfa34-284">每当要记录异常时，可以添加一个 catch 子句，并将此方法用作异常筛选器：</span><span class="sxs-lookup"><span data-stu-id="cfa34-284">Whenever you want to log an exception, you can add a catch clause, and use this method as the exception filter:</span></span>

[!code-csharp[LogException](../../../samples/snippets/csharp/new-in-6/program.cs#LogException)]

<span data-ttu-id="cfa34-285">永远不会捕获异常，因为 `LogException` 方法始终返回 `false`。</span><span class="sxs-lookup"><span data-stu-id="cfa34-285">The exceptions are never caught, because the `LogException` method always returns `false`.</span></span> <span data-ttu-id="cfa34-286">始终为 false 的异常筛选器意味着可以将此日志记录处理程序放置在任何其他异常处理程序之前：</span><span class="sxs-lookup"><span data-stu-id="cfa34-286">That always false exception filter means that you can place this logging handler before any other exception handlers:</span></span>

[!code-csharp[LogExceptionRecovery](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionRecovery)]

<span data-ttu-id="cfa34-287">前一示例中强调了异常筛选器的一个非常重要的方面。</span><span class="sxs-lookup"><span data-stu-id="cfa34-287">The preceding example highlights a very important facet of exception filters.</span></span>
<span data-ttu-id="cfa34-288">通过异常筛选器，可实现以下方案：较常规的异常 catch 子句可出现在较具体的 catch 子句前。</span><span class="sxs-lookup"><span data-stu-id="cfa34-288">The exception filters enable scenarios where a more general exception catch clause may appear before a more specific one.</span></span> <span data-ttu-id="cfa34-289">也可以在多个 catch 子句中出现相同的异常类型：</span><span class="sxs-lookup"><span data-stu-id="cfa34-289">It's also possible to have the same exception type appear in multiple catch clauses:</span></span>

[!code-csharp[HandleNotChanged](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#HandleNotChanged)]

<span data-ttu-id="cfa34-290">另一种建议模式有助于防止 catch 子句在附加调试器时处理异常。</span><span class="sxs-lookup"><span data-stu-id="cfa34-290">Another recommended pattern helps prevent catch clauses from processing exceptions when a debugger is attached.</span></span> <span data-ttu-id="cfa34-291">通过此技术，可以使用调试器运行应用程序，并在引发异常时停止执行。</span><span class="sxs-lookup"><span data-stu-id="cfa34-291">This technique enables you to run an application with the debugger, and stop execution when an exception is thrown.</span></span>

<span data-ttu-id="cfa34-292">在代码中添加一个异常筛选器，使任何恢复代码仅在未附加调试器时执行：</span><span class="sxs-lookup"><span data-stu-id="cfa34-292">In your code, add an exception filter so that any recovery code executes only when a debugger is not attached:</span></span>

[!code-csharp[LogExceptionDebugger](../../../samples/snippets/csharp/new-in-6/program.cs#LogExceptionDebugger)]

<span data-ttu-id="cfa34-293">在代码中添加之后，将调试器设置为在所有未处理的异常处中断。</span><span class="sxs-lookup"><span data-stu-id="cfa34-293">After adding this in code, you set your debugger to break on all unhandled exceptions.</span></span> <span data-ttu-id="cfa34-294">在调试器下运行程序，每当 `PerformFailingOperation()` 引发 `RecoverableException` 时，调试器就会中断。</span><span class="sxs-lookup"><span data-stu-id="cfa34-294">Run the program under the debugger, and the debugger breaks whenever `PerformFailingOperation()` throws a `RecoverableException`.</span></span>
<span data-ttu-id="cfa34-295">调试器将中断程序，因为不会执行 catch 子句（由于异常筛选器返回 false）。</span><span class="sxs-lookup"><span data-stu-id="cfa34-295">The debugger breaks your program, because the catch clause won't be executed due to the false-returning exception filter.</span></span>

## <a name="the-nameof-expression"></a><span data-ttu-id="cfa34-296">`nameof` 表达式</span><span class="sxs-lookup"><span data-stu-id="cfa34-296">The `nameof` expression</span></span>

<span data-ttu-id="cfa34-297">`nameof` 表达式的计算结果为符号的名称。</span><span class="sxs-lookup"><span data-stu-id="cfa34-297">The `nameof` expression evaluates to the name of a symbol.</span></span> <span data-ttu-id="cfa34-298">每当需要变量、属性或成员字段的名称时，这是让工具正常运行的好办法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-298">It's a great way to get tools working whenever you need the name of a variable, a property, or a member field.</span></span>

<span data-ttu-id="cfa34-299">`nameof` 的其中一个最常见的用途是提供引起异常的符号的名称：</span><span class="sxs-lookup"><span data-stu-id="cfa34-299">One of the most common uses for `nameof` is to provide the name of a symbol that caused an exception:</span></span>

[!code-csharp[nameof](../../../samples/snippets/csharp/new-in-6/NewCode.cs#UsingStaticString)]

<span data-ttu-id="cfa34-300">另一个用途是用于实现 `INotifyPropertyChanged` 接口的基于 XAML 的应用程序：</span><span class="sxs-lookup"><span data-stu-id="cfa34-300">Another use is with XAML based applications that implement the `INotifyPropertyChanged` interface:</span></span>

[!code-csharp[nameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#nameofNotify)]

<span data-ttu-id="cfa34-301">相较于使用常量字符串，使用 `nameof` 运算符的优点是工具可以了解符号。</span><span class="sxs-lookup"><span data-stu-id="cfa34-301">The advantage of using the `nameof` operator over a constant string is that tools can understand the symbol.</span></span> <span data-ttu-id="cfa34-302">如果使用重构工具重命名符号，会在 `nameof` 表达式中对其重命名。</span><span class="sxs-lookup"><span data-stu-id="cfa34-302">If you use refactoring tools to rename the symbol, it will rename it in the `nameof` expression.</span></span> <span data-ttu-id="cfa34-303">常量字符串没有这一优势。</span><span class="sxs-lookup"><span data-stu-id="cfa34-303">Constant strings don't have that advantage.</span></span> <span data-ttu-id="cfa34-304">请在你最喜爱的编辑器中亲自尝试一下：重命名一个变量，任何 `nameof` 表达式也将更新。</span><span class="sxs-lookup"><span data-stu-id="cfa34-304">Try it yourself in your favorite editor: rename a variable, and any `nameof` expressions will update as well.</span></span>

<span data-ttu-id="cfa34-305">`nameof` 表达式生成其参数（在前面的示例中为 `LastName`）的非限定名称，即使使用参数的完全限定名称也是如此：</span><span class="sxs-lookup"><span data-stu-id="cfa34-305">The `nameof` expression produces the unqualified name of its argument (`LastName` in the previous examples) even if you use the fully qualified name for the argument:</span></span>

[!code-csharp[QualifiedNameofNotify](../../../samples/snippets/csharp/new-in-6/viewmodel.cs#QualifiedNameofNotify)]

<span data-ttu-id="cfa34-306">此 `nameof` 表达式生成 `FirstName`，而不是 `UXComponents.ViewModel.FirstName`。</span><span class="sxs-lookup"><span data-stu-id="cfa34-306">This `nameof` expression produces `FirstName`, not `UXComponents.ViewModel.FirstName`.</span></span>

## <a name="await-in-catch-and-finally-blocks"></a><span data-ttu-id="cfa34-307">Catch 和 Finally 块中的 Await</span><span class="sxs-lookup"><span data-stu-id="cfa34-307">Await in Catch and Finally blocks</span></span>

<span data-ttu-id="cfa34-308">C# 5 对于可放置 `await` 表达式的位置有若干限制。</span><span class="sxs-lookup"><span data-stu-id="cfa34-308">C# 5 had several limitations around where you could place `await` expressions.</span></span>
<span data-ttu-id="cfa34-309">其中一个限制已在 C# 6 中删除。</span><span class="sxs-lookup"><span data-stu-id="cfa34-309">One of those has been removed in C# 6.</span></span> <span data-ttu-id="cfa34-310">现在，可以在 `catch` 或 `finally` 表达式中使用 `await`。</span><span class="sxs-lookup"><span data-stu-id="cfa34-310">You can now use `await` in `catch` or `finally` expressions.</span></span> 

<span data-ttu-id="cfa34-311">在 catch 和 finally 块中添加 await 表达式可能会使这些表达式的处理方式变得复杂。</span><span class="sxs-lookup"><span data-stu-id="cfa34-311">The addition of await expressions in catch and finally blocks may appear to complicate how those are processed.</span></span> <span data-ttu-id="cfa34-312">让我们添加一个示例对此进行讨论。</span><span class="sxs-lookup"><span data-stu-id="cfa34-312">Let's add an example to discuss how this appears.</span></span> <span data-ttu-id="cfa34-313">在任何异步方法中，都可以在 finally 子句中使用 await 表达式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-313">In any async method, you can use an await expression in a finally clause.</span></span>

<span data-ttu-id="cfa34-314">使用 C# 6，还可以在 catch 表达式中使用 await。</span><span class="sxs-lookup"><span data-stu-id="cfa34-314">With C# 6, you can also await in catch expressions.</span></span> <span data-ttu-id="cfa34-315">这通常用于日志记录方案：</span><span class="sxs-lookup"><span data-stu-id="cfa34-315">This is most often used with logging scenarios:</span></span>

[!code-csharp[AwaitFinally](../../../samples/snippets/csharp/new-in-6/NetworkClient.cs#AwaitFinally)]

<span data-ttu-id="cfa34-316">在 `catch` 和 `finally` 子句中添加 `await` 支持的实现细节可确保该行为与同步代码的行为一致。</span><span class="sxs-lookup"><span data-stu-id="cfa34-316">The implementation details for adding `await` support inside `catch` and `finally` clauses ensures that the behavior is consistent with the behavior for synchronous code.</span></span> <span data-ttu-id="cfa34-317">当在 `catch` 或 `finally` 子句中执行的代码引发异常时，执行将在下一个外层块中查找合适的 `catch` 子句。</span><span class="sxs-lookup"><span data-stu-id="cfa34-317">When code executed in a `catch` or `finally` clause throws, execution looks for a suitable `catch` clause in the next surrounding block.</span></span> <span data-ttu-id="cfa34-318">如果存在当前异常，则该异常将丢失。</span><span class="sxs-lookup"><span data-stu-id="cfa34-318">If there was a current exception, that exception is lost.</span></span> <span data-ttu-id="cfa34-319">`catch` 和 `finally` 子句中的 awaited 表达式也会发生同样的情况：搜索合适的 `catch`，并且当前异常（如果有）将丢失。</span><span class="sxs-lookup"><span data-stu-id="cfa34-319">The same happens with awaited expressions in `catch` and `finally` clauses: a suitable `catch` is searched for, and the current exception, if any, is lost.</span></span>  

> [!NOTE]
> <span data-ttu-id="cfa34-320">鉴于此行为，建议仔细编写 `catch` 和 `finally` 子句，避免引入新的异常。</span><span class="sxs-lookup"><span data-stu-id="cfa34-320">This behavior is the reason it's recommended to write `catch` and `finally` clauses carefully, to avoid introducing new exceptions.</span></span>

## <a name="index-initializers"></a><span data-ttu-id="cfa34-321">索引初始化表达式</span><span class="sxs-lookup"><span data-stu-id="cfa34-321">Index initializers</span></span>

<span data-ttu-id="cfa34-322">索引初始值设定项是提高集合初始值设定项与索引用途一致性的两个功能之一。</span><span class="sxs-lookup"><span data-stu-id="cfa34-322">*Index Initializers* is one of two features that make collection initializers more consistent with index usage.</span></span> <span data-ttu-id="cfa34-323">在早期版本的 C# 中，只能将集合初始值设定项用于序列样式集合，包括在键值对周围添加括号而得到 <xref:System.Collections.Generic.Dictionary%602>：</span><span class="sxs-lookup"><span data-stu-id="cfa34-323">In earlier releases of C#, you could use *collection initializers* only with sequence style collections, including <xref:System.Collections.Generic.Dictionary%602> by adding braces around key and value pairs:</span></span>

[!code-csharp[ListInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#ListInitializer)]

<span data-ttu-id="cfa34-324">现在，可以将它们用于 <xref:System.Collections.Generic.Dictionary%602> 集合及类似的类型：</span><span class="sxs-lookup"><span data-stu-id="cfa34-324">Now, you can use them with <xref:System.Collections.Generic.Dictionary%602> collections and similar types.</span></span> <span data-ttu-id="cfa34-325">新语法支持使用索引分配到集合中：</span><span class="sxs-lookup"><span data-stu-id="cfa34-325">The new syntax supports assignment using an index into the collection:</span></span>

[!code-csharp[DictionaryInitializer](../../../samples/snippets/csharp/new-in-6/initializers.cs#DictionaryInitializer)]

<span data-ttu-id="cfa34-326">此功能意味着，可以使用与多个版本中已有的序列容器语法类似的语法初始化关联容器。</span><span class="sxs-lookup"><span data-stu-id="cfa34-326">This feature means that associative containers can be initialized using syntax similar to what's been in place for sequence containers for several versions.</span></span>

## <a name="extension-add-methods-in-collection-initializers"></a><span data-ttu-id="cfa34-327">集合初始值设定项中的扩展 `Add` 方法</span><span class="sxs-lookup"><span data-stu-id="cfa34-327">Extension `Add` methods in collection initializers</span></span>

<span data-ttu-id="cfa34-328">使集合初始化更容易的另一个功能是对 `Add` 方法使用扩展方法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-328">Another feature that makes collection initialization easier is the ability to use an *extension method* for the `Add` method.</span></span> <span data-ttu-id="cfa34-329">添加此功能的目的是进行 Visual Basic 的奇偶校验。</span><span class="sxs-lookup"><span data-stu-id="cfa34-329">This feature was added for parity with Visual Basic.</span></span> 

<span data-ttu-id="cfa34-330">如果自定义集合类的方法具有通过语义方式添加新项的名称，则此功能非常有用。</span><span class="sxs-lookup"><span data-stu-id="cfa34-330">The feature is most useful when you have a custom collection class that has a method with a different name to semantically add new items.</span></span>

<span data-ttu-id="cfa34-331">例如，请思考以下学生集合：</span><span class="sxs-lookup"><span data-stu-id="cfa34-331">For example, consider a collection of students like this:</span></span>

[!code-csharp[Enrollment](../../../samples/snippets/csharp/new-in-6/enrollment.cs#Enrollment)]

<span data-ttu-id="cfa34-332">`Enroll` 方法会添加一个学生。</span><span class="sxs-lookup"><span data-stu-id="cfa34-332">The `Enroll` method adds a student.</span></span> <span data-ttu-id="cfa34-333">但它不遵循 `Add` 模式。</span><span class="sxs-lookup"><span data-stu-id="cfa34-333">But it doesn't follow the `Add` pattern.</span></span>
<span data-ttu-id="cfa34-334">在以前的 C# 版本中，你不能对 `Enrollment` 对象使用集合初始值设定项：</span><span class="sxs-lookup"><span data-stu-id="cfa34-334">In previous versions of C#, you could not use collection initializers with an `Enrollment` object:</span></span>

[!code-csharp[InitializeEnrollment](../../../samples/snippets/csharp/new-in-6/classList.cs#InitializeEnrollment)]

<span data-ttu-id="cfa34-335">现在可以，但前提是你创建将 `Add` 映射到 `Enroll` 的扩展方法：</span><span class="sxs-lookup"><span data-stu-id="cfa34-335">Now you can, but only if you create an extension method that maps `Add` to `Enroll`:</span></span>

[!code-csharp[ExtensionAdd](../../../samples/snippets/csharp/new-in-6/classList.cs#ExtensionAdd)]

<span data-ttu-id="cfa34-336">你对此功能执行的操作是通过创建扩展方法，将把项添加到集合的任何方法映射到一个名为 `Add` 方法。</span><span class="sxs-lookup"><span data-stu-id="cfa34-336">What you are doing with this feature is to map whatever method adds items to a collection to a method named `Add` by creating an extension method.</span></span>

## <a name="improved-overload-resolution"></a><span data-ttu-id="cfa34-337">改进了重载解析</span><span class="sxs-lookup"><span data-stu-id="cfa34-337">Improved overload resolution</span></span>

<span data-ttu-id="cfa34-338">你可能不会注意到这最后一项功能。</span><span class="sxs-lookup"><span data-stu-id="cfa34-338">This last feature is one you probably won't notice.</span></span> <span data-ttu-id="cfa34-339">在以前的一些构造中，以前版本的 C# 编译器可能会发现涉及 lambda 表达式的一些方法不明确。</span><span class="sxs-lookup"><span data-stu-id="cfa34-339">There were constructs where the previous version of the C# compiler may have found some method calls involving lambda expressions ambiguous.</span></span> <span data-ttu-id="cfa34-340">请考虑此方法：</span><span class="sxs-lookup"><span data-stu-id="cfa34-340">Consider this method:</span></span>

[!code-csharp[AsyncMethod](../../../samples/snippets/csharp/new-in-6/overloads.cs#AsyncMethod)]

<span data-ttu-id="cfa34-341">在早期版本的 C# 中，使用方法组语法调用该方法将失败：</span><span class="sxs-lookup"><span data-stu-id="cfa34-341">In earlier versions of C#, calling that method using the method group syntax would fail:</span></span>

[!code-csharp[MethodGroup](../../../samples/snippets/csharp/new-in-6/overloads.cs#MethodGroup)]
 
<span data-ttu-id="cfa34-342">早期的编译器无法正确区分 `Task.Run(Action)` 和 `Task.Run(Func<Task>())`。</span><span class="sxs-lookup"><span data-stu-id="cfa34-342">The earlier compiler could not distinguish correctly between `Task.Run(Action)` and `Task.Run(Func<Task>())`.</span></span> <span data-ttu-id="cfa34-343">在早期版本中，需要使用 lambda 表达式作为参数：</span><span class="sxs-lookup"><span data-stu-id="cfa34-343">In previous versions, you'd need to use a lambda expression as an argument:</span></span>

[!code-csharp[Lambda](../../../samples/snippets/csharp/new-in-6/overloads.cs#Lambda)]

<span data-ttu-id="cfa34-344">C# 6 编译器正确地确定 `Task.Run(Func<Task>())` 是更好的选择。</span><span class="sxs-lookup"><span data-stu-id="cfa34-344">The C# 6 compiler correctly determines that `Task.Run(Func<Task>())` is a better choice.</span></span>

### <a name="deterministic-compiler-output"></a><span data-ttu-id="cfa34-345">确定性的编译器选项</span><span class="sxs-lookup"><span data-stu-id="cfa34-345">Deterministic compiler output</span></span>

<span data-ttu-id="cfa34-346">`-deterministic` 选项指示编译器为同一源文件的后续编译生成完全相同的输出程序集。</span><span class="sxs-lookup"><span data-stu-id="cfa34-346">The `-deterministic` option instructs the compiler to produce a byte-for-byte identical output assembly for successive compilations of the same source files.</span></span>

<span data-ttu-id="cfa34-347">默认情况下，每个编译都生成唯一的输出内容。</span><span class="sxs-lookup"><span data-stu-id="cfa34-347">By default, every compilation produces unique output on each compilation.</span></span> <span data-ttu-id="cfa34-348">编译器添加一个时间戳和一个随机生成的 GUID。</span><span class="sxs-lookup"><span data-stu-id="cfa34-348">The compiler adds a timestamp, and a GUID generated from random numbers.</span></span> <span data-ttu-id="cfa34-349">如果想按字节比较输出以确保各项生成之间的一致性，请使用此选项。</span><span class="sxs-lookup"><span data-stu-id="cfa34-349">You use this option if you want to compare the byte-for-byte output to ensure consistency across builds.</span></span>

<span data-ttu-id="cfa34-350">有关详细信息，请参阅 [-deterministic 编译器选项](../language-reference/compiler-options/deterministic-compiler-option.md)文章。</span><span class="sxs-lookup"><span data-stu-id="cfa34-350">For more information, see the [-deterministic compiler option](../language-reference/compiler-options/deterministic-compiler-option.md) article.</span></span>
