---
title: dotnet tool list 命令
description: dotnet tool list 命令从计算机中列出指定的 .NET Core 全局工具。
ms.date: 05/29/2018
ms.openlocfilehash: 6d35b1dce0c6d57edb0c6dd5f9711f093bc804aa
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117563"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="01094-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="01094-103">dotnet tool list</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="01094-104">name</span><span class="sxs-lookup"><span data-stu-id="01094-104">Name</span></span>

<span data-ttu-id="01094-105">`dotnet tool list` - 列出当前安装在计算机上的默认目录中或指定路径中的所有 [.NET Core 全局工具](global-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="01094-105">`dotnet tool list` - Lists all [.NET Core Global Tools](global-tools.md) currently installed in the default directory on your machine or in the specified path.</span></span>

## <a name="synopsis"></a><span data-ttu-id="01094-106">摘要</span><span class="sxs-lookup"><span data-stu-id="01094-106">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="01094-107">说明</span><span class="sxs-lookup"><span data-stu-id="01094-107">Description</span></span>

<span data-ttu-id="01094-108">`dotnet tool list` 命令让你可以列出计算机上（当前用户配置文件）或特定路径中安装的所有用户范围的 .NET Core 全局工具。</span><span class="sxs-lookup"><span data-stu-id="01094-108">The `dotnet tool list` command provides a way for you to list all .NET Core Global Tools installed user-wide on your machine (current user profile) or in the specified path.</span></span> <span data-ttu-id="01094-109">此命令列出包名称、安装的版本以及全局工具命令。</span><span class="sxs-lookup"><span data-stu-id="01094-109">The command lists the package name, version installed, and the Global Tool command.</span></span> <span data-ttu-id="01094-110">若要使用此 list 命令，需要使用 `--global` 选项指定要查看所有用户范围的工具或者使用 `--tool-path` 选项指定自定义路径。</span><span class="sxs-lookup"><span data-stu-id="01094-110">To use the list command, you either have to specify that you want to see all user-wide tools using the `--global` option or specify a custom path using the `--tool-path` option.</span></span>

## <a name="options"></a><span data-ttu-id="01094-111">选项</span><span class="sxs-lookup"><span data-stu-id="01094-111">Options</span></span>

`-g|--global`

<span data-ttu-id="01094-112">列出用户范围的全局工具。</span><span class="sxs-lookup"><span data-stu-id="01094-112">Lists user-wide Global Tools.</span></span> <span data-ttu-id="01094-113">不能与 `--tool-path` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="01094-113">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="01094-114">如果不指定此选项，则必须指定 `--tool-path` 选项。</span><span class="sxs-lookup"><span data-stu-id="01094-114">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="01094-115">打印出有关命令的简短帮助。</span><span class="sxs-lookup"><span data-stu-id="01094-115">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="01094-116">指定用于查找全局工具的自定义位置。</span><span class="sxs-lookup"><span data-stu-id="01094-116">Specifies a custom location where to find Global Tools.</span></span> <span data-ttu-id="01094-117">路径可以是绝对的，也可以是相对的。</span><span class="sxs-lookup"><span data-stu-id="01094-117">PATH can be absolute or relative.</span></span> <span data-ttu-id="01094-118">不能与 `--global` 选项一起使用。</span><span class="sxs-lookup"><span data-stu-id="01094-118">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="01094-119">如果不指定此选项，则必须指定 `--global` 选项。</span><span class="sxs-lookup"><span data-stu-id="01094-119">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="01094-120">示例</span><span class="sxs-lookup"><span data-stu-id="01094-120">Examples</span></span>

<span data-ttu-id="01094-121">列出计算机上安装的所有用户范围的全局工具（当前用户配置文件）：</span><span class="sxs-lookup"><span data-stu-id="01094-121">Lists all Global Tools installed user-wide on your machine (current user profile):</span></span>

`dotnet tool list -g`

<span data-ttu-id="01094-122">列出特定 Windows 文件夹中的全局工具：</span><span class="sxs-lookup"><span data-stu-id="01094-122">Lists the Global Tools from a specific Windows folder:</span></span>

`dotnet tool list --tool-path c:\global-tools`

<span data-ttu-id="01094-123">列出特定 Linux/macOS 文件夹中的全局工具：</span><span class="sxs-lookup"><span data-stu-id="01094-123">Lists the Global Tools from a specific Linux/macOS folder:</span></span>

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="01094-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="01094-124">See also</span></span>

- [<span data-ttu-id="01094-125">.NET Core 全局工具</span><span class="sxs-lookup"><span data-stu-id="01094-125">.NET Core Global Tools</span></span>](global-tools.md)
