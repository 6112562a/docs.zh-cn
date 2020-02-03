---
title: 为 RichTextBox 控件设置字体特性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- .rtf files [Windows Forms], formatting in RichTextBox control
- fonts [Windows Forms], changing attributes in RichTextBox control
- RTF files [Windows Forms], formatting in RichTextBox control
- RichTextBox control [Windows Forms], setting font attributes
- text [Windows Forms]
- text boxes [Windows Forms], formatting text
- formatting [Windows Forms]
ms.assetid: 2bc23ddb-0529-4489-a1a2-ad253cb43f9a
ms.openlocfilehash: f27256c155223df576ee3c42e6bf65270c870b0f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744861"
---
# <a name="how-to-set-font-attributes-for-the-windows-forms-richtextbox-control"></a>如何：为 Windows 窗体 RichTextBox 控件设置字体特性
Windows 窗体 <xref:System.Windows.Forms.RichTextBox> 控件有很多用于设置其显示文本格式的选项。 您可以使用 <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> 属性使所选字符变为粗体、下划线或斜体。 也可以使用此属性来更改所选字符的大小和字样。 <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> 属性允许您更改所选字符的颜色。  
  
### <a name="to-change-the-appearance-of-characters"></a>更改字符的外观  
  
1. 将 <xref:System.Windows.Forms.RichTextBox.SelectionFont%2A> 属性设置为合适的字体。  
  
     若要使用户能够在应用程序中设置字体系列、字号和字体，通常应使用 <xref:System.Windows.Forms.FontDialog> 组件。 有关概述，请参阅 [FontDialog 组件概述](fontdialog-component-overview-windows-forms.md)。  
  
2. 将 <xref:System.Windows.Forms.RichTextBox.SelectionColor%2A> 属性设置为适当的颜色。  
  
     若要使用户能够在应用程序中设置颜色，通常应使用 <xref:System.Windows.Forms.ColorDialog> 组件。 有关概述，请参阅 [ColorDialog 组件概述](colordialog-component-overview-windows-forms.md)。  
  
    ```vb  
    RichTextBox1.SelectionFont = New Font("Tahoma", 12, FontStyle.Bold)  
    RichTextBox1.SelectionColor = System.Drawing.Color.Red  
    ```  
  
    ```csharp  
    richTextBox1.SelectionFont = new Font("Tahoma", 12, FontStyle.Bold);  
    richTextBox1.SelectionColor = System.Drawing.Color.Red;  
    ```  
  
    ```cpp  
    richTextBox1->SelectionFont =  
       gcnew System::Drawing::Font("Tahoma", 12, FontStyle::Bold);  
    richTextBox1->SelectionColor = System::Drawing::Color::Red;  
    ```  
  
    > [!NOTE]
    > 这些属性只影响所选的文本，如果未选择文本，则只影响当前插入点位置处键入的文本。 有关以编程方式选择文本的信息，请参阅 <xref:System.Windows.Forms.TextBoxBase.Select%2A>。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox 控件](richtextbox-control-windows-forms.md)
- [在 Windows 窗体上使用的控件](controls-to-use-on-windows-forms.md)
