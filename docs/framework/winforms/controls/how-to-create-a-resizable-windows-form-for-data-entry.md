---
title: 如何：创建用于数据输入的大小可调的 Windows 窗体
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: a632b243715ee42243c184aa2aca25abb6347f9a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733319"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a><span data-ttu-id="95a05-102">如何：创建用于数据输入的大小可调的 Windows 窗体</span><span class="sxs-lookup"><span data-stu-id="95a05-102">How to: Create a Resizable Windows Form for Data Entry</span></span>
<span data-ttu-id="95a05-103">良好的布局可以很好地响应其父窗体尺寸的更改。</span><span class="sxs-lookup"><span data-stu-id="95a05-103">A good layout responds well to changes in the dimensions of its parent form.</span></span> <span data-ttu-id="95a05-104">可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控件来安排窗体布局，从而以与窗体尺寸更改一致的方式调整和定位控件。</span><span class="sxs-lookup"><span data-stu-id="95a05-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to arrange the layout of your form to resize and position your controls in a consistent way as the form's dimensions change.</span></span> <span data-ttu-id="95a05-105">当控件内容的更改引起布局更改时，<xref:System.Windows.Forms.TableLayoutPanel> 控件也会很有用。</span><span class="sxs-lookup"><span data-stu-id="95a05-105">The <xref:System.Windows.Forms.TableLayoutPanel> control is also useful when changes in the contents of your controls cause changes in the layout.</span></span> <span data-ttu-id="95a05-106">可以在 Visual Studio 环境中完成此过程所涵盖的进程。</span><span class="sxs-lookup"><span data-stu-id="95a05-106">The process covered in this procedure can be done within the Visual Studio environment.</span></span>  <span data-ttu-id="95a05-107">另请参阅[演练：创建数据输入可调整大小的 Windows 窗体](https://msdn.microsoft.com/library/991eahec\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="95a05-107">Also see [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://msdn.microsoft.com/library/991eahec\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95a05-108">示例</span><span class="sxs-lookup"><span data-stu-id="95a05-108">Example</span></span>  
 <span data-ttu-id="95a05-109">下面的示例演示当用户调整窗体大小时，如何使用 <xref:System.Windows.Forms.TableLayoutPanel> 控件构建响应良好的布局。</span><span class="sxs-lookup"><span data-stu-id="95a05-109">The following example demonstrates how to use a <xref:System.Windows.Forms.TableLayoutPanel> control to build a layout that responds well when the user resizes the form.</span></span> <span data-ttu-id="95a05-110">它还演示一个适合本地化的布局。</span><span class="sxs-lookup"><span data-stu-id="95a05-110">It also demonstrates a layout that responds well to localization.</span></span>  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="95a05-111">编译代码</span><span class="sxs-lookup"><span data-stu-id="95a05-111">Compiling the Code</span></span>  
 <span data-ttu-id="95a05-112">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="95a05-112">This example requires:</span></span>  
  
-   <span data-ttu-id="95a05-113">对 System、System.Data、System.Drawing 和 System.Windows.Forms 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="95a05-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="95a05-114">Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="95a05-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="95a05-115">也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="95a05-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="95a05-116">另请参阅[如何：编译和运行完整的 Windows 窗体代码示例使用 Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="95a05-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a05-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="95a05-117">See also</span></span>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [<span data-ttu-id="95a05-118">如何：锚定和停靠在 TableLayoutPanel 控件中的子控件</span><span class="sxs-lookup"><span data-stu-id="95a05-118">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="95a05-119">如何：设计很好地响应本地化 Windows 窗体布局</span><span class="sxs-lookup"><span data-stu-id="95a05-119">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [<span data-ttu-id="95a05-120">Microsoft Windows 用户体验，用户界面开发人员和设计人员的官方指南。Redmond，WA:Microsoft Press，1999年。(USBN:0-7356-0566-1)</span><span class="sxs-lookup"><span data-stu-id="95a05-120">Microsoft Windows User Experience, Official Guidelines for User Interface Developers and Designers. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)</span></span>](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
