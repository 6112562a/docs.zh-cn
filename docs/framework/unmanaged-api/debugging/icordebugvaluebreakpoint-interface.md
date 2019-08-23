---
title: ICorDebugValueBreakpoint 接口
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f77268e069d322d0f491f78b154cf63b691e3e38
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966817"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="00bea-102">ICorDebugValueBreakpoint 接口</span><span class="sxs-lookup"><span data-stu-id="00bea-102">ICorDebugValueBreakpoint Interface</span></span>
<span data-ttu-id="00bea-103">扩展 ICorDebugBreakpoint 接口以提供对特定值的访问。</span><span class="sxs-lookup"><span data-stu-id="00bea-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="00bea-104">方法</span><span class="sxs-lookup"><span data-stu-id="00bea-104">Methods</span></span>  
  
|<span data-ttu-id="00bea-105">方法</span><span class="sxs-lookup"><span data-stu-id="00bea-105">Method</span></span>|<span data-ttu-id="00bea-106">描述</span><span class="sxs-lookup"><span data-stu-id="00bea-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00bea-107">GetValue 方法</span><span class="sxs-lookup"><span data-stu-id="00bea-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="00bea-108">获取一个指向 ICorDebugValue 对象的接口指针, 该对象表示在其上设置断点的对象的值。</span><span class="sxs-lookup"><span data-stu-id="00bea-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00bea-109">备注</span><span class="sxs-lookup"><span data-stu-id="00bea-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00bea-110">此接口不支持跨计算机或跨进程远程调用。</span><span class="sxs-lookup"><span data-stu-id="00bea-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00bea-111">要求</span><span class="sxs-lookup"><span data-stu-id="00bea-111">Requirements</span></span>  
 <span data-ttu-id="00bea-112">**适用**请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00bea-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00bea-113">**标头：** Cordebug.idl, Cordebug.idl</span><span class="sxs-lookup"><span data-stu-id="00bea-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="00bea-114">**类库**CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00bea-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00bea-115">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00bea-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00bea-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="00bea-116">See also</span></span>

- [<span data-ttu-id="00bea-117">调试接口</span><span class="sxs-lookup"><span data-stu-id="00bea-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
