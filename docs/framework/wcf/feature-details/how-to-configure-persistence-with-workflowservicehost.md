---
title: 如何：使用 WorkflowServiceHost 配置永久性
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: b8839f42a9b8b5f4da0a1a8364c7eac5a4c06d4e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337157"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a><span data-ttu-id="34f23-102">如何：使用 WorkflowServiceHost 配置永久性</span><span class="sxs-lookup"><span data-stu-id="34f23-102">How to: Configure Persistence with WorkflowServiceHost</span></span>
<span data-ttu-id="34f23-103">本主题介绍如何使用配置文件配置 SQL 工作流实例存储功能，以便对 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 中承载的工作流启用永久性。</span><span class="sxs-lookup"><span data-stu-id="34f23-103">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for workflows hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost> by using a configuration file.</span></span> <span data-ttu-id="34f23-104">使用 SQL 工作流实例存储功能之前，必须创建用于保存工作流实例的 SQL 数据库。</span><span class="sxs-lookup"><span data-stu-id="34f23-104">Before using the SQL Workflow Instance Store feature you must create a SQL database that is used to persist workflow instances.</span></span> <span data-ttu-id="34f23-105">有关详细信息，请参阅[如何：启用 SQL 暂留工作流和工作流服务](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)。</span><span class="sxs-lookup"><span data-stu-id="34f23-105">For more information, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a><span data-ttu-id="34f23-106">在配置中配置 SQL 工作流实例存储</span><span class="sxs-lookup"><span data-stu-id="34f23-106">To Configure the SQL Workflow Instance Store in Configuration</span></span>  
  
1. <span data-ttu-id="34f23-107">可以通过 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>（一个用于通过 XML 配置更改设置的服务行为）配置 SQL 工作流实例存储的属性。</span><span class="sxs-lookup"><span data-stu-id="34f23-107">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through XML configuration.</span></span> <span data-ttu-id="34f23-108">下面的配置示例演示如何使用配置 SQL 工作流实例存储区 <`sqlWorkflowInstanceStore`> 配置文件中的行为元素。</span><span class="sxs-lookup"><span data-stu-id="34f23-108">The following configuration example shows how to configure the SQL workflow instance store by using the <`sqlWorkflowInstanceStore`> behavior element in a configuration file.</span></span>  
  
    ```xml  
    <serviceBehaviors>  
        <behavior name="">  
            <sqlWorkflowInstanceStore   
                 connectionString="provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                 instanceEncodingOption="GZip | None"  
                 instanceCompletionAction="DeleteAll | DeleteNothing"  
                 instanceLockedExceptionAction="NoRetry | SimpleRetry | AggressiveRetry"  
                 hostLockRenewalPeriod="00:00:30"   
                 runnableInstancesDetectionPeriod="00:00:05">  
            <sqlWorkflowInstanceStore/>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     <span data-ttu-id="34f23-109">有关如何配置 SQL 工作流实例存储的详细信息，请参阅[如何：启用 SQL 暂留工作流和工作流服务](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)。</span><span class="sxs-lookup"><span data-stu-id="34f23-109">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="34f23-110">有关各种设置的详细信息 <`sqlWorkflowInstanceStore`> 行为元素，请参阅[SQL 工作流实例存储](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="34f23-110">For more information about the individual settings for the <`sqlWorkflowInstanceStore`> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="34f23-111">Windows Server App Fabric 提供其自己的永久性存储。</span><span class="sxs-lookup"><span data-stu-id="34f23-111">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="34f23-112">有关详细信息，请参阅[Windows Server App Fabric 持久性](https://go.microsoft.com/fwlink/?LinkId=193121)。</span><span class="sxs-lookup"><span data-stu-id="34f23-112">For more information, see [Windows Server App Fabric Persistence](https://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="34f23-113">上面的配置示例使用的是简化配置。</span><span class="sxs-lookup"><span data-stu-id="34f23-113">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="34f23-114">有关详细信息，请参阅[简化配置](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="34f23-114">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a><span data-ttu-id="34f23-115">在代码中配置 SQL 工作流实例存储</span><span class="sxs-lookup"><span data-stu-id="34f23-115">To Configure the SQL Workflow Instance Store in Code</span></span>  
  
1. <span data-ttu-id="34f23-116">可以通过 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>（一个用于通过代码更改设置的服务行为）配置 SQL 工作流实例存储的属性。</span><span class="sxs-lookup"><span data-stu-id="34f23-116">The properties of the SQL workflow instance store can be configured through the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, a service behavior that allows you to change the settings through code.</span></span> <span data-ttu-id="34f23-117">下面的示例演示如何在代码中使用 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 行为元素来配置 SQL 工作流实例存储。</span><span class="sxs-lookup"><span data-stu-id="34f23-117">The following example shows how to configure the SQL workflow instance store by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element in a code</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new SqlWorkflowInstanceStoreBehavior  
    {  
       ConnectionString = "provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true",  
       InstanceEncodingOption = "GZip | None",  
       InstanceCompletionAction = "DeleteAll | DeleteNothing",  
       InstanceLockedExceptionAction = "NoRetry | SimpleRetry | AggressiveRetry",  
       HostLockRenewalPeriod = new TimeSpan(00, 00, 30),  
       RunnableInstancesDetectionPeriod = new TimeSpan(00, 00, 05)  
    });  
    ```  
  
     <span data-ttu-id="34f23-118">有关如何配置 SQL 工作流实例存储的详细信息，请参阅[如何：启用 SQL 暂留工作流和工作流服务](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)。</span><span class="sxs-lookup"><span data-stu-id="34f23-118">For more information about how to configure the SQL workflow instance store, see [How to: Enable SQL Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="34f23-119">有关各种设置的详细信息<xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>行为元素，请参阅[SQL 工作流实例存储](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)。</span><span class="sxs-lookup"><span data-stu-id="34f23-119">For more information about the individual settings for the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior element, see [SQL Workflow Instance Store](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md).</span></span> <span data-ttu-id="34f23-120">Windows Server App Fabric 提供其自己的永久性存储。</span><span class="sxs-lookup"><span data-stu-id="34f23-120">Windows Server App Fabric provides its own persistence store.</span></span> <span data-ttu-id="34f23-121">有关详细信息，请参阅[Windows Server App Fabric 持久性](https://go.microsoft.com/fwlink/?LinkId=193121)。</span><span class="sxs-lookup"><span data-stu-id="34f23-121">For more information, see [Windows Server App Fabric Persistence](https://go.microsoft.com/fwlink/?LinkId=193121).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="34f23-122">上面的配置示例使用的是简化配置。</span><span class="sxs-lookup"><span data-stu-id="34f23-122">The preceding configuration example uses simplified configuration.</span></span> <span data-ttu-id="34f23-123">有关详细信息，请参阅[简化配置](../../../../docs/framework/wcf/simplified-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="34f23-123">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md)</span></span>  
  
     <span data-ttu-id="34f23-124">有关如何以编程方式配置持久性的示例，请参阅[如何：为工作流和工作流服务启用持久性](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md)。</span><span class="sxs-lookup"><span data-stu-id="34f23-124">For an example of how to configure persistence programmatically see [How to: Enable Persistence for Workflows and Workflow Services](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34f23-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="34f23-125">See also</span></span>

- [<span data-ttu-id="34f23-126">工作流服务</span><span class="sxs-lookup"><span data-stu-id="34f23-126">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="34f23-127">工作流暂留</span><span class="sxs-lookup"><span data-stu-id="34f23-127">Workflow Persistence</span></span>](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
- [<span data-ttu-id="34f23-128">Windows Server App Fabric 持久性</span><span class="sxs-lookup"><span data-stu-id="34f23-128">Windows Server App Fabric Persistence</span></span>](https://go.microsoft.com/fwlink/?LinkId=193121)
