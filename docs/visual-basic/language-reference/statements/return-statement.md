---
title: Return 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: 7f8ec0456576133d37dd19b5c0f8878a7ac57dab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831718"
---
# <a name="return-statement-visual-basic"></a><span data-ttu-id="c6fd3-102">Return 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6fd3-102">Return Statement (Visual Basic)</span></span>
<span data-ttu-id="c6fd3-103">将控制返回给调用的代码`Function`， `Sub`， `Get`， `Set`，或`Operator`过程。</span><span class="sxs-lookup"><span data-stu-id="c6fd3-103">Returns control to the code that called a `Function`, `Sub`, `Get`, `Set`, or `Operator` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6fd3-104">语法</span><span class="sxs-lookup"><span data-stu-id="c6fd3-104">Syntax</span></span>  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a><span data-ttu-id="c6fd3-105">部件</span><span class="sxs-lookup"><span data-stu-id="c6fd3-105">Part</span></span>  
 `expression`  
 <span data-ttu-id="c6fd3-106">在所需`Function`， `Get`，或`Operator`过程。</span><span class="sxs-lookup"><span data-stu-id="c6fd3-106">Required in a `Function`, `Get`, or `Operator` procedure.</span></span> <span data-ttu-id="c6fd3-107">表示要返回到调用代码的值的表达式。</span><span class="sxs-lookup"><span data-stu-id="c6fd3-107">Expression that represents the value to be returned to the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6fd3-108">备注</span><span class="sxs-lookup"><span data-stu-id="c6fd3-108">Remarks</span></span>  
 <span data-ttu-id="c6fd3-109">在中`Sub`或`Set`过程中，`Return`语句是等效于`Exit Sub`或`Exit Property`语句中，和`expression`不得提供。</span><span class="sxs-lookup"><span data-stu-id="c6fd3-109">In a `Sub` or `Set` procedure, the `Return` statement is equivalent to an `Exit Sub` or `Exit Property` statement, and `expression` must not be supplied.</span></span>  
  
 <span data-ttu-id="c6fd3-110">在中`Function`， `Get`，或`Operator`过程中，`Return`语句必须包括`expression`，和`expression`的计算结果必须为数据类型转换为该过程的返回类型。</span><span class="sxs-lookup"><span data-stu-id="c6fd3-110">In a `Function`, `Get`, or `Operator` procedure, the `Return` statement must include `expression`, and `expression` must evaluate to a data type that is convertible to the return type of the procedure.</span></span> <span data-ttu-id="c6fd3-111">在中`Function`或`Get`过程中，您还可以选择将表达式分配给要用作返回值的过程名称，然后执行`Exit Function`或`Exit Property`语句。</span><span class="sxs-lookup"><span data-stu-id="c6fd3-111">In a `Function` or `Get` procedure, you also have the alternative of assigning an expression to the procedure name to serve as the return value, and then executing an `Exit Function` or `Exit Property` statement.</span></span> <span data-ttu-id="c6fd3-112">在中`Operator`过程中，必须使用`Return expression`。</span><span class="sxs-lookup"><span data-stu-id="c6fd3-112">In an `Operator` procedure, you must use `Return expression`.</span></span>  
  
 <span data-ttu-id="c6fd3-113">可以包括任意多个`Return`根据需要在同一过程中的语句。</span><span class="sxs-lookup"><span data-stu-id="c6fd3-113">You can include as many `Return` statements as appropriate in the same procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6fd3-114">中的代码`Finally`块运行`Return`中的语句`Try`或`Catch`块是遇到，但在之前的`Return`语句执行。</span><span class="sxs-lookup"><span data-stu-id="c6fd3-114">The code in a `Finally` block runs after a `Return` statement in a `Try` or `Catch` block is encountered, but before that `Return` statement executes.</span></span> <span data-ttu-id="c6fd3-115">一个`Return`语句不能包括在`Finally`块。</span><span class="sxs-lookup"><span data-stu-id="c6fd3-115">A `Return` statement cannot be included in a `Finally` block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6fd3-116">示例</span><span class="sxs-lookup"><span data-stu-id="c6fd3-116">Example</span></span>  
 <span data-ttu-id="c6fd3-117">下面的示例使用`Return`语句数次以返回到调用代码时该过程无需执行任何其他操作。</span><span class="sxs-lookup"><span data-stu-id="c6fd3-117">The following example uses the `Return` statement several times to return to the calling code when the procedure does not have to do anything else.</span></span>  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a><span data-ttu-id="c6fd3-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="c6fd3-118">See also</span></span>

- [<span data-ttu-id="c6fd3-119">Function 语句</span><span class="sxs-lookup"><span data-stu-id="c6fd3-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="c6fd3-120">Sub 语句</span><span class="sxs-lookup"><span data-stu-id="c6fd3-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="c6fd3-121">Get 语句</span><span class="sxs-lookup"><span data-stu-id="c6fd3-121">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="c6fd3-122">Set 语句</span><span class="sxs-lookup"><span data-stu-id="c6fd3-122">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="c6fd3-123">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="c6fd3-123">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="c6fd3-124">Property 语句</span><span class="sxs-lookup"><span data-stu-id="c6fd3-124">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="c6fd3-125">Exit 语句</span><span class="sxs-lookup"><span data-stu-id="c6fd3-125">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="c6fd3-126">Try...Catch...Finally 语句</span><span class="sxs-lookup"><span data-stu-id="c6fd3-126">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
