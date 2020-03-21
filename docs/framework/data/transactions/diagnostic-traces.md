---
title: 诊断跟踪
ms.date: 03/30/2017
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
ms.openlocfilehash: 76712710bf42f498ba859c7b1cd18a261387078c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174415"
---
# <a name="diagnostic-traces"></a><span data-ttu-id="9ee80-102">诊断跟踪</span><span class="sxs-lookup"><span data-stu-id="9ee80-102">Diagnostic Traces</span></span>
<span data-ttu-id="9ee80-103">跟踪是指发布在执行应用程序期间生成的特定消息。</span><span class="sxs-lookup"><span data-stu-id="9ee80-103">Traces are the publishing of specific messages that are generated during application execution.</span></span> <span data-ttu-id="9ee80-104">使用跟踪时，必须具有收集和记录所发送消息的机制。</span><span class="sxs-lookup"><span data-stu-id="9ee80-104">When using tracing, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="9ee80-105">跟踪消息由侦听器来接收。</span><span class="sxs-lookup"><span data-stu-id="9ee80-105">Trace messages are received by listeners.</span></span> <span data-ttu-id="9ee80-106">侦听器的用途是收集、存储和路由跟踪消息。</span><span class="sxs-lookup"><span data-stu-id="9ee80-106">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="9ee80-107">侦听器会将跟踪输出定向到适当的目标，如日志、窗口或文本文件。</span><span class="sxs-lookup"><span data-stu-id="9ee80-107">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="9ee80-108"><xref:System.Diagnostics.DefaultTraceListener> 就是一个这样的侦听器，在启用跟踪后将自动创建并初始化它。</span><span class="sxs-lookup"><span data-stu-id="9ee80-108">One such listener, the <xref:System.Diagnostics.DefaultTraceListener>, is automatically created and initialized when tracing is enabled.</span></span> <span data-ttu-id="9ee80-109">如果要将跟踪输出定向到任何其他源，则必须创建并初始化其他跟踪侦听器。</span><span class="sxs-lookup"><span data-stu-id="9ee80-109">If you want trace output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span> <span data-ttu-id="9ee80-110">所创建的侦听器应反映您的具体需要。</span><span class="sxs-lookup"><span data-stu-id="9ee80-110">The listeners you create should reflect your individual needs.</span></span> <span data-ttu-id="9ee80-111">例如，您可能需要所有跟踪输出的文本记录。</span><span class="sxs-lookup"><span data-stu-id="9ee80-111">For example, you might want a text record of all trace output.</span></span> <span data-ttu-id="9ee80-112">在这种情况下，可以创建一个侦听器，使其在启用时将所有输出写入一个新的文本文件。</span><span class="sxs-lookup"><span data-stu-id="9ee80-112">In this case, you would create a listener that wrote all output to a new text file when enabled.</span></span> <span data-ttu-id="9ee80-113">另一方面，您可能只需要在执行应用程序的过程中查看输出。</span><span class="sxs-lookup"><span data-stu-id="9ee80-113">On the other hand, you might only want to view output during application execution.</span></span> <span data-ttu-id="9ee80-114">在这种情况下，可以创建一个侦听器，使其将所有输出定向到一个控制台窗口。</span><span class="sxs-lookup"><span data-stu-id="9ee80-114">In that case, you might create a listener that directed all output to a console window.</span></span> <span data-ttu-id="9ee80-115"><xref:System.Diagnostics.EventLogTraceListener> 可将跟踪输出定向到事件日志，而 <xref:System.Diagnostics.TextWriterTraceListener> 可将跟踪输出写入流中。</span><span class="sxs-lookup"><span data-stu-id="9ee80-115">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log, and the <xref:System.Diagnostics.TextWriterTraceListener> can write trace output to a stream.</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="9ee80-116">启用跟踪</span><span class="sxs-lookup"><span data-stu-id="9ee80-116">Enabling Tracing</span></span>  
 <span data-ttu-id="9ee80-117">若要在事务处理期间启用跟踪，应编辑应用程序的配置文件。</span><span class="sxs-lookup"><span data-stu-id="9ee80-117">To enable traces during transaction processing, you should edit your application’s configuration file.</span></span> <span data-ttu-id="9ee80-118">下面是一个示例。</span><span class="sxs-lookup"><span data-stu-id="9ee80-118">The following is an example.</span></span>  
  
```xml  
<configuration>  
<system.diagnostics>  
     <sources>  
          <source name="System.Transactions" switchValue="Warning">  
               <listeners>  
                    <add name="tx"
                     type="System.Diagnostics.XmlWriterTraceListener"
                     initializeData= "tx.log" />  
               </listeners>  
          </source>  
     </sources>  
</system.diagnostics>  
</configuration>  
```  
  
 <span data-ttu-id="9ee80-119"><xref:System.Transactions> 跟踪将写入到一个名为“System.Transactions”的源。</span><span class="sxs-lookup"><span data-stu-id="9ee80-119"><xref:System.Transactions> traces are written to the source named "System.Transactions".</span></span> <span data-ttu-id="9ee80-120">可以使用 `add` 指定要使用的跟踪侦听器的名称和类型。</span><span class="sxs-lookup"><span data-stu-id="9ee80-120">You can use `add` to specify the name and type of the trace listener you want to use.</span></span> <span data-ttu-id="9ee80-121">在示例配置中，将侦听器命名为“tx”并添加了标准 .NET Framework 跟踪侦听器 (<xref:System.Diagnostics.XmlWriterTraceListener>) 作为要使用的类型。</span><span class="sxs-lookup"><span data-stu-id="9ee80-121">In our example configuration, we named the Listener "tx" and added the standard .NET Framework trace listener (<xref:System.Diagnostics.XmlWriterTraceListener>) as the type we want to use.</span></span> <span data-ttu-id="9ee80-122">使用 `initializeData` 设置该侦听器的日志文件的名称。</span><span class="sxs-lookup"><span data-stu-id="9ee80-122">Use `initializeData` to set the name of the log file for that listener.</span></span> <span data-ttu-id="9ee80-123">此外，还可以用一个简单文件名来替换完全限定路径。</span><span class="sxs-lookup"><span data-stu-id="9ee80-123">In addition, you can substitute a fully qualified path for a simple file name.</span></span>  
  
 <span data-ttu-id="9ee80-124">每个跟踪消息类型都分配有一个指示其重要程度的级别。</span><span class="sxs-lookup"><span data-stu-id="9ee80-124">Each trace message type is assigned a level to indicate its degree of importance.</span></span> <span data-ttu-id="9ee80-125">如果应用程序域的跟踪级别等于或小于事件类型的级别，就会生成该消息。</span><span class="sxs-lookup"><span data-stu-id="9ee80-125">If the app-domain’s trace level is equal or lower than the level of an event type, then that message is generated.</span></span> <span data-ttu-id="9ee80-126">跟踪级别由配置文件中的 `switchValue` 设置控制。</span><span class="sxs-lookup"><span data-stu-id="9ee80-126">The tracing level is controlled by the `switchValue` setting in the configuration file.</span></span> <span data-ttu-id="9ee80-127">下表定义了与诊断跟踪消息关联的级别。</span><span class="sxs-lookup"><span data-stu-id="9ee80-127">The levels that are associated with diagnostic trace messages are defined in the following table.</span></span>  
  
|<span data-ttu-id="9ee80-128">跟踪级别</span><span class="sxs-lookup"><span data-stu-id="9ee80-128">Trace Level</span></span>|<span data-ttu-id="9ee80-129">说明</span><span class="sxs-lookup"><span data-stu-id="9ee80-129">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="9ee80-130">严重</span><span class="sxs-lookup"><span data-stu-id="9ee80-130">Critical</span></span>|<span data-ttu-id="9ee80-131">表示发生了类似于下面的严重故障：</span><span class="sxs-lookup"><span data-stu-id="9ee80-131">Serious failures, such as the following, have occurred:</span></span><br /><br /> <span data-ttu-id="9ee80-132">- 可能导致用户功能立即丢失的错误。</span><span class="sxs-lookup"><span data-stu-id="9ee80-132">-   An error that can cause an immediate loss in user functionality.</span></span><br /><span data-ttu-id="9ee80-133">- 需要管理员采取措施以避免功能丢失的事件。</span><span class="sxs-lookup"><span data-stu-id="9ee80-133">-   An event that requires an administrator to take action to avoid loss of functionality.</span></span><br /><span data-ttu-id="9ee80-134">- 代码挂起。</span><span class="sxs-lookup"><span data-stu-id="9ee80-134">-   Code hangs.</span></span><br /><span data-ttu-id="9ee80-135">- 此跟踪级别还可以为解释其他关键跟踪提供足够的上下文。</span><span class="sxs-lookup"><span data-stu-id="9ee80-135">-   This tracing level can also provide sufficient context for interpreting other critical traces.</span></span> <span data-ttu-id="9ee80-136">这可以帮助确定导致严重故障的操作序列。</span><span class="sxs-lookup"><span data-stu-id="9ee80-136">This can help to identify the sequence of operations leading to a serious failure.</span></span>|  
|<span data-ttu-id="9ee80-137">错误</span><span class="sxs-lookup"><span data-stu-id="9ee80-137">Error</span></span>|<span data-ttu-id="9ee80-138">发生了可能会导致用户功能丧失的错误（如无效的配置或网络行为）。</span><span class="sxs-lookup"><span data-stu-id="9ee80-138">An error (for example, invalid configuration or network behavior) has occurred that can result in a loss of user functionality.</span></span>|  
|<span data-ttu-id="9ee80-139">警告</span><span class="sxs-lookup"><span data-stu-id="9ee80-139">Warning</span></span>|<span data-ttu-id="9ee80-140">存在一种状况，它可能会在以后导致错误或严重故障（例如，分配失败或达到限制）。</span><span class="sxs-lookup"><span data-stu-id="9ee80-140">A condition exists that can subsequently result in an error or critical failure (for example, allocation failing or approaching a limit).</span></span> <span data-ttu-id="9ee80-141">对用户代码中的错误（例如，事务中止、超时、身份验证失败）的正常处理也可能会生成警告。</span><span class="sxs-lookup"><span data-stu-id="9ee80-141">Normal processing of errors from user code (for example, transaction aborted, timeouts, authentication failed) can also generate a warning.</span></span>|  
|<span data-ttu-id="9ee80-142">信息</span><span class="sxs-lookup"><span data-stu-id="9ee80-142">Information</span></span>|<span data-ttu-id="9ee80-143">生成对监视和诊断系统状态、测量性能或执行分析十分有用的消息。</span><span class="sxs-lookup"><span data-stu-id="9ee80-143">Messages helpful for monitoring and diagnosing system status, measuring performance, or profiling are generated.</span></span> <span data-ttu-id="9ee80-144">这些消息可包括事务和登记生存期事件，如创建或提交事务、跨重要边界或分配重要资源等。</span><span class="sxs-lookup"><span data-stu-id="9ee80-144">These can include transaction and enlistment lifetime events, such as a transaction being created or committed, the crossing of a significant boundary, or the allocation of significant resources.</span></span> <span data-ttu-id="9ee80-145">开发人员可利用此类信息规划容量和管理性能。</span><span class="sxs-lookup"><span data-stu-id="9ee80-145">A developer can then utilize such information for capacity planning and performance management.</span></span>|  
  
## <a name="trace-codes"></a><span data-ttu-id="9ee80-146">跟踪代码</span><span class="sxs-lookup"><span data-stu-id="9ee80-146">Trace Codes</span></span>  
 <span data-ttu-id="9ee80-147">下表列出了由 <xref:System.Transactions> 基础结构生成的跟踪代码。</span><span class="sxs-lookup"><span data-stu-id="9ee80-147">The following table lists the trace codes that are generated by the <xref:System.Transactions> infrastructure.</span></span> <span data-ttu-id="9ee80-148">表中包括跟踪代码标识符、跟踪的枚<xref:System.Diagnostics.EventTypeFilter.EventType%2A>举级别以及跟踪的**TraceRecord**中包含的额外数据。</span><span class="sxs-lookup"><span data-stu-id="9ee80-148">Included in the table are the trace code identifier, the <xref:System.Diagnostics.EventTypeFilter.EventType%2A> enumeration level for the trace, and the extra data contained in the **TraceRecord** for the trace.</span></span> <span data-ttu-id="9ee80-149">此外，跟踪的相应跟踪级别也存储在**跟踪记录中**。</span><span class="sxs-lookup"><span data-stu-id="9ee80-149">In addition, the corresponding trace level of the trace is also stored in the **TraceRecord**.</span></span>  
  
|<span data-ttu-id="9ee80-150">TraceCode</span><span class="sxs-lookup"><span data-stu-id="9ee80-150">TraceCode</span></span>|<span data-ttu-id="9ee80-151">EventType</span><span class="sxs-lookup"><span data-stu-id="9ee80-151">EventType</span></span>|<span data-ttu-id="9ee80-152">TraceRecord 中的额外数据</span><span class="sxs-lookup"><span data-stu-id="9ee80-152">Extra data in TraceRecord</span></span>|  
|---------------|---------------|-------------------------------|  
|<span data-ttu-id="9ee80-153">TransactionCreated</span><span class="sxs-lookup"><span data-stu-id="9ee80-153">TransactionCreated</span></span>|<span data-ttu-id="9ee80-154">信息</span><span class="sxs-lookup"><span data-stu-id="9ee80-154">Info</span></span>|<span data-ttu-id="9ee80-155">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="9ee80-155">TransactionTraceId</span></span>|  
|<span data-ttu-id="9ee80-156">TransactionPromoted</span><span class="sxs-lookup"><span data-stu-id="9ee80-156">TransactionPromoted</span></span>|<span data-ttu-id="9ee80-157">信息</span><span class="sxs-lookup"><span data-stu-id="9ee80-157">Info</span></span>|<span data-ttu-id="9ee80-158">Local TransactionTraceId、Distributed TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="9ee80-158">Local TransactionTraceId, Distributed TransactionTraceId</span></span>|  
|<span data-ttu-id="9ee80-159">EnlistmentCreated</span><span class="sxs-lookup"><span data-stu-id="9ee80-159">EnlistmentCreated</span></span>|<span data-ttu-id="9ee80-160">信息</span><span class="sxs-lookup"><span data-stu-id="9ee80-160">Info</span></span>|<span data-ttu-id="9ee80-161">TransactionTraceId、EnlistmentTraceId、EnlistmentType（持久/可变）、EnlistmentOptions</span><span class="sxs-lookup"><span data-stu-id="9ee80-161">TransactionTraceId, EnlistmentTraceId, EnlistmentType (durable/volatile), EnlistmentOptions</span></span>|  
|<span data-ttu-id="9ee80-162">EnlistmentCallbackNegative</span><span class="sxs-lookup"><span data-stu-id="9ee80-162">EnlistmentCallbackNegative</span></span>|<span data-ttu-id="9ee80-163">警告</span><span class="sxs-lookup"><span data-stu-id="9ee80-163">Warning</span></span>|<span data-ttu-id="9ee80-164">TransactionTraceId、EnlistmentTraceId</span><span class="sxs-lookup"><span data-stu-id="9ee80-164">TransactionTraceId, EnlistmentTraceId,</span></span><br /><br /> <span data-ttu-id="9ee80-165">Callback (forcerollback/aborted/indoubt)</span><span class="sxs-lookup"><span data-stu-id="9ee80-165">Callback (forcerollback/aborted/indoubt)</span></span>|  
|<span data-ttu-id="9ee80-166">TransactionRollbackCalled</span><span class="sxs-lookup"><span data-stu-id="9ee80-166">TransactionRollbackCalled</span></span>|<span data-ttu-id="9ee80-167">警告</span><span class="sxs-lookup"><span data-stu-id="9ee80-167">Warning</span></span>|<span data-ttu-id="9ee80-168">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="9ee80-168">TransactionTraceId</span></span>|  
|<span data-ttu-id="9ee80-169">TransactionAborted</span><span class="sxs-lookup"><span data-stu-id="9ee80-169">TransactionAborted</span></span>|<span data-ttu-id="9ee80-170">警告</span><span class="sxs-lookup"><span data-stu-id="9ee80-170">Warning</span></span>|<span data-ttu-id="9ee80-171">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="9ee80-171">TransactionTraceId</span></span>|  
|<span data-ttu-id="9ee80-172">TransactionInDoubt</span><span class="sxs-lookup"><span data-stu-id="9ee80-172">TransactionInDoubt</span></span>|<span data-ttu-id="9ee80-173">警告</span><span class="sxs-lookup"><span data-stu-id="9ee80-173">Warning</span></span>|<span data-ttu-id="9ee80-174">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="9ee80-174">TransactionTraceId</span></span>|  
|<span data-ttu-id="9ee80-175">TransactionScopeCreated</span><span class="sxs-lookup"><span data-stu-id="9ee80-175">TransactionScopeCreated</span></span>|<span data-ttu-id="9ee80-176">信息</span><span class="sxs-lookup"><span data-stu-id="9ee80-176">Info</span></span>|<span data-ttu-id="9ee80-177">TransactionScopeResult，可为以下各项：</span><span class="sxs-lookup"><span data-stu-id="9ee80-177">TransactionScopeResult, which can be the following:</span></span><br /><br /> <span data-ttu-id="9ee80-178">- 新交易</span><span class="sxs-lookup"><span data-stu-id="9ee80-178">-   New transaction.</span></span><br /><span data-ttu-id="9ee80-179">- 交易通过。</span><span class="sxs-lookup"><span data-stu-id="9ee80-179">-   Transaction passed.</span></span><br /><span data-ttu-id="9ee80-180">- 已传递从属事务。</span><span class="sxs-lookup"><span data-stu-id="9ee80-180">-   Dependent transaction passed.</span></span><br /><span data-ttu-id="9ee80-181">- 使用当前事务。</span><span class="sxs-lookup"><span data-stu-id="9ee80-181">-   Using current transaction.</span></span><br /><span data-ttu-id="9ee80-182">-没有交易</span><span class="sxs-lookup"><span data-stu-id="9ee80-182">-   No transaction.</span></span><br /><br /> <span data-ttu-id="9ee80-183">新的当前 TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="9ee80-183">new current TransactionTraceId</span></span>|  
|<span data-ttu-id="9ee80-184">TransactionScopeDisposed</span><span class="sxs-lookup"><span data-stu-id="9ee80-184">TransactionScopeDisposed</span></span>|<span data-ttu-id="9ee80-185">信息</span><span class="sxs-lookup"><span data-stu-id="9ee80-185">Info</span></span>|<span data-ttu-id="9ee80-186">作用域的"预期"当前事务的事务跟踪Id。</span><span class="sxs-lookup"><span data-stu-id="9ee80-186">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="9ee80-187">TransactionScopeIncomplete</span><span class="sxs-lookup"><span data-stu-id="9ee80-187">TransactionScopeIncomplete</span></span>|<span data-ttu-id="9ee80-188">警告</span><span class="sxs-lookup"><span data-stu-id="9ee80-188">Warning</span></span>|<span data-ttu-id="9ee80-189">作用域的"预期"当前事务的事务跟踪Id。</span><span class="sxs-lookup"><span data-stu-id="9ee80-189">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="9ee80-190">TransactionScopeNestedIncorrectly</span><span class="sxs-lookup"><span data-stu-id="9ee80-190">TransactionScopeNestedIncorrectly</span></span>|<span data-ttu-id="9ee80-191">警告</span><span class="sxs-lookup"><span data-stu-id="9ee80-191">Warning</span></span>|<span data-ttu-id="9ee80-192">作用域的"预期"当前事务的事务跟踪Id。</span><span class="sxs-lookup"><span data-stu-id="9ee80-192">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="9ee80-193">TransactionScopeCurrentTransactionChanged</span><span class="sxs-lookup"><span data-stu-id="9ee80-193">TransactionScopeCurrentTransactionChanged</span></span>|<span data-ttu-id="9ee80-194">警告</span><span class="sxs-lookup"><span data-stu-id="9ee80-194">Warning</span></span>|<span data-ttu-id="9ee80-195">旧的当前 TransactionTraceId、其他 TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="9ee80-195">Old current TransactionTraceId, other TransactionTraceId</span></span>|  
|<span data-ttu-id="9ee80-196">TransactionScopeTimeout</span><span class="sxs-lookup"><span data-stu-id="9ee80-196">TransactionScopeTimeout</span></span>|<span data-ttu-id="9ee80-197">警告</span><span class="sxs-lookup"><span data-stu-id="9ee80-197">Warning</span></span>|<span data-ttu-id="9ee80-198">作用域的"预期"当前事务的事务跟踪Id。</span><span class="sxs-lookup"><span data-stu-id="9ee80-198">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="9ee80-199">DependentCloneCreated</span><span class="sxs-lookup"><span data-stu-id="9ee80-199">DependentCloneCreated</span></span>|<span data-ttu-id="9ee80-200">信息</span><span class="sxs-lookup"><span data-stu-id="9ee80-200">Info</span></span>|<span data-ttu-id="9ee80-201">TransactionTraceId、已创建的依赖事务的类型 (RollbackIfNotComplete/BlockCommitUntilComplete)</span><span class="sxs-lookup"><span data-stu-id="9ee80-201">TransactionTraceId, type of dependent transaction created (RollbackIfNotComplete/BlockCommitUntilComplete)</span></span>|  
|<span data-ttu-id="9ee80-202">DependentCloneComplete</span><span class="sxs-lookup"><span data-stu-id="9ee80-202">DependentCloneComplete</span></span>|<span data-ttu-id="9ee80-203">信息</span><span class="sxs-lookup"><span data-stu-id="9ee80-203">Info</span></span>|<span data-ttu-id="9ee80-204">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="9ee80-204">TransactionTraceId</span></span>|  
|<span data-ttu-id="9ee80-205">RecoveryComplete</span><span class="sxs-lookup"><span data-stu-id="9ee80-205">RecoveryComplete</span></span>|<span data-ttu-id="9ee80-206">信息</span><span class="sxs-lookup"><span data-stu-id="9ee80-206">Info</span></span>|<span data-ttu-id="9ee80-207">资源管理器 GUID（来自基类型）</span><span class="sxs-lookup"><span data-stu-id="9ee80-207">Resource Manager GUID (from base)</span></span>|  
|<span data-ttu-id="9ee80-208">Reenlist</span><span class="sxs-lookup"><span data-stu-id="9ee80-208">Reenlist</span></span>|<span data-ttu-id="9ee80-209">信息</span><span class="sxs-lookup"><span data-stu-id="9ee80-209">Info</span></span>|<span data-ttu-id="9ee80-210">资源管理器 GUID（来自基类型）</span><span class="sxs-lookup"><span data-stu-id="9ee80-210">Resource Manager GUID (from base)</span></span>|  
|<span data-ttu-id="9ee80-211">TransactionSerialized</span><span class="sxs-lookup"><span data-stu-id="9ee80-211">TransactionSerialized</span></span>|<span data-ttu-id="9ee80-212">信息</span><span class="sxs-lookup"><span data-stu-id="9ee80-212">Info</span></span>|<span data-ttu-id="9ee80-213">TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="9ee80-213">TransactionTraceId.</span></span>|  
|<span data-ttu-id="9ee80-214">TransactionException</span><span class="sxs-lookup"><span data-stu-id="9ee80-214">TransactionException</span></span>|<span data-ttu-id="9ee80-215">错误</span><span class="sxs-lookup"><span data-stu-id="9ee80-215">Error</span></span>|<span data-ttu-id="9ee80-216">异常消息</span><span class="sxs-lookup"><span data-stu-id="9ee80-216">Exception message</span></span>|  
|<span data-ttu-id="9ee80-217">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="9ee80-217">InvalidOperationException</span></span>|<span data-ttu-id="9ee80-218">错误</span><span class="sxs-lookup"><span data-stu-id="9ee80-218">Error</span></span>|<span data-ttu-id="9ee80-219">异常消息</span><span class="sxs-lookup"><span data-stu-id="9ee80-219">Exception message</span></span>|  
|<span data-ttu-id="9ee80-220">InternalError</span><span class="sxs-lookup"><span data-stu-id="9ee80-220">InternalError</span></span>|<span data-ttu-id="9ee80-221">严重</span><span class="sxs-lookup"><span data-stu-id="9ee80-221">Critical</span></span>|<span data-ttu-id="9ee80-222">异常消息</span><span class="sxs-lookup"><span data-stu-id="9ee80-222">Exception message</span></span>|  
|<span data-ttu-id="9ee80-223">TransferEvent</span><span class="sxs-lookup"><span data-stu-id="9ee80-223">TransferEvent</span></span>||<span data-ttu-id="9ee80-224">当事务反序列化或者从 <xref:System.Transactions> 事务提升为分布式事务时，将写入 ExecutionContext 中的当前 ActivityID 以及分布式事务 ID。</span><span class="sxs-lookup"><span data-stu-id="9ee80-224">When a transaction is deserialized, or promoted from a <xref:System.Transactions> transaction to a distributed one, the current ActivityID from the ExecutionContext and the distributed transaction ID are written.</span></span><br /><br /> <span data-ttu-id="9ee80-225">当 DTC 回调到托管代码中时，分布式事务 ID 会在回调期间设置为 ExecutionContext 中的 ActivityID。</span><span class="sxs-lookup"><span data-stu-id="9ee80-225">When the DTC calls back into managed code, the distributed transaction ID is set as the ActivityID in the ExecutionContext for the duration of the callback.</span></span>|  
|<span data-ttu-id="9ee80-226">ConfiguredDefaultTimeoutAdjusted</span><span class="sxs-lookup"><span data-stu-id="9ee80-226">ConfiguredDefaultTimeoutAdjusted</span></span>|<span data-ttu-id="9ee80-227">警告</span><span class="sxs-lookup"><span data-stu-id="9ee80-227">Warning</span></span>|<span data-ttu-id="9ee80-228">没有额外数据</span><span class="sxs-lookup"><span data-stu-id="9ee80-228">No extra data</span></span>|  
|<span data-ttu-id="9ee80-229">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="9ee80-229">TransactionTimeout</span></span>|<span data-ttu-id="9ee80-230">警告</span><span class="sxs-lookup"><span data-stu-id="9ee80-230">Warning</span></span>|<span data-ttu-id="9ee80-231">正在超时的事务的 TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="9ee80-231">The TransactionTraceId of the transaction being timed out.</span></span>|  
  
 <span data-ttu-id="9ee80-232">上述每个额外数据项的 XML 架构采用以下格式。</span><span class="sxs-lookup"><span data-stu-id="9ee80-232">The XML schema for each of the preceding extra data items has the following format.</span></span>  
  
### <a name="transactiontraceidentifier"></a><span data-ttu-id="9ee80-233">TransactionTraceIdentifier</span><span class="sxs-lookup"><span data-stu-id="9ee80-233">TransactionTraceIdentifier</span></span>  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `< CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `</TransactionTraceIdentifier>`  
  
### <a name="enlistmenttraceidentifier"></a><span data-ttu-id="9ee80-234">EnlistmentTraceIdentifier</span><span class="sxs-lookup"><span data-stu-id="9ee80-234">EnlistmentTraceIdentifier</span></span>  
 `<EnlistmentTraceIdentifier>`  
  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `<CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<EnlistmentIdentifier>`  
  
 `the enlistment id number`  
  
 `</EnlistmentIdentifier>`  
  
 `</EnlistmentTraceIdentifier>`  
  
### <a name="resource-manager-identifier"></a><span data-ttu-id="9ee80-235">资源管理器标识符</span><span class="sxs-lookup"><span data-stu-id="9ee80-235">Resource Manager Identifier</span></span>  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
## <a name="security-issues-for-tracing"></a><span data-ttu-id="9ee80-236">跟踪的安全问题</span><span class="sxs-lookup"><span data-stu-id="9ee80-236">Security Issues For Tracing</span></span>  
 <span data-ttu-id="9ee80-237">当您以管理员身份启用跟踪时，可能会向默认情况下可公开查看的跟踪日志写入敏感信息。</span><span class="sxs-lookup"><span data-stu-id="9ee80-237">When you as an administrator turn on tracing, sensitive information might be written to a trace log that is publicly viewable by default.</span></span> <span data-ttu-id="9ee80-238">若要消除任何可能的安全威胁，应考虑将该跟踪日志存储在一个由共享和文件系统访问权限控制的安全位置。</span><span class="sxs-lookup"><span data-stu-id="9ee80-238">To mitigate any possible security threat, you should consider storing the trace log in a secure location controlled by share and file system access permissions.</span></span>
