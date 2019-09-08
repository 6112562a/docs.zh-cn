---
title: SQL Server 数据类型和 ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 642fe0d541aca01d6ffb2d9279c4d0fa91eadb63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780846"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="71200-102">SQL Server 数据类型和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="71200-102">SQL Server Data Types and ADO.NET</span></span>
<span data-ttu-id="71200-103">SQL Server 和 .NET Framework 基于不同的类型系统，这可导致潜在的数据丢失。</span><span class="sxs-lookup"><span data-stu-id="71200-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="71200-104">为了保持数据的完整性，适用于 SQL Server 的 .NET Framework 数据提供程序 (<xref:System.Data.SqlClient>) 提供了用于处理 SQL Server 数据的类型化访问器方法。</span><span class="sxs-lookup"><span data-stu-id="71200-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="71200-105">可以使用 <xref:System.Data.SqlDbType> 类中的枚举来指定 <xref:System.Data.SqlClient.SqlParameter> 数据类型。</span><span class="sxs-lookup"><span data-stu-id="71200-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="71200-106">有关 SQL Server 和 .NET Framework 数据类型之间的数据类型映射的详细信息和表，请参阅[SQL Server 数据类型映射](../sql-server-data-type-mappings.md)。</span><span class="sxs-lookup"><span data-stu-id="71200-106">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="71200-107">SQL Server 2008 引入了旨在满足业务需求的新数据类型，以用于处理日期和时间、结构化、半结构化和非结构化的数据。</span><span class="sxs-lookup"><span data-stu-id="71200-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="71200-108">这些文档位于 SQL Server 2008 联机丛书中。</span><span class="sxs-lookup"><span data-stu-id="71200-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="71200-109">可在应用程序中使用的 SQL Server 数据类型取决于您正在使用的 SQL Server 版本。</span><span class="sxs-lookup"><span data-stu-id="71200-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="71200-110">有关更多信息，请参见下表中的相关版本的 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="71200-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="71200-111">**SQL Server 联机丛书**</span><span class="sxs-lookup"><span data-stu-id="71200-111">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="71200-112">数据类型（数据库引擎）</span><span class="sxs-lookup"><span data-stu-id="71200-112">Data Types (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a><span data-ttu-id="71200-113">本节内容</span><span class="sxs-lookup"><span data-stu-id="71200-113">In This Section</span></span>  
 [<span data-ttu-id="71200-114">SqlTypes 和数据集</span><span class="sxs-lookup"><span data-stu-id="71200-114">SqlTypes and the DataSet</span></span>](sqltypes-and-the-dataset.md)  
 <span data-ttu-id="71200-115">说明对 `SqlTypes` 中 `DataSet` 的类型支持。</span><span class="sxs-lookup"><span data-stu-id="71200-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="71200-116">处理 NULL 值</span><span class="sxs-lookup"><span data-stu-id="71200-116">Handling Null Values</span></span>](handling-null-values.md)  
 <span data-ttu-id="71200-117">演示如何使用空值和三值逻辑。</span><span class="sxs-lookup"><span data-stu-id="71200-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="71200-118">比较 GUID 和 uniqueidentifier 值</span><span class="sxs-lookup"><span data-stu-id="71200-118">Comparing GUID and uniqueidentifier Values</span></span>](comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="71200-119">演示如何在 SQL Server 和 .NET Framework 中使用 GUID 和 uniqueidentifier 值。</span><span class="sxs-lookup"><span data-stu-id="71200-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="71200-120">日期和时间数据</span><span class="sxs-lookup"><span data-stu-id="71200-120">Date and Time Data</span></span>](date-and-time-data.md)  
 <span data-ttu-id="71200-121">说明如何使用在 SQL Server 2008 中引入的新的日期和时间数据类型。</span><span class="sxs-lookup"><span data-stu-id="71200-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="71200-122">大型 UDT</span><span class="sxs-lookup"><span data-stu-id="71200-122">Large UDTs</span></span>](large-udts.md)  
 <span data-ttu-id="71200-123">演示如何从在 SQL Server 2008 中引入的大值 UDT 检索数据。</span><span class="sxs-lookup"><span data-stu-id="71200-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="71200-124">SQL Server 中的 XML 数据</span><span class="sxs-lookup"><span data-stu-id="71200-124">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)  
 <span data-ttu-id="71200-125">说明如何使用从 SQL Server 中检索的 XML 数据。</span><span class="sxs-lookup"><span data-stu-id="71200-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="71200-126">参考</span><span class="sxs-lookup"><span data-stu-id="71200-126">Reference</span></span>  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="71200-127">描述 `DataSet` 类及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="71200-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="71200-128">说明 `SqlTypes` 命名空间及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="71200-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="71200-129">说明 `SqlDbType` 枚举及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="71200-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="71200-130">说明 `DbType` 枚举及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="71200-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71200-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="71200-131">See also</span></span>

- [<span data-ttu-id="71200-132">SQL Server 数据类型映射</span><span class="sxs-lookup"><span data-stu-id="71200-132">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="71200-133">配置参数和参数数据类型</span><span class="sxs-lookup"><span data-stu-id="71200-133">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="71200-134">表值参数</span><span class="sxs-lookup"><span data-stu-id="71200-134">Table-Valued Parameters</span></span>](table-valued-parameters.md)
- [<span data-ttu-id="71200-135">SQL Server 二进制和大值数据</span><span class="sxs-lookup"><span data-stu-id="71200-135">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="71200-136">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="71200-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
