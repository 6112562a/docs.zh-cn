---
title: 有关适用于容器化应用的 Microsoft 平台和工具的简介
description: 初步了解 Microsoft 的产品/服务以支持 Docker 应用程序生命周期。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 0e883041624f99d51b49994f02f3a42fc945a96d
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219576"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Microsoft 平台和工具容器化应用简介


图 3-1 显示 Docker 应用的生命周期的主要支柱，这些应用根据多个团队（应用开发、DevOps 基础结构流程和 IT 管理和运营）交付的工作类型分类。 通常，在企业中，负责每个方面的“角色”的个人资料是不同的。 其技能也是如此。

![](./media/image1.png)

图 3-1:使用 Microsoft 平台和工具容器化 Docker 应用程序生命周期中的主要支柱

容器化 Docker 生命周期工作流最初可基于“默认产品选择”具有规定性，以便开发人员快速入门，但从根本上说，必须具有一个开放框架，使其成为可适应每个组织或企业中不同上下文的灵活工作流。 工作流基础结构（组件和产品）必须足够灵活，覆盖每个公司未来会拥有的环境，甚至能够与其他人交换开发或 DevOps 产品。 正如以下章节所述，平台和基础结构的灵活性、开放性和广泛的技术选择正是 Microsoft 对于容器化 Docker 应用程序最重视的几个方面。

表 3-1 显示了适用于容器化 Docker 应用程序的 Microsoft DevOps 的目的，即提供开放式 DevOps 工作流，使用户可选择要用于每个阶段（Microsoft 或第三方）的产品，同时提供具有已互联的“默认产品”的简化工作流，从而使用户可快速使用适用于 Docker 应用的企业级 DevOps 工作流。

表 3-1:任何技术的开放式 DevOps 工作流

| Host | Microsoft 技术 | 第三方 - Azure 可插入 |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Docker 应用平台   | • Microsoft Visual Studio 和 Visual Studio Code<br /> • .NET<br /> • Microsoft Azure 容器服务<br /> • Azure Service Fabric<br /> • Azure 容器注册表<br /> | •任何代码编辑器（如 Sublime）<br /> •任何语言（Node.js、Java、 Go 等）<br /> •任何业务流程协调程序和计划程序<br /> •任何 Docker 注册表<br /> |
| Docker 应用的 DevOps     | • Azure DevOps 服务<br /> • Microsoft Team Foundation Server<br /> • Azure 容器服务<br /> • Azure Service Fabric<br /> | • GitHub、Git、Subversion 等<br /> • Jenkins、Chef、Puppet、Velocity、CircleCI、TravisCI 等<br /> •本地 Docker 数据中心、Docker Swarm、Mesos DC/OS、Kubernetes 等<br /> |
| 管理与监视  | • 操作管理套件<br /> • Applications Insights<br /> | • Marathon、 Chronos 等<br />

如表 3-1 所定义，适用于容器化 Docker 应用的 Microsoft 平台和工具包含以下组件：

-   **适用于 Docker 应用开发的平台** 构建“应用”的一个服务或服务集合的开发。 开发平台提供将代码推送到共享代码存储库前，开发人员所需的所有工作。 开发部署为容器的服务与开发不具有 Docker 的相同应用或服务非常相似。 继续使用你的首选的语言 （.NET、 Node.js、 Go 等） 和偏好的编辑器或 Visual Studio 或 Visual Studio Code 等 IDE。 但是，请不要将 Docker 视为部署目标，你是在 Docker 环境中开发服务。 可以在本地生成、运行、测试和调试容器中的代码，以在开发时提供目标环境。 通过本地提供目标环境，Docker 容器可通过设置大幅度改善 DevOps 生命周期。 Visual Studio 和 Visual Studio Code 具有可在开发过程中集成 Docker 容器的扩展。

-   **Docker 应用的 DevOps**创建 Docker 应用程序的开发人员可以使用 Azure DevOps 服务或任何其他第三方产品，如 Jenkins，若要构建综合自动应用程序生命周期管理 (ALM)。

使用 Azure DevOps 服务，开发人员可以创建容器为重点 DevOps 快速、 迭代的过程涵盖源代码控制从任何位置 （Azure DevOps 服务-Git、 GitHub、 任何远程 Git 存储库或 Subversion） 持续集成 (CI)内部单元测试，间容器/服务集成测试、 持续交付 (CD) 和版本管理 (RM)。 开发人员还能将其 Docker 应用程序版本自动化到 Azure 容器服务中，从开发到暂存和生产环境。
 
-   IT 生产管理和监视。

**管理** IT 可以在几个方面管理生产应用程序和服务：

-   **Azure 门户**  如果使用开放源业务流程协调程序，Azure 容器服务 (ACS) 以及 Docker 数据中心和 Mesosphere Marathon 等群集管理工具有助于设置和维护 Docker 环境。 如果使用 Azure Service Fabric，Service Fabric Explorer 工具可让用户可视化和配置群集。

-   **Docker 工具**  可以使用熟悉的工具管理容器应用程序。 无需更改现有 Docker 管理做法，即可将容器工作负载移动到云。 针对所选的业务流程协调程序，使用熟悉的应用程序管理工具并通过标准 API 终结点连接。 还可以使用其他第三方工具管理 Docker 应用程序，如 Docker 数据中心或 CLI Docker 工具。

-   **开放源工具**  因为 ACS 公开了业务流程引擎的标准 API 终结点，所以 ACS 可与热门工具兼容，并且在大多数情况下，这些工具是现成可用的，包括可视化工具、监视、命令行工具和未来工具（可用时）。

**监视** 运行产品环境时，可以使用以下项监视各个方面：

-   **Operations Management Suite (OMS)** “OMS 容器解决方案”可以管理和监视 Docker 主机和容器，方法是显示以下信息：容器和容器主机的位置、哪些容器正在运行或发生故障、Docker 守护程序和容器日志。 它还显示容器和主机的性能指标，如 CPU、内存、网络和存储，帮助排除故障和找到具有干扰性的相邻容器。

-   **Application Insights** 通过将 SDK 设置到服务中以便获取来自该应用程序的遥测数据，可监视生产 Docker 应用程序。

因此，Microsoft 为端到端容器化 Docker 应用程序生命周期提供了完整的基础。 但是，它是产品和技术的集合，使用户可选择并集成现有工具和流程。 凭借大量方法的灵活性和功能深度优势，Microsoft 在容器化 Docker 应用程序开发领域占据有力地位。

>[!div class="step-by-step"]
>[上一页](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[下一页](../design-develop-containerized-apps/index.md)