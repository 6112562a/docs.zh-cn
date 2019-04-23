---
title: IHostManualEvent::Reset 方法
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b3de70e6bdecba6370174ee825d2dec7c14270e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148559"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="09944-102">IHostManualEvent::Reset 方法</span><span class="sxs-lookup"><span data-stu-id="09944-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="09944-103">重置当前[IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)为非终止状态的实例。</span><span class="sxs-lookup"><span data-stu-id="09944-103">Resets the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09944-104">语法</span><span class="sxs-lookup"><span data-stu-id="09944-104">Syntax</span></span>  
  
```  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="09944-105">返回值</span><span class="sxs-lookup"><span data-stu-id="09944-105">Return Value</span></span>  
  
|<span data-ttu-id="09944-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09944-106">HRESULT</span></span>|<span data-ttu-id="09944-107">描述</span><span class="sxs-lookup"><span data-stu-id="09944-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09944-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="09944-108">S_OK</span></span>|<span data-ttu-id="09944-109">`Reset` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="09944-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="09944-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="09944-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="09944-111">公共语言运行时 (CLR) 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="09944-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="09944-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="09944-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="09944-113">呼叫已超时。</span><span class="sxs-lookup"><span data-stu-id="09944-113">The call timed out.</span></span>|  
|<span data-ttu-id="09944-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="09944-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="09944-115">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="09944-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="09944-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="09944-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="09944-117">事件已取消时被阻塞的线程或纤程正在等待它。</span><span class="sxs-lookup"><span data-stu-id="09944-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="09944-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="09944-118">E_FAIL</span></span>|<span data-ttu-id="09944-119">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="09944-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="09944-120">如果某方法返回 E_FAIL，CLR 不再在进程内可用。</span><span class="sxs-lookup"><span data-stu-id="09944-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="09944-121">对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="09944-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09944-122">要求</span><span class="sxs-lookup"><span data-stu-id="09944-122">Requirements</span></span>  
 <span data-ttu-id="09944-123">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09944-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09944-124">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="09944-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09944-125">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="09944-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09944-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09944-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09944-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="09944-127">See also</span></span>

- [<span data-ttu-id="09944-128">ICLRSyncManager 接口</span><span class="sxs-lookup"><span data-stu-id="09944-128">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="09944-129">IHostAutoEvent 接口</span><span class="sxs-lookup"><span data-stu-id="09944-129">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="09944-130">IHostManualEvent 接口</span><span class="sxs-lookup"><span data-stu-id="09944-130">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="09944-131">IHostSemaphore 接口</span><span class="sxs-lookup"><span data-stu-id="09944-131">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="09944-132">IHostSyncManager 接口</span><span class="sxs-lookup"><span data-stu-id="09944-132">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
