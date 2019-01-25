---
title: 如何：Windows 窗体的作者控件
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
ms.openlocfilehash: a6ea57dda8f034684e8590ce4c3b6d37ab01230e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579519"
---
# <a name="how-to-author-controls-for-windows-forms"></a><span data-ttu-id="6b7d8-102">如何：Windows 窗体的作者控件</span><span class="sxs-lookup"><span data-stu-id="6b7d8-102">How to: Author Controls for Windows Forms</span></span>
<span data-ttu-id="6b7d8-103">控件表示用户和程序之间的图形链接。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-103">A control represents a graphical link between the user and the program.</span></span> <span data-ttu-id="6b7d8-104">控件可以提供或处理数据、接受用户输入、响应事件或执行连接用户和应用程序的其他功能（任意数量）。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-104">A control can provide or process data, accept user input, respond to events, or perform any number of other functions that connect the user and the application.</span></span> <span data-ttu-id="6b7d8-105">因为控件本质上是具有图形界面的组件，所以它能提供组件所提供的所有功能并提供用户交互。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-105">Because a control is essentially a component with a graphical interface, it can serve any function that a component does, as well as provide user interaction.</span></span> <span data-ttu-id="6b7d8-106">控件是针对特定目的而创建的，而创作控件只是另一种编程任务。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-106">Controls are created to serve specific purposes, and authoring controls is just another programming task.</span></span> <span data-ttu-id="6b7d8-107">考虑到这一点，以下步骤概述了控件的创作过程。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-107">With that in mind, the following steps represent an overview of the control authoring process.</span></span> <span data-ttu-id="6b7d8-108">链接提供有关各个步骤的附加信息。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-108">Links provide additional information on the individual steps.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b7d8-109">如果想要创作在 Web 窗体上使用的自定义控件，请参阅[开发自定义 ASP.NET 服务器控件](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-109">If you want to author a custom control to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
>   
>  <span data-ttu-id="6b7d8-110">显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="6b7d8-111">若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="6b7d8-112">有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-112">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-author-a-control"></a><span data-ttu-id="6b7d8-113">创作控件</span><span class="sxs-lookup"><span data-stu-id="6b7d8-113">To author a control</span></span>  
  
1.  <span data-ttu-id="6b7d8-114">确定希望控件完成的操作或它在应用程序中所起的作用。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-114">Determine what you want your control to accomplish, or what part it will play in your application.</span></span> <span data-ttu-id="6b7d8-115">要考虑的因素有：</span><span class="sxs-lookup"><span data-stu-id="6b7d8-115">Factors to consider are:</span></span>  
  
    -   <span data-ttu-id="6b7d8-116">需要哪种图形界面？</span><span class="sxs-lookup"><span data-stu-id="6b7d8-116">What kind of graphical interface do you need?</span></span>  
  
    -   <span data-ttu-id="6b7d8-117">此控件会处理哪些特定用户交互？</span><span class="sxs-lookup"><span data-stu-id="6b7d8-117">What specific user interactions will this control handle?</span></span>  
  
    -   <span data-ttu-id="6b7d8-118">是否有现有控件提供所需功能？</span><span class="sxs-lookup"><span data-stu-id="6b7d8-118">Is the functionality you need provided by any existing controls?</span></span>  
  
    -   <span data-ttu-id="6b7d8-119">通过组合几个 Windows 窗体控件可以获得所需功能吗？</span><span class="sxs-lookup"><span data-stu-id="6b7d8-119">Can you get the functionality you need by combining several Windows Forms controls?</span></span>  
  
2.  <span data-ttu-id="6b7d8-120">如果控件需要一个对象模型，请确定如何在整个对象模型中分配功能，并在控件和任何子对象之间划分功能。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-120">If you need an object model for your control, determine how functionality will be distributed throughout the object model, and divide up functionality between the control and any subobjects.</span></span> <span data-ttu-id="6b7d8-121">如果打算创作一个复杂的控件，或者想要并入一些功能，则对象模型可能会有用。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-121">An object model may be useful if you are planning a complex control, or want to incorporate several functionalities.</span></span>  
  
3.  <span data-ttu-id="6b7d8-122">确定所需控件类型（例如，用户控件、自定义控件、继承的 Windows 窗体控件）。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-122">Determine the type of control (for example, user control, custom control, inherited Windows Forms control) you need.</span></span> <span data-ttu-id="6b7d8-123">有关详细信息，请参阅[控件类型建议](../../../../docs/framework/winforms/controls/control-type-recommendations.md)和[各种自定义控件](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-123">For details, see [Control Type Recommendations](../../../../docs/framework/winforms/controls/control-type-recommendations.md) and [Varieties of Custom Controls](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).</span></span>  
  
4.  <span data-ttu-id="6b7d8-124">将功能表示为控件及其子对象或子级结构的属性、方法和事件，并分配相应的访问级别（例如，公共、受保护等）。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-124">Express functionality as properties, methods, and events of the control and its subobjects or subsidiary structures, and assign appropriate access levels (for example, public, protected, and so on).</span></span>  
  
5.  <span data-ttu-id="6b7d8-125">如果需要为控件自定义绘制，请为其添加代码。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-125">If you need custom painting for your control, add code for it.</span></span> <span data-ttu-id="6b7d8-126">有关详细信息，请参阅[自定义控件的绘制和呈现](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md)。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-126">For details, see [Custom Control Painting and Rendering](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).</span></span>  
  
6.  <span data-ttu-id="6b7d8-127">如果控件继承自<xref:System.Windows.Forms.UserControl>，可以通过生成控件项目并运行测试其运行时行为**UserControl 测试容器**。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-127">If your control inherits from <xref:System.Windows.Forms.UserControl>, you can test its runtime behavior by building the control project and running it in the **UserControl Test Container**.</span></span> <span data-ttu-id="6b7d8-128">有关详细信息，请参阅[如何：测试 UserControl 的运行时行为](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-128">For more information, see [How to: Test the Run-Time Behavior of a UserControl](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>  
  
7.  <span data-ttu-id="6b7d8-129">还可以通过创建新项目（如 Windows 应用程序）并将其放入容器来测试和调试控件。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-129">You can also test and debug your control by creating a new project, such as a Windows Application, and placing it into a container.</span></span> <span data-ttu-id="6b7d8-130">此过程的一部分进行了演示[演练：创作复合控件使用 Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-130">This process is demonstrated as part of [Walkthrough: Authoring a Composite Control with Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md).</span></span>  
  
8.  <span data-ttu-id="6b7d8-131">添加每个功能时，将功能添加到测试项目以执行新功能。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-131">As you add each feature, add features to your test project to exercise the new functionality.</span></span>  
  
9. <span data-ttu-id="6b7d8-132">重复上述步骤，优化设计。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-132">Repeat, refining the design.</span></span>  
  
10. <span data-ttu-id="6b7d8-133">打包和部署控件。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-133">Package and deploy your control.</span></span> <span data-ttu-id="6b7d8-134">有关详细信息，请参阅[部署应用程序、服务和组件](https://msdn.microsoft.com/library/wtzawcsz)。</span><span class="sxs-lookup"><span data-stu-id="6b7d8-134">For details, see [Deploying Applications, Services, and Components](https://msdn.microsoft.com/library/wtzawcsz).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b7d8-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="6b7d8-135">See also</span></span>
- [<span data-ttu-id="6b7d8-136">演练：创作复合控件使用 Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6b7d8-136">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="6b7d8-137">演练：从使用 Visual Basic 的 Windows 窗体控件继承</span><span class="sxs-lookup"><span data-stu-id="6b7d8-137">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)
- [<span data-ttu-id="6b7d8-138">如何：从 UserControl 类继承</span><span class="sxs-lookup"><span data-stu-id="6b7d8-138">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="6b7d8-139">如何：从 Control 类继承</span><span class="sxs-lookup"><span data-stu-id="6b7d8-139">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="6b7d8-140">如何：从现有 Windows 窗体控件继承</span><span class="sxs-lookup"><span data-stu-id="6b7d8-140">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="6b7d8-141">如何：测试 UserControl 的运行时行为</span><span class="sxs-lookup"><span data-stu-id="6b7d8-141">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="6b7d8-142">各种自定义控件</span><span class="sxs-lookup"><span data-stu-id="6b7d8-142">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
