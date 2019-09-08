---
title: 演练：仅使用存储过程 (C#)
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: f980402c976db9ee327a7b726e36a0a4d9d6d73f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792110"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="ead7b-102">演练：仅使用存储过程 (C#)</span><span class="sxs-lookup"><span data-stu-id="ead7b-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>

<span data-ttu-id="ead7b-103">本演练提供了通过仅执行存储过程来访问数据的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 基本端对端方案。</span><span class="sxs-lookup"><span data-stu-id="ead7b-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="ead7b-104">数据库管理员经常使用此方法来限制数据存储的访问方式。</span><span class="sxs-lookup"><span data-stu-id="ead7b-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>

> [!NOTE]
> <span data-ttu-id="ead7b-105">您还可以在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 应用程序中使用存储过程来重写默认行为，尤其是 `Create`、`Update` 和 `Delete` 进程的默认行为。</span><span class="sxs-lookup"><span data-stu-id="ead7b-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="ead7b-106">有关详细信息，请参阅[自定义插入、更新和删除操作](customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="ead7b-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>

<span data-ttu-id="ead7b-107">出于本演练的目的，您将使用已映射到 Northwind 示例数据库中的存储过程的两个方法：CustOrdersDetail 和 CustOrderHist。</span><span class="sxs-lookup"><span data-stu-id="ead7b-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="ead7b-108">此映射发生在运行 SqlMetal 命令行工具来生成 C# 文件时。</span><span class="sxs-lookup"><span data-stu-id="ead7b-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="ead7b-109">有关更多信息，请参见本演练后面的“先决条件”一节。</span><span class="sxs-lookup"><span data-stu-id="ead7b-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>

<span data-ttu-id="ead7b-110">本演练并不依赖于对象关系设计器。</span><span class="sxs-lookup"><span data-stu-id="ead7b-110">This walkthrough does not rely on the Object Relational Designer.</span></span> <span data-ttu-id="ead7b-111">使用 Visual Studio 的开发人员还可以使用 O/R 设计器来实现存储过程功能。</span><span class="sxs-lookup"><span data-stu-id="ead7b-111">Developers using Visual Studio can also use the O/R Designer to implement stored procedure functionality.</span></span> <span data-ttu-id="ead7b-112">请参阅[Visual Studio 中的 LINQ to SQL 工具](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。</span><span class="sxs-lookup"><span data-stu-id="ead7b-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="ead7b-113">本演练是使用 Visual C# 开发设置编写的。</span><span class="sxs-lookup"><span data-stu-id="ead7b-113">This walkthrough was written by using Visual C# Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ead7b-114">系统必备</span><span class="sxs-lookup"><span data-stu-id="ead7b-114">Prerequisites</span></span>

<span data-ttu-id="ead7b-115">本演练需要如下内容：</span><span class="sxs-lookup"><span data-stu-id="ead7b-115">This walkthrough requires the following:</span></span>

- <span data-ttu-id="ead7b-116">本演练使用专用文件夹（“c:\linqtest7”）来保存文件。</span><span class="sxs-lookup"><span data-stu-id="ead7b-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="ead7b-117">请在开始本演练前创建此文件夹。</span><span class="sxs-lookup"><span data-stu-id="ead7b-117">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="ead7b-118">Northwind 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="ead7b-118">The Northwind sample database.</span></span>

     <span data-ttu-id="ead7b-119">如果您的开发计算机上没有此数据库，您可以从 Microsoft 下载网站下载它。</span><span class="sxs-lookup"><span data-stu-id="ead7b-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="ead7b-120">有关说明，请参阅[下载示例数据库](downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="ead7b-120">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="ead7b-121">下载此数据库后，请将 northwnd.mdf 文件复制到 c:\linqtest7 文件夹。</span><span class="sxs-lookup"><span data-stu-id="ead7b-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>

- <span data-ttu-id="ead7b-122">从 Northwind 数据库生成的 C# 代码文件。</span><span class="sxs-lookup"><span data-stu-id="ead7b-122">A C# code file generated from the Northwind database.</span></span>

     <span data-ttu-id="ead7b-123">本演练是通过使用 SqlMetal 工具以及如下命令行编写的：</span><span class="sxs-lookup"><span data-stu-id="ead7b-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>

     <span data-ttu-id="ead7b-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span><span class="sxs-lookup"><span data-stu-id="ead7b-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>

     <span data-ttu-id="ead7b-125">有关详细信息，请参阅 [SqlMetal.exe（代码生成工具）](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="ead7b-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>

## <a name="overview"></a><span data-ttu-id="ead7b-126">概述</span><span class="sxs-lookup"><span data-stu-id="ead7b-126">Overview</span></span>

<span data-ttu-id="ead7b-127">本演练由六项主要任务组成：</span><span class="sxs-lookup"><span data-stu-id="ead7b-127">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="ead7b-128">在 Visual Studio 中设置解决方案。[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ead7b-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="ead7b-129">将 System.Data.Linq 程序集添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="ead7b-129">Adding the System.Data.Linq assembly to the project.</span></span>

- <span data-ttu-id="ead7b-130">向项目添加数据库代码文件。</span><span class="sxs-lookup"><span data-stu-id="ead7b-130">Adding the database code file to the project.</span></span>

- <span data-ttu-id="ead7b-131">创建与数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="ead7b-131">Creating a connection with the database.</span></span>

- <span data-ttu-id="ead7b-132">设置用户界面。</span><span class="sxs-lookup"><span data-stu-id="ead7b-132">Setting up the user interface.</span></span>

- <span data-ttu-id="ead7b-133">运行和测试应用程序。</span><span class="sxs-lookup"><span data-stu-id="ead7b-133">Running and testing the application.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="ead7b-134">创建 LINQ to SQL 解决方案</span><span class="sxs-lookup"><span data-stu-id="ead7b-134">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="ead7b-135">在第一个任务中，您将创建一个 Visual Studio 解决方案，其中包含生成和运行[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]项目所必需的引用。</span><span class="sxs-lookup"><span data-stu-id="ead7b-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="ead7b-136">创建 LINQ to SQL 解决方案</span><span class="sxs-lookup"><span data-stu-id="ead7b-136">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="ead7b-137">在 Visual Studio 的 "**文件**" 菜单上，指向 "**新建**"，然后单击 "**项目**"。</span><span class="sxs-lookup"><span data-stu-id="ead7b-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="ead7b-138">在 "**新建项目**" 对话框的 "**项目类型**" 窗格中，单击 "  **C#视觉对象**"。</span><span class="sxs-lookup"><span data-stu-id="ead7b-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>

3. <span data-ttu-id="ead7b-139">在 **“模板”** 窗格中，单击 **“Windows 窗体应用程序”** 。</span><span class="sxs-lookup"><span data-stu-id="ead7b-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>

4. <span data-ttu-id="ead7b-140">在 "**名称**" 框中，键入**SprocOnlyApp**。</span><span class="sxs-lookup"><span data-stu-id="ead7b-140">In the **Name** box, type **SprocOnlyApp**.</span></span>

5. <span data-ttu-id="ead7b-141">在 "**位置**" 框中，验证要存储项目文件的位置。</span><span class="sxs-lookup"><span data-stu-id="ead7b-141">In the **Location** box, verify where you want to store your project files.</span></span>

6. <span data-ttu-id="ead7b-142">单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="ead7b-142">Click **OK**.</span></span>

     <span data-ttu-id="ead7b-143">Windows 窗体设计器即会打开。</span><span class="sxs-lookup"><span data-stu-id="ead7b-143">The Windows Forms Designer opens.</span></span>

## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="ead7b-144">添加 LINQ to SQL 程序集引用</span><span class="sxs-lookup"><span data-stu-id="ead7b-144">Adding the LINQ to SQL Assembly Reference</span></span>

<span data-ttu-id="ead7b-145">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 程序集未包含在标准的 Windows 窗体应用程序模板中。</span><span class="sxs-lookup"><span data-stu-id="ead7b-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="ead7b-146">您将需要按照以下步骤中的说明自行添加此程序集：</span><span class="sxs-lookup"><span data-stu-id="ead7b-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>

### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="ead7b-147">添加 System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="ead7b-147">To add System.Data.Linq.dll</span></span>

1. <span data-ttu-id="ead7b-148">在**解决方案资源管理器**中，右键单击 "**引用**"，然后单击 "**添加引用**"。</span><span class="sxs-lookup"><span data-stu-id="ead7b-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="ead7b-149">在 "**添加引用**" 对话框中，单击 " **.net**"，单击 "system.web" 程序集，然后单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="ead7b-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="ead7b-150">此程序集即被添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="ead7b-150">The assembly is added to the project.</span></span>

## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="ead7b-151">将 Northwind 代码文件添加到项目</span><span class="sxs-lookup"><span data-stu-id="ead7b-151">Adding the Northwind Code File to the Project</span></span>

<span data-ttu-id="ead7b-152">此步骤假定你已使用 SqlMetal 工具从 Northwind 示例数据库生成代码文件。</span><span class="sxs-lookup"><span data-stu-id="ead7b-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="ead7b-153">有关更多信息，请参见本演练前面部分的“先决条件”一节。</span><span class="sxs-lookup"><span data-stu-id="ead7b-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="ead7b-154">将 northwind 代码文件添加到项目</span><span class="sxs-lookup"><span data-stu-id="ead7b-154">To add the northwind code file to the project</span></span>

1. <span data-ttu-id="ead7b-155">在 "**项目**" 菜单上，单击 "**添加现有项**"。</span><span class="sxs-lookup"><span data-stu-id="ead7b-155">On the **Project** menu, click **Add Existing Item**.</span></span>

2. <span data-ttu-id="ead7b-156">在 "**添加现有项**" 对话框中，转到 "c:\linqtest7\northwind.cs"，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="ead7b-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>

     <span data-ttu-id="ead7b-157">northwind.cs 文件即被添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="ead7b-157">The northwind.cs file is added to the project.</span></span>

## <a name="creating-a-database-connection"></a><span data-ttu-id="ead7b-158">创建数据库连接</span><span class="sxs-lookup"><span data-stu-id="ead7b-158">Creating a Database Connection</span></span>

<span data-ttu-id="ead7b-159">在此步骤中，您要定义与 Northwind 示例数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="ead7b-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="ead7b-160">本演练使用“c:\linqtest7\northwnd.mdf”作为路径。</span><span class="sxs-lookup"><span data-stu-id="ead7b-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>

### <a name="to-create-the-database-connection"></a><span data-ttu-id="ead7b-161">创建数据库连接</span><span class="sxs-lookup"><span data-stu-id="ead7b-161">To create the database connection</span></span>

1. <span data-ttu-id="ead7b-162">在**解决方案资源管理器**中，右键单击**Form1.cs**，然后单击 "**查看代码**"。</span><span class="sxs-lookup"><span data-stu-id="ead7b-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>

2. <span data-ttu-id="ead7b-163">将下面的代码键入到 `Form1` 类中：</span><span class="sxs-lookup"><span data-stu-id="ead7b-163">Type the following code into the `Form1` class:</span></span>

     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]

## <a name="setting-up-the-user-interface"></a><span data-ttu-id="ead7b-164">设置用户界面</span><span class="sxs-lookup"><span data-stu-id="ead7b-164">Setting up the User Interface</span></span>

<span data-ttu-id="ead7b-165">在此任务中，你要设置一个界面，供用户执行存储过程以访问数据库中的数据之用。</span><span class="sxs-lookup"><span data-stu-id="ead7b-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="ead7b-166">在您按照本演练开发的应用程序中，用户只能使用应用程序中嵌入的存储过程来访问数据库中的数据。</span><span class="sxs-lookup"><span data-stu-id="ead7b-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>

### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="ead7b-167">设置用户界面</span><span class="sxs-lookup"><span data-stu-id="ead7b-167">To set up the user interface</span></span>

1. <span data-ttu-id="ead7b-168">返回到 Windows 窗体设计器（**cs [Design]** ）。</span><span class="sxs-lookup"><span data-stu-id="ead7b-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>

2. <span data-ttu-id="ead7b-169">在 **“视图”** 菜单上单击 **“工具箱”** 。</span><span class="sxs-lookup"><span data-stu-id="ead7b-169">On the **View** menu, click **Toolbox**.</span></span>

     <span data-ttu-id="ead7b-170">工具箱即会打开。</span><span class="sxs-lookup"><span data-stu-id="ead7b-170">The toolbox opens.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ead7b-171">单击 "自动**隐藏**" 图钉，使工具箱保持打开状态。</span><span class="sxs-lookup"><span data-stu-id="ead7b-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>

3. <span data-ttu-id="ead7b-172">将两个按钮、两个文本框和两个标签从工具箱拖到**Form1**上。</span><span class="sxs-lookup"><span data-stu-id="ead7b-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>

     <span data-ttu-id="ead7b-173">按照附图排列这些控件。</span><span class="sxs-lookup"><span data-stu-id="ead7b-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="ead7b-174">展开 " **Form1** "，使控件更容易。</span><span class="sxs-lookup"><span data-stu-id="ead7b-174">Expand **Form1** so that the controls fit easily.</span></span>

4. <span data-ttu-id="ead7b-175">右键单击 " **label1**"，然后单击 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="ead7b-175">Right-click **label1**, and then click **Properties**.</span></span>

5. <span data-ttu-id="ead7b-176">将 " **Text** " 属性从 " **label1** " 更改为 "**输入订单 id：** "。</span><span class="sxs-lookup"><span data-stu-id="ead7b-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>

6. <span data-ttu-id="ead7b-177">与**label2**相同的方式，将 " **Text** " 属性从 " **Label2** " 更改为 "**输入 CustomerID：** "。</span><span class="sxs-lookup"><span data-stu-id="ead7b-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>

7. <span data-ttu-id="ead7b-178">同样，将**button1**的**Text**属性更改为 "**订单详细信息**"。</span><span class="sxs-lookup"><span data-stu-id="ead7b-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>

8. <span data-ttu-id="ead7b-179">将**button2**的**Text**属性更改为**Order History**。</span><span class="sxs-lookup"><span data-stu-id="ead7b-179">Change the **Text** property for **button2** to **Order History**.</span></span>

     <span data-ttu-id="ead7b-180">将这些按钮控件加宽，以使所有文本均可见。</span><span class="sxs-lookup"><span data-stu-id="ead7b-180">Widen the button controls so that all the text is visible.</span></span>

### <a name="to-handle-button-clicks"></a><span data-ttu-id="ead7b-181">处理按钮单击</span><span class="sxs-lookup"><span data-stu-id="ead7b-181">To handle button clicks</span></span>

1. <span data-ttu-id="ead7b-182">双击 " **Form1** " 上的 "**订单详细信息**"，以在代码编辑器中打开 button1 事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="ead7b-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>

2. <span data-ttu-id="ead7b-183">将如下代码键入到 `button1` 处理程序中：</span><span class="sxs-lookup"><span data-stu-id="ead7b-183">Type the following code into the `button1` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]

3. <span data-ttu-id="ead7b-184">现在，双击 " **Form1** " 上的 " `button2` **button2** " 打开处理程序</span><span class="sxs-lookup"><span data-stu-id="ead7b-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>

4. <span data-ttu-id="ead7b-185">将如下代码键入到 `button2` 处理程序中：</span><span class="sxs-lookup"><span data-stu-id="ead7b-185">Type the following code into the `button2` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]

## <a name="testing-the-application"></a><span data-ttu-id="ead7b-186">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="ead7b-186">Testing the Application</span></span>

<span data-ttu-id="ead7b-187">现在，可以开始测试您的应用程序了。</span><span class="sxs-lookup"><span data-stu-id="ead7b-187">Now it is time to test your application.</span></span> <span data-ttu-id="ead7b-188">请注意，您可对数据存储施加的影响仅限于这两个存储过程能够执行的操作。</span><span class="sxs-lookup"><span data-stu-id="ead7b-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="ead7b-189">这些操作是要根据您输入的所有 orderID 返回相应订单包括的产品，或根据您输入的所有 CustomerID 返回相应客户的产品订购历史记录。</span><span class="sxs-lookup"><span data-stu-id="ead7b-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>

### <a name="to-test-the-application"></a><span data-ttu-id="ead7b-190">测试应用程序</span><span class="sxs-lookup"><span data-stu-id="ead7b-190">To test the application</span></span>

1. <span data-ttu-id="ead7b-191">按 F5 开始调试。</span><span class="sxs-lookup"><span data-stu-id="ead7b-191">Press F5 to start debugging.</span></span>

     <span data-ttu-id="ead7b-192">此时将显示 Form1。</span><span class="sxs-lookup"><span data-stu-id="ead7b-192">Form1 appears.</span></span>

2. <span data-ttu-id="ead7b-193">在 "**输入订单 id** " 框`10249`中，键入，然后单击 "**订单详细信息**"。</span><span class="sxs-lookup"><span data-stu-id="ead7b-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>

     <span data-ttu-id="ead7b-194">随即会显示一个消息框，其中列出了 10249 号订单中所包括的产品。</span><span class="sxs-lookup"><span data-stu-id="ead7b-194">A message box lists the products included in order 10249.</span></span>

     <span data-ttu-id="ead7b-195">单击 **"确定"** 关闭消息框。</span><span class="sxs-lookup"><span data-stu-id="ead7b-195">Click **OK** to close the message box.</span></span>

3. <span data-ttu-id="ead7b-196">在 "**输入 CustomerID** " 框中`ALFKI`键入，然后单击 "**订单历史记录**"。</span><span class="sxs-lookup"><span data-stu-id="ead7b-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>

     <span data-ttu-id="ead7b-197">随即会显示一个消息框，其中列出了 ALFKI 客户的订单历史记录。</span><span class="sxs-lookup"><span data-stu-id="ead7b-197">A message box appears that lists the order history for customer ALFKI.</span></span>

     <span data-ttu-id="ead7b-198">单击 **"确定"** 关闭消息框。</span><span class="sxs-lookup"><span data-stu-id="ead7b-198">Click **OK** to close the message box.</span></span>

4. <span data-ttu-id="ead7b-199">在 "**输入订单 id** " 框`123`中，键入，然后单击 "**订单详细信息**"。</span><span class="sxs-lookup"><span data-stu-id="ead7b-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>

     <span data-ttu-id="ead7b-200">随即会显示一个消息框，其中显示“无结果”。</span><span class="sxs-lookup"><span data-stu-id="ead7b-200">A message box appears that displays "No results."</span></span>

     <span data-ttu-id="ead7b-201">单击 **"确定"** 关闭消息框。</span><span class="sxs-lookup"><span data-stu-id="ead7b-201">Click **OK** to close the message box.</span></span>

5. <span data-ttu-id="ead7b-202">在 "**调试**" 菜单上单击 "**停止调试**"。</span><span class="sxs-lookup"><span data-stu-id="ead7b-202">On the **Debug** menu, click **Stop debugging**.</span></span>

     <span data-ttu-id="ead7b-203">调试会话即会关闭。</span><span class="sxs-lookup"><span data-stu-id="ead7b-203">The debug session closes.</span></span>

6. <span data-ttu-id="ead7b-204">如果已完成试验，则可以单击 "**文件**" 菜单上的 "**关闭项目**"，并在出现提示时保存项目。</span><span class="sxs-lookup"><span data-stu-id="ead7b-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ead7b-205">后续步骤</span><span class="sxs-lookup"><span data-stu-id="ead7b-205">Next Steps</span></span>

<span data-ttu-id="ead7b-206">您可以通过做一些更改来增强此项目的功能。</span><span class="sxs-lookup"><span data-stu-id="ead7b-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="ead7b-207">例如，您可以在列表框中列出可用的存储过程，供用户选择要执行哪些过程。</span><span class="sxs-lookup"><span data-stu-id="ead7b-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="ead7b-208">您还可以将报告的输出以流的方式传输到文本文件。</span><span class="sxs-lookup"><span data-stu-id="ead7b-208">You could also stream the output of the reports to a text file.</span></span>

## <a name="see-also"></a><span data-ttu-id="ead7b-209">请参阅</span><span class="sxs-lookup"><span data-stu-id="ead7b-209">See also</span></span>

- [<span data-ttu-id="ead7b-210">通过演练学习</span><span class="sxs-lookup"><span data-stu-id="ead7b-210">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="ead7b-211">存储过程</span><span class="sxs-lookup"><span data-stu-id="ead7b-211">Stored Procedures</span></span>](stored-procedures.md)
