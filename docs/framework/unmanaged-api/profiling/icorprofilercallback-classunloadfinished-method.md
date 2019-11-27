---
title: ICorProfilerCallback::ClassUnloadFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
ms.openlocfilehash: b78d604a28ffe01000a763f7e0dd3c1630e2c186
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435922"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="e065b-102">ICorProfilerCallback::ClassUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="e065b-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="e065b-103">通知探查器类已经完成卸载。</span><span class="sxs-lookup"><span data-stu-id="e065b-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e065b-104">语法</span><span class="sxs-lookup"><span data-stu-id="e065b-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e065b-105">参数</span><span class="sxs-lookup"><span data-stu-id="e065b-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="e065b-106">中标识已卸载的类。</span><span class="sxs-lookup"><span data-stu-id="e065b-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="e065b-107">中指示是否已成功卸载类的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="e065b-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e065b-108">备注</span><span class="sxs-lookup"><span data-stu-id="e065b-108">Remarks</span></span>  
 <span data-ttu-id="e065b-109">在 `ClassUnloadFinished` 回调后，卸载类的某些部分可能会继续。</span><span class="sxs-lookup"><span data-stu-id="e065b-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="e065b-110">如果 `hrStatus` 失败，则指示失败。</span><span class="sxs-lookup"><span data-stu-id="e065b-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="e065b-111">不过，`hrStatus` 中的 HRESULT 成功仅指示卸载类的第一部分已成功。</span><span class="sxs-lookup"><span data-stu-id="e065b-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e065b-112">要求</span><span class="sxs-lookup"><span data-stu-id="e065b-112">Requirements</span></span>  
 <span data-ttu-id="e065b-113">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e065b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e065b-114">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e065b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e065b-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e065b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e065b-116">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e065b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e065b-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e065b-117">See also</span></span>

- [<span data-ttu-id="e065b-118">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="e065b-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e065b-119">ClassUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="e065b-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
