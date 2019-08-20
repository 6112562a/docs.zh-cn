---
title: 部署互操作应用程序
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], interop
- strong-named assemblies, interop applications
- unsigned assemblies
- private assemblies
- exposing COM components to .NET Framework
- interoperation with unmanaged code, deploying applications
- shared assemblies
- COM interop, deploying applications
- interoperation with unmanaged code, exposing COM components
- signed assemblies
- COM interop, exposing COM components
ms.assetid: ea8a403e-ae03-4faa-9d9b-02179ec72992
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 080ef48ade496a55f414b64158a40fe0e551c2aa
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567298"
---
# <a name="deploying-an-interop-application"></a><span data-ttu-id="11ae6-102">部署互操作应用程序</span><span class="sxs-lookup"><span data-stu-id="11ae6-102">Deploying an Interop Application</span></span>
<span data-ttu-id="11ae6-103">互操作应用程序通常包括 .NET 客户端程序集，表示不同 COM 类型库的一个或多个互操作程序集，以及一个或多个已注册的 COM 组件。</span><span class="sxs-lookup"><span data-stu-id="11ae6-103">An interop application typically includes a .NET client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span> <span data-ttu-id="11ae6-104">Visual Studio 和 Windows SDK 提供用于将类型库导入并转换为互操作程序集的工具，如[将类型库作为程序集导入](importing-a-type-library-as-an-assembly.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="11ae6-104">Visual Studio and the Windows SDK provide tools to import and convert a type library to an interop assembly, as discussed in [Importing a Type Library as an Assembly](importing-a-type-library-as-an-assembly.md).</span></span> <span data-ttu-id="11ae6-105">可以通过以下两种方式部署互操作应用程序：</span><span class="sxs-lookup"><span data-stu-id="11ae6-105">There are two ways to deploy an interop application:</span></span>  
  
- <span data-ttu-id="11ae6-106">使用嵌入的互操作类型：从 .NET Framework 4 开始，可以指示编译器将类型信息从互操作程序集嵌入到可执行文件中。</span><span class="sxs-lookup"><span data-stu-id="11ae6-106">By using embedded interop types: Beginning with the .NET Framework 4, you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="11ae6-107">编译器只嵌入应用程序使用的类型信息。</span><span class="sxs-lookup"><span data-stu-id="11ae6-107">The compiler embeds only the type information that your application uses.</span></span> <span data-ttu-id="11ae6-108">无需将互操作程序集与应用程序一起部署。</span><span class="sxs-lookup"><span data-stu-id="11ae6-108">You do not have to deploy the interop assembly with your application.</span></span> <span data-ttu-id="11ae6-109">这是推荐采用的方法。</span><span class="sxs-lookup"><span data-stu-id="11ae6-109">This is the recommended technique.</span></span>  
  
- <span data-ttu-id="11ae6-110">部署互操作程序集：创建对互操作程序集的标准引用。</span><span class="sxs-lookup"><span data-stu-id="11ae6-110">By deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="11ae6-111">这种情况下，互操作程序集必须与应用程序一起部署。</span><span class="sxs-lookup"><span data-stu-id="11ae6-111">In this case, the interop assembly must be deployed with your application.</span></span> <span data-ttu-id="11ae6-112">如果使用此方法且不使用专有 COM 组件，请始终引用由打算并入托管代码中的 COM 组件的创建者发布的主互操作程序集 (PIA)。</span><span class="sxs-lookup"><span data-stu-id="11ae6-112">If you employ this technique, and you are not using a private COM component, always reference the primary interop assembly (PIA) published by the author of the COM component you intend to incorporate in your managed code.</span></span> <span data-ttu-id="11ae6-113">有关生成和使用主互操作程序集的详细信息，请参阅[主互操作程序集](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="11ae6-113">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).</span></span>  
  
 <span data-ttu-id="11ae6-114">如果使用嵌入的互操作类型，则部署过程将既简单又直观。</span><span class="sxs-lookup"><span data-stu-id="11ae6-114">If you use embedded interop types, deployment is simple and straightforward.</span></span> <span data-ttu-id="11ae6-115">无需执行任何特殊操作。</span><span class="sxs-lookup"><span data-stu-id="11ae6-115">There is nothing special you need to do.</span></span> <span data-ttu-id="11ae6-116">本文的其余部分将介绍将应用程序与互操作程序集一起部署的方案。</span><span class="sxs-lookup"><span data-stu-id="11ae6-116">The rest of this article describes the scenarios for deploying interop assemblies with your application.</span></span>  
  
## <a name="deploying-interop-assemblies"></a><span data-ttu-id="11ae6-117">部署互操作程序集</span><span class="sxs-lookup"><span data-stu-id="11ae6-117">Deploying Interop Assemblies</span></span>  
 <span data-ttu-id="11ae6-118">程序集可以具有强名称。</span><span class="sxs-lookup"><span data-stu-id="11ae6-118">Assemblies can have strong names.</span></span> <span data-ttu-id="11ae6-119">具有强名称的程序集包括发布者的公钥，它提供一个唯一标识。</span><span class="sxs-lookup"><span data-stu-id="11ae6-119">A strong-named assembly includes the publisher's public key, which provides a unique identity.</span></span> <span data-ttu-id="11ae6-120">通过[类型库导入程序 (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) 生成的程序集可由发行者使用 /keyfile 选项签名  。</span><span class="sxs-lookup"><span data-stu-id="11ae6-120">Assemblies that are produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md) can be signed by the publisher by using the **/keyfile** option.</span></span> <span data-ttu-id="11ae6-121">可将已签名的程序集安装到全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="11ae6-121">You can install signed assemblies into the global assembly cache.</span></span> <span data-ttu-id="11ae6-122">未签名程序集必须作为专用程序集安装在用户计算机上。</span><span class="sxs-lookup"><span data-stu-id="11ae6-122">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>  
  
### <a name="private-assemblies"></a><span data-ttu-id="11ae6-123">私有程序集</span><span class="sxs-lookup"><span data-stu-id="11ae6-123">Private Assemblies</span></span>  
 <span data-ttu-id="11ae6-124">要安装私用程序集，必须在同一目录结构中安装应用程序可执行文件和包含导入的 COM 类型的互操作程序集。</span><span class="sxs-lookup"><span data-stu-id="11ae6-124">To install an assembly to be used privately, both the application executable and the interop assembly that contains imported COM types must be installed in the same directory structure.</span></span> <span data-ttu-id="11ae6-125">下图显示由 Client1.exe 和 Client2.exe 私用的未签名互操作程序集，二者位于不同的应用程序目录中。</span><span class="sxs-lookup"><span data-stu-id="11ae6-125">The following illustration shows an unsigned interop assembly to be used privately by Client1.exe and Client2.exe, which reside in separate application directories.</span></span> <span data-ttu-id="11ae6-126">此示例中名为 LOANLib.dll 的互操作程序集安装了两次。</span><span class="sxs-lookup"><span data-stu-id="11ae6-126">The interop assembly, which is called LOANLib.dll in this example, is installed twice.</span></span>  
  
 <span data-ttu-id="11ae6-127">![目录结构和 Windows 注册表](./media/deploying-an-interop-application/com-private-deployment.gif "私有部署的目录结构和注册表项")</span><span class="sxs-lookup"><span data-stu-id="11ae6-127">![Directory structure and Windows registry](./media/deploying-an-interop-application/com-private-deployment.gif "Directory structure and registry entries for a private deployment")</span></span>  
  
 <span data-ttu-id="11ae6-128">与应用程序关联的所有 COM 组件都必须安装在 Windows 注册表中。</span><span class="sxs-lookup"><span data-stu-id="11ae6-128">All COM components associated with the application must be installed in the Windows registry.</span></span> <span data-ttu-id="11ae6-129">如果图中的 Client1.exe 和 Client2.exe 安装在不同计算机上，则必须在这两台计算机上注册 COM 组件。</span><span class="sxs-lookup"><span data-stu-id="11ae6-129">If Client1.exe and Client2.exe in the illustration are installed on different computers, you must register the COM components on both computers.</span></span>  
  
### <a name="shared-assemblies"></a><span data-ttu-id="11ae6-130">共享程序集</span><span class="sxs-lookup"><span data-stu-id="11ae6-130">Shared Assemblies</span></span>  
 <span data-ttu-id="11ae6-131">多个应用程序共享的程序集应安装在一个称作全局程序集缓存的集中储存库中。</span><span class="sxs-lookup"><span data-stu-id="11ae6-131">Assemblies that are shared by multiple applications should be installed in a centralized repository called the global assembly cache.</span></span> <span data-ttu-id="11ae6-132">多个 .NET 客户端可访问互操作程序集的同一副本，此程序集在全局程序集缓存中签名并安装在其中。</span><span class="sxs-lookup"><span data-stu-id="11ae6-132">.NET clients can access the same copy of the interop assembly, which is signed and installed in the global assembly cache.</span></span> <span data-ttu-id="11ae6-133">有关生成和使用主互操作程序集的详细信息，请参阅[主互操作程序集](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="11ae6-133">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ae6-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="11ae6-134">See also</span></span>

- [<span data-ttu-id="11ae6-135">向 .NET Framework 公开 COM 组件</span><span class="sxs-lookup"><span data-stu-id="11ae6-135">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="11ae6-136">将类型库作为程序集导入</span><span class="sxs-lookup"><span data-stu-id="11ae6-136">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- <span data-ttu-id="11ae6-137">[在托管代码中使用 COM 类型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="11ae6-137">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="11ae6-138">编译互操作项目</span><span class="sxs-lookup"><span data-stu-id="11ae6-138">Compiling an Interop Project</span></span>](compiling-an-interop-project.md)
