---
title: 处理驱动器、目录和文件
ms.date: 07/20/2015
helpviewer_keywords:
- drives
- drives, processing
- Visual Basic code, file access
- files [Visual Basic], processing
- files [Visual Basic], accessing
- directories [Visual Studio], processing
ms.assetid: f1db14c8-a4fd-4d0b-8323-c7cb29d688c2
ms.openlocfilehash: 790cf5aa2d3fde779fcc24c0c9f1fc9c4c42331b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333951"
---
# <a name="processing-drives-directories-and-files-visual-basic"></a><span data-ttu-id="d69e2-102">处理驱动器、目录和文件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d69e2-102">Processing Drives, Directories, and Files (Visual Basic)</span></span>

<span data-ttu-id="d69e2-103">可以通过 Visual Basic 使用 `My.Computer.FileSystem` 对象处理驱动器、文件夹和文件，这样可以提高性能，并且与诸如 `FileOpen` 和 `Write` 函数（尽管它们仍可用）的传统方法相比更易于使用。</span><span class="sxs-lookup"><span data-stu-id="d69e2-103">You can use Visual Basic to process drives, folders, and files with the `My.Computer.FileSystem` object, which provides better performance and is easier to use than traditional methods such as the `FileOpen` and `Write` functions (although they are still available).</span></span> <span data-ttu-id="d69e2-104">以下各节详细地讨论了这些方法。</span><span class="sxs-lookup"><span data-stu-id="d69e2-104">The following sections discuss these methods in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d69e2-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="d69e2-105">In This Section</span></span>  

 [<span data-ttu-id="d69e2-106">使用 Visual Basic 访问文件</span><span class="sxs-lookup"><span data-stu-id="d69e2-106">File Access with Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 <span data-ttu-id="d69e2-107">讨论如何使用 `My.Computer.FileSystem` 对象处理文件、驱动器和文件夹。</span><span class="sxs-lookup"><span data-stu-id="d69e2-107">Discusses how to use the `My.Computer.FileSystem` object to work with files, drives, and folders.</span></span>  
  
 [<span data-ttu-id="d69e2-108">.NET Framework 文件 I/O 和文件系统基础知识 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d69e2-108">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)  
 <span data-ttu-id="d69e2-109">提供 .NET Framework 中文件 I/O 概念的概述，其中包括流、独立存储、文件事件、文件属性和文件访问。</span><span class="sxs-lookup"><span data-stu-id="d69e2-109">Provides an overview of file I/O concepts in the .NET Framework, including streams, isolated storage, file events, file attributes, and file access.</span></span>  
  
 [<span data-ttu-id="d69e2-110">演练：使用 .NET Framework 方法操作文件</span><span class="sxs-lookup"><span data-stu-id="d69e2-110">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 <span data-ttu-id="d69e2-111">演示如何使用 .NET Framework 操作文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="d69e2-111">Demonstrates how to use the .NET Framework to manipulate files and folders.</span></span>  
  
 [<span data-ttu-id="d69e2-112">演练：在 Visual Basic 中操作文件和目录</span><span class="sxs-lookup"><span data-stu-id="d69e2-112">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="d69e2-113">演示如何使用 `My.Computer.FileSystem` 对象操作文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="d69e2-113">Demonstrates how to use the `My.Computer.FileSystem` object to manipulate files and folders.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d69e2-114">相关章节</span><span class="sxs-lookup"><span data-stu-id="d69e2-114">Related Sections</span></span>  

 [<span data-ttu-id="d69e2-115">程序结构和代码约定</span><span class="sxs-lookup"><span data-stu-id="d69e2-115">Program Structure and Code Conventions</span></span>](../../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 <span data-ttu-id="d69e2-116">提供物理结构和程序外观的准则。</span><span class="sxs-lookup"><span data-stu-id="d69e2-116">Provides guidelines for the physical structure and appearance of programs.</span></span>  
  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <span data-ttu-id="d69e2-117">`My.Computer.FileSystem` 对象及其成员的参考文档。</span><span class="sxs-lookup"><span data-stu-id="d69e2-117">Reference documentation for the `My.Computer.FileSystem` object and its members.</span></span>
