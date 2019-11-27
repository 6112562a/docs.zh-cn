---
title: ICorProfilerInfo4::RequestReJIT 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestReJIT
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestReJIT
helpviewer_keywords:
- RequestReJIT method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestReJIT method [.NET Framework profiling]
ms.assetid: 781ed736-f30c-4816-920e-3552e36542c6
topic_type:
- apiref
ms.openlocfilehash: eb4d5e1c4efd67914df95868b67ec5cc3fe6139a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444816"
---
# <a name="icorprofilerinfo4requestrejit-method"></a><span data-ttu-id="ab6c9-102">ICorProfilerInfo4::RequestReJIT 方法</span><span class="sxs-lookup"><span data-stu-id="ab6c9-102">ICorProfilerInfo4::RequestReJIT Method</span></span>
<span data-ttu-id="ab6c9-103">请求 JIT 重新编译指定函数的所有实例。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-103">Requests a JIT recompilation of all instances of the specified functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab6c9-104">语法</span><span class="sxs-lookup"><span data-stu-id="ab6c9-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestReJIT (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab6c9-105">参数</span><span class="sxs-lookup"><span data-stu-id="ab6c9-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="ab6c9-106">[in] 要重新编译的函数数目。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-106">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="ab6c9-107">[in] 指定（`moduleId`、`module`）对的 `methodDef` 部分，它标识要重新编译的函数。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="ab6c9-108">[in] 指定（`methodId`、`module`）对的 `methodDef` 部分，它标识要重新编译的函数。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab6c9-109">返回值</span><span class="sxs-lookup"><span data-stu-id="ab6c9-109">Return Value</span></span>  
 <span data-ttu-id="ab6c9-110">此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ab6c9-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ab6c9-111">HRESULT</span></span>|<span data-ttu-id="ab6c9-112">说明</span><span class="sxs-lookup"><span data-stu-id="ab6c9-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ab6c9-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ab6c9-113">S_OK</span></span>|<span data-ttu-id="ab6c9-114">尝试将所有方法标记为 JIT 重新编译。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-114">An attempt was made to mark all the methods for JIT recompilation.</span></span> <span data-ttu-id="ab6c9-115">探查器必须实现[ICorProfilerCallback4：： ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)方法来确定哪些方法已成功标记为 JIT 重新编译。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-115">The profiler must implement the [ICorProfilerCallback4::ReJITError](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md) method to determine which methods were successfully marked for JIT recompilation.</span></span>|  
|<span data-ttu-id="ab6c9-116">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="ab6c9-116">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="ab6c9-117">探查器必须实现[ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)接口，以便支持此调用。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-117">The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="ab6c9-118">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="ab6c9-118">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="ab6c9-119">尚未启用 JIT 重新编译。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-119">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="ab6c9-120">必须通过使用[ICorProfilerInfo：： SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法设置 `COR_PRF_ENABLE_REJIT` 标志来在初始化期间启用 JIT 重新编译。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-120">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="ab6c9-121">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ab6c9-121">E_INVALIDARG</span></span>|<span data-ttu-id="ab6c9-122">`cFunctions` 为0，或者 `moduleIds` 或 `methodIds` `NULL`。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-122">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|||  
|<span data-ttu-id="ab6c9-123">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ab6c9-123">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ab6c9-124">CLR 无法完成请求，因为它已耗尽内存。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-124">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab6c9-125">备注</span><span class="sxs-lookup"><span data-stu-id="ab6c9-125">Remarks</span></span>  
 <span data-ttu-id="ab6c9-126">调用 `RequestReJIT` 以使运行时重新编译一组指定的函数。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-126">Call `RequestReJIT` to have the runtime recompile a specified set of functions.</span></span> <span data-ttu-id="ab6c9-127">然后，代码探查器可以使用[ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)接口来调整重新编译函数时生成的代码。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-127">A code profiler can then use the [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface to adjust the code that is generated when the functions are recompiled.</span></span> <span data-ttu-id="ab6c9-128">这不会影响当前正在执行的函数，仅影响将来的函数调用。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-128">This does not affect currently executing functions, only future function invocations.</span></span> <span data-ttu-id="ab6c9-129">如果此前已 JIT 重新编译任意指定函数，请求重新编译是指还原和重新编译函数。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-129">If any of the specified functions has previously been JIT-recompiled, requesting a recompilation is equivalent to reverting and recompiling the function.</span></span> <span data-ttu-id="ab6c9-130">若要保留可还原性，当 JIT 编译器编译函数的原始版本时，将仅考虑被调用方用于内联决定的原始版本。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-130">To preserve reversibility, when the JIT compiler compiles the original version of a function, it considers only the original versions of its callees for inlining decisions.</span></span> <span data-ttu-id="ab6c9-131">JIT 编译器重新编译函数时，将考虑被调用方用于内联的当前版本（重新编译版本或原始版本）。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-131">When the JIT compiler recompiles a function, it considers the current versions (recompiled or original) of its callees for inlining.</span></span>  
  
 <span data-ttu-id="ab6c9-132">探查器通常会调用 `RequestReJIT` 以响应用户输入对探查器检测一个或多个方法的请求。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-132">A profiler typically calls `RequestReJIT` in response to user input requesting that the profiler instrument one or more methods.</span></span> <span data-ttu-id="ab6c9-133">`RequestReJIT` 通常会挂起运行时以执行其某些工作，并可能触发垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-133">`RequestReJIT` typically suspends the runtime in order to do some of its work, and can potentially trigger a garbage collection.</span></span> <span data-ttu-id="ab6c9-134">因此，探查器应从其先前创建的线程调用 `RequestReJIT`，而不从 CLR 创建的且当前正在执行探查器回调的线程调用。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-134">As such, the profiler should call `RequestReJIT` from a thread it previously created, and not from a CLR-created thread that is currently executing a profiler callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab6c9-135">要求</span><span class="sxs-lookup"><span data-stu-id="ab6c9-135">Requirements</span></span>  
 <span data-ttu-id="ab6c9-136">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab6c9-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab6c9-137">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ab6c9-137">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab6c9-138">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab6c9-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab6c9-139">**.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab6c9-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab6c9-140">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ab6c9-140">See also</span></span>

- [<span data-ttu-id="ab6c9-141">ICorProfilerInfo4 接口</span><span class="sxs-lookup"><span data-stu-id="ab6c9-141">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="ab6c9-142">Profiling 接口</span><span class="sxs-lookup"><span data-stu-id="ab6c9-142">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ab6c9-143">分析</span><span class="sxs-lookup"><span data-stu-id="ab6c9-143">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
