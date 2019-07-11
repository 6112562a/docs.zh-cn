---
title: IHostSemaphore::ReleaseSemaphore 方法
ms.date: 03/30/2017
api_name:
- IHostSemaphore.ReleaseSemaphore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::ReleaseSemaphore
helpviewer_keywords:
- ReleaseSemaphore method [.NET Framework hosting]
- IHostSemaphore::ReleaseSemaphore method [.NET Framework hosting]
ms.assetid: a343d197-979a-4ac6-ab8c-cb8a05f3120e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e977133d722edc7d090d07cd117ee282a8d29cb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753577"
---
# <a name="ihostsemaphorereleasesemaphore-method"></a><span data-ttu-id="cb65d-102">IHostSemaphore::ReleaseSemaphore 方法</span><span class="sxs-lookup"><span data-stu-id="cb65d-102">IHostSemaphore::ReleaseSemaphore Method</span></span>
<span data-ttu-id="cb65d-103">当前计数[IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)实例指定的量。</span><span class="sxs-lookup"><span data-stu-id="cb65d-103">Increases the count of the current [IHostSemaphore](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md) instance by the specified amount.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb65d-104">语法</span><span class="sxs-lookup"><span data-stu-id="cb65d-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseSemaphore (  
    [in]  LONG  lReleaseCount,  
    [out] LONG  *lpPreviousCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb65d-105">参数</span><span class="sxs-lookup"><span data-stu-id="cb65d-105">Parameters</span></span>  
 `lReleaseCount`  
 <span data-ttu-id="cb65d-106">[in]当前计数增加的量`IHostSemaphore`实例。</span><span class="sxs-lookup"><span data-stu-id="cb65d-106">[in] The amount by which to increase the count of the current `IHostSemaphore` instance.</span></span> <span data-ttu-id="cb65d-107">此数量必须大于零。</span><span class="sxs-lookup"><span data-stu-id="cb65d-107">This amount must be greater than zero.</span></span>  
  
 `lpPreviousCount`  
 <span data-ttu-id="cb65d-108">[out]一个指向前一个计数或如果调用方不需要前一个计数，则为 null。</span><span class="sxs-lookup"><span data-stu-id="cb65d-108">[out] A pointer to the previous count, or null if the caller does not require the previous count.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb65d-109">返回值</span><span class="sxs-lookup"><span data-stu-id="cb65d-109">Return Value</span></span>  
  
|<span data-ttu-id="cb65d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cb65d-110">HRESULT</span></span>|<span data-ttu-id="cb65d-111">描述</span><span class="sxs-lookup"><span data-stu-id="cb65d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cb65d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cb65d-112">S_OK</span></span>|<span data-ttu-id="cb65d-113">`ReleaseSemaphore` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="cb65d-113">`ReleaseSemaphore` returned successfully.</span></span>|  
|<span data-ttu-id="cb65d-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cb65d-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cb65d-115">公共语言运行时 (CLR) 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="cb65d-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cb65d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cb65d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cb65d-117">呼叫已超时。</span><span class="sxs-lookup"><span data-stu-id="cb65d-117">The call timed out.</span></span>|  
|<span data-ttu-id="cb65d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cb65d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cb65d-119">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="cb65d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cb65d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cb65d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cb65d-121">事件已取消时被阻塞的线程或纤程正在等待它。</span><span class="sxs-lookup"><span data-stu-id="cb65d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cb65d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cb65d-122">E_FAIL</span></span>|<span data-ttu-id="cb65d-123">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="cb65d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cb65d-124">如果某方法返回 E_FAIL，CLR 不再在进程内可用。</span><span class="sxs-lookup"><span data-stu-id="cb65d-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cb65d-125">对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="cb65d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb65d-126">备注</span><span class="sxs-lookup"><span data-stu-id="cb65d-126">Remarks</span></span>  
 <span data-ttu-id="cb65d-127">CLR 通常会调用`ReleaseSemaphore`用于通知宿主，它已完成使用资源，将为 1 的值传递`lReleaseCount`参数。</span><span class="sxs-lookup"><span data-stu-id="cb65d-127">The CLR typically calls `ReleaseSemaphore` to notify the host that it has finished using a resource, passing a value of 1 for the `lReleaseCount` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb65d-128">要求</span><span class="sxs-lookup"><span data-stu-id="cb65d-128">Requirements</span></span>  
 <span data-ttu-id="cb65d-129">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb65d-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb65d-130">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cb65d-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cb65d-131">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="cb65d-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb65d-132">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb65d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb65d-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="cb65d-133">See also</span></span>

- [<span data-ttu-id="cb65d-134">ICLRSyncManager 接口</span><span class="sxs-lookup"><span data-stu-id="cb65d-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="cb65d-135">IHostAutoEvent 接口</span><span class="sxs-lookup"><span data-stu-id="cb65d-135">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="cb65d-136">IHostManualEvent 接口</span><span class="sxs-lookup"><span data-stu-id="cb65d-136">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="cb65d-137">IHostSemaphore 接口</span><span class="sxs-lookup"><span data-stu-id="cb65d-137">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="cb65d-138">IHostSyncManager 接口</span><span class="sxs-lookup"><span data-stu-id="cb65d-138">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
