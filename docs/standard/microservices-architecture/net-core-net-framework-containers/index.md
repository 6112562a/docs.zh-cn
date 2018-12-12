---
title: 为 Docker 容器选择 .NET Core 还是 .NET Framework
description: 适用于容器化 .NET 应用程序的 .NET 微服务体系结构 | 为 Docker 容器选择 .NET Core 还是 .NET Framework
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: e71739b06275d4ee786d246004930d7b66fbc72b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151416"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a><span data-ttu-id="386fd-103">为 Docker 容器选择 .NET Core 还是 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="386fd-103">Choosing Between .NET Core and .NET Framework for Docker Containers</span></span>

<span data-ttu-id="386fd-104">通过 .NET 生成服务器端容器化 Docker 应用程序时，有两种支持的框架：[.NET Framework 和 .NET Core](https://www.microsoft.com/net/download)。</span><span class="sxs-lookup"><span data-stu-id="386fd-104">There are two supported frameworks for building server-side containerized Docker applications with .NET: [.NET Framework and .NET Core](https://www.microsoft.com/net/download).</span></span> <span data-ttu-id="386fd-105">这两者共享许多 .NET 平台组件，可在它们之间共享代码。</span><span class="sxs-lookup"><span data-stu-id="386fd-105">They share many .NET platform components, and you can share code across the two.</span></span> <span data-ttu-id="386fd-106">但两者之间存在根本差异，可根据需要实现的目标选择框架。</span><span class="sxs-lookup"><span data-stu-id="386fd-106">However, there are fundamental differences between them, and which framework you use will depend on what you want to accomplish.</span></span> <span data-ttu-id="386fd-107">本节提供有关何时选择各框架的指南。</span><span class="sxs-lookup"><span data-stu-id="386fd-107">This section provides guidance on when to choose each framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="386fd-108">[上一页](../container-docker-introduction/docker-containers-images-registries.md)
>[下一页](general-guidance.md)</span><span class="sxs-lookup"><span data-stu-id="386fd-108">[Previous](../container-docker-introduction/docker-containers-images-registries.md)
[Next](general-guidance.md)</span></span>