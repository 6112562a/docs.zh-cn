---
title: 如何：打印可滚动窗体 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- entire form [Visual Basic], printing
- scrollable form [Visual Basic], printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
ms.openlocfilehash: 6cec75eae8046befeb37da39e0b788f045ff4149
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552497"
---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a><span data-ttu-id="1f9bd-102">如何：打印可滚动窗体 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1f9bd-102">How to: Print a Scrollable Form (Visual Basic)</span></span>
<span data-ttu-id="1f9bd-103">通过 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件，可以在不使用 <xref:System.Drawing.Printing.PrintDocument> 组件的情况下快速打印窗体的图像。</span><span class="sxs-lookup"><span data-stu-id="1f9bd-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="1f9bd-104">默认情况下，只打印窗体当前可见部分；如果用户在运行时调整了窗体的大小，则可能无法按预期打印图像。</span><span class="sxs-lookup"><span data-stu-id="1f9bd-104">By default, only the currently visible part of the form is printed; if a user has resized the form at run time, the image may not print as intended.</span></span> <span data-ttu-id="1f9bd-105">下面的过程演示如何打印可滚动窗体的完整工作区，即使已调整该窗体大小。</span><span class="sxs-lookup"><span data-stu-id="1f9bd-105">The following procedure shows how to print the complete client area of a scrollable form, even if the form has been resized.</span></span>  
  
 <span data-ttu-id="1f9bd-106">Visual Studio 中不再包含 PowerPack 控件，但你可以从 [下载中心](https://www.microsoft.com/en-us/download/details.aspx?id=25169)下载它们。</span><span class="sxs-lookup"><span data-stu-id="1f9bd-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a><span data-ttu-id="1f9bd-107">打印可滚动窗体的完整工作区</span><span class="sxs-lookup"><span data-stu-id="1f9bd-107">To print the complete client area of a scrollable form</span></span>  
  
1.  <span data-ttu-id="1f9bd-108">在“工具箱” 中，单击“Visual Basic PowerPacks”  选项卡，然后将 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件拖动到窗体上。</span><span class="sxs-lookup"><span data-stu-id="1f9bd-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="1f9bd-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件将添加到组件栏。</span><span class="sxs-lookup"><span data-stu-id="1f9bd-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component will be added to the component tray.</span></span>  
  
2.  <span data-ttu-id="1f9bd-110">在“属性”  窗口中，将 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 属性设置为 <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>。</span><span class="sxs-lookup"><span data-stu-id="1f9bd-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="1f9bd-111">在相应的事件处理程序中（例如在“打印” `Click`**的**`Button`事件处理程序中）添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="1f9bd-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1f9bd-112">在某些操作系统上，通过 <xref:System.Drawing.Graphics> 方法绘制的文本或图形可能无法正确打印。</span><span class="sxs-lookup"><span data-stu-id="1f9bd-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="1f9bd-113">在这种情况下，你将无法使用 `Scrollable` 参数进行打印。</span><span class="sxs-lookup"><span data-stu-id="1f9bd-113">In this case, you will not be able to print with the `Scrollable` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f9bd-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="1f9bd-114">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>
- [<span data-ttu-id="1f9bd-115">PrintForm 组件</span><span class="sxs-lookup"><span data-stu-id="1f9bd-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
- [<span data-ttu-id="1f9bd-116">如何：打印窗体的工作区</span><span class="sxs-lookup"><span data-stu-id="1f9bd-116">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)
- [<span data-ttu-id="1f9bd-117">如何：打印窗体的工作区和非工作区</span><span class="sxs-lookup"><span data-stu-id="1f9bd-117">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
