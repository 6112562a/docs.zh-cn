---
title: ASM_CACHE_FLAGS 枚举
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27caa9916b5adab2b2049a8f66ac34fed40e4d7f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778572"
---
# <a name="asmcacheflags-enumeration"></a><span data-ttu-id="99682-102">ASM_CACHE_FLAGS 枚举</span><span class="sxs-lookup"><span data-stu-id="99682-102">ASM_CACHE_FLAGS Enumeration</span></span>
<span data-ttu-id="99682-103">指示由表示程序集的源[IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)全局程序集缓存中。</span><span class="sxs-lookup"><span data-stu-id="99682-103">Indicates the source of an assembly that is represented by [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99682-104">语法</span><span class="sxs-lookup"><span data-stu-id="99682-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="99682-105">成员</span><span class="sxs-lookup"><span data-stu-id="99682-105">Members</span></span>  
  
|<span data-ttu-id="99682-106">成员</span><span class="sxs-lookup"><span data-stu-id="99682-106">Member</span></span>|<span data-ttu-id="99682-107">描述</span><span class="sxs-lookup"><span data-stu-id="99682-107">Description</span></span>|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|<span data-ttu-id="99682-108">枚举通过使用 Ngen.exe 预编译的程序集的缓存。</span><span class="sxs-lookup"><span data-stu-id="99682-108">Enumerates the cache of precompiled assemblies by using Ngen.exe.</span></span>|  
|`ASM_CACHE_GAC`|<span data-ttu-id="99682-109">枚举在全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="99682-109">Enumerates the global assembly cache.</span></span>|  
|`ASM_CACHE_DOWNLOAD`|<span data-ttu-id="99682-110">枚举程序集已经根据需要下载或已经进行了卷影复制。</span><span class="sxs-lookup"><span data-stu-id="99682-110">Enumerates the assemblies that have been downloaded on demand or that have been shadow-copied.</span></span>|  
|`ASM_CACHE_ROOT`|<span data-ttu-id="99682-111">指示[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)函数应返回路径到公共语言运行时 (CLR) 2.0 版的全局程序集缓存。</span><span class="sxs-lookup"><span data-stu-id="99682-111">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for the common language runtime (CLR) version 2.0.</span></span> <span data-ttu-id="99682-112">仅对的调用上下文中有意义[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)。</span><span class="sxs-lookup"><span data-stu-id="99682-112">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
|`ASM_CACHE_ROOT_EX`|<span data-ttu-id="99682-113">指示[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)函数应为 CLR 版本 4 到全局程序集缓存中返回的路径。</span><span class="sxs-lookup"><span data-stu-id="99682-113">Indicates that the [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md) function should return the path to the global assembly cache for CLR version 4.</span></span> <span data-ttu-id="99682-114">仅对的调用上下文中有意义[GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)。</span><span class="sxs-lookup"><span data-stu-id="99682-114">Meaningful only in the context of a call to [GetCachePath](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99682-115">要求</span><span class="sxs-lookup"><span data-stu-id="99682-115">Requirements</span></span>  
 <span data-ttu-id="99682-116">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="99682-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99682-117">**标头：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="99682-117">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="99682-118">**库：** 包含为 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="99682-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="99682-119">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99682-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99682-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="99682-120">See also</span></span>

- [<span data-ttu-id="99682-121">GetCachePath 函数</span><span class="sxs-lookup"><span data-stu-id="99682-121">GetCachePath Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)
- [<span data-ttu-id="99682-122">IAssemblyCacheItem 接口</span><span class="sxs-lookup"><span data-stu-id="99682-122">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
- [<span data-ttu-id="99682-123">合成枚举</span><span class="sxs-lookup"><span data-stu-id="99682-123">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
