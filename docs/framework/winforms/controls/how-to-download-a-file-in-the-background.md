---
title: 如何：下载在后台中的文件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
ms.openlocfilehash: 57a904c5d54b0c3f68efaf017a3405786600ace7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715810"
---
# <a name="how-to-download-a-file-in-the-background"></a><span data-ttu-id="49262-102">如何：下载在后台中的文件</span><span class="sxs-lookup"><span data-stu-id="49262-102">How to: Download a File in the Background</span></span>
<span data-ttu-id="49262-103">下载文件是一项常见任务，在单独线程上运行这个可能很耗时的操作通常很有用。</span><span class="sxs-lookup"><span data-stu-id="49262-103">Downloading a file is a common task, and it is often useful to run this potentially time-consuming operation on a separate thread.</span></span> <span data-ttu-id="49262-104">使用 <xref:System.ComponentModel.BackgroundWorker> 组件来完成此任务，几乎不使用任何代码。</span><span class="sxs-lookup"><span data-stu-id="49262-104">Use the <xref:System.ComponentModel.BackgroundWorker> component to accomplish this task with very little code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49262-105">示例</span><span class="sxs-lookup"><span data-stu-id="49262-105">Example</span></span>  
 <span data-ttu-id="49262-106">以下代码示例演示如何使用 <xref:System.ComponentModel.BackgroundWorker> 组件从 URL 加载 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="49262-106">The following code example demonstrates how to use a <xref:System.ComponentModel.BackgroundWorker> component to load an XML file from a URL.</span></span> <span data-ttu-id="49262-107">当用户单击**下载**按钮，<xref:System.Windows.Forms.Control.Click>事件处理程序调用<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>方法<xref:System.ComponentModel.BackgroundWorker>组件以启动下载操作。</span><span class="sxs-lookup"><span data-stu-id="49262-107">When the user clicks the **Download** button, the <xref:System.Windows.Forms.Control.Click> event handler calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of a <xref:System.ComponentModel.BackgroundWorker> component to start the download operation.</span></span> <span data-ttu-id="49262-108">按钮在下载期间处于禁用状态，下载完毕后处于启用状态。</span><span class="sxs-lookup"><span data-stu-id="49262-108">The button is disabled for the duration of the download, and then enabled when the download is complete.</span></span> <span data-ttu-id="49262-109">
  <xref:System.Windows.Forms.MessageBox> 显示文件的内容。</span><span class="sxs-lookup"><span data-stu-id="49262-109">A <xref:System.Windows.Forms.MessageBox> displays the contents of the file.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 <span data-ttu-id="49262-110">**下载文件**</span><span class="sxs-lookup"><span data-stu-id="49262-110">**Downloading the file**</span></span>  
  
 <span data-ttu-id="49262-111">文件被下载到 <xref:System.ComponentModel.BackgroundWorker> 组件的工作线程上，该线程运行 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="49262-111">The file is downloaded on the <xref:System.ComponentModel.BackgroundWorker> component's worker thread, which runs the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="49262-112">当代码调用 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> 方法时，将启动此线程。</span><span class="sxs-lookup"><span data-stu-id="49262-112">This thread starts when your code calls the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 <span data-ttu-id="49262-113">**等待 BackgroundWorker 完成**</span><span class="sxs-lookup"><span data-stu-id="49262-113">**Waiting for a BackgroundWorker to finish**</span></span>  
  
 <span data-ttu-id="49262-114">
  `downloadButton_Click\` 事件处理程序演示如何等待 <xref:System.ComponentModel.BackgroundWorker> 组件完成其异步任务。</span><span class="sxs-lookup"><span data-stu-id="49262-114">The `downloadButton_Click` event handler demonstrates how to wait for a <xref:System.ComponentModel.BackgroundWorker> component to finish its asynchronous task.</span></span>  
  
 <span data-ttu-id="49262-115">在等待后台线程完成时，如果你只希望应用程序响应事件，而不希望在主线程中执行任何操作，直接退出处理程序即可。</span><span class="sxs-lookup"><span data-stu-id="49262-115">If you only want the application to respond to events and do not want to do any work in the main thread while you wait for the background thread to complete, just exit the handler.</span></span>  
  
 <span data-ttu-id="49262-116">如果想要继续在主线程中执行操作，可使用 <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> 属性来确定 <xref:System.ComponentModel.BackgroundWorker> 线程是否仍在运行。</span><span class="sxs-lookup"><span data-stu-id="49262-116">If you want to continue doing work in the main thread, use the <xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> property to determine whether the <xref:System.ComponentModel.BackgroundWorker> thread is still running.</span></span> <span data-ttu-id="49262-117">在示例中，进度条随下载进行而更新。</span><span class="sxs-lookup"><span data-stu-id="49262-117">In the example, a progress bar is updated while the download is processing.</span></span> <span data-ttu-id="49262-118">请确保调用 <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> 方法以保持 UI 响应能力。</span><span class="sxs-lookup"><span data-stu-id="49262-118">Be sure to call the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method to keep the UI responsive.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 <span data-ttu-id="49262-119">**显示结果**</span><span class="sxs-lookup"><span data-stu-id="49262-119">**Displaying the result**</span></span>  
  
 <span data-ttu-id="49262-120">
  `backgroundWorker1_RunWorkerCompleted\` 方法处理 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件，并在后台操作完成时被调用。</span><span class="sxs-lookup"><span data-stu-id="49262-120">The `backgroundWorker1_RunWorkerCompleted` method handles the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event and is called when the background operation is completed.</span></span> <span data-ttu-id="49262-121">此方法首先检查 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="49262-121">This method first checks the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="49262-122">如果 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> 为 `null`，则此方法显示文件的内容。</span><span class="sxs-lookup"><span data-stu-id="49262-122">If <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> is `null`, then this method displays the contents of the file.</span></span> <span data-ttu-id="49262-123">然后它启用在下载开始后被禁用的下载按钮，并重置进度栏。</span><span class="sxs-lookup"><span data-stu-id="49262-123">It then enables the download button, which was disabled when the download began, and it resets the progress bar.</span></span>  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="49262-124">编译代码</span><span class="sxs-lookup"><span data-stu-id="49262-124">Compiling the Code</span></span>  
 <span data-ttu-id="49262-125">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="49262-125">This example requires:</span></span>  
  
-   <span data-ttu-id="49262-126">引用 System.Drawing、System.Windows.Forms 和 System.Xml 程序集。</span><span class="sxs-lookup"><span data-stu-id="49262-126">References to the System.Drawing, System.Windows.Forms, and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="49262-127">Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="49262-127">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="49262-128">也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="49262-128">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="49262-129">可靠编程</span><span class="sxs-lookup"><span data-stu-id="49262-129">Robust Programming</span></span>  
 <span data-ttu-id="49262-130">始终先检查 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 事件处理程序中的 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> 属性，然后再尝试访问 <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> 属性或可能受 <xref:System.ComponentModel.BackgroundWorker.DoWork> 事件处理程序影响的任何其他对象。</span><span class="sxs-lookup"><span data-stu-id="49262-130">Always check the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> property in your <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler before attempting to access the <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> property or any other object that may have been affected by the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49262-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="49262-131">See also</span></span>
- <xref:System.ComponentModel.BackgroundWorker>
- [<span data-ttu-id="49262-132">如何：在后台运行操作</span><span class="sxs-lookup"><span data-stu-id="49262-132">How to: Run an Operation in the Background</span></span>](how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="49262-133">如何：实现使用后台操作的窗体</span><span class="sxs-lookup"><span data-stu-id="49262-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
