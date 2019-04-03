---
title: Enum 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: fa97a374d4570e014222bf44844271b3394453da
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830066"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="4152e-102">Enum 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4152e-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="4152e-103">声明枚举并定义其成员的值。</span><span class="sxs-lookup"><span data-stu-id="4152e-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4152e-104">语法</span><span class="sxs-lookup"><span data-stu-id="4152e-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="4152e-105">部件</span><span class="sxs-lookup"><span data-stu-id="4152e-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="4152e-106">可选。</span><span class="sxs-lookup"><span data-stu-id="4152e-106">Optional.</span></span> <span data-ttu-id="4152e-107">应用于此枚举的属性列表。</span><span class="sxs-lookup"><span data-stu-id="4152e-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="4152e-108">必须将[属性列表](../../../visual-basic/language-reference/statements/attribute-list.md)括进尖括号 ("`<`"和"`>`")。</span><span class="sxs-lookup"><span data-stu-id="4152e-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="4152e-109"><xref:System.FlagsAttribute>特性指示实例的枚举值可以包含多个枚举成员，并且每个成员表示的枚举值中的位字段。</span><span class="sxs-lookup"><span data-stu-id="4152e-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="4152e-110">可选。</span><span class="sxs-lookup"><span data-stu-id="4152e-110">Optional.</span></span> <span data-ttu-id="4152e-111">指定哪些代码可以访问此枚举。</span><span class="sxs-lookup"><span data-stu-id="4152e-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="4152e-112">可以是以下各项之一：</span><span class="sxs-lookup"><span data-stu-id="4152e-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="4152e-113">Public</span><span class="sxs-lookup"><span data-stu-id="4152e-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="4152e-114">Protected</span><span class="sxs-lookup"><span data-stu-id="4152e-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="4152e-115">Friend</span><span class="sxs-lookup"><span data-stu-id="4152e-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="4152e-116">Private</span><span class="sxs-lookup"><span data-stu-id="4152e-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="4152e-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="4152e-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)
    
    - [<span data-ttu-id="4152e-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="4152e-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     <span data-ttu-id="4152e-119">可选。</span><span class="sxs-lookup"><span data-stu-id="4152e-119">Optional.</span></span> <span data-ttu-id="4152e-120">指定此枚举重新声明并隐藏具有相同名称的编程元素或在基类中的重载元素集。</span><span class="sxs-lookup"><span data-stu-id="4152e-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="4152e-121">您可以指定[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)不上的任何成员，而仅在该枚举本身上。</span><span class="sxs-lookup"><span data-stu-id="4152e-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="4152e-122">必需。</span><span class="sxs-lookup"><span data-stu-id="4152e-122">Required.</span></span> <span data-ttu-id="4152e-123">枚举的名称。</span><span class="sxs-lookup"><span data-stu-id="4152e-123">Name of the enumeration.</span></span> <span data-ttu-id="4152e-124">有关有效的名称的信息，请参阅[声明的元素名称](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="4152e-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="4152e-125">可选。</span><span class="sxs-lookup"><span data-stu-id="4152e-125">Optional.</span></span> <span data-ttu-id="4152e-126">枚举及其所有成员的数据类型。</span><span class="sxs-lookup"><span data-stu-id="4152e-126">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="4152e-127">必需。</span><span class="sxs-lookup"><span data-stu-id="4152e-127">Required.</span></span> <span data-ttu-id="4152e-128">此语句中声明的成员常量的列表。</span><span class="sxs-lookup"><span data-stu-id="4152e-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="4152e-129">在各个源代码行上显示多个成员。</span><span class="sxs-lookup"><span data-stu-id="4152e-129">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="4152e-130">每个`member`具有以下语法和部分： `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="4152e-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="4152e-131">部件</span><span class="sxs-lookup"><span data-stu-id="4152e-131">Part</span></span>|<span data-ttu-id="4152e-132">描述</span><span class="sxs-lookup"><span data-stu-id="4152e-132">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="4152e-133">必需。</span><span class="sxs-lookup"><span data-stu-id="4152e-133">Required.</span></span> <span data-ttu-id="4152e-134">此成员的名称。</span><span class="sxs-lookup"><span data-stu-id="4152e-134">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="4152e-135">可选。</span><span class="sxs-lookup"><span data-stu-id="4152e-135">Optional.</span></span> <span data-ttu-id="4152e-136">在编译时计算和分配给此成员的表达式。</span><span class="sxs-lookup"><span data-stu-id="4152e-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="4152e-137">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="4152e-137">`End` `Enum`</span></span>  
  
     <span data-ttu-id="4152e-138">终止 `Enum` 块。</span><span class="sxs-lookup"><span data-stu-id="4152e-138">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4152e-139">备注</span><span class="sxs-lookup"><span data-stu-id="4152e-139">Remarks</span></span>  
 <span data-ttu-id="4152e-140">如果有一组逻辑上彼此相关的不变值，您可以在枚举中一起定义它们。</span><span class="sxs-lookup"><span data-stu-id="4152e-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="4152e-141">这提供了枚举和其成员，其值比更容易记忆有意义的名称。</span><span class="sxs-lookup"><span data-stu-id="4152e-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="4152e-142">然后可以在代码中，在多个位置中使用的枚举成员。</span><span class="sxs-lookup"><span data-stu-id="4152e-142">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="4152e-143">使用枚举的好处包括：</span><span class="sxs-lookup"><span data-stu-id="4152e-143">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="4152e-144">这样可以减少错误引起的转置或键入数字。</span><span class="sxs-lookup"><span data-stu-id="4152e-144">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="4152e-145">便于将来更改值。</span><span class="sxs-lookup"><span data-stu-id="4152e-145">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="4152e-146">使代码易于阅读，这意味着它不太可能将引入错误。</span><span class="sxs-lookup"><span data-stu-id="4152e-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="4152e-147">可确保向前兼容性。</span><span class="sxs-lookup"><span data-stu-id="4152e-147">Ensures forward compatibility.</span></span> <span data-ttu-id="4152e-148">如果使用枚举，您的代码是不太可能会失败，如果有人在将来更改的成员名称与对应的值。</span><span class="sxs-lookup"><span data-stu-id="4152e-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="4152e-149">枚举具有名称、 基础数据类型和一组的成员。</span><span class="sxs-lookup"><span data-stu-id="4152e-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="4152e-150">每个成员都表示一个常数。</span><span class="sxs-lookup"><span data-stu-id="4152e-150">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="4152e-151">在类、 结构、 模块或接口级别，在任何过程中，外部声明的枚举是*成员枚举*。</span><span class="sxs-lookup"><span data-stu-id="4152e-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="4152e-152">它是类、 结构、 模块或接口声明它的成员。</span><span class="sxs-lookup"><span data-stu-id="4152e-152">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="4152e-153">成员枚举可以是从任何位置访问其类、 结构、 模块或接口。</span><span class="sxs-lookup"><span data-stu-id="4152e-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="4152e-154">代码类之外，结构或模块必须限定成员枚举的名称，并且该类、 结构或模块的名称。</span><span class="sxs-lookup"><span data-stu-id="4152e-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="4152e-155">你可以无需通过添加使用完全限定的名称[导入](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)语句的源文件。</span><span class="sxs-lookup"><span data-stu-id="4152e-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="4152e-156">在命名空间级别，任何类、 结构、 模块或接口，外部声明的枚举是它所在的命名空间的成员。</span><span class="sxs-lookup"><span data-stu-id="4152e-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="4152e-157">*声明上下文*枚举必须是源文件、 命名空间、 类、 结构、 模块或接口，并且不能为一个过程。</span><span class="sxs-lookup"><span data-stu-id="4152e-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="4152e-158">有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="4152e-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="4152e-159">您可以将特性应用到枚举作为一个整体，而不是属于其成员分别。</span><span class="sxs-lookup"><span data-stu-id="4152e-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="4152e-160">属性提供对程序集的元数据的信息。</span><span class="sxs-lookup"><span data-stu-id="4152e-160">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="4152e-161">数据类型</span><span class="sxs-lookup"><span data-stu-id="4152e-161">Data Type</span></span>  
 <span data-ttu-id="4152e-162">`Enum`语句可以声明枚举的数据类型。</span><span class="sxs-lookup"><span data-stu-id="4152e-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="4152e-163">每个成员将在枚举的数据类型。</span><span class="sxs-lookup"><span data-stu-id="4152e-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="4152e-164">您可以指定`Byte`， `Integer`， `Long`， `SByte`， `Short`， `UInteger`， `ULong`，或`UShort`。</span><span class="sxs-lookup"><span data-stu-id="4152e-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="4152e-165">如果未指定`datatype`枚举中，对于每个成员采用的数据类型及其`initializer`。</span><span class="sxs-lookup"><span data-stu-id="4152e-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="4152e-166">如果同时指定`datatype`并`initializer`的数据类型`initializer`必须可转换为`datatype`。</span><span class="sxs-lookup"><span data-stu-id="4152e-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="4152e-167">如果既没有`datatype`也不`initializer`存在，则数据类型默认为`Integer`。</span><span class="sxs-lookup"><span data-stu-id="4152e-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="4152e-168">初始化成员</span><span class="sxs-lookup"><span data-stu-id="4152e-168">Initializing Members</span></span>  
 <span data-ttu-id="4152e-169">`Enum`语句可以初始化中的所选成员的内容`memberlist`。</span><span class="sxs-lookup"><span data-stu-id="4152e-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="4152e-170">您使用`initializer`提供要分配给成员的表达式。</span><span class="sxs-lookup"><span data-stu-id="4152e-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="4152e-171">如果未指定`initializer`成员，Visual Basic 将它初始化为零 (如果它是第一个`member`中`memberlist`)，或为值比前面紧邻的大 1 `member`。</span><span class="sxs-lookup"><span data-stu-id="4152e-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="4152e-172">在每个提供的表达式`initializer`可以是文本、 其他常量已定义的和已定义，包括以前的此枚举成员的枚举成员的任意组合。</span><span class="sxs-lookup"><span data-stu-id="4152e-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="4152e-173">可以使用算术和逻辑运算符来组合这些元素。</span><span class="sxs-lookup"><span data-stu-id="4152e-173">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="4152e-174">不能使用变量或函数中的`initializer`。</span><span class="sxs-lookup"><span data-stu-id="4152e-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="4152e-175">但是，可以使用转换关键字如`CByte`和`CShort`。</span><span class="sxs-lookup"><span data-stu-id="4152e-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="4152e-176">此外可以使用`AscW`如果调用与常量`String`或`Char`参数，因为可以在编译时计算。</span><span class="sxs-lookup"><span data-stu-id="4152e-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="4152e-177">枚举不能具有浮点值。</span><span class="sxs-lookup"><span data-stu-id="4152e-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="4152e-178">如果将成员分配一个浮点值和`Option Strict`设置为 on，会发生编译器错误。</span><span class="sxs-lookup"><span data-stu-id="4152e-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="4152e-179">如果`Option Strict`处于关闭状态，值自动转换为`Enum`类型。</span><span class="sxs-lookup"><span data-stu-id="4152e-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="4152e-180">如果某个成员的值超出了允许的范围的基础数据类型，或者如果初始化任何成员添加到基础数据类型所允许的最大值，编译器会报告错误。</span><span class="sxs-lookup"><span data-stu-id="4152e-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="4152e-181">修饰符</span><span class="sxs-lookup"><span data-stu-id="4152e-181">Modifiers</span></span>  
 <span data-ttu-id="4152e-182">类、 结构、 模块和接口成员枚举默认为公共访问权限。</span><span class="sxs-lookup"><span data-stu-id="4152e-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="4152e-183">您可以调整其访问级别和访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="4152e-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="4152e-184">Namespace 成员枚举默认为友元访问权限。</span><span class="sxs-lookup"><span data-stu-id="4152e-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="4152e-185">您可以调整其公共的但无法访问私有或受保护的访问级别。</span><span class="sxs-lookup"><span data-stu-id="4152e-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="4152e-186">有关详细信息，请参阅[访问 Visual Basic 中的级别](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="4152e-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="4152e-187">所有枚举成员都具有公共访问权限，并且不能对其使用任何访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="4152e-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="4152e-188">但是，如果该枚举本身的更受限制的访问级别，指定的枚举的访问级别优先。</span><span class="sxs-lookup"><span data-stu-id="4152e-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="4152e-189">默认情况下，所有枚举都是类型，其字段都是常量。</span><span class="sxs-lookup"><span data-stu-id="4152e-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="4152e-190">因此`Shared`， `Static`，和`ReadOnly`声明枚举或其成员时，不能使用关键字。</span><span class="sxs-lookup"><span data-stu-id="4152e-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="4152e-191">分配多个值</span><span class="sxs-lookup"><span data-stu-id="4152e-191">Assigning Multiple Values</span></span>  
 <span data-ttu-id="4152e-192">枚举通常表示互斥的值。</span><span class="sxs-lookup"><span data-stu-id="4152e-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="4152e-193">通过包括<xref:System.FlagsAttribute>属性中`Enum`声明中，您可以改为分配多个值的枚举的实例。</span><span class="sxs-lookup"><span data-stu-id="4152e-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="4152e-194"><xref:System.FlagsAttribute>属性指定枚举视为位字段，即一组标志。</span><span class="sxs-lookup"><span data-stu-id="4152e-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="4152e-195">这些被称为*按位*枚举。</span><span class="sxs-lookup"><span data-stu-id="4152e-195">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="4152e-196">当使用声明枚举<xref:System.FlagsAttribute>属性中，我们建议使用的是 2、 1、 2、 4、 8、 16 和等等，幂的值。</span><span class="sxs-lookup"><span data-stu-id="4152e-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="4152e-197">我们还建议"None"是其值为 0 的成员的名称。</span><span class="sxs-lookup"><span data-stu-id="4152e-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="4152e-198">有关其他指南，请参阅<xref:System.FlagsAttribute>和<xref:System.Enum>。</span><span class="sxs-lookup"><span data-stu-id="4152e-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4152e-199">示例</span><span class="sxs-lookup"><span data-stu-id="4152e-199">Example</span></span>  
 <span data-ttu-id="4152e-200">下面的示例演示如何使用 `Enum` 语句。</span><span class="sxs-lookup"><span data-stu-id="4152e-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="4152e-201">请注意，该成员被称为`EggSizeEnum.Medium`，而不是作为`Medium`。</span><span class="sxs-lookup"><span data-stu-id="4152e-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 [!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="4152e-202">示例</span><span class="sxs-lookup"><span data-stu-id="4152e-202">Example</span></span>  
 <span data-ttu-id="4152e-203">下面的示例中的方法是外部`Egg`类。</span><span class="sxs-lookup"><span data-stu-id="4152e-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="4152e-204">因此，`EggSizeEnum`完全限定为`Egg.EggSizeEnum`。</span><span class="sxs-lookup"><span data-stu-id="4152e-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 [!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]  
  
## <a name="example"></a><span data-ttu-id="4152e-205">示例</span><span class="sxs-lookup"><span data-stu-id="4152e-205">Example</span></span>  
 <span data-ttu-id="4152e-206">下面的示例使用`Enum`语句来定义一组相关的命名常量的值。</span><span class="sxs-lookup"><span data-stu-id="4152e-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="4152e-207">在这种情况下，值是您可能选择设计为数据库的数据输入窗体的颜色。</span><span class="sxs-lookup"><span data-stu-id="4152e-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 [!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="4152e-208">示例</span><span class="sxs-lookup"><span data-stu-id="4152e-208">Example</span></span>  
 <span data-ttu-id="4152e-209">下面的示例显示了包括正和负号的值。</span><span class="sxs-lookup"><span data-stu-id="4152e-209">The following example shows values that include both positive and negative numbers.</span></span>  
  
 [!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="4152e-210">示例</span><span class="sxs-lookup"><span data-stu-id="4152e-210">Example</span></span>  
 <span data-ttu-id="4152e-211">在以下示例中，`As`子句用于指定`datatype`的枚举。</span><span class="sxs-lookup"><span data-stu-id="4152e-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="4152e-212">示例</span><span class="sxs-lookup"><span data-stu-id="4152e-212">Example</span></span>  
 <span data-ttu-id="4152e-213">下面的示例演示如何使用按位枚举。</span><span class="sxs-lookup"><span data-stu-id="4152e-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="4152e-214">多个值可以分配给的按位枚举的实例。</span><span class="sxs-lookup"><span data-stu-id="4152e-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="4152e-215">`Enum`声明包括<xref:System.FlagsAttribute>属性，指示可以将枚举视为一组标志。</span><span class="sxs-lookup"><span data-stu-id="4152e-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 [!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="4152e-216">示例</span><span class="sxs-lookup"><span data-stu-id="4152e-216">Example</span></span>  
 <span data-ttu-id="4152e-217">下面的示例循环访问枚举。</span><span class="sxs-lookup"><span data-stu-id="4152e-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="4152e-218">它使用<xref:System.Enum.GetNames%2A>方法从枚举检索的成员名称的数组和<xref:System.Enum.GetValues%2A>检索成员值的数组。</span><span class="sxs-lookup"><span data-stu-id="4152e-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 [!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]  
  
## <a name="see-also"></a><span data-ttu-id="4152e-219">请参阅</span><span class="sxs-lookup"><span data-stu-id="4152e-219">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="4152e-220">Const 语句</span><span class="sxs-lookup"><span data-stu-id="4152e-220">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="4152e-221">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="4152e-221">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="4152e-222">隐式转换和显式转换</span><span class="sxs-lookup"><span data-stu-id="4152e-222">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="4152e-223">类型转换函数</span><span class="sxs-lookup"><span data-stu-id="4152e-223">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="4152e-224">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="4152e-224">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
