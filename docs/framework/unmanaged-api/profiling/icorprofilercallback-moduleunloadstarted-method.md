---
title: ICorProfilerCallback::ModuleUnloadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadStarted
helpviewer_keywords:
- ModuleUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadStarted method [.NET Framework profiling]
ms.assetid: 2debcaab-6005-4245-afdb-4268bb7e74bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c99ddc66cca0a0d0083cfa19cfca34a1e557d4e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769147"
---
# <a name="icorprofilercallbackmoduleunloadstarted-method"></a><span data-ttu-id="74a4b-102">ICorProfilerCallback::ModuleUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="74a4b-102">ICorProfilerCallback::ModuleUnloadStarted Method</span></span>
<span data-ttu-id="74a4b-103">通知探查器正在卸载模块。</span><span class="sxs-lookup"><span data-stu-id="74a4b-103">Notifies the profiler that a module is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74a4b-104">语法</span><span class="sxs-lookup"><span data-stu-id="74a4b-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadStarted(  
    [in] ModuleID moduleId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="74a4b-105">参数</span><span class="sxs-lookup"><span data-stu-id="74a4b-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="74a4b-106">[in]正在卸载模块的 ID。</span><span class="sxs-lookup"><span data-stu-id="74a4b-106">[in] The ID of the module that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74a4b-107">备注</span><span class="sxs-lookup"><span data-stu-id="74a4b-107">Remarks</span></span>  
 <span data-ttu-id="74a4b-108">值`moduleId`不是有效的信息请求后`ModuleUnloadStarted`方法将返回-这是探查器的最后一次机会来获取有关此模块的信息。</span><span class="sxs-lookup"><span data-stu-id="74a4b-108">The value of `moduleId` is not valid for an information request after the `ModuleUnloadStarted` method returns — this is the profiler's last chance to get information about this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74a4b-109">要求</span><span class="sxs-lookup"><span data-stu-id="74a4b-109">Requirements</span></span>  
 <span data-ttu-id="74a4b-110">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="74a4b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74a4b-111">**标头：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="74a4b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74a4b-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74a4b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74a4b-113">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74a4b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a4b-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="74a4b-114">See also</span></span>

- [<span data-ttu-id="74a4b-115">ICorProfilerCallback 接口</span><span class="sxs-lookup"><span data-stu-id="74a4b-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="74a4b-116">ModuleUnloadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="74a4b-116">ModuleUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)
