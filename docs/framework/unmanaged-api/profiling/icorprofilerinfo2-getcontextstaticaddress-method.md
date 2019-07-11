---
title: ICorProfilerInfo2::GetContextStaticAddress 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c5c8165d44cc3a305820f8e97c07da37f2a0693
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775806"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="5c307-102">ICorProfilerInfo2::GetContextStaticAddress 方法</span><span class="sxs-lookup"><span data-stu-id="5c307-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="5c307-103">获取指定的上下文在作用域中的指定上下文的静态字段的地址。</span><span class="sxs-lookup"><span data-stu-id="5c307-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c307-104">语法</span><span class="sxs-lookup"><span data-stu-id="5c307-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c307-105">参数</span><span class="sxs-lookup"><span data-stu-id="5c307-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="5c307-106">[in]包含请求的上下文静态字段的类的 ID。</span><span class="sxs-lookup"><span data-stu-id="5c307-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="5c307-107">[in]请求的上下文静态字段元数据标记。</span><span class="sxs-lookup"><span data-stu-id="5c307-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="5c307-108">[in]请求的上下文静态字段的作用域上下文的 ID。</span><span class="sxs-lookup"><span data-stu-id="5c307-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="5c307-109">[out]一个指向指定的上下文内的静态字段的地址。</span><span class="sxs-lookup"><span data-stu-id="5c307-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c307-110">备注</span><span class="sxs-lookup"><span data-stu-id="5c307-110">Remarks</span></span>  
 <span data-ttu-id="5c307-111">`GetContextStaticAddress`方法可能会返回以下值之一：</span><span class="sxs-lookup"><span data-stu-id="5c307-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="5c307-112">如果尚未分配给定的静态字段中指定的上下文的地址 CORPROF_E_DATAINCOMPLETE HRESULT。</span><span class="sxs-lookup"><span data-stu-id="5c307-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="5c307-113">可能在垃圾回收堆的对象的地址。</span><span class="sxs-lookup"><span data-stu-id="5c307-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="5c307-114">使垃圾回收后，探查器不应假定它们是有效，则这些地址可能会回收后无效。</span><span class="sxs-lookup"><span data-stu-id="5c307-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="5c307-115">类的类构造函数完成之前，`GetContextStaticAddress`将返回 CORPROF_E_DATAINCOMPLETE 对于所有其静态字段，尽管可能已初始化的一些静态字段和根垃圾回收对象。</span><span class="sxs-lookup"><span data-stu-id="5c307-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c307-116">要求</span><span class="sxs-lookup"><span data-stu-id="5c307-116">Requirements</span></span>  
 <span data-ttu-id="5c307-117">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5c307-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c307-118">**标头：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5c307-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5c307-119">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c307-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c307-120">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c307-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c307-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="5c307-121">See also</span></span>

- [<span data-ttu-id="5c307-122">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="5c307-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="5c307-123">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="5c307-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
