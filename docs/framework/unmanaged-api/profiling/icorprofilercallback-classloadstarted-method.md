---
title: ICorProfilerCallback::ClassLoadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d19814b0c663310e977ef148ad37eb74129fd4d2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466494"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="67f90-102">ICorProfilerCallback::ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="67f90-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="67f90-103">通知探查器正在加载的类。</span><span class="sxs-lookup"><span data-stu-id="67f90-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67f90-104">语法</span><span class="sxs-lookup"><span data-stu-id="67f90-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67f90-105">参数</span><span class="sxs-lookup"><span data-stu-id="67f90-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="67f90-106">[in]标识要加载的类。</span><span class="sxs-lookup"><span data-stu-id="67f90-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67f90-107">备注</span><span class="sxs-lookup"><span data-stu-id="67f90-107">Remarks</span></span>  
 <span data-ttu-id="67f90-108">值`classId`不是有效的信息请求之前[icorprofilercallback:: Classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)调用方法。</span><span class="sxs-lookup"><span data-stu-id="67f90-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67f90-109">要求</span><span class="sxs-lookup"><span data-stu-id="67f90-109">Requirements</span></span>  
 <span data-ttu-id="67f90-110">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67f90-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67f90-111">**标头：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67f90-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67f90-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67f90-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67f90-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67f90-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f90-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="67f90-114">See also</span></span>
- [<span data-ttu-id="67f90-115">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="67f90-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
