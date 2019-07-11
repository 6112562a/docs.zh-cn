---
title: EMemoryCriticalLevel 枚举
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26b3761ab49f36c5f687ff2c62882667e044d299
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774220"
---
# <a name="ememorycriticallevel-enumeration"></a><span data-ttu-id="1b9be-102">EMemoryCriticalLevel 枚举</span><span class="sxs-lookup"><span data-stu-id="1b9be-102">EMemoryCriticalLevel Enumeration</span></span>
<span data-ttu-id="1b9be-103">包含指示失败的影响，何时已请求特定的内存分配但是却无法满足的值。</span><span class="sxs-lookup"><span data-stu-id="1b9be-103">Contains values that indicate the impact of a failure when a specific memory allocation has been requested but cannot be satisfied.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b9be-104">语法</span><span class="sxs-lookup"><span data-stu-id="1b9be-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a><span data-ttu-id="1b9be-105">成员</span><span class="sxs-lookup"><span data-stu-id="1b9be-105">Members</span></span>  
  
|<span data-ttu-id="1b9be-106">成员</span><span class="sxs-lookup"><span data-stu-id="1b9be-106">Member</span></span>|<span data-ttu-id="1b9be-107">描述</span><span class="sxs-lookup"><span data-stu-id="1b9be-107">Description</span></span>|  
|------------|-----------------|  
|`eAppDomainCritical`|<span data-ttu-id="1b9be-108">指示分配已请求分配在域中执行托管的代码的关键。</span><span class="sxs-lookup"><span data-stu-id="1b9be-108">Indicates that the allocation is critical for executing managed code in the domain that has requested the allocation.</span></span> <span data-ttu-id="1b9be-109">如果无法分配内存，CLR 不能保证域仍可使用。</span><span class="sxs-lookup"><span data-stu-id="1b9be-109">If memory cannot be allocated, the CLR cannot guarantee that the domain is still usable.</span></span> <span data-ttu-id="1b9be-110">主机决定要执行不能满足分配时的操作。</span><span class="sxs-lookup"><span data-stu-id="1b9be-110">The host decides what action to take when the allocation cannot be satisfied.</span></span> <span data-ttu-id="1b9be-111">它可以指示 CLR 中止`AppDomain`自动，或允许其继续运行通过调用方法[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="1b9be-111">It can instruct the CLR to abort the `AppDomain` automatically, or allow it to keep running by calling methods on [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).</span></span>|  
|`eProcessCritical`|<span data-ttu-id="1b9be-112">指示此分配是关键的过程中的托管代码执行。</span><span class="sxs-lookup"><span data-stu-id="1b9be-112">Indicates that the allocation is critical to the execution of managed code in the process.</span></span> <span data-ttu-id="1b9be-113">使用此值是在启动期间和运行终结器时。</span><span class="sxs-lookup"><span data-stu-id="1b9be-113">This value is used during startup and when running finalizers.</span></span> <span data-ttu-id="1b9be-114">如果无法分配内存，CLR 不能在过程中运行。</span><span class="sxs-lookup"><span data-stu-id="1b9be-114">If memory cannot be allocated, the CLR cannot operate in the process.</span></span> <span data-ttu-id="1b9be-115">如果分配失败时，CLR 会有效地禁用。</span><span class="sxs-lookup"><span data-stu-id="1b9be-115">If the allocation fails, the CLR is effectively disabled.</span></span> <span data-ttu-id="1b9be-116">到 CLR 中的所有后续调用失败，并 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1b9be-116">All subsequent calls into the CLR fail with HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`eTaskCritical`|<span data-ttu-id="1b9be-117">指示此分配是关键到正在运行的已请求分配的任务。</span><span class="sxs-lookup"><span data-stu-id="1b9be-117">Indicates that the allocation is critical to running the task that has requested the allocation.</span></span> <span data-ttu-id="1b9be-118">如果无法分配内存，则 CLR 不能保证可以执行该任务。</span><span class="sxs-lookup"><span data-stu-id="1b9be-118">If memory cannot be allocated, the CLR cannot guarantee that the task can be executed.</span></span> <span data-ttu-id="1b9be-119">出现故障时，CLR 将引发<xref:System.Threading.ThreadAbortException>物理操作系统线程上。</span><span class="sxs-lookup"><span data-stu-id="1b9be-119">In the event of failure, the CLR raises a <xref:System.Threading.ThreadAbortException> on the physical operation system thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b9be-120">备注</span><span class="sxs-lookup"><span data-stu-id="1b9be-120">Remarks</span></span>  
 <span data-ttu-id="1b9be-121">在中定义的内存分配方法[IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)并[IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)接口执行此类型的参数。</span><span class="sxs-lookup"><span data-stu-id="1b9be-121">The memory allocation methods defined in the [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) and [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfaces take a parameter of this type.</span></span> <span data-ttu-id="1b9be-122">根据失败的严重性，主机可以决定是否要立即失败分配请求，或等待，直到可以满足。</span><span class="sxs-lookup"><span data-stu-id="1b9be-122">Depending upon the severity of a failure, a host can decide whether to fail the allocation request immediately or to wait until it can be satisfied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b9be-123">要求</span><span class="sxs-lookup"><span data-stu-id="1b9be-123">Requirements</span></span>  
 <span data-ttu-id="1b9be-124">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b9be-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b9be-125">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1b9be-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b9be-126">**库：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b9be-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b9be-127">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b9be-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b9be-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="1b9be-128">See also</span></span>

- [<span data-ttu-id="1b9be-129">ICLRMemoryNotificationCallback 接口</span><span class="sxs-lookup"><span data-stu-id="1b9be-129">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="1b9be-130">承载枚举</span><span class="sxs-lookup"><span data-stu-id="1b9be-130">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
