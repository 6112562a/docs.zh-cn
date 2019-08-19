---
title: 业务流程模式-无服务器应用
description: Azure 持久性函数 pr
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 18e13c5355490ef4a019ceda459114bdb6bfd539
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577400"
---
# <a name="orchestration-patterns"></a><span data-ttu-id="eaca3-103">业务流程模式</span><span class="sxs-lookup"><span data-stu-id="eaca3-103">Orchestration patterns</span></span>

<span data-ttu-id="eaca3-104">Durable Functions 使你可以更轻松地创建由无服务器环境中的离散的、长时间运行的活动组成的有状态工作流。</span><span class="sxs-lookup"><span data-stu-id="eaca3-104">Durable Functions makes it easier to create stateful workflows that are composed of discrete, long running activities in a serverless environment.</span></span> <span data-ttu-id="eaca3-105">由于 Durable Functions 可以跟踪工作流的进度并定期检查执行历史记录, 因此它的作用就在于实现一些有趣的模式。</span><span class="sxs-lookup"><span data-stu-id="eaca3-105">Since Durable Functions can track the progress of your workflows and periodically checkpoints the execution history, it lends itself to implementing some interesting patterns.</span></span>

## <a name="function-chaining"></a><span data-ttu-id="eaca3-106">函数链接</span><span class="sxs-lookup"><span data-stu-id="eaca3-106">Function chaining</span></span>

<span data-ttu-id="eaca3-107">在典型的顺序过程中, 活动需要按特定顺序逐个执行。</span><span class="sxs-lookup"><span data-stu-id="eaca3-107">In a typical sequential process, activities need to execute one after the other in a particular order.</span></span> <span data-ttu-id="eaca3-108">或者, 即将发生的活动可能需要以前函数的一些输出。</span><span class="sxs-lookup"><span data-stu-id="eaca3-108">Optionally, the upcoming activity may require some output from the previous function.</span></span> <span data-ttu-id="eaca3-109">此依赖项对活动排序创建了一个执行函数链。</span><span class="sxs-lookup"><span data-stu-id="eaca3-109">This dependency on the ordering of activities creates a function chain of execution.</span></span>

<span data-ttu-id="eaca3-110">使用 Durable Functions 实现此工作流模式的好处在于它可以执行检查点操作。</span><span class="sxs-lookup"><span data-stu-id="eaca3-110">The benefit of using Durable Functions to implement this workflow pattern comes from its ability to do checkpointing.</span></span> <span data-ttu-id="eaca3-111">如果服务器崩溃、网络超时或发生其他问题, 则持久性函数可以从上一已知状态恢复, 并继续运行工作流, 即使它在另一台服务器上也是如此。</span><span class="sxs-lookup"><span data-stu-id="eaca3-111">If the server crashes, the network times out or some other issue occurs, Durable functions can resume from the last known state and continue running your workflow even if it's on another server.</span></span>

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<bool>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

<span data-ttu-id="eaca3-112">在上面的代码示例中, `CallActivityAsync`函数负责在数据中心中的虚拟机上运行给定的活动。</span><span class="sxs-lookup"><span data-stu-id="eaca3-112">In the preceding code sample, the `CallActivityAsync` function is responsible for running a given activity on a virtual machine in the data center.</span></span> <span data-ttu-id="eaca3-113">当 await 返回并且基础任务完成时, 执行将记录到历史记录表。</span><span class="sxs-lookup"><span data-stu-id="eaca3-113">When the await returns and the underlying Task completes, the execution will be recorded to the history table.</span></span> <span data-ttu-id="eaca3-114">业务流程协调程序函数中的代码可以使用任何熟悉的任务并行库构造和 async/await 关键字。</span><span class="sxs-lookup"><span data-stu-id="eaca3-114">The code in the orchestrator function can make use of any of the familiar constructs of the Task Parallel Library and the async/await keywords.</span></span>

<span data-ttu-id="eaca3-115">下面的代码简单举例于该`ProcessPayment`方法的外观:</span><span class="sxs-lookup"><span data-stu-id="eaca3-115">The following code is a simplified example of what the `ProcessPayment` method may look like:</span></span>

```csharp
[FunctionName("ProcessPayment")]
public static bool ProcessPayment([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    ApplyCoupons(orderData);
    if(IssuePaymentRequest(orderData)) {
        return true;
    }

    return false;
}
```

## <a name="asynchronous-http-apis"></a><span data-ttu-id="eaca3-116">异步 HTTP Api</span><span class="sxs-lookup"><span data-stu-id="eaca3-116">Asynchronous HTTP APIs</span></span>

<span data-ttu-id="eaca3-117">在某些情况下, 工作流可能包含需要较长时间才能完成的活动。</span><span class="sxs-lookup"><span data-stu-id="eaca3-117">In some cases, workflows may contain activities that take a relatively long period of time to complete.</span></span> <span data-ttu-id="eaca3-118">假设有一个进程, 该进程将媒体文件备份到 blob 存储中。</span><span class="sxs-lookup"><span data-stu-id="eaca3-118">Imagine a process that kicks off the backup of media files into blob storage.</span></span> <span data-ttu-id="eaca3-119">根据媒体文件的大小和数量, 此备份过程可能需要数小时才能完成。</span><span class="sxs-lookup"><span data-stu-id="eaca3-119">Depending on the size and quantity of the media files, this backup process may take hours to complete.</span></span>

<span data-ttu-id="eaca3-120">在此方案中, `DurableOrchestrationClient`检查正在运行的工作流的状态的功能将非常有用。</span><span class="sxs-lookup"><span data-stu-id="eaca3-120">In this scenario, the `DurableOrchestrationClient`'s ability to check the status of a running workflow becomes useful.</span></span> <span data-ttu-id="eaca3-121">使用`HttpTrigger`启动工作流时`CreateCheckStatusResponse` , 可以使用方法来返回的`HttpResponseMessage`实例。</span><span class="sxs-lookup"><span data-stu-id="eaca3-121">When using an `HttpTrigger` to start a workflow, the `CreateCheckStatusResponse` method can be used to return an instance of `HttpResponseMessage`.</span></span> <span data-ttu-id="eaca3-122">此响应为客户端提供有效负载中的 URI, 可用于检查正在运行的进程的状态。</span><span class="sxs-lookup"><span data-stu-id="eaca3-122">This response provides the client with a URI in the payload that can be used to check the status of the running process.</span></span>

```csharp
[FunctionName("OrderWorkflow")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient orchestrationClient)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

<span data-ttu-id="eaca3-123">下面的示例结果显示了响应负载的结构。</span><span class="sxs-lookup"><span data-stu-id="eaca3-123">The sample result below shows the structure of the response payload.</span></span>

```json
{
    "id": "instanceId",
    "statusQueryGetUri": "http://host/statusUri",
    "sendEventPostUri": "http://host/eventUri",
    "terminatePostUri": "http://host/terminateUri"
}
```

<span data-ttu-id="eaca3-124">使用你的首选 HTTP 客户端, 可以对 statusQueryGetUri 中的 URI 发出 GET 请求, 以检查正在运行的工作流的状态。</span><span class="sxs-lookup"><span data-stu-id="eaca3-124">Using your preferred HTTP client, GET requests can be made to the URI in statusQueryGetUri to inspect the status of the running workflow.</span></span> <span data-ttu-id="eaca3-125">返回的状态响应应类似于以下代码。</span><span class="sxs-lookup"><span data-stu-id="eaca3-125">The returned status response should resemble the following code.</span></span>

```json
{
    "runtimeStatus": "Running",
    "input": {
        "$type": "DurableFunctionsDemos.OrderRequestData, DurableFunctionsDemos"
    },
    "output": null,
    "createdTime": "2018-01-01T00:22:05Z",
    "lastUpdatedTime": "2018-01-01T00:22:09Z"
}
```

<span data-ttu-id="eaca3-126">进程继续时, 状态响应将更改为 "已**失败**" 或 "**已完成**"。</span><span class="sxs-lookup"><span data-stu-id="eaca3-126">As the process continues, the status response will change to either **Failed** or **Completed**.</span></span> <span data-ttu-id="eaca3-127">成功完成后, 负载中的**输出**属性将包含任何返回的数据。</span><span class="sxs-lookup"><span data-stu-id="eaca3-127">On successful completion, the **output** property in the payload will contain any returned data.</span></span>

## <a name="monitoring"></a><span data-ttu-id="eaca3-128">监视</span><span class="sxs-lookup"><span data-stu-id="eaca3-128">Monitoring</span></span>

<span data-ttu-id="eaca3-129">对于简单的定期任务, Azure Functions 提供`TimerTrigger`可基于 CRON 表达式计划的。</span><span class="sxs-lookup"><span data-stu-id="eaca3-129">For simple recurring tasks, Azure Functions provides the `TimerTrigger` that can be scheduled based on a CRON expression.</span></span> <span data-ttu-id="eaca3-130">计时器适用于简单、生存期较短的任务, 但可能存在需要更灵活的计划的情况。</span><span class="sxs-lookup"><span data-stu-id="eaca3-130">The timer works well for simple, short-lived tasks, but there might be scenarios where more flexible scheduling is needed.</span></span> <span data-ttu-id="eaca3-131">这种情况是监视模式和 Durable Functions 可帮助。</span><span class="sxs-lookup"><span data-stu-id="eaca3-131">This scenario is when the monitoring pattern and Durable Functions can help.</span></span>

<span data-ttu-id="eaca3-132">Durable Functions 允许灵活计划间隔、生存期管理和从单个业务流程函数创建多个监视器进程。</span><span class="sxs-lookup"><span data-stu-id="eaca3-132">Durable Functions allows for flexible scheduling intervals, lifetime management, and the creation of multiple monitor processes from a single orchestration function.</span></span> <span data-ttu-id="eaca3-133">此功能的一个用例是为在满足特定阈值后完成的股票价格变化创建观察程序。</span><span class="sxs-lookup"><span data-stu-id="eaca3-133">One use case for this functionality might be to create watchers for stock price changes that complete once a certain threshold is met.</span></span>

```csharp
[FunctionName("CheckStockPrice")]
public static async Task CheckStockPrice([OrchestrationTrigger] DurableOrchestrationContext context)
{
    StockWatcherInfo stockInfo = context.GetInput<StockWatcherInfo>();
    const int checkIntervalSeconds = 120;
    StockPrice initialStockPrice = null;

    DateTime fireAt;
    DateTime exitTime = context.CurrentUtcDateTime.Add(stockInfo.TimeLimit);

    while (context.CurrentUtcDateTime < exitTime)
    {
        StockPrice currentStockPrice = await context.CallActivityAsync<StockPrice>("GetStockPrice", stockInfo);

        if (initialStockPrice == null)
        {
            initialStockPrice = currentStockPrice;
            fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
            await context.CreateTimer(fireAt, CancellationToken.None);
            continue;
        }

        decimal percentageChange = (initialStockPrice.Price - currentStockPrice.Price) /
                               ((initialStockPrice.Price + currentStockPrice.Price) / 2);

        if (Math.Abs(percentageChange) >= stockInfo.PercentageChange)
        {
            // Change threshold detected
            await context.CallActivityAsync("NotifyStockPercentageChange", currentStockPrice);
            break;
        }

        // Sleep til next polling interval
        fireAt = context.CurrentUtcDateTime.AddSeconds(checkIntervalSeconds);
        await context.CreateTimer(fireAt, CancellationToken.None);
    }
}
```

<span data-ttu-id="eaca3-134">`DurableOrchestrationContext`的`CreateTimer`方法为下一次调用循环设置计划, 以检查股票价格变化。</span><span class="sxs-lookup"><span data-stu-id="eaca3-134">`DurableOrchestrationContext`'s `CreateTimer` method sets up the schedule for the next invocation of the loop to check for stock price changes.</span></span> <span data-ttu-id="eaca3-135">`DurableOrchestrationContext`还具有`CurrentUtcDateTime`用于获取 UTC 格式的当前日期时间值的属性。</span><span class="sxs-lookup"><span data-stu-id="eaca3-135">`DurableOrchestrationContext` also has a `CurrentUtcDateTime` property to get the current DateTime value in UTC.</span></span> <span data-ttu-id="eaca3-136">最好使用此属性, 而不是`DateTime.UtcNow` , 因为它易于模拟测试。</span><span class="sxs-lookup"><span data-stu-id="eaca3-136">It's better to use this property instead of `DateTime.UtcNow` because it's easily mocked for testing.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="eaca3-137">推荐的资源</span><span class="sxs-lookup"><span data-stu-id="eaca3-137">Recommended resources</span></span>

* [<span data-ttu-id="eaca3-138">Azure Durable Functions</span><span class="sxs-lookup"><span data-stu-id="eaca3-138">Azure Durable Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [<span data-ttu-id="eaca3-139">.NET Core 和 .NET Standard 中的单元测试</span><span class="sxs-lookup"><span data-stu-id="eaca3-139">Unit Testing in .NET Core and .NET Standard</span></span>](../../core/testing/index.md)

>[!div class="step-by-step"]
><span data-ttu-id="eaca3-140">[上一页](durable-azure-functions.md)
>[下一页](serverless-business-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="eaca3-140">[Previous](durable-azure-functions.md)
[Next](serverless-business-scenarios.md)</span></span>
