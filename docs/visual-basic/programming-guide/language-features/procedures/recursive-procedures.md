---
title: 递归过程 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: 1802785e38b58ce2c057d6ddbe1e54e73e079761
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660718"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="06a81-102">递归过程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06a81-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="06a81-103">一个*递归*过程是指调用其自身。</span><span class="sxs-lookup"><span data-stu-id="06a81-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="06a81-104">一般情况下，这不是编写 Visual Basic 代码的最有效方法。</span><span class="sxs-lookup"><span data-stu-id="06a81-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="06a81-105">以下过程使用递归来计算其原始自变量的阶乘。</span><span class="sxs-lookup"><span data-stu-id="06a81-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="06a81-106">递归过程的注意事项</span><span class="sxs-lookup"><span data-stu-id="06a81-106">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="06a81-107">**限制条件**。</span><span class="sxs-lookup"><span data-stu-id="06a81-107">**Limiting Conditions**.</span></span> <span data-ttu-id="06a81-108">必须设计的递归过程测试可以终止递归的至少一个条件和您还必须处理任何此类条件均在合理的递归调用数内的情况。</span><span class="sxs-lookup"><span data-stu-id="06a81-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="06a81-109">没有可以满足而不会出现的至少一个条件，您的过程在运行高风险的无限循环中执行。</span><span class="sxs-lookup"><span data-stu-id="06a81-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="06a81-110">**内存使用率**。</span><span class="sxs-lookup"><span data-stu-id="06a81-110">**Memory Usage**.</span></span> <span data-ttu-id="06a81-111">你的应用程序具有有限的数量的本地变量的空间。</span><span class="sxs-lookup"><span data-stu-id="06a81-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="06a81-112">每次过程调用其自身，将使用这些空间的详细信息为其本地变量的其他副本。</span><span class="sxs-lookup"><span data-stu-id="06a81-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="06a81-113">如果此过程将无限期地继续，则最终会导致<xref:System.StackOverflowException>错误。</span><span class="sxs-lookup"><span data-stu-id="06a81-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="06a81-114">**效率**。</span><span class="sxs-lookup"><span data-stu-id="06a81-114">**Efficiency**.</span></span> <span data-ttu-id="06a81-115">您几乎总是可以替换为递归循环。</span><span class="sxs-lookup"><span data-stu-id="06a81-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="06a81-116">循环没有初始化其他存储和返回值传递自变量的开销。</span><span class="sxs-lookup"><span data-stu-id="06a81-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="06a81-117">应用的性能可以更好的而无需递归调用。</span><span class="sxs-lookup"><span data-stu-id="06a81-117">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="06a81-118">**相互递归**。</span><span class="sxs-lookup"><span data-stu-id="06a81-118">**Mutual Recursion**.</span></span> <span data-ttu-id="06a81-119">你可能会发现性能非常差或甚至无限循环，如果两个过程相互调用。</span><span class="sxs-lookup"><span data-stu-id="06a81-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="06a81-120">这样的设计带来了在一个递归过程中，相同的问题，但很难检测和调试。</span><span class="sxs-lookup"><span data-stu-id="06a81-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="06a81-121">**使用括号调用**。</span><span class="sxs-lookup"><span data-stu-id="06a81-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="06a81-122">当`Function`过程调用其自身以递归方式，必须执行的过程名称使用括号，即使没有参数列表。</span><span class="sxs-lookup"><span data-stu-id="06a81-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="06a81-123">否则，执行的函数名称作为表示该函数的返回值。</span><span class="sxs-lookup"><span data-stu-id="06a81-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="06a81-124">**测试**。</span><span class="sxs-lookup"><span data-stu-id="06a81-124">**Testing**.</span></span> <span data-ttu-id="06a81-125">如果您编写一个递归过程时，应对其进行测试应非常小心以确保其始终满足某些限制条件。</span><span class="sxs-lookup"><span data-stu-id="06a81-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="06a81-126">你还应确保您不能运行由于递归调用过多的内存不足。</span><span class="sxs-lookup"><span data-stu-id="06a81-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06a81-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="06a81-127">See also</span></span>
- <xref:System.StackOverflowException>
- [<span data-ttu-id="06a81-128">过程</span><span class="sxs-lookup"><span data-stu-id="06a81-128">Procedures</span></span>](./index.md)
- [<span data-ttu-id="06a81-129">Sub 过程</span><span class="sxs-lookup"><span data-stu-id="06a81-129">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="06a81-130">Function 过程</span><span class="sxs-lookup"><span data-stu-id="06a81-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="06a81-131">属性过程</span><span class="sxs-lookup"><span data-stu-id="06a81-131">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="06a81-132">运算符过程</span><span class="sxs-lookup"><span data-stu-id="06a81-132">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="06a81-133">过程参数和自变量</span><span class="sxs-lookup"><span data-stu-id="06a81-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="06a81-134">过程重载</span><span class="sxs-lookup"><span data-stu-id="06a81-134">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="06a81-135">过程疑难解答</span><span class="sxs-lookup"><span data-stu-id="06a81-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="06a81-136">循环结构</span><span class="sxs-lookup"><span data-stu-id="06a81-136">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="06a81-137">异常疑难解答：System.StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="06a81-137">Troubleshooting Exceptions: System.StackOverflowException</span></span>](https://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
