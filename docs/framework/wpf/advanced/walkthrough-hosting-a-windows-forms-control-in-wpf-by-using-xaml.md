---
title: 演练：使用 XAML 承载在 WPF 中的 Windows 窗体控件
ms.date: 03/30/2017
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 1aef42cb-4cfb-44b4-9a7a-c02632d3d9c7
ms.openlocfilehash: 1566f27703e2603a5d70cf8cfc7a01a08c407f6a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379531"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml"></a><span data-ttu-id="95d1b-102">演练：使用 XAML 承载在 WPF 中的 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="95d1b-102">Walkthrough: Hosting a Windows Forms Control in WPF by Using XAML</span></span>
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="95d1b-103">提供了许多具有丰富功能集的控件。</span><span class="sxs-lookup"><span data-stu-id="95d1b-103">provides many controls with a rich feature set.</span></span> <span data-ttu-id="95d1b-104">但是，您可能有时想要使用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]上的控件在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]页。</span><span class="sxs-lookup"><span data-stu-id="95d1b-104">However, you may sometimes want to use [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls on your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pages.</span></span> <span data-ttu-id="95d1b-105">例如，可能有大量现有投入[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控件，或者您可能需[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]控件，用于提供的独特功能。</span><span class="sxs-lookup"><span data-stu-id="95d1b-105">For example, you may have a substantial investment in existing [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] controls, or you may have a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] control that provides unique functionality.</span></span>  
  
 <span data-ttu-id="95d1b-106">本演练演示如何承载 Windows 窗体<xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>对的 control 权限[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]页上通过使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="95d1b-106">This walkthrough shows you how to host a Windows Forms <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType> control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page by using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 <span data-ttu-id="95d1b-107">在本演练中所示的任务的完整代码列表，请参阅[承载 Windows 窗体控件在 WPF 中使用 XAML 示例](https://go.microsoft.com/fwlink/?LinkID=160000)。</span><span class="sxs-lookup"><span data-stu-id="95d1b-107">For a complete code listing of the tasks shown in this walkthrough, see [Hosting a Windows Forms Control in WPF by Using XAML Sample](https://go.microsoft.com/fwlink/?LinkID=160000).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="95d1b-108">系统必备</span><span class="sxs-lookup"><span data-stu-id="95d1b-108">Prerequisites</span></span>  

<span data-ttu-id="95d1b-109">若要完成本演练，必须具有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="95d1b-109">You need Visual Studio to complete this walkthrough.</span></span>  
  
## <a name="hosting-the-windows-forms-control"></a><span data-ttu-id="95d1b-110">承载 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="95d1b-110">Hosting the Windows Forms Control</span></span>  
  
#### <a name="to-host-the-maskedtextbox-control"></a><span data-ttu-id="95d1b-111">承载 MaskedTextBox 控件</span><span class="sxs-lookup"><span data-stu-id="95d1b-111">To host the MaskedTextBox control</span></span>  
  
1.  <span data-ttu-id="95d1b-112">创建一个名为的 WPF 应用程序项目`HostingWfInWpfWithXaml`。</span><span class="sxs-lookup"><span data-stu-id="95d1b-112">Create a WPF Application project named `HostingWfInWpfWithXaml`.</span></span>  
  
2.  <span data-ttu-id="95d1b-113">添加对下列程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="95d1b-113">Add references to the following assemblies.</span></span>  
  
    -   <span data-ttu-id="95d1b-114">WindowsFormsIntegration</span><span class="sxs-lookup"><span data-stu-id="95d1b-114">WindowsFormsIntegration</span></span>  
  
    -   <span data-ttu-id="95d1b-115">System.Windows.Forms</span><span class="sxs-lookup"><span data-stu-id="95d1b-115">System.Windows.Forms</span></span>  
  
3.  <span data-ttu-id="95d1b-116">打开 MainWindow.xaml 中的[!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="95d1b-116">Open MainWindow.xaml in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
4.  <span data-ttu-id="95d1b-117">在<xref:System.Windows.Window>元素中，添加以下命名空间映射。</span><span class="sxs-lookup"><span data-stu-id="95d1b-117">In the <xref:System.Windows.Window> element, add the following namespace mapping.</span></span> <span data-ttu-id="95d1b-118">`wf`命名空间映射建立对包含在 Windows 窗体控件的程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="95d1b-118">The `wf` namespace mapping establishes a reference to the assembly that contains the Windows Forms control.</span></span>  
  
    ```xaml  
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"  
    ```  
  
5.  <span data-ttu-id="95d1b-119">在<xref:System.Windows.Controls.Grid>添加以下 XAML 元素。</span><span class="sxs-lookup"><span data-stu-id="95d1b-119">In the <xref:System.Windows.Controls.Grid> element add the following XAML.</span></span>  
  
     <span data-ttu-id="95d1b-120"><xref:System.Windows.Forms.MaskedTextBox>控件被创建为的子<xref:System.Windows.Forms.Integration.WindowsFormsHost>控件。</span><span class="sxs-lookup"><span data-stu-id="95d1b-120">The <xref:System.Windows.Forms.MaskedTextBox> control is created as a child of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control.</span></span>  
  
     [!code-xaml[HostingWfInWpfWithXaml#3](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWpfWithXaml/CSharp/HostingWfInWpf/Window1.xaml#3)]  
  
6.  <span data-ttu-id="95d1b-121">按 F5 生成并运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="95d1b-121">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d1b-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="95d1b-122">See also</span></span>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="95d1b-123">在 Visual Studio 中设计 XAML</span><span class="sxs-lookup"><span data-stu-id="95d1b-123">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="95d1b-124">演练：承载在 WPF 中的 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="95d1b-124">Walkthrough: Hosting a Windows Forms Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [<span data-ttu-id="95d1b-125">演练：承载在 WPF 中的 Windows 窗体复合控件</span><span class="sxs-lookup"><span data-stu-id="95d1b-125">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="95d1b-126">演练：承载 WPF 复合控件在 Windows 窗体中</span><span class="sxs-lookup"><span data-stu-id="95d1b-126">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [<span data-ttu-id="95d1b-127">Windows 窗体控件和等效的 WPF 控件</span><span class="sxs-lookup"><span data-stu-id="95d1b-127">Windows Forms Controls and Equivalent WPF Controls</span></span>](windows-forms-controls-and-equivalent-wpf-controls.md)
- [<span data-ttu-id="95d1b-128">通过使用 XAML 示例中承载 WPF 中的 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="95d1b-128">Hosting a Windows Forms Control in WPF by Using XAML Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160000)
