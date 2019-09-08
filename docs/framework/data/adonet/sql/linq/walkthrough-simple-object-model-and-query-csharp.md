---
title: 演练：简单对象模型和查询 (C#)
ms.date: 03/30/2017
ms.assetid: 419961cc-92d6-45f5-ae8a-d485bdde3a37
ms.openlocfilehash: a9b3b57e37331cd13f2cd30b8a7663f2fb39d8c1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792128"
---
# <a name="walkthrough-simple-object-model-and-query-c"></a><span data-ttu-id="07471-102">演练：简单对象模型和查询 (C#)</span><span class="sxs-lookup"><span data-stu-id="07471-102">Walkthrough: Simple Object Model and Query (C#)</span></span>

<span data-ttu-id="07471-103">本演练提供了复杂性最小的基本端对端 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 方案。</span><span class="sxs-lookup"><span data-stu-id="07471-103">This walkthrough provides a fundamental end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario with minimal complexities.</span></span> <span data-ttu-id="07471-104">您将创建一个可为示例 Northwind 数据库中的 Customers 表建模的实体类。</span><span class="sxs-lookup"><span data-stu-id="07471-104">You will create an entity class that models the Customers table in the sample Northwind database.</span></span> <span data-ttu-id="07471-105">然后您将创建一个简单查询，用于列出位于伦敦的客户。</span><span class="sxs-lookup"><span data-stu-id="07471-105">You will then create a simple query to list customers who are located in London.</span></span>

<span data-ttu-id="07471-106">本演练在设计上是面向代码的，以帮助说明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 概念。</span><span class="sxs-lookup"><span data-stu-id="07471-106">This walkthrough is code-oriented by design to help show [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] concepts.</span></span> <span data-ttu-id="07471-107">通常，可以使用对象关系设计器来创建对象模型。</span><span class="sxs-lookup"><span data-stu-id="07471-107">Normally speaking, you would use the Object Relational Designer to create your object model.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="07471-108">本演练是使用 Visual C# 开发设置编写的。</span><span class="sxs-lookup"><span data-stu-id="07471-108">This walkthrough was written by using Visual C# Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="07471-109">系统必备</span><span class="sxs-lookup"><span data-stu-id="07471-109">Prerequisites</span></span>

- <span data-ttu-id="07471-110">本演练使用专用文件夹（“c:\linqtest5”）来保存文件。</span><span class="sxs-lookup"><span data-stu-id="07471-110">This walkthrough uses a dedicated folder ("c:\linqtest5") to hold files.</span></span> <span data-ttu-id="07471-111">请在开始本演练前创建此文件夹。</span><span class="sxs-lookup"><span data-stu-id="07471-111">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="07471-112">本演练需要 Northwind 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="07471-112">This walkthrough requires the Northwind sample database.</span></span> <span data-ttu-id="07471-113">如果您的开发计算机上没有此数据库，您可以从 Microsoft 下载网站下载它。</span><span class="sxs-lookup"><span data-stu-id="07471-113">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="07471-114">有关说明，请参阅[下载示例数据库](downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="07471-114">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="07471-115">下载此数据库后，请将文件复制到 c:\linqtest5 文件夹。</span><span class="sxs-lookup"><span data-stu-id="07471-115">After you have downloaded the database, copy the file to the c:\linqtest5 folder.</span></span>

## <a name="overview"></a><span data-ttu-id="07471-116">概述</span><span class="sxs-lookup"><span data-stu-id="07471-116">Overview</span></span>

<span data-ttu-id="07471-117">本演练由六项主要任务组成：</span><span class="sxs-lookup"><span data-stu-id="07471-117">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="07471-118">在 Visual Studio 中创建解决方案。[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07471-118">Creating a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="07471-119">将类映射到数据库表。</span><span class="sxs-lookup"><span data-stu-id="07471-119">Mapping a class to a database table.</span></span>

- <span data-ttu-id="07471-120">指定类中的属性表示数据库列。</span><span class="sxs-lookup"><span data-stu-id="07471-120">Designating properties on the class to represent database columns.</span></span>

- <span data-ttu-id="07471-121">指定到 Northwind 数据库的连接。</span><span class="sxs-lookup"><span data-stu-id="07471-121">Specifying the connection to the Northwind database.</span></span>

- <span data-ttu-id="07471-122">创建针对该数据库运行的简单查询。</span><span class="sxs-lookup"><span data-stu-id="07471-122">Creating a simple query to run against the database.</span></span>

- <span data-ttu-id="07471-123">执行查询并观察结果。</span><span class="sxs-lookup"><span data-stu-id="07471-123">Executing the query and observing the results.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="07471-124">创建 LINQ to SQL 解决方案</span><span class="sxs-lookup"><span data-stu-id="07471-124">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="07471-125">在第一个任务中，您将创建一个 Visual Studio 解决方案，其中包含生成和运行[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]项目所必需的引用。</span><span class="sxs-lookup"><span data-stu-id="07471-125">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="07471-126">创建 LINQ to SQL 解决方案</span><span class="sxs-lookup"><span data-stu-id="07471-126">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="07471-127">在 Visual Studio 的 "**文件**" 菜单上，指向 "**新建**"，然后单击 "**项目**"。</span><span class="sxs-lookup"><span data-stu-id="07471-127">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="07471-128">在 "**新建项目**" 对话框的 "**项目类型**" 窗格中，单击 "  **C#视觉对象**"。</span><span class="sxs-lookup"><span data-stu-id="07471-128">In the **Project types** pane of the **New Project** dialog box, click **Visual C#**.</span></span>

3. <span data-ttu-id="07471-129">在“模板”窗格中，单击“控制台应用程序”。</span><span class="sxs-lookup"><span data-stu-id="07471-129">In the **Templates** pane, click **Console Application**.</span></span>

4. <span data-ttu-id="07471-130">在 "**名称**" 框中，键入**LinqConsoleApp**。</span><span class="sxs-lookup"><span data-stu-id="07471-130">In the **Name** box, type **LinqConsoleApp**.</span></span>

5. <span data-ttu-id="07471-131">在 "**位置**" 框中，验证要存储项目文件的位置。</span><span class="sxs-lookup"><span data-stu-id="07471-131">In the **Location** box, verify where you want to store your project files.</span></span>

6. <span data-ttu-id="07471-132">单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="07471-132">Click **OK**.</span></span>

## <a name="adding-linq-references-and-directives"></a><span data-ttu-id="07471-133">添加 LINQ 引用和指令</span><span class="sxs-lookup"><span data-stu-id="07471-133">Adding LINQ References and Directives</span></span>

<span data-ttu-id="07471-134">本演练用到默认情况下您的项目中可能未安装的程序集。</span><span class="sxs-lookup"><span data-stu-id="07471-134">This walkthrough uses assemblies that might not be installed by default in your project.</span></span> <span data-ttu-id="07471-135">如果在你的项目中未将 System.web 列为引用（展开**解决方案资源管理器**中的 "**引用**" 节点），请添加它，如以下步骤中所述。</span><span class="sxs-lookup"><span data-stu-id="07471-135">If System.Data.Linq is not listed as a reference in your project (expand the **References** node in **Solution Explorer**), add it, as explained in the following steps.</span></span>

### <a name="to-add-systemdatalinq"></a><span data-ttu-id="07471-136">添加 System.Data.Linq</span><span class="sxs-lookup"><span data-stu-id="07471-136">To add System.Data.Linq</span></span>

1. <span data-ttu-id="07471-137">在**解决方案资源管理器**中，右键单击 "**引用**"，然后单击 "**添加引用**"。</span><span class="sxs-lookup"><span data-stu-id="07471-137">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="07471-138">在 "**添加引用**" 对话框中，单击 " **.net**"，单击 "system.web" 程序集，然后单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="07471-138">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="07471-139">此程序集即被添加到项目中。</span><span class="sxs-lookup"><span data-stu-id="07471-139">The assembly is added to the project.</span></span>

3. <span data-ttu-id="07471-140">在**Program.cs**的顶部添加以下指令：</span><span class="sxs-lookup"><span data-stu-id="07471-140">Add the following directives at the top of **Program.cs**:</span></span>

     [!code-csharp[DLinqWalk1CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#1)]

## <a name="mapping-a-class-to-a-database-table"></a><span data-ttu-id="07471-141">将类映射到数据库表</span><span class="sxs-lookup"><span data-stu-id="07471-141">Mapping a Class to a Database Table</span></span>

<span data-ttu-id="07471-142">在此步骤中，您将创建一个类，并将其映射到数据库表。</span><span class="sxs-lookup"><span data-stu-id="07471-142">In this step, you create a class and map it to a database table.</span></span> <span data-ttu-id="07471-143">这类类称为*实体类*。</span><span class="sxs-lookup"><span data-stu-id="07471-143">Such a class is termed an *entity class*.</span></span> <span data-ttu-id="07471-144">请注意，只需添加 <xref:System.Data.Linq.Mapping.TableAttribute> 属性即可完成映射。</span><span class="sxs-lookup"><span data-stu-id="07471-144">Note that the mapping is accomplished by just adding the <xref:System.Data.Linq.Mapping.TableAttribute> attribute.</span></span> <span data-ttu-id="07471-145"><xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> 属性指定数据库中的表的名称。</span><span class="sxs-lookup"><span data-stu-id="07471-145">The <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property specifies the name of the table in the database.</span></span>

### <a name="to-create-an-entity-class-and-map-it-to-a-database-table"></a><span data-ttu-id="07471-146">创建一个实体类并将其映射到数据库表</span><span class="sxs-lookup"><span data-stu-id="07471-146">To create an entity class and map it to a database table</span></span>

- <span data-ttu-id="07471-147">将下面的代码键入或粘贴到 Program.cs 中紧靠在 `Program` 类声明上方的位置：</span><span class="sxs-lookup"><span data-stu-id="07471-147">Type or paste the following code into Program.cs immediately above the `Program` class declaration:</span></span>

     [!code-csharp[DLinqWalk1CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#2)]

## <a name="designating-properties-on-the-class-to-represent-database-columns"></a><span data-ttu-id="07471-148">指定类中的属性表示数据库列</span><span class="sxs-lookup"><span data-stu-id="07471-148">Designating Properties on the Class to Represent Database Columns</span></span>

<span data-ttu-id="07471-149">在此步骤中，你要完成几项任务。</span><span class="sxs-lookup"><span data-stu-id="07471-149">In this step, you accomplish several tasks.</span></span>

- <span data-ttu-id="07471-150">您要使用 <xref:System.Data.Linq.Mapping.ColumnAttribute> 属性 (Attribute) 指定实体类中的 `CustomerID` 和 `City` 属性 (Property) 表示数据库表中的列。</span><span class="sxs-lookup"><span data-stu-id="07471-150">You use the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate `CustomerID` and `City` properties on the entity class as representing columns in the database table.</span></span>

- <span data-ttu-id="07471-151">您要指定 `CustomerID` 属性表示数据库中的主键列。</span><span class="sxs-lookup"><span data-stu-id="07471-151">You designate the `CustomerID` property as representing a primary key column in the database.</span></span>

- <span data-ttu-id="07471-152">您要指定 `_CustomerID` 和 `_City` 字段用作私有存储字段。</span><span class="sxs-lookup"><span data-stu-id="07471-152">You designate `_CustomerID` and `_City` fields for private storage.</span></span> <span data-ttu-id="07471-153">然后，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 就可以直接存储和检索值，而不用使用可能包含业务逻辑的公共访问器。</span><span class="sxs-lookup"><span data-stu-id="07471-153">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can then store and retrieve values directly, instead of using public accessors that might include business logic.</span></span>

### <a name="to-represent-characteristics-of-two-database-columns"></a><span data-ttu-id="07471-154">表示两个数据库列的特性</span><span class="sxs-lookup"><span data-stu-id="07471-154">To represent characteristics of two database columns</span></span>

- <span data-ttu-id="07471-155">将下面的代码键入或粘贴到 Program.cs 中 `Customer` 类的大括号内。</span><span class="sxs-lookup"><span data-stu-id="07471-155">Type or paste the following code into Program.cs inside the curly braces for the `Customer` class.</span></span>

     [!code-csharp[DLinqWalk1CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#3)]

## <a name="specifying-the-connection-to-the-northwind-database"></a><span data-ttu-id="07471-156">指定到 Northwind 数据库的连接</span><span class="sxs-lookup"><span data-stu-id="07471-156">Specifying the Connection to the Northwind Database</span></span>

<span data-ttu-id="07471-157">在此步骤中，要使用 <xref:System.Data.Linq.DataContext> 对象在你基于代码的数据结构和数据库本身之间建立连接。</span><span class="sxs-lookup"><span data-stu-id="07471-157">In this step you use a <xref:System.Data.Linq.DataContext> object to establish a connection between your code-based data structures and the database itself.</span></span> <span data-ttu-id="07471-158"><xref:System.Data.Linq.DataContext> 是您从数据库中检索对象和提交更改的主要通道。</span><span class="sxs-lookup"><span data-stu-id="07471-158">The <xref:System.Data.Linq.DataContext> is the main channel through which you retrieve objects from the database and submit changes.</span></span>

<span data-ttu-id="07471-159">您还需声明 `Table<Customer>`，用作您针对数据库中 Customers 表的查询的逻辑、类型化表。</span><span class="sxs-lookup"><span data-stu-id="07471-159">You also declare a `Table<Customer>` to act as the logical, typed table for your queries against the Customers table in the database.</span></span> <span data-ttu-id="07471-160">您将在后续步骤中创建和执行这些查询。</span><span class="sxs-lookup"><span data-stu-id="07471-160">You will create and execute these queries in later steps.</span></span>

### <a name="to-specify-the-database-connection"></a><span data-ttu-id="07471-161">指定数据库连接</span><span class="sxs-lookup"><span data-stu-id="07471-161">To specify the database connection</span></span>

- <span data-ttu-id="07471-162">将下面的代码键入或粘贴到 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="07471-162">Type or paste the following code into the `Main` method.</span></span>

     <span data-ttu-id="07471-163">请注意，假定 `northwnd.mdf` 文件位于 linqtest5 文件夹中。</span><span class="sxs-lookup"><span data-stu-id="07471-163">Note that the `northwnd.mdf` file is assumed to be in the linqtest5 folder.</span></span> <span data-ttu-id="07471-164">有关更多信息，请参见本演练前面部分的“先决条件”一节。</span><span class="sxs-lookup"><span data-stu-id="07471-164">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

     [!code-csharp[DLinqWalk1CS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1CS/cs/Program.cs#4)]

## <a name="creating-a-simple-query"></a><span data-ttu-id="07471-165">创建简单查询</span><span class="sxs-lookup"><span data-stu-id="07471-165">Creating a Simple Query</span></span>

<span data-ttu-id="07471-166">在此步骤中，您将创建一个查询，查找数据库中的 Customers 表内的哪些客户位于伦敦。</span><span class="sxs-lookup"><span data-stu-id="07471-166">In this step, you create a query to find which customers in the database Customers table are located in London.</span></span> <span data-ttu-id="07471-167">此步骤中的查询代码只描述查询。</span><span class="sxs-lookup"><span data-stu-id="07471-167">The query code in this step just describes the query.</span></span> <span data-ttu-id="07471-168">它不执行查询。</span><span class="sxs-lookup"><span data-stu-id="07471-168">It does not execute it.</span></span> <span data-ttu-id="07471-169">此方法称为 "*延迟执行*"。</span><span class="sxs-lookup"><span data-stu-id="07471-169">This approach is known as *deferred execution*.</span></span> <span data-ttu-id="07471-170">有关详细信息，请参阅 [LINQ 查询简介 (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="07471-170">For more information, see [Introduction to LINQ Queries (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

<span data-ttu-id="07471-171">您还将生成一个日志输出，显示 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 生成的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="07471-171">You will also produce a log output to show the SQL commands that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates.</span></span> <span data-ttu-id="07471-172">此日志记录功能（使用 <xref:System.Data.Linq.DataContext.Log%2A>）对调试有帮助，并有助于确定发送给数据库的命令是否准确地表示您的查询。</span><span class="sxs-lookup"><span data-stu-id="07471-172">This logging feature (which uses <xref:System.Data.Linq.DataContext.Log%2A>) is helpful in debugging, and in determining that the commands being sent to the database accurately represent your query.</span></span>

### <a name="to-create-a-simple-query"></a><span data-ttu-id="07471-173">创建简单查询</span><span class="sxs-lookup"><span data-stu-id="07471-173">To create a simple query</span></span>

- <span data-ttu-id="07471-174">将下面的代码键入或粘贴到 `Main` 方法中的 `Table<Customer>` 声明后面。</span><span class="sxs-lookup"><span data-stu-id="07471-174">Type or paste the following code into the `Main` method after the `Table<Customer>` declaration.</span></span>

     [!code-csharp[DLinqWalk1ACS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#5)]

## <a name="executing-the-query"></a><span data-ttu-id="07471-175">执行查询</span><span class="sxs-lookup"><span data-stu-id="07471-175">Executing the Query</span></span>

<span data-ttu-id="07471-176">在此步骤中，您将实际执行查询。</span><span class="sxs-lookup"><span data-stu-id="07471-176">In this step, you actually execute the query.</span></span> <span data-ttu-id="07471-177">您在前面步骤中创建的查询表达式只有在需要结果时才会进行计算。</span><span class="sxs-lookup"><span data-stu-id="07471-177">The query expressions you created in the previous steps are not evaluated until the results are needed.</span></span> <span data-ttu-id="07471-178">当您开始 `foreach` 迭代时，将对数据库执行 SQL 命令，并将对象具体化。</span><span class="sxs-lookup"><span data-stu-id="07471-178">When you begin the `foreach` iteration, a SQL command is executed against the database and objects are materialized.</span></span>

### <a name="to-execute-the-query"></a><span data-ttu-id="07471-179">执行查询</span><span class="sxs-lookup"><span data-stu-id="07471-179">To execute the query</span></span>

1. <span data-ttu-id="07471-180">将下面的代码键入或粘贴到 `Main` 方法的末尾（在查询说明之后）。</span><span class="sxs-lookup"><span data-stu-id="07471-180">Type or paste the following code at the end of the `Main` method (after the query description).</span></span>

     [!code-csharp[DLinqWalk1ACS#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk1ACS/cs/Program.cs#6)]

2. <span data-ttu-id="07471-181">按 F5 调试该应用程序。</span><span class="sxs-lookup"><span data-stu-id="07471-181">Press F5 to debug the application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="07471-182">如果你的应用程序产生运行时错误，请参阅[通过演练学习](learning-by-walkthroughs.md)的疑难解答部分。</span><span class="sxs-lookup"><span data-stu-id="07471-182">If your application generates a run-time error, see the Troubleshooting section of [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

     <span data-ttu-id="07471-183">控制台窗口中的查询结果应显示如下：</span><span class="sxs-lookup"><span data-stu-id="07471-183">The query results in the console window should appear as follows:</span></span>

     `ID=AROUT, City=London`

     `ID=BSBEV, City=London`

     `ID=CONSH, City=London`

     `ID=EASTC, City=London`

     `ID=NORTS, City=London`

     `ID=SEVES, City=London`

3. <span data-ttu-id="07471-184">在控制台窗口中按 Enter 以关闭应用程序。</span><span class="sxs-lookup"><span data-stu-id="07471-184">Press Enter in the console window to close the application.</span></span>

## <a name="next-steps"></a><span data-ttu-id="07471-185">后续步骤</span><span class="sxs-lookup"><span data-stu-id="07471-185">Next Steps</span></span>

<span data-ttu-id="07471-186">[演练：跨关系查询（C#）](walkthrough-querying-across-relationships-csharp.md)主题将继续本演练结束的位置。</span><span class="sxs-lookup"><span data-stu-id="07471-186">The [Walkthrough: Querying Across Relationships (C#)](walkthrough-querying-across-relationships-csharp.md) topic continues where this walkthrough ends.</span></span> <span data-ttu-id="07471-187">"跨关系进行查询" 演练[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]演示如何跨表查询，类似于关系数据库中的*联接*。</span><span class="sxs-lookup"><span data-stu-id="07471-187">The Query Across Relationships walkthrough demonstrates how [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can query across tables, similar to *joins* in a relational database.</span></span>

<span data-ttu-id="07471-188">如果您希望进行“跨关系查询”演练，请务必保存您刚完成演练的解决方案，这是“跨关系查询”演练的前提条件。</span><span class="sxs-lookup"><span data-stu-id="07471-188">If you want to do the Query Across Relationships walkthrough, make sure to save the solution for the walkthrough you have just completed, which is a prerequisite.</span></span>

## <a name="see-also"></a><span data-ttu-id="07471-189">请参阅</span><span class="sxs-lookup"><span data-stu-id="07471-189">See also</span></span>

- [<span data-ttu-id="07471-190">通过演练学习</span><span class="sxs-lookup"><span data-stu-id="07471-190">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
