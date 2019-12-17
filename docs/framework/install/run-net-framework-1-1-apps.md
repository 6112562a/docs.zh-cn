---
title: 在 Windows 8、Windows 8.1 或 Windows 10 上运行 .NET Framework 1.1 应用
ms.date: 05/26/2017
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1364eebf4d94a117a3ee7f0912b6ff4090e93853
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960034"
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a><span data-ttu-id="6eb1d-102">在 Windows 8、Windows 8.1 或 Windows 10 上运行 .NET Framework 1.1 应用</span><span class="sxs-lookup"><span data-stu-id="6eb1d-102">Run .NET Framework 1.1 apps on Windows 8, Windows 8.1, or Windows 10</span></span>

<span data-ttu-id="6eb1d-103">Windows 8、Windows 8.1、Windows Server 2012、[!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] 或 Windows 10 操作系统上不支持 .NET Framework 1.1。</span><span class="sxs-lookup"><span data-stu-id="6eb1d-103">The .NET Framework 1.1 is not supported on the Windows 8, Windows 8.1, Windows Server 2012, [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], or the Windows 10 operating systems.</span></span> <span data-ttu-id="6eb1d-104">在某些情况下，.NET Framework 1.1 专门标识为是运行应用所必需的。</span><span class="sxs-lookup"><span data-stu-id="6eb1d-104">In some cases, the .NET Framework 1.1 is specifically identified as required for an app to run.</span></span> <span data-ttu-id="6eb1d-105">在这些情况下，应联系独立软件供应商 (ISV) 以升级该应用，使其可在 .NET Framework 3.5 SP1 或更高版本上运行。</span><span class="sxs-lookup"><span data-stu-id="6eb1d-105">In those cases, you should contact your independent software vendor (ISV) to have the app upgraded to run on the .NET Framework 3.5 SP1 or later version.</span></span> <span data-ttu-id="6eb1d-106">有关其他信息，请参阅[从 .NET Framework 1.1 迁移](../migration-guide/migrating-from-the-net-framework-1-1.md)。</span><span class="sxs-lookup"><span data-stu-id="6eb1d-106">For additional information, see [Migrating from the .NET Framework 1.1](../migration-guide/migrating-from-the-net-framework-1-1.md).</span></span>

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a><span data-ttu-id="6eb1d-107">从 CD 或下载中心安装 .NET Framework 1.1</span><span class="sxs-lookup"><span data-stu-id="6eb1d-107">Install the .NET Framework 1.1 from a CD or Download Center</span></span>

<span data-ttu-id="6eb1d-108">在 Windows 8、Windows 8.1、Windows Server 2012、[!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)] 或 Windows 10 上无法手动安装 .NET Framework 1.1。</span><span class="sxs-lookup"><span data-stu-id="6eb1d-108">It isn't possible to manually install the .NET Framework 1.1 on Windows 8, Windows 8.1, Windows Server 2012, [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], or Windows 10.</span></span> <span data-ttu-id="6eb1d-109">它不再受支持。</span><span class="sxs-lookup"><span data-stu-id="6eb1d-109">It is no longer supported.</span></span> <span data-ttu-id="6eb1d-110">如果尝试安装包，会显示以下错误消息：“无法继续执行安装程序，因为此版本的 .NET Framework 与以前安装的某个版本不兼容。”</span><span class="sxs-lookup"><span data-stu-id="6eb1d-110">If you try to install the package, the following error message is displayed: "Setup cannot continue because this version of the .NET Framework is incompatible with a previously installed one."</span></span> <span data-ttu-id="6eb1d-111">若要解决此问题，请安装 [.NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22)。</span><span class="sxs-lookup"><span data-stu-id="6eb1d-111">To solve this problem, install the [.NET Framework 3.5 SP1](https://www.microsoft.com/download/details.aspx?id=22).</span></span> <span data-ttu-id="6eb1d-112">此版本包括 .NET Framework 2.0（.NET Framework 1.1 之后的版本），Windows 8、Windows 8.1 和 Windows 10 上支持此版本。</span><span class="sxs-lookup"><span data-stu-id="6eb1d-112">This version includes the .NET Framework 2.0 (the release that follows the .NET Framework 1.1), which is supported on Windows 8, Windows 8.1, and Windows 10.</span></span> <span data-ttu-id="6eb1d-113">首先，应始终尝试安装该应用，确定其是否会自动更新到 .NET Framework 的更高版本。</span><span class="sxs-lookup"><span data-stu-id="6eb1d-113">You should always try to install the app first to determine if it will automatically be updated to a later version of the .NET Framework.</span></span> <span data-ttu-id="6eb1d-114">如果不会，请联系 ISV 获取应用更新。</span><span class="sxs-lookup"><span data-stu-id="6eb1d-114">If it does not, contact your ISV for an app update.</span></span>

## <a name="see-also"></a><span data-ttu-id="6eb1d-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="6eb1d-115">See also</span></span>

- [<span data-ttu-id="6eb1d-116">从 .NET Framework 1.1 迁移</span><span class="sxs-lookup"><span data-stu-id="6eb1d-116">Migrating from the .NET Framework 1.1</span></span>](../migration-guide/migrating-from-the-net-framework-1-1.md)
- [<span data-ttu-id="6eb1d-117">在 Windows 10、Windows 8.1 和 Windows 8 上安装 .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="6eb1d-117">Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8</span></span>](dotnet-35-windows-10.md)
