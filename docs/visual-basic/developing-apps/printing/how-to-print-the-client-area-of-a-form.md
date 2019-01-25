---
title: 如何：打印窗体 (Visual Basic 中) 的工作区
ms.date: 07/20/2015
helpviewer_keywords:
- client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
ms.openlocfilehash: 2c808b480c38fc34006dcdf5832a814dfef1c62c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505622"
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a><span data-ttu-id="30bef-102">如何：打印窗体 (Visual Basic 中) 的工作区</span><span class="sxs-lookup"><span data-stu-id="30bef-102">How to: Print the Client Area of a Form (Visual Basic)</span></span>
<span data-ttu-id="30bef-103">通过 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件，可以在不使用 <xref:System.Drawing.Printing.PrintDocument> 组件的情况下快速打印窗体的图像。</span><span class="sxs-lookup"><span data-stu-id="30bef-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="30bef-104">下面的过程演示如何只打印窗体的工作区而不打印标题栏、边框和滚动条。</span><span class="sxs-lookup"><span data-stu-id="30bef-104">The following procedure shows how to print just the client area of a form, without the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="30bef-105">Visual Studio 中不再包含 PowerPack 控件，但你可以从 [下载中心](https://www.microsoft.com/en-us/download/details.aspx?id=25169)下载它们。</span><span class="sxs-lookup"><span data-stu-id="30bef-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-client-area-of-a-form"></a><span data-ttu-id="30bef-106">打印窗体的工作区</span><span class="sxs-lookup"><span data-stu-id="30bef-106">To print the client area of a form</span></span>  
  
1.  <span data-ttu-id="30bef-107">在“工具箱” 中，单击“Visual Basic PowerPacks”  选项卡，然后将 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件拖动到窗体上。</span><span class="sxs-lookup"><span data-stu-id="30bef-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="30bef-108"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件被添加到组件栏。</span><span class="sxs-lookup"><span data-stu-id="30bef-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="30bef-109">在“属性”  窗口中，将 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 属性设置为 <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>。</span><span class="sxs-lookup"><span data-stu-id="30bef-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="30bef-110">在相应的事件处理程序中（例如在“打印” `Click`**的**`Button`事件处理程序中）添加以下代码。</span><span class="sxs-lookup"><span data-stu-id="30bef-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="30bef-111">在某些操作系统上，通过 <xref:System.Drawing.Graphics> 方法绘制的文本或图形可能无法正确打印。</span><span class="sxs-lookup"><span data-stu-id="30bef-111">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="30bef-112">在这种情况下，请使用兼容的打印方法： `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span><span class="sxs-lookup"><span data-stu-id="30bef-112">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30bef-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="30bef-113">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>
- [<span data-ttu-id="30bef-114">PrintForm 组件</span><span class="sxs-lookup"><span data-stu-id="30bef-114">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
- [<span data-ttu-id="30bef-115">如何：打印窗体的工作区和非工作区</span><span class="sxs-lookup"><span data-stu-id="30bef-115">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
- [<span data-ttu-id="30bef-116">如何：打印可滚动的窗体</span><span class="sxs-lookup"><span data-stu-id="30bef-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
