---
title: 如何：从字符串中读取字符
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbf213c783d1688e9168265cedc27d2ac7a5a96d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54504804"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="7c246-102">如何：从字符串中读取字符</span><span class="sxs-lookup"><span data-stu-id="7c246-102">How to: Read Characters from a String</span></span>
<span data-ttu-id="7c246-103">下面的代码示例展示了如何从字符串中异步和同步读取字符。</span><span class="sxs-lookup"><span data-stu-id="7c246-103">The following code examples show how to read characters synchronously and asynchronously from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c246-104">示例</span><span class="sxs-lookup"><span data-stu-id="7c246-104">Example</span></span>  
 <span data-ttu-id="7c246-105">此示例从字符串中同步读取 13 个字符，将它们存储到数组中，并显示这些字符。</span><span class="sxs-lookup"><span data-stu-id="7c246-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays those characters.</span></span> <span data-ttu-id="7c246-106">然后，它读取字符串中的剩余字符，将它们存储到数组中（从第六个元素开始），并显示数组的内容。</span><span class="sxs-lookup"><span data-stu-id="7c246-106">It then reads the remaining characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="7c246-107">示例</span><span class="sxs-lookup"><span data-stu-id="7c246-107">Example</span></span>  
 <span data-ttu-id="7c246-108">下一个示例从 <xref:System.Windows.Controls.TextBox> 控件异步读取所有字符，并将其存储在数组中。</span><span class="sxs-lookup"><span data-stu-id="7c246-108">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="7c246-109">随后，它以异步方式将每个字母或空格字符写入 <xref:System.Windows.Controls.TextBlock> 控件，每个字母或空格字符各占一行（以换行符结尾）。</span><span class="sxs-lookup"><span data-stu-id="7c246-109">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="7c246-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="7c246-110">See also</span></span>

- <xref:System.IO.StringReader>
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7c246-111">Asynchronous File I/O</span><span class="sxs-lookup"><span data-stu-id="7c246-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
- [<span data-ttu-id="7c246-112">NIB：如何：创建目录列表</span><span class="sxs-lookup"><span data-stu-id="7c246-112">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)
- [<span data-ttu-id="7c246-113">如何：对新建的数据文件进行读取和写入</span><span class="sxs-lookup"><span data-stu-id="7c246-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="7c246-114">如何：打开并追加到日志文件</span><span class="sxs-lookup"><span data-stu-id="7c246-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="7c246-115">如何：从文件中读取文本</span><span class="sxs-lookup"><span data-stu-id="7c246-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="7c246-116">如何：将文本写入文件</span><span class="sxs-lookup"><span data-stu-id="7c246-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [<span data-ttu-id="7c246-117">如何：向字符串写入字符</span><span class="sxs-lookup"><span data-stu-id="7c246-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)
- [<span data-ttu-id="7c246-118">文件和流 I/O</span><span class="sxs-lookup"><span data-stu-id="7c246-118">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
