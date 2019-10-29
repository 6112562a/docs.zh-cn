---
title: SQL Server 中的数据库镜像
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 89befaff-bb46-4290-8382-e67cdb0e3de9
ms.openlocfilehash: b18c67f5573d375fe0872d76d69a1f0aafa7e7f6
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040443"
---
# <a name="database-mirroring-in-sql-server"></a><span data-ttu-id="bc7fb-102">SQL Server 中的数据库镜像</span><span class="sxs-lookup"><span data-stu-id="bc7fb-102">Database Mirroring in SQL Server</span></span>
<span data-ttu-id="bc7fb-103">通过 SQL Server 中的数据库镜像，可以在备用服务器上保留 SQL Server 数据库的副本（即镜像）。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-103">Database mirroring in SQL Server allows you to keep a copy, or mirror, of a SQL Server database on a standby server.</span></span> <span data-ttu-id="bc7fb-104">镜像可以确保数据始终存在两个独立的副本，从而提供高可用性和完整的数据冗余。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-104">Mirroring ensures that two separate copies of the data exist at all times, providing high availability and complete data redundancy.</span></span> <span data-ttu-id="bc7fb-105">用于 SQL Server 的 .NET 数据提供程序提供了数据库镜像的隐式支持，这样，在为 SQL Server 数据库配置了镜像之后，开发人员无需采取任何措施或编写任何代码。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-105">The .NET Data Provider for SQL Server provides implicit support for database mirroring, so that the developer does not need to take any action or write any code once it has been configured for a SQL Server database.</span></span> <span data-ttu-id="bc7fb-106">此外，<xref:System.Data.SqlClient.SqlConnection> 对象支持显式连接模式，该模式允许在 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 中提供故障转移合作伙伴服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-106">In addition, the <xref:System.Data.SqlClient.SqlConnection> object supports an explicit connection mode that allows supplying the name of a failover partner server in the <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="bc7fb-107">对于连接目标为某个配置为镜像的数据库的 <xref:System.Data.SqlClient.SqlConnection> 对象将发生以下简化的事件序列：</span><span class="sxs-lookup"><span data-stu-id="bc7fb-107">The following simplified sequence of events occurs for a <xref:System.Data.SqlClient.SqlConnection> object that targets a database configured for mirroring:</span></span>  
  
1. <span data-ttu-id="bc7fb-108">客户端应用程序成功连接到主体数据库上，服务器发送回合作伙伴服务器的名称，然后将该名称缓存在客户端上。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-108">The client application successfully connects to the principal database, and the server sends back the name of the partner server, which is then cached on the client.</span></span>  
  
2. <span data-ttu-id="bc7fb-109">如果包含主体数据库的服务器失败或连接中断，连接和事务状态将丢失。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-109">If the server containing the principal database fails or connectivity is interrupted, connection and transaction state is lost.</span></span> <span data-ttu-id="bc7fb-110">客户端应用程序尝试重新建立与主体数据库的连接，但是失败。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-110">The client application attempts to re-establish a connection to the principal database and fails.</span></span>  
  
3. <span data-ttu-id="bc7fb-111">然后，客户端应用程序透明地尝试与合作伙伴服务器上的镜像数据库建立连接。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-111">The client application then transparently attempts to establish a connection to the mirror database on the partner server.</span></span> <span data-ttu-id="bc7fb-112">如果成功，连接将重定向到镜像数据库，而该镜像数据库将成为新的主体数据库。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-112">If it succeeds, the connection is redirected to the mirror database, which then becomes the new principal database.</span></span>  
  
## <a name="specifying-the-failover-partner-in-the-connection-string"></a><span data-ttu-id="bc7fb-113">在连接字符串中指定故障转移合作伙伴</span><span class="sxs-lookup"><span data-stu-id="bc7fb-113">Specifying the Failover Partner in the Connection String</span></span>  
 <span data-ttu-id="bc7fb-114">如果在连接字符串中提供故障转移合作伙伴服务器的名称，当客户端应用程序初次连接时，主体数据库不可用，客户端将直接尝试与故障转移合作伙伴建立连接。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-114">If you supply the name of a failover partner server in the connection string, the client will transparently attempt a connection with the failover partner if the principal database is unavailable when the client application first connects.</span></span>  
  
```csharp
";Failover Partner=PartnerServerName"  
```  
  
 <span data-ttu-id="bc7fb-115">如果省略故障转移合作伙伴服务器的名称且客户端应用程序初次连接时主体数据库不可用，则引发 <xref:System.Data.SqlClient.SqlException>。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-115">If you omit the name of the failover partner server and the principal database is unavailable when the client application first connects then a <xref:System.Data.SqlClient.SqlException> is raised.</span></span>  
  
 <span data-ttu-id="bc7fb-116">成功打开 <xref:System.Data.SqlClient.SqlConnection> 后，故障转移合作伙伴名称由服务器返回，取代连接字符串中提供的任何值。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-116">When a <xref:System.Data.SqlClient.SqlConnection> is successfully opened, the failover partner name is returned by the server and supersedes any values supplied in the connection string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc7fb-117">您必须在连接字符串中显式指定数据库镜像方案的初始编录或数据库名称。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-117">You must explicitly specify the initial catalog or database name in the connection string for database mirroring scenarios.</span></span> <span data-ttu-id="bc7fb-118">如果客户端收到没有显式指定初始编录或数据库的连接的故障转移信息，故障转移信息不会缓存，应用程序也不会在主体服务器出现故障时尝试进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-118">If the client receives failover information on a connection that doesn't have an explicitly specified initial catalog or database, the failover information is not cached and the application does not attempt to fail over if the principal server fails.</span></span> <span data-ttu-id="bc7fb-119">如果连接字符串包含故障转移合作伙伴的值，但是没有包含初始编录或数据库的值，则会引发 `InvalidArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-119">If a connection string has a value for the failover partner, but no value for the initial catalog or database, an `InvalidArgumentException` is raised.</span></span>  
  
## <a name="retrieving-the-current-server-name"></a><span data-ttu-id="bc7fb-120">检索当前服务器名称</span><span class="sxs-lookup"><span data-stu-id="bc7fb-120">Retrieving the Current Server Name</span></span>  
 <span data-ttu-id="bc7fb-121">如果进行故障转移，可以使用 <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> 对象的 <xref:System.Data.SqlClient.SqlConnection> 属性来检索当前连接实际连接到的服务器的名称。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-121">In the event of a failover, you can retrieve the name of the server to which the current connection is actually connected by using the <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> property of a <xref:System.Data.SqlClient.SqlConnection> object.</span></span> <span data-ttu-id="bc7fb-122">以下代码段检索活动服务器的名称，假定连接变量引用打开的 <xref:System.Data.SqlClient.SqlConnection>。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-122">The following code fragment retrieves the name of the active server, assuming that the connection variable references an open <xref:System.Data.SqlClient.SqlConnection>.</span></span>  
  
 <span data-ttu-id="bc7fb-123">发生故障转移事件并将连接切换到镜像服务器时，会更新**DataSource**属性以反映镜像名称。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-123">When a failover event occurs and the connection is switched to the mirror server, the **DataSource** property is updated to reflect the mirror name.</span></span>  
  
```vb  
Dim activeServer As String = connection.DataSource  
```  
  
```csharp  
string activeServer = connection.DataSource;  
```  
  
## <a name="sqlclient-mirroring-behavior"></a><span data-ttu-id="bc7fb-124">SqlClient 镜像行为</span><span class="sxs-lookup"><span data-stu-id="bc7fb-124">SqlClient Mirroring Behavior</span></span>  
 <span data-ttu-id="bc7fb-125">客户端总是尝试连接当前的主体服务器。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-125">The client always tries to connect to the current principal server.</span></span> <span data-ttu-id="bc7fb-126">如果失败，将尝试连接故障转移合作伙伴。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-126">If it fails, it tries the failover partner.</span></span> <span data-ttu-id="bc7fb-127">如果镜像数据库已切换为合作伙伴服务器上的主体角色，连接将成功，新的主体/镜像映射将发送到客户端，并在调用 <xref:System.AppDomain> 的生存期期间进行缓存。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-127">If the mirror database has already been switched to the principal role on the partner server, the connection succeeds and the new principal-mirror mapping is sent to the client and cached for the lifetime of the calling <xref:System.AppDomain>.</span></span> <span data-ttu-id="bc7fb-128">它不存储在持久性存储区中，并且不可用于不同**AppDomain**或进程中的后续连接。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-128">It is not stored in persistent storage and is not available for subsequent connections in a different **AppDomain** or process.</span></span> <span data-ttu-id="bc7fb-129">但是，它可用于同一**AppDomain**中的后续连接。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-129">However, it is available for subsequent connections within the same **AppDomain**.</span></span> <span data-ttu-id="bc7fb-130">请注意，在相同或不同计算机上运行的另一个**AppDomain**或进程始终具有其连接池，并且不会重置这些连接。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-130">Note that another **AppDomain** or process running on the same or a different computer always has its pool of connections, and those connections are not reset.</span></span> <span data-ttu-id="bc7fb-131">在这种情况下，如果主数据库出现故障，每个进程或**AppDomain**一次会失败，并自动清除池。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-131">In that case, if the primary database goes down, each process or **AppDomain** fails once, and the pool is automatically cleared.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc7fb-132">每个数据库都要在服务器上配置镜像支持。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-132">Mirroring support on the server is configured on a per-database basis.</span></span> <span data-ttu-id="bc7fb-133">如果对不在主体/镜像数据库集中的其他数据库执行数据操作，那么无论使用多部分名称还是更改当前数据库，在失败时都不会传播对这些数据库的更改。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-133">If data manipulation operations are executed against other databases not included in the principal/mirror set, either by using multipart names or by changing the current database, the changes to these other databases do not propagate in the event of failure.</span></span> <span data-ttu-id="bc7fb-134">修改未镜像的数据库中的数据时，不会生成错误。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-134">No error is generated when data is modified in a database that is not mirrored.</span></span> <span data-ttu-id="bc7fb-135">开发人员必须评估此类操作可能产生的影响。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-135">The developer must evaluate the possible impact of such operations.</span></span>  
  
## <a name="database-mirroring-resources"></a><span data-ttu-id="bc7fb-136">数据库镜像资源</span><span class="sxs-lookup"><span data-stu-id="bc7fb-136">Database Mirroring Resources</span></span>  
 <span data-ttu-id="bc7fb-137">有关配置、部署和管理镜像的概念文档和信息，请参阅 SQL Server 文档中的以下资源。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-137">For conceptual documentation and information on configuring, deploying and administering mirroring, see the following resources in SQL Server documentation.</span></span>  
  
|<span data-ttu-id="bc7fb-138">资源</span><span class="sxs-lookup"><span data-stu-id="bc7fb-138">Resource</span></span>|<span data-ttu-id="bc7fb-139">描述</span><span class="sxs-lookup"><span data-stu-id="bc7fb-139">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="bc7fb-140">数据库镜像</span><span class="sxs-lookup"><span data-stu-id="bc7fb-140">Database Mirroring</span></span>](/sql/database-engine/database-mirroring/database-mirroring-sql-server)|<span data-ttu-id="bc7fb-141">说明如何在 SQL Server 中设置和配置镜像。</span><span class="sxs-lookup"><span data-stu-id="bc7fb-141">Describes how to set up and configure mirroring in SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc7fb-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="bc7fb-142">See also</span></span>

- [<span data-ttu-id="bc7fb-143">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="bc7fb-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
