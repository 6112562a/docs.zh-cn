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
# <a name="docker-containers-images-and-registries"></a>Docker 容器、映像和注册表

使用 Docker 时，你会创建一个应用或服务，并将它及其依赖项打包到一个容器映像中。 映像是应用或服务及其配置和依赖项的静态表示形式。

若要运行应用或服务，应用的映像会实例化，以创建一个在 Docker 主机上运行的容器。 最初，会在开发环境或 PC 中测试容器。

将映像存储在注册表中，该注册表充当映像库。 部署到生产业务流程协调程序时需要一个注册表。 Docker 通过 [Docker Hub](https://hub.docker.com/)维护一个公共注册表；其他供应商为不同映像集合提供注册表，包括 [Azure 容器注册表](https://azure.microsoft.com/services/container-registry/)。 或者，企业可本地拥有一个专用注册表，用于其 Docker 映像。

图 1-4 显示了 Docker 中的映像和注册表与其他组件相关联的方式。 还显示了供应商推出的多种注册表产品/服务。

![Docker 中的基本分类：注册表如同用于存储映像的书架，可被拉取以生成容器，从而运行服务或 Web 应用。 本地和公有云上均有专用 Docker 注册表。 Docker 中心是由 Docker 维护的公共注册表，除了 Docker 信任的注册表（企业级解决方案），Azure 还提供了 Azure 容器注册表。 AWS、Google 和其他产品也有容器注册表。](./media/image4.png)

**图 1-4**。 Docker 术语和概念的分类

通过将映射放在注册表中，可在框架级别存储静态和不可变的应用程序，包括其所有依赖项。 然后，可以在多个环境中对映像进行版本和部署，从而提供一致的部署单元。

无论是托管在本地还是托管在云中，在下列情况下都建议使用私有映像注册表：

- 由于保密性，映像不能被公开分享。

- 希望映像和所选部署环境之间的网络延迟保持在最低水平。 例如，如果生产环境是 Azure，则可能想将映像存储在 [Azure 容器注册表](https://azure.microsoft.com/services/container-registry/)中，以便最小化网络延迟。 同样，如果生产环境是在本地，则需要在同一本地网络中使用本地的 Docker 信任的注册表。

>[!div class="step-by-step"]
>[上一页](docker-terminology.md)
>[下一页](road-to-modern-applications-based-on-containers.md)
