---
title: CorDebugIlToNativeMappingTypes 枚举
ms.date: 03/30/2017
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
ms.openlocfilehash: 949d04fe8d9ce492fb320fb4732677ffb35302ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132829"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="80344-102">CorDebugIlToNativeMappingTypes 枚举</span><span class="sxs-lookup"><span data-stu-id="80344-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="80344-103">指示由 COR_DEBUG_IL_TO_NATIVE_MAP 结构的实例表示的一系列特定的本机指令是否对应于一个特殊的代码区域。</span><span class="sxs-lookup"><span data-stu-id="80344-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80344-104">语法</span><span class="sxs-lookup"><span data-stu-id="80344-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="80344-105">Members</span><span class="sxs-lookup"><span data-stu-id="80344-105">Members</span></span>  
  
|<span data-ttu-id="80344-106">成员</span><span class="sxs-lookup"><span data-stu-id="80344-106">Member</span></span>|<span data-ttu-id="80344-107">描述</span><span class="sxs-lookup"><span data-stu-id="80344-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="80344-108">本机指令的范围不对应于任何特殊代码区域。</span><span class="sxs-lookup"><span data-stu-id="80344-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="80344-109">本机指令的范围对应于序言。</span><span class="sxs-lookup"><span data-stu-id="80344-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="80344-110">本机指令的范围对应于 epilog。</span><span class="sxs-lookup"><span data-stu-id="80344-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="80344-111">要求</span><span class="sxs-lookup"><span data-stu-id="80344-111">Requirements</span></span>  
 <span data-ttu-id="80344-112">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="80344-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80344-113">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80344-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80344-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80344-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80344-115">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80344-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80344-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="80344-116">See also</span></span>

- [<span data-ttu-id="80344-117">GetILToNativeMapping 方法</span><span class="sxs-lookup"><span data-stu-id="80344-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="80344-118">调试枚举</span><span class="sxs-lookup"><span data-stu-id="80344-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
