---
title: .NET 中的并行编程
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
ms.openlocfilehash: ae129ef0cb2b331c1eb0220282f21fec6f6fb77d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134147"
---
# <a name="parallel-programming-in-net"></a><span data-ttu-id="2fd02-102">.NET 中的并行编程</span><span class="sxs-lookup"><span data-stu-id="2fd02-102">Parallel Programming in .NET</span></span>

<span data-ttu-id="2fd02-103">许多个人计算机和工作站都有多个 CPU 内核，以便多个线程能够同时执行。</span><span class="sxs-lookup"><span data-stu-id="2fd02-103">Many personal computers and workstations have multiple CPU cores that enable multiple threads to be executed simultaneously.</span></span> <span data-ttu-id="2fd02-104">为了利用硬件，你可以对代码进行并行化，以将工作分摊在多个处理器上。</span><span class="sxs-lookup"><span data-stu-id="2fd02-104">To take advantage of the hardware, you can parallelize your code to distribute work across multiple processors.</span></span>

<span data-ttu-id="2fd02-105">过去，并行化需要线程和锁的低级操作。</span><span class="sxs-lookup"><span data-stu-id="2fd02-105">In the past, parallelization required low-level manipulation of threads and locks.</span></span> <span data-ttu-id="2fd02-106">Visual Studio 和 .NET Framework 提供了运行时、类库类型和诊断工具，从而增强了对并行编程的支持。</span><span class="sxs-lookup"><span data-stu-id="2fd02-106">Visual Studio and the .NET Framework enhance support for parallel programming by providing a runtime, class library types, and diagnostic tools.</span></span> <span data-ttu-id="2fd02-107">.NET Framework 4 中引入的这些功能简化了并行开发。</span><span class="sxs-lookup"><span data-stu-id="2fd02-107">These features, which were introduced with the .NET Framework 4, simplify parallel development.</span></span> <span data-ttu-id="2fd02-108">你可以通过固有方法编写高效、细化且可伸缩的并行代码，而不必直接处理线程或线程池。</span><span class="sxs-lookup"><span data-stu-id="2fd02-108">You can write efficient, fine-grained, and scalable parallel code in a natural idiom without having to work directly with threads or the thread pool.</span></span>

<span data-ttu-id="2fd02-109">下图简要概述了 .NET Framework 中的并行编程体系结构：</span><span class="sxs-lookup"><span data-stu-id="2fd02-109">The following illustration provides a high-level overview of the parallel programming architecture in the .NET Framework:</span></span>

![.NET 并行编程体系结构](./media/tpl-architecture.png)

## <a name="related-topics"></a><span data-ttu-id="2fd02-111">相关主题</span><span class="sxs-lookup"><span data-stu-id="2fd02-111">Related Topics</span></span>

|<span data-ttu-id="2fd02-112">技术</span><span class="sxs-lookup"><span data-stu-id="2fd02-112">Technology</span></span>|<span data-ttu-id="2fd02-113">说明</span><span class="sxs-lookup"><span data-stu-id="2fd02-113">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="2fd02-114">任务并行库 (TPL)</span><span class="sxs-lookup"><span data-stu-id="2fd02-114">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)|<span data-ttu-id="2fd02-115">提供针对 <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> 类的文档（包括 `For` 和 `ForEach` 循环的并行版本），还提供了针对 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 类的文档（描绘了表示异步操作的首选方式）。</span><span class="sxs-lookup"><span data-stu-id="2fd02-115">Provides documentation for the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> class, which includes parallel versions of `For` and `ForEach` loops, and also for the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class, which represents the preferred way to express asynchronous operations.</span></span>|
|[<span data-ttu-id="2fd02-116">并行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="2fd02-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)|<span data-ttu-id="2fd02-117">LINQ to Objects 的并行实现，该实现显著提高了许多情况下的性能。</span><span class="sxs-lookup"><span data-stu-id="2fd02-117">A parallel implementation of LINQ to Objects that significantly improves performance in many scenarios.</span></span>|
|[<span data-ttu-id="2fd02-118">用于并行编程的数据结构</span><span class="sxs-lookup"><span data-stu-id="2fd02-118">Data Structures for Parallel Programming</span></span>](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)|<span data-ttu-id="2fd02-119">提供一些链接，这些链接指向有关线程安全集合类、轻量同步类型以及延迟初始化类型的文档。</span><span class="sxs-lookup"><span data-stu-id="2fd02-119">Provides links to documentation for thread-safe collection classes, lightweight synchronization types, and types for lazy initialization.</span></span>|
|[<span data-ttu-id="2fd02-120">并行诊断工具</span><span class="sxs-lookup"><span data-stu-id="2fd02-120">Parallel Diagnostic Tools</span></span>](../../../docs/standard/parallel-programming/parallel-diagnostic-tools.md)|<span data-ttu-id="2fd02-121">提供一些链接，这些链接指向任务和并行堆栈的 Visual Studio 调试器窗口和[并发可视化工具](/visualstudio/profiling/concurrency-visualizer)的文档。</span><span class="sxs-lookup"><span data-stu-id="2fd02-121">Provides links to documentation for Visual Studio debugger windows for tasks and parallel stacks, and for the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>|
|[<span data-ttu-id="2fd02-122">PLINQ 和 TPL 的自定义分区程序</span><span class="sxs-lookup"><span data-stu-id="2fd02-122">Custom Partitioners for PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)|<span data-ttu-id="2fd02-123">描述分区程序的工作方式，以及如何配置默认分区程序或创建新的分区程序。</span><span class="sxs-lookup"><span data-stu-id="2fd02-123">Describes how partitioners work and how to configure the default partitioners or create a new partitioner.</span></span>|
|[<span data-ttu-id="2fd02-124">任务计划程序</span><span class="sxs-lookup"><span data-stu-id="2fd02-124">Task Schedulers</span></span>](xref:System.Threading.Tasks.TaskScheduler)|<span data-ttu-id="2fd02-125">描述计划程序的工作方式，以及如何配置默认计划程序。</span><span class="sxs-lookup"><span data-stu-id="2fd02-125">Describes how schedulers work and how the default schedulers may be configured.</span></span>|
|[<span data-ttu-id="2fd02-126">PLINQ 和 TPL 中的 Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="2fd02-126">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)|<span data-ttu-id="2fd02-127">简要概述 C# 和 Visual Basic 中的 Lambda 表达式，并演示如何在 PLINQ 和任务并行库中使用这些表达式。</span><span class="sxs-lookup"><span data-stu-id="2fd02-127">Provides a brief overview of lambda expressions in C# and Visual Basic, and shows how they are used in PLINQ and the Task Parallel Library.</span></span>|
|[<span data-ttu-id="2fd02-128">其他阅读材料</span><span class="sxs-lookup"><span data-stu-id="2fd02-128">For Further Reading</span></span>](../../../docs/standard/parallel-programming/for-further-reading-parallel-programming.md)|<span data-ttu-id="2fd02-129">收录了指向其他信息以及 .NET 中并行编程示例资源的链接。</span><span class="sxs-lookup"><span data-stu-id="2fd02-129">Provides links to additional information and sample resources for parallel programming in .NET.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2fd02-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="2fd02-130">See also</span></span>

- [<span data-ttu-id="2fd02-131">异步概述</span><span class="sxs-lookup"><span data-stu-id="2fd02-131">Async Overview</span></span>](../async.md)
- [<span data-ttu-id="2fd02-132">托管线程</span><span class="sxs-lookup"><span data-stu-id="2fd02-132">Managed Threading</span></span>](../threading/index.md)
