---
title: 操作 DataGridView 控件中的带区
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], manipulating bands
- bands [Windows Forms], manipulating in Windows Forms
- DataGridView control [Windows Forms], manipulating bands
ms.assetid: 1ea3470e-480f-4edc-bcbd-51373eca3856
ms.openlocfilehash: 89fdf41a592ef241935f1f71157588a392320df3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736127"
---
# <a name="how-to-manipulate-bands-in-the-windows-forms-datagridview-control"></a>如何：操作 Windows 窗体 DataGridView 控件中的带区
以下代码示例介绍了使用从 <xref:System.Windows.Forms.DataGridViewRow> 和 <xref:System.Windows.Forms.DataGridViewColumn> 类派生的 <xref:System.Windows.Forms.DataGridViewBand> 类的属性处理 <xref:System.Windows.Forms.DataGridView> 行和列的各种方法。  
  
## <a name="example"></a>示例  
 [!code-cpp[System.Windows.Forms.DataGridView.ButtonDemos#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CPP/DataGridViewBandDemo.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ButtonDemos#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/CS/DataGridViewBandDemo.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ButtonDemos#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ButtonDemos/VB/datagridviewbanddemo.vb#0)]  
  
## <a name="compiling-the-code"></a>编译代码  
 此示例需要：  
  
- 对 System、System.Drawing 和 System.Windows.Forms 程序集的引用。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewBand>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [使用 Windows 窗体 DataGridView 控件中的单元格、行和列编程](programming-with-cells-rows-and-columns-in-the-datagrid.md)
