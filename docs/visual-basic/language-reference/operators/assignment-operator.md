---
title: = 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 75f303219b9bf32613989f65f90a9096ef70e02e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350205"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="0bf1c-102">= 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0bf1c-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="0bf1c-103">为变量或属性赋值。</span><span class="sxs-lookup"><span data-stu-id="0bf1c-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bf1c-104">语法</span><span class="sxs-lookup"><span data-stu-id="0bf1c-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="0bf1c-105">部件</span><span class="sxs-lookup"><span data-stu-id="0bf1c-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="0bf1c-106">任何可写的变量或任何属性。</span><span class="sxs-lookup"><span data-stu-id="0bf1c-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="0bf1c-107">任何文本、常量或表达式。</span><span class="sxs-lookup"><span data-stu-id="0bf1c-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bf1c-108">备注</span><span class="sxs-lookup"><span data-stu-id="0bf1c-108">Remarks</span></span>  
 <span data-ttu-id="0bf1c-109">等号（`=`）左侧的元素可以是简单的标量变量、属性或数组的元素。</span><span class="sxs-lookup"><span data-stu-id="0bf1c-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="0bf1c-110">变量或属性不能是[只读](../../../visual-basic/language-reference/modifiers/readonly.md)的。</span><span class="sxs-lookup"><span data-stu-id="0bf1c-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="0bf1c-111">`=` 运算符将其右侧的值赋值给其左侧的变量或属性。</span><span class="sxs-lookup"><span data-stu-id="0bf1c-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0bf1c-112">`=` 运算符也用作比较运算符。</span><span class="sxs-lookup"><span data-stu-id="0bf1c-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="0bf1c-113">有关详细信息，请参阅[比较运算符](../../../visual-basic/language-reference/operators/comparison-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="0bf1c-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0bf1c-114">重载</span><span class="sxs-lookup"><span data-stu-id="0bf1c-114">Overloading</span></span>  
 <span data-ttu-id="0bf1c-115">只能将 `=` 运算符作为关系比较运算符重载，而不能作为赋值运算符重载。</span><span class="sxs-lookup"><span data-stu-id="0bf1c-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="0bf1c-116">有关更多信息，请参见 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="0bf1c-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bf1c-117">示例</span><span class="sxs-lookup"><span data-stu-id="0bf1c-117">Example</span></span>  
 <span data-ttu-id="0bf1c-118">下面的示例演示了赋值运算符。</span><span class="sxs-lookup"><span data-stu-id="0bf1c-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="0bf1c-119">右侧的值将分配给左侧的变量。</span><span class="sxs-lookup"><span data-stu-id="0bf1c-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="0bf1c-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0bf1c-120">See also</span></span>

- [<span data-ttu-id="0bf1c-121">&= 运算符</span><span class="sxs-lookup"><span data-stu-id="0bf1c-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="0bf1c-122">\*= 运算符</span><span class="sxs-lookup"><span data-stu-id="0bf1c-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="0bf1c-123">+= 运算符</span><span class="sxs-lookup"><span data-stu-id="0bf1c-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="0bf1c-124">-= 运算符（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="0bf1c-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="0bf1c-125">/= 运算符（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="0bf1c-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="0bf1c-126">\\= 运算符</span><span class="sxs-lookup"><span data-stu-id="0bf1c-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="0bf1c-127">^= 运算符</span><span class="sxs-lookup"><span data-stu-id="0bf1c-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="0bf1c-128">语句</span><span class="sxs-lookup"><span data-stu-id="0bf1c-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="0bf1c-129">比较运算符</span><span class="sxs-lookup"><span data-stu-id="0bf1c-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="0bf1c-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="0bf1c-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="0bf1c-131">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="0bf1c-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
