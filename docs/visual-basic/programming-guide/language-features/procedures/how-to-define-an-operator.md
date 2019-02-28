---
title: 如何：定义运算符 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- operator procedures [Visual Basic], about operator procedures
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: d4b0e253-092a-4e6e-9fe2-01f562140a29
ms.openlocfilehash: 1e7d767b1ba370ac7303abfd8aa3606a43c33de9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973283"
---
# <a name="how-to-define-an-operator-visual-basic"></a><span data-ttu-id="894cb-102">如何：定义运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="894cb-102">How to: Define an Operator (Visual Basic)</span></span>
<span data-ttu-id="894cb-103">如果已定义的类或结构，可以定义标准运算符的行为 (如`*`， `<>`，或`And`) 当一个或两个操作数是类或结构的类型。</span><span class="sxs-lookup"><span data-stu-id="894cb-103">If you have defined a class or structure, you can define the behavior of a standard operator (such as `*`, `<>`, or `And`) when one or both of the operands is of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="894cb-104">标准运算符定义为类或结构中的运算符过程。</span><span class="sxs-lookup"><span data-stu-id="894cb-104">Define the standard operator as an operator procedure within the class or structure.</span></span> <span data-ttu-id="894cb-105">所有运算符过程都必须都是`Public` `Shared`。</span><span class="sxs-lookup"><span data-stu-id="894cb-105">All operator procedures must be `Public` `Shared`.</span></span>  
  
 <span data-ttu-id="894cb-106">在类或结构上定义一个运算符也称为*重载*运算符。</span><span class="sxs-lookup"><span data-stu-id="894cb-106">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="894cb-107">示例</span><span class="sxs-lookup"><span data-stu-id="894cb-107">Example</span></span>  
 <span data-ttu-id="894cb-108">下面的示例定义`+`调用的运算符为结构`height`。</span><span class="sxs-lookup"><span data-stu-id="894cb-108">The following example defines the `+` operator for a structure called `height`.</span></span> <span data-ttu-id="894cb-109">该结构的高度以英尺、 英寸为单位。</span><span class="sxs-lookup"><span data-stu-id="894cb-109">The structure uses heights measured in feet and inches.</span></span> <span data-ttu-id="894cb-110">一个*英寸*2.54 厘米和一个*foot*为 12 英寸。</span><span class="sxs-lookup"><span data-stu-id="894cb-110">One *inch* is 2.54 centimeters, and one *foot* is 12 inches.</span></span> <span data-ttu-id="894cb-111">若要确保规范化的值 (英寸 < 12.0)，该构造函数执行*取模*12 的运算。</span><span class="sxs-lookup"><span data-stu-id="894cb-111">To ensure normalized values (inches < 12.0), the constructor performs *modulo* 12 arithmetic.</span></span> <span data-ttu-id="894cb-112">`+`运算符使用构造函数生成规范化的值。</span><span class="sxs-lookup"><span data-stu-id="894cb-112">The `+` operator uses the constructor to generate normalized values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#25)]  
  
 <span data-ttu-id="894cb-113">可以测试结构`height`用下面的代码。</span><span class="sxs-lookup"><span data-stu-id="894cb-113">You can test the structure `height` with the following code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#26)]  
  
  
## <a name="see-also"></a><span data-ttu-id="894cb-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="894cb-114">See also</span></span>
- [<span data-ttu-id="894cb-115">运算符过程</span><span class="sxs-lookup"><span data-stu-id="894cb-115">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="894cb-116">如何：定义转换运算符</span><span class="sxs-lookup"><span data-stu-id="894cb-116">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="894cb-117">如何：调用运算符过程</span><span class="sxs-lookup"><span data-stu-id="894cb-117">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="894cb-118">如何：使用定义运算符的类</span><span class="sxs-lookup"><span data-stu-id="894cb-118">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
- [<span data-ttu-id="894cb-119">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="894cb-119">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="894cb-120">Structure 语句</span><span class="sxs-lookup"><span data-stu-id="894cb-120">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="894cb-121">如何：声明结构</span><span class="sxs-lookup"><span data-stu-id="894cb-121">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="894cb-122">Mod 运算符</span><span class="sxs-lookup"><span data-stu-id="894cb-122">Mod Operator</span></span>](../../../../visual-basic/language-reference/operators/mod-operator.md)
