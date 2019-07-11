---
title: ICorDebugProcess::SetThreadContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b949961e854facf8414c81c47f995b2ac57af3f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755381"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="dea64-102">ICorDebugProcess::SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="dea64-102">ICorDebugProcess::SetThreadContext Method</span></span>
<span data-ttu-id="dea64-103">在此过程中设置给定线程的上下文。</span><span class="sxs-lookup"><span data-stu-id="dea64-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea64-104">语法</span><span class="sxs-lookup"><span data-stu-id="dea64-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dea64-105">参数</span><span class="sxs-lookup"><span data-stu-id="dea64-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="dea64-106">[in]若要设置上下文的线程的 ID。</span><span class="sxs-lookup"><span data-stu-id="dea64-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="dea64-107">[in] `context` 数组的大小。</span><span class="sxs-lookup"><span data-stu-id="dea64-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="dea64-108">[in]一个描述在线程的上下文的字节数组。</span><span class="sxs-lookup"><span data-stu-id="dea64-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="dea64-109">上下文指定在其执行该线程的处理器体系的结构。</span><span class="sxs-lookup"><span data-stu-id="dea64-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dea64-110">备注</span><span class="sxs-lookup"><span data-stu-id="dea64-110">Remarks</span></span>  
 <span data-ttu-id="dea64-111">调试程序应调用此方法，而不是 Win32`SetThreadContext`函数，因为线程实际上可能是在"被劫持"状态下，在其中其上下文已被暂时更改。</span><span class="sxs-lookup"><span data-stu-id="dea64-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="dea64-112">仅当线程在本机代码中时，才应使用此方法。</span><span class="sxs-lookup"><span data-stu-id="dea64-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="dea64-113">使用[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)托管代码中的线程。</span><span class="sxs-lookup"><span data-stu-id="dea64-113">Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="dea64-114">您应永远不会需要在带外 (OOB) 调试事件期间修改线程的上下文。</span><span class="sxs-lookup"><span data-stu-id="dea64-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="dea64-115">传递的数据必须是当前平台的上下文结构。</span><span class="sxs-lookup"><span data-stu-id="dea64-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="dea64-116">如果使用不当，则此方法会损坏运行时。</span><span class="sxs-lookup"><span data-stu-id="dea64-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dea64-117">要求</span><span class="sxs-lookup"><span data-stu-id="dea64-117">Requirements</span></span>  
 <span data-ttu-id="dea64-118">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dea64-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dea64-119">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dea64-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dea64-120">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dea64-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dea64-121">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dea64-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
