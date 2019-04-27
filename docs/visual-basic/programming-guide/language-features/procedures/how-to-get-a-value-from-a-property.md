---
title: 如何：获取一个值，从属性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
ms.openlocfilehash: 5e2676a0880092a78405fe5dafa0469161b85610
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863631"
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="e89f0-102">如何：获取一个值，从属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e89f0-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="e89f0-103">通过将属性名称包含在表达式中检索属性的值。</span><span class="sxs-lookup"><span data-stu-id="e89f0-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="e89f0-104">该属性的`Get`过程中检索值，但并不按名称显式调用它。</span><span class="sxs-lookup"><span data-stu-id="e89f0-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="e89f0-105">您使用该属性，就像您将使用变量。</span><span class="sxs-lookup"><span data-stu-id="e89f0-105">You use the property just as you would use a variable.</span></span> <span data-ttu-id="e89f0-106">Visual Basic 可以对该属性的过程的调用。</span><span class="sxs-lookup"><span data-stu-id="e89f0-106">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="e89f0-107">若要检索属性的值</span><span class="sxs-lookup"><span data-stu-id="e89f0-107">To retrieve a value from a property</span></span>  
  
1. <span data-ttu-id="e89f0-108">将使用变量名的相同方式在表达式中使用的属性名称。</span><span class="sxs-lookup"><span data-stu-id="e89f0-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="e89f0-109">可以使用属性可以在任意位置使用一个变量或常量。</span><span class="sxs-lookup"><span data-stu-id="e89f0-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="e89f0-110">或</span><span class="sxs-lookup"><span data-stu-id="e89f0-110">-or-</span></span>  
  
     <span data-ttu-id="e89f0-111">使用属性名称之后等号 (`=`) 在赋值语句登录。</span><span class="sxs-lookup"><span data-stu-id="e89f0-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="e89f0-112">下面的示例读取的值的 Visual basic`Now`属性外，隐式调用其`Get`过程。</span><span class="sxs-lookup"><span data-stu-id="e89f0-112">The following example reads the value of the Visual Basic `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="e89f0-113">如果该属性接受参数，请按照使用括号将参数列表括起来的属性名称。</span><span class="sxs-lookup"><span data-stu-id="e89f0-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="e89f0-114">如果没有任何自变量，可以选择性地省略括号。</span><span class="sxs-lookup"><span data-stu-id="e89f0-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="e89f0-115">将参数放在括号中，由逗号分隔参数列表中。</span><span class="sxs-lookup"><span data-stu-id="e89f0-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="e89f0-116">请确保提供的属性定义的相应参数的相同顺序中的自变量。</span><span class="sxs-lookup"><span data-stu-id="e89f0-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="e89f0-117">属性的值出现在中，只需为变量表达式或常数那样，或存储在变量或赋值语句左侧的属性。</span><span class="sxs-lookup"><span data-stu-id="e89f0-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e89f0-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="e89f0-118">See also</span></span>

- [<span data-ttu-id="e89f0-119">过程</span><span class="sxs-lookup"><span data-stu-id="e89f0-119">Procedures</span></span>](./index.md)
- [<span data-ttu-id="e89f0-120">属性过程</span><span class="sxs-lookup"><span data-stu-id="e89f0-120">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="e89f0-121">过程参数和自变量</span><span class="sxs-lookup"><span data-stu-id="e89f0-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="e89f0-122">Property 语句</span><span class="sxs-lookup"><span data-stu-id="e89f0-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="e89f0-123">在 Visual Basic 中属性和变量之间的差异</span><span class="sxs-lookup"><span data-stu-id="e89f0-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="e89f0-124">如何：创建属性</span><span class="sxs-lookup"><span data-stu-id="e89f0-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="e89f0-125">如何：声明具有混合的访问级别的属性</span><span class="sxs-lookup"><span data-stu-id="e89f0-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="e89f0-126">如何：调用 Property 过程</span><span class="sxs-lookup"><span data-stu-id="e89f0-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="e89f0-127">如何：声明并在 Visual Basic 中调用默认属性</span><span class="sxs-lookup"><span data-stu-id="e89f0-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="e89f0-128">如何：在属性中放置值</span><span class="sxs-lookup"><span data-stu-id="e89f0-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
