---
title: SQL Server 中的查询通知
ms.date: 03/30/2017
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
ms.openlocfilehash: 94171c8dac59fc17b0dd699d87fc043651fa5b7a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791765"
---
# <a name="query-notifications-in-sql-server"></a><span data-ttu-id="67f23-102">SQL Server 中的查询通知</span><span class="sxs-lookup"><span data-stu-id="67f23-102">Query Notifications in SQL Server</span></span>
<span data-ttu-id="67f23-103">查询通知建立在 Service Broker 基础结构的基础上，使应用程序可以在数据更改时收到通知。</span><span class="sxs-lookup"><span data-stu-id="67f23-103">Built upon the Service Broker infrastructure, query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="67f23-104">如果应用程序提供数据库中信息的缓存（例如 Web 应用程序），需要在源数据更改时接收通知，此功能特别有用。</span><span class="sxs-lookup"><span data-stu-id="67f23-104">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="67f23-105">通过三种方式可以使用 ADO.NET 实现查询通知：</span><span class="sxs-lookup"><span data-stu-id="67f23-105">There are three ways you can implement query notifications using ADO.NET:</span></span>  
  
1. <span data-ttu-id="67f23-106">低级实现由 `SqlNotificationRequest` 类提供，该类公开服务器端功能，使您可以对通知请求执行命令。</span><span class="sxs-lookup"><span data-stu-id="67f23-106">The low-level implementation is provided by the `SqlNotificationRequest` class that exposes server-side functionality, enabling you to execute a command with a notification request.</span></span>  
  
2. <span data-ttu-id="67f23-107">高级实现由 `SqlDependency` 类提供，该类提供源应用程序与 SQL Server 之间通知功能的高级抽象，使您可以使用相关性来检测服务器中的更改。</span><span class="sxs-lookup"><span data-stu-id="67f23-107">The high-level implementation is provided by the `SqlDependency` class, which is a class that provides a high-level abstraction of notification functionality between the source application and SQL Server, enabling you to use a dependency to detect changes in the server.</span></span> <span data-ttu-id="67f23-108">大多数情况下，这是托管客户端应用程序通过适用于 SQL Server 的 .NET Framework 数据提供程序利用 SQL Server 通知功能的最简单、最有效的方法。</span><span class="sxs-lookup"><span data-stu-id="67f23-108">In most cases, this is the simplest and most effective way to leverage SQL Server notifications capability by managed client applications using the .NET Framework Data Provider for SQL Server.</span></span>  
  
3. <span data-ttu-id="67f23-109">此外，使用 ASP.NET 2.0（或更高版本）构建的 Web 应用程序可以使用 `SqlCacheDependency` 帮助器类。</span><span class="sxs-lookup"><span data-stu-id="67f23-109">In addition, Web applications built using ASP.NET 2.0 or later can use the `SqlCacheDependency` helper classes.</span></span>  
  
 <span data-ttu-id="67f23-110">如果应用程序需要通过刷新显示或缓存来响应基础数据中的更改，查询通知非常有用。</span><span class="sxs-lookup"><span data-stu-id="67f23-110">Query notifications are used for applications that need to refresh displays or caches in response to changes in underlying data.</span></span> <span data-ttu-id="67f23-111">如果执行相同命令生成的结果集与最初检索到的结果集不同，则 Microsoft SQL Server 可允许 .NET Framework 应用程序向 SQL Server 发送命令和请求通知。</span><span class="sxs-lookup"><span data-stu-id="67f23-111">Microsoft SQL Server allows .NET Framework applications to send a command to SQL Server and request notification if executing the same command would produce result sets different from those initially retrieved.</span></span> <span data-ttu-id="67f23-112">服务器上生成的通知通过队列发送，供以后处理。</span><span class="sxs-lookup"><span data-stu-id="67f23-112">Notifications generated at the server are sent through queues to be processed later.</span></span>  
  
 <span data-ttu-id="67f23-113">您可以为 SELECT 和 EXECUTE 语句设置通知。</span><span class="sxs-lookup"><span data-stu-id="67f23-113">You can set up notifications for SELECT and EXECUTE statements.</span></span> <span data-ttu-id="67f23-114">使用 EXECUTE 语句时，SQL Server 会为执行的命令而不是 EXECUTE 语句本身注册通知。</span><span class="sxs-lookup"><span data-stu-id="67f23-114">When using an EXECUTE statement, SQL Server registers a notification for the command executed rather than the EXECUTE statement itself.</span></span> <span data-ttu-id="67f23-115">该命令必须满足 SELECT 语句的要求和限制。</span><span class="sxs-lookup"><span data-stu-id="67f23-115">The command must meet the requirements and limitations for a SELECT statement.</span></span> <span data-ttu-id="67f23-116">当注册通知的命令包含多个语句时，数据库引擎会为批处理中的每个语句创建一个通知。</span><span class="sxs-lookup"><span data-stu-id="67f23-116">When a command that registers a notification contains more than one statement, the Database Engine creates a notification for each statement in the batch.</span></span>  
  
 <span data-ttu-id="67f23-117">如果你正在开发的应用程序在数据更改时需要可靠的第二秒通知，请查看**规划有效查询通知策略**的部分和计划中的**查询通知的替代方法** [。](https://go.microsoft.com/fwlink/?LinkId=211984)SQL Server 联机丛书中的通知主题。</span><span class="sxs-lookup"><span data-stu-id="67f23-117">If you are developing an application where you need reliable sub-second notifications when data changes, review the sections **Planning an Efficient Query Notifications Strategy** and **Alternatives to Query Notifications** in the [Planning for Notifications](https://go.microsoft.com/fwlink/?LinkId=211984) topic in SQL Server Books Online.</span></span> <span data-ttu-id="67f23-118">有关查询通知和 SQL Server Service Broker 的更多信息，请参见以下指向“SQL Server 联机丛书”中的主题的链接。</span><span class="sxs-lookup"><span data-stu-id="67f23-118">For more information about Query Notifications and SQL Server Service Broker, see the following links to topics in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="67f23-119">**SQL Server 文档**</span><span class="sxs-lookup"><span data-stu-id="67f23-119">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="67f23-120">[使用查询通知](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="67f23-120">[Using Query Notifications](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms175110(v=sql.105))</span></span>  
  
- <span data-ttu-id="67f23-121">[创建通知查询](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="67f23-121">[Creating a Query for Notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="67f23-122">[开发（Service Broker）](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="67f23-122">[Development (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522889(v=sql.105))</span></span>  
  
- <span data-ttu-id="67f23-123">[Service Broker 开发人员信息中心](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="67f23-123">[Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="67f23-124">[开发人员指南（Service Broker）](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="67f23-124">[Developer's Guide (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67f23-125">本节内容</span><span class="sxs-lookup"><span data-stu-id="67f23-125">In This Section</span></span>  
 [<span data-ttu-id="67f23-126">启用查询通知</span><span class="sxs-lookup"><span data-stu-id="67f23-126">Enabling Query Notifications</span></span>](enabling-query-notifications.md)  
 <span data-ttu-id="67f23-127">介绍如何使用查询通知（包括启用和使用查询通知的需求）。</span><span class="sxs-lookup"><span data-stu-id="67f23-127">Discusses how to use query notifications, including the requirements for enabling and using them.</span></span>  
  
 [<span data-ttu-id="67f23-128">ASP.NET 应用程序中的 SqlDependency</span><span class="sxs-lookup"><span data-stu-id="67f23-128">SqlDependency in an ASP.NET Application</span></span>](sqldependency-in-an-aspnet-app.md)  
 <span data-ttu-id="67f23-129">演示如何使用 ASP.NET 应用程序中的查询通知。</span><span class="sxs-lookup"><span data-stu-id="67f23-129">Demonstrates how to use query notifications from an ASP.NET application.</span></span>  
  
 [<span data-ttu-id="67f23-130">使用 SqlDependency 检测更改</span><span class="sxs-lookup"><span data-stu-id="67f23-130">Detecting Changes with SqlDependency</span></span>](detecting-changes-with-sqldependency.md)  
 <span data-ttu-id="67f23-131">演示如何检测查询结果与最初检索到的结果是否相同。</span><span class="sxs-lookup"><span data-stu-id="67f23-131">Demonstrates how to detect when query results will be different from those originally received.</span></span>  
  
 [<span data-ttu-id="67f23-132">使用 SqlNotificationRequest 的 SqlCommand 执行</span><span class="sxs-lookup"><span data-stu-id="67f23-132">SqlCommand Execution with a SqlNotificationRequest</span></span>](sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 <span data-ttu-id="67f23-133">演示如何将 <xref:System.Data.SqlClient.SqlCommand> 对象配置为处理查询通知。</span><span class="sxs-lookup"><span data-stu-id="67f23-133">Demonstrates configuring a <xref:System.Data.SqlClient.SqlCommand> object to work with a query notification.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="67f23-134">参考</span><span class="sxs-lookup"><span data-stu-id="67f23-134">Reference</span></span>  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 <span data-ttu-id="67f23-135">描述 <xref:System.Data.Sql.SqlNotificationRequest> 类及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="67f23-135">Describes the <xref:System.Data.Sql.SqlNotificationRequest> class and all of its members.</span></span>  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 <span data-ttu-id="67f23-136">描述 <xref:System.Data.SqlClient.SqlDependency> 类及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="67f23-136">Describes the <xref:System.Data.SqlClient.SqlDependency> class and all of its members.</span></span>  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 <span data-ttu-id="67f23-137">描述 <xref:System.Web.Caching.SqlCacheDependency> 类及其所有成员。</span><span class="sxs-lookup"><span data-stu-id="67f23-137">Describes the <xref:System.Web.Caching.SqlCacheDependency> class and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f23-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="67f23-138">See also</span></span>

- [<span data-ttu-id="67f23-139">SQL Server 和 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="67f23-139">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="67f23-140">ADO.NET 概述</span><span class="sxs-lookup"><span data-stu-id="67f23-140">ADO.NET Overview</span></span>](../ado-net-overview.md)
