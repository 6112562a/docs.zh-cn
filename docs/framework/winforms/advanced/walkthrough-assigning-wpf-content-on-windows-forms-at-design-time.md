---
title: 演练：在设计时在 Windows 窗体上分配 WPF 内容
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
ms.openlocfilehash: b4efef869c96ddb4e58445e45ecad12b5658f9f4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343338"
---
# <a name="walkthrough-assigning-wpf-content-on-windows-forms-at-design-time"></a><span data-ttu-id="731cc-102">演练：在设计时在 Windows 窗体上分配 WPF 内容</span><span class="sxs-lookup"><span data-stu-id="731cc-102">Walkthrough: Assigning WPF Content on Windows Forms at Design Time</span></span>
<span data-ttu-id="731cc-103">本演练展示了如何选择要在窗体上显示的 Windows Presentation Foundation (WPF) 控件类型。</span><span class="sxs-lookup"><span data-stu-id="731cc-103">This walkthrough show you how to select the Windows Presentation Foundation (WPF) control types you want to display on your form.</span></span> <span data-ttu-id="731cc-104">可选择项目中包含的任何 WPF 控件类型。</span><span class="sxs-lookup"><span data-stu-id="731cc-104">You can select any WPF control types which are included in your project.</span></span>

 <span data-ttu-id="731cc-105">在本演练中，你将要执行以下任务：</span><span class="sxs-lookup"><span data-stu-id="731cc-105">In this walkthrough, you perform the following tasks:</span></span>

-   <span data-ttu-id="731cc-106">创建项目。</span><span class="sxs-lookup"><span data-stu-id="731cc-106">Create the project.</span></span>

-   <span data-ttu-id="731cc-107">创建 WPF 控件类型。</span><span class="sxs-lookup"><span data-stu-id="731cc-107">Create the WPF control types.</span></span>

-   <span data-ttu-id="731cc-108">选择 WPF 控件。</span><span class="sxs-lookup"><span data-stu-id="731cc-108">Select WPF controls.</span></span>

> [!NOTE]
>  <span data-ttu-id="731cc-109">显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。</span><span class="sxs-lookup"><span data-stu-id="731cc-109">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="731cc-110">若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。</span><span class="sxs-lookup"><span data-stu-id="731cc-110">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="731cc-111">有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="731cc-111">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="731cc-112">系统必备</span><span class="sxs-lookup"><span data-stu-id="731cc-112">Prerequisites</span></span>  
 <span data-ttu-id="731cc-113">你需要以下组件来完成本演练：</span><span class="sxs-lookup"><span data-stu-id="731cc-113">You need the following components to complete this walkthrough:</span></span>  
  
-   <span data-ttu-id="731cc-114">Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="731cc-114">Visual Studio 2012.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="731cc-115">创建项目</span><span class="sxs-lookup"><span data-stu-id="731cc-115">Creating the Project</span></span>  
 <span data-ttu-id="731cc-116">第一步是创建 Windows 窗体项目。</span><span class="sxs-lookup"><span data-stu-id="731cc-116">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="731cc-117">承载 WPF 内容时，仅支持 C# 和 Visual Basic 项目。</span><span class="sxs-lookup"><span data-stu-id="731cc-117">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="731cc-118">要创建项目</span><span class="sxs-lookup"><span data-stu-id="731cc-118">To create the project</span></span>  
  
-   <span data-ttu-id="731cc-119">创建新的 Windows 窗体应用程序项目在 Visual Basic 或 Visual C# 名为`SelectingWpfContent`。</span><span class="sxs-lookup"><span data-stu-id="731cc-119">Create a new Windows Forms Application project in Visual Basic or Visual C# named `SelectingWpfContent`.</span></span>  
  
## <a name="creating-the-wpf-control-types"></a><span data-ttu-id="731cc-120">创建 WPF 控件类型</span><span class="sxs-lookup"><span data-stu-id="731cc-120">Creating the WPF Control Types</span></span>  
 <span data-ttu-id="731cc-121">将 WPF 控件类型添加到项目后，可将其托管到不同的 <xref:System.Windows.Forms.Integration.ElementHost> 控件。</span><span class="sxs-lookup"><span data-stu-id="731cc-121">After you add WPF control types to the project, you can host them in different <xref:System.Windows.Forms.Integration.ElementHost> controls.</span></span>  
  
#### <a name="to-create-wpf-control-types"></a><span data-ttu-id="731cc-122">创建 WPF 控件类型</span><span class="sxs-lookup"><span data-stu-id="731cc-122">To create WPF control types</span></span>  
  
1. <span data-ttu-id="731cc-123">将新的 WPF <xref:System.Windows.Controls.UserControl> 项目添加到解决方案。</span><span class="sxs-lookup"><span data-stu-id="731cc-123">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="731cc-124">使用控件类型的默认名称，`UserControl1.xaml`。</span><span class="sxs-lookup"><span data-stu-id="731cc-124">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="731cc-125">有关详细信息，请参见[演练：在设计时在 Windows 窗体上创建新的 WPF 内容](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)。</span><span class="sxs-lookup"><span data-stu-id="731cc-125">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2. <span data-ttu-id="731cc-126">在设计视图中，请确保已选中 `UserControl1`。</span><span class="sxs-lookup"><span data-stu-id="731cc-126">In Design view, make sure that `UserControl1` is selected.</span></span> <span data-ttu-id="731cc-127">有关详细信息，请参阅[如何：选择并在设计图面上移动元素](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="731cc-127">For more information, see [How to: Select and Move Elements on the Design Surface](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100)).</span></span>  
  
3. <span data-ttu-id="731cc-128">在中**属性**窗口中，设置的值<xref:System.Windows.FrameworkElement.Width%2A>并<xref:System.Windows.FrameworkElement.Height%2A>属性设置为`200`。</span><span class="sxs-lookup"><span data-stu-id="731cc-128">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
4. <span data-ttu-id="731cc-129">添加<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>控制对<xref:System.Windows.Controls.UserControl>并将值设置<xref:System.Windows.Controls.TextBox.Text%2A>属性设置为**承载的内容**。</span><span class="sxs-lookup"><span data-stu-id="731cc-129">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content**.</span></span>  
  
5. <span data-ttu-id="731cc-130">将第二个 WPF <xref:System.Windows.Controls.UserControl> 添加到项目。</span><span class="sxs-lookup"><span data-stu-id="731cc-130">Add a second WPF <xref:System.Windows.Controls.UserControl> to the project.</span></span> <span data-ttu-id="731cc-131">使用控件类型的默认名称，`UserControl2.xaml`。</span><span class="sxs-lookup"><span data-stu-id="731cc-131">Use the default name for the control type, `UserControl2.xaml`.</span></span>  
  
6. <span data-ttu-id="731cc-132">在中**属性**窗口中，设置的值<xref:System.Windows.FrameworkElement.Width%2A>并<xref:System.Windows.FrameworkElement.Height%2A>属性设置为`200`。</span><span class="sxs-lookup"><span data-stu-id="731cc-132">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties to `200`.</span></span>  
  
7. <span data-ttu-id="731cc-133">添加<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>控制对<xref:System.Windows.Controls.UserControl>并将值设置<xref:System.Windows.Controls.TextBox.Text%2A>属性设置为**承载的内容 2**。</span><span class="sxs-lookup"><span data-stu-id="731cc-133">Add a <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control to the <xref:System.Windows.Controls.UserControl> and set the value of the <xref:System.Windows.Controls.TextBox.Text%2A> property to **Hosted Content 2**.</span></span>  
  
 <span data-ttu-id="731cc-134">**请注意**一般情况下，你应承载更复杂的 WPF 内容。</span><span class="sxs-lookup"><span data-stu-id="731cc-134">**Note** In general, you should host more sophisticated WPF content.</span></span> <span data-ttu-id="731cc-135">此处，<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> 控件仅为了便于说明。</span><span class="sxs-lookup"><span data-stu-id="731cc-135">The <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> control is used here for illustrative purposes only.</span></span>  
  
1. <span data-ttu-id="731cc-136">生成项目。</span><span class="sxs-lookup"><span data-stu-id="731cc-136">Build the project.</span></span>  
  
## <a name="selecting-wpf-controls"></a><span data-ttu-id="731cc-137">选择 WPF 控件</span><span class="sxs-lookup"><span data-stu-id="731cc-137">Selecting WPF Controls</span></span>  
 <span data-ttu-id="731cc-138">可将不同的 WPF 内容分配到 <xref:System.Windows.Forms.Integration.ElementHost> 控件，该控件现已承载内容。</span><span class="sxs-lookup"><span data-stu-id="731cc-138">You can assign different WPF content to an <xref:System.Windows.Forms.Integration.ElementHost> control, which is already hosting content.</span></span>  
  
#### <a name="to-select-wpf-controls"></a><span data-ttu-id="731cc-139">选择 WPF 控件</span><span class="sxs-lookup"><span data-stu-id="731cc-139">To select WPF controls</span></span>  
  
1. <span data-ttu-id="731cc-140">在 Windows 窗体设计器中打开 `Form1`。</span><span class="sxs-lookup"><span data-stu-id="731cc-140">Open `Form1` in the Windows Forms Designer.</span></span>  
  
2. <span data-ttu-id="731cc-141">在中**工具箱**，双击`UserControl1`若要创建的实例`UserControl1`窗体上。</span><span class="sxs-lookup"><span data-stu-id="731cc-141">In the **Toolbox**, double-click `UserControl1` to create an instance of `UserControl1` on the form.</span></span>  
  
     <span data-ttu-id="731cc-142">`UserControl1` 的实例托管在名为 `elementHost1` 的新 <xref:System.Windows.Forms.Integration.ElementHost> 控件中。</span><span class="sxs-lookup"><span data-stu-id="731cc-142">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
3. <span data-ttu-id="731cc-143">中的智能标记面板`elementHost1`，打开**选择承载的内容**下拉列表。</span><span class="sxs-lookup"><span data-stu-id="731cc-143">In the smart tag panel for `elementHost1`, open the **Select Hosted Content** drop-down list.</span></span>  
  
4. <span data-ttu-id="731cc-144">选择**UserControl2**从下拉列表框。</span><span class="sxs-lookup"><span data-stu-id="731cc-144">Select **UserControl2** from the drop-down list box.</span></span>  
  
     <span data-ttu-id="731cc-145">`elementHost1` 控件现承载 `UserControl2` 类型的实例。</span><span class="sxs-lookup"><span data-stu-id="731cc-145">The `elementHost1` control now hosts an instance of the `UserControl2` type.</span></span>  
  
5. <span data-ttu-id="731cc-146">在中**属性**窗口中，确认<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>属性设置为**UserControl2**。</span><span class="sxs-lookup"><span data-stu-id="731cc-146">In the **Properties** window, confirm that the <xref:System.Windows.Forms.Integration.ElementHost.Child%2A> property is set to **UserControl2**.</span></span>  
  
6. <span data-ttu-id="731cc-147">从**工具箱**，在**WPF 互操作性**组中，将<xref:System.Windows.Forms.Integration.ElementHost>拖到窗体控件。</span><span class="sxs-lookup"><span data-stu-id="731cc-147">From the **Toolbox**, in the **WPF Interoperability** group, drag an <xref:System.Windows.Forms.Integration.ElementHost> control onto the form.</span></span>  
  
     <span data-ttu-id="731cc-148">新控件的默认名称是 `elementHost2`。</span><span class="sxs-lookup"><span data-stu-id="731cc-148">The default name for the new control is `elementHost2`.</span></span>  
  
7. <span data-ttu-id="731cc-149">中的智能标记面板`elementHost2`，打开**选择承载的内容**下拉列表。</span><span class="sxs-lookup"><span data-stu-id="731cc-149">In the smart tag panel for `elementHost2`, open the **Select Hosted Content** drop-down list.</span></span>  
  
8. <span data-ttu-id="731cc-150">选择**UserControl1**从下拉列表。</span><span class="sxs-lookup"><span data-stu-id="731cc-150">Select **UserControl1** from the drop-down list.</span></span>  
  
9. <span data-ttu-id="731cc-151">`elementHost2` 控件现承载 `UserControl1` 类型的实例。</span><span class="sxs-lookup"><span data-stu-id="731cc-151">The `elementHost2` control now hosts an instance of the `UserControl1` type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="731cc-152">请参阅</span><span class="sxs-lookup"><span data-stu-id="731cc-152">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="731cc-153">迁移和互操作性</span><span class="sxs-lookup"><span data-stu-id="731cc-153">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="731cc-154">使用 WPF 控件</span><span class="sxs-lookup"><span data-stu-id="731cc-154">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="731cc-155">在 Visual Studio 中设计 XAML</span><span class="sxs-lookup"><span data-stu-id="731cc-155">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
