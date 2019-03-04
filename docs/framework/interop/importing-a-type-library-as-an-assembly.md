---
title: 将类型库当作程序集导入
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- type metadata
- custom wrappers
- metadata
- exposing COM components to .NET Framework
- Type Library Importer
- interoperation with unmanaged code, importing type library
- interoperation with unmanaged code, exposing COM components
- type libraries
- TypeLibConverter class, importing type library as assembly
- COM interop, importing type library
- COM interop, exposing COM components
ms.assetid: d1898229-cd40-426e-a275-f3eb65fbc79f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 043fe74f66635c30f12555efb9ccc9415e200ec3
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835234"
---
# <a name="importing-a-type-library-as-an-assembly"></a><span data-ttu-id="383d0-102">将类型库当作程序集导入</span><span class="sxs-lookup"><span data-stu-id="383d0-102">Importing a Type Library as an Assembly</span></span>
<span data-ttu-id="383d0-103">COM 类型定义通常位于类型库中。</span><span class="sxs-lookup"><span data-stu-id="383d0-103">COM type definitions usually reside in a type library.</span></span> <span data-ttu-id="383d0-104">而符合 CLS 的编译器则在程序集中生成类型元数据。</span><span class="sxs-lookup"><span data-stu-id="383d0-104">In contrast, CLS-compliant compilers produce type metadata in an assembly.</span></span> <span data-ttu-id="383d0-105">类型信息的这两种来源具有很大的区别。</span><span class="sxs-lookup"><span data-stu-id="383d0-105">The two sources of type information are quite different.</span></span> <span data-ttu-id="383d0-106">本主题将说明从类型库中生成元数据的技术。</span><span class="sxs-lookup"><span data-stu-id="383d0-106">This topic describes techniques for generating metadata from a type library.</span></span> <span data-ttu-id="383d0-107">生成的程序集称为互操作程序集，其中包含的类型信息允许 .NET Framework 应用程序使用 COM 类型。</span><span class="sxs-lookup"><span data-stu-id="383d0-107">The resulting assembly is called an interop assembly, and the type information it contains enables .NET Framework applications to use COM types.</span></span>  
  
 <span data-ttu-id="383d0-108">可通过两种方式将此类型信息提供给应用程序：</span><span class="sxs-lookup"><span data-stu-id="383d0-108">There are two ways to make this type information available to your application:</span></span>  
  
-   <span data-ttu-id="383d0-109">使用仅设计时互操作程序集：从 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 开始，可以指示编译器将类型信息从互操作程序集嵌入到可执行文件中。</span><span class="sxs-lookup"><span data-stu-id="383d0-109">Using design-time-only interop assemblies: Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can instruct the compiler to embed type information from the interop assembly into your executable.</span></span> <span data-ttu-id="383d0-110">编译器只嵌入应用程序使用的类型信息。</span><span class="sxs-lookup"><span data-stu-id="383d0-110">The compiler embeds only the type information that your application uses.</span></span> <span data-ttu-id="383d0-111">无需将互操作程序集与应用程序一起部署。</span><span class="sxs-lookup"><span data-stu-id="383d0-111">You do not have to deploy the interop assembly with your application.</span></span> <span data-ttu-id="383d0-112">这是推荐采用的方法。</span><span class="sxs-lookup"><span data-stu-id="383d0-112">This is the recommended technique.</span></span>  
  
-   <span data-ttu-id="383d0-113">部署互操作程序集：创建对互操作程序集的标准引用。</span><span class="sxs-lookup"><span data-stu-id="383d0-113">Deploying interop assemblies: You can create a standard reference to the interop assembly.</span></span> <span data-ttu-id="383d0-114">这种情况下，互操作程序集必须与应用程序一起部署。</span><span class="sxs-lookup"><span data-stu-id="383d0-114">In this case, the interop assembly must be deployed with your application.</span></span> <span data-ttu-id="383d0-115">如果使用此方法且不使用专有 COM 组件，请始终引用由打算并入托管代码中的 COM 组件的创建者发布的主互操作程序集 (PIA)。</span><span class="sxs-lookup"><span data-stu-id="383d0-115">If you employ this technique, and you are not using a private COM component, always reference the primary interop assembly (PIA) published by the author of the COM component you intend to incorporate in your managed code.</span></span> <span data-ttu-id="383d0-116">有关生成和使用主互操作程序集的详细信息，请参阅[主互操作程序集](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="383d0-116">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).</span></span>  
  
 <span data-ttu-id="383d0-117">使用仅设计时互操作程序集时，可以嵌入 COM 组件创建者发布的主互操作程序集中的类型信息。</span><span class="sxs-lookup"><span data-stu-id="383d0-117">When you use design-time-only interop assemblies, you can embed type information from the primary interop assembly published by the author of the COM component.</span></span> <span data-ttu-id="383d0-118">但是，无需将主互操作程序集与应用程序一起部署。</span><span class="sxs-lookup"><span data-stu-id="383d0-118">However, you do not have to deploy the primary interop assembly with your application.</span></span>  
  
 <span data-ttu-id="383d0-119">使用仅设计时互操作程序集可以缩减应用程序的大小，因为大部分应用程序不会用到 COM 组件的所有功能。</span><span class="sxs-lookup"><span data-stu-id="383d0-119">Using design-time-only interop assemblies reduces the size of your application, because most applications do not use all the features of a COM component.</span></span> <span data-ttu-id="383d0-120">编译器在嵌入类型信息时效率非常高，如果应用程序只使用 COM 接口上的部分方法，则编译器不嵌入未使用的方法。</span><span class="sxs-lookup"><span data-stu-id="383d0-120">The compiler is very efficient when it embeds type information; if your application uses only some of the methods on a COM interface, the compiler does not embed the unused methods.</span></span> <span data-ttu-id="383d0-121">具有嵌入的类型信息的应用程序与另一个此类应用程序交互时，或者与一个使用主互操作程序集的应用程序交互时，公共语言运行时使用类型等效规则来确定同名的两个类型是否表示相同的 COM 类型。</span><span class="sxs-lookup"><span data-stu-id="383d0-121">When an application that has embedded type information interacts with another such application, or interacts with an application that uses a primary interop assembly, the common language runtime uses type equivalence rules to determine whether two types with the same name represent the same COM type.</span></span> <span data-ttu-id="383d0-122">使用 COM 对象不需要知道这些规则。</span><span class="sxs-lookup"><span data-stu-id="383d0-122">You do not have to know these rules to use COM objects.</span></span> <span data-ttu-id="383d0-123">但是，若对这些规则感兴趣，请参阅[类型等效性和嵌入的互操作类型](../../../docs/framework/interop/type-equivalence-and-embedded-interop-types.md)。</span><span class="sxs-lookup"><span data-stu-id="383d0-123">However, if you are interested in the rules, see [Type Equivalence and Embedded Interop Types](../../../docs/framework/interop/type-equivalence-and-embedded-interop-types.md).</span></span>  
  
## <a name="generating-metadata"></a><span data-ttu-id="383d0-124">生成元数据</span><span class="sxs-lookup"><span data-stu-id="383d0-124">Generating Metadata</span></span>  
 <span data-ttu-id="383d0-125">COM 类型库可以是扩展名名 .tlb 的独立文件，例如 Loanlib.tlb。</span><span class="sxs-lookup"><span data-stu-id="383d0-125">COM type libraries can be stand-alone files that have a .tlb extension, such as Loanlib.tlb.</span></span> <span data-ttu-id="383d0-126">部分类型库嵌入在 .dll 或 .exe 文件的资源部分中。</span><span class="sxs-lookup"><span data-stu-id="383d0-126">Some type libraries are embedded in the resource section of a .dll or .exe file.</span></span> <span data-ttu-id="383d0-127">类型库信息的其它来源为 .olb 和 .ocx 文件。</span><span class="sxs-lookup"><span data-stu-id="383d0-127">Other sources of type library information are .olb and .ocx files.</span></span>  
  
 <span data-ttu-id="383d0-128">找到包含目标 COM 类型的实现的类型库后，可以通过下列选项来生成包含类型元数据的互操作程序集：</span><span class="sxs-lookup"><span data-stu-id="383d0-128">After you locate the type library that contains the implementation of your target COM type, you have the following options for generating an interop assembly containing type metadata:</span></span>  
  
-   <span data-ttu-id="383d0-129">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="383d0-129">Visual Studio</span></span>  
  
     <span data-ttu-id="383d0-130">Visual Studio 将类型库中的 COM 类型自动转换为程序集中的元数据。</span><span class="sxs-lookup"><span data-stu-id="383d0-130">Visual Studio automatically converts COM types in a type library to metadata in an assembly.</span></span> <span data-ttu-id="383d0-131">有关说明，请参阅[如何：添加对类型库的引用](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="383d0-131">For instructions, see [How to: Add References to Type Libraries](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md).</span></span>  
  
-   [<span data-ttu-id="383d0-132">类型库导入程序 (Tlbimp.exe)</span><span class="sxs-lookup"><span data-stu-id="383d0-132">Type Library Importer (Tlbimp.exe)</span></span>](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
  
     <span data-ttu-id="383d0-133">类型库导入程序提供命令行选项，用于调整生成的互操作文件中的元数据、从现有类型库导入类型以及生成互操作程序和命名空间。</span><span class="sxs-lookup"><span data-stu-id="383d0-133">The Type Library Importer provides command-line options to adjust metadata in the resulting interop file, imports types from an existing type library, and generates an interop assembly and a namespace.</span></span> <span data-ttu-id="383d0-134">有关说明，请参阅[如何：从类型库生成互操作程序集](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)。</span><span class="sxs-lookup"><span data-stu-id="383d0-134">For instructions, see [How to: Generate Interop Assemblies from Type Libraries](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
-   <span data-ttu-id="383d0-135"><xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> 类</span><span class="sxs-lookup"><span data-stu-id="383d0-135"><xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> class</span></span>  
  
     <span data-ttu-id="383d0-136">此类提供将类型库中的组件类和接口转换为程序集中的元数据的方法。</span><span class="sxs-lookup"><span data-stu-id="383d0-136">This class provides methods to convert coclasses and interfaces in a type library to metadata within an assembly.</span></span> <span data-ttu-id="383d0-137">它生成和 Tlbimp.exe 相同的元数据输出。</span><span class="sxs-lookup"><span data-stu-id="383d0-137">It produces the same metadata output as Tlbimp.exe.</span></span> <span data-ttu-id="383d0-138">但与 Tlbimp.exe 不同的是，<xref:System.Runtime.InteropServices.TypeLibConverter> 类可以将内存中类型库转换为元数据。</span><span class="sxs-lookup"><span data-stu-id="383d0-138">However, unlike Tlbimp.exe, the <xref:System.Runtime.InteropServices.TypeLibConverter> class can convert an in-memory type library to metadata.</span></span>  
  
-   <span data-ttu-id="383d0-139">自定义包装器</span><span class="sxs-lookup"><span data-stu-id="383d0-139">Custom wrappers</span></span>  
  
     <span data-ttu-id="383d0-140">类型库不可用或不正确时，一种可选的做法是在托管源代码中创建类或接口的重复定义。</span><span class="sxs-lookup"><span data-stu-id="383d0-140">When a type library is unavailable or incorrect, one option is to create a duplicate definition of the class or interface in managed source code.</span></span> <span data-ttu-id="383d0-141">然后，使用面向运行时的编译器来编译源代码，生成程序集中的元数据。</span><span class="sxs-lookup"><span data-stu-id="383d0-141">You then compile the source code with a compiler that targets the runtime to produce metadata in an assembly.</span></span>  
  
     <span data-ttu-id="383d0-142">要手动定义 COM 类型，必须具有对以下项的访问权限：</span><span class="sxs-lookup"><span data-stu-id="383d0-142">To define COM types manually, you must have access to the following items:</span></span>  
  
    -   <span data-ttu-id="383d0-143">所定义的组件类和接口的精确描述。</span><span class="sxs-lookup"><span data-stu-id="383d0-143">Precise descriptions of the coclasses and interfaces being defined.</span></span>  
  
    -   <span data-ttu-id="383d0-144">可生成正确 .NET Framework 类定义的编译器，例如 C# 编译器。</span><span class="sxs-lookup"><span data-stu-id="383d0-144">A compiler, such as the C# compiler, that can generate the appropriate .NET Framework class definitions.</span></span>  
  
    -   <span data-ttu-id="383d0-145">有关类型库到程序集转换规则的知识。</span><span class="sxs-lookup"><span data-stu-id="383d0-145">Knowledge of the type library-to-assembly conversion rules.</span></span>  
  
     <span data-ttu-id="383d0-146">编写自定义包装器是一项高级技术。</span><span class="sxs-lookup"><span data-stu-id="383d0-146">Writing a custom wrapper is an advanced technique.</span></span> <span data-ttu-id="383d0-147">有关如何生成自定义包装器的其他信息，请参阅[自定义标准包装器](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="383d0-147">For additional information about how to generate a custom wrapper, see [Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100)).</span></span>  
  
 <span data-ttu-id="383d0-148">有关 COM 互操作导入过程的详细信息，请参阅[有关从类型库转换到程序集的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="383d0-148">For more information about the COM interop import process, see [Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="383d0-149">请参阅</span><span class="sxs-lookup"><span data-stu-id="383d0-149">See also</span></span>
- <xref:System.Runtime.InteropServices.TypeLibConverter>
- [<span data-ttu-id="383d0-150">向 .NET Framework 公开 COM 组件</span><span class="sxs-lookup"><span data-stu-id="383d0-150">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)
- <span data-ttu-id="383d0-151">[有关从类型库转换到程序集的摘要](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="383d0-151">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>
- [<span data-ttu-id="383d0-152">Tlbimp.exe（类型库导入程序）</span><span class="sxs-lookup"><span data-stu-id="383d0-152">Tlbimp.exe (Type Library Importer)</span></span>](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)
- <span data-ttu-id="383d0-153">[自定义标准包装器](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="383d0-153">[Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="383d0-154">[在托管代码中使用 COM 类型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="383d0-154">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="383d0-155">编译互操作项目</span><span class="sxs-lookup"><span data-stu-id="383d0-155">Compiling an Interop Project</span></span>](../../../docs/framework/interop/compiling-an-interop-project.md)
- [<span data-ttu-id="383d0-156">部署互操作应用程序</span><span class="sxs-lookup"><span data-stu-id="383d0-156">Deploying an Interop Application</span></span>](../../../docs/framework/interop/deploying-an-interop-application.md)
- [<span data-ttu-id="383d0-157">如何：添加对类型库的引用</span><span class="sxs-lookup"><span data-stu-id="383d0-157">How to: Add References to Type Libraries</span></span>](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)
- [<span data-ttu-id="383d0-158">如何：从类型库生成互操作程序集</span><span class="sxs-lookup"><span data-stu-id="383d0-158">How to: Generate Interop Assemblies from Type Libraries</span></span>](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)
