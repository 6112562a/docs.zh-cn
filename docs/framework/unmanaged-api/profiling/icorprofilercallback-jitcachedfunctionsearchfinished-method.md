---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882d3b3c359724688c0fb8fe5e2b567f1d575e76
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782860"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a><span data-ttu-id="3cd23-102">ICorProfilerCallback::JITCachedFunctionSearchFinished 方法</span><span class="sxs-lookup"><span data-stu-id="3cd23-102">ICorProfilerCallback::JITCachedFunctionSearchFinished Method</span></span>
<span data-ttu-id="3cd23-103">通知探查器搜索已完成以前使用本机映像生成器 (NGen.exe) 编译的函数。</span><span class="sxs-lookup"><span data-stu-id="3cd23-103">Notifies the profiler that a search has finished for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cd23-104">语法</span><span class="sxs-lookup"><span data-stu-id="3cd23-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cd23-105">参数</span><span class="sxs-lookup"><span data-stu-id="3cd23-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3cd23-106">[in]为其执行了搜索函数的 ID。</span><span class="sxs-lookup"><span data-stu-id="3cd23-106">[in] The ID of the function for which the search was performed.</span></span>  
  
 `result`  
 <span data-ttu-id="3cd23-107">[in]值为[COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md)枚举，指示搜索结果。</span><span class="sxs-lookup"><span data-stu-id="3cd23-107">[in] A value of the [COR_PRF_JIT_CACHE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) enumeration that indicates the result of the search.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cd23-108">备注</span><span class="sxs-lookup"><span data-stu-id="3cd23-108">Remarks</span></span>  
 <span data-ttu-id="3cd23-109">在.NET Framework 2.0 版中， [icorprofilercallback:: Jitcachedfunctionsearchstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)和`JITCachedFunctionSearchFinished`回调不会为正则 NGen 映像中的所有函数。</span><span class="sxs-lookup"><span data-stu-id="3cd23-109">In the .NET Framework version 2.0, the [ICorProfilerCallback::JITCachedFunctionSearchStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) and `JITCachedFunctionSearchFinished` callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="3cd23-110">仅为探查器优化 NGen 映像将在图中生成的所有函数的回调。</span><span class="sxs-lookup"><span data-stu-id="3cd23-110">Only NGen images optimized for a profiler will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="3cd23-111">但是，由于的额外开销，探查器应请求探查器优化 NGen 映像仅当它要使用这些回调以强制对函数进行编译中实时 (JIT)。</span><span class="sxs-lookup"><span data-stu-id="3cd23-111">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="3cd23-112">否则，探查器应使用延迟策略，用于收集函数的信息。</span><span class="sxs-lookup"><span data-stu-id="3cd23-112">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cd23-113">要求</span><span class="sxs-lookup"><span data-stu-id="3cd23-113">Requirements</span></span>  
 <span data-ttu-id="3cd23-114">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3cd23-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cd23-115">**标头：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3cd23-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3cd23-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cd23-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cd23-117">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cd23-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd23-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="3cd23-118">See also</span></span>

- [<span data-ttu-id="3cd23-119">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="3cd23-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
