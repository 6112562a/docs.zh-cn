---
title: ICorDebugProcess2::GetThreadForTaskID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetThreadForTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetThreadForTaskID
helpviewer_keywords:
- ICorDebugProcess2::GetThreadForTaskId method [.NET Framework debugging]
- GetThreadForTaskID method [.NET Framework debugging]
ms.assetid: 32d54a5b-8ad3-405b-a1b9-0936a3b49d1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c85040a31966a92ead6ca4786f62852f17923056
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736931"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="0c79c-102">ICorDebugProcess2::GetThreadForTaskID 方法</span><span class="sxs-lookup"><span data-stu-id="0c79c-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="0c79c-103">获取具有指定标识符的任务正在执行的线程。</span><span class="sxs-lookup"><span data-stu-id="0c79c-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c79c-104">语法</span><span class="sxs-lookup"><span data-stu-id="0c79c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c79c-105">参数</span><span class="sxs-lookup"><span data-stu-id="0c79c-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="0c79c-106">[in]任务的标识符。</span><span class="sxs-lookup"><span data-stu-id="0c79c-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="0c79c-107">[out]指向一个 ICorDebugThread2 对象，表示要检索的线程的地址的指针。</span><span class="sxs-lookup"><span data-stu-id="0c79c-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c79c-108">备注</span><span class="sxs-lookup"><span data-stu-id="0c79c-108">Remarks</span></span>  
 <span data-ttu-id="0c79c-109">主机可以通过使用设置的任务标识符[iclrtask:: Settaskidentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="0c79c-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c79c-110">要求</span><span class="sxs-lookup"><span data-stu-id="0c79c-110">Requirements</span></span>  
 <span data-ttu-id="0c79c-111">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c79c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c79c-112">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c79c-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c79c-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c79c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c79c-114">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c79c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
