---
title: 如何：开发在 IIS 上运行的 WCF 数据服务
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 89be7aa8339a4edf6d6ab9c0c243e4320d2fdfa8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052975"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="4ae5e-102">如何：开发在 IIS 上运行的 WCF 数据服务</span><span class="sxs-lookup"><span data-stu-id="4ae5e-102">How to: Develop a WCF data service running on IIS</span></span>

<span data-ttu-id="4ae5e-103">本主题演示如何使用 WCF 数据服务创建一个数据服务，该服务基于 Internet Information Services （IIS）上运行的 ASP.NET Web 应用程序所承载的 Northwind 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-103">This topic shows how to use WCF Data Services to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="4ae5e-104">有关如何创建与 ASP.NET 开发服务器上运行的 ASP.NET Web 应用程序相同的 Northwind 数据服务的示例，请参阅[WCF 数据服务快速入门](quickstart-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="4ae5e-105">若要创建 Northwind 数据服务，您的本地计算机上必须已安装 Northwind 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="4ae5e-106">若要下载此示例数据库，请访问 [SQL Server 的示例数据库](https://go.microsoft.com/fwlink/?linkid=24758)下载页。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-106">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

<span data-ttu-id="4ae5e-107">本主题说明如何使用实体框架提供程序创建数据服务。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="4ae5e-108">还有其他一些数据服务提供程序可以使用。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-108">Other data services providers are available.</span></span> <span data-ttu-id="4ae5e-109">有关详细信息，请参阅[数据服务提供程序](data-services-providers-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-109">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>

<span data-ttu-id="4ae5e-110">在创建服务之后，您必须显式提供对数据服务资源的访问权限。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="4ae5e-111">有关详细信息，请参阅[如何：启用对数据服务](how-to-enable-access-to-the-data-service-wcf-data-services.md)的访问。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-111">For more information, see [How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="4ae5e-112">创建在 IIS 上运行的 ASP.NET web 应用程序</span><span class="sxs-lookup"><span data-stu-id="4ae5e-112">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="4ae5e-113">在 Visual Studio 的 "**文件**" 菜单上，选择 "**新建** > **项目**"。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-113">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="4ae5e-114">在 "**新建项目**" 对话框中，选择 "**已安装**的 > [**视觉对象C#** 或**Visual Basic**]" > **Web** "类别。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-114">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="4ae5e-115">选择 " **ASP.NET Web 应用程序**" 模板。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-115">Select the **ASP.NET Web Application** template.</span></span>

4. <span data-ttu-id="4ae5e-116">输入`NorthwindService`作为项目的名称。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-116">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="4ae5e-117">单击 **“确定”** 。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-117">Click **OK**.</span></span>

6. <span data-ttu-id="4ae5e-118">在 "**项目**" 菜单上，选择 " **NorthwindService 属性**"。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-118">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="4ae5e-119">选择 " **Web** " 选项卡，然后选择 "**使用本地 IIS Web 服务器**"。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-119">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="4ae5e-120">单击 "**创建虚拟目录**"，然后单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-120">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="4ae5e-121">从具有管理员权限的命令提示符中，根据操作系统，执行以下命令之一：</span><span class="sxs-lookup"><span data-stu-id="4ae5e-121">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="4ae5e-122">32 位系统：</span><span class="sxs-lookup"><span data-stu-id="4ae5e-122">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - <span data-ttu-id="4ae5e-123">64 位系统：</span><span class="sxs-lookup"><span data-stu-id="4ae5e-123">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="4ae5e-124">这样将确保在计算机上注册 Windows Communication Foundation (WCF)。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-124">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="4ae5e-125">从具有管理员权限的命令提示符中，根据操作系统，执行以下命令之一：</span><span class="sxs-lookup"><span data-stu-id="4ae5e-125">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="4ae5e-126">32 位系统：</span><span class="sxs-lookup"><span data-stu-id="4ae5e-126">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - <span data-ttu-id="4ae5e-127">64 位系统：</span><span class="sxs-lookup"><span data-stu-id="4ae5e-127">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="4ae5e-128">这将确保在计算机上安装了 WCF 之后，IIS 能够正常运行。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-128">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="4ae5e-129">您可能必须重启 IIS。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-129">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="4ae5e-130">当 ASP.NET 应用程序在 IIS7 上运行时，您还必须执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="4ae5e-130">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="4ae5e-131">打开 IIS 管理器并导航到 "**默认**网站" 下的 PhotoService 应用程序。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-131">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="4ae5e-132">在 "**功能视图**" 中，双击 "**身份验证**"。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-132">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="4ae5e-133">在 "**身份验证**" 页上，选择 "**匿名身份验证**"。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-133">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="4ae5e-134">在 "**操作**" 窗格中，单击 "**编辑**" 以设置匿名用户将连接到站点的安全主体。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-134">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="4ae5e-135">在 "**编辑匿名身份验证凭据**" 对话框中，选择 "**应用程序池标识**"。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-135">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="4ae5e-136">使用 Network Service 帐户时，您必须授予匿名用户与该账户关联的所有内部网络访问权限。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-136">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="4ae5e-137">通过在 Visual Studio 中使用 SQL Server Management Studio、sqlcmd.exe 实用工具或 Transact-SQL Editor，针对附加有 Northwind 数据库的 SQL Server 实例执行下面的 Transact-SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="4ae5e-137">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="4ae5e-138">这将在 SQL Server 实例中为用于运行 IIS 的 Windows 帐户创建一个登录名。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-138">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="4ae5e-139">这样，IIS 即可连接到 SQL Server 实例。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-139">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="4ae5e-140">附加 Northwind 数据库后，执行下面的 Transact-SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="4ae5e-140">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

    ```sql
    USE Northwind
    GO
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];
    GO
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]
    WITH DEFAULT_DATABASE=[Northwind];
    GO
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    ```

    <span data-ttu-id="4ae5e-141">这将为新登录名授予相应权限，使得 IIS 能够在 Northwind 数据库中读出和写入数据。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-141">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="4ae5e-142">定义数据模型</span><span class="sxs-lookup"><span data-stu-id="4ae5e-142">Define the data model</span></span>

1. <span data-ttu-id="4ae5e-143">在**解决方案资源管理器**中，右键单击 ASP.NET 项目的名称，然后单击 "**添加** > **新项**"。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-143">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="4ae5e-144">在 "**添加新项**" 对话框中，选择 " **ADO.NET 实体数据模型**"。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-144">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="4ae5e-145">对于数据模型的名称，请键入`Northwind.edmx`。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-145">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="4ae5e-146">在实体数据模型向导中，选择 "**从数据库生成**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-146">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="4ae5e-147">执行以下步骤之一，将数据模型连接到数据库，然后单击 "**下一步**"：</span><span class="sxs-lookup"><span data-stu-id="4ae5e-147">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="4ae5e-148">如果尚未配置数据库连接，请单击 "**新建连接**" 并创建一个新连接。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-148">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="4ae5e-149">有关详细信息，请参阅[如何：创建与 SQL Server 数据库](https://go.microsoft.com/fwlink/?LinkId=123631)的连接。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-149">For more information, see [How to: Create Connections to SQL Server Databases](https://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="4ae5e-150">此 SQL Server 实例必须附加了 Northwind 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-150">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="4ae5e-151">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="4ae5e-151">\- or -</span></span>

    - <span data-ttu-id="4ae5e-152">如果已配置一个连接到 Northwind 数据库的数据库连接，请从连接列表中选择该连接。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-152">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="4ae5e-153">在向导的最后一页中，选中数据库中所有表对应的复选框，并清除视图和存储过程对应的复选框。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-153">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="4ae5e-154">单击“完成”以关闭向导。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-154">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="4ae5e-155">创建数据服务</span><span class="sxs-lookup"><span data-stu-id="4ae5e-155">Create the data service</span></span>

1. <span data-ttu-id="4ae5e-156">在**解决方案资源管理器**中，右键单击 ASP.NET 项目的名称，然后单击 "**添加** > **新项**"。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-156">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="4ae5e-157">在 "**添加新项**" 对话框中，选择 " **WCF 数据服务**"。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-157">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Visual Studio 2015 中的 WCF 数据服务项模板](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="4ae5e-159">**WCF 数据服务**模板在 visual studio 2015 中提供，但在 visual studio 2017 中不可用。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-159">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="4ae5e-160">对于服务的名称，请输入`Northwind`。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-160">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="4ae5e-161">Visual Studio 将为新服务创建 XML 标记和代码文件。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-161">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="4ae5e-162">默认情况下，代码编辑器窗口将打开。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-162">By default, the code-editor window opens.</span></span> <span data-ttu-id="4ae5e-163">在**解决方案资源管理器**中，该服务的名称为 Northwind，svc.cs 或 .svc。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-163">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="4ae5e-164">在数据服务的代码中，用数据模型的实体容器的类型（在此示例中为 `/* TODO: put your data source class name here */`）替换定义数据服务的类定义中的注释 `NorthwindEntities`。</span><span class="sxs-lookup"><span data-stu-id="4ae5e-164">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="4ae5e-165">该类定义应如下所示：</span><span class="sxs-lookup"><span data-stu-id="4ae5e-165">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="4ae5e-166">请参阅</span><span class="sxs-lookup"><span data-stu-id="4ae5e-166">See also</span></span>

- [<span data-ttu-id="4ae5e-167">将数据公开为服务</span><span class="sxs-lookup"><span data-stu-id="4ae5e-167">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
