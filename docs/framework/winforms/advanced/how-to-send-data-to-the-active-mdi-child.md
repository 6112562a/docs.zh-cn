---
title: 如何：将数据发送到活动的 MDI 子窗体
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms
- MDI [Windows Forms], sending data to forms
- Clipboard [Windows Forms], pasting
- Clipboard [Windows Forms], getting data from
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
ms.openlocfilehash: f4399d8548eff76aaa4effae6da7239cd3b0284b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343709"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a>如何：将数据发送到活动的 MDI 子窗体
通常情况下中的上下文[多文档界面 (MDI) 应用程序](multiple-document-interface-mdi-applications.md)，需要将数据发送到活动子窗口，例如当用户将数据从剪贴板粘贴到 MDI 应用程序。  
  
> [!NOTE]
>  有关验证的子窗口是否具有焦点并将其内容发送到剪贴板的信息，请参阅[确定活动的 MDI 子](how-to-determine-the-active-mdi-child.md)。  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>若要从剪贴板将数据发送到活动的 MDI 子窗口  
  
1. 在方法中，将剪贴板上的文本复制到活动子窗体的活动控件。  
  
    > [!NOTE]
    >  此示例假定的 MDI 父窗体 (`Form1`) 具有一个或多个 MDI 子窗口包含<xref:System.Windows.Forms.RichTextBox>控件。 有关详细信息，请参阅[创建 MDI 父窗体](how-to-create-mdi-parent-forms.md)。  
  
    ```vb  
    Public Sub mniPaste_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniPaste.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ParentForm.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Try  
             Dim theBox As RichTextBox = Ctype(activeChild.ActiveControl, RichTextBox)  
             If (Not theBox Is Nothing) Then  
                ' Create a new instance of the DataObject interface.  
                Dim data As IDataObject = Clipboard.GetDataObject()  
                ' If the data is text, then set the text of the   
                ' RichTextBox to the text in the clipboard.  
                If (data.GetDataPresent(DataFormats.Text)) Then  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString()  
                End If  
             End If  
          Catch  
             MessageBox.Show("You need to select a RichTextBox.")  
          End Try  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniPaste_Click (object sender, System.EventArgs e)  
    {  
      // Determine the active child form.  
       Form activeChild = this.ParentForm.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {  
          try   
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Create a new instance of the DataObject interface.  
                IDataObject data = Clipboard.GetDataObject();  
                // If the data is text, then set the text of the   
                // RichTextBox to the text in the clipboard.  
                if (data.GetDataPresent(DataFormats.Text))  
                {  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString();                 
                }  
             }  
          }  
          catch   
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a>请参阅

- [多文档界面 (MDI) 应用程序](multiple-document-interface-mdi-applications.md)
- [如何：创建 MDI 父窗体](how-to-create-mdi-parent-forms.md)
- [如何：创建 MDI 子窗体](how-to-create-mdi-child-forms.md)
- [如何：确定活动的 MDI 子窗体](how-to-determine-the-active-mdi-child.md)
- [如何：排列 MDI 子窗体](how-to-arrange-mdi-child-forms.md)
