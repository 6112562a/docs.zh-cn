---
title: 异步文件 I/O
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET Framework], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b39373239d6aefaa671afebbb85dc2156866358f
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204805"
---
# <a name="asynchronous-file-io"></a><span data-ttu-id="4adeb-102">异步文件 I/O</span><span class="sxs-lookup"><span data-stu-id="4adeb-102">Asynchronous File I/O</span></span>

<span data-ttu-id="4adeb-103">异步操作使您能在不阻塞主线程的情况下执行占用大量资源的 I/O 操作。</span><span class="sxs-lookup"><span data-stu-id="4adeb-103">Asynchronous operations enable you to perform resource-intensive I/O operations without blocking the main thread.</span></span> <span data-ttu-id="4adeb-104">在 Windows 8.x 应用商店应用或桌面应用中一个耗时的流操作可能阻塞 UI 线程并让应用看起来好像不工作时，这种性能的考虑就显得尤为重要了。</span><span class="sxs-lookup"><span data-stu-id="4adeb-104">This performance consideration is particularly important in a Windows 8.x Store app or desktop app where a time-consuming stream operation can block the UI thread and make your app appear as if it is not working.</span></span>

<span data-ttu-id="4adeb-105">从 .NET Framework 4.5 开始，I/O 类型包括异步方法来简化异步操作。</span><span class="sxs-lookup"><span data-stu-id="4adeb-105">Starting with the .NET Framework 4.5, the I/O types include async methods to simplify asynchronous operations.</span></span> <span data-ttu-id="4adeb-106">异步方法在其名称中包括 `Async` ，例如 <xref:System.IO.Stream.ReadAsync%2A>、 <xref:System.IO.Stream.WriteAsync%2A>、 <xref:System.IO.Stream.CopyToAsync%2A>、 <xref:System.IO.Stream.FlushAsync%2A>、 <xref:System.IO.TextReader.ReadLineAsync%2A>和 <xref:System.IO.TextReader.ReadToEndAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="4adeb-106">An async method contains `Async` in its name, such as <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, and <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span></span> <span data-ttu-id="4adeb-107">这些异步方法基于流类（例如 <xref:System.IO.Stream>、 <xref:System.IO.FileStream>和 <xref:System.IO.MemoryStream>）和用来向流中读出或写入数据的类（例如 <xref:System.IO.TextReader> 和 <xref:System.IO.TextWriter>）实现。</span><span class="sxs-lookup"><span data-stu-id="4adeb-107">These async methods are implemented on stream classes, such as <xref:System.IO.Stream>, <xref:System.IO.FileStream>, and <xref:System.IO.MemoryStream>, and on classes that are used for reading from or writing to streams, such <xref:System.IO.TextReader> and <xref:System.IO.TextWriter>.</span></span>

<span data-ttu-id="4adeb-108">在 .NET Framework 4 和更早的版本中，您必须使用 <xref:System.IO.Stream.BeginRead%2A> 和 <xref:System.IO.Stream.EndRead%2A> 之类的方法来实现异步 I/O 操作。</span><span class="sxs-lookup"><span data-stu-id="4adeb-108">In the .NET Framework 4 and earlier versions, you have to use methods such as <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> to implement asynchronous I/O operations.</span></span> <span data-ttu-id="4adeb-109">这些方法仍然在 .NET Framework 4.5 中可用，从而支持传统的代码；但是，异步方法能帮助你更轻松地实现异步 I/O 操作。</span><span class="sxs-lookup"><span data-stu-id="4adeb-109">These methods are still available in the .NET Framework 4.5 to support legacy code; however, the async methods help you implement asynchronous I/O operations more easily.</span></span>

<span data-ttu-id="4adeb-110">C# 和 Visual Basic 分别具有两个用于异步编程的关键字：</span><span class="sxs-lookup"><span data-stu-id="4adeb-110">C# and Visual Basic each have two keywords for asynchronous programming:</span></span>

- <span data-ttu-id="4adeb-111">`Async` (Visual Basic) 或 `async` (C#) 修饰符，您可以用来标记包含异步操作的方法。</span><span class="sxs-lookup"><span data-stu-id="4adeb-111">`Async` (Visual Basic) or `async` (C#) modifier, which is used to mark a method that contains an asynchronous operation.</span></span>

- <span data-ttu-id="4adeb-112">`Await` (Visual Basic) 或 `await` (C#) 运算符，可以应用到异步方法的结果中。</span><span class="sxs-lookup"><span data-stu-id="4adeb-112">`Await` (Visual Basic) or `await` (C#) operator, which is applied to the result of an async method.</span></span>

<span data-ttu-id="4adeb-113">如下面的示例所示，若要实现异步 I/O 操作，请把这些关键字和异步方法结合使用。</span><span class="sxs-lookup"><span data-stu-id="4adeb-113">To implement asynchronous I/O operations, use these keywords in conjunction with the async methods, as shown in the following examples.</span></span> <span data-ttu-id="4adeb-114">有关详细信息，请参阅[使用 async 和 await 的异步编程 (C#)](../../csharp/programming-guide/concepts/async/index.md) 或 [使用 Async 和 Await 的异步编程 (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="4adeb-114">For more information, see [Asynchronous programming with async and await (C#)](../../csharp/programming-guide/concepts/async/index.md) or [Asynchronous Programming with Async and Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="4adeb-115">下面的示例演示如何使用两个 <xref:System.IO.FileStream> 对象把文件从一个目录异步复制到另一个目录。</span><span class="sxs-lookup"><span data-stu-id="4adeb-115">The following example demonstrates how to use two <xref:System.IO.FileStream> objects to copy files asynchronously from one directory to another.</span></span> <span data-ttu-id="4adeb-116">需要注意 <xref:System.Web.UI.WebControls.Button.Click> 控件的 <xref:System.Windows.Controls.Button> 事件处理程序具有 `async` 修饰符标记，因为它调用异步方法。</span><span class="sxs-lookup"><span data-stu-id="4adeb-116">Notice that the <xref:System.Web.UI.WebControls.Button.Click> event handler for the <xref:System.Windows.Controls.Button> control is marked with the `async` modifier because it calls an asynchronous method.</span></span>

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

<span data-ttu-id="4adeb-117">下一个例子类似于前面的例子，但是使用 <xref:System.IO.StreamReader> 和 <xref:System.IO.StreamWriter> 对象以异步方式读取和写入文本文件的内容。</span><span class="sxs-lookup"><span data-stu-id="4adeb-117">The next example is similar to the previous one but uses <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> objects to read and write the contents of a text file asynchronously.</span></span>

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

<span data-ttu-id="4adeb-118">下一个示例演示用于在 Windows 8.x 应用商店应用中以 <xref:System.IO.Stream> 的形式打开文件的代码隐藏文件和 XAML 文件，并且通过使用 <xref:System.IO.StreamReader> 类的实例来读取其内容。</span><span class="sxs-lookup"><span data-stu-id="4adeb-118">The next example shows the code-behind file and the XAML file that are used to open a file as a <xref:System.IO.Stream> in a Windows 8.x Store app, and read its contents by using an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="4adeb-119">它使用异步方法以流的形式打开文件并读取其内容。</span><span class="sxs-lookup"><span data-stu-id="4adeb-119">It uses asynchronous methods to open the file as a stream and to read its contents.</span></span>

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="4adeb-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="4adeb-120">See also</span></span>

- <xref:System.IO.Stream>
- [<span data-ttu-id="4adeb-121">文件和流 I/O</span><span class="sxs-lookup"><span data-stu-id="4adeb-121">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="4adeb-122">使用 Async 和 Await 的异步编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="4adeb-122">Asynchronous programming with async and await (C#)</span></span>](../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="4adeb-123">使用 Async 和 Await 的异步编程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4adeb-123">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
