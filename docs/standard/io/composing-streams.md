---
title: 编写流
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET Framework], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1f2aa68822dd14b4cb81b48598faa6bdb4c71a13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544349"
---
# <a name="composing-streams"></a><span data-ttu-id="5633b-102">编写流</span><span class="sxs-lookup"><span data-stu-id="5633b-102">Composing Streams</span></span>
<span data-ttu-id="5633b-103">后备存储是磁盘或内存等存储介质。</span><span class="sxs-lookup"><span data-stu-id="5633b-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="5633b-104">各个后备存储都实现自己的流，作为 <xref:System.IO.Stream> 类的实现。</span><span class="sxs-lookup"><span data-stu-id="5633b-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="5633b-105">每个流类型对给定的后备存储执行字节读取和写入操作。</span><span class="sxs-lookup"><span data-stu-id="5633b-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="5633b-106">连接到后备存储的流称为“基流”。</span><span class="sxs-lookup"><span data-stu-id="5633b-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="5633b-107">基流的构造函数包含将流连接到后备存储所需的参数。</span><span class="sxs-lookup"><span data-stu-id="5633b-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="5633b-108">例如，<xref:System.IO.FileStream> 包含指定路径参数的构造函数，此参数指定了进程如何共享文件等。</span><span class="sxs-lookup"><span data-stu-id="5633b-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="5633b-109"><xref:System.IO> 类旨在简化流撰写。</span><span class="sxs-lookup"><span data-stu-id="5633b-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="5633b-110">基流可以附加到一个或多个提供所需功能的直通流。</span><span class="sxs-lookup"><span data-stu-id="5633b-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="5633b-111">读取器或编写器可以附加到链的末尾，这样便能轻松读取或编写首选类型。</span><span class="sxs-lookup"><span data-stu-id="5633b-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="5633b-112">下面的代码示例根据现有 `MyFile.txt` 创建了 FileStream 以便缓冲 `MyFile.txt`。</span><span class="sxs-lookup"><span data-stu-id="5633b-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="5633b-113">（请注意，FileStreams 默认缓冲。）接下来，创建从 FileStream 读取字符的 <xref:System.IO.StreamReader>，此读取器作为构造函数参数传递给 StreamReader。</span><span class="sxs-lookup"><span data-stu-id="5633b-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="5633b-114">除非 <xref:System.IO.StreamReader.Peek%2A> 找不到更多字符，否则 <xref:System.IO.StreamReader.ReadLine%2A> 会一直读取字符。</span><span class="sxs-lookup"><span data-stu-id="5633b-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="5633b-115">下面的代码示例根据现有 `MyFile.txt` 创建了 FileStream 以便缓冲 `MyFile.txt`。</span><span class="sxs-lookup"><span data-stu-id="5633b-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="5633b-116">（请注意，FileStreams 默认缓冲。）接下来，创建从 FileStream 读取字节的 BinaryReader，此读取器作为构造函数参数传递给 BinaryReader。</span><span class="sxs-lookup"><span data-stu-id="5633b-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="5633b-117">除非 <xref:System.IO.BinaryReader.PeekChar%2A> 找不到更多字节，否则 <xref:System.IO.BinaryReader.ReadByte%2A> 会一直读取字节。</span><span class="sxs-lookup"><span data-stu-id="5633b-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="5633b-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="5633b-118">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
