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
ms.openlocfilehash: 5e52b827f337892c33ec61b9affa1cc646a759c5
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841172"
---
# <a name="composing-streams"></a>编写流
后备存储是磁盘或内存等存储介质。 各个后备存储都实现自己的流，作为 <xref:System.IO.Stream> 类的实现。 每个流类型对给定的后备存储执行字节读取和写入操作。 连接到后备存储的流称为“基流”。 基流的构造函数包含将流连接到后备存储所需的参数。 例如，<xref:System.IO.FileStream> 包含指定路径参数的构造函数，此参数指定了进程如何共享文件等。  
  
 <xref:System.IO> 类旨在简化流撰写。 基流可以附加到一个或多个提供所需功能的直通流。 读取器或编写器可以附加到链的末尾，这样便能轻松读取或编写首选类型。  
  
 下面的代码示例根据现有 `MyFile.txt` 创建了 FileStream 以便缓冲 `MyFile.txt`。 （请注意，FileStreams 默认缓冲。）接下来，创建从 FileStream 读取字符的 <xref:System.IO.StreamReader>，此读取器作为构造函数参数传递给 StreamReader。 除非 <xref:System.IO.StreamReader.Peek%2A> 找不到更多字符，否则 <xref:System.IO.StreamReader.ReadLine%2A> 会一直读取字符。  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 下面的代码示例根据现有 `MyFile.txt` 创建了 FileStream 以便缓冲 `MyFile.txt`。 （请注意，FileStreams 默认缓冲。）接下来，创建从 FileStream 读取字节的 BinaryReader，此读取器作为构造函数参数传递给 BinaryReader。 除非 <xref:System.IO.BinaryReader.PeekChar%2A> 找不到更多字节，否则 <xref:System.IO.BinaryReader.ReadByte%2A> 会一直读取字节。  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.IO.StreamReader>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
