---
title: = 运算符 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: d260dffb7175e9dddcbf9acb75415f5f973727e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962018"
---
# <a name="-operator-visual-basic"></a>= 运算符 (Visual Basic)
为变量或属性赋值。  
  
## <a name="syntax"></a>语法  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a>部件  
 `variableorproperty`  
 任何可写的变量或任何属性。  
  
 `value`  
 任何文本、常量或表达式。  
  
## <a name="remarks"></a>备注  
 等号 (`=`) 左侧的元素可以是简单的标量变量、属性或数组的元素。 变量或属性不能是[只读](../../../visual-basic/language-reference/modifiers/readonly.md)的。 `=`运算符将其右侧的值赋值给其左侧的变量或属性。  
  
> [!NOTE]
> `=`运算符也用作比较运算符。 有关详细信息, 请参阅[比较运算符](../../../visual-basic/language-reference/operators/comparison-operators.md)。  
  
## <a name="overloading"></a>重载  
 `=`运算符只能作为关系比较运算符重载, 而不能作为赋值运算符重载。 有关详细信息，请参阅 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## <a name="example"></a>示例  
 下面的示例演示了赋值运算符。 右侧的值将分配给左侧的变量。  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>请参阅

- [&= 运算符](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [*= 运算符](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [+= 运算符](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-= 运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [/= 运算符 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\\= 运算符](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [^= 运算符](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [语句](../../../visual-basic/programming-guide/language-features/statements.md)
- [比较运算符](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [局部类型推理](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
