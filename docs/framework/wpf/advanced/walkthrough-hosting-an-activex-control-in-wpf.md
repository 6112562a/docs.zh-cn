---
title: 演练：在 WPF 中承载 ActiveX 控件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 0181093de1c40889110ab7eae75a3847a17845a9
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859938"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a><span data-ttu-id="cc32f-102">演练：在 WPF 中承载 ActiveX 控件</span><span class="sxs-lookup"><span data-stu-id="cc32f-102">Walkthrough: Hosting an ActiveX Control in WPF</span></span>
<span data-ttu-id="cc32f-103">若要启用改进与浏览器交互，可以使用中的 Microsoft ActiveX 控件在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-基于应用程序。</span><span class="sxs-lookup"><span data-stu-id="cc32f-103">To enable improved interaction with browsers, you can use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span> <span data-ttu-id="cc32f-104">本演练演示如何可以承载[!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)]上的控件作为[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]页。</span><span class="sxs-lookup"><span data-stu-id="cc32f-104">This walkthrough demonstrates how you can host the [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] as a control on a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] page.</span></span>

 <span data-ttu-id="cc32f-105">本演练涉及以下任务：</span><span class="sxs-lookup"><span data-stu-id="cc32f-105">Tasks illustrated in this walkthrough include:</span></span>

- <span data-ttu-id="cc32f-106">创建项目。</span><span class="sxs-lookup"><span data-stu-id="cc32f-106">Creating the project.</span></span>

- <span data-ttu-id="cc32f-107">创建 ActiveX 控件。</span><span class="sxs-lookup"><span data-stu-id="cc32f-107">Creating the ActiveX control.</span></span>

- <span data-ttu-id="cc32f-108">承载 WPF 页上的 ActiveX 控件。</span><span class="sxs-lookup"><span data-stu-id="cc32f-108">Hosting the ActiveX control on a WPF Page.</span></span>

 <span data-ttu-id="cc32f-109">完成本演练后，您将了解如何使用 Microsoft ActiveX 控件中的你[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-基于应用程序。</span><span class="sxs-lookup"><span data-stu-id="cc32f-109">When you have completed this walkthrough, you will understand how to use Microsoft ActiveX controls in your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-based application.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cc32f-110">系统必备</span><span class="sxs-lookup"><span data-stu-id="cc32f-110">Prerequisites</span></span>
 <span data-ttu-id="cc32f-111">你需要以下组件来完成本演练：</span><span class="sxs-lookup"><span data-stu-id="cc32f-111">You need the following components to complete this walkthrough:</span></span>

- [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] <span data-ttu-id="cc32f-112">安装 Visual Studio 的计算机上安装。</span><span class="sxs-lookup"><span data-stu-id="cc32f-112">installed on the computer where Visual Studio is installed.</span></span>

- <span data-ttu-id="cc32f-113">Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="cc32f-113">Visual Studio 2010.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="cc32f-114">创建项目</span><span class="sxs-lookup"><span data-stu-id="cc32f-114">Creating the Project</span></span>

### <a name="to-create-and-set-up-the-project"></a><span data-ttu-id="cc32f-115">创建并设置项目</span><span class="sxs-lookup"><span data-stu-id="cc32f-115">To create and set up the project</span></span>

1. <span data-ttu-id="cc32f-116">创建一个名为的 WPF 应用程序项目`HostingAxInWpf`。</span><span class="sxs-lookup"><span data-stu-id="cc32f-116">Create a WPF Application project named `HostingAxInWpf`.</span></span>

2. <span data-ttu-id="cc32f-117">将 Windows 窗体控件库项目添加到解决方案，并将项目命名`WmpAxLib`。</span><span class="sxs-lookup"><span data-stu-id="cc32f-117">Add a Windows Forms Control Library project to the solution, and name the project `WmpAxLib`.</span></span>

3. <span data-ttu-id="cc32f-118">在 WmpAxLib 项目中，将添加到名为 wmp.dll 的 Windows Media Player 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="cc32f-118">In the WmpAxLib project, add a reference to the Windows Media Player assembly, which is named wmp.dll.</span></span>

4. <span data-ttu-id="cc32f-119">打开**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="cc32f-119">Open the **Toolbox**.</span></span>

5. <span data-ttu-id="cc32f-120">在中右击**工具箱**，然后单击**选择项**。</span><span class="sxs-lookup"><span data-stu-id="cc32f-120">Right-click in the **Toolbox**, and then click **Choose Items**.</span></span>

6. <span data-ttu-id="cc32f-121">单击**COM 组件**选项卡上，选择**Windows Media Player**控件，，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="cc32f-121">Click the **COM Components** tab, select the **Windows Media Player** control, and then click **OK**.</span></span>

     <span data-ttu-id="cc32f-122">Windows Media Player 控件添加到**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="cc32f-122">The Windows Media Player control is added to the **Toolbox**.</span></span>

7. <span data-ttu-id="cc32f-123">在解决方案资源管理器中右键单击**UserControl1**文件，，然后单击**重命名**。</span><span class="sxs-lookup"><span data-stu-id="cc32f-123">In Solution Explorer, right-click the **UserControl1** file, and then click **Rename**.</span></span>

8. <span data-ttu-id="cc32f-124">将名称更改为`WmpAxControl.vb`或`WmpAxControl.cs`，取决于语言。</span><span class="sxs-lookup"><span data-stu-id="cc32f-124">Change the name to `WmpAxControl.vb` or `WmpAxControl.cs`, depending on the language.</span></span>

9. <span data-ttu-id="cc32f-125">如果系统提示重命名所有引用，请单击**是**。</span><span class="sxs-lookup"><span data-stu-id="cc32f-125">If you are prompted to rename all references, click **Yes**.</span></span>

## <a name="creating-the-activex-control"></a><span data-ttu-id="cc32f-126">创建 ActiveX 控件</span><span class="sxs-lookup"><span data-stu-id="cc32f-126">Creating the ActiveX Control</span></span>
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] <span data-ttu-id="cc32f-127">自动生成<xref:System.Windows.Forms.AxHost>Microsoft ActiveX 控件时，该控件添加到设计图面上的包装类。</span><span class="sxs-lookup"><span data-stu-id="cc32f-127">automatically generates an <xref:System.Windows.Forms.AxHost> wrapper class for a Microsoft ActiveX control when the control is added to a design surface.</span></span> <span data-ttu-id="cc32f-128">以下过程创建名为 AxInterop.WMPLib.dll 托管程序集。</span><span class="sxs-lookup"><span data-stu-id="cc32f-128">The following procedure creates a managed assembly named AxInterop.WMPLib.dll.</span></span>

### <a name="to-create-the-activex-control"></a><span data-ttu-id="cc32f-129">若要创建 ActiveX 控件</span><span class="sxs-lookup"><span data-stu-id="cc32f-129">To create the ActiveX control</span></span>

1. <span data-ttu-id="cc32f-130">在 Windows 窗体设计器中打开 WmpAxControl.vb 或 WmpAxControl.cs。</span><span class="sxs-lookup"><span data-stu-id="cc32f-130">Open WmpAxControl.vb or WmpAxControl.cs in the Windows Forms Designer.</span></span>

2. <span data-ttu-id="cc32f-131">从**工具箱**，将 Windows Media Player 控件添加到设计图面。</span><span class="sxs-lookup"><span data-stu-id="cc32f-131">From the **Toolbox**, add the Windows Media Player control to the design surface.</span></span>

3. <span data-ttu-id="cc32f-132">在属性窗口中，将 Windows Media Player 控件的值设置<xref:System.Windows.Forms.Control.Dock%2A>属性设置为<xref:System.Windows.Forms.DockStyle.Fill>。</span><span class="sxs-lookup"><span data-stu-id="cc32f-132">In the Properties window, set the value of the Windows Media Player control's <xref:System.Windows.Forms.Control.Dock%2A> property to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

4. <span data-ttu-id="cc32f-133">生成 WmpAxLib 控件库项目。</span><span class="sxs-lookup"><span data-stu-id="cc32f-133">Build the WmpAxLib control library project.</span></span>

## <a name="hosting-the-activex-control-on-a-wpf-page"></a><span data-ttu-id="cc32f-134">承载 WPF 页上的 ActiveX 控件</span><span class="sxs-lookup"><span data-stu-id="cc32f-134">Hosting the ActiveX Control on a WPF Page</span></span>

### <a name="to-host-the-activex-control"></a><span data-ttu-id="cc32f-135">若要承载 ActiveX 控件</span><span class="sxs-lookup"><span data-stu-id="cc32f-135">To host the ActiveX control</span></span>

1. <span data-ttu-id="cc32f-136">在 HostingAxInWpf 项目中，添加对生成的 ActiveX 互操作性程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="cc32f-136">In the HostingAxInWpf project, add a reference to the generated ActiveX interoperability assembly.</span></span>

     <span data-ttu-id="cc32f-137">此程序集名为 AxInterop.WMPLib.dll 和时导入 Windows Media Player 控件添加到 WmpAxLib 项目的调试文件夹。</span><span class="sxs-lookup"><span data-stu-id="cc32f-137">This assembly is named AxInterop.WMPLib.dll and was added to the Debug folder of the WmpAxLib project when you imported the Windows Media Player control.</span></span>

2. <span data-ttu-id="cc32f-138">添加对 WindowsFormsIntegration 程序集，它名为 WindowsFormsIntegration.dll 的引用。</span><span class="sxs-lookup"><span data-stu-id="cc32f-138">Add a reference to the WindowsFormsIntegration assembly, which is named WindowsFormsIntegration.dll.</span></span>

3. <span data-ttu-id="cc32f-139">添加对引用[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]名为 system.windows.forms.dll 的引用的程序集。</span><span class="sxs-lookup"><span data-stu-id="cc32f-139">Add a reference to the [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] assembly, which is named System.Windows.Forms.dll.</span></span>

4. <span data-ttu-id="cc32f-140">在 WPF 设计器中打开 MainWindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="cc32f-140">Open MainWindow.xaml in the WPF Designer.</span></span>

5. <span data-ttu-id="cc32f-141">名称<xref:System.Windows.Controls.Grid>元素`grid1`。</span><span class="sxs-lookup"><span data-stu-id="cc32f-141">Name the <xref:System.Windows.Controls.Grid> element `grid1`.</span></span>

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. <span data-ttu-id="cc32f-142">在设计视图或 XAML 视图中，选择<xref:System.Windows.Window>元素。</span><span class="sxs-lookup"><span data-stu-id="cc32f-142">In Design view or XAML view, select the <xref:System.Windows.Window> element.</span></span>

7. <span data-ttu-id="cc32f-143">在属性窗口中，单击**事件**选项卡。</span><span class="sxs-lookup"><span data-stu-id="cc32f-143">In the Properties window, click the **Events** tab.</span></span>

8. <span data-ttu-id="cc32f-144">双击<xref:System.Windows.FrameworkElement.Loaded>事件。</span><span class="sxs-lookup"><span data-stu-id="cc32f-144">Double-click the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

9. <span data-ttu-id="cc32f-145">插入以下代码以处理<xref:System.Windows.FrameworkElement.Loaded>事件。</span><span class="sxs-lookup"><span data-stu-id="cc32f-145">Insert the following code to handle the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span>

     <span data-ttu-id="cc32f-146">此代码创建的实例<xref:System.Windows.Forms.Integration.WindowsFormsHost>控件，添加的实例`AxWindowsMediaPlayer`作为其子级的控件。</span><span class="sxs-lookup"><span data-stu-id="cc32f-146">This code creates an instance of the <xref:System.Windows.Forms.Integration.WindowsFormsHost> control and adds an instance of the `AxWindowsMediaPlayer` control as its child.</span></span>

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. <span data-ttu-id="cc32f-147">按 F5 生成并运行该应用程序。</span><span class="sxs-lookup"><span data-stu-id="cc32f-147">Press F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc32f-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="cc32f-148">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="cc32f-149">在 Visual Studio 中设计 XAML</span><span class="sxs-lookup"><span data-stu-id="cc32f-149">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
- [<span data-ttu-id="cc32f-150">演练：承载在 WPF 中的 Windows 窗体复合控件</span><span class="sxs-lookup"><span data-stu-id="cc32f-150">Walkthrough: Hosting a Windows Forms Composite Control in WPF</span></span>](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [<span data-ttu-id="cc32f-151">演练：承载 WPF 复合控件在 Windows 窗体中</span><span class="sxs-lookup"><span data-stu-id="cc32f-151">Walkthrough: Hosting a WPF Composite Control in Windows Forms</span></span>](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
