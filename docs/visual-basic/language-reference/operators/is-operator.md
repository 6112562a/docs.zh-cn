---
title: Is 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 52fbb39ab0a36c8b947b78f464fad26be05ce204
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349532"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="871ca-102">Is 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="871ca-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="871ca-103">Compares two object reference variables.</span><span class="sxs-lookup"><span data-stu-id="871ca-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="871ca-104">语法</span><span class="sxs-lookup"><span data-stu-id="871ca-104">Syntax</span></span>  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="871ca-105">部件</span><span class="sxs-lookup"><span data-stu-id="871ca-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="871ca-106">必须的。</span><span class="sxs-lookup"><span data-stu-id="871ca-106">Required.</span></span> <span data-ttu-id="871ca-107">Any `Boolean` value.</span><span class="sxs-lookup"><span data-stu-id="871ca-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="871ca-108">必须的。</span><span class="sxs-lookup"><span data-stu-id="871ca-108">Required.</span></span> <span data-ttu-id="871ca-109">Any `Object` name.</span><span class="sxs-lookup"><span data-stu-id="871ca-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="871ca-110">必须的。</span><span class="sxs-lookup"><span data-stu-id="871ca-110">Required.</span></span> <span data-ttu-id="871ca-111">Any `Object` name.</span><span class="sxs-lookup"><span data-stu-id="871ca-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="871ca-112">备注</span><span class="sxs-lookup"><span data-stu-id="871ca-112">Remarks</span></span>  
 <span data-ttu-id="871ca-113">The `Is` operator determines if two object references refer to the same object.</span><span class="sxs-lookup"><span data-stu-id="871ca-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="871ca-114">However, it does not perform value comparisons.</span><span class="sxs-lookup"><span data-stu-id="871ca-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="871ca-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span><span class="sxs-lookup"><span data-stu-id="871ca-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="871ca-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span><span class="sxs-lookup"><span data-stu-id="871ca-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="871ca-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="871ca-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="871ca-118">示例</span><span class="sxs-lookup"><span data-stu-id="871ca-118">Example</span></span>  
 <span data-ttu-id="871ca-119">The following example uses the `Is` operator to compare pairs of object references.</span><span class="sxs-lookup"><span data-stu-id="871ca-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="871ca-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span><span class="sxs-lookup"><span data-stu-id="871ca-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="871ca-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span><span class="sxs-lookup"><span data-stu-id="871ca-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="871ca-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="871ca-122">See also</span></span>

- [<span data-ttu-id="871ca-123">TypeOf 运算符</span><span class="sxs-lookup"><span data-stu-id="871ca-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="871ca-124">IsNot 运算符</span><span class="sxs-lookup"><span data-stu-id="871ca-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="871ca-125">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="871ca-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="871ca-126">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="871ca-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="871ca-127">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="871ca-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="871ca-128">运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="871ca-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
