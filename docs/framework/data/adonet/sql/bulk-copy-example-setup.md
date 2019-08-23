---
title: 批量复制示例设置
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 2a7c0ddef42ff56306a42288c6960987ce7f714a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918092"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="f3360-102">批量复制示例设置</span><span class="sxs-lookup"><span data-stu-id="f3360-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="f3360-103"><xref:System.Data.SqlClient.SqlBulkCopy> 类只能用于向 SQL Server 表中写入数据。</span><span class="sxs-lookup"><span data-stu-id="f3360-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="f3360-104">本主题中所示的代码示例使用 SQL Server 示例数据库**AdventureWorks**。</span><span class="sxs-lookup"><span data-stu-id="f3360-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="f3360-105">为避免改变现有表，代码示例将数据写入必须先创建的表。</span><span class="sxs-lookup"><span data-stu-id="f3360-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="f3360-106">**BulkCopyDemoMatchingColumns**和**BulkCopyDemoDifferentColumns**表均基于**AdventureWorks** **Products**表。</span><span class="sxs-lookup"><span data-stu-id="f3360-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="f3360-107">在使用这些表的代码示例中, 数据从**Products**表添加到其中一个示例表中。</span><span class="sxs-lookup"><span data-stu-id="f3360-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="f3360-108">当示例演示如何将列从源数据映射到目标表时, 将使用**BulkCopyDemoDifferentColumns**表;**BulkCopyDemoMatchingColumns**用于大多数其他示例。</span><span class="sxs-lookup"><span data-stu-id="f3360-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="f3360-109">一些代码示例演示如何使用一个 <xref:System.Data.SqlClient.SqlBulkCopy> 类写入多个表。</span><span class="sxs-lookup"><span data-stu-id="f3360-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="f3360-110">对于这些示例, **BulkCopyDemoOrderHeader**和**BulkCopyDemoOrderDetail**表用作目标表。</span><span class="sxs-lookup"><span data-stu-id="f3360-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="f3360-111">这些表基于**AdventureWorks**中的**SalesOrderHeader**和**SalesOrderDetail**表。</span><span class="sxs-lookup"><span data-stu-id="f3360-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3360-112">提供**SqlBulkCopy**代码示例是为了演示仅使用**SqlBulkCopy**的语法。</span><span class="sxs-lookup"><span data-stu-id="f3360-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="f3360-113">如果源表和目标表位于同一个 SQL Server 实例中，则使用 Transact-SQL `INSERT … SELECT` 语句复制数据会更加容易、更加迅速。</span><span class="sxs-lookup"><span data-stu-id="f3360-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="f3360-114">表设置</span><span class="sxs-lookup"><span data-stu-id="f3360-114">Table Setup</span></span>  
 <span data-ttu-id="f3360-115">若要创建代码示例正确运行所需的表，必须在 SQL Server 数据库中运行下面的 Transact-SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="f3360-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
```  
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects   
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3360-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="f3360-116">See also</span></span>

- [<span data-ttu-id="f3360-117">SQL Server 中的大容量复制操作</span><span class="sxs-lookup"><span data-stu-id="f3360-117">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="f3360-118">ADO.NET 托管提供程序和数据集开发人员中心</span><span class="sxs-lookup"><span data-stu-id="f3360-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
