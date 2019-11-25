---
title: 如何：创建目录
ms.date: 07/20/2015
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
ms.openlocfilehash: 3d838352a0a3dd69a1555dc34b8acba3afba278b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348811"
---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="e7769-102">如何：在 Visual Basic 中创建目录</span><span class="sxs-lookup"><span data-stu-id="e7769-102">How to: Create a Directory in Visual Basic</span></span>

<span data-ttu-id="e7769-103">使用 `My.Computer.FileSystem` 对象的 `CreateDirectory` 方法来创建目录。</span><span class="sxs-lookup"><span data-stu-id="e7769-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="e7769-104">如果该目录已存在，则不引发任何异常。</span><span class="sxs-lookup"><span data-stu-id="e7769-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="e7769-105">创建目录</span><span class="sxs-lookup"><span data-stu-id="e7769-105">To create a directory</span></span>  
  
- <span data-ttu-id="e7769-106">使用 `CreateDirectory` 方法，指定将在其中创建目录的位置的完整路径。</span><span class="sxs-lookup"><span data-stu-id="e7769-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="e7769-107">此示例在 `NewDirectory` 中创建目录 `C:\Documents and Settings\All Users\Documents`。</span><span class="sxs-lookup"><span data-stu-id="e7769-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e7769-108">可靠编程</span><span class="sxs-lookup"><span data-stu-id="e7769-108">Robust Programming</span></span>  

 <span data-ttu-id="e7769-109">以下情况可能会导致异常：</span><span class="sxs-lookup"><span data-stu-id="e7769-109">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="e7769-110">目录名称格式不正确。</span><span class="sxs-lookup"><span data-stu-id="e7769-110">The directory name is malformed.</span></span> <span data-ttu-id="e7769-111">例如，它包含非法字符或仅为空白 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="e7769-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="e7769-112">要创建的目录的父目录为只读 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="e7769-112">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="e7769-113">目录名称为 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="e7769-113">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="e7769-114">目录名称过长 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="e7769-114">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="e7769-115">目录名称是一个冒号“:”(<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="e7769-115">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="e7769-116">用户无权创建目录 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="e7769-116">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="e7769-117">用户在部分信任情况下缺少权限 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="e7769-117">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7769-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="e7769-118">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>
- [<span data-ttu-id="e7769-119">创建、删除和移动文件和目录</span><span class="sxs-lookup"><span data-stu-id="e7769-119">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
