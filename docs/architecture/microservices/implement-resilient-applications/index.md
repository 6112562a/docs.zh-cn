---
title: 实现具有恢复能力的应用程序
description: 了解恢复能力，这是微服务体系结构中的核心概念。 必须了解如何适当地处理瞬间失败，因为将会发生这些失败。
ms.date: 10/16/2018
ms.openlocfilehash: 766349e72389f848b0a741b020707cc7acf3410d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295125"
---
# <a name="implement-resilient-applications"></a><span data-ttu-id="264de-104">实现可复原的应用程序</span><span class="sxs-lookup"><span data-stu-id="264de-104">Implement Resilient Applications</span></span>

<span data-ttu-id="264de-105">微服务和基于云的应用程序必须允许最终必然会发生的部分故障。*必须设计应用程序，使其可从这些部分失败中恢复。*</span><span class="sxs-lookup"><span data-stu-id="264de-105">*Your microservice and cloud-based applications must embrace the partial failures that will certainly occur eventually. You must design your application to be resilient to those partial failures.*</span></span>

<span data-ttu-id="264de-106">恢复能力是指从故障中恢复并继续工作的能力。</span><span class="sxs-lookup"><span data-stu-id="264de-106">Resiliency is the ability to recover from failures and continue to function.</span></span> <span data-ttu-id="264de-107">这并不是指避免失败，而是接受会发生失败这一事实，并以能够避免停机或数据丢失的方式对失败做出响应。</span><span class="sxs-lookup"><span data-stu-id="264de-107">It isn't about avoiding failures but accepting the fact that failures will happen and responding to them in a way that avoids downtime or data loss.</span></span> <span data-ttu-id="264de-108">恢复的目标是使应用程序在发生故障后回到完全正常运行的状态。</span><span class="sxs-lookup"><span data-stu-id="264de-108">The goal of resiliency is to return the application to a fully functioning state after a failure.</span></span>

<span data-ttu-id="264de-109">设计和部署基于微服务的应用程序已经非常具有挑战性。</span><span class="sxs-lookup"><span data-stu-id="264de-109">It's challenging enough to design and deploy a microservices-based application.</span></span> <span data-ttu-id="264de-110">然而还需要让应用程序在必然发生某种故障的环境中保持正常运行。</span><span class="sxs-lookup"><span data-stu-id="264de-110">But you also need to keep your application running in an environment where some sort of failure is certain.</span></span> <span data-ttu-id="264de-111">因此，应用程序应具有恢复能力。</span><span class="sxs-lookup"><span data-stu-id="264de-111">Therefore, your application should be resilient.</span></span> <span data-ttu-id="264de-112">应将其设计为能够处理部分故障，如网络中断或者云中节点或 VM 故障。</span><span class="sxs-lookup"><span data-stu-id="264de-112">It should be designed to cope with partial failures, like network outages or nodes or VMs crashing in the cloud.</span></span> <span data-ttu-id="264de-113">甚至将微服务（容器）移动到群集内的另一个节点，也可能导致应用程序出现间歇性的功能短缺故障。</span><span class="sxs-lookup"><span data-stu-id="264de-113">Even microservices (containers) being moved to a different node within a cluster can cause intermittent short failures within the application.</span></span>

<span data-ttu-id="264de-114">应用程序的各个组件还应涵盖运行状况监视功能。</span><span class="sxs-lookup"><span data-stu-id="264de-114">The many individual components of your application should also incorporate health monitoring features.</span></span> <span data-ttu-id="264de-115">遵循本章节中的准则，可创建这样的应用程序：即使在基于云的复杂部署中出现短暂停机或暂时中断，它也能平稳运行。</span><span class="sxs-lookup"><span data-stu-id="264de-115">By following the guidelines in this chapter, you can create an application that can work smoothly in spite of transient downtime or the normal hiccups that occur in complex and cloud-based deployments.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="264de-116">[上一页](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[下一页](handle-partial-failure.md)</span><span class="sxs-lookup"><span data-stu-id="264de-116">[Previous](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
[Next](handle-partial-failure.md)</span></span>
