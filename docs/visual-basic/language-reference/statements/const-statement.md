---
title: Const 语句
ms.date: 05/12/2018
f1_keywords:
- vb.Const
helpviewer_keywords:
- Const statement [Visual Basic]
ms.assetid: 495b318d-b7c5-4198-94f8-0790a541b07a
ms.openlocfilehash: 1411e019058e7aac8249b7a50ecd295885a74177
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354129"
---
# <a name="const-statement-visual-basic"></a><span data-ttu-id="5f926-102">Const 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f926-102">Const Statement (Visual Basic)</span></span>

<span data-ttu-id="5f926-103">声明和定义一个或多个常量。</span><span class="sxs-lookup"><span data-stu-id="5f926-103">Declares and defines one or more constants.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f926-104">语法</span><span class="sxs-lookup"><span data-stu-id="5f926-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ Shadows ]
Const constantlist
```

## <a name="parts"></a><span data-ttu-id="5f926-105">部件</span><span class="sxs-lookup"><span data-stu-id="5f926-105">Parts</span></span>

`attributelist`  
<span data-ttu-id="5f926-106">可选。</span><span class="sxs-lookup"><span data-stu-id="5f926-106">Optional.</span></span> <span data-ttu-id="5f926-107">应用于此语句中声明的所有常量的特性列表。</span><span class="sxs-lookup"><span data-stu-id="5f926-107">List of attributes that apply to all the constants declared in this statement.</span></span> <span data-ttu-id="5f926-108">请参阅尖括号中的[属性列表](../../../visual-basic/language-reference/statements/attribute-list.md)（"`<`" 和 "`>`"）。</span><span class="sxs-lookup"><span data-stu-id="5f926-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`accessmodifier`  
<span data-ttu-id="5f926-109">可选。</span><span class="sxs-lookup"><span data-stu-id="5f926-109">Optional.</span></span> <span data-ttu-id="5f926-110">用于指定哪些代码可以访问这些常量。</span><span class="sxs-lookup"><span data-stu-id="5f926-110">Use this to specify what code can access these constants.</span></span> <span data-ttu-id="5f926-111">可以是[公共](../../../visual-basic/language-reference/modifiers/public.md)、[受保护](../../../visual-basic/language-reference/modifiers/protected.md)、[朋友](../../../visual-basic/language-reference/modifiers/friend.md)、[受保护的朋友](../modifiers/protected-friend.md)、[私有](../../../visual-basic/language-reference/modifiers/private.md)或[私有保护](../../language-reference/modifiers/private-protected.md)的。</span><span class="sxs-lookup"><span data-stu-id="5f926-111">Can be [Public](../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../visual-basic/language-reference/modifiers/friend.md), [Protected Friend](../modifiers/protected-friend.md), [Private](../../../visual-basic/language-reference/modifiers/private.md), or [Private Protected](../../language-reference/modifiers/private-protected.md).</span></span>

`Shadows`  
<span data-ttu-id="5f926-112">可选。</span><span class="sxs-lookup"><span data-stu-id="5f926-112">Optional.</span></span> <span data-ttu-id="5f926-113">用于在基类中重新声明和隐藏编程元素。</span><span class="sxs-lookup"><span data-stu-id="5f926-113">Use this to redeclare and hide a programming element in a base class.</span></span> <span data-ttu-id="5f926-114">请参阅[阴影](../../../visual-basic/language-reference/modifiers/shadows.md)。</span><span class="sxs-lookup"><span data-stu-id="5f926-114">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>

`constantlist`  
<span data-ttu-id="5f926-115">必需。</span><span class="sxs-lookup"><span data-stu-id="5f926-115">Required.</span></span> <span data-ttu-id="5f926-116">在此语句中声明的常量的列表。</span><span class="sxs-lookup"><span data-stu-id="5f926-116">List of constants being declared in this statement.</span></span>

<span data-ttu-id="5f926-117">`constant` `[ ,` `constant` `... ]`</span><span class="sxs-lookup"><span data-stu-id="5f926-117">`constant` `[ ,` `constant` `... ]`</span></span>

<span data-ttu-id="5f926-118">每个 `constant` 都具有以下语法和部件：</span><span class="sxs-lookup"><span data-stu-id="5f926-118">Each `constant` has the following syntax and parts:</span></span>

<span data-ttu-id="5f926-119">`constantname` `[ As` `datatype` `] =` `initializer`</span><span class="sxs-lookup"><span data-stu-id="5f926-119">`constantname` `[ As` `datatype` `] =` `initializer`</span></span>

|<span data-ttu-id="5f926-120">部件</span><span class="sxs-lookup"><span data-stu-id="5f926-120">Part</span></span>|<span data-ttu-id="5f926-121">说明</span><span class="sxs-lookup"><span data-stu-id="5f926-121">Description</span></span>|
|----------|-----------------|
|`constantname`|<span data-ttu-id="5f926-122">必需。</span><span class="sxs-lookup"><span data-stu-id="5f926-122">Required.</span></span> <span data-ttu-id="5f926-123">常数的名称。</span><span class="sxs-lookup"><span data-stu-id="5f926-123">Name of the constant.</span></span> <span data-ttu-id="5f926-124">请参阅 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。</span><span class="sxs-lookup"><span data-stu-id="5f926-124">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`datatype`|<span data-ttu-id="5f926-125">如果 `Option Strict` `On`，则为必需。</span><span class="sxs-lookup"><span data-stu-id="5f926-125">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="5f926-126">常量的数据类型。</span><span class="sxs-lookup"><span data-stu-id="5f926-126">Data type of the constant.</span></span>|
|`initializer`|<span data-ttu-id="5f926-127">必需。</span><span class="sxs-lookup"><span data-stu-id="5f926-127">Required.</span></span> <span data-ttu-id="5f926-128">在编译时计算并分配给常量的表达式。</span><span class="sxs-lookup"><span data-stu-id="5f926-128">Expression that is evaluated at compile time and assigned to the constant.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5f926-129">备注</span><span class="sxs-lookup"><span data-stu-id="5f926-129">Remarks</span></span>

<span data-ttu-id="5f926-130">如果你的应用程序中有一个永不更改的值，则可以定义一个已命名的常量，并将其用于替代文本值。</span><span class="sxs-lookup"><span data-stu-id="5f926-130">If you have a value that never changes in your application, you can define a named constant and use it in place of a literal value.</span></span> <span data-ttu-id="5f926-131">名称比值更易于记忆。</span><span class="sxs-lookup"><span data-stu-id="5f926-131">A name is easier to remember than a value.</span></span> <span data-ttu-id="5f926-132">可以仅定义一次常数，并在代码中的多个位置使用它。</span><span class="sxs-lookup"><span data-stu-id="5f926-132">You can define the constant just once and use it in many places in your code.</span></span> <span data-ttu-id="5f926-133">如果在更高版本中，需要重新定义值，只需进行一项更改 `Const` 语句即可。</span><span class="sxs-lookup"><span data-stu-id="5f926-133">If in a later version you need to redefine the value, the `Const` statement is the only place you need to make a change.</span></span>

<span data-ttu-id="5f926-134">只能在模块或过程级别使用 `Const`。</span><span class="sxs-lookup"><span data-stu-id="5f926-134">You can use `Const` only at module or procedure level.</span></span> <span data-ttu-id="5f926-135">这意味着变量的*声明上下文*必须是类、结构、模块、过程或块，而不能是源文件、命名空间或接口。</span><span class="sxs-lookup"><span data-stu-id="5f926-135">This means the *declaration context* for a variable must be a class, structure, module, procedure, or block, and cannot be a source file, namespace, or interface.</span></span> <span data-ttu-id="5f926-136">有关详细信息，请参阅[声明上下文和默认访问级别](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="5f926-136">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="5f926-137">本地常量（在过程中）默认为公共访问，不能对其使用任何访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="5f926-137">Local constants (inside a procedure) default to public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="5f926-138">类和模块成员常量（任何过程外部）默认为私有访问，结构成员常量默认为公共访问。</span><span class="sxs-lookup"><span data-stu-id="5f926-138">Class and module member constants (outside any procedure) default to private access, and structure member constants default to public access.</span></span> <span data-ttu-id="5f926-139">您可以使用访问修饰符调整其访问级别。</span><span class="sxs-lookup"><span data-stu-id="5f926-139">You can adjust their access levels with the access modifiers.</span></span>

## <a name="rules"></a><span data-ttu-id="5f926-140">规则</span><span class="sxs-lookup"><span data-stu-id="5f926-140">Rules</span></span>

- <span data-ttu-id="5f926-141">**声明上下文。**</span><span class="sxs-lookup"><span data-stu-id="5f926-141">**Declaration Context.**</span></span> <span data-ttu-id="5f926-142">在任何过程之外，在模块级别声明的常量是*成员常量*;它是声明它的类、结构或模块的成员。</span><span class="sxs-lookup"><span data-stu-id="5f926-142">A constant declared at module level, outside any procedure, is a *member constant*; it is a member of the class, structure, or module that declares it.</span></span>

  <span data-ttu-id="5f926-143">在过程级别声明的常量是*局部常量*;它在声明它的过程或块的本地。</span><span class="sxs-lookup"><span data-stu-id="5f926-143">A constant declared at procedure level is a *local constant*; it is local to the procedure or block that declares it.</span></span>

- <span data-ttu-id="5f926-144">**属性.**</span><span class="sxs-lookup"><span data-stu-id="5f926-144">**Attributes.**</span></span> <span data-ttu-id="5f926-145">仅可将属性应用于成员常量，而不能应用于局部常数。</span><span class="sxs-lookup"><span data-stu-id="5f926-145">You can apply attributes only to member constants, not to local constants.</span></span> <span data-ttu-id="5f926-146">特性向程序集的元数据提供信息，这对于临时存储（如本地常量）没有意义。</span><span class="sxs-lookup"><span data-stu-id="5f926-146">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local constants.</span></span>

- <span data-ttu-id="5f926-147">**组成.**</span><span class="sxs-lookup"><span data-stu-id="5f926-147">**Modifiers.**</span></span> <span data-ttu-id="5f926-148">默认情况下，所有常量都 `Shared`、`Static`和 `ReadOnly`。</span><span class="sxs-lookup"><span data-stu-id="5f926-148">By default, all constants are `Shared`, `Static`, and `ReadOnly`.</span></span> <span data-ttu-id="5f926-149">在声明常数时不能使用任何这些关键字。</span><span class="sxs-lookup"><span data-stu-id="5f926-149">You cannot use any of these keywords when declaring a constant.</span></span>

  <span data-ttu-id="5f926-150">在过程级别，不能使用 `Shadows` 或任何访问修饰符来声明局部常量。</span><span class="sxs-lookup"><span data-stu-id="5f926-150">At procedure level, you cannot use `Shadows` or any access modifiers to declare local constants.</span></span>

- <span data-ttu-id="5f926-151">**多个常量。**</span><span class="sxs-lookup"><span data-stu-id="5f926-151">**Multiple Constants.**</span></span> <span data-ttu-id="5f926-152">可以在同一声明语句中声明多个常量，同时为每个常量指定 `constantname` 部分。</span><span class="sxs-lookup"><span data-stu-id="5f926-152">You can declare several constants in the same declaration statement, specifying the `constantname` part for each one.</span></span> <span data-ttu-id="5f926-153">多个常量用逗号分隔。</span><span class="sxs-lookup"><span data-stu-id="5f926-153">Multiple constants are separated by commas.</span></span>

## <a name="data-type-rules"></a><span data-ttu-id="5f926-154">数据类型规则</span><span class="sxs-lookup"><span data-stu-id="5f926-154">Data Type Rules</span></span>

- <span data-ttu-id="5f926-155">**数据类型。**</span><span class="sxs-lookup"><span data-stu-id="5f926-155">**Data Types.**</span></span> <span data-ttu-id="5f926-156">`Const` 语句可以声明变量的数据类型。</span><span class="sxs-lookup"><span data-stu-id="5f926-156">The `Const` statement can declare the data type of a variable.</span></span> <span data-ttu-id="5f926-157">您可以指定任何数据类型或枚举的名称。</span><span class="sxs-lookup"><span data-stu-id="5f926-157">You can specify any data type or the name of an enumeration.</span></span>

- <span data-ttu-id="5f926-158">**默认类型。**</span><span class="sxs-lookup"><span data-stu-id="5f926-158">**Default Type.**</span></span> <span data-ttu-id="5f926-159">如果不指定 `datatype`，则常量将采用 `initializer`的数据类型。</span><span class="sxs-lookup"><span data-stu-id="5f926-159">If you do not specify `datatype`, the constant takes the data type of `initializer`.</span></span> <span data-ttu-id="5f926-160">如果同时指定 `datatype` 和 `initializer`，`initializer` 的数据类型必须可以转换为 `datatype`。</span><span class="sxs-lookup"><span data-stu-id="5f926-160">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="5f926-161">如果 `datatype` 和 `initializer` 均不存在，则数据类型默认为 `Object`。</span><span class="sxs-lookup"><span data-stu-id="5f926-161">If neither `datatype` nor `initializer` is present, the data type defaults to `Object`.</span></span>

- <span data-ttu-id="5f926-162">**不同类型。**</span><span class="sxs-lookup"><span data-stu-id="5f926-162">**Different Types.**</span></span> <span data-ttu-id="5f926-163">您可以为不同的常量指定不同的数据类型，为您声明的每个变量使用单独的 `As` 子句。</span><span class="sxs-lookup"><span data-stu-id="5f926-163">You can specify different data types for different constants by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="5f926-164">但是，不能通过使用 common `As` 子句将多个常量声明为同一类型。</span><span class="sxs-lookup"><span data-stu-id="5f926-164">However, you cannot declare several constants to be of the same type by using a common `As` clause.</span></span>

- <span data-ttu-id="5f926-165">**起始.**</span><span class="sxs-lookup"><span data-stu-id="5f926-165">**Initialization.**</span></span> <span data-ttu-id="5f926-166">必须初始化 `constantlist`中每个常量的值。</span><span class="sxs-lookup"><span data-stu-id="5f926-166">You must initialize the value of every constant in `constantlist`.</span></span> <span data-ttu-id="5f926-167">使用 `initializer` 提供要分配给常量的表达式。</span><span class="sxs-lookup"><span data-stu-id="5f926-167">You use `initializer` to supply an expression to be assigned to the constant.</span></span> <span data-ttu-id="5f926-168">表达式可以是文本的任意组合、已经定义的其他常数以及已定义的枚举成员。</span><span class="sxs-lookup"><span data-stu-id="5f926-168">The expression can be any combination of literals, other constants that are already defined, and enumeration members that are already defined.</span></span> <span data-ttu-id="5f926-169">可以使用算术运算符和逻辑运算符来合并此类元素。</span><span class="sxs-lookup"><span data-stu-id="5f926-169">You can use arithmetic and logical operators to combine such elements.</span></span>

  <span data-ttu-id="5f926-170">不能在 `initializer`中使用变量或函数。</span><span class="sxs-lookup"><span data-stu-id="5f926-170">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="5f926-171">不过，您可以使用转换关键字，如 `CByte` 和 `CShort`。</span><span class="sxs-lookup"><span data-stu-id="5f926-171">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="5f926-172">如果使用常量 `String` 或 `Char` 参数调用它，则还可以使用 `AscW`，因为可以在编译时计算。</span><span class="sxs-lookup"><span data-stu-id="5f926-172">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

## <a name="behavior"></a><span data-ttu-id="5f926-173">行为</span><span class="sxs-lookup"><span data-stu-id="5f926-173">Behavior</span></span>

- <span data-ttu-id="5f926-174">**内.**</span><span class="sxs-lookup"><span data-stu-id="5f926-174">**Scope.**</span></span> <span data-ttu-id="5f926-175">本地常量只能从其过程或块中访问。</span><span class="sxs-lookup"><span data-stu-id="5f926-175">Local constants are accessible only from within their procedure or block.</span></span> <span data-ttu-id="5f926-176">成员常量可从其类、结构或模块中的任何位置进行访问。</span><span class="sxs-lookup"><span data-stu-id="5f926-176">Member constants are accessible from anywhere within their class, structure, or module.</span></span>

- <span data-ttu-id="5f926-177">**限定.**</span><span class="sxs-lookup"><span data-stu-id="5f926-177">**Qualification.**</span></span> <span data-ttu-id="5f926-178">类、结构或模块外的代码必须使用该类、结构或模块的名称来限定成员常量的名称。</span><span class="sxs-lookup"><span data-stu-id="5f926-178">Code outside a class, structure, or module must qualify a member constant's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="5f926-179">过程或块外的代码不能引用该过程或块中的任何本地常数。</span><span class="sxs-lookup"><span data-stu-id="5f926-179">Code outside a procedure or block cannot refer to any local constants within that procedure or block.</span></span>

## <a name="example"></a><span data-ttu-id="5f926-180">示例</span><span class="sxs-lookup"><span data-stu-id="5f926-180">Example</span></span>

<span data-ttu-id="5f926-181">下面的示例使用 `Const` 语句声明用于替代文本值的常量。</span><span class="sxs-lookup"><span data-stu-id="5f926-181">The following example uses the `Const` statement to declare constants for use in place of literal values.</span></span>

[!code-vb[VbVbalrStatements#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#13)]

## <a name="example"></a><span data-ttu-id="5f926-182">示例</span><span class="sxs-lookup"><span data-stu-id="5f926-182">Example</span></span>

<span data-ttu-id="5f926-183">如果定义的常量的数据类型 `Object`，则 Visual Basic 编译器会为其提供 `initializer`类型，而不是 `Object`。</span><span class="sxs-lookup"><span data-stu-id="5f926-183">If you define a constant with data type `Object`, the Visual Basic compiler gives it the type of `initializer`, instead of `Object`.</span></span> <span data-ttu-id="5f926-184">在下面的示例中，常量 `naturalLogBase` `Decimal`运行时类型。</span><span class="sxs-lookup"><span data-stu-id="5f926-184">In the following example, the constant `naturalLogBase` has the run-time type `Decimal`.</span></span>

[!code-vb[VbVbalrStatements#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#87)]

<span data-ttu-id="5f926-185">前面的示例对[GetType 运算符](../../../visual-basic/language-reference/operators/gettype-operator.md)返回的 <xref:System.Type> 对象使用 <xref:System.Type.ToString%2A> 方法，因为 <xref:System.Type> 不能使用 `CStr`转换为 `String`。</span><span class="sxs-lookup"><span data-stu-id="5f926-185">The preceding example uses the <xref:System.Type.ToString%2A> method on the <xref:System.Type> object returned by the [GetType Operator](../../../visual-basic/language-reference/operators/gettype-operator.md), because <xref:System.Type> cannot be converted to `String` using `CStr`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f926-186">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5f926-186">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="5f926-187">Enum 语句</span><span class="sxs-lookup"><span data-stu-id="5f926-187">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)
- [<span data-ttu-id="5f926-188">#Const 指令</span><span class="sxs-lookup"><span data-stu-id="5f926-188">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)
- [<span data-ttu-id="5f926-189">Dim 语句</span><span class="sxs-lookup"><span data-stu-id="5f926-189">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="5f926-190">ReDim 语句</span><span class="sxs-lookup"><span data-stu-id="5f926-190">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="5f926-191">隐式转换和显式转换</span><span class="sxs-lookup"><span data-stu-id="5f926-191">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="5f926-192">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="5f926-192">Constants and Enumerations</span></span>](../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="5f926-193">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="5f926-193">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="5f926-194">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="5f926-194">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
