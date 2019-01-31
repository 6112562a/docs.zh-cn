---
title: 向 COM 注册程序集
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3ba8cb41244157b1fca0f7e9d345625cc579d0a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494036"
---
# <a name="registering-assemblies-with-com"></a><span data-ttu-id="46c22-102">向 COM 注册程序集</span><span class="sxs-lookup"><span data-stu-id="46c22-102">Registering Assemblies with COM</span></span>
<span data-ttu-id="46c22-103">可运行名为[程序集注册工具 (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) 的命令行工具注册或取消注册与 COM 一起使用的程序集。</span><span class="sxs-lookup"><span data-stu-id="46c22-103">You can run a command-line tool called the [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) to register or unregister an assembly for use with COM.</span></span> <span data-ttu-id="46c22-104">Regasm.exe 将关于类的信息添加到系统注册表，因此 COM 客户端可以透明地使用 .NET Framework 类。</span><span class="sxs-lookup"><span data-stu-id="46c22-104">Regasm.exe adds information about the class to the system registry so COM clients can use the .NET Framework class transparently.</span></span> <span data-ttu-id="46c22-105"><xref:System.Runtime.InteropServices.RegistrationServices> 类提供等效功能。</span><span class="sxs-lookup"><span data-stu-id="46c22-105">The <xref:System.Runtime.InteropServices.RegistrationServices> class provides the equivalent functionality.</span></span>  
  
 <span data-ttu-id="46c22-106">托管组件从 COM 客户端激活前必须在 Windows 注册表中注册。</span><span class="sxs-lookup"><span data-stu-id="46c22-106">A managed component must be registered in the Windows registry before it can be activated from a COM client.</span></span> <span data-ttu-id="46c22-107">下表显示 Regasm.exe 通常添加到 Windows 注册表的项。</span><span class="sxs-lookup"><span data-stu-id="46c22-107">The following table shows the keys that Regasm.exe typically adds to the Windows registry.</span></span> <span data-ttu-id="46c22-108">（000000 表示实际的 GUID 值。）</span><span class="sxs-lookup"><span data-stu-id="46c22-108">(000000 indicates the actual GUID value.)</span></span>  
  
|<span data-ttu-id="46c22-109">GUID</span><span class="sxs-lookup"><span data-stu-id="46c22-109">GUID</span></span>|<span data-ttu-id="46c22-110">说明</span><span class="sxs-lookup"><span data-stu-id="46c22-110">Description</span></span>|<span data-ttu-id="46c22-111">注册表项</span><span class="sxs-lookup"><span data-stu-id="46c22-111">Registry key</span></span>|  
|----------|-----------------|------------------|  
|<span data-ttu-id="46c22-112">CLSID</span><span class="sxs-lookup"><span data-stu-id="46c22-112">CLSID</span></span>|<span data-ttu-id="46c22-113">类标识符</span><span class="sxs-lookup"><span data-stu-id="46c22-113">Class identifier</span></span>|<span data-ttu-id="46c22-114">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="46c22-114">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span></span>|  
|<span data-ttu-id="46c22-115">IID</span><span class="sxs-lookup"><span data-stu-id="46c22-115">IID</span></span>|<span data-ttu-id="46c22-116">接口标识符</span><span class="sxs-lookup"><span data-stu-id="46c22-116">Interface identifier</span></span>|<span data-ttu-id="46c22-117">HKEY_CLASSES_ROOT\Interface\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="46c22-117">HKEY_CLASSES_ROOT\Interface\\{000…000}</span></span>|  
|<span data-ttu-id="46c22-118">LIBID</span><span class="sxs-lookup"><span data-stu-id="46c22-118">LIBID</span></span>|<span data-ttu-id="46c22-119">库标识符</span><span class="sxs-lookup"><span data-stu-id="46c22-119">Library identifier</span></span>|<span data-ttu-id="46c22-120">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="46c22-120">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span></span>|  
|<span data-ttu-id="46c22-121">ProgID</span><span class="sxs-lookup"><span data-stu-id="46c22-121">ProgID</span></span>|<span data-ttu-id="46c22-122">编程标识符</span><span class="sxs-lookup"><span data-stu-id="46c22-122">Programmatic identifier</span></span>|<span data-ttu-id="46c22-123">HKEY_CLASSES_ROOT\000…000</span><span class="sxs-lookup"><span data-stu-id="46c22-123">HKEY_CLASSES_ROOT\000…000</span></span>|  
  
 <span data-ttu-id="46c22-124">HKCR\CLSID\\{0000…0000} 项下，默认值设置为类的 ProgID，并添加了两个新的命名值：类和程序集。</span><span class="sxs-lookup"><span data-stu-id="46c22-124">Under the HKCR\CLSID\\{0000…0000} key, the default value is set to the ProgID of the class, and two new named values, Class and Assembly, are added.</span></span> <span data-ttu-id="46c22-125">运行时从注册表读取程序集值并传递给运行时程序集解析程序。</span><span class="sxs-lookup"><span data-stu-id="46c22-125">The runtime reads the Assembly value from the registry and passes it on to the runtime assembly resolver.</span></span> <span data-ttu-id="46c22-126">程序集解析程序尝试基于程序集信息（如名称和版本号）定位程序集。</span><span class="sxs-lookup"><span data-stu-id="46c22-126">The assembly resolver attempts to locate the assembly, based on assembly information such as the name and version number.</span></span> <span data-ttu-id="46c22-127">为了让程序集解析程序找到程序集，程序集必须位于以下位置中：</span><span class="sxs-lookup"><span data-stu-id="46c22-127">For the assembly resolver to locate an assembly, the assembly has to be in one of the following locations:</span></span>  
  
-   <span data-ttu-id="46c22-128">全局程序集缓存（必须为强名称程序集）。</span><span class="sxs-lookup"><span data-stu-id="46c22-128">The global assembly cache (must be a strong-named assembly).</span></span>  
  
-   <span data-ttu-id="46c22-129">应用程序目录中。</span><span class="sxs-lookup"><span data-stu-id="46c22-129">In the application directory.</span></span> <span data-ttu-id="46c22-130">从应用程序路径加载的程序集只能从应用程序访问。</span><span class="sxs-lookup"><span data-stu-id="46c22-130">Assemblies loaded from the application path are only accessible from that application.</span></span>  
  
-   <span data-ttu-id="46c22-131">沿 /codebase 选项指定的文件路径到 Regasm.exe。</span><span class="sxs-lookup"><span data-stu-id="46c22-131">Along an file path specified with the **/codebase** option to Regasm.exe.</span></span>  
  
 <span data-ttu-id="46c22-132">Regasm.exe 也会在 HKCR\CLSID\\{0000…0000} 项下创建 InProcServer32 项。</span><span class="sxs-lookup"><span data-stu-id="46c22-132">Regasm.exe also creates the InProcServer32 key under the HKCR\CLSID\\{0000…0000} key.</span></span> <span data-ttu-id="46c22-133">项的默认值设置为初始化公共语言运行时 (Mscoree.dll) 的 DLL 的名称。</span><span class="sxs-lookup"><span data-stu-id="46c22-133">The default value for the key is set to the name of the DLL that initializes the common language runtime (Mscoree.dll).</span></span>  
  
## <a name="examining-registry-entries"></a><span data-ttu-id="46c22-134">检查注册表项</span><span class="sxs-lookup"><span data-stu-id="46c22-134">Examining Registry Entries</span></span>  
 <span data-ttu-id="46c22-135">COM 互操作提供标准的类工厂实现以创建任意 .NET Framework 类的实例。</span><span class="sxs-lookup"><span data-stu-id="46c22-135">COM interop provides a standard class factory implementation to create an instance of any .NET Framework class.</span></span> <span data-ttu-id="46c22-136">客户端可以调用托管 DLL 上的“DllGetClassObject”以获取类工厂并创建对象，与使用任何其他 COM 组件相同。</span><span class="sxs-lookup"><span data-stu-id="46c22-136">Clients can call **DllGetClassObject** on the managed DLL to get a class factory and create objects, just as they would with any other COM component.</span></span>  
  
 <span data-ttu-id="46c22-137">关于 `InprocServer32` 子项, 出现在传统 COM 类型库中的对 Mscoree.dll 的引用表示公共语言运行时创建托管对象。</span><span class="sxs-lookup"><span data-stu-id="46c22-137">For the `InprocServer32` subkey, a reference to Mscoree.dll appears in place of a traditional COM type library to indicate that the common language runtime creates the managed object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c22-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="46c22-138">See also</span></span>
- [<span data-ttu-id="46c22-139">向 COM 公开 .NET Framework 组件</span><span class="sxs-lookup"><span data-stu-id="46c22-139">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="46c22-140">如何：从 COM 引用 .NET 类型</span><span class="sxs-lookup"><span data-stu-id="46c22-140">How to: Reference .NET Types from COM</span></span>](how-to-reference-net-types-from-com.md)
- <span data-ttu-id="46c22-141">[调用 .NET 对象](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="46c22-141">[Calling a .NET Object](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))</span></span>
- <span data-ttu-id="46c22-142">[为 COM 访问部署应用程序](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="46c22-142">[Deploying an Application for COM Access](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))</span></span>
