---
title: 文件系统和注册表 - C# 编程指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: ef6c1da09ea0435643caba0f5e2819c064f8db01
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589906"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="53d30-102">文件系统和注册表（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="53d30-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="53d30-103">下面各主题介绍了如何使用 C# 和 .NET Framework 对文件、文件夹和注册表执行各种基本操作。</span><span class="sxs-lookup"><span data-stu-id="53d30-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53d30-104">本节内容</span><span class="sxs-lookup"><span data-stu-id="53d30-104">In This Section</span></span>  
  
|<span data-ttu-id="53d30-105">**标题**</span><span class="sxs-lookup"><span data-stu-id="53d30-105">**Title**</span></span>|<span data-ttu-id="53d30-106">**说明**</span><span class="sxs-lookup"><span data-stu-id="53d30-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="53d30-107">如何：循环访问目录树</span><span class="sxs-lookup"><span data-stu-id="53d30-107">How to: Iterate Through a Directory Tree</span></span>](./how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="53d30-108">介绍了如何手动循环访问目录树。</span><span class="sxs-lookup"><span data-stu-id="53d30-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="53d30-109">如何：获取文件、文件夹和驱动器的相关信息</span><span class="sxs-lookup"><span data-stu-id="53d30-109">How to: Get Information About Files, Folders, and Drives</span></span>](./how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="53d30-110">介绍了如何检索有关文件、文件夹和驱动器的信息，如创建时间和大小。</span><span class="sxs-lookup"><span data-stu-id="53d30-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="53d30-111">如何：创建文件或文件夹</span><span class="sxs-lookup"><span data-stu-id="53d30-111">How to: Create a File or Folder</span></span>](./how-to-create-a-file-or-folder.md)|<span data-ttu-id="53d30-112">介绍了如何新建文件或文件夹。</span><span class="sxs-lookup"><span data-stu-id="53d30-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="53d30-113">如何：复制、删除和移动文件和文件夹（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="53d30-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="53d30-114">介绍了如何复制、删除、移动文件和文件夹。</span><span class="sxs-lookup"><span data-stu-id="53d30-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="53d30-115">如何：提供文件操作进度对话框</span><span class="sxs-lookup"><span data-stu-id="53d30-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](./how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="53d30-116">介绍了如何显示特定文件操作的标准 Windows 进度对话框。</span><span class="sxs-lookup"><span data-stu-id="53d30-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="53d30-117">如何：写入到文本文件</span><span class="sxs-lookup"><span data-stu-id="53d30-117">How to: Write to a Text File</span></span>](./how-to-write-to-a-text-file.md)|<span data-ttu-id="53d30-118">介绍了如何将内容写入文本文件。</span><span class="sxs-lookup"><span data-stu-id="53d30-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="53d30-119">如何：从文本文件读取</span><span class="sxs-lookup"><span data-stu-id="53d30-119">How to: Read From a Text File</span></span>](./how-to-read-from-a-text-file.md)|<span data-ttu-id="53d30-120">介绍了如何读取文本文件中的内容。</span><span class="sxs-lookup"><span data-stu-id="53d30-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="53d30-121">如何：一次一行地读取文本文件</span><span class="sxs-lookup"><span data-stu-id="53d30-121">How to: Read a Text File One Line at a Time</span></span>](./how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="53d30-122">介绍了如何一次一行地检索文件文本。</span><span class="sxs-lookup"><span data-stu-id="53d30-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="53d30-123">如何：在注册表中创建注册表项</span><span class="sxs-lookup"><span data-stu-id="53d30-123">How to: Create a Key In the Registry</span></span>](./how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="53d30-124">介绍了如何将注册表项写入系统注册表。</span><span class="sxs-lookup"><span data-stu-id="53d30-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="53d30-125">相关章节</span><span class="sxs-lookup"><span data-stu-id="53d30-125">Related Sections</span></span>  
 [<span data-ttu-id="53d30-126">文件和流 I/O</span><span class="sxs-lookup"><span data-stu-id="53d30-126">File and Stream I/O</span></span>](../../../standard/io/index.md)  
  
 [<span data-ttu-id="53d30-127">如何：复制、删除和移动文件和文件夹（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="53d30-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="53d30-128">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="53d30-128">C# Programming Guide</span></span>](../index.md)  
  
 [<span data-ttu-id="53d30-129">文件、文件夹和驱动器</span><span class="sxs-lookup"><span data-stu-id="53d30-129">Files, Folders and Drives</span></span>](./index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
