---
title: ICLRGCManager::SetGCStartupLimits 方法
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b25f73e9af77faadbc691255cb3139498f5d25c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779710"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a><span data-ttu-id="91959-102">ICLRGCManager::SetGCStartupLimits 方法</span><span class="sxs-lookup"><span data-stu-id="91959-102">ICLRGCManager::SetGCStartupLimits Method</span></span>
<span data-ttu-id="91959-103">设置垃圾回收段的大小和第 0 代垃圾回收系统的最大大小。</span><span class="sxs-lookup"><span data-stu-id="91959-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="91959-104">从.NET Framework 4.5 开始，你可以设置片段的大小和最大第 0 代大小为值大于`DWORD`通过使用[ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="91959-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91959-105">语法</span><span class="sxs-lookup"><span data-stu-id="91959-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91959-106">参数</span><span class="sxs-lookup"><span data-stu-id="91959-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="91959-107">[in]垃圾回收段指定的大小。</span><span class="sxs-lookup"><span data-stu-id="91959-107">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="91959-108">最小的段大小为 4 MB。</span><span class="sxs-lookup"><span data-stu-id="91959-108">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="91959-109">段可以增加增量为 1 MB 或更大。</span><span class="sxs-lookup"><span data-stu-id="91959-109">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="91959-110">[in]第 0 代为指定的最大大小。</span><span class="sxs-lookup"><span data-stu-id="91959-110">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="91959-111">最小的第 0 代大小为 64 KB。</span><span class="sxs-lookup"><span data-stu-id="91959-111">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91959-112">返回值</span><span class="sxs-lookup"><span data-stu-id="91959-112">Return Value</span></span>  
  
|<span data-ttu-id="91959-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="91959-113">HRESULT</span></span>|<span data-ttu-id="91959-114">描述</span><span class="sxs-lookup"><span data-stu-id="91959-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="91959-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="91959-115">S_OK</span></span>|<span data-ttu-id="91959-116">`SetGCStartupLimits` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="91959-116">`SetGCStartupLimits` returned successfully.</span></span>|  
|<span data-ttu-id="91959-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="91959-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="91959-118">公共语言运行时 (CLR) 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="91959-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="91959-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="91959-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="91959-120">呼叫已超时。</span><span class="sxs-lookup"><span data-stu-id="91959-120">The call timed out.</span></span>|  
|<span data-ttu-id="91959-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="91959-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="91959-122">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="91959-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="91959-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="91959-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="91959-124">事件已取消时被阻塞的线程或纤程正在等待它。</span><span class="sxs-lookup"><span data-stu-id="91959-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="91959-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="91959-125">E_FAIL</span></span>|<span data-ttu-id="91959-126">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="91959-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="91959-127">方法返回 E_FAIL 后，CLR 不再在进程中使用。</span><span class="sxs-lookup"><span data-stu-id="91959-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="91959-128">对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="91959-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91959-129">备注</span><span class="sxs-lookup"><span data-stu-id="91959-129">Remarks</span></span>  
 <span data-ttu-id="91959-130">值的`SetGCStartupLimits`集可以指定仅一次。</span><span class="sxs-lookup"><span data-stu-id="91959-130">The values that `SetGCStartupLimits` sets can be specified only once.</span></span> <span data-ttu-id="91959-131">更高版本调用`SetGCStartupLimits`将被忽略。</span><span class="sxs-lookup"><span data-stu-id="91959-131">Later calls to `SetGCStartupLimits` are ignored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91959-132">要求</span><span class="sxs-lookup"><span data-stu-id="91959-132">Requirements</span></span>  
 <span data-ttu-id="91959-133">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91959-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91959-134">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="91959-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="91959-135">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="91959-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91959-136">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91959-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91959-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="91959-137">See also</span></span>

- [<span data-ttu-id="91959-138">自动内存管理</span><span class="sxs-lookup"><span data-stu-id="91959-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="91959-139">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="91959-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="91959-140">ICLRControl 接口</span><span class="sxs-lookup"><span data-stu-id="91959-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="91959-141">ICLRGCManager 接口</span><span class="sxs-lookup"><span data-stu-id="91959-141">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
