---
title: 如何：从文件中读取文本
ms.date: 06/19/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f667b0a757a676788b693691504512dfc227a7e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646667"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="19800-102">如何：从文件中读取文本</span><span class="sxs-lookup"><span data-stu-id="19800-102">How to: Read Text from a File</span></span>
<span data-ttu-id="19800-103">下面的示例演示如何使用适用于桌面应用的 .NET 以异步方式和同步方式从文本文件中读取文本。</span><span class="sxs-lookup"><span data-stu-id="19800-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="19800-104">在这两个示例中，当你创建 <xref:System.IO.StreamReader> 类的实例时，你会提供文件的绝对路径或相对路径。</span><span class="sxs-lookup"><span data-stu-id="19800-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span> <span data-ttu-id="19800-105">以下示例假定名为 TestFile.txt 的文件位于此应用程序所在的文件夹中。</span><span class="sxs-lookup"><span data-stu-id="19800-105">The following examples assume that the file named TestFile.txt is in the same folder as the application.</span></span>  
  
 <span data-ttu-id="19800-106">这些代码示例不适用于针对 Windows 应用商店应用的开发，因为 Windows 运行时提供了对文件进行读写操作的不同的流类型。</span><span class="sxs-lookup"><span data-stu-id="19800-106">These code examples do not apply to developing for Windows Store Apps because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="19800-107">有关演示如何在 Microsoft Store 应用中读取文件文本的示例，请参阅[快速入门：对文件执行读取和写入操作](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10))。</span><span class="sxs-lookup"><span data-stu-id="19800-107">For an example that shows how to read text from a file in a Windows Store app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="19800-108">有关演示如何在 .NET Framework 流和 Windows 运行时流之间进行转换的示例，请参阅[如何：在 .NET Framework 流和 Windows 运行时流之间进行转换](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)。</span><span class="sxs-lookup"><span data-stu-id="19800-108">For examples that show how to convert between .NET Framework streams and Windows runtime streams, see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19800-109">示例</span><span class="sxs-lookup"><span data-stu-id="19800-109">Example</span></span>  
 <span data-ttu-id="19800-110">以下示例演示控制台应用程序中的同步读取操作。</span><span class="sxs-lookup"><span data-stu-id="19800-110">The following example shows a synchronous read operation within a console application.</span></span> <span data-ttu-id="19800-111">在此示例中，使用流读取器打开文本文件，将内容复制到一个字符串中，然后将字符串输出到控制台。</span><span class="sxs-lookup"><span data-stu-id="19800-111">In this example, the text file is opened using a stream reader, the contents are copied to a string, and the string is output to the console.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="19800-112">示例</span><span class="sxs-lookup"><span data-stu-id="19800-112">Example</span></span>  
 <span data-ttu-id="19800-113">以下示例演示 Windows Presentation Foundation (WPF) 应用程序中的异步读取操作。</span><span class="sxs-lookup"><span data-stu-id="19800-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="19800-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="19800-114">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- [<span data-ttu-id="19800-115">Asynchronous File I/O</span><span class="sxs-lookup"><span data-stu-id="19800-115">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
- [<span data-ttu-id="19800-116">NIB：如何：创建目录列表</span><span class="sxs-lookup"><span data-stu-id="19800-116">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)
- [<span data-ttu-id="19800-117">快速入门：读取和写入文件</span><span class="sxs-lookup"><span data-stu-id="19800-117">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)
- [<span data-ttu-id="19800-118">如何：在 .NET Framework 流和 Windows 运行时流之间进行转换</span><span class="sxs-lookup"><span data-stu-id="19800-118">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
- [<span data-ttu-id="19800-119">如何：对新建的数据文件进行读取和写入</span><span class="sxs-lookup"><span data-stu-id="19800-119">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="19800-120">如何：打开并追加到日志文件</span><span class="sxs-lookup"><span data-stu-id="19800-120">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="19800-121">如何：将文本写入文件</span><span class="sxs-lookup"><span data-stu-id="19800-121">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [<span data-ttu-id="19800-122">如何：从字符串中读取字符</span><span class="sxs-lookup"><span data-stu-id="19800-122">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
- [<span data-ttu-id="19800-123">如何：向字符串写入字符</span><span class="sxs-lookup"><span data-stu-id="19800-123">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)
- [<span data-ttu-id="19800-124">文件和流 I/O</span><span class="sxs-lookup"><span data-stu-id="19800-124">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
