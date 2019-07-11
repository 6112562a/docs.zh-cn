---
title: CorDebugMappingResult 枚举
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2042d0936359a85d203375c42be0d8a096f004e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739765"
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="7c637-102">CorDebugMappingResult 枚举</span><span class="sxs-lookup"><span data-stu-id="7c637-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="7c637-103">提供如何获取指令指针 (IP) 的值的详细信息。</span><span class="sxs-lookup"><span data-stu-id="7c637-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c637-104">语法</span><span class="sxs-lookup"><span data-stu-id="7c637-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="7c637-105">成员</span><span class="sxs-lookup"><span data-stu-id="7c637-105">Members</span></span>  
  
|<span data-ttu-id="7c637-106">成员</span><span class="sxs-lookup"><span data-stu-id="7c637-106">Member</span></span>|<span data-ttu-id="7c637-107">描述</span><span class="sxs-lookup"><span data-stu-id="7c637-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="7c637-108">本机代码是在序言中，因此 IP 的值为 0。</span><span class="sxs-lookup"><span data-stu-id="7c637-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="7c637-109">本机代码是在 epilog 中，因此 IP 的值是该方法的最后一个指令的地址。</span><span class="sxs-lookup"><span data-stu-id="7c637-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="7c637-110">没有映射信息，则对于方法，因此 IP 的值为 0。</span><span class="sxs-lookup"><span data-stu-id="7c637-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="7c637-111">尽管没有映射信息的方法，但当前的地址不能映射到 Microsoft 中间语言 (MSIL) 代码。</span><span class="sxs-lookup"><span data-stu-id="7c637-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="7c637-112">IP 的值为 0。</span><span class="sxs-lookup"><span data-stu-id="7c637-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="7c637-113">该方法准确地映射到 MSIL 代码，或者已解释了框架，因此 IP 的值为精确值。</span><span class="sxs-lookup"><span data-stu-id="7c637-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="7c637-114">已成功映射方法，但 IP 的值可能为近似值。</span><span class="sxs-lookup"><span data-stu-id="7c637-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c637-115">备注</span><span class="sxs-lookup"><span data-stu-id="7c637-115">Remarks</span></span>  
 <span data-ttu-id="7c637-116">可以使用[icordebugilframe:: Getip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)方法来获取指令指针的值。</span><span class="sxs-lookup"><span data-stu-id="7c637-116">You can use the [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c637-117">要求</span><span class="sxs-lookup"><span data-stu-id="7c637-117">Requirements</span></span>  
 <span data-ttu-id="7c637-118">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c637-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c637-119">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c637-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c637-120">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c637-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c637-121">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c637-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c637-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="7c637-122">See also</span></span>

- [<span data-ttu-id="7c637-123">调试枚举</span><span class="sxs-lookup"><span data-stu-id="7c637-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
