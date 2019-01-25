---
title: 如何：使用打印预览的 Windows 窗体中打印
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: f412e5cbcf3014f57bc2632752a6d1ecbcf46dbc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596080"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="794b7-102">如何：使用打印预览的 Windows 窗体中打印</span><span class="sxs-lookup"><span data-stu-id="794b7-102">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="794b7-103">除了打印服务之外，Windows 窗体编程中通常还提供打印预览。</span><span class="sxs-lookup"><span data-stu-id="794b7-103">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="794b7-104">要将打印预览服务添加到你的应用程序有一个简单的方法，就是将 <xref:System.Windows.Forms.PrintPreviewDialog> 控件与用于打印文件的 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件处理逻辑结合使用。</span><span class="sxs-lookup"><span data-stu-id="794b7-104">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="794b7-105">若要预览带有 PrintPreviewDialog 控件的文本文档</span><span class="sxs-lookup"><span data-stu-id="794b7-105">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1.  <span data-ttu-id="794b7-106">向你的窗体添加 <xref:System.Windows.Forms.PrintPreviewDialog>、 <xref:System.Drawing.Printing.PrintDocument>和两个字符串。</span><span class="sxs-lookup"><span data-stu-id="794b7-106">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2.  <span data-ttu-id="794b7-107">为你想要打印的文档设置 <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> 属性，然后打开并读取文档内容到之前添加的字符串。</span><span class="sxs-lookup"><span data-stu-id="794b7-107">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="794b7-108">就像你为了打印文件所执行的操作那样，在 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件处理程序中使用 <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> 类的 <xref:System.Drawing.Printing.PrintPageEventArgs> 属性和文件内容来计算每页行数并呈现文档的内容。</span><span class="sxs-lookup"><span data-stu-id="794b7-108">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="794b7-109">绘制完每一页后，检查它是否是最后一页，并相应地设置 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 的 <xref:System.Drawing.Printing.PrintPageEventArgs> 属性。</span><span class="sxs-lookup"><span data-stu-id="794b7-109">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="794b7-110">引发 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件，直到 <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> 为 `false`。</span><span class="sxs-lookup"><span data-stu-id="794b7-110">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="794b7-111">当文档已完成呈现时，将字符串重置为已呈现。</span><span class="sxs-lookup"><span data-stu-id="794b7-111">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="794b7-112">此外，确保 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件与其事件处理方法关联。</span><span class="sxs-lookup"><span data-stu-id="794b7-112">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="794b7-113">如果已在应用程序中实现打印，你可能已完成了步骤 2 和 3。</span><span class="sxs-lookup"><span data-stu-id="794b7-113">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="794b7-114">在下列代码示例中，事件处理程序用于打印“testPage.txt”文件的内容，所用字体与窗体上使用的字体相同。</span><span class="sxs-lookup"><span data-stu-id="794b7-114">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="794b7-115">在窗体上，将 <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> 控件的 <xref:System.Windows.Forms.PrintPreviewDialog> 属性设置为 <xref:System.Drawing.Printing.PrintDocument> 组件。</span><span class="sxs-lookup"><span data-stu-id="794b7-115">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5.  <span data-ttu-id="794b7-116">调用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 控件上的 <xref:System.Windows.Forms.PrintPreviewDialog> 方法。</span><span class="sxs-lookup"><span data-stu-id="794b7-116">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="794b7-117">你通常会从一个按钮的 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 事件处理方法调用 <xref:System.Windows.Forms.Control.Click> 。</span><span class="sxs-lookup"><span data-stu-id="794b7-117">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="794b7-118">调用 <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> 会引发 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件，并将输出呈现到 <xref:System.Windows.Forms.PrintPreviewDialog> 控件。</span><span class="sxs-lookup"><span data-stu-id="794b7-118">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="794b7-119">当用户单击对话框上的打印按钮时，会再次引发 <xref:System.Drawing.Printing.PrintDocument.PrintPage> 事件，将输出发送至打印机而不是预览对话框。</span><span class="sxs-lookup"><span data-stu-id="794b7-119">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="794b7-120">这就是在步骤 3 中该字符串在呈现过程结尾重置的原因。</span><span class="sxs-lookup"><span data-stu-id="794b7-120">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="794b7-121">下列代码示例显示了窗体上一个按钮的 <xref:System.Windows.Forms.Control.Click> 事件处理方法。</span><span class="sxs-lookup"><span data-stu-id="794b7-121">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="794b7-122">此事件处理方法调用方法来读取文档，并显示打印预览对话框。</span><span class="sxs-lookup"><span data-stu-id="794b7-122">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="794b7-123">示例</span><span class="sxs-lookup"><span data-stu-id="794b7-123">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="794b7-124">编译代码</span><span class="sxs-lookup"><span data-stu-id="794b7-124">Compiling the Code</span></span>  
 <span data-ttu-id="794b7-125">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="794b7-125">This example requires:</span></span>  
  
-   <span data-ttu-id="794b7-126">对 System、System.Windows.Forms 和 System.Drawing 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="794b7-126">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
-   <span data-ttu-id="794b7-127">Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="794b7-127">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="794b7-128">也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="794b7-128">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="794b7-129">另请参阅[如何：编译和运行完整的 Windows 窗体代码示例使用 Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="794b7-129">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="794b7-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="794b7-130">See also</span></span>
- [<span data-ttu-id="794b7-131">如何：打印 Windows 窗体中的多页文本文件</span><span class="sxs-lookup"><span data-stu-id="794b7-131">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [<span data-ttu-id="794b7-132">Windows 窗体打印支持</span><span class="sxs-lookup"><span data-stu-id="794b7-132">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
- [<span data-ttu-id="794b7-133">Windows 窗体中更加安全的打印</span><span class="sxs-lookup"><span data-stu-id="794b7-133">More Secure Printing in Windows Forms</span></span>](../../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)
