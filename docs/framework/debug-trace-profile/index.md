---
title: 调试、跟踪和分析
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
ms.openlocfilehash: 1a43c7fbcb810b22ff9bc409c233d2b1da67370e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217405"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="cb29a-102">调试、跟踪和分析</span><span class="sxs-lookup"><span data-stu-id="cb29a-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="cb29a-103">若要调试 .NET Framework 应用程序，编译器和运行时环境必须配置为可将调试程序附加到该应用程序，并且如果可能的话，为该应用程序及其相应 Microsoft 中间语言 (MSIL) 同时生成符号和行映射。</span><span class="sxs-lookup"><span data-stu-id="cb29a-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="cb29a-104">在对托管应用程序进行调试后，可对其进行分析以增强性能。</span><span class="sxs-lookup"><span data-stu-id="cb29a-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="cb29a-105">分析计算并描述可生成最常执行的代码的源代码行，以及执行它们所需的时间。</span><span class="sxs-lookup"><span data-stu-id="cb29a-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="cb29a-106">通过使用 Visual Studio 可轻松地调试.NET framework 应用程序，前者用于处理配置的许多详细信息。</span><span class="sxs-lookup"><span data-stu-id="cb29a-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="cb29a-107">如果未安装 Visual Studio，可以通过使用 .NET Framework <xref:System.Diagnostics> 命名空间中的调试类检查并提升 .NET Framework 应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="cb29a-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="cb29a-108">此命名空间包括用于跟踪执行流的 <xref:System.Diagnostics.Trace>、<xref:System.Diagnostics.Debug> 和 <xref:System.Diagnostics.TraceSource> 类，以及用于分析代码的 <xref:System.Diagnostics.Process>、<xref:System.Diagnostics.EventLog> 和 <xref:System.Diagnostics.PerformanceCounter> 类。</span><span class="sxs-lookup"><span data-stu-id="cb29a-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb29a-109">本节内容</span><span class="sxs-lookup"><span data-stu-id="cb29a-109">In This Section</span></span>  
 [<span data-ttu-id="cb29a-110">启用 JIT 附加调试</span><span class="sxs-lookup"><span data-stu-id="cb29a-110">Enabling JIT-Attach Debugging</span></span>](enabling-jit-attach-debugging.md)  
 <span data-ttu-id="cb29a-111">演示如何配置注册表从而将调试引擎以 JIT 方式附加到 .NET Framework 应用程序。</span><span class="sxs-lookup"><span data-stu-id="cb29a-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="cb29a-112">使映像更易于调试</span><span class="sxs-lookup"><span data-stu-id="cb29a-112">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)  
 <span data-ttu-id="cb29a-113">演示如何打开 JIT 跟踪和关闭优化，以使程序集更易于调试。</span><span class="sxs-lookup"><span data-stu-id="cb29a-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="cb29a-114">跟踪应用程序和在应用程序中插入检测点</span><span class="sxs-lookup"><span data-stu-id="cb29a-114">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="cb29a-115">描述如何监视应用程序在运行时的执行，以及如何来检测它以显示其执行状态或是否出现了问题。</span><span class="sxs-lookup"><span data-stu-id="cb29a-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="cb29a-116">使用托管调试助手诊断错误</span><span class="sxs-lookup"><span data-stu-id="cb29a-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="cb29a-117">描述托管调试助手 (MDA)，它是与公共语言运行时 (CLR) 联合工作以提供有关运行时状态信息的调试辅助程序。</span><span class="sxs-lookup"><span data-stu-id="cb29a-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="cb29a-118">使用调试器显示特性增强调试</span><span class="sxs-lookup"><span data-stu-id="cb29a-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="cb29a-119">描述某种类型的开发人员可如何指定该类型在调试器中显示时的样子。</span><span class="sxs-lookup"><span data-stu-id="cb29a-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="cb29a-120">性能计数器</span><span class="sxs-lookup"><span data-stu-id="cb29a-120">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="cb29a-121">描述可用来跟踪应用程序性能的计数器。</span><span class="sxs-lookup"><span data-stu-id="cb29a-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cb29a-122">相关章节</span><span class="sxs-lookup"><span data-stu-id="cb29a-122">Related Sections</span></span>  
 [<span data-ttu-id="cb29a-123">在 Visual Studio 中调试 ASP.NET 或 ASP.NET Core 应用</span><span class="sxs-lookup"><span data-stu-id="cb29a-123">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 <span data-ttu-id="cb29a-124">提供有关如何在开发期间或部署后调试 ASP.NET 应用程序的先决条件和说明。</span><span class="sxs-lookup"><span data-stu-id="cb29a-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="cb29a-125">开发指南</span><span class="sxs-lookup"><span data-stu-id="cb29a-125">Development Guide</span></span>](../development-guide.md)  
 <span data-ttu-id="cb29a-126">提供了有关应用程序开发的所有关键技术区域和任务（包括创建、配置、调试、保护和部署应用程序）的指南，以及有关动态编程、互操作性、扩展性、内存管理和线程处理的信息。</span><span class="sxs-lookup"><span data-stu-id="cb29a-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
