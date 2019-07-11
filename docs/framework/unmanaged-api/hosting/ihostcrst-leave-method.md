---
title: IHostCrst::Leave 方法
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f260e1351c8aa14961a10e0f7087bd076752785d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763765"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="6335a-102">IHostCrst::Leave 方法</span><span class="sxs-lookup"><span data-stu-id="6335a-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="6335a-103">离开临界区的当前实例所表示[IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="6335a-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6335a-104">语法</span><span class="sxs-lookup"><span data-stu-id="6335a-104">Syntax</span></span>  
  
```cpp  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6335a-105">返回值</span><span class="sxs-lookup"><span data-stu-id="6335a-105">Return Value</span></span>  
  
|<span data-ttu-id="6335a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6335a-106">HRESULT</span></span>|<span data-ttu-id="6335a-107">描述</span><span class="sxs-lookup"><span data-stu-id="6335a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6335a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6335a-108">S_OK</span></span>|<span data-ttu-id="6335a-109">`Leave` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="6335a-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="6335a-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6335a-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6335a-111">公共语言运行时 (CLR) 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="6335a-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6335a-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6335a-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6335a-113">呼叫已超时。</span><span class="sxs-lookup"><span data-stu-id="6335a-113">The call timed out.</span></span>|  
|<span data-ttu-id="6335a-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6335a-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6335a-115">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="6335a-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6335a-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6335a-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6335a-117">事件已取消时被阻塞的线程或纤程正在等待它。</span><span class="sxs-lookup"><span data-stu-id="6335a-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6335a-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6335a-118">E_FAIL</span></span>|<span data-ttu-id="6335a-119">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="6335a-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6335a-120">如果某方法返回 E_FAIL，CLR 不再在进程内可用。</span><span class="sxs-lookup"><span data-stu-id="6335a-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6335a-121">对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6335a-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6335a-122">备注</span><span class="sxs-lookup"><span data-stu-id="6335a-122">Remarks</span></span>  
 <span data-ttu-id="6335a-123">`Leave` 使 CLR 能够直接与主机的线程处理实现中，而不是使用对应 Win32 通信`LeaveCriticalSection`函数。</span><span class="sxs-lookup"><span data-stu-id="6335a-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="6335a-124">表示由当前的临界区的所有权的线程`IHostCrst`实例必须调用`Leave`后每次进入该关键部分。</span><span class="sxs-lookup"><span data-stu-id="6335a-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6335a-125">要求</span><span class="sxs-lookup"><span data-stu-id="6335a-125">Requirements</span></span>  
 <span data-ttu-id="6335a-126">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6335a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6335a-127">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6335a-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6335a-128">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="6335a-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6335a-129">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6335a-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6335a-130">请参阅</span><span class="sxs-lookup"><span data-stu-id="6335a-130">See also</span></span>

- [<span data-ttu-id="6335a-131">ICLRSyncManager 接口</span><span class="sxs-lookup"><span data-stu-id="6335a-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="6335a-132">IHostCrst 接口</span><span class="sxs-lookup"><span data-stu-id="6335a-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="6335a-133">IHostSyncManager 接口</span><span class="sxs-lookup"><span data-stu-id="6335a-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
