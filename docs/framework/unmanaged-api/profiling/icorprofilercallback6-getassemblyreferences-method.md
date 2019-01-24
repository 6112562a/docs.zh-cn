---
title: ICorProfilerCallback6::GetAssemblyReferences 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3b63756fd300dc300932d070e451d2d072adc6e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621404"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a><span data-ttu-id="38f04-102">ICorProfilerCallback6::GetAssemblyReferences 方法</span><span class="sxs-lookup"><span data-stu-id="38f04-102">ICorProfilerCallback6::GetAssemblyReferences Method</span></span>
<span data-ttu-id="38f04-103">[仅在 .NET Framework 4.5.2 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="38f04-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="38f04-104">当公共语言运行时执行程序集引用闭包审核时，通知探查器程序集正处于非常早期的加载阶段。</span><span class="sxs-lookup"><span data-stu-id="38f04-104">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38f04-105">语法</span><span class="sxs-lookup"><span data-stu-id="38f04-105">Syntax</span></span>  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38f04-106">参数</span><span class="sxs-lookup"><span data-stu-id="38f04-106">Parameters</span></span>  
 `wszAssemblyPath`  
 <span data-ttu-id="38f04-107">[in] 元数据将发生修改的程序集的路径和名称。</span><span class="sxs-lookup"><span data-stu-id="38f04-107">[in] The path and name of the assembly whose metadata will be modified.</span></span>  
  
 `pAsmRefProvider`  
 <span data-ttu-id="38f04-108">[in]指向的地址的指针[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)接口指定的程序集引用添加。</span><span class="sxs-lookup"><span data-stu-id="38f04-108">[in] A pointer to the address of an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface that specifies the assembly references to add.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38f04-109">返回值</span><span class="sxs-lookup"><span data-stu-id="38f04-109">Return Value</span></span>  
 <span data-ttu-id="38f04-110">将忽略此回调的返回值。</span><span class="sxs-lookup"><span data-stu-id="38f04-110">Return values from this callback are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38f04-111">备注</span><span class="sxs-lookup"><span data-stu-id="38f04-111">Remarks</span></span>  
 <span data-ttu-id="38f04-112">通过设置控制此回调[COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)时调用事件掩码标志[ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="38f04-112">This callback is controlled by setting the [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span> <span data-ttu-id="38f04-113">如果探查器注册[ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回调方法中，运行时将传递的路径和名称的程序集加载，以及一个指向[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)到该方法的接口对象。</span><span class="sxs-lookup"><span data-stu-id="38f04-113">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="38f04-114">然后，探查器可以调用[icorprofilerassemblyreferenceprovider:: Addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)方法替换`COR_PRF_ASSEMBLY_REFERENCE_INFO`它打算从中指定的程序集引用每个目标程序集的对象`GetAssemblyReferences`回调。</span><span class="sxs-lookup"><span data-stu-id="38f04-114">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="38f04-115">仅当探查器必须修改程序集的元数据以添加程序集引用时，才使用 `GetAssemblyReferences` 回调。</span><span class="sxs-lookup"><span data-stu-id="38f04-115">Use the `GetAssemblyReferences` callback only if the profiler has to modify an assembly's metadata to add assembly references.</span></span> <span data-ttu-id="38f04-116">(但请注意，在中完成的程序集的元数据的实际修改[icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回调方法。)探查器应该实现 `GetAssemblyReferences` 回调方法，从而通知公共语言运行时 (CLR)：将在加载完模块后添加程序集引用。</span><span class="sxs-lookup"><span data-stu-id="38f04-116">(But note that the actual modification of an assembly's metadata is done in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)callback method.) The profiler should implement the `GetAssemblyReferences` callback method to inform the common language runtime (CLR) that assembly references will be added when the module has been loaded.</span></span>  <span data-ttu-id="38f04-117">这有助于确保即使探查器打算以后修改元数据程序集引用，CLR 在此早期阶段作出的程序集共享决策也会保持有效。</span><span class="sxs-lookup"><span data-stu-id="38f04-117">This helps ensure that assembly sharing decisions made by the CLR during this early stage remain valid although the profiler plans to modify the metadata assembly references later.</span></span>  <span data-ttu-id="38f04-118">这可以避免一些由于探查器元数据修改而导致 `SECURITY_E_INCOMPATIBLE_SHARE` 错误的实例。</span><span class="sxs-lookup"><span data-stu-id="38f04-118">This can avoid some instances in which profiler metadata modifications cause an `SECURITY_E_INCOMPATIBLE_SHARE` error.</span></span>  
  
 <span data-ttu-id="38f04-119">探查器使用[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)提供的此方法可添加到 CLR 程序集引用闭包审核器程序集引用的对象。</span><span class="sxs-lookup"><span data-stu-id="38f04-119">The profiler uses the [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) object provided by this method to add assembly references to the CLR assembly reference closure walker.</span></span>  <span data-ttu-id="38f04-120">[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)对象应仅从内部此回调中使用。</span><span class="sxs-lookup"><span data-stu-id="38f04-120">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) object should be used only from within this callback.</span></span> <span data-ttu-id="38f04-121">调用[icorprofilerassemblyreferenceprovider:: Addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)从此回调的方法不会导致在修改后的元数据，但仅在修改后的程序集引用闭包审核。</span><span class="sxs-lookup"><span data-stu-id="38f04-121">Calls to the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method from this callback don't result in modified metadata, but only in a modified assembly reference closure walk.</span></span> <span data-ttu-id="38f04-122">探查器仍将需要使用[IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)对象中显式添加程序集引用[icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回调的引用程序集，即使它实现`GetAssemblyReferences`回调。</span><span class="sxs-lookup"><span data-stu-id="38f04-122">The profiler will still have to use an [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) object to explicitly add assembly references from within the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback for the referencing assembly, even if it implements the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="38f04-123">探查器应准备好接收重复调用此回调到同一个程序集，并为每个此类重复调用应完全相同地响应 (一组相同的从而[ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)调用)。</span><span class="sxs-lookup"><span data-stu-id="38f04-123">The profiler should be prepared to receive duplicate calls to this callback for the same assembly, and should respond identically for each such duplicate call (by making the same set of [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) calls).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38f04-124">要求</span><span class="sxs-lookup"><span data-stu-id="38f04-124">Requirements</span></span>  
 <span data-ttu-id="38f04-125">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="38f04-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38f04-126">**标头：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="38f04-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="38f04-127">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38f04-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38f04-128">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38f04-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f04-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="38f04-129">See also</span></span>
- [<span data-ttu-id="38f04-130">ICorProfilerCallback6 接口</span><span class="sxs-lookup"><span data-stu-id="38f04-130">ICorProfilerCallback6 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)
- [<span data-ttu-id="38f04-131">ModuleLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="38f04-131">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="38f04-132">COR_PRF_ASSEMBLY_REFERENCE_INFO 结构</span><span class="sxs-lookup"><span data-stu-id="38f04-132">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
- [<span data-ttu-id="38f04-133">ICorProfilerAssemblyReferenceProvider 接口</span><span class="sxs-lookup"><span data-stu-id="38f04-133">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
