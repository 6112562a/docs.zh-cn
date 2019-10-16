---
ms.openlocfilehash: 47811d3fab2e4fa531d383dfe818e3cac5613eb3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179990"
---
> [!NOTE]
> <span data-ttu-id="6adf4-101">从 .NET Core 2.0 开始，无需运行 [`dotnet restore`](~/docs/core/tools/dotnet-restore.md)，因为它由所有需要还原的命令隐式运行，如 `dotnet build` 和 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="6adf4-101">Starting with .NET Core 2.0, you don't have to run [`dotnet restore`](~/docs/core/tools/dotnet-restore.md) because it's run implicitly by all commands that require a restore to occur, such as `dotnet build` and `dotnet run`.</span></span> <span data-ttu-id="6adf4-102">在执行显式还原有意义的某些情况下，例如 [Azure DevOps Services 中的持续集成生成](/azure/devops/build-release/apps/aspnet/build-aspnet-core)中，或在需要显式控制还原发生时间的生成系统中，它仍然是有效的命令。</span><span class="sxs-lookup"><span data-stu-id="6adf4-102">It's still a valid command in certain scenarios where doing an explicit restore makes sense, such as [continuous integration builds in Azure DevOps Services](/azure/devops/build-release/apps/aspnet/build-aspnet-core) or in build systems that need to explicitly control the time at which the restore occurs.</span></span>
>
> <span data-ttu-id="6adf4-103">以长格式传递命令时，该命令也支持 `dotnet restore` 选项（例如，`--source`）。</span><span class="sxs-lookup"><span data-stu-id="6adf4-103">This command also supports the `dotnet restore` options when passed in the long form (for example, `--source`).</span></span> <span data-ttu-id="6adf4-104">不支持缩写选项，例如 `-s`。</span><span class="sxs-lookup"><span data-stu-id="6adf4-104">Short form options, such as `-s`, are not supported.</span></span>
