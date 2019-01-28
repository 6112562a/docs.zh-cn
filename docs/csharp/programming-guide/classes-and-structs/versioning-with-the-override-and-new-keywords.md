---
title: 使用 Override 和 New 关键字进行版本控制 - C# 编程指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, versioning
- C# language, override and new
ms.assetid: 88247d07-bd0d-49e9-a619-45ccbbfdf0c5
ms.openlocfilehash: 5c83ce79bede1ee4e5752ac0b1dcf9647df1f36c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555981"
---
# <a name="versioning-with-the-override-and-new-keywords-c-programming-guide"></a><span data-ttu-id="08549-102">使用 Override 和 New 关键字进行版本控制（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="08549-102">Versioning with the Override and New Keywords (C# Programming Guide)</span></span>
<span data-ttu-id="08549-103">C# 语言经过专门设计，以便不同库中的[基类](../../../csharp/language-reference/keywords/base.md)与派生类之间的版本控制可以不断向前发展，同时保持后向兼容。</span><span class="sxs-lookup"><span data-stu-id="08549-103">The C# language is designed so that versioning between [base](../../../csharp/language-reference/keywords/base.md) and derived classes in different libraries can evolve and maintain backward compatibility.</span></span> <span data-ttu-id="08549-104">这具有多方面的意义。例如，这意味着在基[类](../../../csharp/language-reference/keywords/class.md)中引入与派生类中的某个成员具有相同名称的新成员在 C# 中是完全支持的，不会导致意外行为。</span><span class="sxs-lookup"><span data-stu-id="08549-104">This means, for example, that the introduction of a new member in a base [class](../../../csharp/language-reference/keywords/class.md) with the same name as a member in a derived class is completely supported by C# and does not lead to unexpected behavior.</span></span> <span data-ttu-id="08549-105">它还意味着类必须显式声明某方法是要替代一个继承方法，还是本身就是一个隐藏具有类似名称的继承方法的新方法。</span><span class="sxs-lookup"><span data-stu-id="08549-105">It also means that a class must explicitly state whether a method is intended to override an inherited method, or whether a method is a new method that hides a similarly named inherited method.</span></span>  
  
 <span data-ttu-id="08549-106">在 C# 中，派生类可以包含与基类方法同名的方法。</span><span class="sxs-lookup"><span data-stu-id="08549-106">In C#, derived classes can contain methods with the same name as base class methods.</span></span>  
  
-   <span data-ttu-id="08549-107">基类方法必须定义为 [virtual](../../../csharp/language-reference/keywords/virtual.md)。</span><span class="sxs-lookup"><span data-stu-id="08549-107">The base class method must be defined [virtual](../../../csharp/language-reference/keywords/virtual.md).</span></span>  
  
-   <span data-ttu-id="08549-108">如果派生类中的方法前面没有 [new](../../../csharp/language-reference/keywords/new.md) 或 [override](../../../csharp/language-reference/keywords/override.md) 关键字，则编译器将发出警告，该方法将如同存在 `new` 关键字一样执行操作。</span><span class="sxs-lookup"><span data-stu-id="08549-108">If the method in the derived class is not preceded by [new](../../../csharp/language-reference/keywords/new.md) or [override](../../../csharp/language-reference/keywords/override.md) keywords, the compiler will issue a warning and the method will behave as if the `new` keyword were present.</span></span>  
  
-   <span data-ttu-id="08549-109">如果派生类中的方法前面带有 `new` 关键字，则该方法被定义为独立于基类中的方法。</span><span class="sxs-lookup"><span data-stu-id="08549-109">If the method in the derived class is preceded with the `new` keyword, the method is defined as being independent of the method in the base class.</span></span>  
  
-   <span data-ttu-id="08549-110">如果派生类中的方法前面带有 `override` 关键字，则派生类的对象将调用该方法，而不是调用基类方法。</span><span class="sxs-lookup"><span data-stu-id="08549-110">If the method in the derived class is preceded with the `override` keyword, objects of the derived class will call that method instead of the base class method.</span></span>  
  
-   <span data-ttu-id="08549-111">可以从派生类中使用 `base` 关键字调用基类方法。</span><span class="sxs-lookup"><span data-stu-id="08549-111">The base class method can be called from within the derived class using the `base` keyword.</span></span>  
  
-   <span data-ttu-id="08549-112">`override`、`virtual` 和 `new` 关键字还可以用于属性、索引器和事件中。</span><span class="sxs-lookup"><span data-stu-id="08549-112">The `override`, `virtual`, and `new` keywords can also be applied to properties, indexers, and events.</span></span>  
  
 <span data-ttu-id="08549-113">默认情况下，C# 方法为非虚方法。</span><span class="sxs-lookup"><span data-stu-id="08549-113">By default, C# methods are not virtual.</span></span> <span data-ttu-id="08549-114">如果某个方法被声明为虚方法，则继承该方法的任何类都可以实现它自己的版本。</span><span class="sxs-lookup"><span data-stu-id="08549-114">If a method is declared as virtual, any class inheriting the method can implement its own version.</span></span> <span data-ttu-id="08549-115">若要使方法成为虚方法，需要在基类的方法声明中使用 `virtual` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="08549-115">To make a method virtual, the `virtual` modifier is used in the method declaration of the base class.</span></span> <span data-ttu-id="08549-116">然后，派生类可以使用 `override` 关键字替代基虚方法，或使用 `new` 关键字隐藏基类中的虚方法。</span><span class="sxs-lookup"><span data-stu-id="08549-116">The derived class can then override the base virtual method by using the `override` keyword or hide the virtual method in the base class by using the `new` keyword.</span></span> <span data-ttu-id="08549-117">如果 `override` 关键字和 `new` 关键字均未指定，编译器将发出警告，并且派生类中的方法将隐藏基类中的方法。</span><span class="sxs-lookup"><span data-stu-id="08549-117">If neither the `override` keyword nor the `new` keyword is specified, the compiler will issue a warning and the method in the derived class will hide the method in the base class.</span></span>  
  
 <span data-ttu-id="08549-118">为了在实践中演示上述情况，暂时假定公司 A 创建了一个名为 `GraphicsClass` 的类，程序将使用此类。</span><span class="sxs-lookup"><span data-stu-id="08549-118">To demonstrate this in practice, assume for a moment that Company A has created a class named `GraphicsClass`, which your program uses.</span></span> <span data-ttu-id="08549-119">`GraphicsClass` 如下所示：</span><span class="sxs-lookup"><span data-stu-id="08549-119">The following is `GraphicsClass`:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#27](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_1.cs)]  
  
 <span data-ttu-id="08549-120">公司使用此类，并且你在添加新方法时将其用于派生自己的类：</span><span class="sxs-lookup"><span data-stu-id="08549-120">Your company uses this class, and you use it to derive your own class, adding a new method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#28](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_2.cs)]  
  
 <span data-ttu-id="08549-121">你的应用程序运行正常，未出现问题，直到公司 A 发布了 `GraphicsClass` 的新版本，类似于以下代码：</span><span class="sxs-lookup"><span data-stu-id="08549-121">Your application is used without problems, until Company A releases a new version of `GraphicsClass`, which resembles the following code:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#29](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_3.cs)]  
  
 <span data-ttu-id="08549-122">现在，`GraphicsClass` 的新版本中包含一个名为 `DrawRectangle` 的方法。</span><span class="sxs-lookup"><span data-stu-id="08549-122">The new version of `GraphicsClass` now contains a method named `DrawRectangle`.</span></span> <span data-ttu-id="08549-123">开始时，没有出现任何问题。</span><span class="sxs-lookup"><span data-stu-id="08549-123">Initially, nothing occurs.</span></span> <span data-ttu-id="08549-124">新版本仍然与旧版本保持二进制兼容。</span><span class="sxs-lookup"><span data-stu-id="08549-124">The new version is still binary compatible with the old version.</span></span> <span data-ttu-id="08549-125">已经部署的任何软件都将继续正常工作，即使新类已安装到这些计算机系统上。</span><span class="sxs-lookup"><span data-stu-id="08549-125">Any software that you have deployed will continue to work, even if the new class is installed on those computer systems.</span></span> <span data-ttu-id="08549-126">在你的派生类中，对方法 `DrawRectangle` 的任何现有调用将继续引用你的版本。</span><span class="sxs-lookup"><span data-stu-id="08549-126">Any existing calls to the method `DrawRectangle` will continue to reference your version, in your derived class.</span></span>  
  
 <span data-ttu-id="08549-127">但是，一旦你使用 `GraphicsClass` 的新版本重新编译应用程序，就会收到来自编译器的警告 CS0108。</span><span class="sxs-lookup"><span data-stu-id="08549-127">However, as soon as you recompile your application by using the new version of `GraphicsClass`, you will receive a warning from the compiler, CS0108.</span></span> <span data-ttu-id="08549-128">此警告提示，必须考虑你所期望的 `DrawRectangle` 方法在应用程序中的工作方式。</span><span class="sxs-lookup"><span data-stu-id="08549-128">This warning informs you that you have to consider how you want your `DrawRectangle` method to behave in your application.</span></span>  
  
 <span data-ttu-id="08549-129">如果需要自己的方法替代新的基类方法，请使用 `override` 关键字：</span><span class="sxs-lookup"><span data-stu-id="08549-129">If you want your method to override the new base class method, use the `override` keyword:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#30](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_4.cs)]  
  
 <span data-ttu-id="08549-130">`override` 关键字可确保派生自 `YourDerivedGraphicsClass` 的任何对象都将使用 `DrawRectangle` 的派生类版本。</span><span class="sxs-lookup"><span data-stu-id="08549-130">The `override` keyword makes sure that any objects derived from `YourDerivedGraphicsClass` will use the derived class version of `DrawRectangle`.</span></span> <span data-ttu-id="08549-131">派生自 `YourDerivedGraphicsClass` 的对象仍可以使用 base 关键字访问 `DrawRectangle` 的基类版本：</span><span class="sxs-lookup"><span data-stu-id="08549-131">Objects derived from `YourDerivedGraphicsClass` can still access the base class version of `DrawRectangle` by using the base keyword:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_5.cs)]  
  
 <span data-ttu-id="08549-132">如果不需要自己的方法替代新的基类方法，则需要注意以下事项。</span><span class="sxs-lookup"><span data-stu-id="08549-132">If you do not want your method to override the new base class method, the following considerations apply.</span></span> <span data-ttu-id="08549-133">为了避免这两个方法之间发生混淆，可以重命名你的方法。</span><span class="sxs-lookup"><span data-stu-id="08549-133">To avoid confusion between the two methods, you can rename your method.</span></span> <span data-ttu-id="08549-134">这可能很耗费时间且容易出错，而且在某些情况下并不可行。</span><span class="sxs-lookup"><span data-stu-id="08549-134">This can be time-consuming and error-prone, and just not practical in some cases.</span></span> <span data-ttu-id="08549-135">但是，如果项目相对较小，则可以使用 Visual Studio 的重构选项来重命名方法。</span><span class="sxs-lookup"><span data-stu-id="08549-135">However, if your project is relatively small, you can use Visual Studio's Refactoring options to rename the method.</span></span> <span data-ttu-id="08549-136">有关详细信息，请参阅[重构类和类型（类设计器）](/visualstudio/ide/refactoring-classes-and-types-class-designer)。</span><span class="sxs-lookup"><span data-stu-id="08549-136">For more information, see [Refactoring Classes and Types (Class Designer)](/visualstudio/ide/refactoring-classes-and-types-class-designer).</span></span>  
  
 <span data-ttu-id="08549-137">或者，也可以通过在派生类定义中使用关键字 `new` 来防止出现该警告：</span><span class="sxs-lookup"><span data-stu-id="08549-137">Alternatively, you can prevent the warning by using the keyword `new` in your derived class definition:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#31](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_6.cs)]  
  
 <span data-ttu-id="08549-138">使用 `new` 关键字可告诉编译器你的定义将隐藏基类中包含的定义。</span><span class="sxs-lookup"><span data-stu-id="08549-138">Using the `new` keyword tells the compiler that your definition hides the definition that is contained in the base class.</span></span> <span data-ttu-id="08549-139">这是默认行为。</span><span class="sxs-lookup"><span data-stu-id="08549-139">This is the default behavior.</span></span>  
  
## <a name="override-and-method-selection"></a><span data-ttu-id="08549-140">替代和方法选择</span><span class="sxs-lookup"><span data-stu-id="08549-140">Override and Method Selection</span></span>  
 <span data-ttu-id="08549-141">当在类中对方法进行命名时，如果有多个方法与调用兼容（例如，存在两种同名的方法，并且其参数与传递的参数兼容），则 C# 编译器将选择最佳方法进行调用。</span><span class="sxs-lookup"><span data-stu-id="08549-141">When a method is named on a class, the C# compiler selects the best method to call if more than one method is compatible with the call, such as when there are two methods with the same name, and parameters that are compatible with the parameter passed.</span></span> <span data-ttu-id="08549-142">以下方法将是兼容的：</span><span class="sxs-lookup"><span data-stu-id="08549-142">The following methods would be compatible:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#32](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_7.cs)]  
  
 <span data-ttu-id="08549-143">在 `Derived` 的一个实例中调用 `DoWork` 时，C# 编译器将首先尝试使该调用与最初在 `Derived` 上声明的 `DoWork` 版本兼容。</span><span class="sxs-lookup"><span data-stu-id="08549-143">When `DoWork` is called on an instance of `Derived`, the C# compiler will first try to make the call compatible with the versions of `DoWork` declared originally on `Derived`.</span></span> <span data-ttu-id="08549-144">替代方法不被视为是在类上进行声明的，而是在基类上声明的方法的新实现。</span><span class="sxs-lookup"><span data-stu-id="08549-144">Override methods are not considered as declared on a class, they are new implementations of a method declared on a base class.</span></span> <span data-ttu-id="08549-145">仅当 C# 编译器无法将方法调用与 `Derived` 上的原始方法匹配时，才尝试将该调用与具有相同名称和兼容参数的替代方法匹配。</span><span class="sxs-lookup"><span data-stu-id="08549-145">Only if the C# compiler cannot match the method call to an original method on `Derived` will it try to match the call to an overridden method with the same name and compatible parameters.</span></span> <span data-ttu-id="08549-146">例如:</span><span class="sxs-lookup"><span data-stu-id="08549-146">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_8.cs)]  
  
 <span data-ttu-id="08549-147">由于变量 `val` 可以隐式转换为 double 类型，因此 C# 编译器将调用 `DoWork(double)`，而不是 `DoWork(int)`。</span><span class="sxs-lookup"><span data-stu-id="08549-147">Because the variable `val` can be converted to a double implicitly, the C# compiler calls `DoWork(double)` instead of `DoWork(int)`.</span></span> <span data-ttu-id="08549-148">有两种方法可以避免此情况。</span><span class="sxs-lookup"><span data-stu-id="08549-148">There are two ways to avoid this.</span></span> <span data-ttu-id="08549-149">首先，避免将新方法声明为与虚方法相同的名称。</span><span class="sxs-lookup"><span data-stu-id="08549-149">First, avoid declaring new methods with the same name as virtual methods.</span></span> <span data-ttu-id="08549-150">其次，可以通过将 `Derived` 的实例强制转换为 `Base` 来使 C# 编译器搜索基类方法列表，从而使其调用虚方法。</span><span class="sxs-lookup"><span data-stu-id="08549-150">Second, you can instruct the C# compiler to call the virtual method by making it search the base class method list by casting the instance of `Derived` to `Base`.</span></span> <span data-ttu-id="08549-151">由于是虚方法，因此将调用 `Derived` 上的 `DoWork(int)` 的实现。</span><span class="sxs-lookup"><span data-stu-id="08549-151">Because the method is virtual, the implementation of `DoWork(int)` on `Derived` will be called.</span></span> <span data-ttu-id="08549-152">例如:</span><span class="sxs-lookup"><span data-stu-id="08549-152">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#34](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/versioning-with-the-override-and-new-keywords_9.cs)]  
  
 <span data-ttu-id="08549-153">有关 `new` 和 `override` 的更多示例，请参阅[了解何时使用 Override 和 New 关键字](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="08549-153">For more examples of `new` and `override`, see [Knowing When to Use Override and New Keywords](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08549-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="08549-154">See also</span></span>

- [<span data-ttu-id="08549-155">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="08549-155">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="08549-156">类和结构</span><span class="sxs-lookup"><span data-stu-id="08549-156">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="08549-157">方法</span><span class="sxs-lookup"><span data-stu-id="08549-157">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="08549-158">继承</span><span class="sxs-lookup"><span data-stu-id="08549-158">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
