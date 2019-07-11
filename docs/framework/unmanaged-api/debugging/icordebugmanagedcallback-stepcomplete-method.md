---
title: ICorDebugManagedCallback::StepComplete 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.StepComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c3ced50457519d62be44712386bdabce176c44e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761309"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a><span data-ttu-id="d05cf-102">ICorDebugManagedCallback::StepComplete 方法</span><span class="sxs-lookup"><span data-stu-id="d05cf-102">ICorDebugManagedCallback::StepComplete Method</span></span>
<span data-ttu-id="d05cf-103">通知调试器步骤已完成。</span><span class="sxs-lookup"><span data-stu-id="d05cf-103">Notifies the debugger that a step has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d05cf-104">语法</span><span class="sxs-lookup"><span data-stu-id="d05cf-104">Syntax</span></span>  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d05cf-105">参数</span><span class="sxs-lookup"><span data-stu-id="d05cf-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="d05cf-106">[in]指向一个 ICorDebugAppDomain 对象，表示包含此步骤具有已完成的线程的应用程序域的指针。</span><span class="sxs-lookup"><span data-stu-id="d05cf-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread in which the step has completed.</span></span>  
  
 `pThread`  
 <span data-ttu-id="d05cf-107">[in]指向表示此步骤具有已完成的线程的 ICorDebugThread 对象的指针。</span><span class="sxs-lookup"><span data-stu-id="d05cf-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the step has completed.</span></span>  
  
 `pStepper`  
 <span data-ttu-id="d05cf-108">[in]指向表示执行代码中的步 ICorDebugStepper 对象的指针。</span><span class="sxs-lookup"><span data-stu-id="d05cf-108">[in] A pointer to an ICorDebugStepper object that represents the step in code execution.</span></span>  
  
 `reason`  
 <span data-ttu-id="d05cf-109">[in]CorDebugStepReason 枚举，指示一个单步执行的结果的值。</span><span class="sxs-lookup"><span data-stu-id="d05cf-109">[in] A value of the CorDebugStepReason enumeration that indicates the outcome of an individual step.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d05cf-110">备注</span><span class="sxs-lookup"><span data-stu-id="d05cf-110">Remarks</span></span>  
 <span data-ttu-id="d05cf-111">分档器可能用于继续单步执行必要时，除非终止调试。</span><span class="sxs-lookup"><span data-stu-id="d05cf-111">The stepper may be used to continue stepping if desired, unless the debugging is terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d05cf-112">要求</span><span class="sxs-lookup"><span data-stu-id="d05cf-112">Requirements</span></span>  
 <span data-ttu-id="d05cf-113">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d05cf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d05cf-114">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d05cf-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d05cf-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d05cf-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d05cf-116">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d05cf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d05cf-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="d05cf-117">See also</span></span>

- [<span data-ttu-id="d05cf-118">ICorDebugManagedCallback 接口</span><span class="sxs-lookup"><span data-stu-id="d05cf-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
