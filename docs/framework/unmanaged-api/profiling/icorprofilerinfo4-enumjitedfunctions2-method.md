---
title: ICorProfilerInfo4::EnumJITedFunctions2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d69b1c0bec89594a148d0d5d501dcab32280a2e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780876"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a><span data-ttu-id="a6a8f-102">ICorProfilerInfo4::EnumJITedFunctions2 方法</span><span class="sxs-lookup"><span data-stu-id="a6a8f-102">ICorProfilerInfo4::EnumJITedFunctions2 Method</span></span>
<span data-ttu-id="a6a8f-103">返回所有先前 JIT 编译和 JIT 重新编译的函数的枚举器。</span><span class="sxs-lookup"><span data-stu-id="a6a8f-103">Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.</span></span> <span data-ttu-id="a6a8f-104">此方法将替换[ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)方法，它不会枚举 JIT 重新编译的 Id。</span><span class="sxs-lookup"><span data-stu-id="a6a8f-104">This method replaces the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which does not enumerate JIT-recompiled IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6a8f-105">语法</span><span class="sxs-lookup"><span data-stu-id="a6a8f-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6a8f-106">参数</span><span class="sxs-lookup"><span data-stu-id="a6a8f-106">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a6a8f-107">[out]一个指向[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)枚举器。</span><span class="sxs-lookup"><span data-stu-id="a6a8f-107">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6a8f-108">备注</span><span class="sxs-lookup"><span data-stu-id="a6a8f-108">Remarks</span></span>  
 <span data-ttu-id="a6a8f-109">此方法可能会与重叠`JITCompilation`如回调[icorprofilercallback:: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="a6a8f-109">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="a6a8f-110">返回的枚举包括值`COR_PRF_FUNCTION::reJitId`字段。</span><span class="sxs-lookup"><span data-stu-id="a6a8f-110">The returned enumeration includes values for the `COR_PRF_FUNCTION::reJitId` field.</span></span> <span data-ttu-id="a6a8f-111">[ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)方法，此方法将替换，不会枚举 JIT 重新编译的 Id，因为`COR_PRF_FUNCTION::reJitId`字段始终设置为 0。</span><span class="sxs-lookup"><span data-stu-id="a6a8f-111">The [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) method, which this method replaces, does not enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is always set to 0.</span></span> <span data-ttu-id="a6a8f-112">`ICorProfilerInfo4::EnumJITedFunctions`方法枚举 JIT 重新编译的 Id，因为`COR_PRF_FUNCTION::reJitId`字段已正确设置。</span><span class="sxs-lookup"><span data-stu-id="a6a8f-112">The `ICorProfilerInfo4::EnumJITedFunctions` method does enumerate JIT-recompiled IDs, because the `COR_PRF_FUNCTION::reJitId` field is set properly.</span></span> <span data-ttu-id="a6a8f-113">请注意， [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)方法可以触发垃圾收集，而[ICorProfilerInfo3::EnumJITedFunctions 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)将不会。</span><span class="sxs-lookup"><span data-stu-id="a6a8f-113">Note that the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method can trigger a garbage collection, whereas [ICorProfilerInfo3::EnumJITedFunctions method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) will not.</span></span>  <span data-ttu-id="a6a8f-114">有关详细信息，请参阅[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a8f-114">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6a8f-115">要求</span><span class="sxs-lookup"><span data-stu-id="a6a8f-115">Requirements</span></span>  
 <span data-ttu-id="a6a8f-116">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6a8f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6a8f-117">**标头：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6a8f-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6a8f-118">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6a8f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6a8f-119">**.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6a8f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a8f-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="a6a8f-120">See also</span></span>

- [<span data-ttu-id="a6a8f-121">EnumJITedFunctions 方法</span><span class="sxs-lookup"><span data-stu-id="a6a8f-121">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
- [<span data-ttu-id="a6a8f-122">ICorProfilerInfo4 接口</span><span class="sxs-lookup"><span data-stu-id="a6a8f-122">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="a6a8f-123">Profiling 接口</span><span class="sxs-lookup"><span data-stu-id="a6a8f-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="a6a8f-124">分析</span><span class="sxs-lookup"><span data-stu-id="a6a8f-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
