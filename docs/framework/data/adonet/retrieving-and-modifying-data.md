---
title: 在 ADO.NET 中检索和修改数据
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: bf26cd216b456e912dbaf0019114ea8e60b439a1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097612"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="5ae38-102">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="5ae38-102">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="5ae38-103">任何数据库应用程序的一项主要功能是连接数据源并检索数据源中包含的数据。</span><span class="sxs-lookup"><span data-stu-id="5ae38-103">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="5ae38-104">ADO.NET 的.NET Framework 数据提供程序充当应用程序和数据源之间的桥梁使您可以执行命令以及使用检索数据**DataReader**或**DataAdapter**.</span><span class="sxs-lookup"><span data-stu-id="5ae38-104">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="5ae38-105">任何数据库应用程序的一项关键功能是更新数据库中存储的数据的能力。</span><span class="sxs-lookup"><span data-stu-id="5ae38-105">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="5ae38-106">在 ADO.NET 中，更新数据时会使用**DataAdapter**并<xref:System.Data.DataSet>，和**命令**对象; 并且它还可能会使用事务。</span><span class="sxs-lookup"><span data-stu-id="5ae38-106">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ae38-107">本节内容</span><span class="sxs-lookup"><span data-stu-id="5ae38-107">In This Section</span></span>  
 [<span data-ttu-id="5ae38-108">连接到数据源</span><span class="sxs-lookup"><span data-stu-id="5ae38-108">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 <span data-ttu-id="5ae38-109">说明如何建立到数据源的连接及如何使用连接事件。</span><span class="sxs-lookup"><span data-stu-id="5ae38-109">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="5ae38-110">连接字符串</span><span class="sxs-lookup"><span data-stu-id="5ae38-110">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 <span data-ttu-id="5ae38-111">包含说明使用连接字符串（包括连接字符串关键字、安全信息以及存储和检索连接字符串）的各个方面的主题。</span><span class="sxs-lookup"><span data-stu-id="5ae38-111">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="5ae38-112">连接池</span><span class="sxs-lookup"><span data-stu-id="5ae38-112">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 <span data-ttu-id="5ae38-113">描述 .NET Framework 数据提供程序的连接池。</span><span class="sxs-lookup"><span data-stu-id="5ae38-113">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="5ae38-114">命令和参数</span><span class="sxs-lookup"><span data-stu-id="5ae38-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 <span data-ttu-id="5ae38-115">包含说明如何创建命令和命令生成器、配置参数以及如何执行命令来检索和修改数据的主题。</span><span class="sxs-lookup"><span data-stu-id="5ae38-115">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="5ae38-116">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="5ae38-116">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 <span data-ttu-id="5ae38-117">包含说明 DataReader、DataAdapter、参数、处理 DataAdapter 事件和执行批操作的主题。</span><span class="sxs-lookup"><span data-stu-id="5ae38-117">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="5ae38-118">事务和并发性</span><span class="sxs-lookup"><span data-stu-id="5ae38-118">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 <span data-ttu-id="5ae38-119">包含说明如何执行本地事务、分布式事务及使用开放式并发的主题。</span><span class="sxs-lookup"><span data-stu-id="5ae38-119">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="5ae38-120">检索标识或自动编号值</span><span class="sxs-lookup"><span data-stu-id="5ae38-120">Retrieving Identity or Autonumber Values</span></span>](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="5ae38-121">提供的映射生成的值示例**标识**或为 SQL Server 表中的列**自动编号**字段在 Microsoft Access 表中，向表中插入行的列。</span><span class="sxs-lookup"><span data-stu-id="5ae38-121">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="5ae38-122">讨论在 `DataTable` 中合并标识值。</span><span class="sxs-lookup"><span data-stu-id="5ae38-122">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="5ae38-123">检索二进制数据</span><span class="sxs-lookup"><span data-stu-id="5ae38-123">Retrieving Binary Data</span></span>](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 <span data-ttu-id="5ae38-124">说明如何使用 `CommandBehavior` 检索二进制数据或大数据结构。</span><span class="sxs-lookup"><span data-stu-id="5ae38-124">Describes how to retrieve binary data or large data structures using `CommandBehavior`.</span></span>`SequentialAccess` <span data-ttu-id="5ae38-125">若要修改的默认行为`DataReader`。</span><span class="sxs-lookup"><span data-stu-id="5ae38-125">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="5ae38-126">使用存储过程修改数据</span><span class="sxs-lookup"><span data-stu-id="5ae38-126">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="5ae38-127">说明如何使用存储过程的输入参数和输出参数在数据库中插入行，同时返回新标识值。</span><span class="sxs-lookup"><span data-stu-id="5ae38-127">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="5ae38-128">检索数据库架构信息</span><span class="sxs-lookup"><span data-stu-id="5ae38-128">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 <span data-ttu-id="5ae38-129">说明如何获取可用数据库或编录、数据库中的表和视图、表存在的约束以及数据源中的其他架构信息。</span><span class="sxs-lookup"><span data-stu-id="5ae38-129">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="5ae38-130">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="5ae38-130">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="5ae38-131">描述提供程序工厂模型及说明如何在 `System.Data.Common` 命名空间中使用基类。</span><span class="sxs-lookup"><span data-stu-id="5ae38-131">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="5ae38-132">ADO.NET 中的数据跟踪</span><span class="sxs-lookup"><span data-stu-id="5ae38-132">Data Tracing in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-tracing.md)  
 <span data-ttu-id="5ae38-133">说明 ADO.NET 如何提供内置的数据跟踪功能。</span><span class="sxs-lookup"><span data-stu-id="5ae38-133">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="5ae38-134">性能计数器</span><span class="sxs-lookup"><span data-stu-id="5ae38-134">Performance Counters</span></span>](../../../../docs/framework/data/adonet/performance-counters.md)  
 <span data-ttu-id="5ae38-135">说明 `SqlClient` 和 `OracleClient` 可用的性能计数器。</span><span class="sxs-lookup"><span data-stu-id="5ae38-135">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="5ae38-136">异步编程</span><span class="sxs-lookup"><span data-stu-id="5ae38-136">Asynchronous Programming</span></span>](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 <span data-ttu-id="5ae38-137">介绍了 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 对异步编程的支持。</span><span class="sxs-lookup"><span data-stu-id="5ae38-137">Describes [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="5ae38-138">SqlClient 流支持</span><span class="sxs-lookup"><span data-stu-id="5ae38-138">SqlClient Streaming Support</span></span>](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 <span data-ttu-id="5ae38-139">讨论如何编写应用程序的流数据从 SQL Server 而无需再对其完全加载到内存中。</span><span class="sxs-lookup"><span data-stu-id="5ae38-139">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ae38-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="5ae38-140">See also</span></span>

- [<span data-ttu-id="5ae38-141">ADO.NET 中的数据类型映射</span><span class="sxs-lookup"><span data-stu-id="5ae38-141">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="5ae38-142">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="5ae38-142">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="5ae38-143">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="5ae38-143">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="5ae38-144">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="5ae38-144">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="5ae38-145">ADO.NET 托管提供程序和 DataSet 开发人员中心</span><span class="sxs-lookup"><span data-stu-id="5ae38-145">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
