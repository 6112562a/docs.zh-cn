---
title: .NET 可移植性分析器 - .NET
description: 了解如何使用 .NET 可移植性分析器工具，评估代码在各种 .NET 实现（包括 .NET Core、.NET Standard、UWP 和 Xamarin）间的可移植性。
ms.date: 04/26/2019
ms.technology: dotnet-standard
ms.assetid: 0375250f-5704-4993-a6d5-e21c499cea1e
ms.openlocfilehash: 7de6aa72b2d30c3e54d2ddf9a2d951688571d654
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063435"
---
# <a name="the-net-portability-analyzer"></a><span data-ttu-id="bf2df-103">.NET 可移植性分析器</span><span class="sxs-lookup"><span data-stu-id="bf2df-103">The .NET Portability Analyzer</span></span>

<span data-ttu-id="bf2df-104">想要让你的库在多个平台上使用？</span><span class="sxs-lookup"><span data-stu-id="bf2df-104">Want to make your libraries multi-platform?</span></span> <span data-ttu-id="bf2df-105">想要了解让应用与其他 .NET 实现和配置文件（包括 .NET Core、.NET Standard、UWP 以及适用于 iOS、Android 和 Mac 的 Xamarin）兼容所需的工作量？</span><span class="sxs-lookup"><span data-stu-id="bf2df-105">Want to see how much work is required to make your application compatible with other .NET implementations and profiles, including .NET Core, .NET Standard, UWP, and Xamarin for iOS, Android, and Mac?</span></span> <span data-ttu-id="bf2df-106">[.NET 可移植性分析器](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)工具可通过分析程序集，详细报告程序在各种 .NET 实现上的灵活性。</span><span class="sxs-lookup"><span data-stu-id="bf2df-106">The [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) is a tool that provides you with a detailed report on how flexible your program is across .NET implementations by analyzing assemblies.</span></span> <span data-ttu-id="bf2df-107">可移植性分析器以 Visual Studio 扩展和控制台应用的形式提供。</span><span class="sxs-lookup"><span data-stu-id="bf2df-107">The Portability Analyzer is offered as a Visual Studio Extension and as a console app.</span></span>

## <a name="new-targets"></a><span data-ttu-id="bf2df-108">新目标</span><span class="sxs-lookup"><span data-stu-id="bf2df-108">New targets</span></span>

* <span data-ttu-id="bf2df-109">[.NET Core](../../core/index.md)：采用模块化设计，可并行工作，面向跨平台方案。</span><span class="sxs-lookup"><span data-stu-id="bf2df-109">[.NET Core](../../core/index.md): Has a modular design, employs side-by-side, and targets cross-platform scenarios.</span></span> <span data-ttu-id="bf2df-110">可并行工作意味着无需破坏其他应用即可采用新的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="bf2df-110">Side-by-side allows you to adopt new .NET Core versions without breaking other apps.</span></span>
* <span data-ttu-id="bf2df-111">[ASP.NET Core](/aspnet/core)：构建在 .NET Core 基础之上的新型 Web 框架，为开发人员提供与 .NET Core 相同的优势。</span><span class="sxs-lookup"><span data-stu-id="bf2df-111">[ASP.NET Core](/aspnet/core): is a modern web-framework built on .NET Core thus giving developers the same benefits.</span></span>
* <span data-ttu-id="bf2df-112">[通用 Windows 平台](/uwp)：使用 .NET Native 的静态编译，提高 x64 和 ARM 计算机上运行的 Windows 应用商店应用的性能。</span><span class="sxs-lookup"><span data-stu-id="bf2df-112">[Universal Windows Platform](/uwp): Improve performance of your Windows Store apps that run on x64 and ARM machines by using .NET Native’s static compilation.</span></span> 
* <span data-ttu-id="bf2df-113">.NET Core + 平台扩展：除 WCF、ASP.NET Core、FSharp 和 Azure 等 .NET 生态系统中的其他 API 外还包括 .NET Core API。</span><span class="sxs-lookup"><span data-stu-id="bf2df-113">.NET Core + Platform Extensions: Includes the .NET Core APIs in addition to other APIs in the .NET ecosystem such as WCF, ASP.NET Core, FSharp, and Azure.</span></span>
* <span data-ttu-id="bf2df-114">.NET Standard + 平台扩展：除 WCF、ASP.NET Core、FSharp 和 Azure 等 .NET 生态系统中的其他 API 外还包括 .NET Standard API。</span><span class="sxs-lookup"><span data-stu-id="bf2df-114">.NET Standard + Platform Extensions: Includes the .NET Standard APIs in addition to other .NET ecosystem such as WCF, ASP.NET Core, FSharp, and Azure.</span></span>

## <a name="how-to-use-the-portability-analyzer"></a><span data-ttu-id="bf2df-115">如何使用可移植性分析器</span><span class="sxs-lookup"><span data-stu-id="bf2df-115">How to use the Portability Analyzer</span></span>

<span data-ttu-id="bf2df-116">若要开始使用 .NET 可移植性分析器，首先需要从 [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer) 下载相应的扩展。</span><span class="sxs-lookup"><span data-stu-id="bf2df-116">To begin using the .NET Portability Analyzer, you first need to download and install the extension from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span></span> <span data-ttu-id="bf2df-117">它适用于 Visual Studio 2017 及更高版本。</span><span class="sxs-lookup"><span data-stu-id="bf2df-117">It works on Visual Studio 2017 and later versions.</span></span> <span data-ttu-id="bf2df-118">可以在 Visual Studio 中转到“分析” > “可移植性分析器设置”并选择目标平台，对可移植性分析器进行配置。</span><span class="sxs-lookup"><span data-stu-id="bf2df-118">You can configure it in Visual Studio via **Analyze** > **Portability Analyzer Settings** and select your Target Platforms.</span></span>

![可移植性屏幕截图](./media/portability-analyzer/portability-screenshot.png)

<span data-ttu-id="bf2df-120">若要分析整个项目，请在“解决方案资源管理器”中右键单击该项目，然后选择“分析程序集可移植性”。</span><span class="sxs-lookup"><span data-stu-id="bf2df-120">To analyze your entire project, right-click on your project in **Solution Explorer** and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="bf2df-121">也可以转到“分析”菜单，选择“分析程序集可移植性”。</span><span class="sxs-lookup"><span data-stu-id="bf2df-121">Otherwise, go to the **Analyze** menu and select **Analyze Assembly Portability**.</span></span> <span data-ttu-id="bf2df-122">在该位置选择项目的可执行文件或 DLL。</span><span class="sxs-lookup"><span data-stu-id="bf2df-122">From there, select your project’s executable or DLL.</span></span>

![解决方案资源管理器中的可移植性分析器](./media/portability-analyzer/portability-solution-explorer.png)

<span data-ttu-id="bf2df-124">运行分析后，将看到 .NET 可移植性报告。</span><span class="sxs-lookup"><span data-stu-id="bf2df-124">After running the analysis, you'll see your .NET Portability Report.</span></span> <span data-ttu-id="bf2df-125">只有不受目标平台支持的类型才显示在列表中，可在“错误列表”的“消息”选项卡中查看建议。</span><span class="sxs-lookup"><span data-stu-id="bf2df-125">Only types that are unsupported by a target platform appear in the list and you can review recommendations in the **Messages** tab in the **Error List**.</span></span> <span data-ttu-id="bf2df-126">还可以直接从“消息”选项卡跳转到问题区域。</span><span class="sxs-lookup"><span data-stu-id="bf2df-126">You can also jump to problem areas directly from the **Messages** tab.</span></span>

![可移植性报告](./media/portability-analyzer/portability-report.png)

<span data-ttu-id="bf2df-128">如果不想使用 Visual Studio，可以通过命令提示符使用可移植性分析器。</span><span class="sxs-lookup"><span data-stu-id="bf2df-128">If you don’t want to use Visual Studio, you can use the Portability Analyzer from the command prompt.</span></span> <span data-ttu-id="bf2df-129">只需从 [Microsoft/dotnet-apiport](https://github.com/Microsoft/dotnet-apiport/releases) 存储库下载 API 可移植性分析器即可。</span><span class="sxs-lookup"><span data-stu-id="bf2df-129">Just download the API Portability Analyzer from the [Microsoft/dotnet-apiport](https://github.com/Microsoft/dotnet-apiport/releases) repository.</span></span>

* <span data-ttu-id="bf2df-130">键入以下命令即可分析当前目录：`\...\ApiPort.exe analyze -f .`</span><span class="sxs-lookup"><span data-stu-id="bf2df-130">Type the following command to analyze the current directory: `\...\ApiPort.exe analyze -f .`</span></span>
* <span data-ttu-id="bf2df-131">若要分析特定的 .dll 文件列表，请键入以下命令：`\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`</span><span class="sxs-lookup"><span data-stu-id="bf2df-131">To analyze a specific list of .dll files, type the following command: `\...\ApiPort.exe analyze -f first.dll -f second.dll -f third.dll`</span></span>

<span data-ttu-id="bf2df-132">.NET 可移植性报告以 Excel 文件 (.xlsx) 格式保存在当前目录中。</span><span class="sxs-lookup"><span data-stu-id="bf2df-132">Your .NET Portability Report is saved as an Excel file (*.xlsx*) in your current directory.</span></span> <span data-ttu-id="bf2df-133">Excel 工作簿中的“详细信息”选项卡包含详细信息。</span><span class="sxs-lookup"><span data-stu-id="bf2df-133">The **Details** tab in the Excel Workbook contains more information.</span></span>

<span data-ttu-id="bf2df-134">有关 .NET 可移植性分析器的详细信息，请访问 [GitHub 文档](https://github.com/Microsoft/dotnet-apiport#documentation)和[简要了解 .NET 可移植性分析器](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer)第 9 频道视频。</span><span class="sxs-lookup"><span data-stu-id="bf2df-134">For more information on the .NET Portability Analyzer, visit the [GitHub documentation](https://github.com/Microsoft/dotnet-apiport#documentation) and [A Brief Look at the .NET Portability Analyzer](https://channel9.msdn.com/Blogs/Seth-Juarez/A-Brief-Look-at-the-NET-Portability-Analyzer) Channel 9 video.</span></span>
