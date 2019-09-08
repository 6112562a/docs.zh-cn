---
title: 下载示例数据库 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: c67ee699cf594f476a728c7345b47b0c32dea7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795174"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a><span data-ttu-id="018d3-102">下载示例数据库 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="018d3-102">Downloading Sample Databases (LINQ to DataSet)</span></span>
<span data-ttu-id="018d3-103">LINQ to DataSet 文档中的示例和演练使用 AdventureWorks 示例数据库。</span><span class="sxs-lookup"><span data-stu-id="018d3-103">The samples and walkthroughs in the LINQ to DataSet documentation use the AdventureWorks sample database.</span></span> <span data-ttu-id="018d3-104">您可以从 Microsoft 下载站点免费下载此产品。</span><span class="sxs-lookup"><span data-stu-id="018d3-104">You can download this product free of charge from the Microsoft download site.</span></span> <span data-ttu-id="018d3-105">LINQ to DataSet 文档中的示例和演练使用 SQL Server 作为数据存储。</span><span class="sxs-lookup"><span data-stu-id="018d3-105">The samples and walkthroughs in the LINQ to DataSet documentation use SQL Server as the data store.</span></span> <span data-ttu-id="018d3-106">免费提供的 SQL Server Express Edition 也可代替 SQL Server 用作数据存储区。</span><span class="sxs-lookup"><span data-stu-id="018d3-106">SQL Server Express Edition, which is available without charge, can also be used as the data store instead of SQL Server.</span></span>  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a><span data-ttu-id="018d3-107">下载并安装 AdventureWorks 数据库</span><span class="sxs-lookup"><span data-stu-id="018d3-107">Downloading and Installing the AdventureWorks Database</span></span>  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a><span data-ttu-id="018d3-108">下载和安装适用于 SQL Server 的 AdventureWorks 示例数据库</span><span class="sxs-lookup"><span data-stu-id="018d3-108">To download and install the AdventureWorks sample database for SQL Server</span></span>  
  
1. <span data-ttu-id="018d3-109">打开 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="018d3-109">Open Internet Explorer.</span></span>  
  
2. <span data-ttu-id="018d3-110">请参阅[SQL Server 2005 示例和示例数据库](https://go.microsoft.com/fwlink/?linkid=31046)网站。</span><span class="sxs-lookup"><span data-stu-id="018d3-110">Go to the [SQL Server 2005 Samples and Sample Databases](https://go.microsoft.com/fwlink/?linkid=31046) Web site.</span></span>  
  
3. <span data-ttu-id="018d3-111">按照说明下载适用于您的处理器类型的 AdventureWorks 示例数据库（如 AdventureWorksDB.msi）并将该 .MSI 文件保存到您的本地计算机。</span><span class="sxs-lookup"><span data-stu-id="018d3-111">Follow the instructions for downloading the AdventureWorks sample database for your processor type (such as AdventureWorksDB.msi), and save the .MSI file to your local computer.</span></span>  
  
4. <span data-ttu-id="018d3-112">如果您通过下载或在 SQL Server 安装过程中安装了先前版本的 AdventureWorks，则在运行 AdventureWorks.msi 之前必须删除该版本。</span><span class="sxs-lookup"><span data-stu-id="018d3-112">If you have a previous version of AdventureWorks installed from the download or during the SQL Server setup, you must remove it before running AdventureWorks.msi.</span></span>  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a><span data-ttu-id="018d3-113">删除先前下载的 AdventureWorks 示例数据库</span><span class="sxs-lookup"><span data-stu-id="018d3-113">To remove a previous download of an AdventureWorks sample database</span></span>  
  
1. <span data-ttu-id="018d3-114">放置 AdventureWorks 或 AdventureWorksDW 数据库。</span><span class="sxs-lookup"><span data-stu-id="018d3-114">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="018d3-115">从 "**添加或删除程序**" 中，选择**adventureworksdb.msi**或**Adventureworksbi.msi** ，然后单击 "**删除**"。</span><span class="sxs-lookup"><span data-stu-id="018d3-115">From **Add or Remove Programs**, select **AdventureWorksDB** or **AdventureWorksBI** and click **Remove**.</span></span>  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a><span data-ttu-id="018d3-116">删除先前使用安装程序安装的 AdventureWorks 示例数据库</span><span class="sxs-lookup"><span data-stu-id="018d3-116">To remove an AdventureWorks sample database previously installed using Setup</span></span>  
  
1. <span data-ttu-id="018d3-117">放置 AdventureWorks 或 AdventureWorksDW 数据库。</span><span class="sxs-lookup"><span data-stu-id="018d3-117">Drop the AdventureWorks or AdventureWorksDW database.</span></span>  
  
2. <span data-ttu-id="018d3-118">从 "**添加或删除程序**" 中，选择**Microsoft SQL Server 2005** ，然后单击 "**更改**"。</span><span class="sxs-lookup"><span data-stu-id="018d3-118">From **Add or Remove Programs**, select **Microsoft SQL Server 2005** and click **Change**.</span></span>  
  
3. <span data-ttu-id="018d3-119">从 "**组件选择**" 中选择 "**工作站组件**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="018d3-119">From **Component Selection**, select **Workstation Components** and then click **Next**.</span></span>  
  
4. <span data-ttu-id="018d3-120">从 **"欢迎使用 SQL Server 安装向导**" 中，单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="018d3-120">From **Welcome to the SQL Server Installation Wizard**, click **Next**.</span></span>  
  
5. <span data-ttu-id="018d3-121">单击 "**系统配置检查**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="018d3-121">From **System Configuration Check**, click **Next**.</span></span>  
  
6. <span data-ttu-id="018d3-122">在 "**更改或删除实例**" 中，单击 "**更改已安装的组件**"。</span><span class="sxs-lookup"><span data-stu-id="018d3-122">From **Change or Remove Instance**, click **Change Installed Components**.</span></span>  
  
7. <span data-ttu-id="018d3-123">从 "**功能选择**" 中，展开 "**文档"、"示例" 和 "示例数据库**" 节点。</span><span class="sxs-lookup"><span data-stu-id="018d3-123">From **Feature Selection**, expand the **Documentation, Samples, and Sample Databases** node.</span></span>  
  
8. <span data-ttu-id="018d3-124">选择 "**代码示例和应用程序**"。</span><span class="sxs-lookup"><span data-stu-id="018d3-124">Select **Sample Code and Applications**.</span></span> <span data-ttu-id="018d3-125">展开 "**示例数据库**"，选择要删除的示例数据库，然后选择 "**整个功能将不可用**"。</span><span class="sxs-lookup"><span data-stu-id="018d3-125">Expand **Sample Databases**, select the sample database to be removed, and select **Entire feature will be unavailable**.</span></span> <span data-ttu-id="018d3-126">单击 **“下一步”** 。</span><span class="sxs-lookup"><span data-stu-id="018d3-126">Click **Next**.</span></span>  
  
9. <span data-ttu-id="018d3-127">单击 "**安装**" 并完成安装向导。</span><span class="sxs-lookup"><span data-stu-id="018d3-127">Click **Install** and finish the installation wizard.</span></span>  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a><span data-ttu-id="018d3-128">将 AdventureWorks 示例数据库文件附加到 SQL Server 的实例</span><span class="sxs-lookup"><span data-stu-id="018d3-128">To attach the AdventureWorks sample database files to an instance of SQL Server</span></span>  
  
1. <span data-ttu-id="018d3-129">下载了文件示例数据库安装程序文件后，双击 " **adventureworksdb.msi** " 文件（或下载的文件）安装数据库。</span><span class="sxs-lookup"><span data-stu-id="018d3-129">After the file sample database installer file has downloaded, double-click the **AdventureWorksDB.msi** file (or the file you downloaded) to install the database.</span></span> <span data-ttu-id="018d3-130">默认情况下，该数据库安装在 c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data 位置。</span><span class="sxs-lookup"><span data-stu-id="018d3-130">By default, the database is installed at c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data.</span></span>  
  
2. <span data-ttu-id="018d3-131">通过执行下面的脚本 SQLCMD 或 SQL Server Management Studio，将 AdventureWorks 数据库文件附加到 SQL Server 的实例：</span><span class="sxs-lookup"><span data-stu-id="018d3-131">Attach the AdventureWorks database files to an instance of SQL Server by executing the following script SQLCMD or SQL Server Management Studio:</span></span>  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     <span data-ttu-id="018d3-132">如果您已将这些文件安装到其他驱动器或目录，则必须在执行 `sp_attach_db` 存储过程之前适当修改路径。</span><span class="sxs-lookup"><span data-stu-id="018d3-132">If you have installed these files to a different drive or directory, you must revise the paths appropriately before you execute the `sp_attach_db` stored procedure.</span></span>  
  
## <a name="downloading-sql-server-express-edition"></a><span data-ttu-id="018d3-133">下载 SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="018d3-133">Downloading SQL Server Express Edition</span></span>  
 <span data-ttu-id="018d3-134">LINQ to DataSet 节中的示例和演练使用 SQL Server 2005 作为数据存储，但可以改为改用 SQL Server Express Edition。</span><span class="sxs-lookup"><span data-stu-id="018d3-134">The samples and walkthroughs in the LINQ to DataSet section use SQL Server 2005 as the data store but can be modified to use SQL Server Express Edition, instead.</span></span> <span data-ttu-id="018d3-135">SQL Server Express Edition 免费提供，您可以利用应用程序重新发布它。</span><span class="sxs-lookup"><span data-stu-id="018d3-135">SQL Server Express Edition is available without charge, and you can redistribute it with applications.</span></span> <span data-ttu-id="018d3-136">如果你使用的是 Visual Studio，则 Pro 版和更高版本中将包含 SQL Server Express 版本。</span><span class="sxs-lookup"><span data-stu-id="018d3-136">If you are using Visual Studio, SQL Server Express Edition is included in the Pro and higher editions.</span></span>  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a><span data-ttu-id="018d3-137">下载并安装 SQL Server Express Edition</span><span class="sxs-lookup"><span data-stu-id="018d3-137">To download and install SQL Server Express Edition</span></span>  
  
1. <span data-ttu-id="018d3-138">启动 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="018d3-138">Start Internet Explorer.</span></span>  
  
2. <span data-ttu-id="018d3-139">请参阅[Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070)下载页。</span><span class="sxs-lookup"><span data-stu-id="018d3-139">Go to the  [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070) download page.</span></span>  
  
3. <span data-ttu-id="018d3-140">按照网站上的安装说明操作。</span><span class="sxs-lookup"><span data-stu-id="018d3-140">Follow the installation instructions on the Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="018d3-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="018d3-141">See also</span></span>

- [<span data-ttu-id="018d3-142">入门</span><span class="sxs-lookup"><span data-stu-id="018d3-142">Getting Started</span></span>](getting-started-linq-to-dataset.md)
