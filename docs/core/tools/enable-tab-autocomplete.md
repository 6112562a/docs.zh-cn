---
title: 启用 tab 自动补全
description: 本文介绍如何针对适用于 PowerShell、Bash 和 zsh 的 .NET Core CLI 启用 tab 自动补全。
author: thraka
ms.author: adegeo
ms.date: 11/03/2019
ms.openlocfilehash: 8c5d6a254db5ba21417ba45122ed0d7cb093c7c3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739309"
---
# <a name="how-to-enable-tab-completion-for-net-core-cli"></a><span data-ttu-id="2451a-103">如何为 .NET Core CLI 启用 TAB 自动补全功能</span><span class="sxs-lookup"><span data-stu-id="2451a-103">How to enable TAB completion for .NET Core CLI</span></span>

<span data-ttu-id="2451a-104">从.NET Core 2.0 SDK 开始，NET Core CLI 支持 tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="2451a-104">Starting with .NET Core 2.0 SDK, the .NET Core CLI supports tab completion.</span></span> <span data-ttu-id="2451a-105">本文介绍如何为三个 shell、PowerShell、Bash 和 zsh 配置 tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="2451a-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="2451a-106">其他 shell 可能支持自动补全功能。</span><span class="sxs-lookup"><span data-stu-id="2451a-106">Other shells may have support for auto completion.</span></span> <span data-ttu-id="2451a-107">请参阅有关如何配置自动补全功能的文档，这些步骤应与本文中介绍的步骤类似。</span><span class="sxs-lookup"><span data-stu-id="2451a-107">Refer to their documentation on how to configure auto completion, the steps should be similar to the steps described in this article.</span></span>

[!INCLUDE [topic-appliesto-net-core-2plus](~/includes/topic-appliesto-net-core-2plus.md)]

<span data-ttu-id="2451a-108">设置完成后，通过在 shell 中键入 `dotnet` 命令，然后按下 TAB 键来触发 .NET Core CLI 的 tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="2451a-108">Once setup, tab completion for the .NET Core CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="2451a-109">当前命令行将发送到 `dotnet complete` 命令，结果将由 shell 处理。</span><span class="sxs-lookup"><span data-stu-id="2451a-109">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="2451a-110">可以通过直接向 `dotnet complete` 命令发送内容来测试结果而无需启用 tab 自动补全。</span><span class="sxs-lookup"><span data-stu-id="2451a-110">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="2451a-111">例如:</span><span class="sxs-lookup"><span data-stu-id="2451a-111">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="2451a-112">如果该命令不起作用，请确保已安装 .NET Core 2.0 SDK 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="2451a-112">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="2451a-113">如果已安装，但该命令仍不起作用，请确保 `dotnet` 命令解析为 .NET Core 2.0 SDK 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="2451a-113">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="2451a-114">使用 `dotnet --version` 命令查看当前路径解析为的 `dotnet` 的版本。</span><span class="sxs-lookup"><span data-stu-id="2451a-114">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="2451a-115">有关详细信息，请参阅[选择要使用的 .NET Core 版本](../versions/selection.md)页面。</span><span class="sxs-lookup"><span data-stu-id="2451a-115">For more information, see [Select the .NET Core version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="2451a-116">示例</span><span class="sxs-lookup"><span data-stu-id="2451a-116">Examples</span></span>

<span data-ttu-id="2451a-117">下面是 tab 自动补全提供的一些示例：</span><span class="sxs-lookup"><span data-stu-id="2451a-117">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="2451a-118">输入</span><span class="sxs-lookup"><span data-stu-id="2451a-118">Input</span></span>                                | <span data-ttu-id="2451a-119">将变为</span><span class="sxs-lookup"><span data-stu-id="2451a-119">becomes</span></span>                                                                     | <span data-ttu-id="2451a-120">因为</span><span class="sxs-lookup"><span data-stu-id="2451a-120">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="2451a-121">`add` 是第一项子命令，按字母排序。</span><span class="sxs-lookup"><span data-stu-id="2451a-121">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="2451a-122">Tab 自动补全匹配子字符串，`--help` 首先按字母顺序排列。</span><span class="sxs-lookup"><span data-stu-id="2451a-122">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="2451a-123">第二次按 Tab 将显示下一条建议。</span><span class="sxs-lookup"><span data-stu-id="2451a-123">Pressing tab a second time brings up the next suggestion.</span></span>      
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="2451a-124">结果按字母顺序返回。</span><span class="sxs-lookup"><span data-stu-id="2451a-124">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="2451a-125">Tab 自动补全是可识别的项目文件。</span><span class="sxs-lookup"><span data-stu-id="2451a-125">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="2451a-126">PowerShell</span><span class="sxs-lookup"><span data-stu-id="2451a-126">PowerShell</span></span>

<span data-ttu-id="2451a-127">要将 tab 自动补全添加到适用于 .NET Core CLI 的 PowerShell，请创建或编辑存储在变量 `$PROFILE` 中的配置文件  。</span><span class="sxs-lookup"><span data-stu-id="2451a-127">To add tab completion to **PowerShell** for the .NET Core CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="2451a-128">有关详细信息，请参阅[如何创建配置文件](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile)和[配置文件和执行策略](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy)。</span><span class="sxs-lookup"><span data-stu-id="2451a-128">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span> 

<span data-ttu-id="2451a-129">将以下代码添加到配置文件中：</span><span class="sxs-lookup"><span data-stu-id="2451a-129">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI 
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="2451a-130">bash</span><span class="sxs-lookup"><span data-stu-id="2451a-130">bash</span></span>

<span data-ttu-id="2451a-131">要将 tab 自动补全添加到适用于 .NET Core CLI 的 bash shell，请将以下代码添加到 `.bashrc` 文件： </span><span class="sxs-lookup"><span data-stu-id="2451a-131">To add tab completion to your **bash** shell for the .NET Core CLI, add the following code to your `.bashrc` file:</span></span>

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)"
  if [ $? -ne 0 ]; then
    completions=""
  fi

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a><span data-ttu-id="2451a-132">zsh</span><span class="sxs-lookup"><span data-stu-id="2451a-132">zsh</span></span>

<span data-ttu-id="2451a-133">要将 tab 自动补全添加到适用于 .NET Core CLI 的 zsh shell，请将以下代码添加到 `.zshrc` 文件： </span><span class="sxs-lookup"><span data-stu-id="2451a-133">To add tab completion to your **zsh** shell for the .NET Core CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete() 
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
