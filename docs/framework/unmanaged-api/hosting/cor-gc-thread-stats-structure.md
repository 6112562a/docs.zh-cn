---
title: COR_GC_THREAD_STATS 结构
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f56ceca5269ebffb29908c63e698ce794027d8a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768058"
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="93242-102">COR_GC_THREAD_STATS 结构</span><span class="sxs-lookup"><span data-stu-id="93242-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="93242-103">包含有关垃圾回收的每个线程统计信息。</span><span class="sxs-lookup"><span data-stu-id="93242-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93242-104">语法</span><span class="sxs-lookup"><span data-stu-id="93242-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="93242-105">成员</span><span class="sxs-lookup"><span data-stu-id="93242-105">Members</span></span>  
  
|<span data-ttu-id="93242-106">成员</span><span class="sxs-lookup"><span data-stu-id="93242-106">Member</span></span>|<span data-ttu-id="93242-107">描述</span><span class="sxs-lookup"><span data-stu-id="93242-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="93242-108">与当前相关联的线程上分配的内存字节数`COR_GC_THREAD_STATS`实例。</span><span class="sxs-lookup"><span data-stu-id="93242-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="93242-109">此数字将清零每次生成零垃圾回收发生时。</span><span class="sxs-lookup"><span data-stu-id="93242-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="93242-110">提升的字节数为更高版本生成的最新的垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="93242-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93242-111">备注</span><span class="sxs-lookup"><span data-stu-id="93242-111">Remarks</span></span>  
 <span data-ttu-id="93242-112">[Iclrtask:: Getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)需要使用输出参数的类型`COR_GC_THREAD_STATS`。</span><span class="sxs-lookup"><span data-stu-id="93242-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93242-113">要求</span><span class="sxs-lookup"><span data-stu-id="93242-113">Requirements</span></span>  
 <span data-ttu-id="93242-114">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="93242-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93242-115">**标头：** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="93242-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="93242-116">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="93242-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93242-117">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93242-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93242-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="93242-118">See also</span></span>

- [<span data-ttu-id="93242-119">承载结构</span><span class="sxs-lookup"><span data-stu-id="93242-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="93242-120">IHostTask 接口</span><span class="sxs-lookup"><span data-stu-id="93242-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
