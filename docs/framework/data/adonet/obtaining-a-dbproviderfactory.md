---
title: 获取 DbProviderFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: dd4bca48c35b9b636a96fe5d4a724272abc4f71d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934401"
---
# <a name="obtaining-a-dbproviderfactory"></a><span data-ttu-id="f9929-102">获取 DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="f9929-102">Obtaining a DbProviderFactory</span></span>
<span data-ttu-id="f9929-103">获取 <xref:System.Data.Common.DbProviderFactory> 的过程涉及将有关数据提供程序的信息传递给 <xref:System.Data.Common.DbProviderFactories> 类。</span><span class="sxs-lookup"><span data-stu-id="f9929-103">The process of obtaining a <xref:System.Data.Common.DbProviderFactory> involves passing information about a data provider to the <xref:System.Data.Common.DbProviderFactories> class.</span></span> <span data-ttu-id="f9929-104"><xref:System.Data.Common.DbProviderFactories.GetFactory%2A> 方法将基于此信息创建一个强类型提供程序工厂。</span><span class="sxs-lookup"><span data-stu-id="f9929-104">Based on this information, the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method creates a strongly typed provider factory.</span></span> <span data-ttu-id="f9929-105">例如，若要创建 <xref:System.Data.SqlClient.SqlClientFactory>，可以向 `GetFactory` 传递一个将提供程序名称指定为“System.Data.SqlClient”的字符串。</span><span class="sxs-lookup"><span data-stu-id="f9929-105">For example, to create a <xref:System.Data.SqlClient.SqlClientFactory>, you can pass `GetFactory` a string with the provider name specified as "System.Data.SqlClient".</span></span> <span data-ttu-id="f9929-106">`GetFactory` 的其他重载采用 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="f9929-106">The other overload of `GetFactory` takes a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="f9929-107">创建该提供程序工厂后，可以使用其方法创建其他对象。</span><span class="sxs-lookup"><span data-stu-id="f9929-107">Once you create the provider factory, you can then use its methods to create additional objects.</span></span> <span data-ttu-id="f9929-108">`SqlClientFactory` 的部分方法包括 <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>、<xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A> 和 <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>。</span><span class="sxs-lookup"><span data-stu-id="f9929-108">Some of the methods of a `SqlClientFactory` include <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, and <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9929-109">.NET Framework <xref:System.Data.OracleClient.OracleClientFactory>、<xref:System.Data.Odbc.OdbcFactory> 和 <xref:System.Data.OleDb.OleDbFactory> 类也提供类似功能。</span><span class="sxs-lookup"><span data-stu-id="f9929-109">The .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, and <xref:System.Data.OleDb.OleDbFactory> classes also provide similar functionality.</span></span>  
  
## <a name="registering-dbproviderfactories"></a><span data-ttu-id="f9929-110">注册 DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="f9929-110">Registering DbProviderFactories</span></span>  
 <span data-ttu-id="f9929-111">支持基于工厂的类的每个 .NET Framework 数据提供程序在本地计算机上的**machine.config**文件的**DbProviderFactories**节中注册配置信息。</span><span class="sxs-lookup"><span data-stu-id="f9929-111">Each .NET Framework data provider that supports a factory-based class registers configuration information in the **DbProviderFactories** section of the **machine.config** file on the local computer.</span></span> <span data-ttu-id="f9929-112">下面的配置文件片断演示 <xref:System.Data.SqlClient> 的语法和格式。</span><span class="sxs-lookup"><span data-stu-id="f9929-112">The following configuration file fragment shows the syntax and format for <xref:System.Data.SqlClient>.</span></span>  
  
```xml  
<system.data>  
  <DbProviderFactories>  
    <add name="SqlClient Data Provider"  
     invariant="System.Data.SqlClient"   
     description=".Net Framework Data Provider for SqlServer"   
     type="System.Data.SqlClient.SqlClientFactory, System.Data,   
     Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
    />  
  </DbProviderFactories>  
</system.data>  
```  
  
 <span data-ttu-id="f9929-113">**固定**属性标识基础数据提供程序。</span><span class="sxs-lookup"><span data-stu-id="f9929-113">The **invariant** attribute identifies the underlying data provider.</span></span> <span data-ttu-id="f9929-114">在创建新工厂时也使用这种由三部分组成的命名语法，并用于标识应用程序配置文件中的提供程序，以便在运行时能够检索提供程序名称及其关联的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="f9929-114">This three-part naming syntax is also used when creating a new factory and for identifying the provider in an application configuration file so that the provider name, along with its associated connection string, can be retrieved at run time.</span></span>  
  
## <a name="retrieving-provider-information"></a><span data-ttu-id="f9929-115">检索提供程序信息</span><span class="sxs-lookup"><span data-stu-id="f9929-115">Retrieving Provider Information</span></span>  
 <span data-ttu-id="f9929-116">使用 <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> 方法可以检索有关安装在本地计算机上的所有数据提供程序的信息。</span><span class="sxs-lookup"><span data-stu-id="f9929-116">You can retrieve information about all of the data providers installed on the local computer by using the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method.</span></span> <span data-ttu-id="f9929-117">它返回一个<xref:System.Data.DataTable>名为**DbProviderFactories**的, 其中包含下表中所述的列。</span><span class="sxs-lookup"><span data-stu-id="f9929-117">It returns a <xref:System.Data.DataTable> named **DbProviderFactories** that contains the columns described in the following table.</span></span>  
  
|<span data-ttu-id="f9929-118">列序号</span><span class="sxs-lookup"><span data-stu-id="f9929-118">Column ordinal</span></span>|<span data-ttu-id="f9929-119">列名</span><span class="sxs-lookup"><span data-stu-id="f9929-119">Column name</span></span>|<span data-ttu-id="f9929-120">示例输出</span><span class="sxs-lookup"><span data-stu-id="f9929-120">Example output</span></span>|<span data-ttu-id="f9929-121">描述</span><span class="sxs-lookup"><span data-stu-id="f9929-121">Description</span></span>|  
|--------------------|-----------------|--------------------|-----------------|  
|<span data-ttu-id="f9929-122">0</span><span class="sxs-lookup"><span data-stu-id="f9929-122">0</span></span>|<span data-ttu-id="f9929-123">**Name**</span><span class="sxs-lookup"><span data-stu-id="f9929-123">**Name**</span></span>|<span data-ttu-id="f9929-124">SqlClient Data Provider</span><span class="sxs-lookup"><span data-stu-id="f9929-124">SqlClient Data Provider</span></span>|<span data-ttu-id="f9929-125">数据提供程序的可读名称</span><span class="sxs-lookup"><span data-stu-id="f9929-125">Readable name for the data provider</span></span>|  
|<span data-ttu-id="f9929-126">1</span><span class="sxs-lookup"><span data-stu-id="f9929-126">1</span></span>|<span data-ttu-id="f9929-127">**说明**</span><span class="sxs-lookup"><span data-stu-id="f9929-127">**Description**</span></span>|<span data-ttu-id="f9929-128">.Net Framework Data Provider for SqlServer</span><span class="sxs-lookup"><span data-stu-id="f9929-128">.Net Framework Data Provider for SqlServer</span></span>|<span data-ttu-id="f9929-129">数据提供程序的可读说明</span><span class="sxs-lookup"><span data-stu-id="f9929-129">Readable description of the data provider</span></span>|  
|<span data-ttu-id="f9929-130">2</span><span class="sxs-lookup"><span data-stu-id="f9929-130">2</span></span>|<span data-ttu-id="f9929-131">**InvariantName**</span><span class="sxs-lookup"><span data-stu-id="f9929-131">**InvariantName**</span></span>|<span data-ttu-id="f9929-132">System.Data.SqlClient</span><span class="sxs-lookup"><span data-stu-id="f9929-132">System.Data.SqlClient</span></span>|<span data-ttu-id="f9929-133">数据提供程序的名称，可用于以编程方式引用该数据提供程序</span><span class="sxs-lookup"><span data-stu-id="f9929-133">Name that can be used programmatically to refer to the data provider</span></span>|  
|<span data-ttu-id="f9929-134">3</span><span class="sxs-lookup"><span data-stu-id="f9929-134">3</span></span>|<span data-ttu-id="f9929-135">**AssemblyQualifiedName**</span><span class="sxs-lookup"><span data-stu-id="f9929-135">**AssemblyQualifiedName**</span></span>|<span data-ttu-id="f9929-136">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="f9929-136">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span></span>|<span data-ttu-id="f9929-137">工厂类的完全限定名称，其中包含实例化对象所需的足够信息</span><span class="sxs-lookup"><span data-stu-id="f9929-137">Fully qualified name of the factory class, which contains enough information to instantiate the object</span></span>|  
  
 <span data-ttu-id="f9929-138">使用此 `DataTable`，用户可以在运行时选择 <xref:System.Data.DataRow>。</span><span class="sxs-lookup"><span data-stu-id="f9929-138">This `DataTable` can be used to enable a user to select a <xref:System.Data.DataRow> at run time.</span></span> <span data-ttu-id="f9929-139">然后，可以将所选的 `DataRow` 传递给 <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> 方法以创建强类型 <xref:System.Data.Common.DbProviderFactory>。</span><span class="sxs-lookup"><span data-stu-id="f9929-139">The selected `DataRow` can then be passed to the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method to create a strongly typed <xref:System.Data.Common.DbProviderFactory>.</span></span> <span data-ttu-id="f9929-140">可以将所选的 <xref:System.Data.DataRow> 传递给 `GetFactory` 方法以创建需要的 `DbProviderFactory` 对象。</span><span class="sxs-lookup"><span data-stu-id="f9929-140">A selected <xref:System.Data.DataRow> can be passed to the `GetFactory` method to create the desired `DbProviderFactory` object.</span></span>  
  
## <a name="listing-the-installed-provider-factory-classes"></a><span data-ttu-id="f9929-141">列出已安装的提供程序工厂类</span><span class="sxs-lookup"><span data-stu-id="f9929-141">Listing the Installed Provider Factory Classes</span></span>  
 <span data-ttu-id="f9929-142">此示例演示如何使用 <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> 方法返回一个包含有关已安装提供程序信息的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="f9929-142">This example demonstrates how to use the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method to return a <xref:System.Data.DataTable> containing information about the installed providers.</span></span> <span data-ttu-id="f9929-143">代码遍历 `DataTable` 中的每一行，在控制台窗口中显示每个已安装的提供程序的信息。</span><span class="sxs-lookup"><span data-stu-id="f9929-143">The code iterates through each row in the `DataTable`, displaying information for each installed provider in the console window.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a><span data-ttu-id="f9929-144">使用应用程序配置文件存储工厂信息</span><span class="sxs-lookup"><span data-stu-id="f9929-144">Using Application Configuration Files to Store Factory Information</span></span>  
 <span data-ttu-id="f9929-145">用于工厂的设计模式需要在应用程序配置文件中存储提供程序和连接字符串信息, 如 Windows 应用程序的**app.config**和用于 ASP.NET 应用程序的 web.config。</span><span class="sxs-lookup"><span data-stu-id="f9929-145">The design pattern used for working with factories entails storing provider and connection string information in an application configuration file, such as **app.config** for a Windows application, and **web.config** for an ASP.NET application.</span></span>  
  
 <span data-ttu-id="f9929-146">下面的配置文件片段演示如何保存两个命名连接字符串：用于连接到 SQL Server 中 Northwind 数据库的“NorthwindSQL”和用于连接到 Access/Jet 中 Northwind 数据库的“NorthwindAccess”。</span><span class="sxs-lookup"><span data-stu-id="f9929-146">The following configuration file fragment demonstrates how to save two named connection strings, "NorthwindSQL" for a connection to the Northwind database in SQL Server, and "NorthwindAccess" for a connection to the Northwind database in Access/Jet.</span></span> <span data-ttu-id="f9929-147">**固定**名称用于**providerName**特性。</span><span class="sxs-lookup"><span data-stu-id="f9929-147">The **invariant** name is used for the **providerName** attribute.</span></span>  
  
```xml  
<configuration>  
  <connectionStrings>  
    <clear/>  
    <add name="NorthwindSQL"   
     providerName="System.Data.SqlClient"   
     connectionString=  
     "Data Source=MSSQL1;Initial Catalog=Northwind;Integrated Security=true"  
    />  
  
    <add name="NorthwindAccess"   
     providerName="System.Data.OleDb"   
     connectionString=  
     "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Data\Northwind.mdb;"  
    />  
  </connectionStrings>  
</configuration>  
```  
  
### <a name="retrieving-a-connection-string-by-provider-name"></a><span data-ttu-id="f9929-148">按提供程序名称检索连接字符串</span><span class="sxs-lookup"><span data-stu-id="f9929-148">Retrieving a Connection String by Provider Name</span></span>  
 <span data-ttu-id="f9929-149">若要创建提供程序工厂，必须提供连接字符串和提供程序名称。</span><span class="sxs-lookup"><span data-stu-id="f9929-149">In order to create a provider factory, you must supply a connection string as well as the provider name.</span></span> <span data-ttu-id="f9929-150">此示例演示如何通过以固定格式 "system.string" 传递提供程序名称来从应用程序配置文件中检索连接字符串。</span><span class="sxs-lookup"><span data-stu-id="f9929-150">This example demonstrates how to retrieve a connection string from an application configuration file by passing the provider name in the invariant format "*System.Data.ProviderName*".</span></span> <span data-ttu-id="f9929-151">代码循环访问 <xref:System.Configuration.ConnectionStringSettingsCollection>。</span><span class="sxs-lookup"><span data-stu-id="f9929-151">The code iterates through the <xref:System.Configuration.ConnectionStringSettingsCollection>.</span></span> <span data-ttu-id="f9929-152">成功时代码返回 <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A>；否则返回 `null`（在 Visual Basic 中为 `Nothing`）。</span><span class="sxs-lookup"><span data-stu-id="f9929-152">It returns the <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> on success; otherwise `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="f9929-153">如果提供程序有多项，则返回找到的第一项。</span><span class="sxs-lookup"><span data-stu-id="f9929-153">If there are multiple entries for a provider, the first one found is returned.</span></span> <span data-ttu-id="f9929-154">有关从配置文件中检索连接字符串的详细信息和示例, 请参阅[连接字符串和配置文件](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="f9929-154">For more information and examples of retrieving connection strings from configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f9929-155">若要此代码正确运行，需要引用 `System.Configuration.dll`。</span><span class="sxs-lookup"><span data-stu-id="f9929-155">A reference to `System.Configuration.dll` is required in order for the code to run.</span></span>  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a><span data-ttu-id="f9929-156">创建 DbProviderFactory 和 DbConnection</span><span class="sxs-lookup"><span data-stu-id="f9929-156">Creating the DbProviderFactory and DbConnection</span></span>  
 <span data-ttu-id="f9929-157">此示例演示如何通过以 " <xref:System.Data.Common.DbProviderFactory> system.string <xref:System.Data.Common.DbConnection> " 格式和连接字符串的形式传递提供程序名称来创建和对象。</span><span class="sxs-lookup"><span data-stu-id="f9929-157">This example demonstrates how to create a <xref:System.Data.Common.DbProviderFactory> and <xref:System.Data.Common.DbConnection> object by passing it the provider name in the format "*System.Data.ProviderName*" and a connection string.</span></span> <span data-ttu-id="f9929-158">成功时返回 `DbConnection` 对象；出错时返回 `null`（在 Visual Basic 中为 `Nothing`）。</span><span class="sxs-lookup"><span data-stu-id="f9929-158">A `DbConnection` object is returned on success; `null` (`Nothing` in Visual Basic) on any error.</span></span>  
  
 <span data-ttu-id="f9929-159">代码通过调用 `DbProviderFactory` 获取 <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>。</span><span class="sxs-lookup"><span data-stu-id="f9929-159">The code obtains the `DbProviderFactory` by calling <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>.</span></span> <span data-ttu-id="f9929-160">然后，<xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> 方法创建 <xref:System.Data.Common.DbConnection> 对象并将 <xref:System.Data.Common.DbConnection.ConnectionString%2A> 属性设置为连接字符串。</span><span class="sxs-lookup"><span data-stu-id="f9929-160">Then the <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> method creates the <xref:System.Data.Common.DbConnection> object and the <xref:System.Data.Common.DbConnection.ConnectionString%2A> property is set to the connection string.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f9929-161">请参阅</span><span class="sxs-lookup"><span data-stu-id="f9929-161">See also</span></span>

- [<span data-ttu-id="f9929-162">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="f9929-162">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [<span data-ttu-id="f9929-163">连接字符串</span><span class="sxs-lookup"><span data-stu-id="f9929-163">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)
- <span data-ttu-id="f9929-164">[使用配置类](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f9929-164">[Using the Configuration Classes](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))</span></span>
- [<span data-ttu-id="f9929-165">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="f9929-165">ADO.NET Overview</span></span>](ado-net-overview.md)
