---
title: enum 关键字 - C# 参考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- enum
- enum_CSharpKeyword
helpviewer_keywords:
- enum keyword [C#]
ms.assetid: bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c
ms.openlocfilehash: e33877d2a5e79866bbef12cd9fec5cb11b044240
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433870"
---
# <a name="enum-c-reference"></a><span data-ttu-id="03981-102">enum（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="03981-102">enum (C# Reference)</span></span>

<span data-ttu-id="03981-103">`enum` 关键字用于声明枚举，一种包含一组被称为枚举数列表的已命名常数的不同类型。</span><span class="sxs-lookup"><span data-stu-id="03981-103">The `enum` keyword is used to declare an enumeration, a distinct type that consists of a set of named constants called the enumerator list.</span></span>

<span data-ttu-id="03981-104">通常最好是直接在命名空间内定义枚举，以便命名空间中的所有类都可以同样方便地访问它。</span><span class="sxs-lookup"><span data-stu-id="03981-104">Usually it is best to define an enum directly within a namespace so that all classes in the namespace can access it with equal convenience.</span></span> <span data-ttu-id="03981-105">但是，也可能会在类或结构中嵌套枚举。</span><span class="sxs-lookup"><span data-stu-id="03981-105">However, an enum can also be nested within a class or struct.</span></span>

<span data-ttu-id="03981-106">默认情况下，第一个枚举数具有值 0，并且每个连续枚举数的值将增加 1。</span><span class="sxs-lookup"><span data-stu-id="03981-106">By default, the first enumerator has the value 0, and the value of each successive enumerator is increased by 1.</span></span> <span data-ttu-id="03981-107">例如，在以下枚举中， `Sat` 的值为 `0`， `Sun` 的值为 `1`， `Mon` 的值为 `2`，依次类推。</span><span class="sxs-lookup"><span data-stu-id="03981-107">For example, in the following enumeration, `Sat` is `0`, `Sun` is `1`, `Mon` is `2`, and so forth.</span></span>

```csharp
enum Day {Sat, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="03981-108">枚举数可以使用初始值设定项来替代默认值，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="03981-108">Enumerators can use initializers to override the default values, as shown in the following example.</span></span>

```csharp
enum Day {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="03981-109">在此枚举中，强制元素的序列从 `1` 开始，而不是 `0`。</span><span class="sxs-lookup"><span data-stu-id="03981-109">In this enumeration, the sequence of elements is forced to start from `1` instead of `0`.</span></span> <span data-ttu-id="03981-110">但建议包括一个值为 0 的常量。</span><span class="sxs-lookup"><span data-stu-id="03981-110">However, including a constant that has the value of 0 is recommended.</span></span> <span data-ttu-id="03981-111">有关详细信息，请参阅[枚举类型](../../programming-guide/enumeration-types.md)。</span><span class="sxs-lookup"><span data-stu-id="03981-111">For more information, see [Enumeration Types](../../programming-guide/enumeration-types.md).</span></span>

<span data-ttu-id="03981-112">每个枚举类型都有一个可以为任意[整型数值类型](../builtin-types/integral-numeric-types.md)的基础类型。</span><span class="sxs-lookup"><span data-stu-id="03981-112">Every enumeration type has an underlying type, which can be any [integral numeric type](../builtin-types/integral-numeric-types.md).</span></span> <span data-ttu-id="03981-113">[char](char.md) 类型不能为枚举的基础类型。</span><span class="sxs-lookup"><span data-stu-id="03981-113">The [char](char.md) type cannot be an underlying type of an enum.</span></span> <span data-ttu-id="03981-114">枚举元素的默认基础类型是 [int](../builtin-types/integral-numeric-types.md)。若要声明另一整型的枚举（如 [byte](../builtin-types/integral-numeric-types.md)），则请在后跟该类型的标识符后使用冒号，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="03981-114">The default underlying type of enumeration elements is [int](../builtin-types/integral-numeric-types.md). To declare an enum of another integral type, such as [byte](../builtin-types/integral-numeric-types.md), use a colon after the identifier followed by the type, as shown in the following example.</span></span>

```csharp
enum Day : byte {Sat=1, Sun, Mon, Tue, Wed, Thu, Fri};
```

<span data-ttu-id="03981-115">枚举类型的变量可在基本类型范围内分配到任何值；这些值不限于已命名常数。</span><span class="sxs-lookup"><span data-stu-id="03981-115">A variable of an enumeration type can be assigned any value in the range of the underlying type; the values are not limited to the named constants.</span></span>

<span data-ttu-id="03981-116">`enum E` 的默认值是由表达式 `(E)0`生成的值。</span><span class="sxs-lookup"><span data-stu-id="03981-116">The default value of an `enum E` is the value produced by the expression `(E)0`.</span></span>

> [!NOTE]
> <span data-ttu-id="03981-117">枚举数名称中不能含有空格。</span><span class="sxs-lookup"><span data-stu-id="03981-117">An enumerator cannot contain white space in its name.</span></span>

<span data-ttu-id="03981-118">基础类型指定为每个枚举数分配多少存储空间。</span><span class="sxs-lookup"><span data-stu-id="03981-118">The underlying type specifies how much storage is allocated for each enumerator.</span></span> <span data-ttu-id="03981-119">但要将 `enum` 类型转换为整型，则必须使用显示转换。</span><span class="sxs-lookup"><span data-stu-id="03981-119">However, an explicit cast is necessary to convert from `enum` type to an integral type.</span></span> <span data-ttu-id="03981-120">例如，以下语句通过使用转换将 `Sun` 转换为 [，从而将枚举数](../builtin-types/integral-numeric-types.md) 赋值为 `enum` int `int`类型的变量。</span><span class="sxs-lookup"><span data-stu-id="03981-120">For example, the following statement assigns the enumerator `Sun` to a variable of the type [int](../builtin-types/integral-numeric-types.md) by using a cast to convert from `enum` to `int`.</span></span>

```csharp
int x = (int)Day.Sun;
```

<span data-ttu-id="03981-121">当你将 <xref:System.FlagsAttribute?displayProperty=nameWithType> 应用到包含可与按位 `OR` 运算组合的元素的枚举中时，该特性与某些工具一起使用时会影响 `enum` 的行为。</span><span class="sxs-lookup"><span data-stu-id="03981-121">When you apply <xref:System.FlagsAttribute?displayProperty=nameWithType> to an enumeration that contains elements that can be combined with a bitwise `OR` operation, the attribute affects the behavior of the `enum` when it is used with some tools.</span></span> <span data-ttu-id="03981-122">当你使用工具（如 <xref:System.Console> 类方法和表达式计算器）时，你可以注意到这些更改。</span><span class="sxs-lookup"><span data-stu-id="03981-122">You can notice these changes when you use tools such as the <xref:System.Console> class methods and the Expression Evaluator.</span></span> <span data-ttu-id="03981-123">（请参阅第三个示例。）</span><span class="sxs-lookup"><span data-stu-id="03981-123">(See the third example.)</span></span>

## <a name="robust-programming"></a><span data-ttu-id="03981-124">可靠编程</span><span class="sxs-lookup"><span data-stu-id="03981-124">Robust programming</span></span>

<span data-ttu-id="03981-125">正如任何常量一样，对枚举的各项值的所有引用在编译时都会转换为数字参数。</span><span class="sxs-lookup"><span data-stu-id="03981-125">Just as with any constant, all references to the individual values of an enum are converted to numeric literals at compile time.</span></span> <span data-ttu-id="03981-126">这可能会造成如[常量](../../programming-guide/classes-and-structs/constants.md)中所述的潜在版本问题。</span><span class="sxs-lookup"><span data-stu-id="03981-126">This can create potential versioning issues as described in [Constants](../../programming-guide/classes-and-structs/constants.md).</span></span>

<span data-ttu-id="03981-127">将其他值分配到枚举的新版本，或者在新版本中更改枚举成员的值，会导致出现相关源代码问题。</span><span class="sxs-lookup"><span data-stu-id="03981-127">Assigning additional values to new versions of enums, or changing the values of the enum members in a new version, can cause problems for dependent source code.</span></span> <span data-ttu-id="03981-128">通常在 [switch](switch.md) 语句中使用枚举值。</span><span class="sxs-lookup"><span data-stu-id="03981-128">Enum values often are used in [switch](switch.md) statements.</span></span> <span data-ttu-id="03981-129">如果已将其他元素添加到 `enum` 类型，则 switch 语句的默认部分可被意外地选中。</span><span class="sxs-lookup"><span data-stu-id="03981-129">If additional elements have been added to the `enum` type, the default section of the switch statement can be selected unexpectedly.</span></span>

<span data-ttu-id="03981-130">如果其他开发人员使用你的代码，则在将新元素添加到任何 `enum` 类型时应提供有关他们的代码应该如何响应的准则。</span><span class="sxs-lookup"><span data-stu-id="03981-130">If other developers use your code, you should provide guidelines about how their code should react if new elements are added to any `enum` types.</span></span>

## <a name="example"></a><span data-ttu-id="03981-131">示例</span><span class="sxs-lookup"><span data-stu-id="03981-131">Example</span></span>

<span data-ttu-id="03981-132">在下面的示例中，已声明枚举 `Day`。</span><span class="sxs-lookup"><span data-stu-id="03981-132">In the following example, an enumeration, `Day`, is declared.</span></span> <span data-ttu-id="03981-133">已将两个枚举数显式转换为整数，并赋值为整数变量。</span><span class="sxs-lookup"><span data-stu-id="03981-133">Two enumerators are explicitly converted to integer and assigned to integer variables.</span></span>

[!code-csharp[csrefKeywordsTypes#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#10)]

## <a name="example"></a><span data-ttu-id="03981-134">示例</span><span class="sxs-lookup"><span data-stu-id="03981-134">Example</span></span>

<span data-ttu-id="03981-135">以下示例中，使用基类型选项来声明其成员是 `enum` 类型的 `long`。</span><span class="sxs-lookup"><span data-stu-id="03981-135">In the following example, the base-type option is used to declare an `enum` whose members are of type `long`.</span></span> <span data-ttu-id="03981-136">请注意，即使该枚举的基础类型是 `long`，仍然需通过使用转换将枚举成员显式转换为类型 `long` 。</span><span class="sxs-lookup"><span data-stu-id="03981-136">Notice that even though the underlying type of the enumeration is `long`, the enumeration members still must be explicitly converted to type `long` by using a cast.</span></span>

[!code-csharp[csrefKeywordsTypes#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#11)]

## <a name="example"></a><span data-ttu-id="03981-137">示例</span><span class="sxs-lookup"><span data-stu-id="03981-137">Example</span></span>

<span data-ttu-id="03981-138">下面的代码示例说明了 <xref:System.FlagsAttribute?displayProperty=nameWithType> 声明中 `enum` 特性的使用和作用。</span><span class="sxs-lookup"><span data-stu-id="03981-138">The following code example illustrates the use and effect of the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute on an `enum` declaration.</span></span>

[!code-csharp[csrefKeywordsTypes#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#12)]

## <a name="comments"></a><span data-ttu-id="03981-139">注释</span><span class="sxs-lookup"><span data-stu-id="03981-139">Comments</span></span>

<span data-ttu-id="03981-140">如果删除 `Flags`，则示例将显示以下值：</span><span class="sxs-lookup"><span data-stu-id="03981-140">If you remove `Flags`, the example displays the following values:</span></span>

`5`

`5`

## <a name="c-language-specification"></a><span data-ttu-id="03981-141">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="03981-141">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="03981-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="03981-142">See also</span></span>

- [<span data-ttu-id="03981-143">C# 参考</span><span class="sxs-lookup"><span data-stu-id="03981-143">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="03981-144">枚举类型</span><span class="sxs-lookup"><span data-stu-id="03981-144">Enumeration Types</span></span>](../../programming-guide/enumeration-types.md)
- [<span data-ttu-id="03981-145">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="03981-145">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="03981-146">整型类型</span><span class="sxs-lookup"><span data-stu-id="03981-146">Integral types</span></span>](../../../csharp/language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="03981-147">内置类型表</span><span class="sxs-lookup"><span data-stu-id="03981-147">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="03981-148">隐式数值转换表</span><span class="sxs-lookup"><span data-stu-id="03981-148">Implicit Numeric Conversions Table</span></span>](implicit-numeric-conversions-table.md)
- [<span data-ttu-id="03981-149">显式数值转换表</span><span class="sxs-lookup"><span data-stu-id="03981-149">Explicit Numeric Conversions Table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="03981-150">枚举命名约定</span><span class="sxs-lookup"><span data-stu-id="03981-150">Enum Naming Conventions</span></span>](../../../standard/design-guidelines/names-of-classes-structs-and-interfaces.md#naming-enumerations)
