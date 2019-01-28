---
title: dotnet tool uninstall 命令
description: dotnet tool uninstall 命令从你计算机上卸载指定的 .NET Core 全局工具。
ms.date: 05/29/2018
ms.openlocfilehash: 4d53d305131e3399ab5d9c19f9319f3ba3544c19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680918"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="1ef0d-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="1ef0d-103">dotnet tool uninstall</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="1ef0d-104">name</span><span class="sxs-lookup"><span data-stu-id="1ef0d-104">Name</span></span>

<span data-ttu-id="1ef0d-105">`dotnet tool uninstall` - 从你的计算机上卸载指定的 [.NET Core 全局工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="1ef0d-105">`dotnet tool uninstall` - Uninstalls the specified [.NET Core Global Tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1ef0d-106">摘要</span><span class="sxs-lookup"><span data-stu-id="1ef0d-106">Synopsis</span></span>

```console
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="1ef0d-107">说明</span><span class="sxs-lookup"><span data-stu-id="1ef0d-107">Description</span></span>

<span data-ttu-id="1ef0d-108">`dotnet tool uninstall` 为你提供一种从计算机上卸载 .NET Core 全局工具的方法。</span><span class="sxs-lookup"><span data-stu-id="1ef0d-108">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core Global Tools from your machine.</span></span> <span data-ttu-id="1ef0d-109">若要使用此命令，需要使用 `--global` 选项指定要删除用户范围的工具或使用 `--tool-path` 选项指定安装工具的路径。</span><span class="sxs-lookup"><span data-stu-id="1ef0d-109">To use the command, you either have to specify that you want to remove a user-wide tool using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="1ef0d-110">自变量</span><span class="sxs-lookup"><span data-stu-id="1ef0d-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="1ef0d-111">包含要卸载的 .NET Core 全局工具的 NuGet 包的名称/ID。</span><span class="sxs-lookup"><span data-stu-id="1ef0d-111">Name/ID of the NuGet package that contains the .NET Core Global Tool to uninstall.</span></span> <span data-ttu-id="1ef0d-112">你可以使用 [dotnet tool list](dotnet-tool-list.md) 命令查找包名称。</span><span class="sxs-lookup"><span data-stu-id="1ef0d-112">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="1ef0d-113">选项</span><span class="sxs-lookup"><span data-stu-id="1ef0d-113">Options</span></span>

`-g|--global`

<span data-ttu-id="1ef0d-114">指定要从用户范围的安装中删除工具。</span><span class="sxs-lookup"><span data-stu-id="1ef0d-114">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="1ef0d-115">不能与 `--tool-path` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="1ef0d-115">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="1ef0d-116">如果不指定此选项，则必须指定 `--tool-path` 选项。</span><span class="sxs-lookup"><span data-stu-id="1ef0d-116">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="1ef0d-117">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="1ef0d-117">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="1ef0d-118">指定卸载全局工具的位置。</span><span class="sxs-lookup"><span data-stu-id="1ef0d-118">Specifies the location where to uninstall the Global Tool.</span></span> <span data-ttu-id="1ef0d-119">路径可以是绝对的，也可以是相对的。</span><span class="sxs-lookup"><span data-stu-id="1ef0d-119">PATH can be absolute or relative.</span></span> <span data-ttu-id="1ef0d-120">不能与 `--global` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="1ef0d-120">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="1ef0d-121">如果不指定此选项，则必须指定 `--global` 选项。</span><span class="sxs-lookup"><span data-stu-id="1ef0d-121">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="1ef0d-122">示例</span><span class="sxs-lookup"><span data-stu-id="1ef0d-122">Examples</span></span>

<span data-ttu-id="1ef0d-123">卸载 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全局工具：</span><span class="sxs-lookup"><span data-stu-id="1ef0d-123">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool uninstall -g dotnetsay`

<span data-ttu-id="1ef0d-124">从特定 Windows 文件夹卸载 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全局工具：</span><span class="sxs-lookup"><span data-stu-id="1ef0d-124">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Windows folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="1ef0d-125">从特定 Linux/macOS 文件夹卸载 [dotnetsay](https://www.nuget.org/packages/dotnetsay/) 全局工具：</span><span class="sxs-lookup"><span data-stu-id="1ef0d-125">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Linux/macOS folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="1ef0d-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="1ef0d-126">See also</span></span>

- [<span data-ttu-id="1ef0d-127">.NET Core 全局工具</span><span class="sxs-lookup"><span data-stu-id="1ef0d-127">.NET Core Global Tools</span></span>](global-tools.md)
