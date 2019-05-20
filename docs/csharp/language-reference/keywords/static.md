---
title: static 修饰符 - C# 参考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: b288e57d9241e294a0fa18edafe72eec675327a7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633192"
---
# <a name="static-c-reference"></a><span data-ttu-id="6ea1a-102">static（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="6ea1a-102">static (C# Reference)</span></span>

<span data-ttu-id="6ea1a-103">使用 `static` 修饰符可声明属于类型本身而不是属于特定对象的静态成员。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="6ea1a-104">`static` 修饰符可用于类、字段、方法、属性、运算符、事件和构造函数，但不能用于索引器、终结器或类以外的类型。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="6ea1a-105">有关详细信息，请参阅[静态类和静态类成员](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-105">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="6ea1a-106">示例</span><span class="sxs-lookup"><span data-stu-id="6ea1a-106">Example</span></span>

<span data-ttu-id="6ea1a-107">下面的类声明为 `static` 并且只含 `static` 方法：</span><span class="sxs-lookup"><span data-stu-id="6ea1a-107">The following class is declared as `static` and contains only `static` methods:</span></span>

[!code-csharp[csrefKeywordsModifiers#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#18)]

<span data-ttu-id="6ea1a-108">常量或类型声明是隐式的静态成员。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-108">A constant or type declaration is implicitly a static member.</span></span>

<span data-ttu-id="6ea1a-109">不能通过实例引用静态成员。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-109">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="6ea1a-110">然而，可以通过类型名称引用它。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-110">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="6ea1a-111">例如，请考虑以下类：</span><span class="sxs-lookup"><span data-stu-id="6ea1a-111">For example, consider the following class:</span></span>

[!code-csharp[csrefKeywordsModifiers#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#19)]

<span data-ttu-id="6ea1a-112">若要引用静态成员 `x`，除非可从相同范围访问该成员，否则请使用完全限定的名称 `MyBaseC.MyStruct.x`：</span><span class="sxs-lookup"><span data-stu-id="6ea1a-112">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>

```csharp
Console.WriteLine(MyBaseC.MyStruct.x);
```

<span data-ttu-id="6ea1a-113">尽管类的实例包含该类的所有实例字段的单独副本，但每个静态字段只有一个副本。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-113">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>

<span data-ttu-id="6ea1a-114">不可以使用 [this](this.md) 引用静态方法或属性访问器。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-114">It is not possible to use [this](this.md) to reference static methods or property accessors.</span></span>

<span data-ttu-id="6ea1a-115">如果 `static` 关键字应用于类，则类的所有成员都必须是静态的。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-115">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>

<span data-ttu-id="6ea1a-116">类和静态类可以包含静态构造函数。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-116">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="6ea1a-117">在程序开始和实例化类之间的某个时刻调用静态构造函数。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-117">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="6ea1a-118">`static` 关键字比用于 C++ 中时受到的限制更多。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-118">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="6ea1a-119">若要与 C++ 关键字进行比较，请参阅 [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static)（存储类 (C++)）。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-119">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>

<span data-ttu-id="6ea1a-120">若要演示静态成员，请考虑表示公司员工的类。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-120">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="6ea1a-121">假定此类包含计数员工的方法和存储员工人数的字段。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-121">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="6ea1a-122">方法和字段均不属于任何实例员工。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-122">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="6ea1a-123">而属于公司类。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-123">Instead they belong to the company class.</span></span> <span data-ttu-id="6ea1a-124">因此，它们应声明为类的静态成员。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-124">Therefore, they should be declared as static members of the class.</span></span>

## <a name="example"></a><span data-ttu-id="6ea1a-125">示例</span><span class="sxs-lookup"><span data-stu-id="6ea1a-125">Example</span></span>

<span data-ttu-id="6ea1a-126">此示例读取新员工的姓名和 ID，员工计数器按 1 递增，并显示新员工信息和新员工人数。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-126">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="6ea1a-127">为简单起见，此程序从键盘读取员工的当前人数。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-127">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="6ea1a-128">在实际应用程序中，应从文件读取该信息。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-128">In a real application, this information should be read from a file.</span></span>

[!code-csharp[csrefKeywordsModifiers#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#20)]  

## <a name="example"></a><span data-ttu-id="6ea1a-129">示例</span><span class="sxs-lookup"><span data-stu-id="6ea1a-129">Example</span></span>

<span data-ttu-id="6ea1a-130">此示例显示，尽管可以使用尚未声明的其他静态字段来初始化某个静态字段，但除非向该静态字段显式分配值，否则不会定义该结果。</span><span class="sxs-lookup"><span data-stu-id="6ea1a-130">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>

[!code-csharp[csrefKeywordsModifiers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#21)]  

## <a name="c-language-specification"></a><span data-ttu-id="6ea1a-131">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="6ea1a-131">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6ea1a-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="6ea1a-132">See also</span></span>

- [<span data-ttu-id="6ea1a-133">C# 参考</span><span class="sxs-lookup"><span data-stu-id="6ea1a-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6ea1a-134">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="6ea1a-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6ea1a-135">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="6ea1a-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6ea1a-136">修饰符</span><span class="sxs-lookup"><span data-stu-id="6ea1a-136">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="6ea1a-137">静态类和静态类成员</span><span class="sxs-lookup"><span data-stu-id="6ea1a-137">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
