---
title: Docker 容器、映像和注册表
description: 了解注册表在部署应用程序的 Docker 方式中扮演的关键角色。
ms.date: 02/15/2019
ms.openlocfilehash: 7becadc3de16d96f8d6f167cf49c6cdd3bcc0d32
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673514"
---
# <a name="docker-containers-images-and-registries"></a><span data-ttu-id="20a11-103">Docker 容器、映像和注册表</span><span class="sxs-lookup"><span data-stu-id="20a11-103">Docker containers, images, and registries</span></span>

<span data-ttu-id="20a11-104">使用 Docker 时，你会创建一个应用或服务，并将它及其依赖项打包到一个容器映像中。</span><span class="sxs-lookup"><span data-stu-id="20a11-104">When using Docker, you create an app or service and package it and its dependencies into a container image.</span></span> <span data-ttu-id="20a11-105">映像是应用或服务及其配置和依赖项的静态表示形式。</span><span class="sxs-lookup"><span data-stu-id="20a11-105">An image is a static representation of the app or service and its configuration and dependencies.</span></span>

<span data-ttu-id="20a11-106">若要运行应用或服务，应用的映像会实例化，以创建一个在 Docker 主机上运行的容器。</span><span class="sxs-lookup"><span data-stu-id="20a11-106">To run the app or service, the app's image is instantiated to create a container, which will be running on the Docker host.</span></span> <span data-ttu-id="20a11-107">最初，会在开发环境或 PC 中测试容器。</span><span class="sxs-lookup"><span data-stu-id="20a11-107">Containers are initially tested in a development environment or PC.</span></span>

<span data-ttu-id="20a11-108">将映像存储在注册表中，该注册表充当映像库。</span><span class="sxs-lookup"><span data-stu-id="20a11-108">You store images in a registry, that acts as a library of images.</span></span> <span data-ttu-id="20a11-109">部署到生产业务流程协调程序时需要一个注册表。</span><span class="sxs-lookup"><span data-stu-id="20a11-109">You need a registry when deploying to production orchestrators.</span></span> <span data-ttu-id="20a11-110">Docker 通过 [Docker Hub](https://hub.docker.com/)维护一个公共注册表；其他供应商为不同映像集合提供注册表，包括 [Azure 容器注册表](https://azure.microsoft.com/services/container-registry/)。</span><span class="sxs-lookup"><span data-stu-id="20a11-110">Docker maintains a public registry via [Docker Hub](https://hub.docker.com/); other vendors provide registries for different collections of images, including [Azure Container Registry](https://azure.microsoft.com/services/container-registry/).</span></span> <span data-ttu-id="20a11-111">或者，企业可本地拥有一个专用注册表，用于其 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="20a11-111">Alternatively, enterprises can have a private registry on-premises for their own Docker images.</span></span>

<span data-ttu-id="20a11-112">图 1-4 显示了 Docker 中的映像和注册表与其他组件相关联的方式。</span><span class="sxs-lookup"><span data-stu-id="20a11-112">Figure 1-4 shows how images and registries in Docker relate to other components.</span></span> <span data-ttu-id="20a11-113">还显示了供应商推出的多种注册表产品/服务。</span><span class="sxs-lookup"><span data-stu-id="20a11-113">It also shows the multiple registry offerings from vendors.</span></span>

![Docker 中的基本分类：注册表如同用于存储映像的书架，可被拉取以生成容器，从而运行服务或 Web 应用。](./media/image4.png)

<span data-ttu-id="20a11-118">**图 1-4**。</span><span class="sxs-lookup"><span data-stu-id="20a11-118">**Figure 1-4**.</span></span> <span data-ttu-id="20a11-119">Docker 术语和概念的分类</span><span class="sxs-lookup"><span data-stu-id="20a11-119">Taxonomy of Docker terms and concepts</span></span>

<span data-ttu-id="20a11-120">通过将映射放在注册表中，可在框架级别存储静态和不可变的应用程序，包括其所有依赖项。</span><span class="sxs-lookup"><span data-stu-id="20a11-120">By putting images in a registry, you can store static and immutable application bits, including all of their dependencies, at a framework level.</span></span> <span data-ttu-id="20a11-121">然后，可以在多个环境中对映像进行版本和部署，从而提供一致的部署单元。</span><span class="sxs-lookup"><span data-stu-id="20a11-121">You then can version and deploy images in multiple environments and thus provide a consistent deployment unit.</span></span>

<span data-ttu-id="20a11-122">无论是托管在本地还是托管在云中，在下列情况下都建议使用私有映像注册表：</span><span class="sxs-lookup"><span data-stu-id="20a11-122">Private image registries, either hosted on-premises or in the cloud, are recommended when:</span></span>

- <span data-ttu-id="20a11-123">由于保密性，映像不能被公开分享。</span><span class="sxs-lookup"><span data-stu-id="20a11-123">Your images must not be shared publicly due to confidentiality.</span></span>

- <span data-ttu-id="20a11-124">希望映像和所选部署环境之间的网络延迟保持在最低水平。</span><span class="sxs-lookup"><span data-stu-id="20a11-124">You want to have minimum network latency between your images and your chosen deployment environment.</span></span> <span data-ttu-id="20a11-125">例如，如果生产环境是 Azure，则可能想将映像存储在 [Azure 容器注册表](https://azure.microsoft.com/services/container-registry/)中，以便最小化网络延迟。</span><span class="sxs-lookup"><span data-stu-id="20a11-125">For example, if your production environment is Azure, you probably want to store your images in [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) so that network latency is minimal.</span></span> <span data-ttu-id="20a11-126">同样，如果生产环境是在本地，则需要在同一本地网络中使用本地的 Docker 信任的注册表。</span><span class="sxs-lookup"><span data-stu-id="20a11-126">In a similar way, if your production environment is on-premises, you might want to have an on-premises Docker Trusted Registry available within the same local network.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="20a11-127">[上一页](docker-terminology.md)
>[下一页](road-to-modern-applications-based-on-containers.md)</span><span class="sxs-lookup"><span data-stu-id="20a11-127">[Previous](docker-terminology.md)
[Next](road-to-modern-applications-based-on-containers.md)</span></span>
