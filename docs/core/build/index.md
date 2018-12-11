---
title: 从源生成 .NET Core
description: 了解如何从源代码生成 .NET Core 和 .NET Core CLI。
author: bleroy
ms.date: 06/28/2017
ms.custom: seodec18
ms.openlocfilehash: 036d7fb64d74c00b4ac0e3d34bacc834f3c3a198
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170062"
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="97d5f-103">从源生成 .NET Core</span><span class="sxs-lookup"><span data-stu-id="97d5f-103">Build .NET Core from source</span></span>

<span data-ttu-id="97d5f-104">能从 .NET Core 的源代码生成它在多个方面都体现出其重要性：能更轻松地将 .NET Core 移植到新平台；可实现对产品做出贡献和修复；并支持创建自定义版本的 .NET。</span><span class="sxs-lookup"><span data-stu-id="97d5f-104">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="97d5f-105">本文为想生成和分发自己的 .NET Core 版本的开发人员提供指导。</span><span class="sxs-lookup"><span data-stu-id="97d5f-105">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="97d5f-106">从源生成 CLR</span><span class="sxs-lookup"><span data-stu-id="97d5f-106">Build the CLR from source</span></span>

<span data-ttu-id="97d5f-107">有关 .NET CoreCLR 的源代码，可以访问 GitHub 上的 [dotnet/coreclr](https://github.com/dotnet/coreclr/) 存储库。</span><span class="sxs-lookup"><span data-stu-id="97d5f-107">The source code for the .NET CoreCLR can be found in the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository on GitHub.</span></span>

<span data-ttu-id="97d5f-108">生成目前依赖于以下系统必备组件：</span><span class="sxs-lookup"><span data-stu-id="97d5f-108">The build currently depends on the following prerequisites:</span></span>

* [<span data-ttu-id="97d5f-109">Git</span><span class="sxs-lookup"><span data-stu-id="97d5f-109">Git</span></span>](https://git-scm.com/)
* [<span data-ttu-id="97d5f-110">CMake</span><span class="sxs-lookup"><span data-stu-id="97d5f-110">CMake</span></span>](https://cmake.org/)
* [<span data-ttu-id="97d5f-111">Python</span><span class="sxs-lookup"><span data-stu-id="97d5f-111">Python</span></span>](https://www.python.org/)
* <span data-ttu-id="97d5f-112">C++ 编译器。</span><span class="sxs-lookup"><span data-stu-id="97d5f-112">a C++ compiler.</span></span>

<span data-ttu-id="97d5f-113">安装完这些必备组件后，可以 [dotnet/coreclr](https://github.com/dotnet/coreclr/) 存储库为基础，调用生成脚本（Windows 中的 `build.cmd`，或 Linux 和 macOS 中的 `build.sh`）生成 CLR。</span><span class="sxs-lookup"><span data-stu-id="97d5f-113">After you've installed these prerequisites, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/coreclr](https://github.com/dotnet/coreclr/) repository.</span></span>

<span data-ttu-id="97d5f-114">组件的安装因操作系统 (OS) 而异。</span><span class="sxs-lookup"><span data-stu-id="97d5f-114">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="97d5f-115">请参阅特定 OS 的生成说明：</span><span class="sxs-lookup"><span data-stu-id="97d5f-115">See the build instructions for your specific OS:</span></span>

* [<span data-ttu-id="97d5f-116">Windows</span><span class="sxs-lookup"><span data-stu-id="97d5f-116">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
* [<span data-ttu-id="97d5f-117">Linux</span><span class="sxs-lookup"><span data-stu-id="97d5f-117">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
* [<span data-ttu-id="97d5f-118">macOS</span><span class="sxs-lookup"><span data-stu-id="97d5f-118">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
* [<span data-ttu-id="97d5f-119">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="97d5f-119">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
* [<span data-ttu-id="97d5f-120">NetBSD</span><span class="sxs-lookup"><span data-stu-id="97d5f-120">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="97d5f-121">不能跨 OS 进行交叉生成（仅适用于基于 X64 的 ARM）。</span><span class="sxs-lookup"><span data-stu-id="97d5f-121">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="97d5f-122">必须在特定的平台上生成该平台。</span><span class="sxs-lookup"><span data-stu-id="97d5f-122">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="97d5f-123">生成具有两个主要的 `buildTypes`：</span><span class="sxs-lookup"><span data-stu-id="97d5f-123">The build has two main `buildTypes`:</span></span>

* <span data-ttu-id="97d5f-124">调试（默认）- 以最低优化水平编译运行时并进行额外的运行时检查（断言）。</span><span class="sxs-lookup"><span data-stu-id="97d5f-124">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="97d5f-125">这种优化级别的降低和额外的检查会减慢运行时的执行速度，但对于调试来说是很有价值的。</span><span class="sxs-lookup"><span data-stu-id="97d5f-125">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="97d5f-126">这是开发和测试环境的推荐设置。</span><span class="sxs-lookup"><span data-stu-id="97d5f-126">This is the recommended setting for development and testing environments.</span></span>
* <span data-ttu-id="97d5f-127">发布 - 以完全优化水平编译运行时，无需进行额外的运行时检查。</span><span class="sxs-lookup"><span data-stu-id="97d5f-127">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="97d5f-128">这将产生更快的运行时性能，但需要更长时间进行生成，并且难以进行调试。</span><span class="sxs-lookup"><span data-stu-id="97d5f-128">This will yield much faster run time performance but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="97d5f-129">将 `release` 传递给生成脚本以选择此生成类型。</span><span class="sxs-lookup"><span data-stu-id="97d5f-129">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="97d5f-130">此外，默认情况下，生成不仅会创建运行时可执行文件，还会生成所有测试。</span><span class="sxs-lookup"><span data-stu-id="97d5f-130">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="97d5f-131">这其中有不少测试都需花费大量时间，但如果只想试验一下更改，则不必执行此操作。</span><span class="sxs-lookup"><span data-stu-id="97d5f-131">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="97d5f-132">可以通过向生成脚本添加 `skiptests` 参数来跳过测试生成，如下例所示（在 Unix 计算机上将 `.\build` 替换为 `./build.sh`）：</span><span class="sxs-lookup"><span data-stu-id="97d5f-132">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests
```

<span data-ttu-id="97d5f-133">之前的示例演示了如何生成 `Debug` 风格，该风格启用了开发时间检查（断言）并禁用优化。</span><span class="sxs-lookup"><span data-stu-id="97d5f-133">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="97d5f-134">若要生成发布（全速）风格，请执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="97d5f-134">To build the release (full speed) flavor, do the following:</span></span>

```bat
    .\build release skiptests
```

<span data-ttu-id="97d5f-135">可使用 -? 或 -help 限定符找到</span><span class="sxs-lookup"><span data-stu-id="97d5f-135">You can find more build options with build by using the -?</span></span> <span data-ttu-id="97d5f-136">更多生成选项。</span><span class="sxs-lookup"><span data-stu-id="97d5f-136">or -help qualifier.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="97d5f-137">使用生成</span><span class="sxs-lookup"><span data-stu-id="97d5f-137">Using Your Build</span></span>

<span data-ttu-id="97d5f-138">生成将其所有生成的文件放在存储库底部的 `bin` 目录下。</span><span class="sxs-lookup"><span data-stu-id="97d5f-138">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="97d5f-139">bin\Log 目录包含生成期间生成的日志文件（生成失败时这些日志最为有用）。</span><span class="sxs-lookup"><span data-stu-id="97d5f-139">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="97d5f-140">实际输出位于bin\Product\[平台].[CPU 体系结构].[生成类型] 目录中，如 bin\Product\Windows_NT.x64.Release。</span><span class="sxs-lookup"><span data-stu-id="97d5f-140">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="97d5f-141">虽然生成的“原始”输出有时很有用，但通常只需要 NuGet 包，这些包位于之前输出目录的 `.nuget\pkg` 子目录中。</span><span class="sxs-lookup"><span data-stu-id="97d5f-141">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="97d5f-142">可通过两种基本方法使用新的运行时：</span><span class="sxs-lookup"><span data-stu-id="97d5f-142">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="97d5f-143">使用 dotnet.exe 和 NuGet 撰写应用程序。</span><span class="sxs-lookup"><span data-stu-id="97d5f-143">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="97d5f-144">请参阅[使用生成](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md)了解如何通过使用刚创建的 NuGet 包和“dotnet”命令行接口 (CLI) 来创建使用你的新运行时的程序。</span><span class="sxs-lookup"><span data-stu-id="97d5f-144">See [Using Your Build](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="97d5f-145">非运行时开发人员常通过此方法使用你的新运行时。</span><span class="sxs-lookup"><span data-stu-id="97d5f-145">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>

 2. <span data-ttu-id="97d5f-146">使用 corerun.exe 运行通过未打包的 DLL 运行应用程序。</span><span class="sxs-lookup"><span data-stu-id="97d5f-146">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="97d5f-147">此存储库还定义了一个名为 corerun.exe 的简单主机，它与 NuGet 没有任何依赖关系。</span><span class="sxs-lookup"><span data-stu-id="97d5f-147">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="97d5f-148">需要告诉主机在何处获取实际使用的所需 DLL，且必须手动将它们聚集在一起。</span><span class="sxs-lookup"><span data-stu-id="97d5f-148">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="97d5f-149">[dotnet/coreclr 存储库](https://github.com/dotnet/coreclr)中的所有测试都使用这种方式，可用于快速本地“编辑-编译-调试”循环（如初步单元测试）。</span><span class="sxs-lookup"><span data-stu-id="97d5f-149">This technique is used by all the tests in the [dotnet/coreclr](https://github.com/dotnet/coreclr) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="97d5f-150">有关使用此方法的详细信息，请参阅[使用 CoreRun.exe 执行 .NET Core 应用](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md)。</span><span class="sxs-lookup"><span data-stu-id="97d5f-150">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="97d5f-151">从源生成 CLI</span><span class="sxs-lookup"><span data-stu-id="97d5f-151">Build the CLI from source</span></span>

<span data-ttu-id="97d5f-152">有关 .NET Core CLI 的源代码，可以访问 GitHub 上的 [dotnet/cli](https://github.com/dotnet/cli/) 存储库。</span><span class="sxs-lookup"><span data-stu-id="97d5f-152">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="97d5f-153">为了生成 .NET Core CLI，需要在计算机上安装以下项。</span><span class="sxs-lookup"><span data-stu-id="97d5f-153">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

* <span data-ttu-id="97d5f-154">Windows 和 Linux：</span><span class="sxs-lookup"><span data-stu-id="97d5f-154">Windows & Linux:</span></span>
  * <span data-ttu-id="97d5f-155">PATH 上的 git</span><span class="sxs-lookup"><span data-stu-id="97d5f-155">git on the PATH</span></span>
* <span data-ttu-id="97d5f-156">macOS：</span><span class="sxs-lookup"><span data-stu-id="97d5f-156">macOS:</span></span>
  * <span data-ttu-id="97d5f-157">PATH 上的 git</span><span class="sxs-lookup"><span data-stu-id="97d5f-157">git on the PATH</span></span>
  * <span data-ttu-id="97d5f-158">Xcode</span><span class="sxs-lookup"><span data-stu-id="97d5f-158">Xcode</span></span>
  * <span data-ttu-id="97d5f-159">OpenSSL</span><span class="sxs-lookup"><span data-stu-id="97d5f-159">OpenSSL</span></span>

<span data-ttu-id="97d5f-160">若要进行生成，请在 Windows 上从根运行 `build.cmd`，在 Linux 和 macOS 上从根运行 `build.sh`。</span><span class="sxs-lookup"><span data-stu-id="97d5f-160">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="97d5f-161">如果不希望执行测试，请运行 `build.cmd -t:Compile` 或 `./build.sh -t:Compile`。</span><span class="sxs-lookup"><span data-stu-id="97d5f-161">If you don't want to execute tests, run `build.cmd -t:Compile` or `./build.sh -t:Compile`.</span></span> <span data-ttu-id="97d5f-162">若要在 macOS Sierra 中生成 CLI，需通过运行 `export DOTNET_RUNTIME_ID=osx.10.11-x64` 设置 DOTNET_RUNTIME_ID 环境变量。</span><span class="sxs-lookup"><span data-stu-id="97d5f-162">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="97d5f-163">使用生成</span><span class="sxs-lookup"><span data-stu-id="97d5f-163">Using your build</span></span>

<span data-ttu-id="97d5f-164">使用 artifacts/{os}-{arch}/stage2 中的 `dotnet` 可执行文件来试用新生成的 CLI。</span><span class="sxs-lookup"><span data-stu-id="97d5f-164">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="97d5f-165">如果想在从当前控制台调用 `dotnet` 时使用生成输出，也可以将 artifacts/{os}-{arch}/stage2 添加到 PATH。</span><span class="sxs-lookup"><span data-stu-id="97d5f-165">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="97d5f-166">另请参阅</span><span class="sxs-lookup"><span data-stu-id="97d5f-166">See also</span></span>

* [<span data-ttu-id="97d5f-167">.NET Core 公共语言运行时 (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="97d5f-167">.NET Core Common Language Runtime (CoreCLR)</span></span>](https://github.com/dotnet/coreclr/blob/master/README.md)
* [<span data-ttu-id="97d5f-168">.NET Core CLI 开发人员指南</span><span class="sxs-lookup"><span data-stu-id="97d5f-168">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
* [<span data-ttu-id="97d5f-169">.NET Core 分发打包</span><span class="sxs-lookup"><span data-stu-id="97d5f-169">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
