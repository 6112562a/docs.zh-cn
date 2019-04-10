---
title: 对话框概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- modeless dialog boxes [WPF]
- dialog boxes [WPF]
- message boxes [WPF]
- modal dialog boxes [WPF]
ms.assetid: 0d23d544-a393-4a02-a3aa-d8cd5d3d6511
ms.openlocfilehash: 162414dbd4b0f5e15eceaf73c87c122701fefc4e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177406"
---
# <a name="dialog-boxes-overview"></a><span data-ttu-id="a36f3-102">对话框概述</span><span class="sxs-lookup"><span data-stu-id="a36f3-102">Dialog Boxes Overview</span></span>
<span data-ttu-id="a36f3-103">独立应用程序通常会在主窗口中同时显示应用程序对其进行操作和公开的功能来处理通过该数据的主数据[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]等机制，菜单栏、 工具栏和状态栏。</span><span class="sxs-lookup"><span data-stu-id="a36f3-103">Standalone applications typically have a main window that both displays the main data over which the application operates and exposes the functionality to process that data through [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] mechanisms like menu bars, tool bars, and status bars.</span></span> <span data-ttu-id="a36f3-104">重要的应用程序可能还会显示其他窗口来执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="a36f3-104">A non-trivial application may also display additional windows to do the following:</span></span>  
  
-   <span data-ttu-id="a36f3-105">向用户显示特定信息。</span><span class="sxs-lookup"><span data-stu-id="a36f3-105">Display specific information to users.</span></span>  
  
-   <span data-ttu-id="a36f3-106">从用户处收集信息。</span><span class="sxs-lookup"><span data-stu-id="a36f3-106">Gather information from users.</span></span>  
  
-   <span data-ttu-id="a36f3-107">同时显示并收集信息。</span><span class="sxs-lookup"><span data-stu-id="a36f3-107">Both display and gather information.</span></span>  
  
 <span data-ttu-id="a36f3-108">这些类型的窗口被称为*对话框*，并有两种类型： 模式和无模式。</span><span class="sxs-lookup"><span data-stu-id="a36f3-108">These types of windows are known as *dialog boxes*, and there are two types: modal and modeless.</span></span>  
  
 <span data-ttu-id="a36f3-109">一个*模式*函数需要来自用户继续的其他数据时，对话框将显示函数。</span><span class="sxs-lookup"><span data-stu-id="a36f3-109">A *modal* dialog box is displayed by a function when the function needs additional data from a user to continue.</span></span> <span data-ttu-id="a36f3-110">由于函数依赖于模式对话框收集数据，模式对话框还会在其保持打开状态时防止用户激活应用程序中的其他窗口。</span><span class="sxs-lookup"><span data-stu-id="a36f3-110">Because the function depends on the modal dialog box to gather data, the modal dialog box also prevents a user from activating other windows in the application while it remains open.</span></span> <span data-ttu-id="a36f3-111">在大多数情况下，模式对话框允许用户在通过按完成与模式对话框时发出信号**确定**或**取消**按钮。</span><span class="sxs-lookup"><span data-stu-id="a36f3-111">In most cases, a modal dialog box allows a user to signal when they have finished with the modal dialog box by pressing either an **OK** or **Cancel** button.</span></span> <span data-ttu-id="a36f3-112">按下**确定**按钮表示用户已输入数据，希望函数继续处理该数据。</span><span class="sxs-lookup"><span data-stu-id="a36f3-112">Pressing the **OK** button indicates that a user has entered data and wants the function to continue processing with that data.</span></span> <span data-ttu-id="a36f3-113">按下**取消**按钮表示用户想要停止从完全执行函数。</span><span class="sxs-lookup"><span data-stu-id="a36f3-113">Pressing the **Cancel** button indicates that a user wants to stop the function from executing altogether.</span></span> <span data-ttu-id="a36f3-114">最常见的模式对话框示例显示为可以打开、保存并打印数据。</span><span class="sxs-lookup"><span data-stu-id="a36f3-114">The most common examples of modal dialog boxes are shown to open, save, and print data.</span></span>  
  
 <span data-ttu-id="a36f3-115">一个*无模式*对话框中，但是，不会阻止用户激活其他窗口打开时。</span><span class="sxs-lookup"><span data-stu-id="a36f3-115">A *modeless* dialog box, on the other hand, does not prevent a user from activating other windows while it is open.</span></span> <span data-ttu-id="a36f3-116">例如，如果用户想要在某个文档中查找特定字的出现次数，主窗口通常会打开一个对话框，询问用户要查找的字是什么。</span><span class="sxs-lookup"><span data-stu-id="a36f3-116">For example, if a user wants to find occurrences of a particular word in a document, a main window will often open a dialog box to ask a user what word they are looking for.</span></span> <span data-ttu-id="a36f3-117">查找字并不会防止用户编辑文档，因此对话框无需为模式对话框。</span><span class="sxs-lookup"><span data-stu-id="a36f3-117">Since finding a word doesn't prevent a user from editing the document, however, the dialog box doesn't need to be modal.</span></span> <span data-ttu-id="a36f3-118">无模式对话框至少提供**关闭**按钮以关闭对话框，并可能会提供其他按钮来执行特定的功能，如**查找下一个**按钮以查找下一个词与字搜索查找条件匹配。</span><span class="sxs-lookup"><span data-stu-id="a36f3-118">A modeless dialog box at least provides a **Close** button to close the dialog box, and may provide additional buttons to execute specific functions, such as a **Find Next** button to find the next word that matches the find criteria of a word search.</span></span>  
  
 <span data-ttu-id="a36f3-119">Windows Presentation Foundation (WPF)，可创建多种类型的对话框，包括消息框、 通用对话框和自定义对话框。</span><span class="sxs-lookup"><span data-stu-id="a36f3-119">Windows Presentation Foundation (WPF) allows you to create several types of dialog boxes, including message boxes, common dialog boxes, and custom dialog boxes.</span></span> <span data-ttu-id="a36f3-120">本主题介绍了每一个，并[对话框示例](https://go.microsoft.com/fwlink/?LinkID=159984)提供匹配的示例。</span><span class="sxs-lookup"><span data-stu-id="a36f3-120">This topic discusses each, and the [Dialog Box Sample](https://go.microsoft.com/fwlink/?LinkID=159984) provides matching examples.</span></span>  

<a name="Message_Boxes"></a>   
## <a name="message-boxes"></a><span data-ttu-id="a36f3-121">消息框</span><span class="sxs-lookup"><span data-stu-id="a36f3-121">Message Boxes</span></span>  
 <span data-ttu-id="a36f3-122">一个*消息框*是可以用于显示文本信息并允许用户使用按钮做出决定的对话框。</span><span class="sxs-lookup"><span data-stu-id="a36f3-122">A *message box* is a dialog box that can be used to display textual information and to allow users to make decisions with buttons.</span></span> <span data-ttu-id="a36f3-123">下图显示的消息框显示文本信息、提出问题并向用户提供了三个按钮来回答问题。</span><span class="sxs-lookup"><span data-stu-id="a36f3-123">The following figure shows a message box that displays textual information, asks a question, and provides the user with three buttons to answer the question.</span></span>  
  
 ![字处理器对话框，询问你是否想要将所做的更改保存到文档，再进行应用程序关闭。](./media/dialog-boxes-overview/word-processor-dialog.png)  
  
 <span data-ttu-id="a36f3-125">若要创建一个消息框，您可以使用<xref:System.Windows.MessageBox>类。</span><span class="sxs-lookup"><span data-stu-id="a36f3-125">To create a message box, you use the <xref:System.Windows.MessageBox> class.</span></span> <xref:System.Windows.MessageBox> <span data-ttu-id="a36f3-126">您可以配置消息框文本、 标题、 图标和按钮，使用如下所示的代码。</span><span class="sxs-lookup"><span data-stu-id="a36f3-126">lets you configure the message box text, title, icon, and buttons, using code like the following.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxconfigurecodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxConfigureCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxconfigurecodebehind)]  
  
 <span data-ttu-id="a36f3-127">若要显示一个消息框，则调用`static`<xref:System.Windows.MessageBox.Show%2A>方法，如下面的代码中所示。</span><span class="sxs-lookup"><span data-stu-id="a36f3-127">To show a message box, you call the `static`<xref:System.Windows.MessageBox.Show%2A> method, as demonstrated in the following code.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowcodebehind)]  
  
 <span data-ttu-id="a36f3-128">当显示消息框的代码需要检测并处理用户决定（按下了哪个按钮）时，该代码可以检查消息框的结果，如以下代码中所示。</span><span class="sxs-lookup"><span data-stu-id="a36f3-128">When code that shows a message box needs to detect and process the user's decision (which button was pressed), the code can inspect the message box result, as shown in the following code.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#msgboxshowandresultcodebehind1)]
 [!code-vb[DialogBoxesOverviewSnippets#MsgBoxShowAndResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#msgboxshowandresultcodebehind1)]  
  
 <span data-ttu-id="a36f3-129">使用消息框的详细信息，请参阅<xref:System.Windows.MessageBox>， [MessageBox 示例](https://go.microsoft.com/fwlink/?LinkID=160023)，和[对话框示例](https://go.microsoft.com/fwlink/?LinkID=159984)。</span><span class="sxs-lookup"><span data-stu-id="a36f3-129">For more information on using message boxes, see <xref:System.Windows.MessageBox>, [MessageBox Sample](https://go.microsoft.com/fwlink/?LinkID=160023), and [Dialog Box Sample](https://go.microsoft.com/fwlink/?LinkID=159984).</span></span>  
  
 <span data-ttu-id="a36f3-130">尽管<xref:System.Windows.MessageBox>可能会提供简单的对话框用户体验，使用的优点<xref:System.Windows.MessageBox>是唯一的部分信任安全沙箱内运行的应用程序均可显示的窗口类型 (请参阅[安全](../security-wpf.md))，如[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a36f3-130">Although <xref:System.Windows.MessageBox> may offer a simple dialog box user experience, the advantage of using <xref:System.Windows.MessageBox> is that is the only type of window that can be shown by applications that run within a partial trust security sandbox (see [Security](../security-wpf.md)), such as [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)].</span></span>  
  
 <span data-ttu-id="a36f3-131">大多数对话框显示和收集比消息框结果更复杂的数据，包括文本、选项（复选框）、互斥选项（单选按钮）和列表选项（列表框、组合框、下拉列表框）。</span><span class="sxs-lookup"><span data-stu-id="a36f3-131">Most dialog boxes display and gather more complex data than the result of a message box, including text, selection (check boxes), mutually exclusive selection (radio buttons), and list selection (list boxes, combo boxes, drop-down list boxes).</span></span> <span data-ttu-id="a36f3-132">对于这些数据，Windows Presentation Foundation (WPF) 提供了几个通用对话框，并允许您创建您自己的对话框，不过使用仅限于以完全信任级别运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="a36f3-132">For these, Windows Presentation Foundation (WPF) provides several common dialog boxes and allows you to create your own dialog boxes, although the use of either is limited to applications running with full trust.</span></span>  
  
<a name="Common_Dialogs"></a>   
## <a name="common-dialog-boxes"></a><span data-ttu-id="a36f3-133">通用对话框</span><span class="sxs-lookup"><span data-stu-id="a36f3-133">Common Dialog Boxes</span></span>  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] <span data-ttu-id="a36f3-134">实现各种可重用的对话框所共有的所有应用程序，包括用于打开文件、 保存文件，然后打印对话框。</span><span class="sxs-lookup"><span data-stu-id="a36f3-134">implements a variety of reusable dialog boxes that are common to all applications, including dialog boxes for opening files, saving files, and printing.</span></span> <span data-ttu-id="a36f3-135">这些对话框由操作系统实现，因此可以在运行于该操作系统上的所有应用程序之间共享，这对用户体验的一致性很有帮助；当用户熟悉一个应用程序中操作系统所提供的对话框时，他们就无需再去了解如何在其他应用程序中使用该对话框。</span><span class="sxs-lookup"><span data-stu-id="a36f3-135">Since these dialog boxes are implemented by the operating system, they can be shared among all the applications that run on the operating system, which helps user experience consistency; when users are familiar with the use of an operating system-provided dialog box in one application, they don't need to learn how to use that dialog box in other applications.</span></span> <span data-ttu-id="a36f3-136">因为这些对话框可供所有应用程序，因为它们可帮助提供一致的用户体验，因此它们被称为*公共对话框*。</span><span class="sxs-lookup"><span data-stu-id="a36f3-136">Because these dialog boxes are available to all applications and because they help provide a consistent user experience, they are known as *common dialog boxes*.</span></span>  
  
 <span data-ttu-id="a36f3-137">Windows Presentation Foundation (WPF) 封装用于打开文件、 保存文件，并打印通用对话框和将其公开为托管的类以便您可以在独立应用程序中使用。</span><span class="sxs-lookup"><span data-stu-id="a36f3-137">Windows Presentation Foundation (WPF) encapsulates the open file, save file, and print common dialog boxes and exposes them as managed classes for you to use in standalone applications.</span></span> <span data-ttu-id="a36f3-138">本主题提供每个通用对话框的简要概述。</span><span class="sxs-lookup"><span data-stu-id="a36f3-138">This topic provides a brief overview of each.</span></span>  
  
<a name="Open_File_Dialog"></a>   
### <a name="open-file-dialog"></a><span data-ttu-id="a36f3-139">打开文件对话框</span><span class="sxs-lookup"><span data-stu-id="a36f3-139">Open File Dialog</span></span>  
 <span data-ttu-id="a36f3-140">如下图中所示的打开文件对话框由文件打开功能用于检索要打开文件的名称。</span><span class="sxs-lookup"><span data-stu-id="a36f3-140">The open file dialog box, shown in the following figure, is used by file opening functionality to retrieve the name of a file to open.</span></span>  
  
 ![打开的对话框显示用于检索文件的位置。](./media/dialog-boxes-overview/open-file-dialog-box.png)  
  
 <span data-ttu-id="a36f3-142">作为实现常见的打开文件对话框<xref:Microsoft.Win32.OpenFileDialog>类，它位于<xref:Microsoft.Win32>命名空间。</span><span class="sxs-lookup"><span data-stu-id="a36f3-142">The common open file dialog box is implemented as the <xref:Microsoft.Win32.OpenFileDialog> class and is located in the <xref:Microsoft.Win32> namespace.</span></span> <span data-ttu-id="a36f3-143">以下代码显示了如何创建、配置和显示保存文件对话框以及如何处理结果。</span><span class="sxs-lookup"><span data-stu-id="a36f3-143">The following code shows how to create, configure, and show one, and how to process the result.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#openfiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#OpenFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#openfiledialogboxcodebehind)]  
  
 <span data-ttu-id="a36f3-144">打开文件对话框的详细信息，请参阅<xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a36f3-144">For more information on the open file dialog box, see <xref:Microsoft.Win32.OpenFileDialog?displayProperty=nameWithType>.</span></span>  
  
> [!NOTE]
>  <xref:Microsoft.Win32.OpenFileDialog> <span data-ttu-id="a36f3-145">可用于安全地检索文件名的部分信任环境中运行的应用程序 (请参阅[安全](../security-wpf.md))。</span><span class="sxs-lookup"><span data-stu-id="a36f3-145">can be used to safely retrieve file names by applications running with partial trust (see [Security](../security-wpf.md)).</span></span>  
  
<a name="Save_File_Dialog"></a>   
### <a name="save-file-dialog-box"></a><span data-ttu-id="a36f3-146">保存文件对话框</span><span class="sxs-lookup"><span data-stu-id="a36f3-146">Save File Dialog Box</span></span>  
 <span data-ttu-id="a36f3-147">如下图中所示的保存文件对话框由文件保存功能用以检索要保存的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="a36f3-147">The save file dialog box, shown in the following figure, is used by file saving functionality to retrieve the name of a file to save.</span></span>  
  
 ![另存为对话框显示要保存该文件的位置。](./media/dialog-boxes-overview/save-file-dialog-box.png)  
  
 <span data-ttu-id="a36f3-149">作为实现常见的保存文件对话框<xref:Microsoft.Win32.SaveFileDialog>类，并位于<xref:Microsoft.Win32>命名空间。</span><span class="sxs-lookup"><span data-stu-id="a36f3-149">The common save file dialog box is implemented as the <xref:Microsoft.Win32.SaveFileDialog> class, and is located in the <xref:Microsoft.Win32> namespace.</span></span> <span data-ttu-id="a36f3-150">以下代码显示了如何创建、配置和显示保存文件对话框以及如何处理结果。</span><span class="sxs-lookup"><span data-stu-id="a36f3-150">The following code shows how to create, configure, and show one, and how to process the result.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#savefiledialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#SaveFileDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#savefiledialogboxcodebehind)]  
  
 <span data-ttu-id="a36f3-151">有关详细信息保存文件对话框中，请参阅<xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a36f3-151">For more information on the save file dialog box, see <xref:Microsoft.Win32.SaveFileDialog?displayProperty=nameWithType>.</span></span>  
  
<a name="Print_Dialog"></a>   
### <a name="print-dialog-box"></a><span data-ttu-id="a36f3-152">打印对话框</span><span class="sxs-lookup"><span data-stu-id="a36f3-152">Print Dialog Box</span></span>  
 <span data-ttu-id="a36f3-153">如下图中所示的打印对话框由打印功能用以选择和配置用户想要将数据打印到的打印机。</span><span class="sxs-lookup"><span data-stu-id="a36f3-153">The print dialog box, shown in the following figure, is used by printing functionality to choose and configure the printer that a user would like to print data to.</span></span>  
  
 ![显示打印对话框的屏幕截图。](./media/dialog-boxes-overview/print-data-dialog-box.png)  
  
 <span data-ttu-id="a36f3-155">作为实现通用打印对话框<xref:System.Windows.Controls.PrintDialog>类，并位于<xref:System.Windows.Controls>命名空间。</span><span class="sxs-lookup"><span data-stu-id="a36f3-155">The common print dialog box is implemented as the <xref:System.Windows.Controls.PrintDialog> class, and is located in the <xref:System.Windows.Controls> namespace.</span></span> <span data-ttu-id="a36f3-156">以下代码显示了如何创建、配置和显示打印对话框。</span><span class="sxs-lookup"><span data-stu-id="a36f3-156">The following code shows how to create, configure, and show one.</span></span>  
  
 [!code-csharp[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/CSharp/Window1.xaml.cs#printdialogboxcodebehind)]
 [!code-vb[DialogBoxesOverviewSnippets#PrintDialogBoxCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxesOverviewSnippets/VisualBasic/window1.xaml.vb#printdialogboxcodebehind)]  
  
 <span data-ttu-id="a36f3-157">打印对话框的详细信息，请参阅<xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a36f3-157">For more information on the print dialog box, see <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a36f3-158">有关中的打印功能的详细讨论[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，请参阅[打印概述](../advanced/printing-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a36f3-158">For detailed discussion of printing in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], see [Printing Overview](../advanced/printing-overview.md).</span></span>  
  
<a name="Custom_Dialog_Boxes"></a>   
## <a name="custom-dialog-boxes"></a><span data-ttu-id="a36f3-159">自定义对话框</span><span class="sxs-lookup"><span data-stu-id="a36f3-159">Custom Dialog Boxes</span></span>  
 <span data-ttu-id="a36f3-160">尽管通用对话框很有用并应尽可能使用，但它们并不支持特定于域的对话框的要求。</span><span class="sxs-lookup"><span data-stu-id="a36f3-160">While common dialog boxes are useful, and should be used when possible, they do not support the requirements of domain-specific dialog boxes.</span></span> <span data-ttu-id="a36f3-161">在这些情况下，就需要创建自己的对话框。</span><span class="sxs-lookup"><span data-stu-id="a36f3-161">In these cases, you need to create your own dialog boxes.</span></span> <span data-ttu-id="a36f3-162">如我们所见，对话框是具有特殊行为的窗口。</span><span class="sxs-lookup"><span data-stu-id="a36f3-162">As we'll see, a dialog box is a window with special behaviors.</span></span> <xref:System.Windows.Window> <span data-ttu-id="a36f3-163">实现那些行为，因此，使用<xref:System.Windows.Window>创建自定义模式和无模式对话框。</span><span class="sxs-lookup"><span data-stu-id="a36f3-163">implements those behaviors and, consequently, you use <xref:System.Windows.Window> to create custom modal and modeless dialog boxes.</span></span>  
  
<a name="Creating_a_Modal_Custom_Dialog_Box"></a>   
### <a name="creating-a-modal-custom-dialog-box"></a><span data-ttu-id="a36f3-164">创建模式自定义对话框</span><span class="sxs-lookup"><span data-stu-id="a36f3-164">Creating a Modal Custom Dialog Box</span></span>  
 <span data-ttu-id="a36f3-165">本主题演示如何使用<xref:System.Windows.Window>若要创建典型模式对话框实现，使用`Margins`对话框中的作为示例 (请参阅[对话框示例](https://go.microsoft.com/fwlink/?LinkID=159984))。</span><span class="sxs-lookup"><span data-stu-id="a36f3-165">This topic shows how to use <xref:System.Windows.Window> to create a typical modal dialog box implementation, using the `Margins` dialog box as an example (see [Dialog Box Sample](https://go.microsoft.com/fwlink/?LinkID=159984)).</span></span> <span data-ttu-id="a36f3-166">`Margins`对话框显示下图中。</span><span class="sxs-lookup"><span data-stu-id="a36f3-166">The `Margins` dialog box is shown in the following figure.</span></span>  
  
 ![字段以定义左边的距、 上边距、 右边距和下边距边距对话框。](./media/dialog-boxes-overview/margin-size-dialog-box.png)  
  
#### <a name="configuring-a-modal-dialog-box"></a><span data-ttu-id="a36f3-168">配置模式对话框</span><span class="sxs-lookup"><span data-stu-id="a36f3-168">Configuring a Modal Dialog Box</span></span>  
 <span data-ttu-id="a36f3-169">典型对话框的用户界面包括以下内容：</span><span class="sxs-lookup"><span data-stu-id="a36f3-169">The user interface for a typical dialog box includes the following:</span></span>  
  
-   <span data-ttu-id="a36f3-170">收集所需数据要求的各种控件。</span><span class="sxs-lookup"><span data-stu-id="a36f3-170">The various controls that are required to gather the desired data.</span></span>  
  
-   <span data-ttu-id="a36f3-171">显示**确定**按钮用户单击以关闭对话框，返回到函数，并继续处理。</span><span class="sxs-lookup"><span data-stu-id="a36f3-171">Showing an **OK** button that users click to close the dialog box, return to the function, and continue processing.</span></span>  
  
-   <span data-ttu-id="a36f3-172">显示**取消**按钮，用户单击关闭对话框并停止进一步处理功能。</span><span class="sxs-lookup"><span data-stu-id="a36f3-172">Showing a **Cancel** button that users click to close the dialog box and stop the function from further processing.</span></span>  
  
-   <span data-ttu-id="a36f3-173">显示**关闭**标题栏中的按钮。</span><span class="sxs-lookup"><span data-stu-id="a36f3-173">Showing a **Close** button in the title bar.</span></span>  
  
-   <span data-ttu-id="a36f3-174">显示一个图标。</span><span class="sxs-lookup"><span data-stu-id="a36f3-174">Showing an icon.</span></span>  
  
-   <span data-ttu-id="a36f3-175">显示**最小化**，**最大化**，并**还原**按钮。</span><span class="sxs-lookup"><span data-stu-id="a36f3-175">Showing **Minimize**, **Maximize**, and **Restore** buttons.</span></span>  
  
-   <span data-ttu-id="a36f3-176">显示**系统**菜单以最小化、 最大化、 还原和关闭该对话框。</span><span class="sxs-lookup"><span data-stu-id="a36f3-176">Showing a **System** menu to minimize, maximize, restore, and close the dialog box.</span></span>  
  
-   <span data-ttu-id="a36f3-177">在打开对话框的窗口上方和中心打开。</span><span class="sxs-lookup"><span data-stu-id="a36f3-177">Opening above and in the center of the window that opened the dialog box.</span></span>  
  
-   <span data-ttu-id="a36f3-178">对话框应尽可能可以调整大小（以防对话框过小）并为用户提供合适的默认尺寸，需要分别设置默认和最小尺寸。</span><span class="sxs-lookup"><span data-stu-id="a36f3-178">Dialog boxes should be resizable where possible so, to prevent the dialog box from being too small, and to provide the user with a useful default size, you need to set both default and a minimum dimensions respectively.</span></span>  
  
-   <span data-ttu-id="a36f3-179">按 ESC 键应该配置导致的键盘快捷方式**取消**按钮按下。</span><span class="sxs-lookup"><span data-stu-id="a36f3-179">Pressing the ESC key should be configured as a keyboard shortcut that causes the **Cancel** button to be pressed.</span></span> <span data-ttu-id="a36f3-180">这通过设置来实现<xref:System.Windows.Controls.Button.IsCancel%2A>的属性**取消**按钮切换为`true`。</span><span class="sxs-lookup"><span data-stu-id="a36f3-180">This is achieved by setting the <xref:System.Windows.Controls.Button.IsCancel%2A> property of the **Cancel** button to `true`.</span></span>  
  
-   <span data-ttu-id="a36f3-181">按 ENTER （或 RETURN） 键应该配置导致的键盘快捷方式**确定**按钮按下。</span><span class="sxs-lookup"><span data-stu-id="a36f3-181">Pressing the ENTER (or RETURN) key should be configured as a keyboard shortcut that causes the **OK** button to be pressed.</span></span> <span data-ttu-id="a36f3-182">这通过设置来实现<xref:System.Windows.Controls.Button.IsDefault%2A>的属性**确定**按钮`true`。</span><span class="sxs-lookup"><span data-stu-id="a36f3-182">This is achieved by setting the <xref:System.Windows.Controls.Button.IsDefault%2A> property of the **OK** button `true`.</span></span>  
  
 <span data-ttu-id="a36f3-183">以下代码演示了这种配置。</span><span class="sxs-lookup"><span data-stu-id="a36f3-183">The following code demonstrates this configuration.</span></span>  
  
 [!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsDialogBoxMainBitsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogboxmainbitsmarkup2)]  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxmainbitscodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxMainBitsCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxmainbitscodebehind2)]  
  
 <span data-ttu-id="a36f3-184">对话框用户体验还扩展到打开对话框的窗口菜单栏。</span><span class="sxs-lookup"><span data-stu-id="a36f3-184">The user experience for a dialog box also extends into the menu bar of the window that opens the dialog box.</span></span> <span data-ttu-id="a36f3-185">当菜单项运行需要用户通过对话框交互才能继续运行的函数时，函数的菜单项标题上会有一个省略号，如此处所示。</span><span class="sxs-lookup"><span data-stu-id="a36f3-185">When a menu item runs a function that requires user interaction through a dialog box before the function can continue, the menu item for the function will have an ellipsis in its header, as shown here.</span></span>  
  
 [!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup1)]  
[!code-xaml[DialogBoxSample#MainWindowMarginsDialogBoxMenuItemMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#mainwindowmarginsdialogboxmenuitemmarkup2)]  
  
 <span data-ttu-id="a36f3-186">当菜单项运行的函数显示无需用户交互的对话框（如“关于”对话框）时，则不需要省略号。</span><span class="sxs-lookup"><span data-stu-id="a36f3-186">When a menu item runs a function that displays a dialog box which does not require user interaction, such as an About dialog box, an ellipsis is not required.</span></span>  
  
#### <a name="opening-a-modal-dialog-box"></a><span data-ttu-id="a36f3-187">打开模式对话框</span><span class="sxs-lookup"><span data-stu-id="a36f3-187">Opening a Modal Dialog Box</span></span>  
 <span data-ttu-id="a36f3-188">对话框通常显示为用户选择菜单项来执行特定于域的函数的结果，比如在字处理器中设置文档边距。</span><span class="sxs-lookup"><span data-stu-id="a36f3-188">A dialog box is typically shown as a result of a user selecting a menu item to perform a domain-specific function, such as setting the margins of a document in a word processor.</span></span> <span data-ttu-id="a36f3-189">将窗口显示为对话框类似于显示普通窗口，只是它需要其他特定于对话框的配置。</span><span class="sxs-lookup"><span data-stu-id="a36f3-189">Showing a window as a dialog box is similar to showing a normal window, although it requires additional dialog box-specific configuration.</span></span> <span data-ttu-id="a36f3-190">以下代码中显示了实例化、配置和打开对话框的整个过程。</span><span class="sxs-lookup"><span data-stu-id="a36f3-190">The entire process of instantiating, configuring, and opening a dialog box is shown in the following code.</span></span>  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogcodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogcodebehind4)]  
  
 <span data-ttu-id="a36f3-191">此处代码将默认信息（当前边距）传递给对话框。</span><span class="sxs-lookup"><span data-stu-id="a36f3-191">Here, the code is passing default information (the current margins) to the dialog box.</span></span> <span data-ttu-id="a36f3-192">它还设置<xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType>具有对显示的对话框窗口的引用的属性。</span><span class="sxs-lookup"><span data-stu-id="a36f3-192">It is also setting the <xref:System.Windows.Window.Owner%2A?displayProperty=nameWithType> property with a reference to the window that is showing the dialog box.</span></span> <span data-ttu-id="a36f3-193">一般情况下，应始终设置对话框中的所有者才能提供窗口状态相关的行为所共有的所有对话框 (请参阅[WPF Windows 概述](wpf-windows-overview.md)有关详细信息)。</span><span class="sxs-lookup"><span data-stu-id="a36f3-193">In general, you should always set the owner for a dialog box to provide window state-related behaviors that are common to all dialog boxes (see [WPF Windows Overview](wpf-windows-overview.md) for more information).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a36f3-194">必须提供所有者以支持[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]自动化对话框 (请参阅[UI 自动化概述](../../ui-automation/ui-automation-overview.md))。</span><span class="sxs-lookup"><span data-stu-id="a36f3-194">You must provide an owner to support [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] automation for dialog boxes (see [UI Automation Overview](../../ui-automation/ui-automation-overview.md)).</span></span>  
  
 <span data-ttu-id="a36f3-195">配置对话框的后，会有模式地显示通过调用<xref:System.Windows.Window.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="a36f3-195">After the dialog box is configured, it is shown modally by calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span>  
  
#### <a name="validating-user-provided-data"></a><span data-ttu-id="a36f3-196">验证用户提供的数据</span><span class="sxs-lookup"><span data-stu-id="a36f3-196">Validating User-Provided Data</span></span>  
 <span data-ttu-id="a36f3-197">当打开对话框并且用户提供所需数据时，对话框出于以下原因负责确保提供的数据有效：</span><span class="sxs-lookup"><span data-stu-id="a36f3-197">When a dialog box is opened and the user provides the required data, a dialog box is responsible for ensuring that the provided data is valid for the following reasons:</span></span>  
  
-   <span data-ttu-id="a36f3-198">从安全角度，应该验证所有输入。</span><span class="sxs-lookup"><span data-stu-id="a36f3-198">From a security perspective, all input should be validated.</span></span>  
  
-   <span data-ttu-id="a36f3-199">从特定于域的角度，数据验证可以防止代码处理错误数据，这可能引发异常。</span><span class="sxs-lookup"><span data-stu-id="a36f3-199">From a domain-specific perspective, data validation prevents erroneous data from being processed by the code, which could potentially throw exceptions.</span></span>  
  
-   <span data-ttu-id="a36f3-200">从用户体验角度，对话框可以帮助用户显示他们输入的哪些数据无效。</span><span class="sxs-lookup"><span data-stu-id="a36f3-200">From a user-experience perspective, a dialog box can help users by showing them which data they have entered is invalid.</span></span>  
  
-   <span data-ttu-id="a36f3-201">从性能角度，多层应用程序中的数据验证可以减少客户端和应用程序层之间的往返次数，尤其当应用程序由 Web 服务或基于服务器的数据库构成时。</span><span class="sxs-lookup"><span data-stu-id="a36f3-201">From a performance perspective, data validation in a multi-tier application can reduce the number of round trips between the client and the application tiers, particularly when the application is composed of Web services or server-based databases.</span></span>  
  
 <span data-ttu-id="a36f3-202">若要验证中的绑定的控件[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]，您需要定义验证规则并将其与绑定相关联。</span><span class="sxs-lookup"><span data-stu-id="a36f3-202">To validate a bound control in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], you need to define a validation rule and associate it with the binding.</span></span> <span data-ttu-id="a36f3-203">验证规则是派生的自定义类<xref:System.Windows.Controls.ValidationRule>。</span><span class="sxs-lookup"><span data-stu-id="a36f3-203">A validation rule is a custom class that derives from <xref:System.Windows.Controls.ValidationRule>.</span></span> <span data-ttu-id="a36f3-204">下面的示例演示的验证规则， `MarginValidationRule`，哪些会检查绑定的值是否<xref:System.Double>和指定范围内。</span><span class="sxs-lookup"><span data-stu-id="a36f3-204">The following example shows a validation rule, `MarginValidationRule`, which checks that a bound value is a <xref:System.Double> and is within a specified range.</span></span>  
  
 [!code-csharp[DialogBoxSample#MarginValidationRuleCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginValidationRule.cs#marginvalidationrulecode)]
 [!code-vb[DialogBoxSample#MarginValidationRuleCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginValidationRule.vb#marginvalidationrulecode)]  
  
 <span data-ttu-id="a36f3-205">在此代码中，验证规则的验证逻辑实现通过重写<xref:System.Windows.Controls.ValidationRule.Validate%2A>方法，用于验证数据并返回相应<xref:System.Windows.Controls.ValidationResult>。</span><span class="sxs-lookup"><span data-stu-id="a36f3-205">In this code, the validation logic of a validation rule is implemented by overriding the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method, which validates the data and returns an appropriate <xref:System.Windows.Controls.ValidationResult>.</span></span>  
  
 <span data-ttu-id="a36f3-206">要将验证规则与绑定控件进行关联，可以使用以下标记。</span><span class="sxs-lookup"><span data-stu-id="a36f3-206">To associate the validation rule with the bound control, you use the following markup.</span></span>  
  
 [!code-xaml[DialogBoxSample#MarginsValidationMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup1)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup2)]  
[!code-xaml[DialogBoxSample#MarginsValidationMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsvalidationmarkup3)]  
  
 <span data-ttu-id="a36f3-207">一旦验证规则已关联，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]会自动将其应用时数据输入到绑定控件。</span><span class="sxs-lookup"><span data-stu-id="a36f3-207">Once the validation rule is associated, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] will automatically apply it when data is entered into the bound control.</span></span> <span data-ttu-id="a36f3-208">当控件包含无效数据，[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]下图中所示，将显示在无效控件四周的红色边框。</span><span class="sxs-lookup"><span data-stu-id="a36f3-208">When a control contains invalid data, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] will display a red border around the invalid control, as shown in the following figure.</span></span>  
  
 ![无效左边的距值四周的红色边框边距对话框。](./media/dialog-boxes-overview/invalid-left-margin-dialog.png)  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="a36f3-210">不限制用户对无效控件，直到它们已输入有效的数据。</span><span class="sxs-lookup"><span data-stu-id="a36f3-210">does not restrict a user to the invalid control until they have entered valid data.</span></span> <span data-ttu-id="a36f3-211">这对于对话框来说很好，无论数据是否有效用户都应该可以自由导航到对话框中的控件。</span><span class="sxs-lookup"><span data-stu-id="a36f3-211">This is good behavior for a dialog box; a user should be able to freely navigate the controls in a dialog box whether or not data is valid.</span></span> <span data-ttu-id="a36f3-212">但是，这意味着用户可以输入无效数据并按**确定**按钮。</span><span class="sxs-lookup"><span data-stu-id="a36f3-212">However, this means a user can enter invalid data and press the **OK** button.</span></span> <span data-ttu-id="a36f3-213">出于此原因，代码还需要验证所有控件在对话框中，当**确定**通过处理按下按钮<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="a36f3-213">For this reason, your code also needs to validate all controls in a dialog box when the **OK** button is pressed by handling the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxvalidationcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxValidationCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxvalidationcodebehind3)]  
  
 <span data-ttu-id="a36f3-214">此代码枚举窗口上的所有依赖项对象，如果无效 (返回的<xref:System.Windows.Controls.Validation.GetHasError%2A>，则无效控件获得焦点时，`IsValid`方法将返回`false`，和窗口被视为无效。</span><span class="sxs-lookup"><span data-stu-id="a36f3-214">This code enumerates all dependency objects on a window and, if any are invalid (as returned by <xref:System.Windows.Controls.Validation.GetHasError%2A>, the invalid control gets the focus, the `IsValid` method returns `false`, and the window is considered invalid.</span></span>  
  
 <span data-ttu-id="a36f3-215">一旦对话框有效，就可以安全关闭并返回。</span><span class="sxs-lookup"><span data-stu-id="a36f3-215">Once a dialog box is valid, it can safely close and return.</span></span> <span data-ttu-id="a36f3-216">作为返回过程的一部分，需要将结果返回到调用函数。</span><span class="sxs-lookup"><span data-stu-id="a36f3-216">As part of the return process, it needs to return a result to the calling function.</span></span>  
  
#### <a name="setting-the-modal-dialog-result"></a><span data-ttu-id="a36f3-217">设置模式对话框结果</span><span class="sxs-lookup"><span data-stu-id="a36f3-217">Setting the Modal Dialog Result</span></span>  
 <span data-ttu-id="a36f3-218">打开对话框框中使用<xref:System.Windows.Window.ShowDialog%2A>基本上就像调用方法： 打开对话框框中使用的代码<xref:System.Windows.Window.ShowDialog%2A>将等待，直至<xref:System.Windows.Window.ShowDialog%2A>返回。</span><span class="sxs-lookup"><span data-stu-id="a36f3-218">Opening a dialog box using <xref:System.Windows.Window.ShowDialog%2A> is fundamentally like calling a method: the code that opened the dialog box using <xref:System.Windows.Window.ShowDialog%2A> waits until <xref:System.Windows.Window.ShowDialog%2A> returns.</span></span> <span data-ttu-id="a36f3-219">当<xref:System.Windows.Window.ShowDialog%2A>，则返回的代码需要调用它来决定是否要继续还是停止处理，根据用户按下**确定**按钮或**取消**按钮。</span><span class="sxs-lookup"><span data-stu-id="a36f3-219">When <xref:System.Windows.Window.ShowDialog%2A> returns, the code that called it needs to decide whether to continue processing or stop processing, based on whether the user pressed the **OK** button or the **Cancel** button.</span></span> <span data-ttu-id="a36f3-220">若要帮助做出决定，对话框需要返回用户的选择作为<xref:System.Boolean>从返回的值<xref:System.Windows.Window.ShowDialog%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="a36f3-220">To facilitate this decision, the dialog box needs to return the user's choice as a <xref:System.Boolean> value that is returned from the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span>  
  
 <span data-ttu-id="a36f3-221">当**确定**单击按钮时，<xref:System.Windows.Window.ShowDialog%2A>应返回`true`。</span><span class="sxs-lookup"><span data-stu-id="a36f3-221">When the **OK** button is clicked, <xref:System.Windows.Window.ShowDialog%2A> should return `true`.</span></span> <span data-ttu-id="a36f3-222">这通过设置来实现<xref:System.Windows.Window.DialogResult%2A>属性对话框的框何时**确定**单击按钮。</span><span class="sxs-lookup"><span data-stu-id="a36f3-222">This is achieved by setting the <xref:System.Windows.Window.DialogResult%2A> property of the dialog box when the **OK** button is clicked.</span></span>  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind3)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxokresultsetcodebehind4)]
[!code-vb[DialogBoxSample#MarginsDialogBoxOKResultSetCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxokresultsetcodebehind4)]  
  
 <span data-ttu-id="a36f3-223">请注意，设置<xref:System.Windows.Window.DialogResult%2A>属性还会导致窗口自动关闭，这减少了需要显式调用<xref:System.Windows.Window.Close%2A>。</span><span class="sxs-lookup"><span data-stu-id="a36f3-223">Note that setting the <xref:System.Windows.Window.DialogResult%2A> property also causes the window to close automatically, which alleviates the need to explicitly call <xref:System.Windows.Window.Close%2A>.</span></span>  
  
 <span data-ttu-id="a36f3-224">当**取消**单击按钮时，<xref:System.Windows.Window.ShowDialog%2A>应返回`false`，这也要求设置<xref:System.Windows.Window.DialogResult%2A>属性。</span><span class="sxs-lookup"><span data-stu-id="a36f3-224">When the **Cancel** button is clicked, <xref:System.Windows.Window.ShowDialog%2A> should return `false`, which also requires setting the <xref:System.Windows.Window.DialogResult%2A> property.</span></span>  
  
 [!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind1)]
 [!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind1)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind2)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind2)]  
[!code-csharp[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml.cs#marginsdialogboxcancelresultsetcodebehind3)]
[!code-vb[DialogBoxSample#MarginsDialogBoxCancelResultSetCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MarginsDialogBox.xaml.vb#marginsdialogboxcancelresultsetcodebehind3)]  
  
 <span data-ttu-id="a36f3-225">当按钮的<xref:System.Windows.Controls.Button.IsCancel%2A>属性设置为`true`和用户按**取消**按钮或 ESC 键<xref:System.Windows.Window.DialogResult%2A>会自动设置为`false`。</span><span class="sxs-lookup"><span data-stu-id="a36f3-225">When a button's <xref:System.Windows.Controls.Button.IsCancel%2A> property is set to `true` and the user presses either the **Cancel** button or the ESC key, <xref:System.Windows.Window.DialogResult%2A> is automatically set to `false`.</span></span> <span data-ttu-id="a36f3-226">以下标记具有相同的效果与上面的代码，而无需处理<xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件。</span><span class="sxs-lookup"><span data-stu-id="a36f3-226">The following markup has the same effect as the preceding code, without the need to handle the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  
  
 [!code-xaml[DialogBoxSample#MarginsDialogDefaultCancelMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MarginsDialogBox.xaml#marginsdialogdefaultcancelmarkup)]  
  
 <span data-ttu-id="a36f3-227">一个对话框将自动返回`false`当用户按下**关闭**按钮的标题栏中，也可以选择**关闭**中的菜单项**系统**菜单。</span><span class="sxs-lookup"><span data-stu-id="a36f3-227">A dialog box automatically returns `false` when a user presses the **Close** button in the title bar or chooses the **Close** menu item from the **System** menu.</span></span>  
  
#### <a name="processing-data-returned-from-a-modal-dialog-box"></a><span data-ttu-id="a36f3-228">处理从模式对话框返回的数据</span><span class="sxs-lookup"><span data-stu-id="a36f3-228">Processing Data Returned from a Modal Dialog Box</span></span>  
 <span data-ttu-id="a36f3-229">当<xref:System.Windows.Window.DialogResult%2A>设置对话框中，通过打开它的函数可以通过检查获取对话框结果<xref:System.Windows.Window.DialogResult%2A>属性时<xref:System.Windows.Window.ShowDialog%2A>返回。</span><span class="sxs-lookup"><span data-stu-id="a36f3-229">When <xref:System.Windows.Window.DialogResult%2A> is set by a dialog box, the function that opened it can get the dialog box result by inspecting the <xref:System.Windows.Window.DialogResult%2A> property when <xref:System.Windows.Window.ShowDialog%2A> returns.</span></span>  
  
 [!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind1)]
 [!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind1)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind2)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind2)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind3)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind3)]  
[!code-csharp[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openmarginsdialogprocessreturncodebehind4)]
[!code-vb[DialogBoxSample#OpenMarginsDialogProcessReturnCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openmarginsdialogprocessreturncodebehind4)]  
  
 <span data-ttu-id="a36f3-230">如果对话框结果为`true`，该函数将其用作提示来检索和处理由用户提供的数据。</span><span class="sxs-lookup"><span data-stu-id="a36f3-230">If the dialog result is `true`, the function uses that as a cue to retrieve and process the data provided by the user.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a36f3-231">之后<xref:System.Windows.Window.ShowDialog%2A>已返回，不能重新打开对话框。</span><span class="sxs-lookup"><span data-stu-id="a36f3-231">After <xref:System.Windows.Window.ShowDialog%2A> has returned, a dialog box cannot be reopened.</span></span> <span data-ttu-id="a36f3-232">相反，需要创建新实例。</span><span class="sxs-lookup"><span data-stu-id="a36f3-232">Instead, you need to create a new instance.</span></span>  
  
 <span data-ttu-id="a36f3-233">如果对话框结果为`false`，该函数应适当结束处理。</span><span class="sxs-lookup"><span data-stu-id="a36f3-233">If the dialog result is `false`, the function should end processing appropriately.</span></span>  
  
<a name="Creating_a_Modeless_Custom_Dialog_Box"></a>   
### <a name="creating-a-modeless-custom-dialog-box"></a><span data-ttu-id="a36f3-234">创建无模式自定义对话框</span><span class="sxs-lookup"><span data-stu-id="a36f3-234">Creating a Modeless Custom Dialog Box</span></span>  
 <span data-ttu-id="a36f3-235">无模式对话框（如下图中所示的“查找”对话框）与模式对话框具有相同的基本外观。</span><span class="sxs-lookup"><span data-stu-id="a36f3-235">A modeless dialog box, such as the Find Dialog Box shown in the following figure, has the same fundamental appearance as the modal dialog box.</span></span>  
  
 ![显示查找对话框的屏幕截图。](./media/dialog-boxes-overview/find-modeless-dialog-box.png)  
  
 <span data-ttu-id="a36f3-237">但行为稍有不同，如以下各节中所述。</span><span class="sxs-lookup"><span data-stu-id="a36f3-237">However, the behavior is slightly different, as described in the following sections.</span></span>  
  
#### <a name="opening-a-modeless-dialog-box"></a><span data-ttu-id="a36f3-238">打开无模式对话框</span><span class="sxs-lookup"><span data-stu-id="a36f3-238">Opening a Modeless Dialog Box</span></span>  
 <span data-ttu-id="a36f3-239">通过调用打开无模式对话框<xref:System.Windows.Window.Show%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="a36f3-239">A modeless dialog box is opened by calling the <xref:System.Windows.Window.Show%2A> method.</span></span>  
  
 [!code-xaml[DialogBoxSample#OpenFindDialogMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml#openfinddialogmarkup1)]  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind2)]  
[!code-csharp[DialogBoxSample#OpenFindDialogCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogcodebehind3)]
[!code-vb[DialogBoxSample#OpenFindDialogCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogcodebehind3)]  
  
 <span data-ttu-id="a36f3-240">与不同<xref:System.Windows.Window.ShowDialog%2A>，<xref:System.Windows.Window.Show%2A>立即返回。</span><span class="sxs-lookup"><span data-stu-id="a36f3-240">Unlike <xref:System.Windows.Window.ShowDialog%2A>, <xref:System.Windows.Window.Show%2A> returns immediately.</span></span> <span data-ttu-id="a36f3-241">因此，调用窗口无法判断无模式对话框何时关闭，也就不知道何时检查对话框结果或从对话框获取数据进行进一步处理。</span><span class="sxs-lookup"><span data-stu-id="a36f3-241">Consequently, the calling window cannot tell when the modeless dialog box is closed and, therefore, does not know when to check for a dialog box result or get data from the dialog box for further processing.</span></span> <span data-ttu-id="a36f3-242">相反，对话框需要创建替代方法来将数据返回到调用窗口进行处理。</span><span class="sxs-lookup"><span data-stu-id="a36f3-242">Instead, the dialog box needs to create an alternative way to return data to the calling window for processing.</span></span>  
  
#### <a name="processing-data-returned-from-a-modeless-dialog-box"></a><span data-ttu-id="a36f3-243">处理无模式对话框返回的数据</span><span class="sxs-lookup"><span data-stu-id="a36f3-243">Processing Data Returned from a Modeless Dialog Box</span></span>  
 <span data-ttu-id="a36f3-244">在此示例中，`FindDialogBox`可能会返回一个或多个查找到主窗口中，具体取决于要而无需任何特定频率搜索的文本的结果。</span><span class="sxs-lookup"><span data-stu-id="a36f3-244">In this example, the `FindDialogBox` may return one or more find results to the main window, depending on the text being searched for without any specific frequency.</span></span> <span data-ttu-id="a36f3-245">和模式对话框一样，无模式对话框也可以使用属性返回结果。</span><span class="sxs-lookup"><span data-stu-id="a36f3-245">As with a modal dialog box, a modeless dialog box can return results using properties.</span></span> <span data-ttu-id="a36f3-246">但拥有对话框的窗口需要了解何时检查那些属性。</span><span class="sxs-lookup"><span data-stu-id="a36f3-246">However, the window that owns the dialog box needs to know when to check those properties.</span></span> <span data-ttu-id="a36f3-247">实现此目的的一种方法是用对话框实现事件，只要找到文本就引发它。</span><span class="sxs-lookup"><span data-stu-id="a36f3-247">One way to enable this is for the dialog box to implement an event that is raised whenever text is found.</span></span> `FindDialogBox` <span data-ttu-id="a36f3-248">实现`TextFoundEvent`出于此目的，这首先需要委托。</span><span class="sxs-lookup"><span data-stu-id="a36f3-248">implements the `TextFoundEvent` for this purpose, which first requires a delegate.</span></span>  
  
 [!code-csharp[DialogBoxSample#TextFoundEventHandlerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/TextFoundEventHandler.cs#textfoundeventhandlercode)]
 [!code-vb[DialogBoxSample#TextFoundEventHandlerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/TextFoundEventHandler.vb#textfoundeventhandlercode)]  
  
 <span data-ttu-id="a36f3-249">使用`TextFoundEventHandler`委派，请`FindDialogBox`实现`TextFoundEvent`。</span><span class="sxs-lookup"><span data-stu-id="a36f3-249">Using the `TextFoundEventHandler` delegate, `FindDialogBox` implements the `TextFoundEvent`.</span></span>  
  
 [!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventcodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventcodebehind2)]  
  
 <span data-ttu-id="a36f3-250">因此，`Find`可以引发事件时找到搜索结果。</span><span class="sxs-lookup"><span data-stu-id="a36f3-250">Consequently, `Find` can raise the event when a search result is found.</span></span>  
  
 [!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind1)]
 [!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind1)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind2)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind2)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind3)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind3)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind4)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind4)]  
[!code-csharp[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#textfoundeventraisecodebehind5)]
[!code-vb[DialogBoxSample#TextFoundEventRaiseCODEBEHIND5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#textfoundeventraisecodebehind5)]  
  
 <span data-ttu-id="a36f3-251">所有者窗口则需要注册和处理此事件。</span><span class="sxs-lookup"><span data-stu-id="a36f3-251">The owner window then needs to register with and handle this event.</span></span>  
  
 [!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind1)]
 [!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind1)]  
[!code-csharp[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/MainWindow.xaml.cs#openfinddialogresultcodebehind2)]
[!code-vb[DialogBoxSample#OpenFindDialogResultCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/MainWindow.xaml.vb#openfinddialogresultcodebehind2)]  
  
#### <a name="closing-a-modeless-dialog-box"></a><span data-ttu-id="a36f3-252">关闭无模式对话框</span><span class="sxs-lookup"><span data-stu-id="a36f3-252">Closing a Modeless Dialog Box</span></span>  
 <span data-ttu-id="a36f3-253">因为<xref:System.Windows.Window.DialogResult%2A>不需要为其设置，可以使用系统关闭无模式对话框提供机制，包括以下：</span><span class="sxs-lookup"><span data-stu-id="a36f3-253">Because <xref:System.Windows.Window.DialogResult%2A> does not need to be set, a modeless dialog can be closed using system provide mechanisms, including the following:</span></span>  
  
-   <span data-ttu-id="a36f3-254">单击**关闭**标题栏中的按钮。</span><span class="sxs-lookup"><span data-stu-id="a36f3-254">Clicking the **Close** button in the title bar.</span></span>  
  
-   <span data-ttu-id="a36f3-255">按 ALT+F4。</span><span class="sxs-lookup"><span data-stu-id="a36f3-255">Pressing ALT+F4.</span></span>  
  
-   <span data-ttu-id="a36f3-256">选择**关闭**从**系统**菜单。</span><span class="sxs-lookup"><span data-stu-id="a36f3-256">Choosing **Close** from the **System** menu.</span></span>  
  
 <span data-ttu-id="a36f3-257">或者，你的代码可以调用<xref:System.Windows.Window.Close%2A>时**关闭**单击按钮。</span><span class="sxs-lookup"><span data-stu-id="a36f3-257">Alternatively, your code can call <xref:System.Windows.Window.Close%2A> when the **Close** button is clicked.</span></span>  
  
 [!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind1)]
 [!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind1)]  
[!code-csharp[DialogBoxSample#FindDialogCloseCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/DialogBoxSample/CSharp/FindDialogBox.xaml.cs#finddialogclosecodebehind2)]
[!code-vb[DialogBoxSample#FindDialogCloseCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DialogBoxSample/VisualBasic/FindDialogBox.xaml.vb#finddialogclosecodebehind2)]  
  
## <a name="see-also"></a><span data-ttu-id="a36f3-258">请参阅</span><span class="sxs-lookup"><span data-stu-id="a36f3-258">See also</span></span>

- [<span data-ttu-id="a36f3-259">Popup 概述</span><span class="sxs-lookup"><span data-stu-id="a36f3-259">Popup Overview</span></span>](../controls/popup-overview.md)
- [<span data-ttu-id="a36f3-260">对话框示例</span><span class="sxs-lookup"><span data-stu-id="a36f3-260">Dialog Box Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159984)
- [<span data-ttu-id="a36f3-261">ColorPicker 自定义控件示例</span><span class="sxs-lookup"><span data-stu-id="a36f3-261">ColorPicker Custom Control Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159977)
