---
title: sealed 修饰符 - C# 参考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: d86f3ea7b9ee2a7c511119d9b7c3e52f44bd5e6a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634077"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="bb85d-102">sealed（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="bb85d-102">sealed (C# Reference)</span></span>

<span data-ttu-id="bb85d-103">应用于某个类时，`sealed` 修饰符可阻止其他类继承自该类。</span><span class="sxs-lookup"><span data-stu-id="bb85d-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="bb85d-104">在下面的示例中，类 `B` 继承自类 `A`，但没有类可以继承自类 `B`。</span><span class="sxs-lookup"><span data-stu-id="bb85d-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="bb85d-105">还可以对替代基类中的虚方法或属性的方法或属性使用 `sealed` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="bb85d-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="bb85d-106">这使你可以允许类派生自你的类并防止它们替代特定虚方法或属性。</span><span class="sxs-lookup"><span data-stu-id="bb85d-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="bb85d-107">示例</span><span class="sxs-lookup"><span data-stu-id="bb85d-107">Example</span></span>

<span data-ttu-id="bb85d-108">在下面的示例中，`Z` 继承自 `Y`，但 `Z` 无法替代在 `X` 中声明并在 `Y` 中密封的虚函数 `F`。</span><span class="sxs-lookup"><span data-stu-id="bb85d-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="bb85d-109">在类中定义新方法或属性时，可以通过不将它们声明为[虚拟](virtual.md)，来防止派生类替代它们。</span><span class="sxs-lookup"><span data-stu-id="bb85d-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="bb85d-110">将 [abstract](abstract.md) 修饰符与密封类结合使用是错误的，因为抽象类必须由提供抽象方法或属性的实现的类来继承。</span><span class="sxs-lookup"><span data-stu-id="bb85d-110">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="bb85d-111">应用于方法或属性时，`sealed` 修饰符必须始终与 [override](override.md) 结合使用。</span><span class="sxs-lookup"><span data-stu-id="bb85d-111">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="bb85d-112">因为结构是隐式密封的，所以无法继承它们。</span><span class="sxs-lookup"><span data-stu-id="bb85d-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="bb85d-113">有关详细信息，请参阅[继承](../../programming-guide/classes-and-structs/inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="bb85d-113">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="bb85d-114">有关更多示例，请参阅[抽象类、密封类及类成员](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="bb85d-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="bb85d-115">示例</span><span class="sxs-lookup"><span data-stu-id="bb85d-115">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="bb85d-116">在上面的示例中，可能会尝试使用以下语句从密封类继承：</span><span class="sxs-lookup"><span data-stu-id="bb85d-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="bb85d-117">结果是出现错误消息：</span><span class="sxs-lookup"><span data-stu-id="bb85d-117">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="c-language-specification"></a><span data-ttu-id="bb85d-118">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="bb85d-118">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="remarks"></a><span data-ttu-id="bb85d-119">备注</span><span class="sxs-lookup"><span data-stu-id="bb85d-119">Remarks</span></span>

<span data-ttu-id="bb85d-120">若要确定是否密封类、方法或属性，通常应考虑以下两点：</span><span class="sxs-lookup"><span data-stu-id="bb85d-120">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="bb85d-121">派生类通过可以自定义类而可能获得的潜在好处。</span><span class="sxs-lookup"><span data-stu-id="bb85d-121">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="bb85d-122">派生类可能采用使它们无法再正常工作或按预期工作的方式来修改类的可能性。</span><span class="sxs-lookup"><span data-stu-id="bb85d-122">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb85d-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="bb85d-123">See also</span></span>

- [<span data-ttu-id="bb85d-124">C# 参考</span><span class="sxs-lookup"><span data-stu-id="bb85d-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bb85d-125">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="bb85d-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bb85d-126">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="bb85d-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bb85d-127">静态类和静态类成员</span><span class="sxs-lookup"><span data-stu-id="bb85d-127">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="bb85d-128">抽象类、密封类及类成员</span><span class="sxs-lookup"><span data-stu-id="bb85d-128">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="bb85d-129">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="bb85d-129">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="bb85d-130">修饰符</span><span class="sxs-lookup"><span data-stu-id="bb85d-130">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="bb85d-131">override</span><span class="sxs-lookup"><span data-stu-id="bb85d-131">override</span></span>](override.md)
- [<span data-ttu-id="bb85d-132">virtual</span><span class="sxs-lookup"><span data-stu-id="bb85d-132">virtual</span></span>](virtual.md)
