---
title: 决策表。 用于 Docker 的 .NET Framework
description: 适用于容器化 .NET 应用程序的 .NET 微服务体系结构 | 决策表，用于 Docker 的 .NET Framework
ms.date: 09/11/2018
ms.openlocfilehash: 96b2750e52d64b06444b7f87dea624879f37d3d7
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2019
ms.locfileid: "68675814"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="59164-104">决策表：用于 Docker 的 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="59164-104">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="59164-105">下列决策表汇总了是使用 .NET Framework 还是 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="59164-105">The following decision table summarizes whether to use .NET Framework or .NET Core.</span></span> <span data-ttu-id="59164-106">请记住，对于 Linux 容器，你需要基于 Linux 的 Docker 主机（VM 或服务器）；对于 Windows 容器，你需要基于 Windows Server 的 Docker 主机（VM 或服务器）。</span><span class="sxs-lookup"><span data-stu-id="59164-106">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="59164-107">开发计算机将运行一个 Docker 主机，Linux 或 Windows 均可。</span><span class="sxs-lookup"><span data-stu-id="59164-107">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="59164-108">想在一个解决方案中一起运行和测试的相关微服务都需要在同一容器平台上运行。</span><span class="sxs-lookup"><span data-stu-id="59164-108">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="59164-109"><strong>体系结构/应用类型</strong></span><span class="sxs-lookup"><span data-stu-id="59164-109"><strong>Architecture / App Type</strong></span></span></th>
<th><span data-ttu-id="59164-110"><strong>Linux 容器</strong></span><span class="sxs-lookup"><span data-stu-id="59164-110"><strong>Linux containers</strong></span></span></th>
<th><span data-ttu-id="59164-111"><strong>Windows 容器</strong></span><span class="sxs-lookup"><span data-stu-id="59164-111"><strong>Windows Containers</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="59164-112">容器上的微服务</span><span class="sxs-lookup"><span data-stu-id="59164-112">Microservices on containers</span></span></td>
<td><span data-ttu-id="59164-113">.NET Core</span><span class="sxs-lookup"><span data-stu-id="59164-113">.NET Core</span></span></td>
<td><span data-ttu-id="59164-114">.NET Core</span><span class="sxs-lookup"><span data-stu-id="59164-114">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="59164-115">单一应用程序</span><span class="sxs-lookup"><span data-stu-id="59164-115">Monolithic app</span></span></td>
<td><span data-ttu-id="59164-116">.NET Core</span><span class="sxs-lookup"><span data-stu-id="59164-116">.NET Core</span></span></td>
<td><p><span data-ttu-id="59164-117">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="59164-117">.NET Framework</span></span></p>
<p><span data-ttu-id="59164-118">.NET Core</span><span class="sxs-lookup"><span data-stu-id="59164-118">.NET Core</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="59164-119">一流性能和可扩展性</span><span class="sxs-lookup"><span data-stu-id="59164-119">Best-in-class performance and scalability</span></span></td>
<td><span data-ttu-id="59164-120">.NET Core</span><span class="sxs-lookup"><span data-stu-id="59164-120">.NET Core</span></span></td>
<td><span data-ttu-id="59164-121">.NET Core</span><span class="sxs-lookup"><span data-stu-id="59164-121">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="59164-122">到容器的 Windows Server 旧应用程序（“棕色字段”）迁移</span><span class="sxs-lookup"><span data-stu-id="59164-122">Windows Server legacy app ("brown-field") migration to containers</span></span></td>
<td>--</td>
<td><span data-ttu-id="59164-123">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="59164-123">.NET Framework</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="59164-124">基于容器的新开发（“绿色字段”）</span><span class="sxs-lookup"><span data-stu-id="59164-124">New container-based development ("green-field")</span></span></td>
<td><span data-ttu-id="59164-125">.NET Core</span><span class="sxs-lookup"><span data-stu-id="59164-125">.NET Core</span></span></td>
<td><span data-ttu-id="59164-126">.NET Core</span><span class="sxs-lookup"><span data-stu-id="59164-126">.NET Core</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="59164-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="59164-127">ASP.NET Core</span></span></td>
<td><span data-ttu-id="59164-128">.NET Core</span><span class="sxs-lookup"><span data-stu-id="59164-128">.NET Core</span></span></td>
<td><p><span data-ttu-id="59164-129">.NET Core（推荐）</span><span class="sxs-lookup"><span data-stu-id="59164-129">.NET Core (recommended)</span></span></p>
<p><span data-ttu-id="59164-130">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="59164-130">.NET Framework</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="59164-131">ASP.NET 4（MVC 5、Web API 2 和 Web 窗体）</span><span class="sxs-lookup"><span data-stu-id="59164-131">ASP.NET 4 (MVC 5, Web API 2, and Web Forms)</span></span></td>
<td>--</td>
<td><span data-ttu-id="59164-132">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="59164-132">.NET Framework</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="59164-133">SignalR 服务</span><span class="sxs-lookup"><span data-stu-id="59164-133">SignalR services</span></span></td>
<td><span data-ttu-id="59164-134">.NET Core 2.1 或更高版本</span><span class="sxs-lookup"><span data-stu-id="59164-134">.NET Core 2.1 or higher version</span></span></td>
<td><p><span data-ttu-id="59164-135">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="59164-135">.NET Framework</span></span></p>
<p><span data-ttu-id="59164-136">.NET Core 2.1 或更高版本</span><span class="sxs-lookup"><span data-stu-id="59164-136">.NET Core 2.1 or higher version</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="59164-137">WCF、WF 和其他旧框架</span><span class="sxs-lookup"><span data-stu-id="59164-137">WCF, WF, and other legacy frameworks</span></span></td>
<td><span data-ttu-id="59164-138">.NET Core 中的 WCF（仅 WCF 客户端库）</span><span class="sxs-lookup"><span data-stu-id="59164-138">WCF in .NET Core (only the WCF client library)</span></span></td>
<td><p><span data-ttu-id="59164-139">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="59164-139">.NET Framework</span></span></p>
<p><span data-ttu-id="59164-140">.NET Core 中的 WCF（仅 WCF 客户端库）</span><span class="sxs-lookup"><span data-stu-id="59164-140">WCF in .NET Core (only the WCF client library)</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="59164-141">Azure 服务的消耗</span><span class="sxs-lookup"><span data-stu-id="59164-141">Consumption of Azure services</span></span></td>
<td><p><span data-ttu-id="59164-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="59164-142">.NET Core</span></span></p>
<p><span data-ttu-id="59164-143">（最终所有 Azure 服务都将为 .NET Core 提供客户端 SDK）。</span><span class="sxs-lookup"><span data-stu-id="59164-143">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
<td><p><span data-ttu-id="59164-144">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="59164-144">.NET Framework</span></span></p>
<p><span data-ttu-id="59164-145">.NET Core</span><span class="sxs-lookup"><span data-stu-id="59164-145">.NET Core</span></span></p>
<p><span data-ttu-id="59164-146">（最终所有 Azure 服务都将为 .NET Core 提供客户端 SDK）。</span><span class="sxs-lookup"><span data-stu-id="59164-146">(eventually all Azure services will provide client SDKs for .NET Core)</span></span></p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
><span data-ttu-id="59164-147">[上一页](net-framework-container-scenarios.md)
>[下一页](net-container-os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="59164-147">[Previous](net-framework-container-scenarios.md)
[Next](net-container-os-targets.md)</span></span>
