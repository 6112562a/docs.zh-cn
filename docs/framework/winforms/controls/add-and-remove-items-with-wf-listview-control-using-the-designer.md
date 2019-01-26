---
title: 如何：添加和删除项与使用设计器在 Windows 窗体 ListView 控件
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 487cd93364566a442eac728f90f02af02d678836
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654030"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>如何：添加和删除项与使用设计器在 Windows 窗体 ListView 控件
将项添加到 Windows 窗体的过程<xref:System.Windows.Forms.ListView>控件主要包括指定项并为其分配属性。 可在任何时间完成添加或删除列表项。  
  
 下面的过程需要**Windows 应用程序**包含一个窗体，其中包含项目<xref:System.Windows.Forms.ListView>控件。 有关设置此类项目的信息，请参阅[如何：创建 Windows 应用程序项目](https://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)和[如何：将控件添加到 Windows 窗体](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)。  
  
> [!NOTE]
>  显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。 若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。 有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。  
  
### <a name="to-add-or-remove-items-using-the-designer"></a>若要添加或删除项目使用设计器  
  
1.  选择 <xref:System.Windows.Forms.ListView> 控件。  
  
2.  在中**属性**窗口中，单击**省略号**(![VisualStudioEllipsesButton 屏幕快照](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 按钮旁边<xref:System.Windows.Forms.ListView.Items%2A>属性。  
  
     **列表视图项集合编辑器**出现。  
  
3.  若要添加某个项，请单击**添加**按钮。 然后可以设置属性的新项，如<xref:System.Windows.Forms.ListView.Text%2A>和<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>属性。  
  
4.  若要删除某个项，请选择它，然后单击**删除**按钮。  
  
## <a name="see-also"></a>请参阅
- [ListView 控件概述](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)
- [如何：将列添加到 Windows 窗体 ListView 控件](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)
- [如何：在使用 Windows 窗体 ListView 控件的列中显示子项](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [如何：Windows 窗体 ListView 控件中显示图标](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)
- [如何：将自定义信息添加到 TreeView 或 ListView 控件 （Windows 窗体）](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [如何：Windows 窗体 ListView 控件中的项进行分组](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)
