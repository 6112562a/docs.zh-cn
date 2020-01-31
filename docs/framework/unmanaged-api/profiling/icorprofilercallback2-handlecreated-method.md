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
ms.openlocfilehash: 0c25a5cad01ef0eb268e90c38bd24d638b6f8cc4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865761"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="1b97c-102">ICorProfilerCallback2::HandleCreated 方法</span><span class="sxs-lookup"><span data-stu-id="1b97c-102">ICorProfilerCallback2::HandleCreated Method</span></span>
<span data-ttu-id="1b97c-103">通知代码探查器已创建垃圾回收句柄。</span><span class="sxs-lookup"><span data-stu-id="1b97c-103">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b97c-104">语法</span><span class="sxs-lookup"><span data-stu-id="1b97c-104">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b97c-105">参数</span><span class="sxs-lookup"><span data-stu-id="1b97c-105">Parameters</span></span>  
 `handleId`  
 <span data-ttu-id="1b97c-106">中垃圾回收的句柄的 ID。</span><span class="sxs-lookup"><span data-stu-id="1b97c-106">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="1b97c-107">中为其创建垃圾回收句柄的对象的 ID。</span><span class="sxs-lookup"><span data-stu-id="1b97c-107">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b97c-108">需求</span><span class="sxs-lookup"><span data-stu-id="1b97c-108">Requirements</span></span>  
 <span data-ttu-id="1b97c-109">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b97c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b97c-110">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1b97c-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1b97c-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b97c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b97c-112">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b97c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b97c-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1b97c-113">See also</span></span>

- [<span data-ttu-id="1b97c-114">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="1b97c-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1b97c-115">ICorProfilerCallback2 接口</span><span class="sxs-lookup"><span data-stu-id="1b97c-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
