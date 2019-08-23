---
title: Oracle 和 ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 381f796bec31bece354001ad46bf5079381d1b3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914557"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="ef7d2-102">Oracle 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ef7d2-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="ef7d2-103"><xref:System.Data.OracleClient> 中的类型已过时。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="ef7d2-104">当前版本的 .NET Framework 仍支持这些类型，但以后的版本会将这些类型删除。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="ef7d2-105">Microsoft 建议您使用第三方 Oracle 提供程序。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="ef7d2-106">本节介绍特定于 Oracle .NET Framework 数据提供程序的功能和行为。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="ef7d2-107">用于 Oracle 的 .NET Framework 数据提供程序使用 oracle 客户端软件提供的 Oracle 调用接口 (OCI) 来访问 Oracle 数据库。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="ef7d2-108">数据提供程序的功能与 SQL Server、OLE DB 和 ODBC 的 .NET Framework 数据提供程序的功能类似。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="ef7d2-109">若要使用适用于 Oracle 的 .NET Framework 数据提供程序, 应用程序<xref:System.Data.OracleClient>必须引用命名空间, 如下所示:</span><span class="sxs-lookup"><span data-stu-id="ef7d2-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="ef7d2-110">在编译代码时还必须包括对该 DLL 的引用。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="ef7d2-111">例如，如果编译的是 C# 程序，命令行中应包括：</span><span class="sxs-lookup"><span data-stu-id="ef7d2-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="ef7d2-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="ef7d2-112">In This Section</span></span>  
 [<span data-ttu-id="ef7d2-113">系统要求</span><span class="sxs-lookup"><span data-stu-id="ef7d2-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="ef7d2-114">描述使用适用于 Oracle 的 .NET Framework 数据提供程序的要求, 并介绍使用它时要注意的一些问题。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="ef7d2-115">Oracle BFILEs</span><span class="sxs-lookup"><span data-stu-id="ef7d2-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="ef7d2-116">描述用于使用 Oracle BFILE 数据类型的 <xref:System.Data.OracleClient.OracleBFile> 类。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="ef7d2-117">Oracle LOBs</span><span class="sxs-lookup"><span data-stu-id="ef7d2-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="ef7d2-118">描述用于使用 Oracle LOB 数据类型的 <xref:System.Data.OracleClient.OracleLob> 类。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="ef7d2-119">Oracle REF CURSORs</span><span class="sxs-lookup"><span data-stu-id="ef7d2-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="ef7d2-120">描述对 Oracle REF CURSOR 数据类型的支持。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="ef7d2-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="ef7d2-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="ef7d2-122">描述可以用于使用 Oracle 数据类型的结构，包括 <xref:System.Data.OracleClient.OracleNumber> 和 <xref:System.Data.OracleClient.OracleString>。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="ef7d2-123">Oracle 序列</span><span class="sxs-lookup"><span data-stu-id="ef7d2-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="ef7d2-124">说明对检索服务器生成的 Oracle 键序列值的支持。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="ef7d2-125">Oracle 数据类型映射</span><span class="sxs-lookup"><span data-stu-id="ef7d2-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="ef7d2-126">列出 Oracle 数据类型及其与 <xref:System.Data.OracleClient.OracleDataReader> 的映射。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="ef7d2-127">Oracle 分布式事务</span><span class="sxs-lookup"><span data-stu-id="ef7d2-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="ef7d2-128">描述 <xref:System.Data.OracleClient.OracleConnection> 对象如何自动在现有分布式事务中登记（如果确定某个事务是活动的）。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ef7d2-129">相关章节</span><span class="sxs-lookup"><span data-stu-id="ef7d2-129">Related Sections</span></span>  
 [<span data-ttu-id="ef7d2-130">保证 ADO.NET 应用程序的安全</span><span class="sxs-lookup"><span data-stu-id="ef7d2-130">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="ef7d2-131">描述使用 ADO.NET 时的安全编码做法。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="ef7d2-132">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="ef7d2-132">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="ef7d2-133">说明如何创建和使用 `DataSets`、类型化 `DataSets`、`DataTables` 和 `DataViews`。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="ef7d2-134">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="ef7d2-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="ef7d2-135">说明如何使用 ADO.NET 中的数据。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="ef7d2-136">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ef7d2-136">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 <span data-ttu-id="ef7d2-137">描述如何使用 SQL Server 特定的功能。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="ef7d2-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="ef7d2-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="ef7d2-139">描述用于在 ADO.NET 中编写与提供程序无关的代码的一般类。</span><span class="sxs-lookup"><span data-stu-id="ef7d2-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef7d2-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="ef7d2-140">See also</span></span>

- [<span data-ttu-id="ef7d2-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ef7d2-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="ef7d2-142">ADO.NET 托管提供程序和数据集开发人员中心</span><span class="sxs-lookup"><span data-stu-id="ef7d2-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
