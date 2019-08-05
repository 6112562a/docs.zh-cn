---
title: 设计 Docker 应用程序
description: 此处可以找到微服务架构的深入指南的参考，因为这是本指南中未详述的主题。
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674034"
---
# <a name="design-docker-applications"></a><span data-ttu-id="e3b6c-103">设计 Docker 应用程序</span><span class="sxs-lookup"><span data-stu-id="e3b6c-103">Design Docker applications</span></span>

<span data-ttu-id="e3b6c-104">第 1 章介绍了有关容器和 Docker 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="e3b6c-104">Chapter 1 introduced the fundamental concepts regarding containers and Docker.</span></span> <span data-ttu-id="e3b6c-105">该信息是入门所需的基础级别信息。</span><span class="sxs-lookup"><span data-stu-id="e3b6c-105">That information is the basic level of information you need to get started.</span></span> <span data-ttu-id="e3b6c-106">但是，企业应用程序可能会很复杂且由多个服务而不是单个服务或容器组成。</span><span class="sxs-lookup"><span data-stu-id="e3b6c-106">But, enterprise applications can be complex and composed of multiple services instead of a single service or container.</span></span> <span data-ttu-id="e3b6c-107">对于那些可选用例，需要了解其他设计方法，例如面向服务的体系结构 (SOA) 以及更高级的微服务概念和容器业务流程概念。</span><span class="sxs-lookup"><span data-stu-id="e3b6c-107">For those optional use cases, you need to know additional approaches to design, such as Service-Oriented Architecture (SOA) and the more advanced microservices concepts and container orchestration concepts.</span></span> <span data-ttu-id="e3b6c-108">本文档的范围并不局限于微服务，也适用于任何 Docker 应用程序生命周期。因此，本文档不会深入介绍微服务体系结构。因为还可以将容器和 Docker 与常规 SOA、后台任务或作业一起使用，甚至可以使用整体式应用程序部署方法。</span><span class="sxs-lookup"><span data-stu-id="e3b6c-108">The scope of this document is not limited to microservices but to any Docker application life cycle, therefore, it does not explore microservices architecture in depth because you also can use containers and Docker with regular SOA, background tasks or jobs, or even with monolithic application deployment approaches.</span></span>

<span data-ttu-id="e3b6c-109">**详细信息** 要深入了解有关企业应用程序和微服务体系结构的详细信息，请阅读指南 [NET 微服务：适用于容器化 .NET 应用程序的体系结构](../../microservices/index.md)，也可以从 <https://aka.ms/MicroservicesEbook> 下载。</span><span class="sxs-lookup"><span data-stu-id="e3b6c-109">**More info** To learn more about enterprise applications and microservices architecture in depth, read the guide [NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) that you can also download from <https://aka.ms/MicroservicesEbook>.</span></span>

<span data-ttu-id="e3b6c-110">但是，在开始了解应用程序生命周期和 DevOps 之前，了解如何设计和构造应用程序以及设计选择非常重要。</span><span class="sxs-lookup"><span data-stu-id="e3b6c-110">However, before we get into the application life cycle and DevOps, it's important to know how you're going to design and construct your application and what are your design choices.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e3b6c-111">[上一页](index.md)
>[下一页](common-container-design-principles.md)</span><span class="sxs-lookup"><span data-stu-id="e3b6c-111">[Previous](index.md)
[Next](common-container-design-principles.md)</span></span>
