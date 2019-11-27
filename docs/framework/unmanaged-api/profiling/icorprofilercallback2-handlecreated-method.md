---
title: ICorProfilerCallback2::HandleCreated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
ms.openlocfilehash: 594d970dbe0a176a5ec49015e105f89ff64bdfac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439771"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="52780-102">ICorProfilerCallback2::HandleCreated 方法</span><span class="sxs-lookup"><span data-stu-id="52780-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="52780-103">通知代码探查器已创建垃圾回收句柄。</span><span class="sxs-lookup"><span data-stu-id="52780-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52780-104">语法</span><span class="sxs-lookup"><span data-stu-id="52780-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52780-105">参数</span><span class="sxs-lookup"><span data-stu-id="52780-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="52780-106">中垃圾回收的句柄的 ID。</span><span class="sxs-lookup"><span data-stu-id="52780-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="52780-107">中为其创建垃圾回收句柄的对象的 ID。</span><span class="sxs-lookup"><span data-stu-id="52780-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52780-108">要求</span><span class="sxs-lookup"><span data-stu-id="52780-108">Requirements</span></span>  
 <span data-ttu-id="52780-109">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52780-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52780-110">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="52780-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52780-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52780-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52780-112">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52780-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52780-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="52780-113">See also</span></span>

- [<span data-ttu-id="52780-114">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="52780-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="52780-115">ICorProfilerCallback2 接口</span><span class="sxs-lookup"><span data-stu-id="52780-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
