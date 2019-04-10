---
title: 如何：确定 Windows 窗体 RichTextBox 控件中的格式设置特性何时更改
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], determining font changes
- text boxes [Windows Forms], determining font changes
- SelChange event
ms.assetid: bdfed015-f77a-41e5-b38f-f8629b2fa166
ms.openlocfilehash: a90affde9de36f1c83d5b7c21b40580cdf53402e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308453"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="c3719-102">如何：确定 Windows 窗体 RichTextBox 控件中的格式设置特性何时更改</span><span class="sxs-lookup"><span data-stu-id="c3719-102">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="c3719-103">Windows 窗体的一个常见用途<xref:System.Windows.Forms.RichTextBox>控件格式化文本的字体选项或段落样式之类的属性。</span><span class="sxs-lookup"><span data-stu-id="c3719-103">A common use of the Windows Forms <xref:System.Windows.Forms.RichTextBox> control is formatting text with attributes such as font options or paragraph styles.</span></span> <span data-ttu-id="c3719-104">你的应用程序可能需要跟踪的文本格式设置用于显示一个工具栏，如下所示许多字处理应用程序中的任何更改。</span><span class="sxs-lookup"><span data-stu-id="c3719-104">Your application may need to keep track of any changes in text formatting for the purpose of displaying a toolbar, as in many word-processing applications.</span></span>  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a><span data-ttu-id="c3719-105">若要响应格式设置特性中的更改</span><span class="sxs-lookup"><span data-stu-id="c3719-105">To respond to changes in formatting attributes</span></span>  
  
1. <span data-ttu-id="c3719-106">在中编写代码<xref:System.Windows.Forms.RichTextBox.SelectionChanged>事件处理程序以执行相应的操作取决于值的属性。</span><span class="sxs-lookup"><span data-stu-id="c3719-106">Write code in the <xref:System.Windows.Forms.RichTextBox.SelectionChanged> event handler to perform an appropriate action depending on the value of the attribute.</span></span> <span data-ttu-id="c3719-107">下面的示例更改工具栏按钮，具体取决于值的外观<xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>属性。</span><span class="sxs-lookup"><span data-stu-id="c3719-107">The following example changes the appearance of a toolbar button depending on the value of the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="c3719-108">当插入点移动控件中时，才会更新工具栏按钮。</span><span class="sxs-lookup"><span data-stu-id="c3719-108">The toolbar button will only be updated when the insertion point is moved in the control.</span></span>  
  
     <span data-ttu-id="c3719-109">下面的示例假定窗体<xref:System.Windows.Forms.RichTextBox>控件和一个<xref:System.Windows.Forms.ToolBar>包含一个工具栏按钮的控件。</span><span class="sxs-lookup"><span data-stu-id="c3719-109">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control and a <xref:System.Windows.Forms.ToolBar> control that contains a toolbar button.</span></span> <span data-ttu-id="c3719-110">有关工具栏和工具栏按钮的详细信息，请参阅[如何：向 ToolBar 控件添加按钮](how-to-add-buttons-to-a-toolbar-control.md)。</span><span class="sxs-lookup"><span data-stu-id="c3719-110">For more information about toolbars and toolbar buttons, see [How to: Add Buttons to a ToolBar Control](how-to-add-buttons-to-a-toolbar-control.md).</span></span>  
  
    ```vb  
    ' The following code assumes the existence of a toolbar control  
    ' with at least one toolbar button.  
    Private Sub RichTextBox1_SelectionChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles RichTextBox1.SelectionChanged  
       If RichTextBox1.SelectionBullet = True Then  
          ' Bullet button on toolbar should appear pressed  
          ToolBarButton1.Pushed = True  
       Else  
           ' Bullet button on toolbar should appear unpressed  
           ToolBarButton1.Pushed = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private void richTextBox1_SelectionChanged(object sender,  
    System.EventArgs e)  
    {  
       if (richTextBox1.SelectionBullet == true)   
       {  
          // Bullet button on toolbar should appear pressed  
          toolBarButton1.Pushed = true;  
       }  
       else   
       {  
          // Bullet button on toolbar should appear unpressed  
          toolBarButton1.Pushed = false;  
       }  
    }  
    ```  
  
    ```cpp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private:  
       System::Void richTextBox1_SelectionChanged(  
          System::Object ^  sender, System::EventArgs ^  e)  
       {  
          if (richTextBox1->SelectionBullet == true)  
          {  
             // Bullet button on toolbar should appear pressed  
             toolBarButton1->Pushed = true;  
          }  
          else  
          {  
             // Bullet button on toolbar should appear unpressed  
             toolBarButton1->Pushed = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c3719-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="c3719-111">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="c3719-112">RichTextBox 控件</span><span class="sxs-lookup"><span data-stu-id="c3719-112">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="c3719-113">在 Windows 窗体上使用的控件</span><span class="sxs-lookup"><span data-stu-id="c3719-113">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
