---
title: DataGridView 控件中的内容更改时自动调整单元格大小
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells automatically
- cells [Windows Forms], resizing automatically
- DataGridView control [Windows Forms], resizing cells
ms.assetid: 1d68934d-a04c-4b12-9e66-c856c6828131
ms.openlocfilehash: 86e3bce993aa06546e301c6d7a7e03a31013c337
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732066"
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a>如何：自动调整单元格的大小来适应 Windows 窗体 DataGridView 控件中的内容变化
你可以配置 <xref:System.Windows.Forms.DataGridView> 控件，使其在内容发生更改时自动重新调整行、列和标题，以便单元格始终足以显示其值，而不出现剪切情况。  
  
 你可以选择多种方法来限制用于确定新大小的单元格类型。 例如，你可以将控件配置为根据当前限制的行中的值自动调整列宽。 使用此方法，你可以提高处理大量行时的工作效率，尽管在这种情况下，你可能想要使用调整方法（例如， <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> ）在选择时调整大小。  
  
 有关自动调整大小的详细信息，请参阅 [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md)。  
  
 以下代码示例演示了可用于自动调整大小的选项。  
  
## <a name="example"></a>示例  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
- 对 System、System.Drawing 和 System.Windows.Forms 程序集的引用。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [调整 Windows 窗体 DataGridView 控件中列和行的大小](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的重设大小选项](sizing-options-in-the-windows-forms-datagridview-control.md)
- [如何：以编程方式重设单元格大小以适应 Windows 窗体 DataGridView 控件中的内容](programmatically-resize-cells-to-fit-content-in-the-datagrid.md)
