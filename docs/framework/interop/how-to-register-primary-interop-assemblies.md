---
title: 如何：注册主互操作程序集
ms.date: 03/30/2017
helpviewer_keywords:
- registering primary interop assemblies
- primary interop assemblies, registering
ms.assetid: 4b2fcf8a-429d-43ce-8334-e026040be8bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08d10e0c1a38201a68d0a043b9f52d5f3eaf2ece
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596119"
---
# <a name="how-to-register-primary-interop-assemblies"></a><span data-ttu-id="2c200-102">如何：注册主互操作程序集</span><span class="sxs-lookup"><span data-stu-id="2c200-102">How to: Register Primary Interop Assemblies</span></span>

<span data-ttu-id="2c200-103">类仅能由 COM 互操作封送，并总是作为接口封送。</span><span class="sxs-lookup"><span data-stu-id="2c200-103">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="2c200-104">在某些情况下用来将该类封送的接口称为类接口。</span><span class="sxs-lookup"><span data-stu-id="2c200-104">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="2c200-105">有关使用选择的接口重写类接口的信息，请参阅 [COM可调用包装器](../../../docs/framework/interop/com-callable-wrapper.md)。</span><span class="sxs-lookup"><span data-stu-id="2c200-105">For information about overriding the class interface with an interface of your choice, see [COM Callable Wrapper](../../../docs/framework/interop/com-callable-wrapper.md).</span></span>

 <span data-ttu-id="2c200-106">尽管任何想要从 .NET Framework 应用程序使用 COM 类型的开发人员都可以生成互操作程序集，但这样做会产生一个问题。</span><span class="sxs-lookup"><span data-stu-id="2c200-106">Although any developer who wants to use COM types from a .NET Framework application can generate an interop assembly, doing so creates a problem.</span></span> <span data-ttu-id="2c200-107">每次一名开发人员导入 COM 类型库并对其进行签名时，该开发人员就创建了一组与另一个开发人员所导入和签名的类型不兼容的唯一类型。</span><span class="sxs-lookup"><span data-stu-id="2c200-107">Each time a developer imports and signs a COM type library, that developer creates a set of unique types that are incompatible with those imported and signed by another developer.</span></span> <span data-ttu-id="2c200-108">此类型不兼容性问题的解决方案是每个开发人员都获取供应商提供并签名的主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="2c200-108">The solution to this type incompatibility problem is for each developer to obtain the vendor-supplied and signed primary interop assembly.</span></span>

 <span data-ttu-id="2c200-109">如果你打算向其他应用程序公开第三方 COM 类型，请始终使用与定义的类型库相同的发布者所提供的主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="2c200-109">If you plan to expose third-party COM types to other applications, always use the primary interop assembly provided by the same publisher as the type library it defines.</span></span> <span data-ttu-id="2c200-110">除了提供有保证的类型兼容性，主互操作程序集通常由供应商自定义以增强互操作性。</span><span class="sxs-lookup"><span data-stu-id="2c200-110">In addition to providing guaranteed type compatibility, primary interop assemblies are often customized by the vendor to enhance interoperability.</span></span>

 <span data-ttu-id="2c200-111">即使你不打算公开第三方 COM 类型，使用主互操作程序集也可以使与 COM 组件进行互操作的任务变得更简单。</span><span class="sxs-lookup"><span data-stu-id="2c200-111">Even if you do not plan to expose third-party COM types, using the primary interop assembly can ease the task of interoperating with COM components.</span></span> <span data-ttu-id="2c200-112">但是，此策略不会提供对供应商可能对主互操作程序集中定义的类型所进行的更改的隔离。</span><span class="sxs-lookup"><span data-stu-id="2c200-112">However, this strategy provides no insulation from changes a vendor might make to types defined in a primary interop assembly.</span></span> <span data-ttu-id="2c200-113">当你的应用程序需要此类隔离时，请生成自己的互操作程序集，而不是使用主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="2c200-113">When your application requires such insulation, generate your own interop assembly instead of using the primary interop assembly.</span></span>

 <span data-ttu-id="2c200-114">必须在开发计算机上注册所有需要的主互操作程序集，然后才能通过 Visual Studio 引用它们。</span><span class="sxs-lookup"><span data-stu-id="2c200-114">You must register all acquired primary interop assemblies on your development computer before you can reference them with Visual Studio.</span></span> <span data-ttu-id="2c200-115">Visual Studio 在你第一次从 COM 类型库引用类型时会查找并使用主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="2c200-115">Visual Studio looks for and uses a primary interop assembly the first time that you reference a type from a COM type library.</span></span> <span data-ttu-id="2c200-116">如果 Visual Studio 找不到与该类型库关联的主互操作程序集，它会提示你获取它，或提出创建一个互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="2c200-116">If Visual Studio cannot locate the primary interop assembly associated with the type library, it prompts you to acquire it or offers to create an interop assembly instead.</span></span> <span data-ttu-id="2c200-117">同样，[类型库导入程序 (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) 也使用注册表来定位主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="2c200-117">Likewise, the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) also uses the registry to locate primary interop assemblies.</span></span>

 <span data-ttu-id="2c200-118">尽管没有必要注册主互操作程序集（除非你打算使用 Visual Studio），但注册可提供两大好处：</span><span class="sxs-lookup"><span data-stu-id="2c200-118">Although it is not necessary to register primary interop assemblies unless you plan to use Visual Studio, registration provides two advantages:</span></span>

-   <span data-ttu-id="2c200-119">在原始类型库的注册表项下清楚地标记已注册的主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="2c200-119">A registered primary interop assembly is clearly marked under the registry key of the original type library.</span></span> <span data-ttu-id="2c200-120">注册是在你的计算机上定位主互操作程序集的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="2c200-120">Registration is the best way for you to locate a primary interop assembly on your computer.</span></span>

-   <span data-ttu-id="2c200-121">如果在将来某个时间你使用 Visual Studio 引用具有未注册的主互操作程序集的类型，可以避免意外地生成和使用新的互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="2c200-121">You can avoid accidentally generating and using a new interop assembly if, at some time in the future, you do use Visual Studio to reference a type for which you have an unregistered primary interop assembly.</span></span>

<span data-ttu-id="2c200-122">使用[程序集注册工具 (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) 注册主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="2c200-122">Use the [Assembly Registration Tool (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) to register a primary interop assembly.</span></span>

## <a name="to-register-a-primary-interop-assembly"></a><span data-ttu-id="2c200-123">注册主互操作程序集</span><span class="sxs-lookup"><span data-stu-id="2c200-123">To register a primary interop assembly</span></span>

1.  <span data-ttu-id="2c200-124">在命令提示符处，键入：</span><span class="sxs-lookup"><span data-stu-id="2c200-124">At the command prompt, type:</span></span>

     <span data-ttu-id="2c200-125">regasm assemblyname</span><span class="sxs-lookup"><span data-stu-id="2c200-125">**regasm** *assemblyname*</span></span>

     <span data-ttu-id="2c200-126">在此命令中，assemblyname 是已注册的程序集的文件名。</span><span class="sxs-lookup"><span data-stu-id="2c200-126">In this command, *assemblyname* is the file name of the assembly that is registered.</span></span> <span data-ttu-id="2c200-127">Regasm.exe 会在与原始类型库相同的注册表项下为主互操作程序集添加一个条目。</span><span class="sxs-lookup"><span data-stu-id="2c200-127">Regasm.exe adds an entry for the primary interop assembly under the same registry key as the original type library.</span></span>

## <a name="example"></a><span data-ttu-id="2c200-128">示例</span><span class="sxs-lookup"><span data-stu-id="2c200-128">Example</span></span>
 <span data-ttu-id="2c200-129">下列示例注册 `CompanyA.UtilLib.dll` 主互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="2c200-129">The following example registers the `CompanyA.UtilLib.dll` primary interop assembly.</span></span>

```console
regasm CompanyA.UtilLib.dll
```

## <a name="see-also"></a><span data-ttu-id="2c200-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="2c200-130">See also</span></span>

- <span data-ttu-id="2c200-131">[用主互操作程序集编程](https://msdn.microsoft.com/library/306fa1d6-0703-4004-9e93-d0a57f1be81e(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2c200-131">[Programming with Primary Interop Assemblies](https://msdn.microsoft.com/library/306fa1d6-0703-4004-9e93-d0a57f1be81e(v=vs.100))</span></span>
- <span data-ttu-id="2c200-132">[定位主互操作程序集](https://msdn.microsoft.com/library/d6768e4b-cd80-414d-a4f8-05d979eb393b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2c200-132">[Locating Primary Interop Assemblies](https://msdn.microsoft.com/library/d6768e4b-cd80-414d-a4f8-05d979eb393b(v=vs.100))</span></span>
- <span data-ttu-id="2c200-133">[重新分发主互操作程序集](https://msdn.microsoft.com/library/e76384f0-d631-474c-bdbd-13884cba0265(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2c200-133">[Redistributing Primary Interop Assemblies](https://msdn.microsoft.com/library/e76384f0-d631-474c-bdbd-13884cba0265(v=vs.100))</span></span>