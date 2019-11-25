---
title: 如何：读取文本文件
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 8af088ad269cc77bc5c83aedb86bde9af2e37a15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334588"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a><span data-ttu-id="896b9-102">如何：在 Visual Basic 中读取文本文件</span><span class="sxs-lookup"><span data-stu-id="896b9-102">How to: Read From Text Files in Visual Basic</span></span>

<span data-ttu-id="896b9-103">通过 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> 对象的 `My.Computer.FileSystem` 方法，可以读取文本文件。</span><span class="sxs-lookup"><span data-stu-id="896b9-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file.</span></span> <span data-ttu-id="896b9-104">如果文件的内容使用类似 ASCII 或 UTF-8 的编码，则可以指定文件编码。</span><span class="sxs-lookup"><span data-stu-id="896b9-104">The file encoding can be specified if the contents of the file use an encoding such as ASCII or UTF-8.</span></span>

<span data-ttu-id="896b9-105">若要读取包含扩展字符的文件，则需要指定文件编码。</span><span class="sxs-lookup"><span data-stu-id="896b9-105">If you are reading from a file with extended characters, you will need to specify the file encoding.</span></span>

> [!NOTE]
> <span data-ttu-id="896b9-106">若要以一次读取一行文本的方式读取文件，请使用 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> 对象的 `My.Computer.FileSystem` 方法。</span><span class="sxs-lookup"><span data-stu-id="896b9-106">To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object.</span></span> <span data-ttu-id="896b9-107">`OpenTextFileReader` 方法返回 <xref:System.IO.StreamReader> 对象。</span><span class="sxs-lookup"><span data-stu-id="896b9-107">The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object.</span></span> <span data-ttu-id="896b9-108">可以使用 <xref:System.IO.StreamReader.ReadLine%2A> 对象的 `StreamReader` 方法以一次读取一行的方式读取文件。</span><span class="sxs-lookup"><span data-stu-id="896b9-108">You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time.</span></span> <span data-ttu-id="896b9-109">可以使用 <xref:System.IO.StreamReader.EndOfStream%2A> 对象的 `StreamReader` 方法测试文件的结尾。</span><span class="sxs-lookup"><span data-stu-id="896b9-109">You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.</span></span>

## <a name="to-read-from-a-text-file"></a><span data-ttu-id="896b9-110">读取文本文件</span><span class="sxs-lookup"><span data-stu-id="896b9-110">To read from a text file</span></span>

<span data-ttu-id="896b9-111">使用 `ReadAllText` 对象的 `My.Computer.FileSystem` 方法并提供路径，可以将文本文件的内容读入字符串中。</span><span class="sxs-lookup"><span data-stu-id="896b9-111">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path.</span></span> <span data-ttu-id="896b9-112">下面的示例将 test.txt 的内容读入字符串中，然后在消息框中显示内容。</span><span class="sxs-lookup"><span data-stu-id="896b9-112">The following example reads the contents of test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a><span data-ttu-id="896b9-113">读取已编码的文本文件</span><span class="sxs-lookup"><span data-stu-id="896b9-113">To read from a text file that is encoded</span></span>

<span data-ttu-id="896b9-114">使用 `ReadAllText` 对象的 `My.Computer.FileSystem` 方法并提供路径和文件编码类型，可以将文本文件的内容读入字符串中。</span><span class="sxs-lookup"><span data-stu-id="896b9-114">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type.</span></span> <span data-ttu-id="896b9-115">下面的示例将 UTF32 文件 test.txt 的内容读入字符串中，然后在消息框中显示内容。</span><span class="sxs-lookup"><span data-stu-id="896b9-115">The following example reads the contents of the UTF32 file test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a><span data-ttu-id="896b9-116">可靠编程</span><span class="sxs-lookup"><span data-stu-id="896b9-116">Robust Programming</span></span>

<span data-ttu-id="896b9-117">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="896b9-117">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="896b9-118">路径由于以下原因之一而无效：它是零长度字符串；它仅包含空白；它包含无效字符；或者它是一个设备路径 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="896b9-118">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="896b9-119">路径无效，因为它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="896b9-119">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="896b9-120">该文件不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="896b9-120">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>

- <span data-ttu-id="896b9-121">文件正由另一个进程使用，或者出现 I/O 错误 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="896b9-121">The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="896b9-122">路径超过了系统定义的最大长度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="896b9-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="896b9-123">路径中的文件名或目录名包含冒号 (:)，或格式无效 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="896b9-123">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="896b9-124">内存不足，无法将字符串写入缓冲区 (<xref:System.OutOfMemoryException>)。</span><span class="sxs-lookup"><span data-stu-id="896b9-124">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>

- <span data-ttu-id="896b9-125">该用户缺少查看该路径所必需的权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="896b9-125">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

<span data-ttu-id="896b9-126">不要根据文件的名称来判断文件的内容。</span><span class="sxs-lookup"><span data-stu-id="896b9-126">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="896b9-127">例如，文件 Form1.vb 可能不是 Visual Basic 源文件。</span><span class="sxs-lookup"><span data-stu-id="896b9-127">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>

<span data-ttu-id="896b9-128">在应用程序中使用输入的数据之前，需验证所有的输入内容。</span><span class="sxs-lookup"><span data-stu-id="896b9-128">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="896b9-129">文件的内容可能不是预期内容，并且用来读取该文件的方法可能失败。</span><span class="sxs-lookup"><span data-stu-id="896b9-129">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

## <a name="see-also"></a><span data-ttu-id="896b9-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="896b9-130">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [<span data-ttu-id="896b9-131">从文件读取</span><span class="sxs-lookup"><span data-stu-id="896b9-131">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="896b9-132">如何：读取逗号分隔的文本文件</span><span class="sxs-lookup"><span data-stu-id="896b9-132">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="896b9-133">如何：读取固定宽度的文本文件</span><span class="sxs-lookup"><span data-stu-id="896b9-133">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="896b9-134">如何：读取具有多种格式的文本文件</span><span class="sxs-lookup"><span data-stu-id="896b9-134">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="896b9-135">排除故障：读取和写入文本文件</span><span class="sxs-lookup"><span data-stu-id="896b9-135">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="896b9-136">演练：在 Visual Basic 中操作文件和目录</span><span class="sxs-lookup"><span data-stu-id="896b9-136">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="896b9-137">文件编码</span><span class="sxs-lookup"><span data-stu-id="896b9-137">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
