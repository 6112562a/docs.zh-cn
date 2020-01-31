---
title: CorDebugExceptionUnwindCallbackType 枚举
ms.date: 03/30/2017
api_name:
- CorDebugExceptionUnwindCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionUnwindCallbackType
helpviewer_keywords:
- CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type:
- apiref
ms.openlocfilehash: e714c41812c8aaccd713115712df05744cc015e3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789388"
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="e19b3-102">CorDebugExceptionUnwindCallbackType 枚举</span><span class="sxs-lookup"><span data-stu-id="e19b3-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="e19b3-103">指示在展开阶段正由回调发送信号的事件。</span><span class="sxs-lookup"><span data-stu-id="e19b3-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e19b3-104">语法</span><span class="sxs-lookup"><span data-stu-id="e19b3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="e19b3-105">Members</span><span class="sxs-lookup"><span data-stu-id="e19b3-105">Members</span></span>  
  
|<span data-ttu-id="e19b3-106">成员</span><span class="sxs-lookup"><span data-stu-id="e19b3-106">Member</span></span>|<span data-ttu-id="e19b3-107">描述</span><span class="sxs-lookup"><span data-stu-id="e19b3-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="e19b3-108">展开进程的开头。</span><span class="sxs-lookup"><span data-stu-id="e19b3-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="e19b3-109">异常已被截取。</span><span class="sxs-lookup"><span data-stu-id="e19b3-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e19b3-110">需求</span><span class="sxs-lookup"><span data-stu-id="e19b3-110">Requirements</span></span>  
 <span data-ttu-id="e19b3-111">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e19b3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e19b3-112">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e19b3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e19b3-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e19b3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e19b3-114">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e19b3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e19b3-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e19b3-115">See also</span></span>

- [<span data-ttu-id="e19b3-116">调试枚举</span><span class="sxs-lookup"><span data-stu-id="e19b3-116">Debugging Enumerations</span></span>](debugging-enumerations.md)
