---
title: + 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 448ca9d52d820029464b75a616dc032a7cc41f59
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979634"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="77410-102">+ 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77410-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="77410-103">两个数字相加或返回数值表达式的正值。</span><span class="sxs-lookup"><span data-stu-id="77410-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="77410-104">此外可以用于连接两个字符串表达式。</span><span class="sxs-lookup"><span data-stu-id="77410-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77410-105">语法</span><span class="sxs-lookup"><span data-stu-id="77410-105">Syntax</span></span>  
  
```vb
expression1 + expression2  
- or -  
+ expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="77410-106">部件</span><span class="sxs-lookup"><span data-stu-id="77410-106">Parts</span></span>  
  
|<span data-ttu-id="77410-107">术语</span><span class="sxs-lookup"><span data-stu-id="77410-107">Term</span></span>|<span data-ttu-id="77410-108">定义</span><span class="sxs-lookup"><span data-stu-id="77410-108">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="77410-109">必需。</span><span class="sxs-lookup"><span data-stu-id="77410-109">Required.</span></span> <span data-ttu-id="77410-110">任何数值或字符串表达式。</span><span class="sxs-lookup"><span data-stu-id="77410-110">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="77410-111">必填，除非`+`运算符正在计算值为负。</span><span class="sxs-lookup"><span data-stu-id="77410-111">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="77410-112">任何数值或字符串表达式。</span><span class="sxs-lookup"><span data-stu-id="77410-112">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="77410-113">结果</span><span class="sxs-lookup"><span data-stu-id="77410-113">Result</span></span>  
 <span data-ttu-id="77410-114">如果`expression1`和`expression2`均为数值，结果是其算术的总和。</span><span class="sxs-lookup"><span data-stu-id="77410-114">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="77410-115">如果`expression2`不存在，`+`操作员*一元*恒等运算符的表达式的未更改值。</span><span class="sxs-lookup"><span data-stu-id="77410-115">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="77410-116">在这种情况下，该操作包含的保留的符号`expression1`，因此，结果为负如果`expression1`为负。</span><span class="sxs-lookup"><span data-stu-id="77410-116">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="77410-117">如果`expression1`和`expression2`都是字符串，结果是其值的串联。</span><span class="sxs-lookup"><span data-stu-id="77410-117">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="77410-118">如果`expression1`并`expression2`是混合类型的所执行的操作取决于它们的类型、 其内容和设置[Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="77410-118">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="77410-119">有关详细信息，请参阅"备注。"中的表</span><span class="sxs-lookup"><span data-stu-id="77410-119">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="77410-120">支持的类型</span><span class="sxs-lookup"><span data-stu-id="77410-120">Supported Types</span></span>  
 <span data-ttu-id="77410-121">所有数值类型，包括未签名和浮点类型和`Decimal`，和`String`。</span><span class="sxs-lookup"><span data-stu-id="77410-121">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77410-122">备注</span><span class="sxs-lookup"><span data-stu-id="77410-122">Remarks</span></span>  
 <span data-ttu-id="77410-123">一般情况下，`+`执行算术加法运算，如果可能，并将连接仅当这两个表达式都是字符串。</span><span class="sxs-lookup"><span data-stu-id="77410-123">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="77410-124">如果一个表达式都不是`Object`，Visual Basic 将采取以下措施。</span><span class="sxs-lookup"><span data-stu-id="77410-124">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="77410-125">数据类型的表达式</span><span class="sxs-lookup"><span data-stu-id="77410-125">Data types of expressions</span></span>|<span data-ttu-id="77410-126">由编译器的操作</span><span class="sxs-lookup"><span data-stu-id="77410-126">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="77410-127">这两个表达式是数值数据类型 (`SByte`， `Byte`， `Short`， `UShort`， `Integer`， `UInteger`， `Long`， `ULong`， `Decimal`， `Single`，或`Double`)</span><span class="sxs-lookup"><span data-stu-id="77410-127">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="77410-128">添加。</span><span class="sxs-lookup"><span data-stu-id="77410-128">Add.</span></span> <span data-ttu-id="77410-129">结果数据类型为数值类型的数据类型的相应`expression1`和`expression2`。</span><span class="sxs-lookup"><span data-stu-id="77410-129">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="77410-130">请参阅中的"整数运算"表[数据类型的运算符结果](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)。</span><span class="sxs-lookup"><span data-stu-id="77410-130">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="77410-131">这两个表达式都是类型 `String`</span><span class="sxs-lookup"><span data-stu-id="77410-131">Both expressions are of type `String`</span></span>|<span data-ttu-id="77410-132">串联在一起。</span><span class="sxs-lookup"><span data-stu-id="77410-132">Concatenate.</span></span>|  
|<span data-ttu-id="77410-133">一个表达式是数值数据类型和另一个是一个字符串，</span><span class="sxs-lookup"><span data-stu-id="77410-133">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="77410-134">如果`Option Strict`是`On`，然后生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="77410-134">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="77410-135">如果`Option Strict`是`Off`，然后隐式转换`String`到`Double`和添加。</span><span class="sxs-lookup"><span data-stu-id="77410-135">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="77410-136">如果`String`不能转换为`Double`，然后引发<xref:System.InvalidCastException>异常。</span><span class="sxs-lookup"><span data-stu-id="77410-136">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="77410-137">一个表达式是数值数据类型，和另一个是[执行任何操作](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="77410-137">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|<span data-ttu-id="77410-138">添加，请使用`Nothing`作为零值。</span><span class="sxs-lookup"><span data-stu-id="77410-138">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="77410-139">一个表达式是一个字符串，另一个是 `Nothing`</span><span class="sxs-lookup"><span data-stu-id="77410-139">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="77410-140">连接，使用`Nothing`值为""。</span><span class="sxs-lookup"><span data-stu-id="77410-140">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="77410-141">如果一个表达式是`Object`表达式，Visual Basic 将采取以下措施。</span><span class="sxs-lookup"><span data-stu-id="77410-141">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="77410-142">数据类型的表达式</span><span class="sxs-lookup"><span data-stu-id="77410-142">Data types of expressions</span></span>|<span data-ttu-id="77410-143">由编译器的操作</span><span class="sxs-lookup"><span data-stu-id="77410-143">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="77410-144">`Object` 表达式包含的数值和另一个是数值数据类型</span><span class="sxs-lookup"><span data-stu-id="77410-144">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="77410-145">如果`Option Strict`是`On`，然后生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="77410-145">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="77410-146">如果`Option Strict`是`Off`，然后添加。</span><span class="sxs-lookup"><span data-stu-id="77410-146">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="77410-147">`Object` 表达式包含的数值和另一个是类型 `String`</span><span class="sxs-lookup"><span data-stu-id="77410-147">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="77410-148">如果`Option Strict`是`On`，然后生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="77410-148">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="77410-149">如果`Option Strict`是`Off`，然后隐式转换`String`到`Double`和添加。</span><span class="sxs-lookup"><span data-stu-id="77410-149">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="77410-150">如果`String`不能转换为`Double`，然后引发<xref:System.InvalidCastException>异常。</span><span class="sxs-lookup"><span data-stu-id="77410-150">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="77410-151">`Object` 表达式包含一个字符串，另一个是数值数据类型</span><span class="sxs-lookup"><span data-stu-id="77410-151">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="77410-152">如果`Option Strict`是`On`，然后生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="77410-152">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="77410-153">如果`Option Strict`是`Off`，然后将字符串隐式转换`Object`到`Double`和添加。</span><span class="sxs-lookup"><span data-stu-id="77410-153">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="77410-154">如果字符串`Object`不能转换为`Double`，然后引发<xref:System.InvalidCastException>异常。</span><span class="sxs-lookup"><span data-stu-id="77410-154">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="77410-155">`Object` 表达式包含一个字符串和另一个是类型 `String`</span><span class="sxs-lookup"><span data-stu-id="77410-155">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="77410-156">如果`Option Strict`是`On`，然后生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="77410-156">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="77410-157">如果`Option Strict`是`Off`，然后隐式转换`Object`到`String`和连接。</span><span class="sxs-lookup"><span data-stu-id="77410-157">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="77410-158">如果两个表达式均`Object`表达式，Visual Basic 将采取以下措施 (`Option Strict Off`仅)。</span><span class="sxs-lookup"><span data-stu-id="77410-158">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="77410-159">数据类型的表达式</span><span class="sxs-lookup"><span data-stu-id="77410-159">Data types of expressions</span></span>|<span data-ttu-id="77410-160">由编译器的操作</span><span class="sxs-lookup"><span data-stu-id="77410-160">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="77410-161">同时`Object`表达式包含数字值</span><span class="sxs-lookup"><span data-stu-id="77410-161">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="77410-162">添加。</span><span class="sxs-lookup"><span data-stu-id="77410-162">Add.</span></span>|  
|<span data-ttu-id="77410-163">同时`Object`表达式均为类型 `String`</span><span class="sxs-lookup"><span data-stu-id="77410-163">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="77410-164">串联在一起。</span><span class="sxs-lookup"><span data-stu-id="77410-164">Concatenate.</span></span>|  
|<span data-ttu-id="77410-165">一个`Object`表达式包含的数字值和其他包含字符串</span><span class="sxs-lookup"><span data-stu-id="77410-165">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="77410-166">将字符串隐式转换`Object`到`Double`和添加。</span><span class="sxs-lookup"><span data-stu-id="77410-166">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="77410-167">如果字符串`Object`不能转换为数值，则引发<xref:System.InvalidCastException>异常。</span><span class="sxs-lookup"><span data-stu-id="77410-167">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="77410-168">如果任一`Object`表达式的计算结果[Nothing](../../../visual-basic/language-reference/nothing.md)或<xref:System.DBNull>，则`+`运算符将其视为`String`值为""。</span><span class="sxs-lookup"><span data-stu-id="77410-168">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77410-169">当你使用`+`运算符，您可能不能确定是否将进行加法或字符串串联。</span><span class="sxs-lookup"><span data-stu-id="77410-169">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="77410-170">使用`&`串联以消除二义性，并提供自我说明代码的运算符。</span><span class="sxs-lookup"><span data-stu-id="77410-170">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="77410-171">重载</span><span class="sxs-lookup"><span data-stu-id="77410-171">Overloading</span></span>  
 <span data-ttu-id="77410-172">`+`运算符可以被*重载*，这意味着，某个类或结构可以重新定义其行为时，操作数的类或结构的类型。</span><span class="sxs-lookup"><span data-stu-id="77410-172">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="77410-173">如果你的代码对此类的类或结构使用此运算符，请确保了解其被重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="77410-173">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="77410-174">有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="77410-174">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="77410-175">示例</span><span class="sxs-lookup"><span data-stu-id="77410-175">Example</span></span>  
 <span data-ttu-id="77410-176">下面的示例使用`+`运算符将数相加。</span><span class="sxs-lookup"><span data-stu-id="77410-176">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="77410-177">如果操作数均为数值的同时，Visual Basic 计算运算的结果。</span><span class="sxs-lookup"><span data-stu-id="77410-177">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="77410-178">算术结果表示两个操作数之和。</span><span class="sxs-lookup"><span data-stu-id="77410-178">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="77410-179">此外可以使用`+`运算符来串联字符串。</span><span class="sxs-lookup"><span data-stu-id="77410-179">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="77410-180">如果操作数均为这两个字符串，Visual Basic 将它们连接。</span><span class="sxs-lookup"><span data-stu-id="77410-180">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="77410-181">串联结果表示在它们包含两个操作数的内容的单个字符串。</span><span class="sxs-lookup"><span data-stu-id="77410-181">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="77410-182">如果操作数均为混合类型的结果取决于的设置[Option Strict 语句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="77410-182">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="77410-183">下面的示例说明了结果时`Option Strict`是`On`。</span><span class="sxs-lookup"><span data-stu-id="77410-183">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="77410-184">下面的示例说明了结果时`Option Strict`是`Off`。</span><span class="sxs-lookup"><span data-stu-id="77410-184">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="77410-185">若要消除二义性，应使用`&`运算符而不是`+`的串联。</span><span class="sxs-lookup"><span data-stu-id="77410-185">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77410-186">请参阅</span><span class="sxs-lookup"><span data-stu-id="77410-186">See also</span></span>
- [<span data-ttu-id="77410-187">& 运算符</span><span class="sxs-lookup"><span data-stu-id="77410-187">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="77410-188">串联运算符</span><span class="sxs-lookup"><span data-stu-id="77410-188">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="77410-189">算术运算符</span><span class="sxs-lookup"><span data-stu-id="77410-189">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="77410-190">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="77410-190">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="77410-191">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="77410-191">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="77410-192">在 Visual Basic 中的算术运算符</span><span class="sxs-lookup"><span data-stu-id="77410-192">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="77410-193">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="77410-193">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
