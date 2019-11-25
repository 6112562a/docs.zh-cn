---
title: 排队消息处理疑难解答
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: dcff128a7718245fa765c57d3af80665699f4891
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976041"
---
# <a name="troubleshooting-queued-messaging"></a><span data-ttu-id="2a8f3-102">排队消息处理疑难解答</span><span class="sxs-lookup"><span data-stu-id="2a8f3-102">Troubleshooting Queued Messaging</span></span>

<span data-ttu-id="2a8f3-103">本部分包含有关在 Windows Communication Foundation （WCF）中使用队列的常见问题和故障排除帮助。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-103">This section contains common questions and troubleshooting help for using queues in Windows Communication Foundation (WCF).</span></span>

## <a name="common-questions"></a><span data-ttu-id="2a8f3-104">常见问题</span><span class="sxs-lookup"><span data-stu-id="2a8f3-104">Common Questions</span></span>

<span data-ttu-id="2a8f3-105">**问：** 我使用了 WCF Beta 1 并安装了 MSMQ 修补程序。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-105">**Q:** I used WCF Beta 1 and I installed the MSMQ hotfix.</span></span> <span data-ttu-id="2a8f3-106">现在，是否需要移除此修补程序？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-106">Do I need to remove the hotfix?</span></span>

<span data-ttu-id="2a8f3-107">**答：** 可以。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-107">**A:** Yes.</span></span> <span data-ttu-id="2a8f3-108">此修补程序不再受支持。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-108">This hotfix is no longer supported.</span></span> <span data-ttu-id="2a8f3-109">WCF 现在可以在没有修补程序要求的情况下运行 MSMQ。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-109">WCF now works on MSMQ without a hotfix requirement.</span></span>

<span data-ttu-id="2a8f3-110">**问：** MSMQ： <xref:System.ServiceModel.NetMsmqBinding> 和 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>有两个绑定。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-110">**Q:** There are two bindings for MSMQ: <xref:System.ServiceModel.NetMsmqBinding> and <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span> <span data-ttu-id="2a8f3-111">我应该使用哪一种绑定以及在什么情况下使用？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-111">What should I use and when?</span></span>

<span data-ttu-id="2a8f3-112">**答：** 如果要使用 MSMQ 作为两个 WCF 应用程序之间排队通信的传输，请使用 <xref:System.ServiceModel.NetMsmqBinding>。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-112">**A:** Use the <xref:System.ServiceModel.NetMsmqBinding> when you want to use MSMQ as a transport for queued communication between two WCF applications.</span></span> <span data-ttu-id="2a8f3-113">如果要使用现有的 MSMQ 应用程序与新的 WCF 应用程序通信，请使用 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-113">Use the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> when you want to use existing MSMQ applications to communicate with new WCF applications.</span></span>

<span data-ttu-id="2a8f3-114">**问：** 是否必须升级 MSMQ 才能使用 <xref:System.ServiceModel.NetMsmqBinding> 和 `MsmqIntegration` 绑定？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-114">**Q:** Do I have to upgrade MSMQ to use the <xref:System.ServiceModel.NetMsmqBinding> and `MsmqIntegration` bindings?</span></span>

<span data-ttu-id="2a8f3-115">**答：** 否。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-115">**A:** No.</span></span> <span data-ttu-id="2a8f3-116">在 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 和 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 中，这两种绑定都可以与 MSMQ 3.0 一起使用。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-116">Both bindings work with MSMQ 3.0 on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span> <span data-ttu-id="2a8f3-117">在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 中，只有升级到 MSMQ 4.0，绑定的某些功能才可用。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-117">Certain features of the bindings become available when you upgrade to MSMQ 4.0 in [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span>

<span data-ttu-id="2a8f3-118">**问：** <xref:System.ServiceModel.NetMsmqBinding> 和 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 绑定的哪些功能在 MSMQ 4.0 中可用，但在 MSMQ 3.0 中不可用？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-118">**Q:** What features of the <xref:System.ServiceModel.NetMsmqBinding> and <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> bindings are available in MSMQ 4.0 but not in MSMQ 3.0?</span></span>

<span data-ttu-id="2a8f3-119">**答：** 以下功能在 MSMQ 4.0 中可用，但在 MSMQ 3.0 中不可用：</span><span class="sxs-lookup"><span data-stu-id="2a8f3-119">**A:** The following features are available in MSMQ 4.0 but not in MSMQ 3.0:</span></span>

- <span data-ttu-id="2a8f3-120">只有 MSMQ 4.0 才支持自定义死信队列。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-120">Custom dead-letter queue is supported only on MSMQ 4.0.</span></span>

- <span data-ttu-id="2a8f3-121">MSMQ 3.0 和 MSMQ 4.0 处理病毒消息的方式不同。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-121">MSMQ 3.0 and 4.0 handle poison messages differently.</span></span>

- <span data-ttu-id="2a8f3-122">只有 MSMQ 4.0 才支持远程事务处理读取。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-122">Only MSMQ 4.0 supports remote transacted read.</span></span>

<span data-ttu-id="2a8f3-123">有关详细信息，请参阅[Windows Vista、Windows Server 2003 和 WINDOWS XP 中的队列功能](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)之间的差异。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-123">For more information, see [Differences in Queuing Features in Windows Vista, Windows Server 2003, and Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).</span></span>

<span data-ttu-id="2a8f3-124">**问：** 是否可以在一侧排队通信和 MSMQ 4.0 一端使用 MSMQ 3.0？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-124">**Q:** Can I use MSMQ 3.0 on one side of a queued communication and MSMQ 4.0 on the other side?</span></span>

<span data-ttu-id="2a8f3-125">**答：** 可以。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-125">**A:** Yes.</span></span>

<span data-ttu-id="2a8f3-126">**问：** 我想要将现有的 MSMQ 应用程序与新的 WCF 客户端或服务器集成。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-126">**Q:** I want to integrate existing MSMQ applications with new WCF clients or servers.</span></span> <span data-ttu-id="2a8f3-127">是否需要升级两端的 MSMQ 基础结构？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-127">Do I need to upgrade both sides of my MSMQ infrastructure?</span></span>

<span data-ttu-id="2a8f3-128">**答：** 否。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-128">**A:** No.</span></span> <span data-ttu-id="2a8f3-129">您不必将任何一端升级到 MSMQ 4.0。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-129">You do not have to upgrade to MSMQ 4.0 on either side.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="2a8f3-130">疑难解答</span><span class="sxs-lookup"><span data-stu-id="2a8f3-130">Troubleshooting</span></span>

<span data-ttu-id="2a8f3-131">此部分包含大多数常见疑难问题的答案。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-131">This section contains answers to most common troubleshooting issues.</span></span> <span data-ttu-id="2a8f3-132">某些已知限制问题还将在发行说明中进行介绍。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-132">Some issues that are known limitations are also described in the release notes.</span></span>

<span data-ttu-id="2a8f3-133">**问：** 我尝试使用专用队列，但收到以下异常： `System.InvalidOperationException`： URL 无效。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-133">**Q:** I am trying to use a private queue and I get the following exception: `System.InvalidOperationException`: The URL is invalid.</span></span> <span data-ttu-id="2a8f3-134">队列的 URL 不能包含“$”字符。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-134">The URL for the queue cannot contain the '$' character.</span></span> <span data-ttu-id="2a8f3-135">使用 net.msmq://machine/private/queueName 中的语法指定专有队列的地址。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-135">Use the syntax in net.msmq://machine/private/queueName to address a private queue.</span></span>

<span data-ttu-id="2a8f3-136">**答：** 请在配置和代码中检查队列统一资源标识符（URI）。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-136">**A:** Please check the queue Uniform Resource Identifier (URI) in your configuration and code.</span></span> <span data-ttu-id="2a8f3-137">不要在 URI 中使用“$”字符。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-137">Do not use the "$" character in the URI.</span></span> <span data-ttu-id="2a8f3-138">例如，若要为名为 OrdersQueue 的专有队列指定地址，可以将 URI 指定为 net.msmq://localhost/private/ordersQueue。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-138">For example, to address a private queue named OrdersQueue, specify the URI as net.msmq://localhost/private/ordersQueue.</span></span>

<span data-ttu-id="2a8f3-139">**问：** 对排队的应用程序调用 `ServiceHost.Open()` 将引发以下异常： `System.ArgumentException`：基址中不能包含 URI 查询字符串。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-139">**Q:** Calling `ServiceHost.Open()` on my queued application throws the following exception: `System.ArgumentException`: A base address cannot contain a URI query string.</span></span> <span data-ttu-id="2a8f3-140">为什么？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-140">Why?</span></span>

<span data-ttu-id="2a8f3-141">**答：** 检查配置文件和代码中的队列 URI。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-141">**A:** Check the queue URI in your configuration file and in your code.</span></span> <span data-ttu-id="2a8f3-142">虽然 MSMQ 队列支持使用“?”字符，但 URI 将此字符解释为字符串查询的开头。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-142">While MSMQ queues support the use of the '?' character, URIs interpret this character as the beginning of a string query.</span></span> <span data-ttu-id="2a8f3-143">若要避免此问题，请使用不包含“?”字符的队列名称。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-143">To avoid this issue, use queue names that do not contain '?' characters.</span></span>

<span data-ttu-id="2a8f3-144">**问：** 已成功发送，但没有在接收方调用任何服务操作。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-144">**Q:** My send succeeded but no service operation is invoked on the receiver.</span></span> <span data-ttu-id="2a8f3-145">为什么？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-145">Why?</span></span>

<span data-ttu-id="2a8f3-146">**答：** 若要确定答案，请通过以下检查列表进行操作：</span><span class="sxs-lookup"><span data-stu-id="2a8f3-146">**A:** To determine the answer, work through the following check list:</span></span>

- <span data-ttu-id="2a8f3-147">检查事务性队列需求是否与指定的保证相符。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-147">Check that the transactional queue requirements are compatible with the assurances specified.</span></span> <span data-ttu-id="2a8f3-148">请注意下面的原则：</span><span class="sxs-lookup"><span data-stu-id="2a8f3-148">Note the following principles:</span></span>

  - <span data-ttu-id="2a8f3-149">仅可通过 "仅一次" （<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`）将持久消息（数据报和会话）发送到事务性队列。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-149">You can send durable messages (datagrams and sessions) with "exactly once" assurances (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) only to a transactional queue.</span></span>

  - <span data-ttu-id="2a8f3-150">可以发送只具有“一次性”保证的会话。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-150">You can send sessions only with "exactly once" assurances.</span></span>

  - <span data-ttu-id="2a8f3-151">需要使用事务从事务性队列接收会话中的消息。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-151">A transaction is required to receive messages in a session from a transactional queue.</span></span>

  - <span data-ttu-id="2a8f3-152">您可以仅向非事务性队列发送或接收不能保证（<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`）的可变或持久消息（仅限数据报）。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-152">You can send or receive volatile or durable messages (datagrams only) with no assurances (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) only to a non-transactional queue.</span></span>

- <span data-ttu-id="2a8f3-153">检查死信队列。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-153">Check the dead-letter queue.</span></span> <span data-ttu-id="2a8f3-154">如果在此处找到消息，则确定没有传送这些消息的原因。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-154">If you find the messages there, determine why they were not delivered.</span></span>

- <span data-ttu-id="2a8f3-155">检查传出队列的连通性或寻址问题。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-155">Check the outgoing queues for connectivity or addressing problems.</span></span>

<span data-ttu-id="2a8f3-156">**问：** 我指定了一个自定义死信队列，但当我启动发送程序应用程序时，我收到一个例外，指出未找到死信队列，或发送应用程序没有对死信队列的权限。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-156">**Q:** I have specified a custom dead-letter queue, but when I start the sender application, I get an exception that either the dead-letter queue is not found, or the sending application has no permission to the dead-letter queue.</span></span> <span data-ttu-id="2a8f3-157">为什么会出现这种情况？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-157">Why is this happening?</span></span>

<span data-ttu-id="2a8f3-158">**答：** 自定义死信队列 URI 必须在第一段包含 "localhost" 或计算机名称，例如，net.pipe：//localhost/private/myAppdead-letter queue。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-158">**A:** The custom dead-letter queue URI must include a "localhost" or the computer name in the first segment, for example, net.msmq://localhost/private/myAppdead-letter queue.</span></span>

<span data-ttu-id="2a8f3-159">**问：** 是否始终需要定义自定义死信队列，或是否有默认的死信队列？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-159">**Q:** Is it always necessary to define a custom dead-letter queue, or is there a default dead-letter queue?</span></span>

<span data-ttu-id="2a8f3-160">**答：** 如果保证为 "恰好一次" （<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`），并且如果未指定自定义死信队列，则默认为系统级事务性死信队列。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-160">**A:** If assurances are "exactly once" (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), and if you do not specify a custom dead-letter queue, the default is a system-wide transactional dead-letter queue.</span></span>

<span data-ttu-id="2a8f3-161">如果保证为 "无" （<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`），则默认值为 "无死信队列" 功能。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-161">If assurances are none (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), then the default is no dead-letter queue functionality.</span></span>

<span data-ttu-id="2a8f3-162">**问：** 我的服务在 SvcHost 上抛出。打开并出现消息 "调用 svchost.open 时无法满足 EndpointListener 要求"。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-162">**Q:** My service throws on SvcHost.Open with a message "EndpointListener requirements cannot be met by the ListenerFactory".</span></span> <span data-ttu-id="2a8f3-163">为什么？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-163">Why?</span></span>

<span data-ttu-id="2a8f3-164">答：</span><span class="sxs-lookup"><span data-stu-id="2a8f3-164">A.</span></span> <span data-ttu-id="2a8f3-165">请检查您的服务协定。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-165">Check your service contract.</span></span> <span data-ttu-id="2a8f3-166">您可能忘记了在所有服务操作上放置 "IsOneWay =`true`"。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-166">You may have forgotten to put "IsOneWay=`true`" on all the service operations.</span></span> <span data-ttu-id="2a8f3-167">队列仅支持单向服务操作。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-167">Queues support only one-way service operations.</span></span>

<span data-ttu-id="2a8f3-168">**问：** 队列中有消息，但未调用任何服务操作。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-168">**Q:** There are messages in the queue but no service operation is invoked.</span></span> <span data-ttu-id="2a8f3-169">有什么问题？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-169">What is the problem?</span></span>

<span data-ttu-id="2a8f3-170">**答：** 确定服务主机是否出错。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-170">**A:** Determine if your service host is faulted.</span></span> <span data-ttu-id="2a8f3-171">可以通过查看跟踪情况或实现 `IErrorHandler` 进行检查。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-171">You can check by looking at the trace or implementing `IErrorHandler`.</span></span> <span data-ttu-id="2a8f3-172">默认情况下，如果检测到病毒消息，则服务主机将出现故障。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-172">Service host faults, by default, if a poison message is detected.</span></span>

<span data-ttu-id="2a8f3-173">**问：** 队列中有消息，但 Web 托管的排队服务未激活。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-173">**Q:** There are messages in the queue but my Web-hosted queued service is not getting activated.</span></span> <span data-ttu-id="2a8f3-174">为什么？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-174">Why?</span></span>

<span data-ttu-id="2a8f3-175">**答：** 最常见的原因是权限。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-175">**A:** The most common reason is permissions.</span></span>

1. <span data-ttu-id="2a8f3-176">确保 `NetMsmqActivator` 进程正在运行，并为 `NetMsmqActivator` 进程的标识提供对此队列的读取和查找权限。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-176">Ensure that the `NetMsmqActivator` process is running and the identity of the `NetMsmqActivator` process is given read and seek permission on the queue.</span></span>

2. <span data-ttu-id="2a8f3-177">如果 `NetMsmqActivator` 正在监视远程计算机上的队列，请确保 `NetMsmqActivator` 不使用受限制的令牌运行。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-177">If the `NetMsmqActivator` is monitoring queues on a remote machine, ensure that `NetMsmqActivator` does not run under a restricted token.</span></span> <span data-ttu-id="2a8f3-178">若要使用不受限制的令牌运行 `NetMsmqActivator`，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2a8f3-178">To run the `NetMsmqActivator` with an unrestricted token:</span></span>

    ```console
    sc sidtype NetMsmqActivator unrestricted
    ```

<span data-ttu-id="2a8f3-179">有关非安全相关的 Web 主机问题，请参阅：[承载排队应用程序的 web](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-179">For non-security related Web host issues refer to: [Web Hosting a Queued Application](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).</span></span>

<span data-ttu-id="2a8f3-180">**问：** 访问会话的最简单方法是什么？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-180">**Q:** What is the easiest way to access sessions?</span></span>

<span data-ttu-id="2a8f3-181">**答：** 在操作中设置 "自动完成" =`true` 与会话中的最后一条消息相对应，并在所有剩余服务操作中设置 "自动完成 =`false`"。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-181">**A:** Set AutoComplete=`true` on the operation that corresponds to the last message in the session, and set AutoComplete=`false` on all remaining service operations.</span></span>

<span data-ttu-id="2a8f3-182">**问：** 在哪里可以找到有关 MSMQ 的常见问题的答案？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-182">**Q:** Where can I find answers to common questions on MSMQ?</span></span>

<span data-ttu-id="2a8f3-183">**答：** 有关 MSMQ 的详细信息，请参阅[Microsoft 消息队列](https://go.microsoft.com/fwlink/?LinkId=87810)。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-183">**A:** For more information about MSMQ, see [Microsoft Message Queuing](https://go.microsoft.com/fwlink/?LinkId=87810).</span></span>

<span data-ttu-id="2a8f3-184">**问：** 为什么当从包含排队会话消息和排队数据报消息的队列中进行读取时，服务才会引发 `ProtocolException`？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-184">**Q:** Why does my service throw a `ProtocolException` when reading from a queue that contains both queued session messages and queued datagram messages?</span></span>

<span data-ttu-id="2a8f3-185">**答：** 排队会话消息和排队数据报消息的构建方式存在根本的差异。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-185">**A:** There is a fundamental difference in the way queued session messages and queued datagram messages are composed.</span></span> <span data-ttu-id="2a8f3-186">因此，要读取排队会话消息的服务无法接收排队数据报消息，而要读取排队数据报消息的服务也无法接收会话消息。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-186">Because of this, a service that is expecting to read a queued session message cannot receive a queued datagram message and a service expecting to read a queued datagram message cannot receive a session message.</span></span> <span data-ttu-id="2a8f3-187">试图从同一个队列读取这两种消息时将引发以下异常：</span><span class="sxs-lookup"><span data-stu-id="2a8f3-187">Attempting to read both types of messages from the same queue throws the following exception:</span></span>

```console
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.
```

<span data-ttu-id="2a8f3-188">当应用程序从同一台计算机既发送排队会话消息又发送排队数据报消息时，系统死信队列以及任何自定义死信队列对这种问题尤其敏感。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-188">The system dead-letter queue, as well as any custom dead-letter queue, is particularly susceptible to this issue if an application sends both queued session messages and queued datagram messages from the same computer.</span></span> <span data-ttu-id="2a8f3-189">如果消息无法成功发送，则会被移入死信队列。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-189">If a message cannot be sent successfully, it is moved to the dead-letter queue.</span></span> <span data-ttu-id="2a8f3-190">在这些情况下，很有可能将会话消息和数据报消息都移入死信队列。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-190">Under these circumstances, it is possible to have both session and datagram messages in the dead-letter queue.</span></span> <span data-ttu-id="2a8f3-191">从队列进行读取时，无法在运行时将两种消息分开。因此，应用程序不应从同一台计算机既发送排队会话消息又发送排队数据报消息。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-191">There is no way to separate both types of messages at runtime when reading from a queue, therefore, applications should not send both queued session messages and queued datagram messages from the same computer.</span></span>

### <a name="msmq-integration-specific-troubleshooting"></a><span data-ttu-id="2a8f3-192">MSMQ 集成：特定的疑难解答</span><span class="sxs-lookup"><span data-stu-id="2a8f3-192">MSMQ Integration: Specific Troubleshooting</span></span>

<span data-ttu-id="2a8f3-193">**问：** 发送消息时，或打开服务主机时，出现错误，指出方案错误。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-193">**Q:** When I send a message, or when I open the service host, I get an error that indicates the scheme is wrong.</span></span> <span data-ttu-id="2a8f3-194">为什么？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-194">Why?</span></span>

<span data-ttu-id="2a8f3-195">**答：** 如果使用 MSMQ 集成绑定，则必须使用 msmq.formatname 方案。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-195">**A:** When you use the MSMQ integration binding, you must use the msmq.formatname scheme.</span></span> <span data-ttu-id="2a8f3-196">例如，msmq.formatname:DIRECT=OS:.\private$\OrdersQueue。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-196">For example, msmq.formatname:DIRECT=OS:.\private$\OrdersQueue.</span></span> <span data-ttu-id="2a8f3-197">但是，如果您指定自定义死信队列，则必须使用 net.msmq 方案。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-197">But when you specify the custom dead-letter queue, you must use the net.msmq scheme.</span></span>

<span data-ttu-id="2a8f3-198">**问：** 使用公用或专用格式名称并打开 [!INCLUDE[wv](../../../../includes/wv-md.md)]上的服务主机时，出现错误。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-198">**Q:** When I use a public or private format name and open the service host on [!INCLUDE[wv](../../../../includes/wv-md.md)], I get an error.</span></span> <span data-ttu-id="2a8f3-199">为什么？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-199">Why?</span></span>

<span data-ttu-id="2a8f3-200">**答：** [!INCLUDE[wv](../../../../includes/wv-md.md)] 上的 WCF 集成通道检查是否可以为主应用程序队列打开子队列，以便处理病毒消息。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-200">**A:** The WCF integration channel on [!INCLUDE[wv](../../../../includes/wv-md.md)] checks to see if a sub-queue can be opened for the main application queue for handling poison messages.</span></span> <span data-ttu-id="2a8f3-201">子队列名称派生自传递到侦听器的 msmq.formatname URI。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-201">The sub-queue name is derived from an msmq.formatname URI passed to the listener.</span></span> <span data-ttu-id="2a8f3-202">MSMQ 中的子队列名只能是直接格式名。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-202">The sub-queue name in MSMQ can only be a direct format name.</span></span> <span data-ttu-id="2a8f3-203">因此，您会发现以上错误。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-203">So you see the error.</span></span> <span data-ttu-id="2a8f3-204">将队列 URI 改为直接格式名。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-204">Change the queue URI to a direct format name.</span></span>

<span data-ttu-id="2a8f3-205">**问：** 从 MSMQ 应用程序接收消息时，消息位于队列中，并且不由接收 WCF 应用程序读取。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-205">**Q:** When receiving a message from an MSMQ application, the message sits in the queue and is not read by the receiving WCF application.</span></span> <span data-ttu-id="2a8f3-206">为什么？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-206">Why?</span></span>

<span data-ttu-id="2a8f3-207">**答：** 检查消息是否具有正文。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-207">**A:** Check to see whether the message has a body.</span></span> <span data-ttu-id="2a8f3-208">如果消息没有正文，则 MSMQ 集成通道会忽略此消息。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-208">If the message has no body, the MSMQ integration channel ignores the message.</span></span> <span data-ttu-id="2a8f3-209">实现向其通知异常的 `IErrorHandler` 并检查跟踪情况。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-209">Implement `IErrorHandler` to be notified of exceptions and check the traces.</span></span>

### <a name="security-related-troubleshooting"></a><span data-ttu-id="2a8f3-210">与安全相关的疑难解答</span><span class="sxs-lookup"><span data-stu-id="2a8f3-210">Security-Related Troubleshooting</span></span>

<span data-ttu-id="2a8f3-211">**问：** 当我在工作组模式下运行使用默认绑定的示例时，消息似乎已发送，但接收方永远无法接收。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-211">**Q:** When I run the sample that uses a default binding in workgroup mode, messages seem to get sent but are never received by the receiver.</span></span>

<span data-ttu-id="2a8f3-212">**答：** 默认情况下，使用需要 Active Directory Directory 服务的 MSMQ 内部证书对消息进行签名。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-212">**A:** By default, messages are signed using an MSMQ internal certificate that requires the Active Directory directory service.</span></span> <span data-ttu-id="2a8f3-213">在工作组模式下，因为 Active Directory 不可用，所以对消息的签名会失败。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-213">In workgroup mode, because Active Directory is not available, signing the message fails.</span></span> <span data-ttu-id="2a8f3-214">因此，会显示消息 "死信队列" 和 "失败原因"，如 "签名无效"。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-214">So the message lands in the dead-letter queue and failure cause, such as "Bad signature", is indicated.</span></span>

<span data-ttu-id="2a8f3-215">解决方法是关闭安全性。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-215">The workaround is to turn off security.</span></span> <span data-ttu-id="2a8f3-216">为此，可设置 <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A> = <xref:System.ServiceModel.NetMsmqSecurityMode.None>，使其在工作组模式下工作。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-216">This is done by setting <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A> = <xref:System.ServiceModel.NetMsmqSecurityMode.None> to make it work in workgroup mode.</span></span>

<span data-ttu-id="2a8f3-217">另一个解决方法是从 <xref:System.ServiceModel.MsmqTransportSecurity> 属性获取 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> 并将其设置为 <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>，然后设置客户端证书。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-217">Another workaround is to get the <xref:System.ServiceModel.MsmqTransportSecurity> from the <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> property and set it to <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, and set the client certificate.</span></span>

<span data-ttu-id="2a8f3-218">还有一种解决方法就是安装集成了 Active Directory 的 MSMQ。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-218">Yet another workaround is to install MSMQ with Active Directory integration.</span></span>

<span data-ttu-id="2a8f3-219">**问：** 当我将 Active Directory 中的消息发送到队列时，会收到 "未找到内部证书" 消息。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-219">**Q:** When I send a message with default binding (transport security turned on) in Active Directory to a queue, I get an "internal certificate not found" message.</span></span> <span data-ttu-id="2a8f3-220">如何修复此问题？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-220">How do I fix this?</span></span>

<span data-ttu-id="2a8f3-221">**答：** 这意味着必须续订发送方 Active Directory 的证书。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-221">**A:** This means that the certificate in Active Directory for the sender must be renewed.</span></span> <span data-ttu-id="2a8f3-222">为此，请打开 **"控制面板**"、"**管理工具**"、"**计算机管理**"，右键单击 " **MSMQ**"，然后选择 "**属性**"。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-222">To do so, open **Control Panel**, **Administrative Tools**, **Computer Management**, right-click **MSMQ**, and select **Properties**.</span></span> <span data-ttu-id="2a8f3-223">选择 "**用户证书**" 选项卡，然后单击 "**续订**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-223">Select the **User Certificate** tab and click the **Renew** button.</span></span>

<span data-ttu-id="2a8f3-224">**问：** 当我使用 <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> 发送消息并指定要使用的证书时，会收到 "证书无效" 消息。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-224">**Q:** When I send a message using <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> and specify the certificate to use, I get an "Invalid certificate" message.</span></span> <span data-ttu-id="2a8f3-225">如何修复此问题？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-225">How do I fix this?</span></span>

<span data-ttu-id="2a8f3-226">**答：** 不能将本地计算机证书存储与证书模式一起使用。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-226">**A:** You cannot use a local machine certificate store with certificate mode.</span></span> <span data-ttu-id="2a8f3-227">必须使用证书管理单元将证书从计算机证书存储区复制到当前用户存储区。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-227">You have to copy the certificate from the machine certificate store to the current user store using the Certificate snap-in.</span></span> <span data-ttu-id="2a8f3-228">若要打开证书管理单元，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="2a8f3-228">To get the Certificate snap-in:</span></span>

1. <span data-ttu-id="2a8f3-229">单击 "**开始**"，选择 "**运行**"，键入 `mmc`，然后单击 **"确定"** 。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-229">Click **Start**, select **Run**, type `mmc`, and click **OK**.</span></span>

2. <span data-ttu-id="2a8f3-230">在**Microsoft 管理控制台**中，打开 "**文件**" 菜单，然后选择 "**添加/删除管理单元**"。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-230">In the **Microsoft Management Console**, open the **File** menu and select **Add/Remove Snap-in**.</span></span>

3. <span data-ttu-id="2a8f3-231">在 "**添加/删除管理单元**" 对话框中，单击 "**添加**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-231">In the **Add/Remove Snap-in** dialog box, click the **Add** button.</span></span>

4. <span data-ttu-id="2a8f3-232">在 "**添加独立管理单元**" 对话框中，选择 "证书"，然后单击 "**添加**"。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-232">In the **Add Standalone Snap-in** dialog box, select Certificates and click **Add**.</span></span>

5. <span data-ttu-id="2a8f3-233">在 "**证书**管理单元" 对话框中，选择 "**我的用户帐户"，** 然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-233">In the **Certificates** snap-in dialog box, select **My user account,** and click **Finish**.</span></span>

6. <span data-ttu-id="2a8f3-234">接下来，使用前面的步骤添加另一个证书管理单元，但这次请选择 "**计算机帐户**"，然后单击 "**下一步**"。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-234">Next, add a second Certificates snap-in using the previous steps, but this time select **Computer account** and click **Next**.</span></span>

7. <span data-ttu-id="2a8f3-235">选择 "**本地计算机**"，然后单击 "**完成**"。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-235">Select **Local Computer** and click **Finish**.</span></span> <span data-ttu-id="2a8f3-236">现在，可以将证书从计算机证书存储区拖放到当前用户存储区。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-236">You can now drag and drop certificates from the machine certificate store to the current user store.</span></span>

<span data-ttu-id="2a8f3-237">**问：** 当我的服务在工作组模式下从另一台计算机上的队列中读取时，出现 "拒绝访问" 异常。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-237">**Q:** When my service reads from a queue on another computer in workgroup mode, I get an "access denied" exception.</span></span>

<span data-ttu-id="2a8f3-238">**答：** 在工作组模式下，对于远程应用程序，若要获取对队列的访问权限，该应用程序必须有权访问该队列。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-238">**A:** In workgroup mode, for a remote application to gain access to the queue, the application must have permission to access the queue.</span></span> <span data-ttu-id="2a8f3-239">向队列的访问控制列表（ACL）添加 "匿名登录"，并向其授予 "读取" 权限。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-239">Add "Anonymous login" to the queue's access control list (ACL) and give it read permission.</span></span>

<span data-ttu-id="2a8f3-240">**问：** 当网络服务客户端（或没有域帐户的任何客户端）发送排队消息时，发送将失败，并出现无效证书。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-240">**Q:** When a network service client (or any client that does not have a domain account) sends a queued message, the send fails with an invalid certificate.</span></span> <span data-ttu-id="2a8f3-241">如何修复此问题？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-241">How do I fix this?</span></span>

<span data-ttu-id="2a8f3-242">**答：** 检查绑定配置。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-242">**A:** Check the binding configuration.</span></span> <span data-ttu-id="2a8f3-243">默认绑定会打开 MSMQ 传输安全以对消息进行签名。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-243">The default binding has MSMQ transport security turned on to sign the message.</span></span> <span data-ttu-id="2a8f3-244">关闭该传输安全。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-244">Turn it off.</span></span>

### <a name="remote-transacted-receives"></a><span data-ttu-id="2a8f3-245">远程事务处理接收</span><span class="sxs-lookup"><span data-stu-id="2a8f3-245">Remote Transacted Receives</span></span>

<span data-ttu-id="2a8f3-246">**问：** 当我在计算机 A 上有一个队列，而在计算机 B 上读取消息的 WCF 服务（远程事务处理接收方案）时，不会从队列中读取消息。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-246">**Q:** When I have a queue on machine A, and a WCF service that reads messages from a queue on machine B (the remote transacted receive scenario), messages are not read from the queue.</span></span> <span data-ttu-id="2a8f3-247">跟踪信息指示接收失败，并显示消息 "无法导入事务"。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-247">Tracing information indicates the receive failed with the message "Transaction cannot be imported."</span></span> <span data-ttu-id="2a8f3-248">可以执行哪些操作来解决此问题？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-248">What can I do to fix this?</span></span>

<span data-ttu-id="2a8f3-249">**答：** 有三个可能的原因：</span><span class="sxs-lookup"><span data-stu-id="2a8f3-249">**A:** There are three possible reasons for this:</span></span>

- <span data-ttu-id="2a8f3-250">如果处于域模式下，则远程事务处理接收要求 Microsoft 分布式事务协调器 (MSDTC) 网络访问。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-250">If you are in domain mode, remote transacted receive requires Microsoft Distributed Transaction Coordinator (MSDTC) network access.</span></span> <span data-ttu-id="2a8f3-251">你可以使用 "**添加/删除组件**" 启用它。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-251">You can enable this using **Add/Remove Components**.</span></span>

  ![显示启用网络 DTC 访问的屏幕截图。](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)

- <span data-ttu-id="2a8f3-253">检查与事务管理器进行通信的身份验证模式。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-253">Check the authentication mode for communicating with the transaction manager.</span></span> <span data-ttu-id="2a8f3-254">如果处于工作组模式，则必须选择 "不要求进行身份验证"。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-254">If you are in workgroup mode, "No Authentication Required" must be selected.</span></span> <span data-ttu-id="2a8f3-255">如果处于域模式下，则必须选择 "需要相互身份验证"。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-255">If you are in domain mode, then "Mutual Authentication Required" must be selected.</span></span>

  <span data-ttu-id="2a8f3-256">![启用 XA 事务](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")</span><span class="sxs-lookup"><span data-stu-id="2a8f3-256">![Enabling XA transactions](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")</span></span>

- <span data-ttu-id="2a8f3-257">请确保 MSDTC 位于**Internet 连接防火墙**设置中的例外列表中。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-257">Make sure that MSDTC is in the list of exceptions in the **Internet Connection Firewall** settings.</span></span>

- <span data-ttu-id="2a8f3-258">确保您使用的是 [!INCLUDE[wv](../../../../includes/wv-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-258">Ensure that you are using [!INCLUDE[wv](../../../../includes/wv-md.md)].</span></span> <span data-ttu-id="2a8f3-259">[!INCLUDE[wv](../../../../includes/wv-md.md)] 上的 MSMQ 支持远程事务处理读取。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-259">MSMQ on [!INCLUDE[wv](../../../../includes/wv-md.md)] supports remote transacted read.</span></span> <span data-ttu-id="2a8f3-260">早期的 Windows 版本上的 MSMQ 不支持远程事务处理读取。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-260">MSMQ on earlier Windows releases does not support remote transacted read.</span></span>

<span data-ttu-id="2a8f3-261">**问：** 如果从队列中读取的服务是一个网络服务，例如，在 Web 主机上，从队列中读取时，为什么会出现 "拒绝访问" 异常？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-261">**Q:** When the service reading from the queue is a network service, for example, in a Web host, why do I get an access-denied exception is raised when reading from the queue?</span></span>

<span data-ttu-id="2a8f3-262">**答：** 必须将网络服务读取访问权限添加到队列 ACL，以确保网络服务可以从队列中读取。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-262">**A:** Network service read access must be added to the queue ACL to ensure that a network service can read from the queue.</span></span>

<span data-ttu-id="2a8f3-263">**问：** 是否可以使用 MSMQ 激活服务根据远程计算机上的队列中的消息激活应用程序？</span><span class="sxs-lookup"><span data-stu-id="2a8f3-263">**Q:** Can I use the MSMQ activation service to activate applications based on messages in a queue on a remote machine?</span></span>

<span data-ttu-id="2a8f3-264">**答：** 可以。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-264">**A:** Yes.</span></span> <span data-ttu-id="2a8f3-265">为此，您必须将 MSMQ 激活服务配置为以网络服务方式运行，并将网络服务访问权限添加到远程计算机上的队列中。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-265">To do this, you must configure the MSMQ activation service to run as a network service, and add network service access to the queue on the remote machine.</span></span>

## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a><span data-ttu-id="2a8f3-266">使用已启用 ReceiveContext 的自定义 MSMQ 绑定</span><span class="sxs-lookup"><span data-stu-id="2a8f3-266">Using Custom MSMQ Bindings with ReceiveContext Enabled</span></span>

<span data-ttu-id="2a8f3-267">当将自定义 MSMQ 绑定用于已启用 <xref:System.ServiceModel.Channels.ReceiveContext> 的处理时，传入消息将使用一个线程池线程，这是因为本机 MSMQ 不支持异步 <xref:System.ServiceModel.Channels.ReceiveContext> 接收的 I/O 完成。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-267">When using a custom MSMQ binding with <xref:System.ServiceModel.Channels.ReceiveContext> enabled processing an incoming message will use a thread pool thread because native MSMQ does not support I/O completion for asynchronous <xref:System.ServiceModel.Channels.ReceiveContext> receives.</span></span> <span data-ttu-id="2a8f3-268">这是因为处理此类消息需使用 <xref:System.ServiceModel.Channels.ReceiveContext> 的内部事务，并且 MSMQ 不支持异步处理。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-268">This is because processing such a message uses internal transactions for <xref:System.ServiceModel.Channels.ReceiveContext> and MSMQ does not support asynchronous processing.</span></span> <span data-ttu-id="2a8f3-269">若要解决此问题，可将 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> 添加到终结点以强制进行同步处理或将 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> 设置为 1。</span><span class="sxs-lookup"><span data-stu-id="2a8f3-269">To work around this issue you can add a <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> to the endpoint to force synchronous processing or set <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> to 1.</span></span>
