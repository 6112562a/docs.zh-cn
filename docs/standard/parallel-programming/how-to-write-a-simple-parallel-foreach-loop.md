---
title: 使用 Parallel.ForEach 编写简单的并行程序
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d54f06c1fc774a2e73b3b99a7d5bb24dd8baf3f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835264"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="a7afa-102">如何：编写简单的 Parallel.ForEach 循环</span><span class="sxs-lookup"><span data-stu-id="a7afa-102">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="a7afa-103">此示例展示了如何使用 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 循环，对任何 <xref:System.Collections.IEnumerable?displayProperty=nameWithType> 或 <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> 数据源启用数据并行。</span><span class="sxs-lookup"><span data-stu-id="a7afa-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="a7afa-104">本文档使用 lambda 表达式在 PLINQ 中定义委托。</span><span class="sxs-lookup"><span data-stu-id="a7afa-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="a7afa-105">如果不熟悉 C# 或 Visual Basic 中的 lambda 表达式，请参阅 [PLINQ 和 TPL 中的 Lambda 表达式](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)。</span><span class="sxs-lookup"><span data-stu-id="a7afa-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="a7afa-106">示例</span><span class="sxs-lookup"><span data-stu-id="a7afa-106">Example</span></span>

<span data-ttu-id="a7afa-107">此示例假定 C:\Users\Public\Pictures\Sample Pictures  文件夹中有几个 .jpg 文件，并创建名为“Modified”  的新子文件夹。</span><span class="sxs-lookup"><span data-stu-id="a7afa-107">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="a7afa-108">运行该示例时，它会旋转示例图片中的每个 .jpg 图像  并将其保存到“Modified”文件夹 </span><span class="sxs-lookup"><span data-stu-id="a7afa-108">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="a7afa-109">可以根据需要修改这两个路径。</span><span class="sxs-lookup"><span data-stu-id="a7afa-109">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="a7afa-110"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 循环的工作原理类似 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 循环。</span><span class="sxs-lookup"><span data-stu-id="a7afa-110">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="a7afa-111">该循环对源集合进行分区，并根据系统环境在多个线程上安排工作。</span><span class="sxs-lookup"><span data-stu-id="a7afa-111">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="a7afa-112">系统上的处理器越多，并行方法的运行速度就越快。</span><span class="sxs-lookup"><span data-stu-id="a7afa-112">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="a7afa-113">对于一些源集合，有序循环可能会更快，具体视源大小以及该循环要执行的工作类型而定。</span><span class="sxs-lookup"><span data-stu-id="a7afa-113">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="a7afa-114">有关性能的详细信息，请参阅[数据和任务并行的潜在问题](potential-pitfalls-in-data-and-task-parallelism.md)。</span><span class="sxs-lookup"><span data-stu-id="a7afa-114">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="a7afa-115">若要详细了解并行循环，请参阅[如何：编写简单的 Parallel.For 循环](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md)。</span><span class="sxs-lookup"><span data-stu-id="a7afa-115">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="a7afa-116">若要将 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 与非泛型集合结合使用，可以使用 <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> 扩展方法，将集合转换为泛型集合，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="a7afa-116">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="a7afa-117">还可以使用并行 LINQ (PLINQ) 并行处理 <xref:System.Collections.Generic.IEnumerable%601> 数据源。</span><span class="sxs-lookup"><span data-stu-id="a7afa-117">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="a7afa-118">借助 PLINQ，可以使用声明性查询语法来表达循环行为。</span><span class="sxs-lookup"><span data-stu-id="a7afa-118">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="a7afa-119">有关详细信息，请参阅[并行 LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)。</span><span class="sxs-lookup"><span data-stu-id="a7afa-119">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="a7afa-120">编译并运行代码</span><span class="sxs-lookup"><span data-stu-id="a7afa-120">Compile and run the code</span></span>

<span data-ttu-id="a7afa-121">可以作为 .NET Framework 的控制台应用程序或 .NET Core 的控制台应用程序编译代码。</span><span class="sxs-lookup"><span data-stu-id="a7afa-121">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="a7afa-122">Visual Studio 中有适用于 Windows 桌面和 .NET Core 的 Visual Basic 和 C# 控制台应用程序模板。</span><span class="sxs-lookup"><span data-stu-id="a7afa-122">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="a7afa-123">从命令行，可使用 .NET Core 及其 CLI 工具（例如 `dotnet new console` 或 `dotnet new console -lang vb`），或者可创建文件并使用 .NET Framework 应用程序提供的命令行编译器。</span><span class="sxs-lookup"><span data-stu-id="a7afa-123">From the command line, you can use either .NET Core and its CLI tools (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="a7afa-124">对于.NET Core 项目，必须引用 System.Drawing.Common  NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="a7afa-124">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="a7afa-125">在 Visual Studio 中，使用 NuGet 包管理器安装该包。</span><span class="sxs-lookup"><span data-stu-id="a7afa-125">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="a7afa-126">或者，也可以在 \*.csproj 或 \*.vbproj 文件中添加对包的引用：</span><span class="sxs-lookup"><span data-stu-id="a7afa-126">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>
 
```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="a7afa-127">要从命令行运行 .NET Core 控制台应用程序，请使用包含该应用程序的文件夹中的 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="a7afa-127">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="a7afa-128">要从 Visual Studio 中运行控制台应用程序，请按 F5  。</span><span class="sxs-lookup"><span data-stu-id="a7afa-128">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a7afa-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="a7afa-129">See also</span></span>

- [<span data-ttu-id="a7afa-130">数据并行</span><span class="sxs-lookup"><span data-stu-id="a7afa-130">Data parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="a7afa-131">并行编程</span><span class="sxs-lookup"><span data-stu-id="a7afa-131">Parallel programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="a7afa-132">并行 LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a7afa-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
