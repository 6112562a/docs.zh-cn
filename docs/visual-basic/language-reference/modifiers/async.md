---
title: Async
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: 73d433c66750ead3a97b1c283cc26b4c43f078df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351631"
---
# <a name="async-visual-basic"></a><span data-ttu-id="24cac-102">Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24cac-102">Async (Visual Basic)</span></span>

<span data-ttu-id="24cac-103">The `Async` modifier indicates that the method or [lambda expression](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous.</span><span class="sxs-lookup"><span data-stu-id="24cac-103">The `Async` modifier indicates that the method or [lambda expression](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous.</span></span> <span data-ttu-id="24cac-104">Such methods are referred to as *async methods*.</span><span class="sxs-lookup"><span data-stu-id="24cac-104">Such methods are referred to as *async methods*.</span></span>

<span data-ttu-id="24cac-105">异步方法提供了一种简便方式来完成可能需要长时间运行的工作，而不必阻止调用方的线程。</span><span class="sxs-lookup"><span data-stu-id="24cac-105">An async method provides a convenient way to do potentially long-running work without blocking the caller's thread.</span></span> <span data-ttu-id="24cac-106">The caller of an async method can resume its work without waiting for the async method to finish.</span><span class="sxs-lookup"><span data-stu-id="24cac-106">The caller of an async method can resume its work without waiting for the async method to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="24cac-107">`Async` 和 `Await` 关键字是在 Visual Studio 2012 中引入的。</span><span class="sxs-lookup"><span data-stu-id="24cac-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="24cac-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="24cac-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="24cac-109">下面的示例显示一个异步方法的结构。</span><span class="sxs-lookup"><span data-stu-id="24cac-109">The following example shows the structure of an async method.</span></span> <span data-ttu-id="24cac-110">按照约定，异步方法名的结尾为“Async”。</span><span class="sxs-lookup"><span data-stu-id="24cac-110">By convention, async method names end in "Async."</span></span>

```vb
Public Async Function ExampleMethodAsync() As Task(Of Integer)
    ' . . .

    ' At the Await expression, execution in this method is suspended and,
    ' if AwaitedProcessAsync has not already finished, control returns
    ' to the caller of ExampleMethodAsync. When the awaited task is
    ' completed, this method resumes execution.
    Dim exampleInt As Integer = Await AwaitedProcessAsync()

    ' . . .

    ' The return statement completes the task. Any method that is
    ' awaiting ExampleMethodAsync can now get the integer result.
    Return exampleInt
End Function
```

<span data-ttu-id="24cac-111">Typically, a method modified by the `Async` keyword contains at least one [Await](../../../visual-basic/language-reference/modifiers/async.md) expression or statement.</span><span class="sxs-lookup"><span data-stu-id="24cac-111">Typically, a method modified by the `Async` keyword contains at least one [Await](../../../visual-basic/language-reference/modifiers/async.md) expression or statement.</span></span> <span data-ttu-id="24cac-112">方法同步运行，直至到达第一个 `Await`，此时暂停，直到等待的任务完成。</span><span class="sxs-lookup"><span data-stu-id="24cac-112">The method runs synchronously until it reaches the first `Await`, at which point it suspends until the awaited task completes.</span></span> <span data-ttu-id="24cac-113">同时，控制权返回给方法的调用方。</span><span class="sxs-lookup"><span data-stu-id="24cac-113">In the meantime, control is returned to the caller of the method.</span></span> <span data-ttu-id="24cac-114">If the method doesn't contain an `Await` expression or statement, the method isn't suspended and executes as a synchronous method does.</span><span class="sxs-lookup"><span data-stu-id="24cac-114">If the method doesn't contain an `Await` expression or statement, the method isn't suspended and executes as a synchronous method does.</span></span> <span data-ttu-id="24cac-115">A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error.</span><span class="sxs-lookup"><span data-stu-id="24cac-115">A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error.</span></span> <span data-ttu-id="24cac-116">For more information, see the [compiler error](../error-messages/bc42358.md).</span><span class="sxs-lookup"><span data-stu-id="24cac-116">For more information, see the [compiler error](../error-messages/bc42358.md).</span></span>

<span data-ttu-id="24cac-117">`Async` 关键字是一个非保留的关键字。</span><span class="sxs-lookup"><span data-stu-id="24cac-117">The `Async` keyword is an unreserved keyword.</span></span> <span data-ttu-id="24cac-118">在修饰方法或 lambda 表达式时，它是关键字。</span><span class="sxs-lookup"><span data-stu-id="24cac-118">It is a keyword when it modifies a method or a lambda expression.</span></span> <span data-ttu-id="24cac-119">在所有其他上下文中，都会将其解释为标识符。</span><span class="sxs-lookup"><span data-stu-id="24cac-119">In all other contexts, it is interpreted as an identifier.</span></span>

## <a name="return-types"></a><span data-ttu-id="24cac-120">返回类型</span><span class="sxs-lookup"><span data-stu-id="24cac-120">Return Types</span></span>

<span data-ttu-id="24cac-121">An async method is either a [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="24cac-121">An async method is either a [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="24cac-122">The method cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span><span class="sxs-lookup"><span data-stu-id="24cac-122">The method cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="24cac-123">You specify `Task(Of TResult)` for the return type of an async method if the [Return](../../../visual-basic/language-reference/statements/return-statement.md) statement of the method has an operand of type TResult.</span><span class="sxs-lookup"><span data-stu-id="24cac-123">You specify `Task(Of TResult)` for the return type of an async method if the [Return](../../../visual-basic/language-reference/statements/return-statement.md) statement of the method has an operand of type TResult.</span></span> <span data-ttu-id="24cac-124">如果当方法完成时未返回有意义的值，则应使用 `Task`。</span><span class="sxs-lookup"><span data-stu-id="24cac-124">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="24cac-125">即对方法的调用返回 `Task`，但 `Task` 完成时，等待 `Await` 的任何 `Task` 语句不会产生结果值。</span><span class="sxs-lookup"><span data-stu-id="24cac-125">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `Await` statement that's awaiting the `Task` doesn’t produce a result value.</span></span>

<span data-ttu-id="24cac-126">异步子例程主要用于定义需要 `Sub` 程序的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="24cac-126">Async subroutines are used primarily to define event handlers where a `Sub` procedure is required.</span></span> <span data-ttu-id="24cac-127">异步子程序的调用方不能等待它，并且无法捕获该方法引发的异常。</span><span class="sxs-lookup"><span data-stu-id="24cac-127">The caller of an async subroutine can't await it and can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="24cac-128">有关详细信息和示例，请参阅[异步返回类型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="24cac-128">For more information and examples, see [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="24cac-129">示例</span><span class="sxs-lookup"><span data-stu-id="24cac-129">Example</span></span>

<span data-ttu-id="24cac-130">下面的示例显示一个异步事件处理程序、一个异步 lambda 表达式和一个异步方法。</span><span class="sxs-lookup"><span data-stu-id="24cac-130">The following examples show an async event handler, an async lambda expression, and an async method.</span></span> <span data-ttu-id="24cac-131">For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="24cac-131">For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="24cac-132">可从[开发人员代码示例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)下载演练代码。</span><span class="sxs-lookup"><span data-stu-id="24cac-132">You can download the walkthrough code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

```vb
' An event handler must be a Sub procedure.
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click
    textBox1.Clear()
    ' SumPageSizesAsync is a method that returns a Task.
    Await SumPageSizesAsync()
    textBox1.Text = vbCrLf & "Control returned to button1_Click."
End Sub

' The following async lambda expression creates an equivalent anonymous
' event handler.
AddHandler button1.Click, Async Sub(sender, e)
                              textBox1.Clear()
                              ' SumPageSizesAsync is a method that returns a Task.
                              Await SumPageSizesAsync()
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."
                          End Sub

' The following async method returns a Task(Of T).
' A typical call awaits the Byte array result:
'      Dim result As Byte() = Await GetURLContents("https://msdn.com")
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

    ' The downloaded resource ends up in the variable named content.
    Dim content = New MemoryStream()

    ' Initialize an HttpWebRequest for the current URL.
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

    ' Send the request to the Internet resource and wait for
    ' the response.
    Using response As WebResponse = Await webReq.GetResponseAsync()
        ' Get the data stream that is associated with the specified URL.
        Using responseStream As Stream = response.GetResponseStream()
            ' Read the bytes in responseStream and copy them to content.
            ' CopyToAsync returns a Task, not a Task<T>.
            Await responseStream.CopyToAsync(content)
        End Using
    End Using

    ' Return the result as a byte array.
    Return content.ToArray()
End Function
```

## <a name="see-also"></a><span data-ttu-id="24cac-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="24cac-133">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="24cac-134">Await 运算符</span><span class="sxs-lookup"><span data-stu-id="24cac-134">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="24cac-135">使用 Async 和 Await 的异步编程</span><span class="sxs-lookup"><span data-stu-id="24cac-135">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="24cac-136">演练：使用 Async 和 Await 访问 Web</span><span class="sxs-lookup"><span data-stu-id="24cac-136">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
