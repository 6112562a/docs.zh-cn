---
title: ICorDebugThread2::GetTaskID 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1272df17a9a9a500b84f62914811b8d109bf3cdd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768957"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="28352-102">ICorDebugThread2::GetTaskID 方法</span><span class="sxs-lookup"><span data-stu-id="28352-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="28352-103">获取此线程上运行的任务的标识符。</span><span class="sxs-lookup"><span data-stu-id="28352-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28352-104">语法</span><span class="sxs-lookup"><span data-stu-id="28352-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28352-105">参数</span><span class="sxs-lookup"><span data-stu-id="28352-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="28352-106">[out]一个指向此 ICorDebugThread2 对象表示在线程上运行的任务的标识符。</span><span class="sxs-lookup"><span data-stu-id="28352-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28352-107">备注</span><span class="sxs-lookup"><span data-stu-id="28352-107">Remarks</span></span>  
 <span data-ttu-id="28352-108">如果线程是与连接相关联，仅可以在线程上运行任务。</span><span class="sxs-lookup"><span data-stu-id="28352-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="28352-109">`GetTaskID` 在中，则返回零`pTaskId`线程是否不与连接相关联。</span><span class="sxs-lookup"><span data-stu-id="28352-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28352-110">要求</span><span class="sxs-lookup"><span data-stu-id="28352-110">Requirements</span></span>  
 <span data-ttu-id="28352-111">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="28352-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28352-112">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28352-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28352-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28352-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28352-114">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28352-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
