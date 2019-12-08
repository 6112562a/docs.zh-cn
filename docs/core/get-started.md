---
title: .NET Core 入门
description: 查找相关资源，了解如何在 Windows、Linux 和 macOS 上生成 .NET Core 应用程序。
author: thraka
ms.author: adegeo
ms.date: 09/19/2019
ms.openlocfilehash: 89db6d79336c01315983133d9041904d88cba301
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884249"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="c08cf-103">.NET Core 入门</span><span class="sxs-lookup"><span data-stu-id="c08cf-103">Get started with .NET Core</span></span>

<span data-ttu-id="c08cf-104">本文提供 .NET Core 入门的相关信息。</span><span class="sxs-lookup"><span data-stu-id="c08cf-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="c08cf-105">可在 Windows、Linux 和 macOS 上安装 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="c08cf-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="c08cf-106">你可在最喜欢的文本编辑器中编写代码并生成跨平台的库和应用程序。</span><span class="sxs-lookup"><span data-stu-id="c08cf-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span> 

<span data-ttu-id="c08cf-107">如果不确定 .NET Core 是什么或其与其他 .NET 技术的关系，请首先参阅 [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet)（.NET 是什么）概述。</span><span class="sxs-lookup"><span data-stu-id="c08cf-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="c08cf-108">简单地说，.NET Core 是一个跨平台的开放源代码 .NET 实现。</span><span class="sxs-lookup"><span data-stu-id="c08cf-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="c08cf-109">创建应用程序</span><span class="sxs-lookup"><span data-stu-id="c08cf-109">Create an application</span></span>

<span data-ttu-id="c08cf-110">首先，在计算机上下载并安装 [.NET Core SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="c08cf-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="c08cf-111">然后，打开某一终端，如 PowerShell、命令提示符或 Bash    。</span><span class="sxs-lookup"><span data-stu-id="c08cf-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="c08cf-112">键入以下 `dotnet` 命令以创建并运行 C# 应用程序：</span><span class="sxs-lookup"><span data-stu-id="c08cf-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="c08cf-113">您应看到以下输出：</span><span class="sxs-lookup"><span data-stu-id="c08cf-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="c08cf-114">祝贺你！</span><span class="sxs-lookup"><span data-stu-id="c08cf-114">Congratulations!</span></span> <span data-ttu-id="c08cf-115">现已创建了一个简单的 .NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="c08cf-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="c08cf-116">还可以使用 [Visual Studio Code](tutorials/with-visual-studio-code.md)、[Visual Studio](tutorials/with-visual-studio.md)（仅限 Windows）或 [Visual Studio for Mac](tutorials/using-on-mac-vs.md)（仅限 macOS）来创建 .NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="c08cf-116">You can also use [Visual Studio Code](tutorials/with-visual-studio-code.md), [Visual Studio](tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="c08cf-117">教程</span><span class="sxs-lookup"><span data-stu-id="c08cf-117">Tutorials</span></span>

<span data-ttu-id="c08cf-118">可以通过以下分步教程着手开发 .NET Core 应用程序。</span><span class="sxs-lookup"><span data-stu-id="c08cf-118">You can get started developing .NET Core applications by following these step-by-step tutorials.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="c08cf-119">Windows</span><span class="sxs-lookup"><span data-stu-id="c08cf-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="c08cf-120">使用 Visual Studio 2017 生成 C# .NET Core“Hello World”应用程序。</span><span class="sxs-lookup"><span data-stu-id="c08cf-120">Build a C# "Hello World" Application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="c08cf-121">使用 Visual Studio 2017 生成 C# .NET Core 类库。</span><span class="sxs-lookup"><span data-stu-id="c08cf-121">Build a C# class library with .NET Core in Visual Studio 2017.</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="c08cf-122">使用 Visual Studio 2017 生成 Visual Basic .NET Core“Hello World”应用程序。</span><span class="sxs-lookup"><span data-stu-id="c08cf-122">Build a Visual Basic "Hello World" application with .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-with-visual-studio.md)
- [<span data-ttu-id="c08cf-123">使用 Visual Studio 2017 生成 Visual Basic 和 .NET Core 类库。</span><span class="sxs-lookup"><span data-stu-id="c08cf-123">Build a class library with Visual Basic and .NET Core in Visual Studio 2017.</span></span>](./tutorials/vb-library-with-visual-studio.md)  
- <span data-ttu-id="c08cf-124">观看视频，了解[如何安装和使用 Visual Studio Code 和 .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/)。</span><span class="sxs-lookup"><span data-stu-id="c08cf-124">Watch a video on [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/).</span></span>
- <span data-ttu-id="c08cf-125">观看视频，了解[如何安装和使用 Visual Studio 2017 和 .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/)。</span><span class="sxs-lookup"><span data-stu-id="c08cf-125">Watch a video on [how to install and use Visual Studio 2017 and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-Started-NET-Core-Visual-Studio-2017/).</span></span>
- [<span data-ttu-id="c08cf-126">使用命令行实现 .NET Core 入门。</span><span class="sxs-lookup"><span data-stu-id="c08cf-126">Getting started with .NET Core using the command-line.</span></span>](tutorials/cli-create-console-app.md)

<span data-ttu-id="c08cf-127">请参阅 [.NET Core 依赖项和要求](install/dependencies.md?tabs=netcore30&pivots=os-windows)一文，以获取支持的 Windows 版本列表。</span><span class="sxs-lookup"><span data-stu-id="c08cf-127">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="c08cf-128">Linux</span><span class="sxs-lookup"><span data-stu-id="c08cf-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="c08cf-129">可以通过以下分步教程着手开发 .NET Core 应用程序：</span><span class="sxs-lookup"><span data-stu-id="c08cf-129">You can get started developing .NET Core application by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="c08cf-130">使用命令行实现 .NET Core 入门。</span><span class="sxs-lookup"><span data-stu-id="c08cf-130">Getting started with .NET Core using the command-line.</span></span>](tutorials/cli-create-console-app.md)
- <span data-ttu-id="c08cf-131">观看视频：[在 Ubuntu 上使用 C# 和 .NET Core 实现 Visual Studio Code 入门](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)。</span><span class="sxs-lookup"><span data-stu-id="c08cf-131">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span>

<span data-ttu-id="c08cf-132">请参阅 [ 依赖项和要求](install/dependencies.md?tabs=netcore30&pivots=os-linux)一文，以获取支持的 Linux 发行版和版本列表。</span><span class="sxs-lookup"><span data-stu-id="c08cf-132">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="c08cf-133">macOS</span><span class="sxs-lookup"><span data-stu-id="c08cf-133">macOS</span></span>](#tab/macos)

<span data-ttu-id="c08cf-134">可以通过以下分步教程着手开发 .NET Core 应用程序：</span><span class="sxs-lookup"><span data-stu-id="c08cf-134">You can get started developing .NET Core application by following these step-by-step tutorials:</span></span>

- <span data-ttu-id="c08cf-135">观看视频：[在 macOS 上使用 C# 和 .NET Core 实现 Visual Studio Code 入门](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)。</span><span class="sxs-lookup"><span data-stu-id="c08cf-135">Watch a video on [Getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span>
- [<span data-ttu-id="c08cf-136">使用 Visual Studio Code 在 macOS 上实现 .NET Core 入门。</span><span class="sxs-lookup"><span data-stu-id="c08cf-136">Getting started with .NET Core on macOS, using Visual Studio Code.</span></span>](tutorials/using-on-macos.md)
- [<span data-ttu-id="c08cf-137">使用命令行实现 .NET Core 入门。</span><span class="sxs-lookup"><span data-stu-id="c08cf-137">Getting started with .NET Core using the command-line.</span></span>](tutorials/cli-create-console-app.md)
- [<span data-ttu-id="c08cf-138">借助 Visual Studio for Mac 在 macOS 上实现 .NET Core 入门。</span><span class="sxs-lookup"><span data-stu-id="c08cf-138">Getting started with .NET Core on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="c08cf-139">使用 Visual Studio for Mac 在 macOS 上构建完整的 .NET Core 解决方案。</span><span class="sxs-lookup"><span data-stu-id="c08cf-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac.</span></span>](tutorials/using-on-mac-vs-full-solution.md)

<span data-ttu-id="c08cf-140">请参阅 [ 依赖项和要求](install/dependencies.md?tabs=netcore30&pivots=os-macos)一文，以获取支持的 OS X / macOS 版本列表。</span><span class="sxs-lookup"><span data-stu-id="c08cf-140">See the [.NET Core dependencies and requirements](install/dependencies.md?tabs=netcore30&pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
