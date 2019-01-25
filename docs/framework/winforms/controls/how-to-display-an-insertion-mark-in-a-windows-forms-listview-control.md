---
title: 如何：Windows 窗体 ListView 控件中显示插入标记
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: 6e2e89baf17c63ea3ad4814cd761449baeb78405
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627507"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a><span data-ttu-id="b661d-102">如何：Windows 窗体 ListView 控件中显示插入标记</span><span class="sxs-lookup"><span data-stu-id="b661d-102">How to: Display an Insertion Mark in a Windows Forms ListView Control</span></span>
<span data-ttu-id="b661d-103"><xref:System.Windows.Forms.ListView> 控件的插入标记向用户显示拖动项将插入的位置。</span><span class="sxs-lookup"><span data-stu-id="b661d-103">The insertion mark in the <xref:System.Windows.Forms.ListView> control shows users the point where dragged items will be inserted.</span></span> <span data-ttu-id="b661d-104">当用户将某项拖至两个其他项之间的位置时，插入标记会显示该项的预计新位置。</span><span class="sxs-lookup"><span data-stu-id="b661d-104">When a user drags an item to a point between two other items, the insertion mark shows the item's expected new location.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b661d-105">当应用程序调用 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法时，插入标记功能则仅在 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 中可用。</span><span class="sxs-lookup"><span data-stu-id="b661d-105">The insertion mark feature is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b661d-106">在早期的操作系统中，与插入标记相关的任何代码都不会有影响，并且插入标记也不会出现。</span><span class="sxs-lookup"><span data-stu-id="b661d-106">On earlier operating systems, any code relating to the insertion mark has no effect and the insertion mark will not appear.</span></span> <span data-ttu-id="b661d-107">有关详细信息，请参阅<xref:System.Windows.Forms.ListViewInsertionMark>。</span><span class="sxs-lookup"><span data-stu-id="b661d-107">For more information, see <xref:System.Windows.Forms.ListViewInsertionMark>.</span></span>  
  
 <span data-ttu-id="b661d-108">下图显示一个插入标记：</span><span class="sxs-lookup"><span data-stu-id="b661d-108">The following image shows an insertion mark:</span></span>  
  
 <span data-ttu-id="b661d-109">![ListView 插入标记](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span><span class="sxs-lookup"><span data-stu-id="b661d-109">![A ListView Insertion Mark](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")</span></span>  
  
 <span data-ttu-id="b661d-110">下面的代码示例显示如何使用此功能。</span><span class="sxs-lookup"><span data-stu-id="b661d-110">The following code example demonstrates how to use this feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b661d-111">示例</span><span class="sxs-lookup"><span data-stu-id="b661d-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b661d-112">编译代码</span><span class="sxs-lookup"><span data-stu-id="b661d-112">Compiling the Code</span></span>  
 <span data-ttu-id="b661d-113">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="b661d-113">This example requires:</span></span>  
  
-   <span data-ttu-id="b661d-114">对 System 和 System.Windows.Forms 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="b661d-114">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b661d-115">Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="b661d-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b661d-116">也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="b661d-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="b661d-117">另请参阅[如何：编译和运行完整的 Windows 窗体代码示例使用 Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="b661d-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b661d-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="b661d-118">See also</span></span>
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [<span data-ttu-id="b661d-119">ListView 控件</span><span class="sxs-lookup"><span data-stu-id="b661d-119">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [<span data-ttu-id="b661d-120">ListView 控件概述</span><span class="sxs-lookup"><span data-stu-id="b661d-120">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [<span data-ttu-id="b661d-121">Windows XP 功能和 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="b661d-121">Windows XP Features and Windows Forms Controls</span></span>](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
- [<span data-ttu-id="b661d-122">演练：在 Windows 窗体中执行拖放操作</span><span class="sxs-lookup"><span data-stu-id="b661d-122">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
