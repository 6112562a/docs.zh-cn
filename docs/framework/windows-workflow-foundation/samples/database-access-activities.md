---
title: 数据库访问活动
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: eec368803eeacb2bab729bcd6d57cc7fc6107256
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710863"
---
# <a name="database-access-activities"></a><span data-ttu-id="e2a50-102">数据库访问活动</span><span class="sxs-lookup"><span data-stu-id="e2a50-102">Database Access Activities</span></span>

<span data-ttu-id="e2a50-103">数据库访问活动可用于在一个工作流内访问数据库。</span><span class="sxs-lookup"><span data-stu-id="e2a50-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="e2a50-104">这些活动允许访问数据库以检索或修改信息，并使用[ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081)来访问数据库。</span><span class="sxs-lookup"><span data-stu-id="e2a50-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e2a50-105">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="e2a50-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e2a50-106">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="e2a50-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e2a50-107">如果此目录不存在，请参阅（下载页）下载所有 Windows Communication Foundation （WCF）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="e2a50-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e2a50-108">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="e2a50-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="e2a50-109">数据库活动</span><span class="sxs-lookup"><span data-stu-id="e2a50-109">Database Activities</span></span>

<span data-ttu-id="e2a50-110">以下部分详细介绍了此示例中包含的活动列表。</span><span class="sxs-lookup"><span data-stu-id="e2a50-110">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="e2a50-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="e2a50-111">DbUpdate</span></span>

<span data-ttu-id="e2a50-112">执行可在数据库中产生修改（插入、更新、删除和其他修改）的 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="e2a50-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

<span data-ttu-id="e2a50-113">此类采用异步方式执行其工作（它派生自 <xref:System.Activities.AsyncCodeActivity> 并使用其异步功能）。</span><span class="sxs-lookup"><span data-stu-id="e2a50-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="e2a50-114">通过设置提供程序固定名称 (`ProviderName`) 和连接字符串 (`ConnectionString`)，或仅使用应用程序配置文件中的连接字符串配置名称 (`ConfigFileSectionName`)，可以配置连接信息。</span><span class="sxs-lookup"><span data-stu-id="e2a50-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="e2a50-115">要执行的查询在其 `Sql` 属性中配置，并通过 `Parameters` 集合传递参数。</span><span class="sxs-lookup"><span data-stu-id="e2a50-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="e2a50-116">执行 `DbUpdate` 后，在 `AffectedRecords` 属性中返回受影响的记录的数量。</span><span class="sxs-lookup"><span data-stu-id="e2a50-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

```csharp
Public class DbUpdate: AsyncCodeActivity
{
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [DependsOn("Parameters")]
    public OutArgument<int> AffectedRecords { get; set; }
}
```

|<span data-ttu-id="e2a50-117">自变量</span><span class="sxs-lookup"><span data-stu-id="e2a50-117">Argument</span></span>|<span data-ttu-id="e2a50-118">描述</span><span class="sxs-lookup"><span data-stu-id="e2a50-118">Description</span></span>|
|-|-|
|<span data-ttu-id="e2a50-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="e2a50-119">ProviderName</span></span>|<span data-ttu-id="e2a50-120">ADO.NET 提供程序固定名称。</span><span class="sxs-lookup"><span data-stu-id="e2a50-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="e2a50-121">如果设置此自变量，则必须还要设置 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="e2a50-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="e2a50-122">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="e2a50-122">ConnectionString</span></span>|<span data-ttu-id="e2a50-123">用于连接到数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="e2a50-123">Connection string to connect to the database.</span></span> <span data-ttu-id="e2a50-124">如果设置此自变量，则必须还要设置 `ProviderName`。</span><span class="sxs-lookup"><span data-stu-id="e2a50-124">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="e2a50-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="e2a50-125">ConfigName</span></span>|<span data-ttu-id="e2a50-126">存储连接信息的配置文件部分的名称。</span><span class="sxs-lookup"><span data-stu-id="e2a50-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="e2a50-127">设置此自变量之后，将不再需要 `ProviderName` 和 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="e2a50-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="e2a50-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="e2a50-128">CommandType</span></span>|<span data-ttu-id="e2a50-129">要执行的 <xref:System.Data.Common.DbCommand> 的类型。</span><span class="sxs-lookup"><span data-stu-id="e2a50-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="e2a50-130">Sql</span><span class="sxs-lookup"><span data-stu-id="e2a50-130">Sql</span></span>|<span data-ttu-id="e2a50-131">要执行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="e2a50-131">The SQL command to be executed.</span></span>|
|<span data-ttu-id="e2a50-132">参数</span><span class="sxs-lookup"><span data-stu-id="e2a50-132">Parameters</span></span>|<span data-ttu-id="e2a50-133">SQL 查询的参数集合。</span><span class="sxs-lookup"><span data-stu-id="e2a50-133">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="e2a50-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="e2a50-134">AffectedRecords</span></span>|<span data-ttu-id="e2a50-135">最后一个操作影响的记录的数量。</span><span class="sxs-lookup"><span data-stu-id="e2a50-135">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="e2a50-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="e2a50-136">DbQueryScalar</span></span>

<span data-ttu-id="e2a50-137">执行可从数据库检索单个值的查询。</span><span class="sxs-lookup"><span data-stu-id="e2a50-137">Executes a query that retrieves a single value from the database.</span></span>

<span data-ttu-id="e2a50-138">此类采用异步方式执行其工作（它派生自 <xref:System.Activities.AsyncCodeActivity%601> 并使用其异步功能）。</span><span class="sxs-lookup"><span data-stu-id="e2a50-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

<span data-ttu-id="e2a50-139">通过设置提供程序固定名称 (`ProviderName`) 和连接字符串 (`ConnectionString`)，或仅使用应用程序配置文件中的连接字符串配置名称 (`ConfigFileSectionName`)，可以配置连接信息。</span><span class="sxs-lookup"><span data-stu-id="e2a50-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="e2a50-140">要执行的查询在其 `Sql` 属性中配置，并通过 `Parameters` 集合传递参数。</span><span class="sxs-lookup"><span data-stu-id="e2a50-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="e2a50-141">执行 `DbQueryScalar` 后，将在 `Result out` 参数（类型 `TResult`，在基类 <xref:System.Activities.AsyncCodeActivity%601>中定义）中返回标量。</span><span class="sxs-lookup"><span data-stu-id="e2a50-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="e2a50-142">自变量</span><span class="sxs-lookup"><span data-stu-id="e2a50-142">Argument</span></span>|<span data-ttu-id="e2a50-143">描述</span><span class="sxs-lookup"><span data-stu-id="e2a50-143">Description</span></span>|
|-|-|
|<span data-ttu-id="e2a50-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="e2a50-144">ProviderName</span></span>|<span data-ttu-id="e2a50-145">ADO.NET 提供程序固定名称。</span><span class="sxs-lookup"><span data-stu-id="e2a50-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="e2a50-146">如果设置此自变量，则必须还要设置 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="e2a50-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="e2a50-147">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="e2a50-147">ConnectionString</span></span>|<span data-ttu-id="e2a50-148">用于连接到数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="e2a50-148">Connection string to connect to the database.</span></span> <span data-ttu-id="e2a50-149">如果设置此自变量，则必须还要设置 `ProviderName`。</span><span class="sxs-lookup"><span data-stu-id="e2a50-149">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="e2a50-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="e2a50-150">ConfigName</span></span>|<span data-ttu-id="e2a50-151">存储连接信息的配置文件部分的名称。</span><span class="sxs-lookup"><span data-stu-id="e2a50-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="e2a50-152">设置此自变量之后，将不再需要 `ProviderName` 和 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="e2a50-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="e2a50-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="e2a50-153">CommandType</span></span>|<span data-ttu-id="e2a50-154">要执行的 <xref:System.Data.Common.DbCommand> 的类型。</span><span class="sxs-lookup"><span data-stu-id="e2a50-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="e2a50-155">Sql</span><span class="sxs-lookup"><span data-stu-id="e2a50-155">Sql</span></span>|<span data-ttu-id="e2a50-156">要执行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="e2a50-156">The SQL command to be executed.</span></span>|
|<span data-ttu-id="e2a50-157">参数</span><span class="sxs-lookup"><span data-stu-id="e2a50-157">Parameters</span></span>|<span data-ttu-id="e2a50-158">SQL 查询的参数集合。</span><span class="sxs-lookup"><span data-stu-id="e2a50-158">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="e2a50-159">结果</span><span class="sxs-lookup"><span data-stu-id="e2a50-159">Result</span></span>|<span data-ttu-id="e2a50-160">执行查询后获得的标量。</span><span class="sxs-lookup"><span data-stu-id="e2a50-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="e2a50-161">此自变量的类型为 `TResult`。</span><span class="sxs-lookup"><span data-stu-id="e2a50-161">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="e2a50-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="e2a50-162">DbQuery</span></span>

<span data-ttu-id="e2a50-163">执行可检索对象列表的查询。</span><span class="sxs-lookup"><span data-stu-id="e2a50-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="e2a50-164">执行查询后，将执行一个映射函数（它可以 <xref:System.Func%601><`DbDataReader`、`TResult`> 或 <xref:System.Activities.ActivityFunc%601><`DbDataReader``TResult`>）。</span><span class="sxs-lookup"><span data-stu-id="e2a50-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="e2a50-165">此映射函数在 `DbDataReader` 中获取一个记录，并将其映射到要返回的对象。</span><span class="sxs-lookup"><span data-stu-id="e2a50-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

<span data-ttu-id="e2a50-166">通过设置提供程序固定名称 (`ProviderName`) 和连接字符串 (`ConnectionString`)，或仅使用应用程序配置文件中的连接字符串配置名称 (`ConfigFileSectionName`)，可以配置连接信息。</span><span class="sxs-lookup"><span data-stu-id="e2a50-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="e2a50-167">要执行的查询在其 `Sql` 属性中配置，并通过 `Parameters` 集合传递参数。</span><span class="sxs-lookup"><span data-stu-id="e2a50-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="e2a50-168">使用 `DbDataReader` 检索 SQL 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="e2a50-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="e2a50-169">此活动将循环访问 `DbDataReader`，并将 `DbDataReader` 中的行映射到 `TResult` 的实例。</span><span class="sxs-lookup"><span data-stu-id="e2a50-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="e2a50-170">`DbQuery` 的用户必须提供映射代码，可以通过两种方式完成此操作：使用 <xref:System.Func%601><`DbDataReader`、`TResult`> 或 <xref:System.Activities.ActivityFunc%601><`DbDataReader``TResult`>。</span><span class="sxs-lookup"><span data-stu-id="e2a50-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="e2a50-171">在第一种情况下，将在单个执行脉冲中完成映射。</span><span class="sxs-lookup"><span data-stu-id="e2a50-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="e2a50-172">因此，此方法的速度更快，但无法序列化为 XAML。</span><span class="sxs-lookup"><span data-stu-id="e2a50-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="e2a50-173">在后一种情况下，将在多个脉冲中完成映射。</span><span class="sxs-lookup"><span data-stu-id="e2a50-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="e2a50-174">因此，此方法的速度较慢，但可序列化为 XAML，并以声明方式进行创作（任何现有活动均可参与映射）。</span><span class="sxs-lookup"><span data-stu-id="e2a50-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

```csharp
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [OverloadGroup("DirectMapping")]
    [DefaultValue(null)]
    public Func<DbDataReader, TResult> Mapper { get; set; }

    [OverloadGroup("MultiplePulseMapping")]
    [DefaultValue(null)]
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }
}
```

|<span data-ttu-id="e2a50-175">自变量</span><span class="sxs-lookup"><span data-stu-id="e2a50-175">Argument</span></span>|<span data-ttu-id="e2a50-176">描述</span><span class="sxs-lookup"><span data-stu-id="e2a50-176">Description</span></span>|
|-|-|
|<span data-ttu-id="e2a50-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="e2a50-177">ProviderName</span></span>|<span data-ttu-id="e2a50-178">ADO.NET 提供程序固定名称。</span><span class="sxs-lookup"><span data-stu-id="e2a50-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="e2a50-179">如果设置此自变量，则必须还要设置 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="e2a50-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="e2a50-180">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="e2a50-180">ConnectionString</span></span>|<span data-ttu-id="e2a50-181">用于连接到数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="e2a50-181">Connection string to connect to the database.</span></span> <span data-ttu-id="e2a50-182">如果设置此自变量，则必须还要设置 `ProviderName`。</span><span class="sxs-lookup"><span data-stu-id="e2a50-182">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="e2a50-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="e2a50-183">ConfigName</span></span>|<span data-ttu-id="e2a50-184">存储连接信息的配置文件部分的名称。</span><span class="sxs-lookup"><span data-stu-id="e2a50-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="e2a50-185">设置此自变量之后，将不再需要 `ProviderName` 和 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="e2a50-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="e2a50-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="e2a50-186">CommandType</span></span>|<span data-ttu-id="e2a50-187">要执行的 <xref:System.Data.Common.DbCommand> 的类型。</span><span class="sxs-lookup"><span data-stu-id="e2a50-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="e2a50-188">Sql</span><span class="sxs-lookup"><span data-stu-id="e2a50-188">Sql</span></span>|<span data-ttu-id="e2a50-189">要执行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="e2a50-189">The SQL command to be executed.</span></span>|
|<span data-ttu-id="e2a50-190">参数</span><span class="sxs-lookup"><span data-stu-id="e2a50-190">Parameters</span></span>|<span data-ttu-id="e2a50-191">SQL 查询的参数集合。</span><span class="sxs-lookup"><span data-stu-id="e2a50-191">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="e2a50-192">Mapper</span><span class="sxs-lookup"><span data-stu-id="e2a50-192">Mapper</span></span>|<span data-ttu-id="e2a50-193">映射函数（<xref:System.Func%601><`DbDataReader`，`TResult`>），该函数采用在执行查询后获得的 `DataReader` 中的记录，并返回要添加到 `TResult` 集合的类型 `Result` 的对象的实例。</span><span class="sxs-lookup"><span data-stu-id="e2a50-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="e2a50-194">在这种情况下，将在单个执行脉冲中完成映射，但不能使用设计器以声明方式创作它。</span><span class="sxs-lookup"><span data-stu-id="e2a50-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="e2a50-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="e2a50-195">MapperFunc</span></span>|<span data-ttu-id="e2a50-196">映射函数（<xref:System.Activities.ActivityFunc%601><`DbDataReader`，`TResult`>），该函数采用在执行查询后获得的 `DataReader` 中的记录，并返回要添加到 `TResult` 集合的类型 `Result` 的对象的实例。</span><span class="sxs-lookup"><span data-stu-id="e2a50-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="e2a50-197">在这种情况下，将在多个执行脉冲中完成映射。</span><span class="sxs-lookup"><span data-stu-id="e2a50-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="e2a50-198">此函数可序列化为 XAML，并以声明方式进行创作（任何现有活动均可参与映射）。</span><span class="sxs-lookup"><span data-stu-id="e2a50-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="e2a50-199">结果</span><span class="sxs-lookup"><span data-stu-id="e2a50-199">Result</span></span>|<span data-ttu-id="e2a50-200">对象列表，这些对象是通过执行查询并对 `DataReader` 中的每个记录执行映射函数得到的。</span><span class="sxs-lookup"><span data-stu-id="e2a50-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="e2a50-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="e2a50-201">DbQueryDataSet</span></span>

<span data-ttu-id="e2a50-202">执行可返回 <xref:System.Data.DataSet> 的查询。</span><span class="sxs-lookup"><span data-stu-id="e2a50-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e2a50-203">此类以异步方式执行其工作。</span><span class="sxs-lookup"><span data-stu-id="e2a50-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="e2a50-204">它派生自 <xref:System.Activities.AsyncCodeActivity><`TResult`> 并使用其异步功能。</span><span class="sxs-lookup"><span data-stu-id="e2a50-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

<span data-ttu-id="e2a50-205">通过设置提供程序固定名称 (`ProviderName`) 和连接字符串 (`ConnectionString`)，或仅使用应用程序配置文件中的连接字符串配置名称 (`ConfigFileSectionName`)，可以配置连接信息。</span><span class="sxs-lookup"><span data-stu-id="e2a50-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

<span data-ttu-id="e2a50-206">要执行的查询在其 `Sql` 属性中配置，并通过 `Parameters` 集合传递参数。</span><span class="sxs-lookup"><span data-stu-id="e2a50-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

<span data-ttu-id="e2a50-207">执行 `DbQueryDataSet` 后，`DataSet` 将返回到 `Result out` 参数（类型 `TResult`，该参数在基类 <xref:System.Activities.AsyncCodeActivity%601>中定义）。</span><span class="sxs-lookup"><span data-stu-id="e2a50-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```csharp
public class DbQueryDataSet : AsyncCodeActivity<DataSet>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|<span data-ttu-id="e2a50-208">自变量</span><span class="sxs-lookup"><span data-stu-id="e2a50-208">Argument</span></span>|<span data-ttu-id="e2a50-209">描述</span><span class="sxs-lookup"><span data-stu-id="e2a50-209">Description</span></span>|
|-|-|
|<span data-ttu-id="e2a50-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="e2a50-210">ProviderName</span></span>|<span data-ttu-id="e2a50-211">ADO.NET 提供程序固定名称。</span><span class="sxs-lookup"><span data-stu-id="e2a50-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="e2a50-212">如果设置此自变量，则必须还要设置 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="e2a50-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="e2a50-213">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="e2a50-213">ConnectionString</span></span>|<span data-ttu-id="e2a50-214">用于连接到数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="e2a50-214">Connection string to connect to the database.</span></span> <span data-ttu-id="e2a50-215">如果设置此自变量，则必须还要设置 `ProviderName`。</span><span class="sxs-lookup"><span data-stu-id="e2a50-215">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="e2a50-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="e2a50-216">ConfigName</span></span>|<span data-ttu-id="e2a50-217">存储连接信息的配置文件部分的名称。</span><span class="sxs-lookup"><span data-stu-id="e2a50-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="e2a50-218">设置此自变量之后，将不再需要 `ProviderName` 和 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="e2a50-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="e2a50-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="e2a50-219">CommandType</span></span>|<span data-ttu-id="e2a50-220">要执行的 <xref:System.Data.Common.DbCommand> 的类型。</span><span class="sxs-lookup"><span data-stu-id="e2a50-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="e2a50-221">Sql</span><span class="sxs-lookup"><span data-stu-id="e2a50-221">Sql</span></span>|<span data-ttu-id="e2a50-222">要执行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="e2a50-222">The SQL command to be executed.</span></span>|
|<span data-ttu-id="e2a50-223">参数</span><span class="sxs-lookup"><span data-stu-id="e2a50-223">Parameters</span></span>|<span data-ttu-id="e2a50-224">SQL 查询的参数集合。</span><span class="sxs-lookup"><span data-stu-id="e2a50-224">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="e2a50-225">结果</span><span class="sxs-lookup"><span data-stu-id="e2a50-225">Result</span></span>|<span data-ttu-id="e2a50-226">执行查询后获得的 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="e2a50-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="e2a50-227">配置连接信息</span><span class="sxs-lookup"><span data-stu-id="e2a50-227">Configuring Connection Information</span></span>

<span data-ttu-id="e2a50-228">所有 DbActivities 共享相同的配置参数。</span><span class="sxs-lookup"><span data-stu-id="e2a50-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="e2a50-229">可以通过两种方式进行相关配置：</span><span class="sxs-lookup"><span data-stu-id="e2a50-229">They can be configured in two ways:</span></span>

- <span data-ttu-id="e2a50-230">`ConnectionString + InvariantName`：设置 ADO.NET 提供程序固定名称和连接字符串。</span><span class="sxs-lookup"><span data-stu-id="e2a50-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<DateTime>()
  {
      ProviderName = "System.Data.SqlClient",
      ConnectionString = @"Data Source=.\SQLExpress;
                            Initial Catalog=DbActivitiesSample;
                            Integrated Security=True",
      Sql = "SELECT GetDate()"
  };
  ```

- <span data-ttu-id="e2a50-231">`ConfigName`：设置包含连接信息的配置部分的名称。</span><span class="sxs-lookup"><span data-stu-id="e2a50-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

  ```xml
  <connectionStrings>
      <add name="DbActivitiesSample"
            providerName="System.Data.SqlClient"
            connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
    </connectionStrings>
  ```

- <span data-ttu-id="e2a50-232">在活动中：</span><span class="sxs-lookup"><span data-stu-id="e2a50-232">In the activity:</span></span>

  ```csharp
  Activity dbSelectCount = new DbQueryScalar<int>()
  {
      ConfigName = "DbActivitiesSample",
      Sql = "SELECT COUNT(*) FROM Roles"
  };
  ```

## <a name="running-this-sample"></a><span data-ttu-id="e2a50-233">运行此示例</span><span class="sxs-lookup"><span data-stu-id="e2a50-233">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="e2a50-234">设置说明</span><span class="sxs-lookup"><span data-stu-id="e2a50-234">Setup instructions</span></span>

<span data-ttu-id="e2a50-235">此示例使用一个数据库。</span><span class="sxs-lookup"><span data-stu-id="e2a50-235">This sample uses a database.</span></span> <span data-ttu-id="e2a50-236">此示例提供了一个安装和加载脚本 (Setup.cmd)。</span><span class="sxs-lookup"><span data-stu-id="e2a50-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="e2a50-237">必须使用命令提示执行该文件。</span><span class="sxs-lookup"><span data-stu-id="e2a50-237">You must execute that file using the command prompt.</span></span>

<span data-ttu-id="e2a50-238">Setup.cmd 脚本调用 CreateDb.sql 脚本文件，该文件包含可执行下列操作的 SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="e2a50-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

- <span data-ttu-id="e2a50-239">创建一个名为 DbActivitiesSample 的数据库。</span><span class="sxs-lookup"><span data-stu-id="e2a50-239">Creates a database called DbActivitiesSample.</span></span>

- <span data-ttu-id="e2a50-240">创建 Roles 表。</span><span class="sxs-lookup"><span data-stu-id="e2a50-240">Creates the Roles table.</span></span>

- <span data-ttu-id="e2a50-241">创建 Employees 表。</span><span class="sxs-lookup"><span data-stu-id="e2a50-241">Creates Employees table.</span></span>

- <span data-ttu-id="e2a50-242">将 3 个记录插入到 Roles 表中。</span><span class="sxs-lookup"><span data-stu-id="e2a50-242">Inserts three records into the Roles table.</span></span>

- <span data-ttu-id="e2a50-243">将 12 个记录插入到 Employees 表中。</span><span class="sxs-lookup"><span data-stu-id="e2a50-243">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="e2a50-244">运行 Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="e2a50-244">To run Setup.cmd</span></span>

1. <span data-ttu-id="e2a50-245">打开命令提示。</span><span class="sxs-lookup"><span data-stu-id="e2a50-245">Open a command prompt.</span></span>

2. <span data-ttu-id="e2a50-246">转到 DbActivities 示例文件夹。</span><span class="sxs-lookup"><span data-stu-id="e2a50-246">Go to the DbActivities sample folder.</span></span>

3. <span data-ttu-id="e2a50-247">键入 "setup .cmd"，然后按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="e2a50-247">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e2a50-248">Setup.cmd 尝试将此示例安装在您本地计算机的 SqlExpress 实例中。</span><span class="sxs-lookup"><span data-stu-id="e2a50-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="e2a50-249">如果您需要在其他 SQL Server 实例中安装它，请将 Setup.cmd 改为使用新的实例名称。</span><span class="sxs-lookup"><span data-stu-id="e2a50-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="e2a50-250">卸载示例数据库</span><span class="sxs-lookup"><span data-stu-id="e2a50-250">To uninstall the sample database</span></span>

1. <span data-ttu-id="e2a50-251">在命令提示中运行示例文件夹中的 Cleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="e2a50-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="e2a50-252">运行示例</span><span class="sxs-lookup"><span data-stu-id="e2a50-252">To run the sample</span></span>

1. <span data-ttu-id="e2a50-253">在 Visual Studio 2010 中打开解决方案</span><span class="sxs-lookup"><span data-stu-id="e2a50-253">Open the solution in Visual Studio 2010</span></span>

2. <span data-ttu-id="e2a50-254">若要编译解决方案，请按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="e2a50-254">To compile the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="e2a50-255">若要运行示例而不进行调试，按 Ctrl+F5。</span><span class="sxs-lookup"><span data-stu-id="e2a50-255">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e2a50-256">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="e2a50-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e2a50-257">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="e2a50-257">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e2a50-258">如果此目录不存在，请参阅[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）示例](https://www.microsoft.com/download/details.aspx?id=21459)以下载所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 示例。</span><span class="sxs-lookup"><span data-stu-id="e2a50-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e2a50-259">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="e2a50-259">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
