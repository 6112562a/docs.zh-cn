---
title: Docker 应用程序的外部循环 DevOps 工作流步骤
description: 使用 Microsoft 平台和工具的容器化 Docker 应用程序的生命周期
ms.date: 02/15/2019
ms.openlocfilehash: 9fdc5acfd375e4f2266859f061ef1c854286b914
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "68673774"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="3fd17-103">在 Azure DevOps Services 中为容器中的 .NET Core 2.0 应用程序创建 CI/CD 管道并部署到 Kubernetes 群集</span><span class="sxs-lookup"><span data-stu-id="3fd17-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="3fd17-104">在图 5-12 中，可以看到端到端 DevOps 场景，包括代码管理、代码编译、Docker 映像生成、Docker 映像推送到 Docker 注册表并最后部署到 Azure 中的 Kubernetes 群集。</span><span class="sxs-lookup"><span data-stu-id="3fd17-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![工作流程：在开发计算机中启动。](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="3fd17-107">**图 5-12**。</span><span class="sxs-lookup"><span data-stu-id="3fd17-107">**Figure 5-12**.</span></span> <span data-ttu-id="3fd17-108">创建 Docker 映像并将其部署到 Azure 中的 Kubernetes 群集的 CI/CD 场景</span><span class="sxs-lookup"><span data-stu-id="3fd17-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="3fd17-109">请务必注意通过 Docker 注册表（如Docker Hub 或 Azure 容器注册表）连接的生成/CI 和发布/CD 这两个管道。</span><span class="sxs-lookup"><span data-stu-id="3fd17-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="3fd17-110">与不带 Docker 的传统 CI/CD 进程相比，Docker 注册表是主要区别之一。</span><span class="sxs-lookup"><span data-stu-id="3fd17-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="3fd17-111">如图 5-13 所示，第一阶段是生成/CI 管道。</span><span class="sxs-lookup"><span data-stu-id="3fd17-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="3fd17-112">在 Azure DevOps Services 中，可以创建生成/CI 管道，这些管道将编译代码、创建 Docker 映像，并将其推送到 Docker Hub 或 Azure 容器注册表等 Docker 注册表。</span><span class="sxs-lookup"><span data-stu-id="3fd17-112">In Azure DevOps Services you can create build/CI pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Azure DevOps 生成流程任务定义的浏览器视图。](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="3fd17-114">**图 5-13**。</span><span class="sxs-lookup"><span data-stu-id="3fd17-114">**Figure 5-13**.</span></span> <span data-ttu-id="3fd17-115">Azure DevOps 中的生成 Docker 映像并将映像推送到 Docker 注册表的生成/CI 管道</span><span class="sxs-lookup"><span data-stu-id="3fd17-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="3fd17-116">第二个阶段是创建部署/发布管道。</span><span class="sxs-lookup"><span data-stu-id="3fd17-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="3fd17-117">在 Azure DevOps Services 中，可以使用 Azure DevOps Services 的 Kubernetes 任务轻松创建面向 Kubernetes 群集的部署管道（如图 5-14 所示）。</span><span class="sxs-lookup"><span data-stu-id="3fd17-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Azure DevOps 部署到 Kubernetes 任务定义的浏览器视图。](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="3fd17-119">**图 5-14**。</span><span class="sxs-lookup"><span data-stu-id="3fd17-119">**Figure 5-14**.</span></span> <span data-ttu-id="3fd17-120">Azure DevOps 服务中部署到 Kubernetes 群集的发布/CD 管道</span><span class="sxs-lookup"><span data-stu-id="3fd17-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [!Walkthrough]<span data-ttu-id="3fd17-121"> 将 eShopModernized 部署到 Kubernetes：</span><span class="sxs-lookup"><span data-stu-id="3fd17-121"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="3fd17-122">如需了解部署到 Kubernetes 的 Azure DevOps CI/CD 管道的详细演练，请参阅以下帖子：</span><span class="sxs-lookup"><span data-stu-id="3fd17-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: </span></span>\
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="3fd17-123">[上一页](docker-application-outer-loop-devops-workflow.md)
>[下一页](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="3fd17-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
