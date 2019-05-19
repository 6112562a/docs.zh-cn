---
ms.openlocfilehash: 497ac09e5c9a10470d3ae1932d7e3dc114d121dd
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632019"
---
> [!NOTE]
> 从 .NET Core 2.0 开始，无需运行 [`dotnet restore`](~/docs/core/tools/dotnet-restore.md)，因为它由需有还原的所有命令隐式运行，如 `dotnet build` 和 `dotnet run`。 在执行显式还原有意义的某些情况下，例如 [Azure DevOps Services 中的持续集成生成](/azure/devops/build-release/apps/aspnet/build-aspnet-core)中，或在需要显式控制还原发生时间的生成系统中，它仍然是有效的命令。
>
> 以长格式传递命令时，该命令也支持 `dotnet restore` 选项（例如，`--source`）。 不支持缩写选项，例如 `-s`。
