---
title: 向 .NET Framework 公开 COM 组件
ms.date: 03/30/2017
helpviewer_keywords:
- exposing COM components to .NET Framework
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: e78b14f1-e487-43cd-9c6d-1a07483f1730
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 230853abf73a368bfcd8b88375c216fdadfc7d46
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567270"
---
# <a name="exposing-com-components-to-the-net-framework"></a><span data-ttu-id="3e1f0-102">向 .NET Framework 公开 COM 组件</span><span class="sxs-lookup"><span data-stu-id="3e1f0-102">Exposing COM Components to the .NET Framework</span></span>
<span data-ttu-id="3e1f0-103">本部分概述向托管代码公开现有 COM 组件所需的步骤。</span><span class="sxs-lookup"><span data-stu-id="3e1f0-103">This section summarizes the process needed to expose an existing COM component to managed code.</span></span> <span data-ttu-id="3e1f0-104">有关编写与 .NET Framework 紧密集成的 COM 服务器的详细信息，请参阅[互操作的设计注意事项](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="3e1f0-104">For details about writing COM servers that tightly integrate with the .NET Framework, see [Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100)).</span></span>
  
 <span data-ttu-id="3e1f0-105">作为中间层业务应用程序或独立功能，现有 COM 组件是托管代码中的宝贵资源。</span><span class="sxs-lookup"><span data-stu-id="3e1f0-105">Existing COM components are valuable resources in managed code as middle-tier business applications or as isolated functionality.</span></span> <span data-ttu-id="3e1f0-106">理想的组件具有主互操作程序集，且完全符合 COM 实施的编程标准。</span><span class="sxs-lookup"><span data-stu-id="3e1f0-106">An ideal component has a primary interop assembly and conforms tightly to the programming standards imposed by COM.</span></span>  
  
#### <a name="to-expose-com-components-to-the-net-framework"></a><span data-ttu-id="3e1f0-107">向 .NET Framework 公开 COM 组件</span><span class="sxs-lookup"><span data-stu-id="3e1f0-107">To expose COM components to the .NET Framework</span></span>  
  
1. <span data-ttu-id="3e1f0-108">[将类型库当作程序集导入](importing-a-type-library-as-an-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="3e1f0-108">[Import a type library as an assembly](importing-a-type-library-as-an-assembly.md).</span></span>  
  
     <span data-ttu-id="3e1f0-109">公共语言运行时需要包括 COM 类型在内的所有类型的元数据。</span><span class="sxs-lookup"><span data-stu-id="3e1f0-109">The common language runtime requires metadata for all types, including COM types.</span></span> <span data-ttu-id="3e1f0-110">有多种方法来获取包含 COM 类型（作为元数据导入）的程序集。</span><span class="sxs-lookup"><span data-stu-id="3e1f0-110">There are several ways to obtain an assembly containing COM types imported as metadata.</span></span>  
  
2. <span data-ttu-id="3e1f0-111">[在托管代码中使用 COM 类型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3e1f0-111">[Use COM types in managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).</span></span>  
  
     <span data-ttu-id="3e1f0-112">可检查 COM 类型、激活实例，并采用在任何托管类型上进行调用的方式在 COM 对象上调用方法。</span><span class="sxs-lookup"><span data-stu-id="3e1f0-112">You can inspect COM types, activate instances, and invoke methods on the COM object the same way you do for any managed type.</span></span>  
  
3. <span data-ttu-id="3e1f0-113">[编译互操作项目](compiling-an-interop-project.md)。</span><span class="sxs-lookup"><span data-stu-id="3e1f0-113">[Compile an interop project](compiling-an-interop-project.md).</span></span>  
  
     <span data-ttu-id="3e1f0-114">Windows SDK 为符合公共语言规范 (CLS) 的多种语言提供编译器，其中包括 Visual Basic、C# 和 C++。</span><span class="sxs-lookup"><span data-stu-id="3e1f0-114">The Windows SDK provides compilers for several languages compliant with the Common Language Specification (CLS), including Visual Basic, C#, and C++.</span></span>  
  
4. <span data-ttu-id="3e1f0-115">[部署互操作应用程序](deploying-an-interop-application.md)。</span><span class="sxs-lookup"><span data-stu-id="3e1f0-115">[Deploy an interop application](deploying-an-interop-application.md).</span></span>  
  
     <span data-ttu-id="3e1f0-116">最好将互操作应用程序部署为全局程序集缓存中具有[强名称](../app-domains/strong-named-assemblies.md)的签名程序集。</span><span class="sxs-lookup"><span data-stu-id="3e1f0-116">Interop applications are best deployed as [strong-named](../app-domains/strong-named-assemblies.md), signed assemblies in the global assembly cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e1f0-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="3e1f0-117">See also</span></span>

- [<span data-ttu-id="3e1f0-118">与非托管代码交互操作</span><span class="sxs-lookup"><span data-stu-id="3e1f0-118">Interoperating with Unmanaged Code</span></span>](index.md)
- <span data-ttu-id="3e1f0-119">[互操作的设计注意事项](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3e1f0-119">[Design Considerations for Interoperation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/61aax4kh(v=vs.100))</span></span>
- [<span data-ttu-id="3e1f0-120">COM 互操作示例：.NET 客户端和 COM 服务器</span><span class="sxs-lookup"><span data-stu-id="3e1f0-120">COM Interop Sample: .NET Client and COM Server</span></span>](com-interop-sample-net-client-and-com-server.md)
- [<span data-ttu-id="3e1f0-121">语言独立性和与语言无关的组件</span><span class="sxs-lookup"><span data-stu-id="3e1f0-121">Language Independence and Language-Independent Components</span></span>](../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="3e1f0-122">Gacutil.exe（全局程序集缓存工具）</span><span class="sxs-lookup"><span data-stu-id="3e1f0-122">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
