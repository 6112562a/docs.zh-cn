---
title: ICorDebugStackWalk::GetContext 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f453e950a79b0f929ec8f813cc13eb2e01ab8c87
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760939"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="ab62b-102">ICorDebugStackWalk::GetContext 方法</span><span class="sxs-lookup"><span data-stu-id="ab62b-102">ICorDebugStackWalk::GetContext Method</span></span>
<span data-ttu-id="ab62b-103">返回的上下文中的当前帧[ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)对象。</span><span class="sxs-lookup"><span data-stu-id="ab62b-103">Returns the context for the current frame in the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab62b-104">语法</span><span class="sxs-lookup"><span data-stu-id="ab62b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab62b-105">参数</span><span class="sxs-lookup"><span data-stu-id="ab62b-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="ab62b-106">[in]指示请求 （在 WinNT.h 中定义） 的上下文缓冲区的内容的标志。</span><span class="sxs-lookup"><span data-stu-id="ab62b-106">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="ab62b-107">[in]已分配的上下文缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="ab62b-107">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="ab62b-108">[out]上下文的实际大小。</span><span class="sxs-lookup"><span data-stu-id="ab62b-108">[out] The actual size of the context.</span></span> <span data-ttu-id="ab62b-109">此值必须小于或等于上下文缓冲区的大小。</span><span class="sxs-lookup"><span data-stu-id="ab62b-109">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="ab62b-110">[out]上下文缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="ab62b-110">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab62b-111">返回值</span><span class="sxs-lookup"><span data-stu-id="ab62b-111">Return Value</span></span>  
 <span data-ttu-id="ab62b-112">此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="ab62b-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ab62b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ab62b-113">HRESULT</span></span>|<span data-ttu-id="ab62b-114">描述</span><span class="sxs-lookup"><span data-stu-id="ab62b-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ab62b-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="ab62b-115">S_OK</span></span>|<span data-ttu-id="ab62b-116">成功地返回当前帧的上下文。</span><span class="sxs-lookup"><span data-stu-id="ab62b-116">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="ab62b-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ab62b-117">E_FAIL</span></span>|<span data-ttu-id="ab62b-118">不会返回上下文。</span><span class="sxs-lookup"><span data-stu-id="ab62b-118">The context could not be returned.</span></span>|  
|<span data-ttu-id="ab62b-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span><span class="sxs-lookup"><span data-stu-id="ab62b-119">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="ab62b-120">上下文缓冲区因过小。</span><span class="sxs-lookup"><span data-stu-id="ab62b-120">The context buffer is too small.</span></span>|  
|<span data-ttu-id="ab62b-121">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="ab62b-121">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="ab62b-122">帧指针已末尾的堆栈;因此，可以不访问任何其他帧。</span><span class="sxs-lookup"><span data-stu-id="ab62b-122">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="ab62b-123">Exceptions</span><span class="sxs-lookup"><span data-stu-id="ab62b-123">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab62b-124">备注</span><span class="sxs-lookup"><span data-stu-id="ab62b-124">Remarks</span></span>  
 <span data-ttu-id="ab62b-125">因为展开还原寄存器中，例如非易失寄存器的一个子集上下文在调用时可能不完全匹配的注册状态。</span><span class="sxs-lookup"><span data-stu-id="ab62b-125">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab62b-126">要求</span><span class="sxs-lookup"><span data-stu-id="ab62b-126">Requirements</span></span>  
 <span data-ttu-id="ab62b-127">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab62b-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab62b-128">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ab62b-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ab62b-129">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab62b-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab62b-130">**.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab62b-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab62b-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="ab62b-131">See also</span></span>

- [<span data-ttu-id="ab62b-132">调试接口</span><span class="sxs-lookup"><span data-stu-id="ab62b-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ab62b-133">调试</span><span class="sxs-lookup"><span data-stu-id="ab62b-133">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
