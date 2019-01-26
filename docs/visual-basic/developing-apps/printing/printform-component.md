---
title: PrintForm 组件 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
ms.openlocfilehash: a093dbb674a0d182b9a981cf39668d9ca11d0e8c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54746190"
---
# <a name="printform-component-visual-basic"></a>PrintForm 组件 (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>适用于 Visual Basic 组件，可以在运行时打印 Windows 窗体的图像。 其行为取代了 Visual Basic 早期版本中的 `PrintForm` 方法。  
  
 Visual Studio 中不再包含 PowerPack 控件，但你可以从 [下载中心](https://www.microsoft.com/en-us/download/details.aspx?id=25169)下载它们。  
  
## <a name="printform-component-overview"></a>PrintForm 组件概述  
 Windows 窗体的一个常见方案是创建格式设置为类似于纸质表单或报表的窗体，然后打印窗体的图像。 虽然可以使用 <xref:System.Drawing.Printing.PrintDocument> 组件来执行此操作，但这将需要大量的代码。 通过 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件，可以在不使用 <xref:System.Drawing.Printing.PrintDocument> 组件的情况下，将窗体的图像打印到打印机、打印预览窗口或文件。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件位于“工具箱”  的“Visual Basic PowerPacks” 选项卡上。 将其拖动到窗体上时，它将显示在组件栏中，组件栏是窗体下边框之下的小块区域。 选中该组件后，可以在“属性”  窗口中设置定义其行为的属性。 所有这些属性也可以在代码中设置。 你还可以在代码中创建 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件的实例而无需在设计时添加该组件。  
  
 打印窗体时，将打印该窗体工作区中的所有内容。 这包括所有控件和通过图形方法在窗体上绘制的任何文本或图形。 默认情况下，不打印窗体的标题栏、滚动条和边框。 并且默认情况下， <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件只打印窗体的可见部分。 例如，如果用户在运行时调整窗体大小，则只打印当前可见的控件和图形。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件使用的默认打印机由操作系统的“控制面板”设置确定。  
  
 启动打印后，随即显示标准 <xref:System.Drawing.Printing.PrintDocument> 打印对话框。 用户可通过此对话框取消打印作业。  
  
### <a name="key-methods-properties-and-events"></a>关键方法、属性和事件  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件的关键方法是 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> 方法，它可将窗体的图像打印到打印机、打印预览窗口或文件。 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> 方法有两个版本：  
  
-   不带参数基本版本： `Print()`  
  
-   带有指定打印行为的参数的重载版本： `Print(printForm As Form, printFormOption As PrintOption)`  
  
     重载的方法的 `PrintOption` 参数将决定用于打印窗体的基础实现；是否打印窗体的标题栏、滚动条和边框；是否打印窗体的可滚动部分。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 属性是 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件的关键属性。 此属性确定是将输出发送到打印机、显示在打印预览窗口中还是另存为封装的 PostScript 文件。 如果将 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> 属性设置为 <xref:System.Drawing.Printing.PrintAction.PrintToFile>，则将由 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> 属性指定路径和文件名。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> 属性提供对基础 <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> 对象的访问权限，让你能够指定要使用的打印机和要打印的份数的设置。 此外还可以查询打印机的功能，如颜色或双工支持。 此属性不显示在“属性”  窗口中；只能从代码对其进行访问。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> 属性用于指定以编程方式调用 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件时要打印的窗体。 如果在设计时向某窗体添加了该组件，则该窗体为默认窗体。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件的关键事件包括如下：  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> 事件。 在调用 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> 方法之后、打印文档首页之前发生。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> 事件。 在已打印最后一页之后发生。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> 事件。 在打印每一页之前立即发生。  
  
### <a name="remarks"></a>备注  
 如果通过 <xref:System.Drawing.Graphics> 方法绘制了包含文本或图形的窗体，请使用基本 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> (`Print()`) 方法打印它。 使用重载 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> 方法时，某些操作系统上可能无法呈现图形。  
  
 如果窗体的宽度大于打印机中纸张的宽度，则窗体的右侧可能被截断。 设计要打印的窗体时，请确保窗体可容纳于标准尺寸的纸张之上。  
  
## <a name="example"></a>示例  
 下面的示例演示 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> 组件的常见用法。  
  
```  
' Visual Basic.  
Dim pf As New PrintForm  
pf.Form = Me  
pf.PrintAction = PrintToPrinter  
pf.Print()  
```  
  
## <a name="see-also"></a>请参阅
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>
- <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>
- [如何：使用 PrintForm 组件打印窗体](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md)
- [如何：打印窗体的工作区](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)
- [如何：打印窗体的工作区和非工作区](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
- [如何：打印可滚动的窗体](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
