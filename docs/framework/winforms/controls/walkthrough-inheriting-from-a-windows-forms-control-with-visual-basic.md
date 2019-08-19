---
title: 演练：使用 Visual Basic 从 Windows 窗体控件继承
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: 0891b64fdb26953ab90f3da931f04513ac9e8bcf
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040216"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a><span data-ttu-id="20faa-102">演练：使用 Visual Basic 从 Windows 窗体控件继承</span><span class="sxs-lookup"><span data-stu-id="20faa-102">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>
<span data-ttu-id="20faa-103">使用 Visual Basic, 可以通过*继承*来创建功能强大的自定义控件。</span><span class="sxs-lookup"><span data-stu-id="20faa-103">With Visual Basic, you can create powerful custom controls through *inheritance*.</span></span> <span data-ttu-id="20faa-104">通过继承，可以创建不仅保留了标准 Windows 窗体控件的所有固有功能，而且还包含自定义功能的控件。</span><span class="sxs-lookup"><span data-stu-id="20faa-104">Through inheritance you are able to create controls that retain all of the inherent functionality of standard Windows Forms controls but also incorporate custom functionality.</span></span> <span data-ttu-id="20faa-105">在本演练中，将创建一个名为 `ValueButton` 的简单继承控件。</span><span class="sxs-lookup"><span data-stu-id="20faa-105">In this walkthrough, you will create a simple inherited control called `ValueButton`.</span></span> <span data-ttu-id="20faa-106">此按钮将从标准 Windows 窗体<xref:System.Windows.Forms.Button>控件继承功能, 并将公开一个名`ButtonValue`为的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="20faa-106">This button will inherit functionality from the standard Windows Forms <xref:System.Windows.Forms.Button> control, and will expose a custom property called `ButtonValue`.</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="20faa-107">创建项目</span><span class="sxs-lookup"><span data-stu-id="20faa-107">Creating the Project</span></span>
 <span data-ttu-id="20faa-108">创建新的项目时应指定其名称，以设置根命名空间、程序集名称和项目名称，并确保默认组件将位于正确的命名空间中。</span><span class="sxs-lookup"><span data-stu-id="20faa-108">When you create a new project, you specify its name in order to set the root namespace, assembly name, and project name, and to ensure that the default component will be in the correct namespace.</span></span>

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a><span data-ttu-id="20faa-109">创建 ValueButtonLib 控件库和 ValueButton 控件</span><span class="sxs-lookup"><span data-stu-id="20faa-109">To create the ValueButtonLib control library and the ValueButton control</span></span>

1. <span data-ttu-id="20faa-110">在“文件”菜单上指向“新建”，然后单击“项目”打开“新建项目”对话框。</span><span class="sxs-lookup"><span data-stu-id="20faa-110">On the **File** menu, point to **New** and then click **Project** to open the **New Project** dialog box.</span></span>

2. <span data-ttu-id="20faa-111">从 Visual Basic 项目的列表中选择 " **Windows 窗体控件库**项目模板", 然后`ValueButtonLib`在 "**名称**" 框中键入。</span><span class="sxs-lookup"><span data-stu-id="20faa-111">Select the **Windows Forms Control Library** project template from the list of Visual Basic projects, and type `ValueButtonLib` in the **Name** box.</span></span>

     <span data-ttu-id="20faa-112">默认情况下，项目名称 `ValueButtonLib` 也会分配到根命名空间中。</span><span class="sxs-lookup"><span data-stu-id="20faa-112">The project name, `ValueButtonLib`, is also assigned to the root namespace by default.</span></span> <span data-ttu-id="20faa-113">根命名空间用于限定程序集中的组件名。</span><span class="sxs-lookup"><span data-stu-id="20faa-113">The root namespace is used to qualify the names of components in the assembly.</span></span> <span data-ttu-id="20faa-114">例如，如果两个程序集都提供名为 `ValueButton` 的组件，则可以使用 `ValueButtonLib.ValueButton` 指定 `ValueButton` 组件。</span><span class="sxs-lookup"><span data-stu-id="20faa-114">For example, if two assemblies provide components named `ValueButton`, you can specify your `ValueButton` component using `ValueButtonLib.ValueButton`.</span></span> <span data-ttu-id="20faa-115">有关详细信息，请参阅 [Visual Basic 中的命名空间](~/docs/visual-basic/programming-guide/program-structure/namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="20faa-115">For more information, see [Namespaces in Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).</span></span>

3. <span data-ttu-id="20faa-116">在“解决方案资源管理器”中，右键单击“UserControl1.vb”，然后从快捷菜单中选择“重命名”。</span><span class="sxs-lookup"><span data-stu-id="20faa-116">In **Solution Explorer**, right-click **UserControl1.vb**, then choose **Rename** from the shortcut menu.</span></span> <span data-ttu-id="20faa-117">将文件名更改为 `ValueButton.vb`。</span><span class="sxs-lookup"><span data-stu-id="20faa-117">Change the file name to `ValueButton.vb`.</span></span> <span data-ttu-id="20faa-118">当系统询问是否重命名对代码元素“UserControl1”的所有引用时，单击“是”按钮。</span><span class="sxs-lookup"><span data-stu-id="20faa-118">Click the **Yes** button when you are asked if you want to rename all references to the code element 'UserControl1'.</span></span>

4. <span data-ttu-id="20faa-119">在“解决方案资源管理器”中，单击“显示所有文件”按钮。</span><span class="sxs-lookup"><span data-stu-id="20faa-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>

5. <span data-ttu-id="20faa-120">打开“ValueButton.vb”节点显示设计器生成的代码文件 **ValueButton.Designer.vb**。</span><span class="sxs-lookup"><span data-stu-id="20faa-120">Open the **ValueButton.vb** node to display the designer-generated code file, **ValueButton.Designer.vb**.</span></span> <span data-ttu-id="20faa-121">在“代码编辑器”中打开此文件。</span><span class="sxs-lookup"><span data-stu-id="20faa-121">Open this file in the **Code Editor**.</span></span>

6. <span data-ttu-id="20faa-122">找到语句, `Partial Public Class ValueButton`并将此控件继承<xref:System.Windows.Forms.UserControl>的类型从更改为<xref:System.Windows.Forms.Button>。 `Class`</span><span class="sxs-lookup"><span data-stu-id="20faa-122">Locate the `Class` statement, `Partial Public Class ValueButton`, and change the type from which this control inherits from <xref:System.Windows.Forms.UserControl> to <xref:System.Windows.Forms.Button>.</span></span> <span data-ttu-id="20faa-123">这允许继承的控件继承<xref:System.Windows.Forms.Button>控件的所有功能。</span><span class="sxs-lookup"><span data-stu-id="20faa-123">This allows your inherited control to inherit all the functionality of the <xref:System.Windows.Forms.Button> control.</span></span>

7. <span data-ttu-id="20faa-124">找到方法并删除<xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>分配属性的行。 `InitializeComponent`</span><span class="sxs-lookup"><span data-stu-id="20faa-124">Locate the `InitializeComponent` method and remove the line that assigns the <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> property.</span></span> <span data-ttu-id="20faa-125">此属性在<xref:System.Windows.Forms.Button>控件中不存在。</span><span class="sxs-lookup"><span data-stu-id="20faa-125">This property does not exist in the <xref:System.Windows.Forms.Button> control.</span></span>

8. <span data-ttu-id="20faa-126">在“文件”菜单中，选择“全部保存”以保存项目。</span><span class="sxs-lookup"><span data-stu-id="20faa-126">From the **File** menu, choose **Save All** to save the project.</span></span>

     <span data-ttu-id="20faa-127">请注意，可视化设计器不再可用。</span><span class="sxs-lookup"><span data-stu-id="20faa-127">Note that a visual designer is no longer available.</span></span> <span data-ttu-id="20faa-128"><xref:System.Windows.Forms.Button>由于控件执行其自己的绘制, 因此无法在设计器中修改其外观。</span><span class="sxs-lookup"><span data-stu-id="20faa-128">Because the <xref:System.Windows.Forms.Button> control does its own painting, you are unable to modify its appearance in the designer.</span></span> <span data-ttu-id="20faa-129">它的可视化表示形式将与它继承自的类 (即<xref:System.Windows.Forms.Button>) 的可视化表示形式完全相同, 除非在代码中进行了修改。</span><span class="sxs-lookup"><span data-stu-id="20faa-129">Its visual representation will be exactly the same as that of the class it inherits from (that is, <xref:System.Windows.Forms.Button>) unless modified in the code.</span></span>

> [!NOTE]
>  <span data-ttu-id="20faa-130">但仍然可以向设计器图面添加不含 UI 元素的组件。</span><span class="sxs-lookup"><span data-stu-id="20faa-130">You can still add components, which have no UI elements, to the design surface.</span></span>

## <a name="adding-a-property-to-your-inherited-control"></a><span data-ttu-id="20faa-131">将属性添加到继承控件</span><span class="sxs-lookup"><span data-stu-id="20faa-131">Adding a Property to Your Inherited Control</span></span>
 <span data-ttu-id="20faa-132">继承的 Windows 窗体控件的可能用途之一是创建与标准 Windows 窗体控件的外观和行为相同、但公开自定义属性的控件。</span><span class="sxs-lookup"><span data-stu-id="20faa-132">One possible use of inherited Windows Forms controls is the creation of controls that are identical in appearance and behavior (look and feel) to standard Windows Forms controls, but expose custom properties.</span></span> <span data-ttu-id="20faa-133">在本节中，将向控件中添加名为 `ButtonValue` 的属性。</span><span class="sxs-lookup"><span data-stu-id="20faa-133">In this section, you will add a property called `ButtonValue` to your control.</span></span>

### <a name="to-add-the-value-property"></a><span data-ttu-id="20faa-134">添加 Value 属性</span><span class="sxs-lookup"><span data-stu-id="20faa-134">To add the Value property</span></span>

1. <span data-ttu-id="20faa-135">在“解决方案资源管理器”中，右键单击“ValueButton.vb”，然后从快捷菜单中单击“查看代码”。</span><span class="sxs-lookup"><span data-stu-id="20faa-135">In **Solution Explorer**, right-click **ValueButton.vb**, and then click **View Code** from the shortcut menu.</span></span>

2. <span data-ttu-id="20faa-136">找到 `Public Class ValueButton` 语句。</span><span class="sxs-lookup"><span data-stu-id="20faa-136">Locate the `Public Class ValueButton` statement.</span></span> <span data-ttu-id="20faa-137">在紧靠该语句下方键入以下代码：</span><span class="sxs-lookup"><span data-stu-id="20faa-137">Immediately beneath this statement, type the following code:</span></span>

    ```vb
    ' Creates the private variable that will store the value of your
    ' property.
    Private varValue as integer
    ' Declares the property.
    Property ButtonValue() as Integer
    ' Sets the method for retrieving the value of your property.
       Get
          Return varValue
       End Get
    ' Sets the method for setting the value of your property.
       Set(ByVal Value as Integer)
          varValue = Value
       End Set
    End Property
    ```

     <span data-ttu-id="20faa-138">此代码设置存储和检索 `ButtonValue` 属性的方法。</span><span class="sxs-lookup"><span data-stu-id="20faa-138">This code sets the methods by which the `ButtonValue` property is stored and retrieved.</span></span> <span data-ttu-id="20faa-139">          `Get` 语句将返回的值设置为存储在私有变量 `varValue` 中的值，而 `Set` 语句通过使用 `Value` 关键字设置该私有变量的值。</span><span class="sxs-lookup"><span data-stu-id="20faa-139">The `Get` statement sets the value returned to the value that is stored in the private variable `varValue`, and the `Set` statement sets the value of the private variable by use of the `Value` keyword.</span></span>

3. <span data-ttu-id="20faa-140">在“文件”菜单中，选择“全部保存”以保存项目。</span><span class="sxs-lookup"><span data-stu-id="20faa-140">From the **File** menu, choose **Save All** to save the project.</span></span>

## <a name="testing-your-control"></a><span data-ttu-id="20faa-141">测试控件</span><span class="sxs-lookup"><span data-stu-id="20faa-141">Testing Your Control</span></span>
 <span data-ttu-id="20faa-142">控件不是独立的项目，它们必须托管在容器中。</span><span class="sxs-lookup"><span data-stu-id="20faa-142">Controls are not stand-alone projects; they must be hosted in a container.</span></span> <span data-ttu-id="20faa-143">若要测试控件，必须提供一个测试项目，以使控件在其中运行。</span><span class="sxs-lookup"><span data-stu-id="20faa-143">In order to test your control, you must provide a test project for it to run in.</span></span> <span data-ttu-id="20faa-144">还必须通过生成（编译）该控件使测试项目能够访问它。</span><span class="sxs-lookup"><span data-stu-id="20faa-144">You must also make your control accessible to the test project by building (compiling) it.</span></span> <span data-ttu-id="20faa-145">在本节中，将生成控件并在 Windows 窗体中对其进行测试。</span><span class="sxs-lookup"><span data-stu-id="20faa-145">In this section, you will build your control and test it in a Windows Form.</span></span>

### <a name="to-build-your-control"></a><span data-ttu-id="20faa-146">生成控件</span><span class="sxs-lookup"><span data-stu-id="20faa-146">To build your control</span></span>

1. <span data-ttu-id="20faa-147">在 **“生成”** 菜单上，单击 **“生成解决方案”** 。</span><span class="sxs-lookup"><span data-stu-id="20faa-147">On the **Build** menu, click **Build Solution**.</span></span>

     <span data-ttu-id="20faa-148">生成应会成功，且没有任何编译器错误或警告。</span><span class="sxs-lookup"><span data-stu-id="20faa-148">The build should be successful with no compiler errors or warnings.</span></span>

### <a name="to-create-a-test-project"></a><span data-ttu-id="20faa-149">创建测试项目</span><span class="sxs-lookup"><span data-stu-id="20faa-149">To create a test project</span></span>

1. <span data-ttu-id="20faa-150">在“文件”菜单上，指向“添加”，然后单击“新建项目”打开“添加新项目”对话框。</span><span class="sxs-lookup"><span data-stu-id="20faa-150">On the **File** menu, point to **Add** and then click **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="20faa-151">选择 "Visual Basic 项目" 节点, 然后单击 " **Windows 窗体应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="20faa-151">Select the Visual Basic projects node, and click **Windows Forms Application**.</span></span>

3. <span data-ttu-id="20faa-152">在“名称”框中键入 `Test`。</span><span class="sxs-lookup"><span data-stu-id="20faa-152">In the **Name** box, type `Test`.</span></span>

4. <span data-ttu-id="20faa-153">在“解决方案资源管理器”中，单击“显示所有文件”按钮。</span><span class="sxs-lookup"><span data-stu-id="20faa-153">In **Solution Explorer**, click the **Show All Files** button.</span></span>

5. <span data-ttu-id="20faa-154">在“解决方案资源管理器”中，右键单击测试项目的“引用”节点，然后从快捷菜单上选择“添加引用”以显示“添加引用”对话框。</span><span class="sxs-lookup"><span data-stu-id="20faa-154">In **Solution Explorer**, right-click the **References** node for your test project, then select **Add Reference** from the shortcut menu to display the **Add Reference** dialog box.</span></span>

6. <span data-ttu-id="20faa-155">单击“项目”选项卡。</span><span class="sxs-lookup"><span data-stu-id="20faa-155">Click the **Projects** tab.</span></span>

7. <span data-ttu-id="20faa-156">单击标记为“项目”的选项卡。</span><span class="sxs-lookup"><span data-stu-id="20faa-156">Click the tab labeled **Projects**.</span></span> <span data-ttu-id="20faa-157">“项目名称”下将列出 `ValueButtonLib` 项目。</span><span class="sxs-lookup"><span data-stu-id="20faa-157">Your `ValueButtonLib` project will be listed under **Project Name**.</span></span> <span data-ttu-id="20faa-158">双击该项目将引用添加到测试项目。</span><span class="sxs-lookup"><span data-stu-id="20faa-158">Double-click the project to add the reference to the test project.</span></span>

8. <span data-ttu-id="20faa-159">在“解决方案资源管理器”中，右键单击“测试”，然后选择“生成”。</span><span class="sxs-lookup"><span data-stu-id="20faa-159">In **Solution Explorer,** right-click **Test** and select **Build**.</span></span>

### <a name="to-add-your-control-to-the-form"></a><span data-ttu-id="20faa-160">将控件添加到窗体</span><span class="sxs-lookup"><span data-stu-id="20faa-160">To add your control to the form</span></span>

1. <span data-ttu-id="20faa-161">在“解决方案资源管理器”中，右键单击“Form1.vb”，然后从快捷菜单中选择“视图设计器”。</span><span class="sxs-lookup"><span data-stu-id="20faa-161">In **Solution Explorer**, right-click **Form1.vb** and choose **View Designer** from the shortcut menu.</span></span>

2. <span data-ttu-id="20faa-162">在“工具箱”中单击“ValueButtonLib 组件”。</span><span class="sxs-lookup"><span data-stu-id="20faa-162">In the **Toolbox**, click **ValueButtonLib Components**.</span></span> <span data-ttu-id="20faa-163">双击“ValueButton”。</span><span class="sxs-lookup"><span data-stu-id="20faa-163">Double-click **ValueButton**.</span></span>

     <span data-ttu-id="20faa-164">窗体上将出现“ValueButton”。</span><span class="sxs-lookup"><span data-stu-id="20faa-164">A **ValueButton** appears on the form.</span></span>

3. <span data-ttu-id="20faa-165">右键单击“ValueButton”，并从快捷菜单中选择“属性”。</span><span class="sxs-lookup"><span data-stu-id="20faa-165">Right-click the **ValueButton** and select **Properties** from the shortcut menu.</span></span>

4. <span data-ttu-id="20faa-166">在“属性”窗口中，检查该控件的属性。</span><span class="sxs-lookup"><span data-stu-id="20faa-166">In the **Properties** window, examine the properties of this control.</span></span> <span data-ttu-id="20faa-167">请注意，除增加了一个 `ButtonValue` 属性外，它们与标准按钮公开的属性相同。</span><span class="sxs-lookup"><span data-stu-id="20faa-167">Note that they are identical to the properties exposed by a standard button, except that there is an additional property, `ButtonValue`.</span></span>

5. <span data-ttu-id="20faa-168">将 `ButtonValue` 属性设置为 `5`。</span><span class="sxs-lookup"><span data-stu-id="20faa-168">Set the `ButtonValue` property to `5`.</span></span>

6. <span data-ttu-id="20faa-169">在 "**工具箱**" 的 "**所有 Windows 窗体**" 选项卡上 , 双击 " <xref:System.Windows.Forms.Label>标签" 将控件添加到窗体。</span><span class="sxs-lookup"><span data-stu-id="20faa-169">On the **All Windows Forms** tab of the **Toolbox**, double-click **Label** to add a <xref:System.Windows.Forms.Label> control to your form.</span></span>

7. <span data-ttu-id="20faa-170">将标签重新定位到窗体的中央。</span><span class="sxs-lookup"><span data-stu-id="20faa-170">Relocate the label to the center of the form.</span></span>

8. <span data-ttu-id="20faa-171">双击 `ValueButton1`。</span><span class="sxs-lookup"><span data-stu-id="20faa-171">Double-click `ValueButton1`.</span></span>

     <span data-ttu-id="20faa-172">“代码编辑器”随即打开并显示 `ValueButton1_Click` 事件。</span><span class="sxs-lookup"><span data-stu-id="20faa-172">The **Code Editor** opens to the `ValueButton1_Click` event.</span></span>

9. <span data-ttu-id="20faa-173">键入以下代码行。</span><span class="sxs-lookup"><span data-stu-id="20faa-173">Type the following line of code.</span></span>

    ```vb
    Label1.Text = CStr(ValueButton1.ButtonValue)
    ```

10. <span data-ttu-id="20faa-174">在“解决方案资源管理器”中，右键单击“测试”，然后从快捷菜单中选择“设为启动项目”。</span><span class="sxs-lookup"><span data-stu-id="20faa-174">In **Solution Explorer**, right-click **Test**, and choose **Set as Startup Project** from the shortcut menu.</span></span>

11. <span data-ttu-id="20faa-175">从“调试”菜单中选择“启动调试”。</span><span class="sxs-lookup"><span data-stu-id="20faa-175">From the **Debug** menu, select **Start Debugging**.</span></span>

     <span data-ttu-id="20faa-176">`Form1` 将出现。</span><span class="sxs-lookup"><span data-stu-id="20faa-176">`Form1` appears.</span></span>

12. <span data-ttu-id="20faa-177">单击 `Valuebutton1`。</span><span class="sxs-lookup"><span data-stu-id="20faa-177">Click `Valuebutton1`.</span></span>

     <span data-ttu-id="20faa-178">          `Label1` 中显示数字“5”，表明继承的控件的 `ButtonValue` 属性已通过 `ValueButton1_Click` 方法传递给 `Label1`。</span><span class="sxs-lookup"><span data-stu-id="20faa-178">The numeral '5' is displayed in `Label1`, demonstrating that the `ButtonValue` property of your inherited control has been passed to `Label1` through the `ValueButton1_Click` method.</span></span> <span data-ttu-id="20faa-179">这样，`ValueButton` 控件便继承了标准 Windows 窗体按钮的所有功能，但是公开了一个附加的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="20faa-179">Thus your `ValueButton` control inherits all the functionality of the standard Windows Forms button, but exposes an additional, custom property.</span></span>

## <a name="see-also"></a><span data-ttu-id="20faa-180">请参阅</span><span class="sxs-lookup"><span data-stu-id="20faa-180">See also</span></span>

- [<span data-ttu-id="20faa-181">演练：使用 Visual Basic 创作复合控件</span><span class="sxs-lookup"><span data-stu-id="20faa-181">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [<span data-ttu-id="20faa-182">如何：在 "选择工具箱项" 对话框中显示控件</span><span class="sxs-lookup"><span data-stu-id="20faa-182">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [<span data-ttu-id="20faa-183">使用 .NET Framework 开发自定义 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="20faa-183">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="20faa-184">继承的基础知识 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20faa-184">Inheritance basics (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
