---
title: 使用 SqlNotificationRequest 执行 SqlCommand
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1776f48f-9bea-41f6-83a4-c990c7a2c991
ms.openlocfilehash: 90ec7653f7de931bd8127263643b5467998325b5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364458"
---
# <a name="sqlcommand-execution-with-a-sqlnotificationrequest"></a><span data-ttu-id="abeb8-102">使用 SqlNotificationRequest 执行 SqlCommand</span><span class="sxs-lookup"><span data-stu-id="abeb8-102">SqlCommand Execution with a SqlNotificationRequest</span></span>

<span data-ttu-id="abeb8-103">可以配置 <xref:System.Data.SqlClient.SqlCommand>，以便在从服务器获取的数据发生更改时生成通知，且再次执行查询时结果集会不同。</span><span class="sxs-lookup"><span data-stu-id="abeb8-103">A <xref:System.Data.SqlClient.SqlCommand> can be configured to generate a notification when data changes after it has been fetched from the server and the result set would be different if the query were executed again.</span></span> <span data-ttu-id="abeb8-104">如果要在服务器上使用自定义通知队列或不希望维护实时对象，此功能非常有用。</span><span class="sxs-lookup"><span data-stu-id="abeb8-104">This is useful for scenarios where you want to use custom notification queues on the server or when you do not want to maintain live objects.</span></span>

## <a name="creating-the-notification-request"></a><span data-ttu-id="abeb8-105">创建通知请求</span><span class="sxs-lookup"><span data-stu-id="abeb8-105">Creating the Notification Request</span></span>

<span data-ttu-id="abeb8-106">您可以使用 <xref:System.Data.Sql.SqlNotificationRequest> 对象来创建通知请求，方法是将其绑定到 `SqlCommand` 对象上。</span><span class="sxs-lookup"><span data-stu-id="abeb8-106">You can use a <xref:System.Data.Sql.SqlNotificationRequest> object to create the notification request by binding it to a `SqlCommand` object.</span></span> <span data-ttu-id="abeb8-107">创建完请求后，将不再需要 `SqlNotificationRequest` 对象。</span><span class="sxs-lookup"><span data-stu-id="abeb8-107">Once the request is created, you no longer need the `SqlNotificationRequest` object.</span></span> <span data-ttu-id="abeb8-108">您可以在队列中查询任何通知，并相应地对找到的通知进行响应。</span><span class="sxs-lookup"><span data-stu-id="abeb8-108">You can query the queue for any notifications and respond appropriately.</span></span> <span data-ttu-id="abeb8-109">即使应用程序关闭后再重新启动，也会出现通知。</span><span class="sxs-lookup"><span data-stu-id="abeb8-109">Notifications can occur even if the application is shut down and subsequently restarted.</span></span>

<span data-ttu-id="abeb8-110">在执行带有关联通知的命令时，对原始结果集所做的任何更改都会触发向在通知请求中配置的 SQL Server 队列发送消息的操作。</span><span class="sxs-lookup"><span data-stu-id="abeb8-110">When the command with the associated notification is executed, any changes to the original result set trigger sending a message to the SQL Server queue that was configured in the notification request.</span></span>

<span data-ttu-id="abeb8-111">如何轮询 SQL Server 队列和解释该消息是应用程序特定的。</span><span class="sxs-lookup"><span data-stu-id="abeb8-111">How you poll the SQL Server queue and interpret the message is specific to your application.</span></span> <span data-ttu-id="abeb8-112">应用程序负责轮询队列并根据消息的内容做出响应。</span><span class="sxs-lookup"><span data-stu-id="abeb8-112">The application is responsible for polling the queue and reacting based on the contents of the message.</span></span>

> [!NOTE]
> <span data-ttu-id="abeb8-113">在使用具有 <xref:System.Data.SqlClient.SqlDependency> 的 SQL Server 通知请求时，应创建自己的队列名称，而不是使用默认的服务名称。</span><span class="sxs-lookup"><span data-stu-id="abeb8-113">When using SQL Server notification requests with <xref:System.Data.SqlClient.SqlDependency>, create your own queue name instead of using the default service name.</span></span>

<span data-ttu-id="abeb8-114"><xref:System.Data.Sql.SqlNotificationRequest> 没有新的客户端安全性元素。</span><span class="sxs-lookup"><span data-stu-id="abeb8-114">There are no new client-side security elements for <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="abeb8-115">这主要是一项服务器功能，服务器创建了用户在请求通知时必须具有的特殊权限。</span><span class="sxs-lookup"><span data-stu-id="abeb8-115">This is primarily a server feature, and the server has created special privileges that users must have to request a notification.</span></span>

### <a name="example"></a><span data-ttu-id="abeb8-116">示例</span><span class="sxs-lookup"><span data-stu-id="abeb8-116">Example</span></span>

<span data-ttu-id="abeb8-117">下面的代码段演示了如何创建 <xref:System.Data.Sql.SqlNotificationRequest> 并将其与 <xref:System.Data.SqlClient.SqlCommand> 相关联。</span><span class="sxs-lookup"><span data-stu-id="abeb8-117">The following code fragment demonstrates how to create a <xref:System.Data.Sql.SqlNotificationRequest> and associate it with a <xref:System.Data.SqlClient.SqlCommand>.</span></span>

```vb
' Assume connection is an open SqlConnection.
' Create a new SqlCommand object.
Dim command As New SqlCommand( _
  "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection)

' Create a SqlNotificationRequest object.
Dim notifcationRequest As New SqlNotificationRequest()
notificationRequest.id = "NotificationID"
notificationRequest.Service = "mySSBQueue"

' Associate the notification request with the command.
command.Notification = notificationRequest
' Execute the command.
command.ExecuteReader()
' Process the DataReader.
' You can use Transact-SQL syntax to periodically poll the
' SQL Server queue to see if you have a new message.
```

```csharp
// Assume connection is an open SqlConnection.
// Create a new SqlCommand object.
SqlCommand command=new SqlCommand(
 "SELECT ShipperID, CompanyName, Phone FROM dbo.Shippers", connection);

// Create a SqlNotificationRequest object.
SqlNotificationRequest notificationRequest=new SqlNotificationRequest();
notificationRequest.id="NotificationID";
notificationRequest.Service="mySSBQueue";

// Associate the notification request with the command.
command.Notification=notificationRequest;
// Execute the command.
command.ExecuteReader();
// Process the DataReader.
// You can use Transact-SQL syntax to periodically poll the
// SQL Server queue to see if you have a new message.
```

## <a name="see-also"></a><span data-ttu-id="abeb8-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="abeb8-118">See also</span></span>

- [<span data-ttu-id="abeb8-119">SQL Server 中的查询通知</span><span class="sxs-lookup"><span data-stu-id="abeb8-119">Query Notifications in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/query-notifications-in-sql-server.md)
- [<span data-ttu-id="abeb8-120">ADO.NET 托管提供程序和数据集开发人员中心</span><span class="sxs-lookup"><span data-stu-id="abeb8-120">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
