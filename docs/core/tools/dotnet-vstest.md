---
title: dotnet vstest 命令
description: dotnet vstest 命令可生成项目及其所有依赖项。
author: mairaw
ms.date: 05/30/2018
ms.openlocfilehash: 4630982ba21ab37b051895faf3dc0fcd8784cb18
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202781"
---
# <a name="dotnet-vstest"></a><span data-ttu-id="e8144-103">dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="e8144-103">dotnet vstest</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="e8144-104">name</span><span class="sxs-lookup"><span data-stu-id="e8144-104">Name</span></span>

<span data-ttu-id="e8144-105">`dotnet-vstest` - 从指定文件运行测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-105">`dotnet-vstest` - Runs tests from the specified files.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e8144-106">摘要</span><span class="sxs-lookup"><span data-stu-id="e8144-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e8144-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e8144-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [--Blame|/Blame] [--InIsolation|/InIsolation]
    [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="e8144-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="e8144-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath] 
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger]
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e8144-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="e8144-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet vstest [<TEST_FILE_NAMES>] [--Settings|/Settings] [--Tests|/Tests] [--TestAdapterPath|/TestAdapterPath]
    [--Platform|/Platform] [--Framework|/Framework] [--Parallel|/Parallel] [--TestCaseFilter|/TestCaseFilter] [--logger|/logger] 
    [-lt|--ListTests|/lt|/ListTests] [--ParentProcessId|/ParentProcessId] [--Port|/Port] [--Diag|/Diag] [[--] <args>...]] [-?|--Help|/?|/Help]
```

---

## <a name="description"></a><span data-ttu-id="e8144-110">说明</span><span class="sxs-lookup"><span data-stu-id="e8144-110">Description</span></span>

<span data-ttu-id="e8144-111">`dotnet-vstest` 命令运行 `VSTest.Console` 命令行应用程序以运行自动化单元测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-111">The `dotnet-vstest` command runs the `VSTest.Console` command-line application to run automated unit tests.</span></span>

## <a name="arguments"></a><span data-ttu-id="e8144-112">自变量</span><span class="sxs-lookup"><span data-stu-id="e8144-112">Arguments</span></span>

`TEST_FILE_NAMES`

<span data-ttu-id="e8144-113">从指定的程序集运行测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-113">Run tests from the specified assemblies.</span></span> <span data-ttu-id="e8144-114">用空格分隔多个测试程序集名称。</span><span class="sxs-lookup"><span data-stu-id="e8144-114">Separate multiple test assembly names with spaces.</span></span>

## <a name="options"></a><span data-ttu-id="e8144-115">选项</span><span class="sxs-lookup"><span data-stu-id="e8144-115">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e8144-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="e8144-116">.NET Core 2.1</span></span>](#tab/netcore21)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="e8144-117">运行测试时要使用的设置。</span><span class="sxs-lookup"><span data-stu-id="e8144-117">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="e8144-118">运行具有与提供的值匹配的名称的测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-118">Run tests with names that match the provided values.</span></span> <span data-ttu-id="e8144-119">用逗号分隔多个值。</span><span class="sxs-lookup"><span data-stu-id="e8144-119">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="e8144-120">在测试运行中使用来自给定路径（如果有）的自定义测试适配器。</span><span class="sxs-lookup"><span data-stu-id="e8144-120">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="e8144-121">用于执行测试的目标平台体系结构。</span><span class="sxs-lookup"><span data-stu-id="e8144-121">Target platform architecture used for test execution.</span></span> <span data-ttu-id="e8144-122">有效值为 `x86`、`x64` 和 `ARM`。</span><span class="sxs-lookup"><span data-stu-id="e8144-122">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="e8144-123">用于测试执行的目标 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="e8144-123">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="e8144-124">有效值的示例为 `.NETFramework,Version=v4.6` 或 `.NETCoreApp,Version=v1.0`。</span><span class="sxs-lookup"><span data-stu-id="e8144-124">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="e8144-125">其他支持的值为 `Framework40`、`Framework45`、`FrameworkCore10` 和 `FrameworkUap10`。</span><span class="sxs-lookup"><span data-stu-id="e8144-125">Other supported values are `Framework40`, `Framework45`, `FrameworkCore10`, and `FrameworkUap10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="e8144-126">并行执行测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-126">Execute tests in parallel.</span></span> <span data-ttu-id="e8144-127">默认情况下，计算机上的所有可用内核都可供使用。</span><span class="sxs-lookup"><span data-stu-id="e8144-127">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="e8144-128">通过在 runsettings 文件的 RunConfiguration 节点下设置 MaxCpuCount 属性来指定显式内核数。</span><span class="sxs-lookup"><span data-stu-id="e8144-128">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="e8144-129">运行与给定表达式匹配的测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-129">Run tests that match the given expression.</span></span> <span data-ttu-id="e8144-130">`<Expression>` 的格式为 `<property>Operator<value>[|&<Expression>]`，其中运算符是 `=`、`!=` 或 `~` 之一。</span><span class="sxs-lookup"><span data-stu-id="e8144-130">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="e8144-131">运算符 `~` 具有“包含”语义，并适用于字符串属性，如 `DisplayName`。</span><span class="sxs-lookup"><span data-stu-id="e8144-131">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="e8144-132">括号 `()` 用于组的子表达式。</span><span class="sxs-lookup"><span data-stu-id="e8144-132">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="e8144-133">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="e8144-133">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="e8144-134">为测试结果指定一个记录器。</span><span class="sxs-lookup"><span data-stu-id="e8144-134">Specify a logger for test results.</span></span>

* <span data-ttu-id="e8144-135">若要将测试结果发布到 Team Foundation Server，请使用 `TfsPublisher` 记录器提供程序：</span><span class="sxs-lookup"><span data-stu-id="e8144-135">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="e8144-136">若要将结果记录到 Visual Studio 测试结果文件 (TRX)，请使用 `trx` 记录器提供程序。</span><span class="sxs-lookup"><span data-stu-id="e8144-136">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="e8144-137">此开关使用给定的日志文件名在测试结果目录中创建一个文件。</span><span class="sxs-lookup"><span data-stu-id="e8144-137">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="e8144-138">如果未提供 `LogFileName`，将创建唯一的文件名以保留测试结果。</span><span class="sxs-lookup"><span data-stu-id="e8144-138">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="e8144-139">列出给定测试容器中所有已发现的测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-139">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="e8144-140">父进程的进程 ID 负责启动当前进程。</span><span class="sxs-lookup"><span data-stu-id="e8144-140">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="e8144-141">指定套接字连接和接收事件消息的端口。</span><span class="sxs-lookup"><span data-stu-id="e8144-141">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="e8144-142">为测试平台启用详细日志。</span><span class="sxs-lookup"><span data-stu-id="e8144-142">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="e8144-143">日志被写入到所提供的文件。</span><span class="sxs-lookup"><span data-stu-id="e8144-143">Logs are written to the provided file.</span></span>

`--Blame|/Blame`

<span data-ttu-id="e8144-144">在意见模式中运行测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-144">Runs the tests in blame mode.</span></span> <span data-ttu-id="e8144-145">此选项有助于隔离导致测试主机出现故障的有问题的测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-145">This option is helpful in isolating the problematic tests causing test host to crash.</span></span> <span data-ttu-id="e8144-146">它会在当前目录中创建一个输出文件 (Sequence.xml)，其中捕获了故障前的测试执行顺序  。</span><span class="sxs-lookup"><span data-stu-id="e8144-146">It creates an output file in the current directory as *Sequence.xml* that captures the order of tests execution before the crash.</span></span>

`--InIsolation|/InIsolation`

<span data-ttu-id="e8144-147">在隔离的进程中运行测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-147">Runs the tests in an isolated process.</span></span> <span data-ttu-id="e8144-148">虽然这使得 vstest.console.exe 进程不太可能在测试出错时停止，但测试的运行速度会较慢  。</span><span class="sxs-lookup"><span data-stu-id="e8144-148">This makes *vstest.console.exe* process less likely to be stopped on an error in the tests, but tests may run slower.</span></span>

`@<file>`

<span data-ttu-id="e8144-149">有关更多选项，请阅读响应文件。</span><span class="sxs-lookup"><span data-stu-id="e8144-149">Reads response file for more options.</span></span>

`args`

<span data-ttu-id="e8144-150">指定要传递到适配器的额外参数。</span><span class="sxs-lookup"><span data-stu-id="e8144-150">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="e8144-151">参数被指定为 `<n>=<v>` 格式的名称值对，其中 `<n>` 是参数名称，`<v>` 是参数值。</span><span class="sxs-lookup"><span data-stu-id="e8144-151">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="e8144-152">使用空格分隔多个参数。</span><span class="sxs-lookup"><span data-stu-id="e8144-152">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="e8144-153">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="e8144-153">.NET Core 2.0</span></span>](#tab/netcore20)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="e8144-154">运行测试时要使用的设置。</span><span class="sxs-lookup"><span data-stu-id="e8144-154">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="e8144-155">运行具有与提供的值匹配的名称的测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-155">Run tests with names that match the provided values.</span></span> <span data-ttu-id="e8144-156">用逗号分隔多个值。</span><span class="sxs-lookup"><span data-stu-id="e8144-156">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="e8144-157">在测试运行中使用来自给定路径（如果有）的自定义测试适配器。</span><span class="sxs-lookup"><span data-stu-id="e8144-157">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="e8144-158">用于执行测试的目标平台体系结构。</span><span class="sxs-lookup"><span data-stu-id="e8144-158">Target platform architecture used for test execution.</span></span> <span data-ttu-id="e8144-159">有效值为 `x86`、`x64` 和 `ARM`。</span><span class="sxs-lookup"><span data-stu-id="e8144-159">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="e8144-160">用于测试执行的目标 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="e8144-160">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="e8144-161">有效值的示例为 `.NETFramework,Version=v4.6` 或 `.NETCoreApp,Version=v1.0`。</span><span class="sxs-lookup"><span data-stu-id="e8144-161">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="e8144-162">其他支持的值为 `Framework40`、`Framework45` 和 `FrameworkCore10`。</span><span class="sxs-lookup"><span data-stu-id="e8144-162">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="e8144-163">并行执行测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-163">Execute tests in parallel.</span></span> <span data-ttu-id="e8144-164">默认情况下，计算机上的所有可用内核都可供使用。</span><span class="sxs-lookup"><span data-stu-id="e8144-164">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="e8144-165">通过在 runsettings 文件的 RunConfiguration 节点下设置 MaxCpuCount 属性来指定显式内核数。</span><span class="sxs-lookup"><span data-stu-id="e8144-165">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="e8144-166">运行与给定表达式匹配的测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-166">Run tests that match the given expression.</span></span> <span data-ttu-id="e8144-167">`<Expression>` 的格式为 `<property>Operator<value>[|&<Expression>]`，其中运算符是 `=`、`!=` 或 `~` 之一。</span><span class="sxs-lookup"><span data-stu-id="e8144-167">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="e8144-168">运算符 `~` 具有“包含”语义，并适用于字符串属性，如 `DisplayName`。</span><span class="sxs-lookup"><span data-stu-id="e8144-168">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="e8144-169">括号 `()` 用于组的子表达式。</span><span class="sxs-lookup"><span data-stu-id="e8144-169">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="e8144-170">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="e8144-170">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="e8144-171">为测试结果指定一个记录器。</span><span class="sxs-lookup"><span data-stu-id="e8144-171">Specify a logger for test results.</span></span>

* <span data-ttu-id="e8144-172">若要将测试结果发布到 Team Foundation Server，请使用 `TfsPublisher` 记录器提供程序：</span><span class="sxs-lookup"><span data-stu-id="e8144-172">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="e8144-173">若要将结果记录到 Visual Studio 测试结果文件 (TRX)，请使用 `trx` 记录器提供程序。</span><span class="sxs-lookup"><span data-stu-id="e8144-173">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="e8144-174">此开关使用给定的日志文件名在测试结果目录中创建一个文件。</span><span class="sxs-lookup"><span data-stu-id="e8144-174">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="e8144-175">如果未提供 `LogFileName`，将创建唯一的文件名以保留测试结果。</span><span class="sxs-lookup"><span data-stu-id="e8144-175">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="e8144-176">列出给定测试容器中所有已发现的测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-176">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="e8144-177">父进程的进程 ID 负责启动当前进程。</span><span class="sxs-lookup"><span data-stu-id="e8144-177">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="e8144-178">指定套接字连接和接收事件消息的端口。</span><span class="sxs-lookup"><span data-stu-id="e8144-178">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="e8144-179">为测试平台启用详细日志。</span><span class="sxs-lookup"><span data-stu-id="e8144-179">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="e8144-180">日志被写入到所提供的文件。</span><span class="sxs-lookup"><span data-stu-id="e8144-180">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="e8144-181">指定要传递到适配器的额外参数。</span><span class="sxs-lookup"><span data-stu-id="e8144-181">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="e8144-182">参数被指定为 `<n>=<v>` 格式的名称值对，其中 `<n>` 是参数名称，`<v>` 是参数值。</span><span class="sxs-lookup"><span data-stu-id="e8144-182">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="e8144-183">使用空格分隔多个参数。</span><span class="sxs-lookup"><span data-stu-id="e8144-183">Use a space to separate multiple arguments.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e8144-184">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="e8144-184">.NET Core 1.x</span></span>](#tab/netcore1x)

`--Settings|/Settings:<Settings File>`

<span data-ttu-id="e8144-185">运行测试时要使用的设置。</span><span class="sxs-lookup"><span data-stu-id="e8144-185">Settings to use when running tests.</span></span>

`--Tests|/Tests:<Test Names>`

<span data-ttu-id="e8144-186">运行具有与提供的值匹配的名称的测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-186">Run tests with names that match the provided values.</span></span> <span data-ttu-id="e8144-187">用逗号分隔多个值。</span><span class="sxs-lookup"><span data-stu-id="e8144-187">Separate multiple values with commas.</span></span>

`--TestAdapterPath|/TestAdapterPath`

<span data-ttu-id="e8144-188">在测试运行中使用来自给定路径（如果有）的自定义测试适配器。</span><span class="sxs-lookup"><span data-stu-id="e8144-188">Use custom test adapters from a given path (if any) in the test run.</span></span>

`--Platform|/Platform:<Platform type>`

<span data-ttu-id="e8144-189">用于执行测试的目标平台体系结构。</span><span class="sxs-lookup"><span data-stu-id="e8144-189">Target platform architecture used for test execution.</span></span> <span data-ttu-id="e8144-190">有效值为 `x86`、`x64` 和 `ARM`。</span><span class="sxs-lookup"><span data-stu-id="e8144-190">Valid values are `x86`, `x64`, and `ARM`.</span></span>

`--Framework|/Framework:<Framework Version>`

<span data-ttu-id="e8144-191">用于测试执行的目标 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="e8144-191">Target .NET Framework version used for test execution.</span></span> <span data-ttu-id="e8144-192">有效值的示例为 `.NETFramework,Version=v4.6` 或 `.NETCoreApp,Version=v1.0`。</span><span class="sxs-lookup"><span data-stu-id="e8144-192">Examples of valid values are `.NETFramework,Version=v4.6` or `.NETCoreApp,Version=v1.0`.</span></span> <span data-ttu-id="e8144-193">其他支持的值为 `Framework40`、`Framework45` 和 `FrameworkCore10`。</span><span class="sxs-lookup"><span data-stu-id="e8144-193">Other supported values are `Framework40`, `Framework45`, and `FrameworkCore10`.</span></span>

`--Parallel|/Parallel`

<span data-ttu-id="e8144-194">并行执行测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-194">Execute tests in parallel.</span></span> <span data-ttu-id="e8144-195">默认情况下，计算机上的所有可用内核都可供使用。</span><span class="sxs-lookup"><span data-stu-id="e8144-195">By default, all available cores on the machine are available for use.</span></span> <span data-ttu-id="e8144-196">通过在 runsettings 文件的 RunConfiguration 节点下设置 MaxCpuCount 属性来指定显式内核数。</span><span class="sxs-lookup"><span data-stu-id="e8144-196">Specify an explicit number of cores by setting the MaxCpuCount property under the RunConfiguration node in the runsettings file.</span></span>

`--TestCaseFilter|/TestCaseFilter:<Expression>`

<span data-ttu-id="e8144-197">运行与给定表达式匹配的测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-197">Run tests that match the given expression.</span></span> <span data-ttu-id="e8144-198">`<Expression>` 的格式为 `<property>Operator<value>[|&<Expression>]`，其中运算符是 `=`、`!=` 或 `~` 之一。</span><span class="sxs-lookup"><span data-stu-id="e8144-198">`<Expression>` is of the format `<property>Operator<value>[|&<Expression>]`, where Operator is one of `=`, `!=`, or `~`.</span></span> <span data-ttu-id="e8144-199">运算符 `~` 具有“包含”语义，并适用于字符串属性，如 `DisplayName`。</span><span class="sxs-lookup"><span data-stu-id="e8144-199">Operator `~` has 'contains' semantics and is applicable for string properties like `DisplayName`.</span></span> <span data-ttu-id="e8144-200">括号 `()` 用于组的子表达式。</span><span class="sxs-lookup"><span data-stu-id="e8144-200">Parenthesis `()` are used to group sub-expressions.</span></span>

`-?|--Help|/?|/Help`

<span data-ttu-id="e8144-201">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="e8144-201">Prints out a short help for the command.</span></span>

`--logger|/logger:<Logger Uri/FriendlyName>`

<span data-ttu-id="e8144-202">为测试结果指定一个记录器。</span><span class="sxs-lookup"><span data-stu-id="e8144-202">Specify a logger for test results.</span></span>

* <span data-ttu-id="e8144-203">若要将测试结果发布到 Team Foundation Server，请使用 `TfsPublisher` 记录器提供程序：</span><span class="sxs-lookup"><span data-stu-id="e8144-203">To publish test results to Team Foundation Server, use the `TfsPublisher` logger provider:</span></span>

  ```console
  /logger:TfsPublisher;
      Collection=<team project collection url>;
      BuildName=<build name>;
      TeamProject=<team project name>
      [;Platform=<Defaults to "Any CPU">]
      [;Flavor=<Defaults to "Debug">]
      [;RunTitle=<title>]
  ```

* <span data-ttu-id="e8144-204">若要将结果记录到 Visual Studio 测试结果文件 (TRX)，请使用 `trx` 记录器提供程序。</span><span class="sxs-lookup"><span data-stu-id="e8144-204">To log results to a Visual Studio Test Results File (TRX), use the `trx` logger provider.</span></span> <span data-ttu-id="e8144-205">此开关使用给定的日志文件名在测试结果目录中创建一个文件。</span><span class="sxs-lookup"><span data-stu-id="e8144-205">This switch creates a file in the test results directory with given log file name.</span></span> <span data-ttu-id="e8144-206">如果未提供 `LogFileName`，将创建唯一的文件名以保留测试结果。</span><span class="sxs-lookup"><span data-stu-id="e8144-206">If `LogFileName` isn't provided, a unique file name is created to hold the test results.</span></span>

  ```console
  /logger:trx [;LogFileName=<Defaults to unique file name>]
  ```

`-lt|--ListTests|/lt|/ListTests:<File Name>`

<span data-ttu-id="e8144-207">列出给定测试容器中所有已发现的测试。</span><span class="sxs-lookup"><span data-stu-id="e8144-207">Lists all discovered tests from the given test container.</span></span>

`--ParentProcessId|/ParentProcessId:<ParentProcessId>`

<span data-ttu-id="e8144-208">父进程的进程 ID 负责启动当前进程。</span><span class="sxs-lookup"><span data-stu-id="e8144-208">Process ID of the parent process responsible for launching the current process.</span></span>

`--Port|/Port:<Port>`

<span data-ttu-id="e8144-209">指定套接字连接和接收事件消息的端口。</span><span class="sxs-lookup"><span data-stu-id="e8144-209">Specifies the port for the socket connection and receiving the event messages.</span></span>

`--Diag|/Diag:<Path to log file>`

<span data-ttu-id="e8144-210">为测试平台启用详细日志。</span><span class="sxs-lookup"><span data-stu-id="e8144-210">Enables verbose logs for the test platform.</span></span> <span data-ttu-id="e8144-211">日志被写入到所提供的文件。</span><span class="sxs-lookup"><span data-stu-id="e8144-211">Logs are written to the provided file.</span></span>

`args`

<span data-ttu-id="e8144-212">指定要传递到适配器的额外参数。</span><span class="sxs-lookup"><span data-stu-id="e8144-212">Specifies extra arguments to pass to the adapter.</span></span> <span data-ttu-id="e8144-213">参数被指定为 `<n>=<v>` 格式的名称值对，其中 `<n>` 是参数名称，`<v>` 是参数值。</span><span class="sxs-lookup"><span data-stu-id="e8144-213">Arguments are specified as name-value pairs of the form `<n>=<v>`, where `<n>` is the argument name and `<v>` is the argument value.</span></span> <span data-ttu-id="e8144-214">使用空格分隔多个参数。</span><span class="sxs-lookup"><span data-stu-id="e8144-214">Use a space to separate multiple arguments.</span></span>

---

## <a name="examples"></a><span data-ttu-id="e8144-215">示例</span><span class="sxs-lookup"><span data-stu-id="e8144-215">Examples</span></span>

<span data-ttu-id="e8144-216">在 `mytestproject.dll` 中运行测试：</span><span class="sxs-lookup"><span data-stu-id="e8144-216">Run tests in `mytestproject.dll`:</span></span>

`dotnet vstest mytestproject.dll`

<span data-ttu-id="e8144-217">在 `mytestproject.dll` 中运行测试，并使用自定义名称导出到自定义文件夹：</span><span class="sxs-lookup"><span data-stu-id="e8144-217">Run tests in `mytestproject.dll`, exporting to custom folder with custom name:</span></span>

`dotnet vstest mytestproject.dll --logger:"trx;LogFileName=custom_file_name.trx" --ResultsDirectory:custom/file/path`

<span data-ttu-id="e8144-218">在 `mytestproject.dll` 和 `myothertestproject.exe` 中运行测试：</span><span class="sxs-lookup"><span data-stu-id="e8144-218">Run tests in `mytestproject.dll` and `myothertestproject.exe`:</span></span>

`dotnet vstest mytestproject.dll myothertestproject.exe`

<span data-ttu-id="e8144-219">运行 `TestMethod1` 测试：</span><span class="sxs-lookup"><span data-stu-id="e8144-219">Run `TestMethod1` tests:</span></span>

`dotnet vstest /Tests:TestMethod1`

<span data-ttu-id="e8144-220">运行 `TestMethod1` 和 `TestMethod2` 测试：</span><span class="sxs-lookup"><span data-stu-id="e8144-220">Run `TestMethod1` and `TestMethod2` tests:</span></span>

`dotnet vstest /Tests:TestMethod1,TestMethod2`
