---
title: CorDebugExceptionObjectStackFrame 结构
ms.date: 03/30/2017
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
ms.openlocfilehash: faa2082d31c5fa47b87e2238017066b477fdc191
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132174"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="b2076-102">CorDebugExceptionObjectStackFrame 结构</span><span class="sxs-lookup"><span data-stu-id="b2076-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="b2076-103">表示异常对象中的堆栈帧信息。</span><span class="sxs-lookup"><span data-stu-id="b2076-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2076-104">语法</span><span class="sxs-lookup"><span data-stu-id="b2076-104">Syntax</span></span>  
  
```cpp  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="b2076-105">Members</span><span class="sxs-lookup"><span data-stu-id="b2076-105">Members</span></span>  
  
|<span data-ttu-id="b2076-106">成员</span><span class="sxs-lookup"><span data-stu-id="b2076-106">Member</span></span>|<span data-ttu-id="b2076-107">描述</span><span class="sxs-lookup"><span data-stu-id="b2076-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="b2076-108">指向当前帧的 ICorDebugModule 对象的指针。</span><span class="sxs-lookup"><span data-stu-id="b2076-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="b2076-109">当前帧的指令指针（EIP/裂缝）的值。</span><span class="sxs-lookup"><span data-stu-id="b2076-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="b2076-110">当前帧的方法标记。</span><span class="sxs-lookup"><span data-stu-id="b2076-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="b2076-111">一个值，该值指示帧是否为外部异常中的最后一个帧。</span><span class="sxs-lookup"><span data-stu-id="b2076-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2076-112">备注</span><span class="sxs-lookup"><span data-stu-id="b2076-112">Remarks</span></span>  
 <span data-ttu-id="b2076-113">当不再使用 ICorDebugModule 对象时，调用方必须释放指向该对象的指针。</span><span class="sxs-lookup"><span data-stu-id="b2076-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2076-114">要求</span><span class="sxs-lookup"><span data-stu-id="b2076-114">Requirements</span></span>  
 <span data-ttu-id="b2076-115">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2076-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2076-116">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2076-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2076-117">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2076-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2076-118">**.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2076-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2076-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="b2076-119">See also</span></span>

- [<span data-ttu-id="b2076-120">调试结构</span><span class="sxs-lookup"><span data-stu-id="b2076-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="b2076-121">调试</span><span class="sxs-lookup"><span data-stu-id="b2076-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
