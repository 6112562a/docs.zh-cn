---
title: CorDebugChainReason 枚举
ms.date: 03/30/2017
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 621ae6dae32e79a26d81441841b4c6a274d86f83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497585"
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="2852a-102">CorDebugChainReason 枚举</span><span class="sxs-lookup"><span data-stu-id="2852a-102">CorDebugChainReason Enumeration</span></span>
<span data-ttu-id="2852a-103">指示启动调用链的一个或多个原因。</span><span class="sxs-lookup"><span data-stu-id="2852a-103">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2852a-104">语法</span><span class="sxs-lookup"><span data-stu-id="2852a-104">Syntax</span></span>  
  
```  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a><span data-ttu-id="2852a-105">成员</span><span class="sxs-lookup"><span data-stu-id="2852a-105">Members</span></span>  
  
|<span data-ttu-id="2852a-106">成员</span><span class="sxs-lookup"><span data-stu-id="2852a-106">Member</span></span>|<span data-ttu-id="2852a-107">描述</span><span class="sxs-lookup"><span data-stu-id="2852a-107">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="2852a-108">尚未启动任何调用链。</span><span class="sxs-lookup"><span data-stu-id="2852a-108">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="2852a-109">由构造函数启动该链。</span><span class="sxs-lookup"><span data-stu-id="2852a-109">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="2852a-110">由异常筛选器启动该链。</span><span class="sxs-lookup"><span data-stu-id="2852a-110">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="2852a-111">由强制实施安全的代码启动该链。</span><span class="sxs-lookup"><span data-stu-id="2852a-111">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="2852a-112">由上下文策略启动该链。</span><span class="sxs-lookup"><span data-stu-id="2852a-112">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="2852a-113">未使用。</span><span class="sxs-lookup"><span data-stu-id="2852a-113">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="2852a-114">未使用。</span><span class="sxs-lookup"><span data-stu-id="2852a-114">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="2852a-115">由线程执行开始启动该链。</span><span class="sxs-lookup"><span data-stu-id="2852a-115">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="2852a-116">由托管代码中的条目启动该链。</span><span class="sxs-lookup"><span data-stu-id="2852a-116">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="2852a-117">由非托管代码中的条目启动该链。</span><span class="sxs-lookup"><span data-stu-id="2852a-117">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="2852a-118">未使用。</span><span class="sxs-lookup"><span data-stu-id="2852a-118">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="2852a-119">未使用。</span><span class="sxs-lookup"><span data-stu-id="2852a-119">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="2852a-120">由函数求值启动该链。</span><span class="sxs-lookup"><span data-stu-id="2852a-120">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2852a-121">备注</span><span class="sxs-lookup"><span data-stu-id="2852a-121">Remarks</span></span>  
 <span data-ttu-id="2852a-122">使用[icordebugchain:: Getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)方法可确定调用链的用于启动的原因。</span><span class="sxs-lookup"><span data-stu-id="2852a-122">Use the [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2852a-123">要求</span><span class="sxs-lookup"><span data-stu-id="2852a-123">Requirements</span></span>  
 <span data-ttu-id="2852a-124">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2852a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2852a-125">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2852a-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2852a-126">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2852a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2852a-127">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2852a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2852a-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="2852a-128">See also</span></span>
- [<span data-ttu-id="2852a-129">调试枚举</span><span class="sxs-lookup"><span data-stu-id="2852a-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
