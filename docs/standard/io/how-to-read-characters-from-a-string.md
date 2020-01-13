---
title: 如何：从字符串中读取字符
ms.date: 01/21/2019
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
ms.openlocfilehash: 0c3516c4abadfd22609c3568beffc14e027ef69e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706668"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="bc16e-102">如何：从字符串中读取字符</span><span class="sxs-lookup"><span data-stu-id="bc16e-102">How to: Read characters from a string</span></span>
<span data-ttu-id="bc16e-103">下面的代码示例展示了如何从字符串中异步或同步读取字符。</span><span class="sxs-lookup"><span data-stu-id="bc16e-103">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="bc16e-104">示例：同步读取字符</span><span class="sxs-lookup"><span data-stu-id="bc16e-104">Example: Read characters synchronously</span></span> 
 <span data-ttu-id="bc16e-105">此示例从字符串中同步读取 13 个字符，将它们存储到数组中，并显示这些字符。</span><span class="sxs-lookup"><span data-stu-id="bc16e-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="bc16e-106">然后，示例将读取字符串中的剩余字符，将它们存储到数组中（从第六个元素开始），并显示数组的内容。</span><span class="sxs-lookup"><span data-stu-id="bc16e-106">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="bc16e-107">示例：异步读取字符</span><span class="sxs-lookup"><span data-stu-id="bc16e-107">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="bc16e-108">下一个示例是 WPF 应用背后的代码。</span><span class="sxs-lookup"><span data-stu-id="bc16e-108">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="bc16e-109">在窗口加载时，示例从 <xref:System.Windows.Controls.TextBox> 控件异步读取所有字符，并将其存储在数组中。</span><span class="sxs-lookup"><span data-stu-id="bc16e-109">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="bc16e-110">随后，它以异步方式将每个字母或空格字符写入单独的 <xref:System.Windows.Controls.TextBlock> 控件行。</span><span class="sxs-lookup"><span data-stu-id="bc16e-110">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bc16e-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="bc16e-111">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="bc16e-112">异步文件 I/O</span><span class="sxs-lookup"><span data-stu-id="bc16e-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="bc16e-113">[如何：创建目录列表](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bc16e-113">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="bc16e-114">如何：对新建的数据文件进行读取和写入</span><span class="sxs-lookup"><span data-stu-id="bc16e-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="bc16e-115">如何：打开并追加到日志文件</span><span class="sxs-lookup"><span data-stu-id="bc16e-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="bc16e-116">如何：从文件中读取文本</span><span class="sxs-lookup"><span data-stu-id="bc16e-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="bc16e-117">如何：将文本写入文件</span><span class="sxs-lookup"><span data-stu-id="bc16e-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="bc16e-118">如何：向字符串写入字符</span><span class="sxs-lookup"><span data-stu-id="bc16e-118">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="bc16e-119">文件和流 I/O</span><span class="sxs-lookup"><span data-stu-id="bc16e-119">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
