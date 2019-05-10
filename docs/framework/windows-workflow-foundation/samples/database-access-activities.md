---
title: 数据库访问活动
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: 5a7c6fa6664acee8000c100513b2cc955ffa3392
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622458"
---
# <a name="database-access-activities"></a><span data-ttu-id="47cd4-102">数据库访问活动</span><span class="sxs-lookup"><span data-stu-id="47cd4-102">Database Access Activities</span></span>
<span data-ttu-id="47cd4-103">数据库访问活动可用于在一个工作流内访问数据库。</span><span class="sxs-lookup"><span data-stu-id="47cd4-103">Database access activities allow you to access a database within a workflow.</span></span> <span data-ttu-id="47cd4-104">这些活动可以访问数据库以检索或修改信息并使用[ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081)来访问数据库。</span><span class="sxs-lookup"><span data-stu-id="47cd4-104">These activities allow accessing databases to retrieve or modify information and use [ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081) to access the database.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="47cd4-105">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="47cd4-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="47cd4-106">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="47cd4-106">Check for the following (default) directory before continuing.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples`
>
>  <span data-ttu-id="47cd4-107">如果此目录不存在，请转到 （下载页） 以下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。</span><span class="sxs-lookup"><span data-stu-id="47cd4-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="47cd4-108">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="47cd4-108">This sample is located in the following directory.</span></span>
>
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a><span data-ttu-id="47cd4-109">数据库活动</span><span class="sxs-lookup"><span data-stu-id="47cd4-109">Database Activities</span></span>
 <span data-ttu-id="47cd4-110">以下部分详细介绍了此示例中包含的活动列表。</span><span class="sxs-lookup"><span data-stu-id="47cd4-110">The following sections detail the list of activities included in this sample.</span></span>

## <a name="dbupdate"></a><span data-ttu-id="47cd4-111">DbUpdate</span><span class="sxs-lookup"><span data-stu-id="47cd4-111">DbUpdate</span></span>
 <span data-ttu-id="47cd4-112">执行可在数据库中产生修改（插入、更新、删除和其他修改）的 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="47cd4-112">Executes a SQL query that produces a modification in the database (insert, update, delete, and other modifications).</span></span>

 <span data-ttu-id="47cd4-113">此类采用异步方式执行其工作（它派生自 <xref:System.Activities.AsyncCodeActivity> 并使用其异步功能）。</span><span class="sxs-lookup"><span data-stu-id="47cd4-113">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="47cd4-114">通过设置提供程序固定名称 (`ProviderName`) 和连接字符串 (`ConnectionString`)，或仅使用应用程序配置文件中的连接字符串配置名称 (`ConfigFileSectionName`)，可以配置连接信息。</span><span class="sxs-lookup"><span data-stu-id="47cd4-114">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="47cd4-115">要执行的查询在其 `Sql` 属性中配置，并通过 `Parameters` 集合传递参数。</span><span class="sxs-lookup"><span data-stu-id="47cd4-115">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="47cd4-116">执行 `DbUpdate` 后，在 `AffectedRecords` 属性中返回受影响的记录的数量。</span><span class="sxs-lookup"><span data-stu-id="47cd4-116">After `DbUpdate` is executed, the number of affected records is returned in the `AffectedRecords` property.</span></span>

```
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

|<span data-ttu-id="47cd4-117">参数</span><span class="sxs-lookup"><span data-stu-id="47cd4-117">Argument</span></span>|<span data-ttu-id="47cd4-118">描述</span><span class="sxs-lookup"><span data-stu-id="47cd4-118">Description</span></span>|
|-|-|
|<span data-ttu-id="47cd4-119">ProviderName</span><span class="sxs-lookup"><span data-stu-id="47cd4-119">ProviderName</span></span>|<span data-ttu-id="47cd4-120">ADO.NET 提供程序固定名称。</span><span class="sxs-lookup"><span data-stu-id="47cd4-120">ADO.NET provider invariant name.</span></span> <span data-ttu-id="47cd4-121">如果设置此自变量，则必须还要设置 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="47cd4-121">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="47cd4-122">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="47cd4-122">ConnectionString</span></span>|<span data-ttu-id="47cd4-123">用于连接到数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="47cd4-123">Connection string to connect to the database.</span></span> <span data-ttu-id="47cd4-124">如果设置此自变量，则必须还要设置 `ProviderName`。</span><span class="sxs-lookup"><span data-stu-id="47cd4-124">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="47cd4-125">ConfigName</span><span class="sxs-lookup"><span data-stu-id="47cd4-125">ConfigName</span></span>|<span data-ttu-id="47cd4-126">存储连接信息的配置文件部分的名称。</span><span class="sxs-lookup"><span data-stu-id="47cd4-126">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="47cd4-127">设置此自变量之后，将不再需要 `ProviderName` 和 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="47cd4-127">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="47cd4-128">CommandType</span><span class="sxs-lookup"><span data-stu-id="47cd4-128">CommandType</span></span>|<span data-ttu-id="47cd4-129">要执行的 <xref:System.Data.Common.DbCommand> 的类型。</span><span class="sxs-lookup"><span data-stu-id="47cd4-129">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="47cd4-130">Sql</span><span class="sxs-lookup"><span data-stu-id="47cd4-130">Sql</span></span>|<span data-ttu-id="47cd4-131">要执行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="47cd4-131">The SQL command to be executed.</span></span>|
|<span data-ttu-id="47cd4-132">参数</span><span class="sxs-lookup"><span data-stu-id="47cd4-132">Parameters</span></span>|<span data-ttu-id="47cd4-133">SQL 查询的参数集合。</span><span class="sxs-lookup"><span data-stu-id="47cd4-133">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="47cd4-134">AffectedRecords</span><span class="sxs-lookup"><span data-stu-id="47cd4-134">AffectedRecords</span></span>|<span data-ttu-id="47cd4-135">最后一个操作影响的记录的数量。</span><span class="sxs-lookup"><span data-stu-id="47cd4-135">Number of records affected by the last operation.</span></span>|

## <a name="dbqueryscalar"></a><span data-ttu-id="47cd4-136">DbQueryScalar</span><span class="sxs-lookup"><span data-stu-id="47cd4-136">DbQueryScalar</span></span>
 <span data-ttu-id="47cd4-137">执行可从数据库检索单个值的查询。</span><span class="sxs-lookup"><span data-stu-id="47cd4-137">Executes a query that retrieves a single value from the database.</span></span>

 <span data-ttu-id="47cd4-138">此类采用异步方式执行其工作（它派生自 <xref:System.Activities.AsyncCodeActivity%601> 并使用其异步功能）。</span><span class="sxs-lookup"><span data-stu-id="47cd4-138">This class performs its work asynchronously (it derives from <xref:System.Activities.AsyncCodeActivity%601> and uses its asynchronous capabilities).</span></span>

 <span data-ttu-id="47cd4-139">通过设置提供程序固定名称 (`ProviderName`) 和连接字符串 (`ConnectionString`)，或仅使用应用程序配置文件中的连接字符串配置名称 (`ConfigFileSectionName`)，可以配置连接信息。</span><span class="sxs-lookup"><span data-stu-id="47cd4-139">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="47cd4-140">要执行的查询在其 `Sql` 属性中配置，并通过 `Parameters` 集合传递参数。</span><span class="sxs-lookup"><span data-stu-id="47cd4-140">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="47cd4-141">之后`DbQueryScalar`是执行，在返回标量`Result out`自变量 (类型的`TResult`，该基类中定义<xref:System.Activities.AsyncCodeActivity%601>)。</span><span class="sxs-lookup"><span data-stu-id="47cd4-141">After `DbQueryScalar` is executed, the scalar is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```
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

|<span data-ttu-id="47cd4-142">参数</span><span class="sxs-lookup"><span data-stu-id="47cd4-142">Argument</span></span>|<span data-ttu-id="47cd4-143">描述</span><span class="sxs-lookup"><span data-stu-id="47cd4-143">Description</span></span>|
|-|-|
|<span data-ttu-id="47cd4-144">ProviderName</span><span class="sxs-lookup"><span data-stu-id="47cd4-144">ProviderName</span></span>|<span data-ttu-id="47cd4-145">ADO.NET 提供程序固定名称。</span><span class="sxs-lookup"><span data-stu-id="47cd4-145">ADO.NET provider invariant name.</span></span> <span data-ttu-id="47cd4-146">如果设置此自变量，则必须还要设置 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="47cd4-146">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="47cd4-147">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="47cd4-147">ConnectionString</span></span>|<span data-ttu-id="47cd4-148">用于连接到数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="47cd4-148">Connection string to connect to the database.</span></span> <span data-ttu-id="47cd4-149">如果设置此自变量，则必须还要设置 `ProviderName`。</span><span class="sxs-lookup"><span data-stu-id="47cd4-149">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="47cd4-150">ConfigName</span><span class="sxs-lookup"><span data-stu-id="47cd4-150">ConfigName</span></span>|<span data-ttu-id="47cd4-151">存储连接信息的配置文件部分的名称。</span><span class="sxs-lookup"><span data-stu-id="47cd4-151">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="47cd4-152">设置此自变量之后，将不再需要 `ProviderName` 和 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="47cd4-152">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="47cd4-153">CommandType</span><span class="sxs-lookup"><span data-stu-id="47cd4-153">CommandType</span></span>|<span data-ttu-id="47cd4-154">要执行的 <xref:System.Data.Common.DbCommand> 的类型。</span><span class="sxs-lookup"><span data-stu-id="47cd4-154">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="47cd4-155">Sql</span><span class="sxs-lookup"><span data-stu-id="47cd4-155">Sql</span></span>|<span data-ttu-id="47cd4-156">要执行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="47cd4-156">The SQL command to be executed.</span></span>|
|<span data-ttu-id="47cd4-157">参数</span><span class="sxs-lookup"><span data-stu-id="47cd4-157">Parameters</span></span>|<span data-ttu-id="47cd4-158">SQL 查询的参数集合。</span><span class="sxs-lookup"><span data-stu-id="47cd4-158">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="47cd4-159">结果</span><span class="sxs-lookup"><span data-stu-id="47cd4-159">Result</span></span>|<span data-ttu-id="47cd4-160">执行查询后获得的标量。</span><span class="sxs-lookup"><span data-stu-id="47cd4-160">Scalar that is obtained after the query is executed.</span></span> <span data-ttu-id="47cd4-161">此自变量的类型为 `TResult`。</span><span class="sxs-lookup"><span data-stu-id="47cd4-161">This argument is of type `TResult`.</span></span>|

## <a name="dbquery"></a><span data-ttu-id="47cd4-162">DbQuery</span><span class="sxs-lookup"><span data-stu-id="47cd4-162">DbQuery</span></span>
 <span data-ttu-id="47cd4-163">执行可检索对象列表的查询。</span><span class="sxs-lookup"><span data-stu-id="47cd4-163">Executes a query that retrieves a list of objects.</span></span> <span data-ttu-id="47cd4-164">执行查询后，将执行映射函数 (它可以是<xref:System.Func%601> < `DbDataReader`， `TResult`> 或者<xref:System.Activities.ActivityFunc%601> < `DbDataReader`， `TResult`>)。</span><span class="sxs-lookup"><span data-stu-id="47cd4-164">After the query is executed, a mapping function is executed (it can be <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>).</span></span> <span data-ttu-id="47cd4-165">此映射函数在 `DbDataReader` 中获取一个记录，并将其映射到要返回的对象。</span><span class="sxs-lookup"><span data-stu-id="47cd4-165">This mapping function gets a record in a `DbDataReader` and maps it to the object to be returned.</span></span>

 <span data-ttu-id="47cd4-166">通过设置提供程序固定名称 (`ProviderName`) 和连接字符串 (`ConnectionString`)，或仅使用应用程序配置文件中的连接字符串配置名称 (`ConfigFileSectionName`)，可以配置连接信息。</span><span class="sxs-lookup"><span data-stu-id="47cd4-166">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="47cd4-167">要执行的查询在其 `Sql` 属性中配置，并通过 `Parameters` 集合传递参数。</span><span class="sxs-lookup"><span data-stu-id="47cd4-167">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="47cd4-168">使用 `DbDataReader` 检索 SQL 查询的结果。</span><span class="sxs-lookup"><span data-stu-id="47cd4-168">The results of the SQL query are retrieved using a `DbDataReader`.</span></span> <span data-ttu-id="47cd4-169">此活动将循环访问 `DbDataReader`，并将 `DbDataReader` 中的行映射到 `TResult` 的实例。</span><span class="sxs-lookup"><span data-stu-id="47cd4-169">The activity iterates through the `DbDataReader` and maps the rows in the `DbDataReader` to an instance of `TResult`.</span></span> <span data-ttu-id="47cd4-170">用户`DbQuery`必须提供映射代码，这可以通过两种方式： 使用<xref:System.Func%601> < `DbDataReader`， `TResult`> 或<xref:System.Activities.ActivityFunc%601> < `DbDataReader`， `TResult`>。</span><span class="sxs-lookup"><span data-stu-id="47cd4-170">The user of `DbQuery` has to provide the mapping code and this can be done in two ways: using a <xref:System.Func%601><`DbDataReader`, `TResult`> or an <xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>.</span></span> <span data-ttu-id="47cd4-171">在第一种情况下，将在单个执行脉冲中完成映射。</span><span class="sxs-lookup"><span data-stu-id="47cd4-171">In the first case, the map is done in a single pulse of execution.</span></span> <span data-ttu-id="47cd4-172">因此，此方法的速度更快，但无法序列化为 XAML。</span><span class="sxs-lookup"><span data-stu-id="47cd4-172">Therefore, it is faster, but this cannot be serialized to XAML.</span></span> <span data-ttu-id="47cd4-173">在后一种情况下，将在多个脉冲中完成映射。</span><span class="sxs-lookup"><span data-stu-id="47cd4-173">In the last case, the map is performed in multiple pulses.</span></span> <span data-ttu-id="47cd4-174">因此，此方法的速度较慢，但可序列化为 XAML，并以声明方式进行创作（任何现有活动均可参与映射）。</span><span class="sxs-lookup"><span data-stu-id="47cd4-174">Therefore, it might be slower but can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>

```
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

|<span data-ttu-id="47cd4-175">参数</span><span class="sxs-lookup"><span data-stu-id="47cd4-175">Argument</span></span>|<span data-ttu-id="47cd4-176">描述</span><span class="sxs-lookup"><span data-stu-id="47cd4-176">Description</span></span>|
|-|-|
|<span data-ttu-id="47cd4-177">ProviderName</span><span class="sxs-lookup"><span data-stu-id="47cd4-177">ProviderName</span></span>|<span data-ttu-id="47cd4-178">ADO.NET 提供程序固定名称。</span><span class="sxs-lookup"><span data-stu-id="47cd4-178">ADO.NET provider invariant name.</span></span> <span data-ttu-id="47cd4-179">如果设置此自变量，则必须还要设置 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="47cd4-179">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="47cd4-180">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="47cd4-180">ConnectionString</span></span>|<span data-ttu-id="47cd4-181">用于连接到数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="47cd4-181">Connection string to connect to the database.</span></span> <span data-ttu-id="47cd4-182">如果设置此自变量，则必须还要设置 `ProviderName`。</span><span class="sxs-lookup"><span data-stu-id="47cd4-182">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="47cd4-183">ConfigName</span><span class="sxs-lookup"><span data-stu-id="47cd4-183">ConfigName</span></span>|<span data-ttu-id="47cd4-184">存储连接信息的配置文件部分的名称。</span><span class="sxs-lookup"><span data-stu-id="47cd4-184">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="47cd4-185">设置此自变量之后，将不再需要 `ProviderName` 和 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="47cd4-185">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="47cd4-186">CommandType</span><span class="sxs-lookup"><span data-stu-id="47cd4-186">CommandType</span></span>|<span data-ttu-id="47cd4-187">要执行的 <xref:System.Data.Common.DbCommand> 的类型。</span><span class="sxs-lookup"><span data-stu-id="47cd4-187">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="47cd4-188">Sql</span><span class="sxs-lookup"><span data-stu-id="47cd4-188">Sql</span></span>|<span data-ttu-id="47cd4-189">要执行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="47cd4-189">The SQL command to be executed.</span></span>|
|<span data-ttu-id="47cd4-190">参数</span><span class="sxs-lookup"><span data-stu-id="47cd4-190">Parameters</span></span>|<span data-ttu-id="47cd4-191">SQL 查询的参数集合。</span><span class="sxs-lookup"><span data-stu-id="47cd4-191">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="47cd4-192">Mapper</span><span class="sxs-lookup"><span data-stu-id="47cd4-192">Mapper</span></span>|<span data-ttu-id="47cd4-193">映射函数 (<xref:System.Func%601><`DbDataReader`， `TResult`>) 记录，采用`DataReader`接受在执行查询后获得和返回类型的对象的实例`TResult`要添加到`Result`集合。</span><span class="sxs-lookup"><span data-stu-id="47cd4-193">Mapping function (<xref:System.Func%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="47cd4-194">在这种情况下，将在单个执行脉冲中完成映射，但不能使用设计器以声明方式创作它。</span><span class="sxs-lookup"><span data-stu-id="47cd4-194">In this case, mapping is done in a single pulse of execution, but it cannot be authored declaratively using the designer.</span></span>|
|<span data-ttu-id="47cd4-195">MapperFunc</span><span class="sxs-lookup"><span data-stu-id="47cd4-195">MapperFunc</span></span>|<span data-ttu-id="47cd4-196">映射函数 (<xref:System.Activities.ActivityFunc%601><`DbDataReader`， `TResult`>) 记录，采用`DataReader`接受在执行查询后获得和返回类型的对象的实例`TResult`要添加到`Result`集合。</span><span class="sxs-lookup"><span data-stu-id="47cd4-196">Mapping function (<xref:System.Activities.ActivityFunc%601><`DbDataReader`, `TResult`>) that takes a record in the `DataReader` obtained as result of executing the query and returns an instance of an object of type `TResult` to be added to the `Result` collection.</span></span><br /><br /> <span data-ttu-id="47cd4-197">在这种情况下，将在多个执行脉冲中完成映射。</span><span class="sxs-lookup"><span data-stu-id="47cd4-197">In this case, the mapping is done in multiple pulses of execution.</span></span> <span data-ttu-id="47cd4-198">此函数可序列化为 XAML，并以声明方式进行创作（任何现有活动均可参与映射）。</span><span class="sxs-lookup"><span data-stu-id="47cd4-198">This function can be serialized to XAML and authored declaratively (any existing activity can participate in the mapping).</span></span>|
|<span data-ttu-id="47cd4-199">结果</span><span class="sxs-lookup"><span data-stu-id="47cd4-199">Result</span></span>|<span data-ttu-id="47cd4-200">对象列表，这些对象是通过执行查询并对 `DataReader` 中的每个记录执行映射函数得到的。</span><span class="sxs-lookup"><span data-stu-id="47cd4-200">List of objects obtained as result of executing the query and executing the mapping function for each record in the `DataReader`.</span></span>|

## <a name="dbquerydataset"></a><span data-ttu-id="47cd4-201">DbQueryDataSet</span><span class="sxs-lookup"><span data-stu-id="47cd4-201">DbQueryDataSet</span></span>
 <span data-ttu-id="47cd4-202">执行可返回 <xref:System.Data.DataSet> 的查询。</span><span class="sxs-lookup"><span data-stu-id="47cd4-202">Executes a query that returns a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="47cd4-203">此类以异步方式执行其工作。</span><span class="sxs-lookup"><span data-stu-id="47cd4-203">This class performs its work asynchronously.</span></span> <span data-ttu-id="47cd4-204">它派生<xref:System.Activities.AsyncCodeActivity> < `TResult`> 并使用其异步功能。</span><span class="sxs-lookup"><span data-stu-id="47cd4-204">It derives from <xref:System.Activities.AsyncCodeActivity><`TResult`> and uses its asynchronous capabilities.</span></span>

 <span data-ttu-id="47cd4-205">通过设置提供程序固定名称 (`ProviderName`) 和连接字符串 (`ConnectionString`)，或仅使用应用程序配置文件中的连接字符串配置名称 (`ConfigFileSectionName`)，可以配置连接信息。</span><span class="sxs-lookup"><span data-stu-id="47cd4-205">The connection information can be configured by setting a provider invariant name (`ProviderName`) and the connection string (`ConnectionString`) or just using a connection string configuration name (`ConfigFileSectionName`) from the application configuration file.</span></span>

 <span data-ttu-id="47cd4-206">要执行的查询在其 `Sql` 属性中配置，并通过 `Parameters` 集合传递参数。</span><span class="sxs-lookup"><span data-stu-id="47cd4-206">The query to be executed is configured in its `Sql` property and the parameters are passed through the `Parameters` collection.</span></span>

 <span data-ttu-id="47cd4-207">之后`DbQueryDataSet`执行`DataSet`中返回`Result out`自变量 (类型的`TResult`，该基类中定义<xref:System.Activities.AsyncCodeActivity%601>)。</span><span class="sxs-lookup"><span data-stu-id="47cd4-207">After the `DbQueryDataSet` is executed the `DataSet` is returned in the `Result out` argument (of type `TResult`, that is defined in the base class <xref:System.Activities.AsyncCodeActivity%601>).</span></span>

```
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

|<span data-ttu-id="47cd4-208">参数</span><span class="sxs-lookup"><span data-stu-id="47cd4-208">Argument</span></span>|<span data-ttu-id="47cd4-209">描述</span><span class="sxs-lookup"><span data-stu-id="47cd4-209">Description</span></span>|
|-|-|
|<span data-ttu-id="47cd4-210">ProviderName</span><span class="sxs-lookup"><span data-stu-id="47cd4-210">ProviderName</span></span>|<span data-ttu-id="47cd4-211">ADO.NET 提供程序固定名称。</span><span class="sxs-lookup"><span data-stu-id="47cd4-211">ADO.NET provider invariant name.</span></span> <span data-ttu-id="47cd4-212">如果设置此自变量，则必须还要设置 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="47cd4-212">If this argument is set, then the `ConnectionString` must also be set.</span></span>|
|<span data-ttu-id="47cd4-213">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="47cd4-213">ConnectionString</span></span>|<span data-ttu-id="47cd4-214">用于连接到数据库的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="47cd4-214">Connection string to connect to the database.</span></span> <span data-ttu-id="47cd4-215">如果设置此自变量，则必须还要设置 `ProviderName`。</span><span class="sxs-lookup"><span data-stu-id="47cd4-215">If this argument is set, then `ProviderName` must also be set.</span></span>|
|<span data-ttu-id="47cd4-216">ConfigName</span><span class="sxs-lookup"><span data-stu-id="47cd4-216">ConfigName</span></span>|<span data-ttu-id="47cd4-217">存储连接信息的配置文件部分的名称。</span><span class="sxs-lookup"><span data-stu-id="47cd4-217">Name of the configuration file section where the connection information is stored.</span></span> <span data-ttu-id="47cd4-218">设置此自变量之后，将不再需要 `ProviderName` 和 `ConnectionString`。</span><span class="sxs-lookup"><span data-stu-id="47cd4-218">When this argument is set `ProviderName` and `ConnectionString` are not required.</span></span>|
|<span data-ttu-id="47cd4-219">CommandType</span><span class="sxs-lookup"><span data-stu-id="47cd4-219">CommandType</span></span>|<span data-ttu-id="47cd4-220">要执行的 <xref:System.Data.Common.DbCommand> 的类型。</span><span class="sxs-lookup"><span data-stu-id="47cd4-220">Type of the <xref:System.Data.Common.DbCommand> to be executed.</span></span>|
|<span data-ttu-id="47cd4-221">Sql</span><span class="sxs-lookup"><span data-stu-id="47cd4-221">Sql</span></span>|<span data-ttu-id="47cd4-222">要执行的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="47cd4-222">The SQL command to be executed.</span></span>|
|<span data-ttu-id="47cd4-223">参数</span><span class="sxs-lookup"><span data-stu-id="47cd4-223">Parameters</span></span>|<span data-ttu-id="47cd4-224">SQL 查询的参数集合。</span><span class="sxs-lookup"><span data-stu-id="47cd4-224">Collection of the parameters of the SQL query.</span></span>|
|<span data-ttu-id="47cd4-225">结果</span><span class="sxs-lookup"><span data-stu-id="47cd4-225">Result</span></span>|<span data-ttu-id="47cd4-226">执行查询后获得的 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="47cd4-226"><xref:System.Data.DataSet> that is obtained after the query is executed.</span></span>|

## <a name="configuring-connection-information"></a><span data-ttu-id="47cd4-227">配置连接信息</span><span class="sxs-lookup"><span data-stu-id="47cd4-227">Configuring Connection Information</span></span>
 <span data-ttu-id="47cd4-228">所有 DbActivities 共享相同的配置参数。</span><span class="sxs-lookup"><span data-stu-id="47cd4-228">All DbActivities share the same configuration parameters.</span></span> <span data-ttu-id="47cd4-229">可以通过两种方式进行相关配置：</span><span class="sxs-lookup"><span data-stu-id="47cd4-229">They can be configured in two ways:</span></span>

- <span data-ttu-id="47cd4-230">`ConnectionString + InvariantName`：设置 ADO.NET 提供程序固定名称和连接字符串。</span><span class="sxs-lookup"><span data-stu-id="47cd4-230">`ConnectionString + InvariantName`: Set the ADO.NET provider invariant name and connection string.</span></span>

    ```
    Activity dbSelectCount = new DbQueryScalar<DateTime>()
    {
        ProviderName = "System.Data.SqlClient",
        ConnectionString = @"Data Source=.\SQLExpress;
                             Initial Catalog=DbActivitiesSample;
                             Integrated Security=True",
        Sql = "SELECT GetDate()"
    };
    ```

- <span data-ttu-id="47cd4-231">`ConfigName`：设置包含连接信息的配置节的名称。</span><span class="sxs-lookup"><span data-stu-id="47cd4-231">`ConfigName`: Set the name of the configuration section that contains the connection information.</span></span>

    ```xml
    <connectionStrings>
        <add name="DbActivitiesSample"
             providerName="System.Data.SqlClient"
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
      </connectionStrings>
    ```

- <span data-ttu-id="47cd4-232">在活动中：</span><span class="sxs-lookup"><span data-stu-id="47cd4-232">In the activity:</span></span>

    ```
    Activity dbSelectCount = new DbQueryScalar<int>()
    {
        ConfigName = "DbActivitiesSample",
        Sql = "SELECT COUNT(*) FROM Roles"
    };
    ```

## <a name="running-this-sample"></a><span data-ttu-id="47cd4-233">运行此示例</span><span class="sxs-lookup"><span data-stu-id="47cd4-233">Running this sample</span></span>

### <a name="setup-instructions"></a><span data-ttu-id="47cd4-234">设置说明</span><span class="sxs-lookup"><span data-stu-id="47cd4-234">Setup instructions</span></span>
 <span data-ttu-id="47cd4-235">此示例使用一个数据库。</span><span class="sxs-lookup"><span data-stu-id="47cd4-235">This sample uses a database.</span></span> <span data-ttu-id="47cd4-236">此示例提供了一个安装和加载脚本 (Setup.cmd)。</span><span class="sxs-lookup"><span data-stu-id="47cd4-236">A set-up and load script (Setup.cmd) is provided with the sample.</span></span> <span data-ttu-id="47cd4-237">必须使用命令提示执行该文件。</span><span class="sxs-lookup"><span data-stu-id="47cd4-237">You must execute that file using the command prompt.</span></span>

 <span data-ttu-id="47cd4-238">Setup.cmd 脚本调用 CreateDb.sql 脚本文件，该文件包含可执行下列操作的 SQL 命令：</span><span class="sxs-lookup"><span data-stu-id="47cd4-238">The Setup.cmd script invokes the CreateDb.sql script file, which contains SQL commands that do the following:</span></span>

- <span data-ttu-id="47cd4-239">创建一个名为 DbActivitiesSample 的数据库。</span><span class="sxs-lookup"><span data-stu-id="47cd4-239">Creates a database called DbActivitiesSample.</span></span>

- <span data-ttu-id="47cd4-240">创建 Roles 表。</span><span class="sxs-lookup"><span data-stu-id="47cd4-240">Creates the Roles table.</span></span>

- <span data-ttu-id="47cd4-241">创建 Employees 表。</span><span class="sxs-lookup"><span data-stu-id="47cd4-241">Creates Employees table.</span></span>

- <span data-ttu-id="47cd4-242">将 3 个记录插入到 Roles 表中。</span><span class="sxs-lookup"><span data-stu-id="47cd4-242">Inserts three records into the Roles table.</span></span>

- <span data-ttu-id="47cd4-243">将 12 个记录插入到 Employees 表中。</span><span class="sxs-lookup"><span data-stu-id="47cd4-243">Inserts twelve records into the Employees table.</span></span>

##### <a name="to-run-setupcmd"></a><span data-ttu-id="47cd4-244">运行 Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="47cd4-244">To run Setup.cmd</span></span>

1. <span data-ttu-id="47cd4-245">打开命令提示。</span><span class="sxs-lookup"><span data-stu-id="47cd4-245">Open a command prompt.</span></span>

2. <span data-ttu-id="47cd4-246">转到 DbActivities 示例文件夹。</span><span class="sxs-lookup"><span data-stu-id="47cd4-246">Go to the DbActivities sample folder.</span></span>

3. <span data-ttu-id="47cd4-247">键入"setup.cmd"，然后按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="47cd4-247">Type "setup.cmd" and press ENTER.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="47cd4-248">Setup.cmd 尝试将此示例安装在您本地计算机的 SqlExpress 实例中。</span><span class="sxs-lookup"><span data-stu-id="47cd4-248">Setup.cmd attempts to install the sample in your local machine SqlExpress instance.</span></span> <span data-ttu-id="47cd4-249">如果您需要在其他 SQL Server 实例中安装它，请将 Setup.cmd 改为使用新的实例名称。</span><span class="sxs-lookup"><span data-stu-id="47cd4-249">If you want to install it in other SQL server instance, edit Setup.cmd with the new instance name.</span></span>

##### <a name="to-uninstall-the-sample-database"></a><span data-ttu-id="47cd4-250">卸载示例数据库</span><span class="sxs-lookup"><span data-stu-id="47cd4-250">To uninstall the sample database</span></span>

1. <span data-ttu-id="47cd4-251">在命令提示中运行示例文件夹中的 Cleanup.cmd。</span><span class="sxs-lookup"><span data-stu-id="47cd4-251">Run Cleanup.cmd from the sample folder in a command prompt.</span></span>

##### <a name="to-run-the-sample"></a><span data-ttu-id="47cd4-252">运行示例</span><span class="sxs-lookup"><span data-stu-id="47cd4-252">To run the sample</span></span>

1. <span data-ttu-id="47cd4-253">在 Visual Studio 2010 中打开解决方案</span><span class="sxs-lookup"><span data-stu-id="47cd4-253">Open the solution in Visual Studio 2010</span></span>

2. <span data-ttu-id="47cd4-254">若要编译解决方案，请按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="47cd4-254">To compile the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="47cd4-255">若要运行示例而不进行调试，按 Ctrl+F5。</span><span class="sxs-lookup"><span data-stu-id="47cd4-255">To run the sample without debugging, press CTRL+F5.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="47cd4-256">您的计算机上可能已安装这些示例。</span><span class="sxs-lookup"><span data-stu-id="47cd4-256">The samples may already be installed on your machine.</span></span> <span data-ttu-id="47cd4-257">在继续操作之前，请先检查以下（默认）目录：</span><span class="sxs-lookup"><span data-stu-id="47cd4-257">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="47cd4-258">如果此目录不存在，请转到[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 示例](https://go.microsoft.com/fwlink/?LinkId=150780)若要下载所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]示例。</span><span class="sxs-lookup"><span data-stu-id="47cd4-258">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="47cd4-259">此示例位于以下目录：</span><span class="sxs-lookup"><span data-stu-id="47cd4-259">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
