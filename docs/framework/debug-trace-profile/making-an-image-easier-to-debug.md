---
title: 使映像更易于在 .NET 中进行调试
description: 了解如何配置可执行映像，以便使用 IDE 开关和命令行选项更轻松地进行调试。
ms.date: 08/30/2018
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b64bd1e112932f394bb473a21642d37e28e39d3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052504"
---
# <a name="making-an-image-easier-to-debug-in-net"></a><span data-ttu-id="f5914-103">使映像更易于在 .NET 中进行调试</span><span class="sxs-lookup"><span data-stu-id="f5914-103">Making an image easier to debug in .NET</span></span>

<span data-ttu-id="f5914-104">编译非托管代码时，可以通过设置 IDE 开关或命令线选项来配置可执行映像进行调试。</span><span class="sxs-lookup"><span data-stu-id="f5914-104">When compiling unmanaged code, you can configure an executable image for debugging by setting IDE switches or command-line options.</span></span> <span data-ttu-id="f5914-105">例如，可以使用 Visual C++ 中的 /Zi 命令行选项，使其发出调试符号文件（文件扩展名为 .pdb）。</span><span class="sxs-lookup"><span data-stu-id="f5914-105">For example, you can use the /**Zi** command-line option in Visual C++ to ask it to emit debug symbol files (file extension .pdb).</span></span> <span data-ttu-id="f5914-106">同样，/Od 命令行选项告知编译器禁用优化。</span><span class="sxs-lookup"><span data-stu-id="f5914-106">Similarly, the /**Od** command-line option tells the compiler to disable optimization.</span></span> <span data-ttu-id="f5914-107">生成的代码运行速度变慢，但调试起来更容易，但这是必需的。</span><span class="sxs-lookup"><span data-stu-id="f5914-107">The resulting code runs more slowly, but it's easier to debug, should this be necessary.</span></span>

<span data-ttu-id="f5914-108">编译 .NET Framework 托管代码时，编译器（如视觉C++对象 Visual Basic）， C#并将其源程序编译为 MICROSOFT 中间语言（MSIL）。</span><span class="sxs-lookup"><span data-stu-id="f5914-108">When compiling .NET Framework managed code, compilers such as Visual C++, Visual Basic, and C# compile their source program into Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="f5914-109">然后，在执行之前将 MSIL 编译为本机代码。</span><span class="sxs-lookup"><span data-stu-id="f5914-109">MSIL is then JIT-compiled, just before execution, into native machine code.</span></span> <span data-ttu-id="f5914-110">与非托管代码一样，可以通过设置 IDE 开关或命令行选项来配置可执行映像进行调试。</span><span class="sxs-lookup"><span data-stu-id="f5914-110">As with unmanaged code, you can configure an executable image for debugging by setting IDE switches or command-line options.</span></span> <span data-ttu-id="f5914-111">你还可以配置 JIT 编译以便进行调试，其方式大致相同。</span><span class="sxs-lookup"><span data-stu-id="f5914-111">You can also configure the JIT compilation for debugging in much the same way.</span></span>

<span data-ttu-id="f5914-112">这种 JIT 配置具有两个方面：</span><span class="sxs-lookup"><span data-stu-id="f5914-112">This JIT configuration has two aspects:</span></span>

- <span data-ttu-id="f5914-113">可以请求 JIT 编译器生成跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="f5914-113">You can request the JIT compiler to generate tracking information.</span></span> <span data-ttu-id="f5914-114">这使调试程序能将 MSIL 链与其机器码对应项相匹配，并跟踪存储本地变量和函数参数的位置。</span><span class="sxs-lookup"><span data-stu-id="f5914-114">This makes it possible for the debugger to match up a chain of MSIL with its machine code counterpart, and to track where local variables and function arguments are stored.</span></span> <span data-ttu-id="f5914-115">从 .NET Framework 版本2.0 开始，JIT 编译器将始终生成跟踪信息，因此无需对其进行请求。</span><span class="sxs-lookup"><span data-stu-id="f5914-115">Starting with the .NET Framework version 2.0, the JIT compiler always generates tracking information, so there is no need to request it.</span></span>

- <span data-ttu-id="f5914-116">可以请求 JIT 编译器不优化生成的计算机代码。</span><span class="sxs-lookup"><span data-stu-id="f5914-116">You can request the JIT compiler to not optimize the resulting machine code.</span></span>

<span data-ttu-id="f5914-117">通常，生成 MSIL 的编译器会根据你指定的 IDE 开关或命令行选项（例如/**Od**）适当地设置这些 JIT 编译器选项。</span><span class="sxs-lookup"><span data-stu-id="f5914-117">Normally, the compiler that generates the MSIL sets these JIT compiler options appropriately, based upon the IDE switches or command-line options you specify, for example, /**Od**.</span></span>

<span data-ttu-id="f5914-118">某些情况下，可能需要更改 JIT 编译器的行为，使其生成的机器码更易于调试。</span><span class="sxs-lookup"><span data-stu-id="f5914-118">In some cases, you might want to change the behavior of the JIT compiler so that the machine code it generates is easier to debug.</span></span> <span data-ttu-id="f5914-119">例如，可能希望为零售版本或控制优化生成实时跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="f5914-119">For example, you might want to generate JIT tracking information for a retail build or control optimization.</span></span> <span data-ttu-id="f5914-120">可以使用初始化 (.ini) 文件来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="f5914-120">You can do so with an initialization (.ini) file.</span></span>

<span data-ttu-id="f5914-121">例如，如果你想要调试的程序集名为*myapp.exe*，则可以创建一个*名为* *myapp*的文本文件，该文件包含以下三行：</span><span class="sxs-lookup"><span data-stu-id="f5914-121">For example, if the assembly you want to debug is called *MyApp.exe*, then you can create a text file named *MyApp.ini*, in the same folder as *MyApp.exe*, which contains these three lines:</span></span>

```ini
[.NET Framework Debugging Control]
GenerateTrackingInfo=1
AllowOptimize=0
```

<span data-ttu-id="f5914-122">可将每个选项的值设置为 0 或 1，任何不存在选项默认为 0。</span><span class="sxs-lookup"><span data-stu-id="f5914-122">You can set the value of each option to 0 or 1, and any absent option defaults to 0.</span></span> <span data-ttu-id="f5914-123">将 `GenerateTrackingInfo` 设为 1、`AllowOptimize` 设为 0，这可提供最简单的调试。</span><span class="sxs-lookup"><span data-stu-id="f5914-123">Setting `GenerateTrackingInfo` to 1 and `AllowOptimize` to 0 provides the easiest debugging.</span></span>

<span data-ttu-id="f5914-124">从 .NET Framework 版本2.0 开始，JIT 编译器将始终生成跟踪信息，而不考虑的值`GenerateTrackingInfo`; 但是`AllowOptimize` ，该值仍有效果。</span><span class="sxs-lookup"><span data-stu-id="f5914-124">Starting with the .NET Framework version 2.0, the JIT compiler always generates tracking information regardless of the value for `GenerateTrackingInfo`; however, the `AllowOptimize` value still has an effect.</span></span> <span data-ttu-id="f5914-125">如果使用 [Ngen.exe（本机映像生成器）](../tools/ngen-exe-native-image-generator.md)预编译本机映像而不进行优化，Ngen.exe 执行时 .ini 文件必须存在于 `AllowOptimize=0` 的目标文件夹。</span><span class="sxs-lookup"><span data-stu-id="f5914-125">When using the [Ngen.exe (Native Image Generator)](../tools/ngen-exe-native-image-generator.md) to precompile the native image without optimization, the .ini file must be present in the target folder with `AllowOptimize=0` when Ngen.exe executes.</span></span> <span data-ttu-id="f5914-126">如果在未优化的情况下预编译程序集，则必须先使用 Ngen.exe **/uninstall**选项删除预编译代码，然后再重新运行 ngen.exe，以将代码预编译为优化。</span><span class="sxs-lookup"><span data-stu-id="f5914-126">If you have precompiled an assembly without optimization, you must remove the precompiled code using NGen.exe **/uninstall** option before rerunning Ngen.exe to precompile the code as optimized.</span></span> <span data-ttu-id="f5914-127">如果文件夹中不存在 .ini 文件，则默认情况下，Ngen.exe 将代码预编译为优化。</span><span class="sxs-lookup"><span data-stu-id="f5914-127">If the .ini file isn't present in the folder, by default Ngen.exe precompiles the code as optimized.</span></span>

<span data-ttu-id="f5914-128"><xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> 控制程序集的设置。</span><span class="sxs-lookup"><span data-stu-id="f5914-128">The <xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> controls the settings for an assembly.</span></span> <span data-ttu-id="f5914-129">**DebuggableAttribute**包含两个字段，用于控制 JIT 编译器是否应优化和/或生成跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="f5914-129">**DebuggableAttribute** includes two fields that control whether the JIT compiler should optimize and/or generate tracking information.</span></span> <span data-ttu-id="f5914-130">从 .NET Framework 版本2.0 开始，JIT 编译器将始终生成跟踪信息。</span><span class="sxs-lookup"><span data-stu-id="f5914-130">Starting with the .NET Framework version 2.0, the JIT compiler always generates tracking information.</span></span>

<span data-ttu-id="f5914-131">对于零售版本，编译器不会设置任何**DebuggableAttribute**。</span><span class="sxs-lookup"><span data-stu-id="f5914-131">For a retail build, compilers don't set any **DebuggableAttribute**.</span></span> <span data-ttu-id="f5914-132">默认情况下，JIT 编译器将生成最高性能，最难调试计算机代码。</span><span class="sxs-lookup"><span data-stu-id="f5914-132">By default, the JIT compiler generates the highest performance, hardest to debug machine code.</span></span> <span data-ttu-id="f5914-133">启用实时跟踪会稍微降低性能，禁用优化会极大降低性能。</span><span class="sxs-lookup"><span data-stu-id="f5914-133">Enabling JIT tracking lowers performance a little, and disabling optimization lowers performance a lot.</span></span>

<span data-ttu-id="f5914-134">DebuggableAttribute 一次应用于整个程序集，而不是应用于程序集中的单个模块。</span><span class="sxs-lookup"><span data-stu-id="f5914-134">The **DebuggableAttribute** applies to a whole assembly at a time, not to individual modules within the assembly.</span></span> <span data-ttu-id="f5914-135">因此，开发工具必须将自定义属性附加到程序集元数据令牌，如果已经创建程序集，则附加到名为 System.Runtime.CompilerServices.AssemblyAttributesGoHere 的类。</span><span class="sxs-lookup"><span data-stu-id="f5914-135">Development tools must therefore attach custom attributes to the assembly metadata token, if an assembly has already been created, or to the class called **System.Runtime.CompilerServices.AssemblyAttributesGoHere**.</span></span> <span data-ttu-id="f5914-136">然后，ALink 工具会将每个模块中的这些**DebuggableAttribute**属性升级到它们所属的程序集。</span><span class="sxs-lookup"><span data-stu-id="f5914-136">The ALink tool then promotes these **DebuggableAttribute** attributes from each module to the assembly they become a part of.</span></span> <span data-ttu-id="f5914-137">如果存在冲突，则 ALink 操作将失败。</span><span class="sxs-lookup"><span data-stu-id="f5914-137">If there's a conflict, the ALink operation fails.</span></span>

> [!NOTE]
> <span data-ttu-id="f5914-138">在 .NET Framework 1.0 版本中，当指定 /clr 和 /Zi 编译器选项时，Microsoft Visual C++ 编译器将添加 DebuggableAttribute。</span><span class="sxs-lookup"><span data-stu-id="f5914-138">In version 1.0 of the .NET Framework, the Microsoft Visual C++ compiler adds the **DebuggableAttribute** when the **/clr** and **/Zi** compiler options are specified.</span></span> <span data-ttu-id="f5914-139">在 .NET Framework 版本1.1 中，你必须在代码中手动添加**DebuggableAttribute** ，或使用 **/ASSEMBLYDEBUG**链接器选项。</span><span class="sxs-lookup"><span data-stu-id="f5914-139">In version 1.1 of the .NET Framework, you must either add the **DebuggableAttribute** manually in your code or use the **/ASSEMBLYDEBUG** linker option.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5914-140">请参阅</span><span class="sxs-lookup"><span data-stu-id="f5914-140">See also</span></span>

- [<span data-ttu-id="f5914-141">调试、跟踪和分析</span><span class="sxs-lookup"><span data-stu-id="f5914-141">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="f5914-142">启用 JIT 附加调试</span><span class="sxs-lookup"><span data-stu-id="f5914-142">Enabling JIT-Attach Debugging</span></span>](enabling-jit-attach-debugging.md)
- <span data-ttu-id="f5914-143">[启用分析](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f5914-143">[Enabling Profiling](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s5ec0es1(v=vs.100))</span></span>
