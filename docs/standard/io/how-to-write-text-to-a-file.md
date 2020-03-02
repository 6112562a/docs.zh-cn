---
title: 如何：将文本写入文件
ms.date: 01/04/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
ms.openlocfilehash: ba1c1815f0e49c02d1f0ee3c48ba01b7c2f5e727
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160243"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="41755-102">如何：将文本写入文件</span><span class="sxs-lookup"><span data-stu-id="41755-102">How to: Write text to a file</span></span>
<span data-ttu-id="41755-103">本主题介绍将文本写入 .NET 应用文件的不同方法。</span><span class="sxs-lookup"><span data-stu-id="41755-103">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="41755-104">下面的类和方法通常用于将文本写入文件：</span><span class="sxs-lookup"><span data-stu-id="41755-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="41755-105"><xref:System.IO.StreamWriter> 包含同步写入文件的方法（<xref:System.IO.StreamWriter.Write%2A> 或 <xref:System.IO.TextWriter.WriteLine%2A>）或者异步写入文件的方法（<xref:System.IO.StreamWriter.WriteAsync%2A> 和 <xref:System.IO.StreamWriter.WriteLineAsync%2A>）。</span><span class="sxs-lookup"><span data-stu-id="41755-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="41755-106"><xref:System.IO.File> 提供了将文本写入文件的静态方法（例如，<xref:System.IO.File.WriteAllLines%2A> 和 <xref:System.IO.File.WriteAllText%2A>），或者向文件中追加文本的静态方法（例如，<xref:System.IO.File.AppendAllLines%2A>、<xref:System.IO.File.AppendAllText%2A> 和 <xref:System.IO.File.AppendText%2A>）。</span><span class="sxs-lookup"><span data-stu-id="41755-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="41755-107"><xref:System.IO.Path> 适用于包含文件或目录路径信息的字符串。</span><span class="sxs-lookup"><span data-stu-id="41755-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="41755-108">它包含 <xref:System.IO.Path.Combine%2A> 方法，在 .NET Core 2.1 及更高版本中包含 <xref:System.IO.Path.Join%2A> 和 <xref:System.IO.Path.TryJoin%2A> 方法，允许串联字符串以生成文件或目录路径。</span><span class="sxs-lookup"><span data-stu-id="41755-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="41755-109">以下示例仅显示所需的最少代码量。</span><span class="sxs-lookup"><span data-stu-id="41755-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="41755-110">实际的应用通常提供更可靠的错误检查和异常处理。</span><span class="sxs-lookup"><span data-stu-id="41755-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="41755-111">示例：使用 StreamWriter 同步写入文本</span><span class="sxs-lookup"><span data-stu-id="41755-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="41755-112">以下示例演示如何使用 <xref:System.IO.StreamWriter> 类，一次一行同步地将文本写入新文件。</span><span class="sxs-lookup"><span data-stu-id="41755-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="41755-113">因为在 <xref:System.IO.StreamWriter> 语句中已声明并实例化 `using` 对象，所以会调用自动刷新并关闭流的 <xref:System.IO.StreamWriter.Dispose%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="41755-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="41755-114">示例：使用 StreamWriter 同步追加文本</span><span class="sxs-lookup"><span data-stu-id="41755-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="41755-115">以下示例演示如何使用 <xref:System.IO.StreamWriter> 类以同步方式将文本追加到第一个示例中创建的文本文件。</span><span class="sxs-lookup"><span data-stu-id="41755-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="41755-116">示例：使用 StreamWriter 异步写入文本</span><span class="sxs-lookup"><span data-stu-id="41755-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="41755-117">下面的示例演示如何使用 <xref:System.IO.StreamWriter> 类异步地将文本写入新文件。</span><span class="sxs-lookup"><span data-stu-id="41755-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="41755-118">要调用 <xref:System.IO.StreamWriter.WriteAsync%2A> 方法，方法调用必须在 `async` 方法内。</span><span class="sxs-lookup"><span data-stu-id="41755-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="41755-119">C# 示例需要 C# 7.1或更高版本，这会在对程序入口点上增加对 `async` 修饰符的支持。</span><span class="sxs-lookup"><span data-stu-id="41755-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="41755-120">示例：使用文件类编写和追加文本</span><span class="sxs-lookup"><span data-stu-id="41755-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="41755-121">下面的示例演示如何使用 <xref:System.IO.File> 类将文本写入新文件并将新的文本行追加到同一文件。</span><span class="sxs-lookup"><span data-stu-id="41755-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="41755-122"><xref:System.IO.File.WriteAllText%2A> 和 <xref:System.IO.File.AppendAllLines%2A> 方法会自动打开和关闭文件。</span><span class="sxs-lookup"><span data-stu-id="41755-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="41755-123">如果提供给 <xref:System.IO.File.WriteAllText%2A> 方法的路径已存在，则覆盖该文件。</span><span class="sxs-lookup"><span data-stu-id="41755-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="41755-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="41755-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="41755-125">如何：枚举目录和文件</span><span class="sxs-lookup"><span data-stu-id="41755-125">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="41755-126">如何：对新建的数据文件进行读取和写入</span><span class="sxs-lookup"><span data-stu-id="41755-126">How to: Read and write to a newly-created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="41755-127">如何：打开并追加到日志文件</span><span class="sxs-lookup"><span data-stu-id="41755-127">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="41755-128">如何：从文件中读取文本</span><span class="sxs-lookup"><span data-stu-id="41755-128">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="41755-129">文件和流 I/O</span><span class="sxs-lookup"><span data-stu-id="41755-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
