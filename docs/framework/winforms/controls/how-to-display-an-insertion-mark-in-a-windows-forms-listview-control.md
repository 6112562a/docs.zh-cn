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
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a>如何：Windows 窗体 ListView 控件中显示插入标记
<xref:System.Windows.Forms.ListView> 控件的插入标记向用户显示拖动项将插入的位置。 当用户将某项拖至两个其他项之间的位置时，插入标记会显示该项的预计新位置。  
  
> [!NOTE]
>  当应用程序调用 <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> 方法时，插入标记功能则仅在 [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] 中可用。 在早期的操作系统中，与插入标记相关的任何代码都不会有影响，并且插入标记也不会出现。 有关详细信息，请参阅<xref:System.Windows.Forms.ListViewInsertionMark>。  
  
 下图显示一个插入标记：  
  
 ![ListView 插入标记](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")  
  
 下面的代码示例显示如何使用此功能。  
  
## <a name="example"></a>示例  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 System 和 System.Windows.Forms 程序集的引用。  
  
 Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。  另请参阅[如何：编译和运行完整的 Windows 窗体代码示例使用 Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [ListView 控件](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)
- [ListView 控件概述](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [Windows XP 功能和 Windows 窗体控件](https://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)
- [演练：在 Windows 窗体中执行拖放操作](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
