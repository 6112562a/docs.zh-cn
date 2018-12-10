---
title: 实现复原 Entity Framework Core SQL 连接
description: 适用于容器化 .NET 应用程序的 .NET 微服务体系结构 | 实现复原 Entity Framework Core SQL 连接。 在云中使用 Azure SQL 数据库时，此技术尤为重要。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: 0df375737c0e079baba426f3c97b95edcb9aca75
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127181"
---
# <a name="implement-resilient-entity-framework-core-sql-connections"></a><span data-ttu-id="7968d-104">实现复原 Entity Framework Core SQL 连接</span><span class="sxs-lookup"><span data-stu-id="7968d-104">Implement resilient Entity Framework Core SQL connections</span></span>

<span data-ttu-id="7968d-105">对于 Azure SQL DB，Entity Framework Core 早已提供了内部数据库连接复原和重试逻辑。</span><span class="sxs-lookup"><span data-stu-id="7968d-105">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="7968d-106">但如果想要[复原 EF Core 连接](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)，则需要为每个 DbContext 连接启用 Entity Framework 执行策略。</span><span class="sxs-lookup"><span data-stu-id="7968d-106">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have [resilient EF Core connections](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency).</span></span>

<span data-ttu-id="7968d-107">例如，EF Core 连接级别的下列代码可启用复原 SQL 连接，此连接在连接失败时会重试。</span><span class="sxs-lookup"><span data-stu-id="7968d-107">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    // Other code ...
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        // ...
        services.AddDbContext<CatalogContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
            {
                sqlOptions.EnableRetryOnFailure(
                maxRetryCount: 10,
                maxRetryDelay: TimeSpan.FromSeconds(30),
                errorNumbersToAdd: null);
            });
        });
    }
//...
}
```

## <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="7968d-108">使用 BeginTransaction 和多个 DbContext 的执行策略和显式事务</span><span class="sxs-lookup"><span data-stu-id="7968d-108">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="7968d-109">在 EF Core 连接中启用重试时，使用 EF Core 执行的每项操作都会成为其自己的可重试操作。</span><span class="sxs-lookup"><span data-stu-id="7968d-109">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="7968d-110">如果发生暂时性故障，每个查询和 SaveChanges 的每次调用都会作为一个单元进行重试。</span><span class="sxs-lookup"><span data-stu-id="7968d-110">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="7968d-111">但是，如果代码使用 BeginTransaction 启动事务，这表示在定义一组自己的操作，这些操作需要被视为一个单元 - 如果发生故障，事务内的所有内容都会回退。</span><span class="sxs-lookup"><span data-stu-id="7968d-111">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="7968d-112">如果在使用 EF 执行策略（重试策略）时尝试执行该事务，并且事务中包含一些来自多个 DbContext 的 SaveChanges 调用，则会看到与下列情况类似的异常。</span><span class="sxs-lookup"><span data-stu-id="7968d-112">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges calls from multiple DbContexts in the transaction.</span></span>

> <span data-ttu-id="7968d-113">System.InvalidOperationException：已配置的执行策略“SqlServerRetryingExecutionStrategy”不支持用户启动的事务。</span><span class="sxs-lookup"><span data-stu-id="7968d-113">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="7968d-114">使用由“DbContext.Database.CreateExecutionStrategy()”返回的执行策略执行事务（作为一个可回溯单元）中的所有操作。</span><span class="sxs-lookup"><span data-stu-id="7968d-114">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="7968d-115">该解决方案通过代表所有需要执行的委托来手动调用 EF 执行策略。</span><span class="sxs-lookup"><span data-stu-id="7968d-115">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="7968d-116">如果发生暂时性故障，执行策略会再次调用委托。</span><span class="sxs-lookup"><span data-stu-id="7968d-116">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="7968d-117">例如，以下代码演示了在更新产品时，如何使用两个 DbContext (\_ catalogContext 和 IntegrationEventLogContext) 在 eShopOnContainers 中实现该操作，然后保存需要使用不同 DbContext 的 ProductPriceChangedIntegrationEvent 对象。</span><span class="sxs-lookup"><span data-stu-id="7968d-117">For example, the following code show how it is implemented in eShopOnContainers with two multiple DbContexts (\_catalogContext and the IntegrationEventLogContext) when updating a product and then saving the ProductPriceChangedIntegrationEvent object, which needs to use a different DbContext.</span></span>

```csharp
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem
    productToUpdate)
{
    // Other code ...
    // Update current product
    catalogItem = productToUpdate;

    // Use of an EF Core resiliency strategy when using multiple DbContexts
    // within an explicit transaction
    // See:
    // https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
    var strategy = _catalogContext.Database.CreateExecutionStrategy();
    await strategy.ExecuteAsync(async () =>
    {
        // Achieving atomicity between original Catalog database operation and the
        // IntegrationEventLog thanks to a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
            _catalogContext.CatalogItems.Update(catalogItem);
            await _catalogContext.SaveChangesAsync();
            // Save to EventLog only if product price changed
            if (raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
            transaction.Commit();
        }
    });
}
```

<span data-ttu-id="7968d-118">第一个 DbContext 是 \_catalogContext，第二个 DbContext 位于 \_ integrationEventLogService 对象内。</span><span class="sxs-lookup"><span data-stu-id="7968d-118">The first DbContext is \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="7968d-119">通过使用 EF 执行策略在多个 DbContext 之间执行“提交”操作。</span><span class="sxs-lookup"><span data-stu-id="7968d-119">The Commit action is performed across multiple DbContexts using an EF execution strategy.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7968d-120">其他资源</span><span class="sxs-lookup"><span data-stu-id="7968d-120">Additional resources</span></span>

-   <span data-ttu-id="7968d-121">**EF 连接复原** (Entity Framework Core)[*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span><span class="sxs-lookup"><span data-stu-id="7968d-121">**EF Connection Resiliency** (Entity Framework Core) [*https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency*](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency)</span></span>

-   <span data-ttu-id="7968d-122">**通过 Entity Framework 连接复原和命令截获**
    [*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span><span class="sxs-lookup"><span data-stu-id="7968d-122">**Connection Resiliency and Command Interception with the Entity Framework**
[*https://docs.microsoft.com/azure/architecture/patterns/category/resiliency*](https://docs.microsoft.com/azure/architecture/patterns/category/resiliency)</span></span>

-   <span data-ttu-id="7968d-123">**Cesar de la Torre。使用复原 Entity Framework Core SQL 连接和事务**
    <https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span><span class="sxs-lookup"><span data-stu-id="7968d-123">**Cesar de la Torre. Using Resilient Entity Framework Core Sql Connections and Transactions**
<https://blogs.msdn.microsoft.com/cesardelatorre/2017/03/26/using-resilient-entity-framework-core-sql-connections-and-transactions-retries-with-exponential-backoff/></span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7968d-124">[上一页](implement-retries-exponential-backoff.md)
>[下一页](explore-custom-http-call-retries-exponential-backoff.md)</span><span class="sxs-lookup"><span data-stu-id="7968d-124">[Previous](implement-retries-exponential-backoff.md)
[Next](explore-custom-http-call-retries-exponential-backoff.md)</span></span>