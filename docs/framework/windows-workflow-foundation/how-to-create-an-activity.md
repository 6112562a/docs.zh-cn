---
title: 如何：创建活动
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
ms.assetid: c09b1e99-21b5-4d96-9c04-ec31db3f4436
ms.openlocfilehash: 6d74af6af6cea0d65c33db67ecbfd71ac1d5c346
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636943"
---
# <a name="how-to-create-an-activity"></a><span data-ttu-id="11921-102">如何：创建活动</span><span class="sxs-lookup"><span data-stu-id="11921-102">How to: Create an Activity</span></span>

<span data-ttu-id="11921-103">活动是 [!INCLUDE[wf1](../../../includes/wf1-md.md)] 中的核心行为单元。</span><span class="sxs-lookup"><span data-stu-id="11921-103">Activities are the core unit of behavior in [!INCLUDE[wf1](../../../includes/wf1-md.md)].</span></span> <span data-ttu-id="11921-104">活动的执行逻辑可以使用托管代码实现，也可以使用其他活动实现。</span><span class="sxs-lookup"><span data-stu-id="11921-104">The execution logic of an activity can be implemented in managed code or it can be implemented by using other activities.</span></span> <span data-ttu-id="11921-105">本主题演示如何创建两个活动。</span><span class="sxs-lookup"><span data-stu-id="11921-105">This topic demonstrates how to create two activities.</span></span> <span data-ttu-id="11921-106">第一个活动是简单活动，它使用代码来实现其执行逻辑。</span><span class="sxs-lookup"><span data-stu-id="11921-106">The first activity is a simple activity that uses code to implement its execution logic.</span></span> <span data-ttu-id="11921-107">第二个活动的实现是用其他活动定义的。</span><span class="sxs-lookup"><span data-stu-id="11921-107">The implementation of the second activity is defined by using other activities.</span></span> <span data-ttu-id="11921-108">后续教程步骤会使用这些活动。</span><span class="sxs-lookup"><span data-stu-id="11921-108">These activities are used in following steps in the tutorial.</span></span>

> [!NOTE]
> <span data-ttu-id="11921-109">若要下载完整版教程，请参阅 [Windows Workflow Foundation (WF45) — 入门教程](https://go.microsoft.com/fwlink/?LinkID=248976)。</span><span class="sxs-lookup"><span data-stu-id="11921-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="create-the-activity-library-project"></a><span data-ttu-id="11921-110">创建活动库项目</span><span class="sxs-lookup"><span data-stu-id="11921-110">Create the activity library project</span></span>

1. <span data-ttu-id="11921-111">打开 Visual Studio，然后选择**新建** > **项目**从**文件**菜单。</span><span class="sxs-lookup"><span data-stu-id="11921-111">Open Visual Studio and choose **New** > **Project** from the **File** menu.</span></span>

2. <span data-ttu-id="11921-112">在中**新的项目**对话框下**已安装**类别中，选择**Visual C#** > **工作流**(或**Visual Basic** > **工作流**)。</span><span class="sxs-lookup"><span data-stu-id="11921-112">In the **New Project** dialog, under the **Installed** category, select **Visual C#** > **Workflow** (or **Visual Basic** > **Workflow**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="11921-113">如果没有看到**工作流**模板类别中，您可能需要安装**Windows Workflow Foundation**组件的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="11921-113">If you don't see the **Workflow** template category, you may need to install the **Windows Workflow Foundation** component of Visual Studio.</span></span> <span data-ttu-id="11921-114">选择**打开 Visual Studio 安装程序**上的左侧链接**新项目**对话框。</span><span class="sxs-lookup"><span data-stu-id="11921-114">Choose the **Open Visual Studio Installer** link on the left-hand side of the **New Project** dialog.</span></span> <span data-ttu-id="11921-115">在 Visual Studio 安装程序中，选择**各个组件**选项卡。然后，在**开发活动**类别中，选择**Windows Workflow Foundation**组件。</span><span class="sxs-lookup"><span data-stu-id="11921-115">In Visual Studio Installer, select the **Individual components** tab. Then, under the **Development activities** category, select the **Windows Workflow Foundation** component.</span></span> <span data-ttu-id="11921-116">选择**修改**要安装该组件。</span><span class="sxs-lookup"><span data-stu-id="11921-116">Choose **Modify** to install the component.</span></span>

3. <span data-ttu-id="11921-117">选择**活动库**项目模板。</span><span class="sxs-lookup"><span data-stu-id="11921-117">Select the **Activity Library** project template.</span></span> <span data-ttu-id="11921-118">类型`NumberGuessWorkflowActivities`中**名称**框，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="11921-118">Type `NumberGuessWorkflowActivities` in the **Name** box and then click **OK**.</span></span>

4. <span data-ttu-id="11921-119">右键单击**Activity1.xaml**中**解决方案资源管理器**，然后选择**删除**。</span><span class="sxs-lookup"><span data-stu-id="11921-119">Right-click **Activity1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="11921-120">单击 **“确定”** 以确认。</span><span class="sxs-lookup"><span data-stu-id="11921-120">Click **OK** to confirm.</span></span>

## <a name="create-the-readint-activity"></a><span data-ttu-id="11921-121">创建 ReadInt 活动</span><span class="sxs-lookup"><span data-stu-id="11921-121">Create the ReadInt activity</span></span>

1. <span data-ttu-id="11921-122">选择**添加新项**从**项目**菜单。</span><span class="sxs-lookup"><span data-stu-id="11921-122">Choose **Add New Item** from the **Project** menu.</span></span>

2. <span data-ttu-id="11921-123">在中**已安装** > **常见项**节点中，选择**工作流**。</span><span class="sxs-lookup"><span data-stu-id="11921-123">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="11921-124">选择**代码活动**从**工作流**列表。</span><span class="sxs-lookup"><span data-stu-id="11921-124">Select **Code Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="11921-125">类型`ReadInt`成**名称**框，然后单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="11921-125">Type `ReadInt` into the **Name** box and then click **Add**.</span></span>

4. <span data-ttu-id="11921-126">将现有的 `ReadInt` 定义替换为下面的定义。</span><span class="sxs-lookup"><span data-stu-id="11921-126">Replace the existing `ReadInt` definition with the following definition.</span></span>

     [!code-csharp[CFX_WF_GettingStarted#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/readint.cs#1)]
     [!code-vb[CFX_WF_GettingStarted#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/readint.vb#1)]

    > [!NOTE]
    > <span data-ttu-id="11921-127">`ReadInt` 活动派生自 <xref:System.Activities.NativeActivity%601> 而不是 <xref:System.Activities.CodeActivity>，这是默认的代码活动模板。</span><span class="sxs-lookup"><span data-stu-id="11921-127">The `ReadInt` activity derives from <xref:System.Activities.NativeActivity%601> instead of <xref:System.Activities.CodeActivity>, which is the default for the code activity template.</span></span> <span data-ttu-id="11921-128">如果活动提供单个结果，可以使用 <xref:System.Activities.CodeActivity%601>，它是通过 <xref:System.Activities.Activity%601.Result%2A> 自变量公开的，但是 <xref:System.Activities.CodeActivity%601> 不支持使用书签，因此使用 <xref:System.Activities.NativeActivity%601>。</span><span class="sxs-lookup"><span data-stu-id="11921-128"><xref:System.Activities.CodeActivity%601> can be used if the activity provides a single result, which is exposed through the <xref:System.Activities.Activity%601.Result%2A> argument, but <xref:System.Activities.CodeActivity%601> does not support the use of bookmarks, so <xref:System.Activities.NativeActivity%601> is used.</span></span>

## <a name="create-the-prompt-activity"></a><span data-ttu-id="11921-129">创建 Prompt 活动</span><span class="sxs-lookup"><span data-stu-id="11921-129">Create the Prompt activity</span></span>

1. <span data-ttu-id="11921-130">按**Ctrl**+**Shift**+**B**以生成项目。</span><span class="sxs-lookup"><span data-stu-id="11921-130">Press **Ctrl**+**Shift**+**B** to build the project.</span></span> <span data-ttu-id="11921-131">通过生成项目，可以使用此项目中的 `ReadInt` 活动生成此步骤中的自定义活动。</span><span class="sxs-lookup"><span data-stu-id="11921-131">Building the project enables the `ReadInt` activity in this project to be used to build the custom activity from this step.</span></span>

2. <span data-ttu-id="11921-132">选择**添加新项**从**项目**菜单。</span><span class="sxs-lookup"><span data-stu-id="11921-132">Choose **Add New Item** from the **Project** menu.</span></span>

3. <span data-ttu-id="11921-133">在中**已安装** > **常见项**节点中，选择**工作流**。</span><span class="sxs-lookup"><span data-stu-id="11921-133">In the **Installed** > **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="11921-134">选择**活动**从**工作流**列表。</span><span class="sxs-lookup"><span data-stu-id="11921-134">Select **Activity** from the **Workflow** list.</span></span>

4. <span data-ttu-id="11921-135">类型`Prompt`成**名称**框，然后单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="11921-135">Type `Prompt` into the **Name** box and then click **Add**.</span></span>

5. <span data-ttu-id="11921-136">双击**Prompt.xaml**中**解决方案资源管理器**如果未显示设计器中显示它。</span><span class="sxs-lookup"><span data-stu-id="11921-136">Double-click **Prompt.xaml** in **Solution Explorer** to display it in the designer if it is not already displayed.</span></span>

6. <span data-ttu-id="11921-137">单击**自变量**中显示的活动设计器左下方**自变量**窗格。</span><span class="sxs-lookup"><span data-stu-id="11921-137">Click **Arguments** in the lower-left side of the activity designer to display the **Arguments** pane.</span></span>

7. <span data-ttu-id="11921-138">单击**创建参数**。</span><span class="sxs-lookup"><span data-stu-id="11921-138">Click **Create Argument**.</span></span>

8. <span data-ttu-id="11921-139">类型`BookmarkName`成**名称**框中，选择**中**从**方向**下拉列表中，选择**字符串**从**自变量类型**下拉列表，再按**Enter**保存该自变量。</span><span class="sxs-lookup"><span data-stu-id="11921-139">Type `BookmarkName` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

9. <span data-ttu-id="11921-140">单击**创建参数**。</span><span class="sxs-lookup"><span data-stu-id="11921-140">Click **Create Argument**.</span></span>

10. <span data-ttu-id="11921-141">类型`Result`成**名称**下新添加的框`BookmarkName`参数中，选择**Out**从**方向**下拉列表中，选择**Int32**从**自变量类型**下拉列表，然后按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="11921-141">Type `Result` into the **Name** box that is underneath the newly added `BookmarkName` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press **Enter**.</span></span>

11. <span data-ttu-id="11921-142">单击**创建参数**。</span><span class="sxs-lookup"><span data-stu-id="11921-142">Click **Create Argument**.</span></span>

12. <span data-ttu-id="11921-143">类型`Text`成**名称**框中，选择**中**从**方向**下拉列表中，选择**字符串**从**自变量类型**下拉列表，再按**Enter**保存该自变量。</span><span class="sxs-lookup"><span data-stu-id="11921-143">Type `Text` into the **Name** box, select **In** from the **Direction** drop-down list, select **String** from the **Argument type** drop-down list, and then press **Enter** to save the argument.</span></span>

     <span data-ttu-id="11921-144">在以下步骤中，这三个参数将绑定到添加到 <xref:System.Activities.Statements.WriteLine> 活动中的 `ReadInt` 和 `Prompt` 活动的相应参数。</span><span class="sxs-lookup"><span data-stu-id="11921-144">These three arguments are bound to the corresponding arguments of the <xref:System.Activities.Statements.WriteLine> and `ReadInt` activities that are added to the `Prompt` activity in the following steps.</span></span>

13. <span data-ttu-id="11921-145">单击**自变量**左下角的活动设计器，以关闭**自变量**窗格。</span><span class="sxs-lookup"><span data-stu-id="11921-145">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

14. <span data-ttu-id="11921-146">拖动**序列**活动从**控制流**一部分**工具箱**放到**在此处放置活动**的标签**提示**活动设计器。</span><span class="sxs-lookup"><span data-stu-id="11921-146">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Prompt** activity designer.</span></span>

    > [!TIP]
    > <span data-ttu-id="11921-147">如果**工具箱**不显示窗口中，选择**工具箱**从**视图**菜单。</span><span class="sxs-lookup"><span data-stu-id="11921-147">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

15. <span data-ttu-id="11921-148">拖动**WriteLine**活动从**基元**一部分**工具箱**放到**在此处放置活动**的标签**序列**活动。</span><span class="sxs-lookup"><span data-stu-id="11921-148">Drag a **WriteLine** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Drop activity here** label of the **Sequence** activity.</span></span>

16. <span data-ttu-id="11921-149">将绑定**文本**的参数**WriteLine**活动**文本**自变量的**提示**活动通过键入`Text`到**输入 C# 表达式**或**输入 VB 表达式**框中**属性**窗口中，然后再按**选项卡**键两次。</span><span class="sxs-lookup"><span data-stu-id="11921-149">Bind the **Text** argument of the **WriteLine** activity to the **Text** argument of the **Prompt** activity by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box in the **Properties** window, and then press the **Tab** key two times.</span></span> <span data-ttu-id="11921-150">这会关闭 IntelliSense 列表成员窗口，并通过将选择范围移离属性保存属性值。</span><span class="sxs-lookup"><span data-stu-id="11921-150">This dismisses the IntelliSense list members window and saves the property value by moving the selection off the property.</span></span> <span data-ttu-id="11921-151">此外可以通过键入来设置此属性`Text`成**输入 C# 表达式**或**输入 VB 表达式**在活动本身上的框。</span><span class="sxs-lookup"><span data-stu-id="11921-151">This property can also be set by typing `Text` into the **Enter a C# expression** or **Enter a VB expression** box on the activity itself.</span></span>

    > [!TIP]
    > <span data-ttu-id="11921-152">如果**属性窗口**未显示，选择**属性窗口**从**视图**菜单。</span><span class="sxs-lookup"><span data-stu-id="11921-152">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

17. <span data-ttu-id="11921-153">拖动**ReadInt**活动从**NumberGuessWorkflowActivities**一部分**工具箱**并将其放置**序列**活动中，以便它**WriteLine**活动。</span><span class="sxs-lookup"><span data-stu-id="11921-153">Drag a **ReadInt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the **WriteLine** activity.</span></span>

18. <span data-ttu-id="11921-154">将绑定**BookmarkName**的参数**ReadInt**活动**BookmarkName**自变量的**提示**通过键入活动`BookmarkName`成**输入 VB 表达式**右侧的框中**BookmarkName**中的参数**属性窗口**，然后按**选项卡**键两次以关闭 IntelliSense 列表成员窗口，然后保存该属性。</span><span class="sxs-lookup"><span data-stu-id="11921-154">Bind the **BookmarkName** argument of the **ReadInt** activity to the **BookmarkName** argument of the **Prompt** activity by typing `BookmarkName` into the **Enter a VB expression** box to the right of the **BookmarkName** argument in the **Properties Window**, and then press the **Tab** key two times to close the IntelliSense list members window and save the property.</span></span>

19. <span data-ttu-id="11921-155">将绑定**结果**的参数**ReadInt**活动**结果**自变量的**提示**活动通过键入`Result`到**输入 VB 表达式**右侧的框中**结果**中的参数**属性窗口**，然后按**选项卡**键两次。</span><span class="sxs-lookup"><span data-stu-id="11921-155">Bind the **Result** argument of the **ReadInt** activity to the **Result** argument of the **Prompt** activity by typing `Result` into the **Enter a VB expression** box to the right of the **Result** argument in the **Properties Window**, and then press the **Tab** key two times.</span></span>

20. <span data-ttu-id="11921-156">按**Ctrl**+**Shift**+**B**以生成解决方案。</span><span class="sxs-lookup"><span data-stu-id="11921-156">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

## <a name="next-steps"></a><span data-ttu-id="11921-157">后续步骤</span><span class="sxs-lookup"><span data-stu-id="11921-157">Next steps</span></span>

<span data-ttu-id="11921-158">有关说明如何使用这些活动创建工作流教程中，请参阅下一步[如何：创建工作流](how-to-create-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="11921-158">For instructions on how to create a workflow by using these activities, see the next step in the tutorial, [How to: Create a Workflow](how-to-create-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11921-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="11921-159">See also</span></span>

- <xref:System.Activities.CodeActivity>
- <xref:System.Activities.NativeActivity%601>
- [<span data-ttu-id="11921-160">设计和实现自定义活动</span><span class="sxs-lookup"><span data-stu-id="11921-160">Designing and Implementing Custom Activities</span></span>](designing-and-implementing-custom-activities.md)
- [<span data-ttu-id="11921-161">入门教程</span><span class="sxs-lookup"><span data-stu-id="11921-161">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="11921-162">如何：创建工作流</span><span class="sxs-lookup"><span data-stu-id="11921-162">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)
- [<span data-ttu-id="11921-163">在自定义活动设计器中使用 ExpressionTextBox</span><span class="sxs-lookup"><span data-stu-id="11921-163">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
