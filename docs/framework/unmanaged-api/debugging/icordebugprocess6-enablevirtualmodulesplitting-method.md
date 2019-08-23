---
title: ICorDebugProcess6::EnableVirtualModuleSplitting 方法
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bd06dd3f58a1f74fbdb5ec61c4896f5c1696856
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931060"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a><span data-ttu-id="594c0-102">ICorDebugProcess6::EnableVirtualModuleSplitting 方法</span><span class="sxs-lookup"><span data-stu-id="594c0-102">ICorDebugProcess6::EnableVirtualModuleSplitting Method</span></span>
<span data-ttu-id="594c0-103">启用或禁用虚拟模块拆分。</span><span class="sxs-lookup"><span data-stu-id="594c0-103">Enables or disables virtual module splitting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="594c0-104">语法</span><span class="sxs-lookup"><span data-stu-id="594c0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="594c0-105">参数</span><span class="sxs-lookup"><span data-stu-id="594c0-105">Parameters</span></span>  
 `enableSplitting`  
 <span data-ttu-id="594c0-106">`true` 来启用虚拟模块拆分；`false` 来将其禁用。</span><span class="sxs-lookup"><span data-stu-id="594c0-106">`true` to enable virtual module splitting; `false` to disable it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="594c0-107">备注</span><span class="sxs-lookup"><span data-stu-id="594c0-107">Remarks</span></span>  
 <span data-ttu-id="594c0-108">虚拟模块拆分会导致[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)识别在生成过程中合并在一起的模块, 并将它们显示为一组单独的模块, 而不是单个大模块。</span><span class="sxs-lookup"><span data-stu-id="594c0-108">Virtual module splitting causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) to recognize modules that were merged together during the build process and present them as a group of separate modules rather than a single large module.</span></span> <span data-ttu-id="594c0-109">执行此操作将更改以下所述的各种[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)方法的行为。</span><span class="sxs-lookup"><span data-stu-id="594c0-109">Doing this changes the behavior of various [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods described below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="594c0-110">此方法仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="594c0-110">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="594c0-111">可随时调用方法并更改 `enableSplitting` 值。</span><span class="sxs-lookup"><span data-stu-id="594c0-111">This method can be called and the value of `enableSplitting` can be changed at any time.</span></span> <span data-ttu-id="594c0-112">它不会在[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)对象中产生任何有状态的功能更改, 而不是在调用[虚拟模块拆分和非托管调试 api](#APIs)部分中列出的方法的行为。</span><span class="sxs-lookup"><span data-stu-id="594c0-112">It does not cause any stateful functional changes in an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object, other than altering the behavior of the methods listed in the [Virtual module splitting and the unmanaged debugging APIs](#APIs) section at the time they are called.</span></span> <span data-ttu-id="594c0-113">调用那些方法时，使用虚拟模块确实会导致性能显著下降。</span><span class="sxs-lookup"><span data-stu-id="594c0-113">Using virtual modules does incur a performance penalty when calling those methods.</span></span> <span data-ttu-id="594c0-114">此外, 可能还需要对虚拟化的元数据进行大量的内存中缓存, 才能正确实现[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) api, 并且即使在关闭虚拟模块拆分后, 这些缓存也会保留。</span><span class="sxs-lookup"><span data-stu-id="594c0-114">In addition, significant in-memory caching of the virtualized metadata may be required to correctly implement the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) APIs, and these caches may be retained even after virtual module splitting has been turned off.</span></span>  
  
## <a name="terminology"></a><span data-ttu-id="594c0-115">术语</span><span class="sxs-lookup"><span data-stu-id="594c0-115">Terminology</span></span>  
 <span data-ttu-id="594c0-116">描述虚拟模块拆分时会用到下列术语：</span><span class="sxs-lookup"><span data-stu-id="594c0-116">The following terms are used when describing virtual module splitting:</span></span>  
  
 <span data-ttu-id="594c0-117">容器模块，即容器</span><span class="sxs-lookup"><span data-stu-id="594c0-117">container modules, or containers</span></span>  
 <span data-ttu-id="594c0-118">聚合模块。</span><span class="sxs-lookup"><span data-stu-id="594c0-118">The aggregate modules.</span></span>  
  
 <span data-ttu-id="594c0-119">子模块，即虚拟模块</span><span class="sxs-lookup"><span data-stu-id="594c0-119">sub-modules, or virtual modules</span></span>  
 <span data-ttu-id="594c0-120">在容器中发现的各模块。</span><span class="sxs-lookup"><span data-stu-id="594c0-120">The modules found in a container.</span></span>  
  
 <span data-ttu-id="594c0-121">普通模块</span><span class="sxs-lookup"><span data-stu-id="594c0-121">regular modules</span></span>  
 <span data-ttu-id="594c0-122">未在生成过程中合并的模块。</span><span class="sxs-lookup"><span data-stu-id="594c0-122">Modules that were not merged at build time.</span></span> <span data-ttu-id="594c0-123">它们既不是容器模块也不是子模块。</span><span class="sxs-lookup"><span data-stu-id="594c0-123">They are neither container modules nor sub-modules.</span></span>  
  
 <span data-ttu-id="594c0-124">容器模块和子模块都由 ICorDebugModule 接口对象表示。</span><span class="sxs-lookup"><span data-stu-id="594c0-124">Both container modules and sub-modules are represented by ICorDebugModule interface objects.</span></span> <span data-ttu-id="594c0-125">但是, 在每种情况下, 接口的行为稍有不同, 如\<> 部分的 x-引用部分所述。</span><span class="sxs-lookup"><span data-stu-id="594c0-125">However, the behavior of the interface is slightly different in each case, as the \<x-ref to section> section describes.</span></span>  
  
## <a name="modules-and-assemblies"></a><span data-ttu-id="594c0-126">模块和程序集</span><span class="sxs-lookup"><span data-stu-id="594c0-126">Modules and assemblies</span></span>  
 <span data-ttu-id="594c0-127">在程序集合并的情况下，多模块程序集不受支持，因此模块和程序集之间存在一对一的关系。</span><span class="sxs-lookup"><span data-stu-id="594c0-127">Multi-module assemblies are not supported for assembly merging scenarios, so there is a one-to-one relationship between a module and an assembly.</span></span> <span data-ttu-id="594c0-128">每个 ICorDebugModule 对象无论是表示容器模块还是子模块, 都有相应的 ICorDebugAssembly 对象。</span><span class="sxs-lookup"><span data-stu-id="594c0-128">Each ICorDebugModule object, regardless of whether it represents a container module or a sub-module, has a corresponding ICorDebugAssembly object.</span></span> <span data-ttu-id="594c0-129">[ICorDebugModule:: GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)方法从模块转换为程序集。</span><span class="sxs-lookup"><span data-stu-id="594c0-129">The [ICorDebugModule::GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) method converts from the module to the assembly.</span></span> <span data-ttu-id="594c0-130">若要以其他方向映射, [ICorDebugAssembly:: EnumerateModules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)方法只枚举1个模块。</span><span class="sxs-lookup"><span data-stu-id="594c0-130">To map in the other direction, the [ICorDebugAssembly::EnumerateModules](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md) method enumerates only 1 module.</span></span> <span data-ttu-id="594c0-131">因为在此情况下的程序集和模块形成了一个紧密耦合对，术语程序集和模块变得在很大程度上可以互换。</span><span class="sxs-lookup"><span data-stu-id="594c0-131">Because assembly and module form a tightly coupled pair in this case, the terms assembly and module become largely interchangeable.</span></span>  
  
## <a name="behavioral-differences"></a><span data-ttu-id="594c0-132">行为差异</span><span class="sxs-lookup"><span data-stu-id="594c0-132">Behavioral differences</span></span>  
 <span data-ttu-id="594c0-133">容器模块包含以下行为和特征：</span><span class="sxs-lookup"><span data-stu-id="594c0-133">Container modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="594c0-134">所有组成子模块的元数据合并在一起。</span><span class="sxs-lookup"><span data-stu-id="594c0-134">Their metadata for all of the constituent sub-modules is merged together.</span></span>  
  
- <span data-ttu-id="594c0-135">类型名称可能改变。</span><span class="sxs-lookup"><span data-stu-id="594c0-135">Their type names may be mangled.</span></span>  
  
- <span data-ttu-id="594c0-136">[ICorDebugModule:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)方法返回磁盘上的模块的路径。</span><span class="sxs-lookup"><span data-stu-id="594c0-136">The [ICorDebugModule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) method returns the path to an on-disk module.</span></span>  
  
- <span data-ttu-id="594c0-137">[ICorDebugModule:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)方法返回该图像的大小。</span><span class="sxs-lookup"><span data-stu-id="594c0-137">The [ICorDebugModule::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) method returns the size of that image.</span></span>  
  
- <span data-ttu-id="594c0-138">ICorDebugAssembly3.EnumerateContainedAssemblies 方法列举子模块。</span><span class="sxs-lookup"><span data-stu-id="594c0-138">The ICorDebugAssembly3.EnumerateContainedAssemblies method lists the sub-modules.</span></span>  
  
- <span data-ttu-id="594c0-139">ICorDebugAssembly3.GetContainerAssembly 方法返回 `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="594c0-139">The ICorDebugAssembly3.GetContainerAssembly method returns `S_FALSE`.</span></span>  
  
 <span data-ttu-id="594c0-140">子模块包含以下行为和特征：</span><span class="sxs-lookup"><span data-stu-id="594c0-140">Sub-modules have the following behaviors and characteristics:</span></span>  
  
- <span data-ttu-id="594c0-141">他们具有一套减少的元数据，这些元数据只对应合并的原始程序集。</span><span class="sxs-lookup"><span data-stu-id="594c0-141">They have a reduced set of metadata that corresponds only to the original assembly that was merged.</span></span>  
  
- <span data-ttu-id="594c0-142">元数据名未改变。</span><span class="sxs-lookup"><span data-stu-id="594c0-142">The metadata names are not mangled.</span></span>  
  
- <span data-ttu-id="594c0-143">元数据令牌经生成过程合并之前，不大可能与原始程序集中的令牌匹配。</span><span class="sxs-lookup"><span data-stu-id="594c0-143">Metadata tokens are unlikely to match the tokens in the original assembly before it was merged in the build process.</span></span>  
  
- <span data-ttu-id="594c0-144">[ICorDebugModule:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)方法返回程序集名称, 而不是文件路径。</span><span class="sxs-lookup"><span data-stu-id="594c0-144">The [ICorDebugModule::GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) method returns the assembly name, not a file path.</span></span>  
  
- <span data-ttu-id="594c0-145">[ICorDebugModule:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)方法返回未合并的原始图像大小。</span><span class="sxs-lookup"><span data-stu-id="594c0-145">The [ICorDebugModule::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) method returns the original unmerged image size.</span></span>  
  
- <span data-ttu-id="594c0-146">ICorDebugModule3.EnumerateContainedAssemblies 方法返回 `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="594c0-146">The ICorDebugModule3.EnumerateContainedAssemblies method returns `S_FALSE`.</span></span>  
  
- <span data-ttu-id="594c0-147">ICorDebugAssembly3.GetContainerAssembly 方法返回包含模块。</span><span class="sxs-lookup"><span data-stu-id="594c0-147">The ICorDebugAssembly3.GetContainerAssembly method returns the containing module.</span></span>  
  
## <a name="interfaces-retrieved-from-modules"></a><span data-ttu-id="594c0-148">从模块恢复的接口</span><span class="sxs-lookup"><span data-stu-id="594c0-148">Interfaces retrieved from modules</span></span>  
 <span data-ttu-id="594c0-149">模块可恢复或创建多个接口。</span><span class="sxs-lookup"><span data-stu-id="594c0-149">A variety of interfaces can be created or retrieved from modules.</span></span> <span data-ttu-id="594c0-150">其中包括：</span><span class="sxs-lookup"><span data-stu-id="594c0-150">Some of these include:</span></span>  
  
- <span data-ttu-id="594c0-151">ICorDebugClass 对象, 由[ICorDebugModule:: GetClassFromToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)方法返回。</span><span class="sxs-lookup"><span data-stu-id="594c0-151">An ICorDebugClass object, which is returned by the [ICorDebugModule::GetClassFromToken](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md) method.</span></span>  
  
- <span data-ttu-id="594c0-152">ICorDebugAssembly 对象, 由[ICorDebugModule:: GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)方法返回。</span><span class="sxs-lookup"><span data-stu-id="594c0-152">An ICorDebugAssembly object, which is returned by the [ICorDebugModule::GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) method.</span></span>  
  
 <span data-ttu-id="594c0-153">这些对象始终由[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)缓存, 它们具有相同的指针标识, 无论是从容器模块还是子模块中创建或查询它们。</span><span class="sxs-lookup"><span data-stu-id="594c0-153">These objects are always cached by [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md), and they will have the same pointer identity regardless of whether they were created or queried from the container module or a sub-module.</span></span> <span data-ttu-id="594c0-154">子模块提供了这些缓存对象的筛选视图，而非包含各自副本的单独缓存。</span><span class="sxs-lookup"><span data-stu-id="594c0-154">The sub-module provides a filtered view of these cached objects, not a separate cache with its own copies.</span></span>  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a><span data-ttu-id="594c0-155">虚拟模块拆分和未托管调试 API</span><span class="sxs-lookup"><span data-stu-id="594c0-155">Virtual module splitting and the unmanaged debugging APIs</span></span>  
 <span data-ttu-id="594c0-156">下表显示了虚拟模块拆分如何影响未托管调试 API 中的其他方法的行为。</span><span class="sxs-lookup"><span data-stu-id="594c0-156">The following table shows how virtual module splitting affects the behavior of other methods in the unmanaged debugging API.</span></span>  
  
|<span data-ttu-id="594c0-157">方法</span><span class="sxs-lookup"><span data-stu-id="594c0-157">Method</span></span>|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[<span data-ttu-id="594c0-158">ICorDebugFunction::GetModule</span><span class="sxs-lookup"><span data-stu-id="594c0-158">ICorDebugFunction::GetModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|<span data-ttu-id="594c0-159">返回最初定义该功能的子模块</span><span class="sxs-lookup"><span data-stu-id="594c0-159">Returns the sub-module this function was originally defined in</span></span>|<span data-ttu-id="594c0-160">返回该功能合并到的容器模块</span><span class="sxs-lookup"><span data-stu-id="594c0-160">Returns the container module this function was merged into</span></span>|  
|[<span data-ttu-id="594c0-161">ICorDebugClass::GetModule</span><span class="sxs-lookup"><span data-stu-id="594c0-161">ICorDebugClass::GetModule</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="594c0-162">返回最初定义该类的子模块。</span><span class="sxs-lookup"><span data-stu-id="594c0-162">Returns the sub-module this class was originally defined in.</span></span>|<span data-ttu-id="594c0-163">返回该类合并到的容器模块。</span><span class="sxs-lookup"><span data-stu-id="594c0-163">Returns the container module this class was merged into.</span></span>|  
|<span data-ttu-id="594c0-164">ICorDebugModuleDebugEvent::GetModule</span><span class="sxs-lookup"><span data-stu-id="594c0-164">ICorDebugModuleDebugEvent::GetModule</span></span>|<span data-ttu-id="594c0-165">返回加载的容器模块。</span><span class="sxs-lookup"><span data-stu-id="594c0-165">Returns the container module that was loaded.</span></span> <span data-ttu-id="594c0-166">不管此设置如何，子模块不会收到加载事件。</span><span class="sxs-lookup"><span data-stu-id="594c0-166">Sub-modules are not given load events regardless of this setting.</span></span>|<span data-ttu-id="594c0-167">返回加载的容器模块。</span><span class="sxs-lookup"><span data-stu-id="594c0-167">Returns the container module that was loaded.</span></span>|  
|[<span data-ttu-id="594c0-168">ICorDebugAppDomain::EnumerateAssemblies</span><span class="sxs-lookup"><span data-stu-id="594c0-168">ICorDebugAppDomain::EnumerateAssemblies</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="594c0-169">返回一组子程序集和普通程序集；不包含容器程序集。</span><span class="sxs-lookup"><span data-stu-id="594c0-169">Returns a list of sub-assemblies and regular assemblies; no container assemblies are included.</span></span> <span data-ttu-id="594c0-170">**注意：** 如果任一容器程序集缺少符号，则其所有的子程序集都不会被枚举。</span><span class="sxs-lookup"><span data-stu-id="594c0-170">**Note:**  If any container assembly is missing symbols, none of its sub-assemblies will be enumerated.</span></span> <span data-ttu-id="594c0-171">如果任一普通程序集缺少符号，则其可能被枚举或不枚举。</span><span class="sxs-lookup"><span data-stu-id="594c0-171">If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|<span data-ttu-id="594c0-172">返回一组子程序集和普通程序集；不包含子程序集。</span><span class="sxs-lookup"><span data-stu-id="594c0-172">Returns a list of container assemblies and regular assemblies; no sub-assemblies are included.</span></span> <span data-ttu-id="594c0-173">**注意：** 如果任一普通程序集缺少符号，则其可能被枚举或不枚举。</span><span class="sxs-lookup"><span data-stu-id="594c0-173">**Note:**  If any regular assembly is missing symbols, it may or may not be enumerated.</span></span>|  
|<span data-ttu-id="594c0-174">[ICorDebugCode:: GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md)(仅当引用 IL 代码时)</span><span class="sxs-lookup"><span data-stu-id="594c0-174">[ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (when referring to IL code only)</span></span>|<span data-ttu-id="594c0-175">返回可能在预合并程序集图像中有效的 IL。</span><span class="sxs-lookup"><span data-stu-id="594c0-175">Returns IL that would be valid in a pre-merge assembly image.</span></span> <span data-ttu-id="594c0-176">具体来说，当包含 IL 的虚拟模块未定义参考类型时，任一内联元数据令牌都可以作为 TypeRef 或 MemberRef 令牌。</span><span class="sxs-lookup"><span data-stu-id="594c0-176">Specifically, any inline metadata tokens will correctly be TypeRef or MemberRef tokens when the types being referred to are not defined in the virtual module containing the IL.</span></span> <span data-ttu-id="594c0-177">可以在对应的 virtual ICorDebugModule 对象的[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)对象中查找这些 TypeRef 或 MemberRef 标记。</span><span class="sxs-lookup"><span data-stu-id="594c0-177">These TypeRef or MemberRef tokens can be looked up in the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object for the corresponding virtual ICorDebugModule object.</span></span>|<span data-ttu-id="594c0-178">返回预合并程序集图像中的 IL。</span><span class="sxs-lookup"><span data-stu-id="594c0-178">Returns the IL in the post-merge assembly image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="594c0-179">要求</span><span class="sxs-lookup"><span data-stu-id="594c0-179">Requirements</span></span>  
 <span data-ttu-id="594c0-180">**适用**请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="594c0-180">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="594c0-181">**标头：** Cordebug.idl, Cordebug.idl</span><span class="sxs-lookup"><span data-stu-id="594c0-181">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="594c0-182">**类库**CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="594c0-182">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="594c0-183">**.NET Framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="594c0-183">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="594c0-184">请参阅</span><span class="sxs-lookup"><span data-stu-id="594c0-184">See also</span></span>

- [<span data-ttu-id="594c0-185">ICorDebugProcess6 接口</span><span class="sxs-lookup"><span data-stu-id="594c0-185">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="594c0-186">调试接口</span><span class="sxs-lookup"><span data-stu-id="594c0-186">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
