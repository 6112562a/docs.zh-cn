---
title: 如何：操作 Windows 窗体 DataGridView 控件中的行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGridView control [Windows Forms], manipulating rows
- data grids [Windows Forms], manipulating rows
- rows [Windows Forms], manipulating on Windows Forms
ms.assetid: 522d8944-e073-4488-9673-923f0a8d7214
ms.openlocfilehash: e81adfea480f75ae0c5136c6c609b38d413d761a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527341"
---
# <a name="how-to-manipulate-rows-in-the-windows-forms-datagridview-control"></a>如何：操作 Windows 窗体 DataGridView 控件中的行
以下代码示例演示了使用 <xref:System.Windows.Forms.DataGridViewRow> 类的属性操作 <xref:System.Windows.Forms.DataGridView> 行的各种方法。  
  
## <a name="example"></a>示例  
 [!code-cpp[System.Windows.Forms.DataGridView.ButtonDemos#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CPP/DataGridViewRowDemo.cpp#200)]
 [!code-csharp[System.Windows.Forms.DataGridView.ButtonDemos#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CS/DataGridViewRowDemo.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.ButtonDemos#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/VB/datagridviewrowdemo.vb#200)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
-   对 System、System.Drawing 和 System.Windows.Forms 程序集的引用。  
  
 Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。  另请参阅[如何：编译和运行完整的 Windows 窗体代码示例使用 Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>请参阅
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewBand>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [使用 Windows 窗体 DataGridView 控件中的单元格、行和列编程](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
