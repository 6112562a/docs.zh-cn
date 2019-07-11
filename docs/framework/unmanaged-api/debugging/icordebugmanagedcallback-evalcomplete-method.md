---
title: ICorDebugManagedCallback::EvalComplete 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalComplete
helpviewer_keywords:
- ICorDebugManagedCallback::EvalComplete method [.NET Framework debugging]
- EvalComplete method [.NET Framework debugging]
ms.assetid: f74ab4eb-cd1b-407c-a66d-8ec0d85647f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a874646a6746a9b2fc8ce597e6c1ca47340c199a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759642"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a><span data-ttu-id="e78bc-102">ICorDebugManagedCallback::EvalComplete 方法</span><span class="sxs-lookup"><span data-stu-id="e78bc-102">ICorDebugManagedCallback::EvalComplete Method</span></span>
<span data-ttu-id="e78bc-103">通知调试器已完成评估。</span><span class="sxs-lookup"><span data-stu-id="e78bc-103">Notifies the debugger that an evaluation has been completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e78bc-104">语法</span><span class="sxs-lookup"><span data-stu-id="e78bc-104">Syntax</span></span>  
  
```cpp  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e78bc-105">参数</span><span class="sxs-lookup"><span data-stu-id="e78bc-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e78bc-106">[in]指向一个 ICorDebugAppDomain 对象，表示在其中执行计算的应用程序域的指针。</span><span class="sxs-lookup"><span data-stu-id="e78bc-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the evaluation was performed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="e78bc-107">[in]指向一个 ICorDebugThread 对象，表示在其中执行计算的线程的指针。</span><span class="sxs-lookup"><span data-stu-id="e78bc-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the evaluation was performed.</span></span>  
  
 `pEval`  
 <span data-ttu-id="e78bc-108">[in]指向一个 ICorDebugEval 对象，表示执行计算的代码的指针。</span><span class="sxs-lookup"><span data-stu-id="e78bc-108">[in] A pointer to an ICorDebugEval object that represents the code that performed the evaluation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e78bc-109">要求</span><span class="sxs-lookup"><span data-stu-id="e78bc-109">Requirements</span></span>  
 <span data-ttu-id="e78bc-110">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e78bc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e78bc-111">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e78bc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e78bc-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e78bc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e78bc-113">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e78bc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e78bc-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="e78bc-114">See also</span></span>

- [<span data-ttu-id="e78bc-115">ICorDebugManagedCallback 接口</span><span class="sxs-lookup"><span data-stu-id="e78bc-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
