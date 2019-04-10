---
title: 命令和参数
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: a769e8cbd5138e78136df018abe058ac6c568951
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198122"
---
# <a name="commands-and-parameters"></a><span data-ttu-id="2c445-102">命令和参数</span><span class="sxs-lookup"><span data-stu-id="2c445-102">Commands and Parameters</span></span>
<span data-ttu-id="2c445-103">建立与数据源的连接后，可以使用 <xref:System.Data.Common.DbCommand> 对象来执行命令并从数据源中返回结果。</span><span class="sxs-lookup"><span data-stu-id="2c445-103">After establishing a connection to a data source, you can execute commands and return results from the data source using a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="2c445-104">您可以使用命令构造函数之一为要使用的 .NET Framework 数据提供程序创建命令。</span><span class="sxs-lookup"><span data-stu-id="2c445-104">You can create a command using one of the command constructors for the .NET Framework data provider you are working with.</span></span> <span data-ttu-id="2c445-105">构造函数可以采用可选自变量，如要在数据源中执行的 SQL 语句、<xref:System.Data.Common.DbConnection> 对象或 <xref:System.Data.Common.DbTransaction> 对象。</span><span class="sxs-lookup"><span data-stu-id="2c445-105">Constructors can take optional arguments, such as an SQL statement to execute at the data source, a <xref:System.Data.Common.DbConnection> object, or a <xref:System.Data.Common.DbTransaction> object.</span></span> <span data-ttu-id="2c445-106">您也可以将这些对象配置为命令的属性。</span><span class="sxs-lookup"><span data-stu-id="2c445-106">You can also configure those objects as properties of the command.</span></span> <span data-ttu-id="2c445-107">也可以使用 <xref:System.Data.Common.DbConnection.CreateCommand%2A> 对象的 `DbConnection` 方法创建用于特定连接的命令。</span><span class="sxs-lookup"><span data-stu-id="2c445-107">You can also create a command for a particular connection using the <xref:System.Data.Common.DbConnection.CreateCommand%2A> method of a `DbConnection` object.</span></span> <span data-ttu-id="2c445-108">由命令执行的 SQL 语句可以使用 <xref:System.Data.Common.DbCommand.CommandText%2A> 属性进行配置。</span><span class="sxs-lookup"><span data-stu-id="2c445-108">The SQL statement being executed by the command can be configured using the <xref:System.Data.Common.DbCommand.CommandText%2A> property.</span></span>  
  
 <span data-ttu-id="2c445-109">随 .NET Framework 提供的每个 .NET Framework 数据提供程序都具有一个 `Command` 对象。</span><span class="sxs-lookup"><span data-stu-id="2c445-109">Each .NET Framework data provider included with the .NET Framework has a `Command` object.</span></span> <span data-ttu-id="2c445-110">适用于 OLE DB 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OleDb.OleDbCommand> 对象，适用于 SQL Server 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.SqlClient.SqlCommand> 对象，适用于 ODBC 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.Odbc.OdbcCommand> 对象，适用于 Oracle 的 .NET Framework 数据提供程序包括一个 <xref:System.Data.OracleClient.OracleCommand> 对象。</span><span class="sxs-lookup"><span data-stu-id="2c445-110">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c445-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="2c445-111">In This Section</span></span>  
 [<span data-ttu-id="2c445-112">执行命令</span><span class="sxs-lookup"><span data-stu-id="2c445-112">Executing a Command</span></span>](../../../../docs/framework/data/adonet/executing-a-command.md)  
 <span data-ttu-id="2c445-113">说明 ADO.NET `Command` 对象以及如何使用该对象对数据源执行查询和命令。</span><span class="sxs-lookup"><span data-stu-id="2c445-113">Describes the ADO.NET `Command` object and how to use it to execute queries and commands against a data source.</span></span>  
  
 [<span data-ttu-id="2c445-114">配置参数和参数数据类型</span><span class="sxs-lookup"><span data-stu-id="2c445-114">Configuring Parameters and Parameter Data Types</span></span>](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 <span data-ttu-id="2c445-115">说明如何使用 `Command` 参数，包括方向、数据类型和参数语法。</span><span class="sxs-lookup"><span data-stu-id="2c445-115">Describes working with `Command` parameters, including direction, data types, and parameter syntax.</span></span>  
  
 [<span data-ttu-id="2c445-116">使用 CommandBuilder 生成命令</span><span class="sxs-lookup"><span data-stu-id="2c445-116">Generating Commands with CommandBuilders</span></span>](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md)  
 <span data-ttu-id="2c445-117">说明如何使用命令生成器为具有单表 SELECT 命令的 `DataAdapter` 自动生成 INSERT、UPDATE 和 DELETE 命令。</span><span class="sxs-lookup"><span data-stu-id="2c445-117">Describes how to use command builders to automatically generate INSERT, UPDATE, and DELETE commands for a `DataAdapter` that has a single-table SELECT command.</span></span>  
  
 [<span data-ttu-id="2c445-118">从数据库获取单一值</span><span class="sxs-lookup"><span data-stu-id="2c445-118">Obtaining a Single Value from a Database</span></span>](../../../../docs/framework/data/adonet/obtaining-a-single-value-from-a-database.md)  
 <span data-ttu-id="2c445-119">说明如何使用 `ExecuteScalar`对象的 `Command` 方法从数据库查询中返回单个值。</span><span class="sxs-lookup"><span data-stu-id="2c445-119">Describes how to use the `ExecuteScalar` method of a `Command` object to return a single value from a database query.</span></span>  
  
 [<span data-ttu-id="2c445-120">使用命令修改数据</span><span class="sxs-lookup"><span data-stu-id="2c445-120">Using Commands to Modify Data</span></span>](../../../../docs/framework/data/adonet/using-commands-to-modify-data.md)  
 <span data-ttu-id="2c445-121">说明如何使用数据提供程序来执行存储过程或数据定义语言 (DDL) 语句。</span><span class="sxs-lookup"><span data-stu-id="2c445-121">Describes how to use a data provider to execute stored procedures or data definition language (DDL) statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c445-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="2c445-122">See also</span></span>

- [<span data-ttu-id="2c445-123">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="2c445-123">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="2c445-124">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="2c445-124">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="2c445-125">连接到数据源</span><span class="sxs-lookup"><span data-stu-id="2c445-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [<span data-ttu-id="2c445-126">ADO.NET 托管提供程序和 DataSet 开发人员中心</span><span class="sxs-lookup"><span data-stu-id="2c445-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
