---
title: CorDebugCreateProcessFlags 枚举
ms.date: 03/30/2017
api_name:
- CorDebugCreateProcessFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugCreateProcessFlags
helpviewer_keywords:
- CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83cee30ed9831accb96de17768f63e7f401908f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495940"
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="d81bf-102">CorDebugCreateProcessFlags 枚举</span><span class="sxs-lookup"><span data-stu-id="d81bf-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="d81bf-103">提供了更多调试选项，可在调用[icordebug:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d81bf-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d81bf-104">语法</span><span class="sxs-lookup"><span data-stu-id="d81bf-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d81bf-105">成员</span><span class="sxs-lookup"><span data-stu-id="d81bf-105">Members</span></span>  
  
|<span data-ttu-id="d81bf-106">成员</span><span class="sxs-lookup"><span data-stu-id="d81bf-106">Member</span></span>|<span data-ttu-id="d81bf-107">描述</span><span class="sxs-lookup"><span data-stu-id="d81bf-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="d81bf-108">不设置任何特殊选项。</span><span class="sxs-lookup"><span data-stu-id="d81bf-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d81bf-109">要求</span><span class="sxs-lookup"><span data-stu-id="d81bf-109">Requirements</span></span>  
 <span data-ttu-id="d81bf-110">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d81bf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d81bf-111">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d81bf-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d81bf-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d81bf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d81bf-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d81bf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d81bf-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="d81bf-114">See also</span></span>
- [<span data-ttu-id="d81bf-115">调试枚举</span><span class="sxs-lookup"><span data-stu-id="d81bf-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
