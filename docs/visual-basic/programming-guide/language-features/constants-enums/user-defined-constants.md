---
title: 用户定义的常量 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: dc940105bbeb5e54819b8df5d5b3c831c7a6e145
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527310"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="5f322-102">用户定义的常量 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f322-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="5f322-103">常量是有意义的名称采用的数字或字符串不会更改的位置。</span><span class="sxs-lookup"><span data-stu-id="5f322-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="5f322-104">顾名思义，常量存储在应用程序的执行过程中保持不变的值。</span><span class="sxs-lookup"><span data-stu-id="5f322-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="5f322-105">您可以使用由该控件或组件，定义的常量或可以创建你自己。</span><span class="sxs-lookup"><span data-stu-id="5f322-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="5f322-106">创建自己的常量被称为*用户定义*。</span><span class="sxs-lookup"><span data-stu-id="5f322-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="5f322-107">声明与常量`Const`语句，用于创建变量的名称使用相同的规则。</span><span class="sxs-lookup"><span data-stu-id="5f322-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="5f322-108">如果`Option Strict`是`On`，必须显式声明常量的类型。</span><span class="sxs-lookup"><span data-stu-id="5f322-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="5f322-109">Const 语句使用情况</span><span class="sxs-lookup"><span data-stu-id="5f322-109">Const Statement Usage</span></span>  
 <span data-ttu-id="5f322-110">一个`Const`语句可以表示数学或日期/时间数量：</span><span class="sxs-lookup"><span data-stu-id="5f322-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 <span data-ttu-id="5f322-111">它还可以定义`String`常量：</span><span class="sxs-lookup"><span data-stu-id="5f322-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 <span data-ttu-id="5f322-112">等号右侧的表达式 ( `=` ) 通常是一个数字或文本字符串，但它也可以是计算结果为数字或字符串 （尽管该表达式不能包含对函数的调用） 的表达式。</span><span class="sxs-lookup"><span data-stu-id="5f322-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="5f322-113">甚至可以定义根据以前定义的常数的常量：</span><span class="sxs-lookup"><span data-stu-id="5f322-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="5f322-114">作用域的用户定义的常量</span><span class="sxs-lookup"><span data-stu-id="5f322-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="5f322-115">一个`Const`语句的作用域是在同一位置中声明的变量相同。</span><span class="sxs-lookup"><span data-stu-id="5f322-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="5f322-116">您可以通过以下方式之一指定作用域：</span><span class="sxs-lookup"><span data-stu-id="5f322-116">You can specify scope in any of the following ways:</span></span>  
  
-   <span data-ttu-id="5f322-117">若要创建过程中仅存在一个常量，请在该过程中声明。</span><span class="sxs-lookup"><span data-stu-id="5f322-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
-   <span data-ttu-id="5f322-118">若要创建在类中，所有过程而不是属于该模块以外的任何代码都可用的常数，请将其声明的类的声明部分。</span><span class="sxs-lookup"><span data-stu-id="5f322-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="5f322-119">若要创建一个常量，它是可用的程序集外部客户端程序集的所有成员而不可用，将使用其声明`Friend`类的声明部分中的关键字。</span><span class="sxs-lookup"><span data-stu-id="5f322-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="5f322-120">若要创建可在整个应用程序使用的常量，将使用其声明`Public`关键字在下面的声明部分类。</span><span class="sxs-lookup"><span data-stu-id="5f322-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="5f322-121">有关详细信息，请参阅[如何：声明常量](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)。</span><span class="sxs-lookup"><span data-stu-id="5f322-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="5f322-122">避免循环引用</span><span class="sxs-lookup"><span data-stu-id="5f322-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="5f322-123">由于可以在其他常量方面定义常量，它是可能无意中产生*周期*，或两个或多个常量之间的循环引用。</span><span class="sxs-lookup"><span data-stu-id="5f322-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="5f322-124">发生一次时有两个或多个公共常量，其中每个定义，根据其他的如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="5f322-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 <span data-ttu-id="5f322-125">如果发生一次，Visual Basic 生成编译器错误。</span><span class="sxs-lookup"><span data-stu-id="5f322-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f322-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="5f322-126">See also</span></span>
- [<span data-ttu-id="5f322-127">Const 语句</span><span class="sxs-lookup"><span data-stu-id="5f322-127">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="5f322-128">常量和文本数据类型</span><span class="sxs-lookup"><span data-stu-id="5f322-128">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="5f322-129">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="5f322-129">Constants and Enumerations</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="5f322-130">常量和枚举</span><span class="sxs-lookup"><span data-stu-id="5f322-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="5f322-131">枚举概述</span><span class="sxs-lookup"><span data-stu-id="5f322-131">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="5f322-132">常量概述</span><span class="sxs-lookup"><span data-stu-id="5f322-132">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="5f322-133">如何：声明枚举</span><span class="sxs-lookup"><span data-stu-id="5f322-133">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="5f322-134">枚举和名称限定</span><span class="sxs-lookup"><span data-stu-id="5f322-134">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="5f322-135">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="5f322-135">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
