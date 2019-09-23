---
title: 如何安装 ML.NET 命令行接口 (CLI) 工具
description: ML.NET 命令行接口 (CLI) 工具的概述和安装。
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: baced9bbcc72153458d42d4b6d8206921bf187b8
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118006"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a><span data-ttu-id="27670-103">如何安装 ML.NET 命令行接口 (CLI) 工具</span><span class="sxs-lookup"><span data-stu-id="27670-103">How to install the ML.NET Command-Line Interface (CLI) tool</span></span>

<span data-ttu-id="27670-104">ML.NET CLI（命令行接口）是可以在任何命令提示符（Windows、Mac 或 Linux）上运行的工具，用于根据提供的训练数据集生成高质量的 ML.NET 模型和源代码。</span><span class="sxs-lookup"><span data-stu-id="27670-104">The ML.NET CLI (command-line interface) is a tool you can run on any command-prompt (Windows, Mac, or Linux) for generating good quality ML.NET models and source code based on training datasets you provide.</span></span>

> [!NOTE]
> <span data-ttu-id="27670-105">本主题涉及目前处于预览状态的 ML.NET CLI 和 ML.NET AutoML，且材料可能会有所变化。</span><span class="sxs-lookup"><span data-stu-id="27670-105">This topic refers to ML.NET CLI and ML.NET AutoML, which are currently in Preview, and material may be subject to change.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="27670-106">先决条件</span><span class="sxs-lookup"><span data-stu-id="27670-106">Pre-requisites</span></span>

- [<span data-ttu-id="27670-107">.NET Core 2.2 SDK</span><span class="sxs-lookup"><span data-stu-id="27670-107">.NET Core 2.2 SDK</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- <span data-ttu-id="27670-108">（可选）[Visual Studio 2017 或 2019](https://visualstudio.microsoft.com/vs/)</span><span class="sxs-lookup"><span data-stu-id="27670-108">(Optional) [Visual Studio 2017 or 2019](https://visualstudio.microsoft.com/vs/)</span></span>

<span data-ttu-id="27670-109">可以使用 Visual Studio F5 或 `dotnet run` (.NET Core CLI) 运行生成的 C# 代码项目。</span><span class="sxs-lookup"><span data-stu-id="27670-109">You can either run the generated C# code projects with Visual Studio F5 or with `dotnet run` (.NET Core CLI).</span></span>

<span data-ttu-id="27670-110">注意：如果在安装 [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) 后，`dotnet tool` 命令不起作用，请从 Windows 注销并再次登录。</span><span class="sxs-lookup"><span data-stu-id="27670-110">Note: If after installing [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) the `dotnet tool` command is not working, sign out from Windows and sign in again.</span></span>

## <a name="install"></a><span data-ttu-id="27670-111">安装</span><span class="sxs-lookup"><span data-stu-id="27670-111">Install</span></span>

<span data-ttu-id="27670-112">ML.NET CLI 的安装方式与任何其他 dotnet 全局工具一样。</span><span class="sxs-lookup"><span data-stu-id="27670-112">The ML.NET CLI is installed like any other dotnet Global Tool.</span></span> <span data-ttu-id="27670-113">使用 `dotnet tool install` .NET Core CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="27670-113">You use the `dotnet tool install` .NET Core CLI command.</span></span> 

<span data-ttu-id="27670-114">以下示例显示如何在默认 NuGet 源位置安装 ML.NET CLI：</span><span class="sxs-lookup"><span data-stu-id="27670-114">The following example shows how to install the ML.NET CLI in the default NuGet feed location:</span></span>

```dotnetcli
dotnet tool install -g mlnet
```

<span data-ttu-id="27670-115">如果无法安装该工具（即，如果它在默认 NuGet 源中不可用），则会显示错误消息。</span><span class="sxs-lookup"><span data-stu-id="27670-115">If the tool can't be installed (that is, if it is not available at the default NuGet feed), error messages are displayed.</span></span> <span data-ttu-id="27670-116">检查所需源是否正在被检查。</span><span class="sxs-lookup"><span data-stu-id="27670-116">Check that the feeds you expected are being checked.</span></span>

<span data-ttu-id="27670-117">如果安装成功，会出现一条消息，显示用于调用工具的命令以及所安装的版本，类似于以下示例：</span><span class="sxs-lookup"><span data-stu-id="27670-117">If installation is successful, a message is displayed showing the command used to call the tool and the version installed, similar to the following example:</span></span>

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

<span data-ttu-id="27670-118">可以通过键入以下命令来确认安装是否成功：</span><span class="sxs-lookup"><span data-stu-id="27670-118">You can confirm the installation was successful by typing the following command:</span></span>

```console
mlnet
```

<span data-ttu-id="27670-119">应该看到 mlnet 工具的可用命令帮助，例如“auto-train”命令。</span><span class="sxs-lookup"><span data-stu-id="27670-119">You should see the help for available commands for the mlnet tool such as the 'auto-train' command.</span></span>

## <a name="install-a-specific-release-version"></a><span data-ttu-id="27670-120">安装特定版本</span><span class="sxs-lookup"><span data-stu-id="27670-120">Install a specific release version</span></span>

<span data-ttu-id="27670-121">如果想安装工具的预发布版本或特定版本，可以采用以下格式指定[框架](../../standard/frameworks.md)：</span><span class="sxs-lookup"><span data-stu-id="27670-121">If you're trying to install a pre-release version or a specific version of the tool, you can specify the [framework](../../standard/frameworks.md) using the following format:</span></span>

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

<span data-ttu-id="27670-122">还可以通过键入以下命令来检查包是否已正确安装：</span><span class="sxs-lookup"><span data-stu-id="27670-122">You can also check if the package is properly installed by typing the following command:</span></span>

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a><span data-ttu-id="27670-123">卸载 CLI 包</span><span class="sxs-lookup"><span data-stu-id="27670-123">Uninstall the CLI package</span></span>

<span data-ttu-id="27670-124">键入以下命令，从本地计算机卸载包：</span><span class="sxs-lookup"><span data-stu-id="27670-124">Type the following command to uninstall the package from your local machine:</span></span>

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a><span data-ttu-id="27670-125">更新 CLI 包</span><span class="sxs-lookup"><span data-stu-id="27670-125">Update the CLI package</span></span>

<span data-ttu-id="27670-126">键入以下命令，从本地计算机更新包：</span><span class="sxs-lookup"><span data-stu-id="27670-126">Type the following command to update the package from your local machine:</span></span>

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a><span data-ttu-id="27670-127">设置 CLI 建议（Tab 自动补全）</span><span class="sxs-lookup"><span data-stu-id="27670-127">Set up CLI suggestions (tab-based auto-completion)</span></span>

<span data-ttu-id="27670-128">由于 ML.NET CLI 基于 `System.CommandLine`，它具有对 Tab 补全的内置支持。</span><span class="sxs-lookup"><span data-stu-id="27670-128">Since the ML.NET CLI is based on `System.CommandLine`, it has built-in support for tab completion.</span></span>

<span data-ttu-id="27670-129">Tab 自动补全工作原理的示例如以下动画所示：</span><span class="sxs-lookup"><span data-stu-id="27670-129">An example of how tab auto completion works is shown in the following animation:</span></span>

![图像](./media/cli-tab-completion.gif)

<span data-ttu-id="27670-131">“Tab 自动补全”（参数建议）适用于 *Windows PowerShell* 和 *macOS/Linux bash*，但它不适用于 *Windows CMD*。</span><span class="sxs-lookup"><span data-stu-id="27670-131">'Tab-based auto-completion' (parameter suggestions) works on *Windows PowerShell* and *macOS/Linux bash* but it won't work on *Windows CMD*.</span></span>

<span data-ttu-id="27670-132">若要启用它，在当前预览版本中，最终用户必须为每个 shell 执行一次相关步骤，如下所述。</span><span class="sxs-lookup"><span data-stu-id="27670-132">To enable it, in the current preview version, the end user has to take a few steps once per shell, outlined below.</span></span> <span data-ttu-id="27670-133">完成此操作后，补全将适用于使用 `System.CommandLine` 编写的所有应用，例如 ML.NET CLI。</span><span class="sxs-lookup"><span data-stu-id="27670-133">Once this is done, completions will work for all apps written using `System.CommandLine` such as the ML.NET CLI.</span></span>

<span data-ttu-id="27670-134">在想要启用补全的计算机上，需要执行两个操作。</span><span class="sxs-lookup"><span data-stu-id="27670-134">On the machine where you'd like to enable completion, you'll need to do two things.</span></span>

1. <span data-ttu-id="27670-135">通过运行以下命令安装 `dotnet-suggest` 全局工具：</span><span class="sxs-lookup"><span data-stu-id="27670-135">Install the `dotnet-suggest` global tool by running the following command:</span></span>

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. <span data-ttu-id="27670-136">将适当的填充码脚本添加到 shell 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="27670-136">Add the appropriate shim script to your shell profile.</span></span> <span data-ttu-id="27670-137">可能必须创建一个 shell 配置文件。</span><span class="sxs-lookup"><span data-stu-id="27670-137">You may have to create a shell profile file.</span></span> <span data-ttu-id="27670-138">填充码脚本会将补全请求从 shell 转发到 `dotnet-suggest` 工具，其会委托到相应的基于 `System.CommandLine` 的应用。</span><span class="sxs-lookup"><span data-stu-id="27670-138">The shim script will forward completion requests from your shell to the `dotnet-suggest` tool, which delegates to the appropriate `System.CommandLine`-based app.</span></span>

    - <span data-ttu-id="27670-139">对于 bash，将 [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) 的内容添加到 `~/.bash_profile`。</span><span class="sxs-lookup"><span data-stu-id="27670-139">For bash, add the contents of [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) to `~/.bash_profile`.</span></span>

    - <span data-ttu-id="27670-140">对于 PowerShell，将 [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) 的内容添加到 PowerShell 配置文件中。</span><span class="sxs-lookup"><span data-stu-id="27670-140">For PowerShell, add the contents of [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) to your PowerShell profile.</span></span> <span data-ttu-id="27670-141">可以通过在控制台中运行以下命令来查找 PowerShell 配置文件的预期路径：</span><span class="sxs-lookup"><span data-stu-id="27670-141">You can find the expected path to your PowerShell profile by running the following command in your console:</span></span>

    ```console
    echo $profile
    ``` 

<span data-ttu-id="27670-142">（对于其他 shell，[查找](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22)或创建[问题](https://github.com/dotnet/System.CommandLine/issues)。）</span><span class="sxs-lookup"><span data-stu-id="27670-142">(For other shells, [look for](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22) or open an [issue](https://github.com/dotnet/System.CommandLine/issues).)</span></span>

## <a name="installation-directory"></a><span data-ttu-id="27670-143">安装目录</span><span class="sxs-lookup"><span data-stu-id="27670-143">Installation directory</span></span>

<span data-ttu-id="27670-144">ML.NET CLI 可安装在默认目录或特定位置。</span><span class="sxs-lookup"><span data-stu-id="27670-144">The ML.NET CLI can be installed in the default directory or in a specific location.</span></span> <span data-ttu-id="27670-145">默认目录为：</span><span class="sxs-lookup"><span data-stu-id="27670-145">The default directories are:</span></span>

| <span data-ttu-id="27670-146">(OS)</span><span class="sxs-lookup"><span data-stu-id="27670-146">OS</span></span>          | <span data-ttu-id="27670-147">路径</span><span class="sxs-lookup"><span data-stu-id="27670-147">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="27670-148">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="27670-148">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="27670-149">Windows</span><span class="sxs-lookup"><span data-stu-id="27670-149">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="27670-150">这些位置在首次运行 SDK 时添加到用户的路径，所以可以直接调用安装在这里的全局工具。</span><span class="sxs-lookup"><span data-stu-id="27670-150">These locations are added to the user's path when the SDK is first run, so Global Tools installed there can be called directly.</span></span>

<span data-ttu-id="27670-151">注意：全局工具特定于用户，而不针对计算机全局。</span><span class="sxs-lookup"><span data-stu-id="27670-151">Note: the Global Tools are user-specific, not machine global.</span></span> <span data-ttu-id="27670-152">特定于用户的意思是无法在一台计算机上安装所有用户都可用的全局工具。</span><span class="sxs-lookup"><span data-stu-id="27670-152">Being user-specific means you cannot install a Global Tool that is available to all users of the machine.</span></span> <span data-ttu-id="27670-153">只有安装了该工具的用户配置文件才能使用它。</span><span class="sxs-lookup"><span data-stu-id="27670-153">The tool is only available for each user profile where the tool was installed.</span></span>

<span data-ttu-id="27670-154">也可在特定目录安装全局工具。</span><span class="sxs-lookup"><span data-stu-id="27670-154">Global Tools can also be installed in a specific directory.</span></span> <span data-ttu-id="27670-155">如果在特定目录安装全局工具，用户必须确保命令是可用的，方法是将该目录添加至路径、使用指定目录调用命令或从特定目录调用该工具。</span><span class="sxs-lookup"><span data-stu-id="27670-155">When installed in a specific directory, the user must ensure the command is available, by including that directory in the path, by calling the command with the directory specified, or calling the tool from within the specified directory.</span></span>
<span data-ttu-id="27670-156">在这种情况下，.NET Core CLI 不将此地址自动添加至 PATH 环境变量。</span><span class="sxs-lookup"><span data-stu-id="27670-156">In this case, the .NET Core CLI doesn't add this location automatically to the PATH environment variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="27670-157">请参阅</span><span class="sxs-lookup"><span data-stu-id="27670-157">See also</span></span>

- [<span data-ttu-id="27670-158">“ML.NET CLI 工具入门”教程</span><span class="sxs-lookup"><span data-stu-id="27670-158">Tutorial on 'Getting Started with ML.NET CLI tool'</span></span>](../tutorials/mlnet-cli.md)
- [<span data-ttu-id="27670-159">如何使用 ML.NET CLI 工具自动训练模型</span><span class="sxs-lookup"><span data-stu-id="27670-159">How to automatically train models with the ML.NET CLI tool</span></span>](../automate-training-with-cli.md)
- [<span data-ttu-id="27670-160">ML.NET CLI auto-train 命令参考指南</span><span class="sxs-lookup"><span data-stu-id="27670-160">ML.NET CLI auto-train command reference guide</span></span>](../reference/ml-net-cli-reference.md) 
- [<span data-ttu-id="27670-161">ML.NET CLI 中的遥测</span><span class="sxs-lookup"><span data-stu-id="27670-161">Telemetry in ML.NET CLI</span></span>](../resources/ml-net-cli-telemetry.md)
