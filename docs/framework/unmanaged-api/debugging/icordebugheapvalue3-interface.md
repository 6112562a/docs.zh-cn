---
title: ICorDebugHeapValue3 接口
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d3b22d8dc140bf16af7f59781d5ed103dafbf4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191700"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="5bcc1-102">ICorDebugHeapValue3 接口</span><span class="sxs-lookup"><span data-stu-id="5bcc1-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="5bcc1-103">公开对象的监视器锁属性。</span><span class="sxs-lookup"><span data-stu-id="5bcc1-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="5bcc1-104">此接口扩展的 ICorDebugHeapValue 和 ICorDebugHeapValue2 接口。</span><span class="sxs-lookup"><span data-stu-id="5bcc1-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5bcc1-105">方法</span><span class="sxs-lookup"><span data-stu-id="5bcc1-105">Methods</span></span>  
  
|<span data-ttu-id="5bcc1-106">方法</span><span class="sxs-lookup"><span data-stu-id="5bcc1-106">Method</span></span>|<span data-ttu-id="5bcc1-107">描述</span><span class="sxs-lookup"><span data-stu-id="5bcc1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5bcc1-108">GetThreadOwningMonitorLock 方法</span><span class="sxs-lookup"><span data-stu-id="5bcc1-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="5bcc1-109">返回拥有此对象的监视器锁的托管的线程。</span><span class="sxs-lookup"><span data-stu-id="5bcc1-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="5bcc1-110">GetMonitorEventWaitList 方法</span><span class="sxs-lookup"><span data-stu-id="5bcc1-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="5bcc1-111">提供的监视器锁与相关联的事件的线程排队的排序的列表。</span><span class="sxs-lookup"><span data-stu-id="5bcc1-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bcc1-112">备注</span><span class="sxs-lookup"><span data-stu-id="5bcc1-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5bcc1-113">此接口不支持跨计算机或跨进程远程调用。</span><span class="sxs-lookup"><span data-stu-id="5bcc1-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bcc1-114">要求</span><span class="sxs-lookup"><span data-stu-id="5bcc1-114">Requirements</span></span>  
 <span data-ttu-id="5bcc1-115">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5bcc1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bcc1-116">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5bcc1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5bcc1-117">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bcc1-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5bcc1-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="5bcc1-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5bcc1-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="5bcc1-119">See also</span></span>

- [<span data-ttu-id="5bcc1-120">调试接口</span><span class="sxs-lookup"><span data-stu-id="5bcc1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5bcc1-121">调试</span><span class="sxs-lookup"><span data-stu-id="5bcc1-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
