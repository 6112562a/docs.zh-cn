---
title: 演练：DataGrid 控件中显示的 SQL Server 数据库中的数据
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: 022be17c946529583694afc0fe1c61b832aa03e4
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351316"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a><span data-ttu-id="75349-102">演练：DataGrid 控件中显示的 SQL Server 数据库中的数据</span><span class="sxs-lookup"><span data-stu-id="75349-102">Walkthrough: Display data from a SQL Server database in a DataGrid control</span></span>

<span data-ttu-id="75349-103">在本演练中，将从 SQL Server 数据库中检索数据和显示中的这些数据<xref:System.Windows.Controls.DataGrid>控件。</span><span class="sxs-lookup"><span data-stu-id="75349-103">In this walkthrough, you retrieve data from a SQL Server database and display that data in a <xref:System.Windows.Controls.DataGrid> control.</span></span> <span data-ttu-id="75349-104">ADO.NET 实体框架用于创建表示数据，并使用 LINQ 编写从实体类检索指定的数据的查询的实体类。</span><span class="sxs-lookup"><span data-stu-id="75349-104">You use the ADO.NET Entity Framework to create the entity classes that represent the data, and use LINQ to write a query that retrieves the specified data from an entity class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="75349-105">系统必备</span><span class="sxs-lookup"><span data-stu-id="75349-105">Prerequisites</span></span>

<span data-ttu-id="75349-106">你需要以下组件来完成本演练：</span><span class="sxs-lookup"><span data-stu-id="75349-106">You need the following components to complete this walkthrough:</span></span>

-   <span data-ttu-id="75349-107">Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="75349-107">Visual Studio.</span></span>

-   <span data-ttu-id="75349-108">正在运行的 SQL Server 或 SQL Server Express 的 AdventureWorks 示例数据库附加到该实例的访问权限。</span><span class="sxs-lookup"><span data-stu-id="75349-108">Access to a running instance of SQL Server or SQL Server Express that has the AdventureWorks sample database attached to it.</span></span> <span data-ttu-id="75349-109">您可以下载 AdventureWorks 数据库从[GitHub](https://github.com/Microsoft/sql-server-samples/releases)。</span><span class="sxs-lookup"><span data-stu-id="75349-109">You can download the AdventureWorks database from the [GitHub](https://github.com/Microsoft/sql-server-samples/releases).</span></span>

## <a name="create-entity-classes"></a><span data-ttu-id="75349-110">创建实体类</span><span class="sxs-lookup"><span data-stu-id="75349-110">Create entity classes</span></span>

1.  <span data-ttu-id="75349-111">在 Visual Basic 或 C# 中，创建一个新的 WPF 应用程序项目并将其命名`DataGridSQLExample`。</span><span class="sxs-lookup"><span data-stu-id="75349-111">Create a new WPF Application project in Visual Basic or C#, and name it `DataGridSQLExample`.</span></span>

2.  <span data-ttu-id="75349-112">在解决方案资源管理器中右键单击你的项目，指向**外**，然后选择**新项**。</span><span class="sxs-lookup"><span data-stu-id="75349-112">In Solution Explorer, right-click your project, point to **Add**, and then select **New Item**.</span></span>

     <span data-ttu-id="75349-113">添加新项对话框。</span><span class="sxs-lookup"><span data-stu-id="75349-113">The Add New Item dialog box appears.</span></span>

3.  <span data-ttu-id="75349-114">在已安装的模板窗格中，选择**数据**，然后在模板列表中，选择**ADO.NET 实体数据模型**。</span><span class="sxs-lookup"><span data-stu-id="75349-114">In the Installed Templates pane, select **Data** and in the list of templates, select **ADO.NET Entity Data Model**.</span></span>

     ![ADO.NET 实体数据模型项模板](../../wcf/feature-details/./media/ado-net-entity-data-model-item-template.png)

4.  <span data-ttu-id="75349-116">将文件命名`AdventureWorksModel.edmx`，然后单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="75349-116">Name the file `AdventureWorksModel.edmx` and then click **Add**.</span></span>

     <span data-ttu-id="75349-117">此时将显示实体数据模型向导。</span><span class="sxs-lookup"><span data-stu-id="75349-117">The Entity Data Model Wizard appears.</span></span>

5.  <span data-ttu-id="75349-118">在选择模型内容屏幕中，选择**EF 设计器从数据库**，然后单击**下一步**。</span><span class="sxs-lookup"><span data-stu-id="75349-118">In the Choose Model Contents screen, select **EF Designer from database** and then click **Next**.</span></span>

6.  <span data-ttu-id="75349-119">在选择数据连接屏幕中，提供 AdventureWorksLT2008 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="75349-119">In the Choose Your Data Connection screen, provide the connection to your AdventureWorksLT2008 database.</span></span> <span data-ttu-id="75349-120">有关详细信息，请参阅[选择数据连接对话框中](https://go.microsoft.com/fwlink/?LinkId=160190)。</span><span class="sxs-lookup"><span data-stu-id="75349-120">For more information, see [Choose Your Data Connection Dialog Box](https://go.microsoft.com/fwlink/?LinkId=160190).</span></span>

    <span data-ttu-id="75349-121">请确保名称是`AdventureWorksLT2008Entities`并且**将实体连接设置保存在 App.Config 作为**复选框已选中，然后依次**下一步**。</span><span class="sxs-lookup"><span data-stu-id="75349-121">Make sure that the name is `AdventureWorksLT2008Entities` and that the **Save entity connection settings in App.Config as** check box is selected, and then click **Next**.</span></span>

7.  <span data-ttu-id="75349-122">在选择数据库对象屏幕中，展开表节点，并选择**产品**并**ProductCategory**表。</span><span class="sxs-lookup"><span data-stu-id="75349-122">In the Choose Your Database Objects screen, expand the Tables node, and select the **Product** and **ProductCategory** tables.</span></span>

     <span data-ttu-id="75349-123">您可以为生成实体类的所有表;但是，在此示例中您只能从检索数据这两个表。</span><span class="sxs-lookup"><span data-stu-id="75349-123">You can generate entity classes for all of the tables; however, in this example you only retrieve data from those two tables.</span></span>

     <span data-ttu-id="75349-124">![从表中选择 Product 和 ProductCategory](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span><span class="sxs-lookup"><span data-stu-id="75349-124">![Select Product and ProductCategory from tables](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")</span></span>

8. <span data-ttu-id="75349-125">单击 **“完成”**。</span><span class="sxs-lookup"><span data-stu-id="75349-125">Click **Finish**.</span></span>

     <span data-ttu-id="75349-126">在实体设计器中显示 Product 和 ProductCategory 实体。</span><span class="sxs-lookup"><span data-stu-id="75349-126">The Product and ProductCategory entities are displayed in the Entity Designer.</span></span>

     <span data-ttu-id="75349-127">![Product 和 ProductCategory 实体模型](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span><span class="sxs-lookup"><span data-stu-id="75349-127">![Product and ProductCategory entity models](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")</span></span>

## <a name="retrieve-and-present-the-data"></a><span data-ttu-id="75349-128">检索和呈现数据</span><span class="sxs-lookup"><span data-stu-id="75349-128">Retrieve and present the data</span></span>

1.  <span data-ttu-id="75349-129">打开 MainWindow.xaml 文件。</span><span class="sxs-lookup"><span data-stu-id="75349-129">Open the MainWindow.xaml file.</span></span>

2.  <span data-ttu-id="75349-130">设置<xref:System.Windows.FrameworkElement.Width%2A>属性上的<xref:System.Windows.Window>到 450。</span><span class="sxs-lookup"><span data-stu-id="75349-130">Set the <xref:System.Windows.FrameworkElement.Width%2A> property on the <xref:System.Windows.Window> to 450.</span></span>

3.  <span data-ttu-id="75349-131">在 XAML 编辑器中，添加以下<xref:System.Windows.Controls.DataGrid>标记之间`<Grid>`并`</Grid>`要添加的标记<xref:System.Windows.Controls.DataGrid>名为`dataGrid1`。</span><span class="sxs-lookup"><span data-stu-id="75349-131">In the XAML editor, add the following <xref:System.Windows.Controls.DataGrid> tag between the `<Grid>` and `</Grid>` tags to add a <xref:System.Windows.Controls.DataGrid> named `dataGrid1`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     <span data-ttu-id="75349-132">![含 DataGrid 的窗口](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span><span class="sxs-lookup"><span data-stu-id="75349-132">![Window with DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")</span></span>

4.  <span data-ttu-id="75349-133">选择 <xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="75349-133">Select the <xref:System.Windows.Window>.</span></span>

5.  <span data-ttu-id="75349-134">使用属性窗口或 XAML 编辑器中，创建的事件处理程序<xref:System.Windows.Window>名为`Window_Loaded`为<xref:System.Windows.FrameworkElement.Loaded>事件。</span><span class="sxs-lookup"><span data-stu-id="75349-134">Using the Properties window or XAML editor, create an event handler for the <xref:System.Windows.Window> named `Window_Loaded` for the <xref:System.Windows.FrameworkElement.Loaded> event.</span></span> <span data-ttu-id="75349-135">有关详细信息，请参阅[如何：创建一个简单的事件处理程序](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="75349-135">For more information, see [How to: Create a Simple Event Handler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).</span></span>

     <span data-ttu-id="75349-136">下图显示 XAML mainwindow.xaml。</span><span class="sxs-lookup"><span data-stu-id="75349-136">The following shows the XAML for MainWindow.xaml.</span></span>

    > [!NOTE]
    > <span data-ttu-id="75349-137">如果使用的 Visual Basic 中，在 MainWindow.xaml 的第一行中，替换`x:Class="DataGridSQLExample.MainWindow"`与`x:Class="MainWindow"`。</span><span class="sxs-lookup"><span data-stu-id="75349-137">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridSQLExample.MainWindow"` with `x:Class="MainWindow"`.</span></span>

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6.  <span data-ttu-id="75349-138">打开代码隐藏文件 （MainWindow.xaml.vb 或 MainWindow.xaml.cs） <xref:System.Windows.Window>。</span><span class="sxs-lookup"><span data-stu-id="75349-138">Open the code-behind file (MainWindow.xaml.vb or MainWindow.xaml.cs) for the <xref:System.Windows.Window>.</span></span>

7.  <span data-ttu-id="75349-139">添加以下代码来联接表中检索特定的值并设置<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>属性的<xref:System.Windows.Controls.DataGrid>到查询的结果。</span><span class="sxs-lookup"><span data-stu-id="75349-139">Add the following code to retrieve only specific values from the joined tables and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.DataGrid> to the results of the query.</span></span>

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8.  <span data-ttu-id="75349-140">运行示例。</span><span class="sxs-lookup"><span data-stu-id="75349-140">Run the example.</span></span>

     <span data-ttu-id="75349-141">应会看到<xref:System.Windows.Controls.DataGrid>显示数据。</span><span class="sxs-lookup"><span data-stu-id="75349-141">You should see a <xref:System.Windows.Controls.DataGrid> that displays data.</span></span>

     <span data-ttu-id="75349-142">![SQL 数据库中的数据的 DataGrid](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span><span class="sxs-lookup"><span data-stu-id="75349-142">![DataGrid with data from SQL database](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")</span></span>

## <a name="see-also"></a><span data-ttu-id="75349-143">请参阅</span><span class="sxs-lookup"><span data-stu-id="75349-143">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>
- [<span data-ttu-id="75349-144">如何实现:开始使用 WPF 应用程序中的实体框架？</span><span class="sxs-lookup"><span data-stu-id="75349-144">How Do I: Get Started with Entity Framework in WPF Applications?</span></span>](https://go.microsoft.com/fwlink/?LinkId=159868)