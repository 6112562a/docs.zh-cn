---
title: Yield 语句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: fea91731694f18625e43c5545b353851e72234a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821083"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="1bc16-102">Yield 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bc16-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="1bc16-103">将发送到集合的下一个元素`For Each...Next`语句。</span><span class="sxs-lookup"><span data-stu-id="1bc16-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bc16-104">语法</span><span class="sxs-lookup"><span data-stu-id="1bc16-104">Syntax</span></span>  
  
```  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bc16-105">参数</span><span class="sxs-lookup"><span data-stu-id="1bc16-105">Parameters</span></span>  
  
|<span data-ttu-id="1bc16-106">术语</span><span class="sxs-lookup"><span data-stu-id="1bc16-106">Term</span></span>|<span data-ttu-id="1bc16-107">定义</span><span class="sxs-lookup"><span data-stu-id="1bc16-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="1bc16-108">必需。</span><span class="sxs-lookup"><span data-stu-id="1bc16-108">Required.</span></span> <span data-ttu-id="1bc16-109">隐式转换为迭代器函数的类型的表达式或`Get`访问器，它包含`Yield`语句。</span><span class="sxs-lookup"><span data-stu-id="1bc16-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bc16-110">备注</span><span class="sxs-lookup"><span data-stu-id="1bc16-110">Remarks</span></span>  
 <span data-ttu-id="1bc16-111">`Yield`语句返回的集合一次一个元素。</span><span class="sxs-lookup"><span data-stu-id="1bc16-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="1bc16-112">`Yield`语句包含在迭代器函数或`Get`访问器，它对集合执行自定义迭代。</span><span class="sxs-lookup"><span data-stu-id="1bc16-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="1bc16-113">通过使用迭代器函数[为每个...下一条语句](../../../visual-basic/language-reference/statements/for-each-next-statement.md)或 LINQ 查询。</span><span class="sxs-lookup"><span data-stu-id="1bc16-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="1bc16-114">每次迭代`For Each`循环调用迭代器函数。</span><span class="sxs-lookup"><span data-stu-id="1bc16-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="1bc16-115">当`Yield`语句到达迭代器函数中`expression`返回，并保留在代码中当前的位置。</span><span class="sxs-lookup"><span data-stu-id="1bc16-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="1bc16-116">下次调用迭代器函数时，将从该位置重新开始执行。</span><span class="sxs-lookup"><span data-stu-id="1bc16-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="1bc16-117">必须存在从类型的隐式转换`expression`在`Yield`到迭代器的返回类型的语句。</span><span class="sxs-lookup"><span data-stu-id="1bc16-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="1bc16-118">可以使用`Exit Function`或`Return`语句来终止迭代。</span><span class="sxs-lookup"><span data-stu-id="1bc16-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="1bc16-119">"Yield"不是保留的字且仅当使用中时，它具有特殊含义`Iterator`函数或`Get`访问器。</span><span class="sxs-lookup"><span data-stu-id="1bc16-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="1bc16-120">有关迭代器函数的详细信息和`Get`访问器，请参阅[迭代器](../../programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc16-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="1bc16-121">迭代器函数和 Get 访问器</span><span class="sxs-lookup"><span data-stu-id="1bc16-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="1bc16-122">迭代器函数的声明或`Get`访问器必须满足以下要求：</span><span class="sxs-lookup"><span data-stu-id="1bc16-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="1bc16-123">它必须包括[迭代器](../../../visual-basic/language-reference/modifiers/iterator.md)修饰符。</span><span class="sxs-lookup"><span data-stu-id="1bc16-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
-   <span data-ttu-id="1bc16-124">返回类型必须为 <xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator> 或 <xref:System.Collections.Generic.IEnumerator%601>。</span><span class="sxs-lookup"><span data-stu-id="1bc16-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="1bc16-125">它不能有任何`ByRef`参数。</span><span class="sxs-lookup"><span data-stu-id="1bc16-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="1bc16-126">迭代器函数不能在事件、 实例构造函数、 静态构造函数或静态析构函数中。</span><span class="sxs-lookup"><span data-stu-id="1bc16-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="1bc16-127">迭代器函数可以是匿名函数。</span><span class="sxs-lookup"><span data-stu-id="1bc16-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="1bc16-128">有关更多信息，请参见 [迭代器](../../programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc16-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="1bc16-129">异常处理</span><span class="sxs-lookup"><span data-stu-id="1bc16-129">Exception Handling</span></span>  
 <span data-ttu-id="1bc16-130">一个`Yield`语句可以是内部`Try`块[尝试...Catch...Finally 语句](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc16-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="1bc16-131">一个`Try`具有的块`Yield`语句可以有`Catch`阻止，并且可以具有`Finally`块。</span><span class="sxs-lookup"><span data-stu-id="1bc16-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="1bc16-132">一个`Yield`语句不能包含在内`Catch`块或`Finally`块。</span><span class="sxs-lookup"><span data-stu-id="1bc16-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="1bc16-133">如果`For Each`正文 （之外的迭代器函数） 会引发异常，`Catch`未执行迭代器函数中的块，但`Finally`执行迭代器函数中的块。</span><span class="sxs-lookup"><span data-stu-id="1bc16-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="1bc16-134">一个`Catch`迭代器函数内的块将捕获在迭代器函数内部发生的异常。</span><span class="sxs-lookup"><span data-stu-id="1bc16-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="1bc16-135">技术实现</span><span class="sxs-lookup"><span data-stu-id="1bc16-135">Technical Implementation</span></span>  
 <span data-ttu-id="1bc16-136">下面的代码返回`IEnumerable (Of String)`从迭代器函数，然后循环访问的元素`IEnumerable (Of String)`。</span><span class="sxs-lookup"><span data-stu-id="1bc16-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="1bc16-137">对调用`MyIteratorFunction`不会执行该函数的主体。</span><span class="sxs-lookup"><span data-stu-id="1bc16-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="1bc16-138">相反，该调用会将 `IEnumerable(Of String)` 返回到 `elements` 变量中。</span><span class="sxs-lookup"><span data-stu-id="1bc16-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="1bc16-139">在 `For Each` 循环迭代时，将为 <xref:System.Collections.IEnumerator.MoveNext%2A> 调用 `elements` 方法。</span><span class="sxs-lookup"><span data-stu-id="1bc16-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="1bc16-140">此调用将执行 `MyIteratorFunction` 的主体，直至到达下一个 `Yield` 语句。</span><span class="sxs-lookup"><span data-stu-id="1bc16-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="1bc16-141">`Yield`语句返回一个表达式，用于确定的值不仅`element`循环体使用的变量，但还<xref:System.Collections.Generic.IEnumerator%601.Current%2A>属性的元素，它是`IEnumerable (Of String)`。</span><span class="sxs-lookup"><span data-stu-id="1bc16-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="1bc16-142">在 `For Each` 循环的每个后续迭代中，迭代器主体的执行将从它暂停的位置继续，直至到达 `Yield` 语句后才会停止。</span><span class="sxs-lookup"><span data-stu-id="1bc16-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="1bc16-143">`For Each`循环完成时的迭代器函数末尾或`Return`或`Exit Function`到达语句。</span><span class="sxs-lookup"><span data-stu-id="1bc16-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bc16-144">示例</span><span class="sxs-lookup"><span data-stu-id="1bc16-144">Example</span></span>  
 <span data-ttu-id="1bc16-145">下面的示例有`Yield`内的语句[为...下一步](../../../visual-basic/language-reference/statements/for-next-statement.md)循环。</span><span class="sxs-lookup"><span data-stu-id="1bc16-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="1bc16-146">每次迭代[为每个](../../../visual-basic/language-reference/statements/for-each-next-statement.md)在语句体`Main`会调用`Power`迭代器函数。</span><span class="sxs-lookup"><span data-stu-id="1bc16-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="1bc16-147">对迭代器函数的每个调用将继续到 `Yield` 语句的下一次执行（在 `For…Next` 循环的下一次迭代期间发生）。</span><span class="sxs-lookup"><span data-stu-id="1bc16-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="1bc16-148">迭代器方法的返回类型是<xref:System.Collections.Generic.IEnumerable%601>，迭代器接口类型。</span><span class="sxs-lookup"><span data-stu-id="1bc16-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="1bc16-149">当调用迭代器方法时，它将返回一个包含数字幂的可枚举对象。</span><span class="sxs-lookup"><span data-stu-id="1bc16-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="1bc16-150">示例</span><span class="sxs-lookup"><span data-stu-id="1bc16-150">Example</span></span>  
 <span data-ttu-id="1bc16-151">下面的示例演示一个作为迭代器的 `Get` 访问器。</span><span class="sxs-lookup"><span data-stu-id="1bc16-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="1bc16-152">属性声明包含`Iterator`修饰符。</span><span class="sxs-lookup"><span data-stu-id="1bc16-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="1bc16-153">有关其他示例，请参阅[迭代器](../../programming-guide/concepts/iterators.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc16-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc16-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="1bc16-154">See also</span></span>

- [<span data-ttu-id="1bc16-155">语句</span><span class="sxs-lookup"><span data-stu-id="1bc16-155">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
