---
title: 如何：将 TextBox 控件设为只读
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 7f24458eb98bd669d59f15c49d1d9e3beb6833b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229831"
---
# <a name="how-to-make-a-textbox-control-read-only"></a><span data-ttu-id="c316c-102">如何：将 TextBox 控件设为只读</span><span class="sxs-lookup"><span data-stu-id="c316c-102">How to: Make a TextBox Control Read-Only</span></span>
<span data-ttu-id="c316c-103">此示例演示如何配置<xref:System.Windows.Controls.TextBox>控件不允许用户输入或修改。</span><span class="sxs-lookup"><span data-stu-id="c316c-103">This example shows how to configure a <xref:System.Windows.Controls.TextBox> control to not allow user input or modification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c316c-104">示例</span><span class="sxs-lookup"><span data-stu-id="c316c-104">Example</span></span>  
 <span data-ttu-id="c316c-105">若要防止用户修改的内容<xref:System.Windows.Controls.TextBox>控件，将<xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>归于**true**。</span><span class="sxs-lookup"><span data-stu-id="c316c-105">To prevent users from modifying the contents of a <xref:System.Windows.Controls.TextBox> control, set the <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute to **true**.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <span data-ttu-id="c316c-106"><xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>属性会影响仅用户输入; 不会影响文本中设置[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]的说明<xref:System.Windows.Controls.TextBox>控件或以编程方式通过设置文本<xref:System.Windows.Controls.TextBox.Text%2A>属性。</span><span class="sxs-lookup"><span data-stu-id="c316c-106">The <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> attribute affects user input only; it does not affect text set in the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] description of a <xref:System.Windows.Controls.TextBox> control, or text set programmatically through the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="c316c-107">默认值<xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>是**false**。</span><span class="sxs-lookup"><span data-stu-id="c316c-107">The default value of <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> is **false**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c316c-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="c316c-108">See also</span></span>

- [<span data-ttu-id="c316c-109">TextBox 概述</span><span class="sxs-lookup"><span data-stu-id="c316c-109">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="c316c-110">RichTextBox 概述</span><span class="sxs-lookup"><span data-stu-id="c316c-110">RichTextBox Overview</span></span>](richtextbox-overview.md)
