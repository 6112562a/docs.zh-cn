---
title: Windows Communication Foundation 中的队列
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: 92bd3a6809386764251c4a69c6bc583ed745205d
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921362"
---
# <a name="queues-in-windows-communication-foundation"></a><span data-ttu-id="64a9a-102">Windows Communication Foundation 中的队列</span><span class="sxs-lookup"><span data-stu-id="64a9a-102">Queues in Windows Communication Foundation</span></span>
<span data-ttu-id="64a9a-103">本节中的主题讨论 Windows Communication Foundation （WCF）对队列的支持。</span><span class="sxs-lookup"><span data-stu-id="64a9a-103">The topics in this section discuss Windows Communication Foundation (WCF) support for queues.</span></span> <span data-ttu-id="64a9a-104">WCF 通过利用 Microsoft 消息队列（以前称为 MSMQ）作为传输来提供队列支持，并启用以下方案：</span><span class="sxs-lookup"><span data-stu-id="64a9a-104">WCF provides support for queuing by leveraging Microsoft Message Queuing (previously known as MSMQ) as a transport and enables the following scenarios:</span></span>  
  
- <span data-ttu-id="64a9a-105">松耦合应用程序。</span><span class="sxs-lookup"><span data-stu-id="64a9a-105">Loosely coupled applications.</span></span> <span data-ttu-id="64a9a-106">发送应用程序可以将消息发送到队列，而无需知道接收应用程序是否可用于处理该消息。</span><span class="sxs-lookup"><span data-stu-id="64a9a-106">Sending applications can send messages to queues without needing to know whether the receiving application is available to process the message.</span></span> <span data-ttu-id="64a9a-107">队列提供了处理独立性，它允许发送应用程序将消息以一定的速率发送到队列，该速率不依赖于接收应用程序的消息处理速度。</span><span class="sxs-lookup"><span data-stu-id="64a9a-107">The queue provides processing independence that allows a sending application to send messages to the queue at a rate that does not depend on how fast the receiving applications can process the messages.</span></span> <span data-ttu-id="64a9a-108">如果向队列发送消息的操作与消息处理的操作不是紧密耦合的，则会提高系统的整体可用性。</span><span class="sxs-lookup"><span data-stu-id="64a9a-108">Overall system availability increases when sending messages to a queue is not tightly coupled to message processing.</span></span>  
  
- <span data-ttu-id="64a9a-109">故障隔离。</span><span class="sxs-lookup"><span data-stu-id="64a9a-109">Failure isolation.</span></span> <span data-ttu-id="64a9a-110">应用程序与队列之间发送或接收消息如果失败，两种操作互不影响。</span><span class="sxs-lookup"><span data-stu-id="64a9a-110">Applications sending or receiving messages to a queue can fail without affecting each other.</span></span> <span data-ttu-id="64a9a-111">例如，如果接收应用程序失败，发送应用程序可以继续向队列发送消息。</span><span class="sxs-lookup"><span data-stu-id="64a9a-111">If, for example, the receiving application fails, the sending application can continue to send messages to the queue.</span></span> <span data-ttu-id="64a9a-112">接收方再次启动时，即可处理队列中的消息。</span><span class="sxs-lookup"><span data-stu-id="64a9a-112">When the receiver is up again, it can process the messages from the queue.</span></span> <span data-ttu-id="64a9a-113">故障隔离提高了整体系统的可靠性和可用性。</span><span class="sxs-lookup"><span data-stu-id="64a9a-113">Failure isolation increases the overall system reliability and availability.</span></span>  
  
- <span data-ttu-id="64a9a-114">负载量。</span><span class="sxs-lookup"><span data-stu-id="64a9a-114">Load leveling.</span></span> <span data-ttu-id="64a9a-115">发送应用程序发出的消息可能使接收应用程序过载。</span><span class="sxs-lookup"><span data-stu-id="64a9a-115">Sending applications can overwhelm receiving applications with messages.</span></span> <span data-ttu-id="64a9a-116">队列可以管理不匹配的消息生成率和处理率，以使接收方不会过载。</span><span class="sxs-lookup"><span data-stu-id="64a9a-116">Queues can manage mismatched message production and consumption rates so that a receiver is not overwhelmed.</span></span>  
  
- <span data-ttu-id="64a9a-117">断开连接的操作。</span><span class="sxs-lookup"><span data-stu-id="64a9a-117">Disconnected operations.</span></span> <span data-ttu-id="64a9a-118">在高延迟网络或有限可用性网络上通信（例如，在移动设备中）时，发送、接收和处理操作可能会断开连接。</span><span class="sxs-lookup"><span data-stu-id="64a9a-118">Sending, receiving, and processing operations can become disconnected when communicating over high-latency networks or limited-availability networks, such as in the case of mobile devices.</span></span> <span data-ttu-id="64a9a-119">队列允许这些操作继续执行，即使终结点断开连接也是如此。</span><span class="sxs-lookup"><span data-stu-id="64a9a-119">Queues allow these operations to continue, even when the endpoints are disconnected.</span></span> <span data-ttu-id="64a9a-120">重新建立连接后，队列将消息转发到接收应用程序。</span><span class="sxs-lookup"><span data-stu-id="64a9a-120">When the connection is reestablished, the queue forwards messages to the receiving application.</span></span>  
  
 <span data-ttu-id="64a9a-121">若要在 WCF 应用程序中使用队列功能，可以使用其中一个标准绑定，如果其中一个标准绑定不满足你的要求，则可以创建自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="64a9a-121">To use the queues feature in a WCF application, you can use one of the standard bindings, or you can create a custom binding if one of the standard bindings does not satisfy your requirements.</span></span> <span data-ttu-id="64a9a-122">有关相关标准绑定和如何选择的详细信息，请参阅[如何：与 WCF 终结点和消息队列应用程序交换消息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="64a9a-122">For more information about relevant standard bindings and how to choose one, see [How to: Exchange Messages with WCF Endpoints and Message Queuing Applications](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).</span></span> <span data-ttu-id="64a9a-123">有关创建自定义绑定的详细信息，请参阅[自定义绑定](../../../../docs/framework/wcf/extending/custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="64a9a-123">For more information about creating custom bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64a9a-124">本节内容</span><span class="sxs-lookup"><span data-stu-id="64a9a-124">In This Section</span></span>  
 [<span data-ttu-id="64a9a-125">队列概述</span><span class="sxs-lookup"><span data-stu-id="64a9a-125">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 <span data-ttu-id="64a9a-126">消息队列概念概述。</span><span class="sxs-lookup"><span data-stu-id="64a9a-126">An overview of message queuing concepts.</span></span>  
  
 [<span data-ttu-id="64a9a-127">在 WCF 中排队</span><span class="sxs-lookup"><span data-stu-id="64a9a-127">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 <span data-ttu-id="64a9a-128">WCF 队列支持概述。</span><span class="sxs-lookup"><span data-stu-id="64a9a-128">An overview of WCF queue support.</span></span>  
  
 [<span data-ttu-id="64a9a-129">如何：使用 WCF 终结点交换排队消息</span><span class="sxs-lookup"><span data-stu-id="64a9a-129">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 <span data-ttu-id="64a9a-130">介绍如何使用 <xref:System.ServiceModel.NetMsmqBinding> 类在 WCF 客户端和 WCF 服务之间进行通信。</span><span class="sxs-lookup"><span data-stu-id="64a9a-130">Explains how to use the <xref:System.ServiceModel.NetMsmqBinding> class to communicate between a WCF client and WCF service.</span></span>  
  
 [<span data-ttu-id="64a9a-131">如何：与 WCF 终结点和消息队列应用程序交换消息</span><span class="sxs-lookup"><span data-stu-id="64a9a-131">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 <span data-ttu-id="64a9a-132">介绍如何使用 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 在 WCF 和消息队列应用程序之间进行通信。</span><span class="sxs-lookup"><span data-stu-id="64a9a-132">Explains how to use the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> to communicate between WCF and Message Queuing applications.</span></span>  
  
 [<span data-ttu-id="64a9a-133">在会话中对排队消息进行分组</span><span class="sxs-lookup"><span data-stu-id="64a9a-133">Grouping Queued Messages in a Session</span></span>](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 <span data-ttu-id="64a9a-134">说明如何对队列中的消息分组，以便单个接收应用程序加速处理相关消息。</span><span class="sxs-lookup"><span data-stu-id="64a9a-134">Explains how to group messages in a queue to facilitate correlated message processing by a single receiving application.</span></span>  
  
 [<span data-ttu-id="64a9a-135">在事务中对消息进行批处理</span><span class="sxs-lookup"><span data-stu-id="64a9a-135">Batching Messages in a Transaction</span></span>](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 <span data-ttu-id="64a9a-136">说明如何在事务中对消息进行批处理。</span><span class="sxs-lookup"><span data-stu-id="64a9a-136">Explains how to batch messages in a transaction.</span></span>  
  
 [<span data-ttu-id="64a9a-137">使用死信队列处理消息传输故障</span><span class="sxs-lookup"><span data-stu-id="64a9a-137">Using Dead-Letter Queues to Handle Message Transfer Failures</span></span>](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 <span data-ttu-id="64a9a-138">说明如何使用死信队列来处理消息传输和传送故障，以及如何处理死信队列中的消息。</span><span class="sxs-lookup"><span data-stu-id="64a9a-138">Explains how to handle message transfer and delivery failures using dead letter queues and how to process messages from the dead letter queue.</span></span>  
  
 [<span data-ttu-id="64a9a-139">有害消息处理</span><span class="sxs-lookup"><span data-stu-id="64a9a-139">Poison Message Handling</span></span>](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 <span data-ttu-id="64a9a-140">说明如何处理病毒消息（向接收应用程序尝试传送的次数超出最大次数的消息）。</span><span class="sxs-lookup"><span data-stu-id="64a9a-140">Explains how to handle poison messages (messages that have exceeded the maximum number of delivery attempts to the receiving application).</span></span>  
  
 [<span data-ttu-id="64a9a-141">Windows Vista、Windows Server 2003 和 Windows XP 在排队功能方面的差异</span><span class="sxs-lookup"><span data-stu-id="64a9a-141">Differences in Queuing Features in Windows Vista, Windows Server 2003, and Windows XP</span></span>](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 <span data-ttu-id="64a9a-142">概述 Windows Vista、Windows Server 2003 和 Windows XP 之间的 WCF 队列功能之间的差异。</span><span class="sxs-lookup"><span data-stu-id="64a9a-142">Summarizes the differences in the WCF queues feature between Windows Vista, Windows Server 2003, and Windows XP.</span></span>  
  
 [<span data-ttu-id="64a9a-143">使用传输安全性保护消息</span><span class="sxs-lookup"><span data-stu-id="64a9a-143">Securing Messages Using Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 <span data-ttu-id="64a9a-144">介绍如何使用传输安全来保护排队消息。</span><span class="sxs-lookup"><span data-stu-id="64a9a-144">Describes how to use transport security to secure queued messages.</span></span>  
  
 [<span data-ttu-id="64a9a-145">使用消息安全性保护消息</span><span class="sxs-lookup"><span data-stu-id="64a9a-145">Securing Messages Using Message Security</span></span>](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 <span data-ttu-id="64a9a-146">介绍如何使用消息安全来保护排队消息。</span><span class="sxs-lookup"><span data-stu-id="64a9a-146">Describes how to use message security to secure queued messages.</span></span>  
  
 [<span data-ttu-id="64a9a-147">排队消息处理疑难解答</span><span class="sxs-lookup"><span data-stu-id="64a9a-147">Troubleshooting Queued Messaging</span></span>](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 <span data-ttu-id="64a9a-148">说明如何解决常见队列问题。</span><span class="sxs-lookup"><span data-stu-id="64a9a-148">Explains how to troubleshoot common queuing problems.</span></span>  
  
 [<span data-ttu-id="64a9a-149">排队通信的最佳做法</span><span class="sxs-lookup"><span data-stu-id="64a9a-149">Best Practices for Queued Communication</span></span>](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 <span data-ttu-id="64a9a-150">介绍使用 WCF 排队通信的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="64a9a-150">Explains best practices for using WCF queued communication.</span></span>  
