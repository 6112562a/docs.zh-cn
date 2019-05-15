---
title: 如何：创建数据服务使用 ADO.NET 实体框架数据源 （WCF 数据服务）
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: e9b2c1077cf3323a7d5b69bee6dff7e6f9611818
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634118"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="854ef-102">如何：创建数据服务使用 ADO.NET 实体框架数据源 （WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="854ef-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>

<span data-ttu-id="854ef-103">WCF 数据服务公开实体数据作为数据服务。</span><span class="sxs-lookup"><span data-stu-id="854ef-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="854ef-104">如果数据源为关系数据库，则此实体数据是由 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]提供的。</span><span class="sxs-lookup"><span data-stu-id="854ef-104">This entity data is provided by the [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] when the data source is a relational database.</span></span> <span data-ttu-id="854ef-105">本主题演示如何创建[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-基于 Visual Studio Web 应用程序，基于现有数据库和使用此数据模型来创建新的数据服务中的数据模型。</span><span class="sxs-lookup"><span data-stu-id="854ef-105">This topic shows you how to create an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-based data model in a Visual Studio Web application that is based on an existing database and use this data model to create a new data service.</span></span>

<span data-ttu-id="854ef-106">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]还提供了可以生成一个命令行工具[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]模型之外的 Visual Studio 项目。</span><span class="sxs-lookup"><span data-stu-id="854ef-106">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] also provides a command line tool that can generate an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] model outside of a Visual Studio project.</span></span> <span data-ttu-id="854ef-107">有关详细信息，请参阅[如何：使用 EdmGen.exe 生成模型和映射文件](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)。</span><span class="sxs-lookup"><span data-stu-id="854ef-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="854ef-108">将基于现有数据库的实体框架模型添加到现有 Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="854ef-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>

1. <span data-ttu-id="854ef-109">上**项目**菜单上，单击**添加** > **新项**。</span><span class="sxs-lookup"><span data-stu-id="854ef-109">On the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="854ef-110">在中**模板**窗格中，单击**数据**类别中，并选择**ADO.NET 实体数据模型**。</span><span class="sxs-lookup"><span data-stu-id="854ef-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="854ef-111">输入模型名称，然后单击**添加**。</span><span class="sxs-lookup"><span data-stu-id="854ef-111">Enter the model name and then click **Add**.</span></span>

     <span data-ttu-id="854ef-112">将显示“[!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)]向导”的第一页。</span><span class="sxs-lookup"><span data-stu-id="854ef-112">The first page of the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard is displayed.</span></span>

4. <span data-ttu-id="854ef-113">在中**选择模型内容**对话框中，选择**从数据库生成**。</span><span class="sxs-lookup"><span data-stu-id="854ef-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="854ef-114">然后，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="854ef-114">Then click **Next**.</span></span>

5. <span data-ttu-id="854ef-115">单击**新的连接**按钮。</span><span class="sxs-lookup"><span data-stu-id="854ef-115">Click the **New Connection** button.</span></span>

6. <span data-ttu-id="854ef-116">在中**连接属性**对话框中，键入你的服务器名称、 选择身份验证方法中，键入数据库名称，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="854ef-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>

     <span data-ttu-id="854ef-117">**选择数据连接**对话框以数据库的连接设置更新。</span><span class="sxs-lookup"><span data-stu-id="854ef-117">The **Choose Your Data Connection** dialog box is updated with your database connection settings.</span></span>

7. <span data-ttu-id="854ef-118">絋粄**将实体连接设置保存为 App.Config 中：** 选中复选框。</span><span class="sxs-lookup"><span data-stu-id="854ef-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="854ef-119">然后，单击 **“下一步”**。</span><span class="sxs-lookup"><span data-stu-id="854ef-119">Then click **Next**.</span></span>

8. <span data-ttu-id="854ef-120">在中**选择数据库对象**对话框中，选择的所有数据库对象计划要在数据服务中公开。</span><span class="sxs-lookup"><span data-stu-id="854ef-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="854ef-121">数据服务不自动公开数据模型中包含的对象。</span><span class="sxs-lookup"><span data-stu-id="854ef-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="854ef-122">它们必须由服务本身显式公开。</span><span class="sxs-lookup"><span data-stu-id="854ef-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="854ef-123">有关详细信息，请参阅[数据服务配置](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="854ef-123">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>

9. <span data-ttu-id="854ef-124">单击**完成**以完成向导。</span><span class="sxs-lookup"><span data-stu-id="854ef-124">Click **Finish** to complete the wizard.</span></span>

     <span data-ttu-id="854ef-125">这将基于特定数据库创建默认数据模型。</span><span class="sxs-lookup"><span data-stu-id="854ef-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="854ef-126">[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]允许对数据模型进行自定义。</span><span class="sxs-lookup"><span data-stu-id="854ef-126">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] enables to customize the data model.</span></span> <span data-ttu-id="854ef-127">有关详细信息，请参阅[实体数据模型工具任务](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="854ef-127">For more information, see [Entity Data Model Tools Tasks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span></span>

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="854ef-128">使用新数据模型创建数据服务</span><span class="sxs-lookup"><span data-stu-id="854ef-128">To create the data service by using the new data model</span></span>

1. <span data-ttu-id="854ef-129">在 Visual Studio 中，打开代表数据模型的 .edmx 文件。</span><span class="sxs-lookup"><span data-stu-id="854ef-129">In Visual Studio, open the .edmx file that represents the data model.</span></span>

2. <span data-ttu-id="854ef-130">在中**模型浏览器**，右键单击该模型，单击**属性**，然后记下实体容器的名称。</span><span class="sxs-lookup"><span data-stu-id="854ef-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>

3. <span data-ttu-id="854ef-131">在中**解决方案资源管理器**，右键单击名称你[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]项目，然后依次**添加** > **新项**。</span><span class="sxs-lookup"><span data-stu-id="854ef-131">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add** > **New Item**.</span></span>

4. <span data-ttu-id="854ef-132">在中**添加新项**对话框中，选择**WCF 数据服务**中的模板**Web**类别。</span><span class="sxs-lookup"><span data-stu-id="854ef-132">In the **Add New Item** dialog box, select the **WCF Data Service** template in the **Web** category.</span></span>

   ![在 Visual Studio 2015 中的 WCF 数据服务项模板](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="854ef-134">**WCF 数据服务**模板现已推出 Visual Studio 2015，但未在 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="854ef-134">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

5. <span data-ttu-id="854ef-135">提供服务的名称，然后单击**确定**。</span><span class="sxs-lookup"><span data-stu-id="854ef-135">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="854ef-136">Visual Studio 将为新服务创建 XML 标记和代码文件。</span><span class="sxs-lookup"><span data-stu-id="854ef-136">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="854ef-137">默认情况下，代码编辑器窗口将打开。</span><span class="sxs-lookup"><span data-stu-id="854ef-137">By default, the code-editor window opens.</span></span>

6. <span data-ttu-id="854ef-138">在数据服务代码中，将用于定义数据服务的类定义中的注释 `/* TODO: put your data source class name here */` 替换为从 <xref:System.Data.Objects.ObjectContext> 类继承且作为数据模型的实体容器的类型，如步骤 2 中所述。</span><span class="sxs-lookup"><span data-stu-id="854ef-138">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>

7. <span data-ttu-id="854ef-139">在数据服务代码中，启用经过授权的客户端来访问数据服务公开的实体集。</span><span class="sxs-lookup"><span data-stu-id="854ef-139">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="854ef-140">有关详细信息，请参阅[创建数据服务](../../../../docs/framework/data/wcf/creating-the-data-service.md)。</span><span class="sxs-lookup"><span data-stu-id="854ef-140">For more information, see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>

8. <span data-ttu-id="854ef-141">若要使用 Web 浏览器测试 Northwind.svc 数据服务，请按照本主题中的说明[从 Web 浏览器访问服务](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)。</span><span class="sxs-lookup"><span data-stu-id="854ef-141">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="854ef-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="854ef-142">See also</span></span>

- [<span data-ttu-id="854ef-143">定义 WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="854ef-143">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
- [<span data-ttu-id="854ef-144">数据服务提供程序</span><span class="sxs-lookup"><span data-stu-id="854ef-144">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="854ef-145">如何：创建数据服务使用反射提供程序</span><span class="sxs-lookup"><span data-stu-id="854ef-145">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="854ef-146">如何：创建使用 LINQ to SQL 数据源的数据服务</span><span class="sxs-lookup"><span data-stu-id="854ef-146">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
