---
title: IHostIoCompletionManager::SetCLRIoCompletionManager 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.SetCLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager::SetCLRIoCompletionManager method [.NET Framework hosting]
- SetCLRIoCompletionManager method [.NET Framework hosting]
ms.assetid: 4254bb01-3a14-4f34-a3be-60ff1f5072b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97d4561c34c03eefc7487f5f96b7a490a480ac19
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780760"
---
# <a name="ihostiocompletionmanagersetclriocompletionmanager-method"></a><span data-ttu-id="15794-102">IHostIoCompletionManager::SetCLRIoCompletionManager 方法</span><span class="sxs-lookup"><span data-stu-id="15794-102">IHostIoCompletionManager::SetCLRIoCompletionManager Method</span></span>
<span data-ttu-id="15794-103">为宿主提供的接口指针到[ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)由公共语言运行时 (CLR) 实现的实例。</span><span class="sxs-lookup"><span data-stu-id="15794-103">Provides the host with an interface pointer to the [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15794-104">语法</span><span class="sxs-lookup"><span data-stu-id="15794-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRIoCompletionManager (  
    [in] ICLRIoCompletionManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15794-105">参数</span><span class="sxs-lookup"><span data-stu-id="15794-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="15794-106">[in]接口指针`ICLRIoCompletionManager`由 CLR 提供的实例。</span><span class="sxs-lookup"><span data-stu-id="15794-106">[in] An interface pointer to an `ICLRIoCompletionManager` instance provided by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15794-107">返回值</span><span class="sxs-lookup"><span data-stu-id="15794-107">Return Value</span></span>  
  
|<span data-ttu-id="15794-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15794-108">HRESULT</span></span>|<span data-ttu-id="15794-109">描述</span><span class="sxs-lookup"><span data-stu-id="15794-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15794-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="15794-110">S_OK</span></span>|<span data-ttu-id="15794-111">`SetCLRIoCompletionManager` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="15794-111">`SetCLRIoCompletionManager` returned successfully.</span></span>|  
|<span data-ttu-id="15794-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="15794-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="15794-113">CLR 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="15794-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="15794-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="15794-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="15794-115">呼叫已超时。</span><span class="sxs-lookup"><span data-stu-id="15794-115">The call timed out.</span></span>|  
|<span data-ttu-id="15794-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="15794-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="15794-117">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="15794-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="15794-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="15794-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="15794-119">事件已取消时被阻塞的线程或纤程正在等待它。</span><span class="sxs-lookup"><span data-stu-id="15794-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="15794-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="15794-120">E_FAIL</span></span>|<span data-ttu-id="15794-121">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="15794-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="15794-122">如果某方法返回 E_FAIL，CLR 不再在进程内可用。</span><span class="sxs-lookup"><span data-stu-id="15794-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="15794-123">对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="15794-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15794-124">备注</span><span class="sxs-lookup"><span data-stu-id="15794-124">Remarks</span></span>  
 <span data-ttu-id="15794-125">CLR 已调用后`SetCLRIoCompletionManager`，主机必须调用[iclriocompletionmanager:: Oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) I/O 请求完成时通知 CLR。</span><span class="sxs-lookup"><span data-stu-id="15794-125">After the CLR has called `SetCLRIoCompletionManager`, the host must call [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) to notify the CLR when an I/O request has been completed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15794-126">要求</span><span class="sxs-lookup"><span data-stu-id="15794-126">Requirements</span></span>  
 <span data-ttu-id="15794-127">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15794-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15794-128">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="15794-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15794-129">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="15794-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15794-130">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15794-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15794-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="15794-131">See also</span></span>

- [<span data-ttu-id="15794-132">ICLRIoCompletionManager 接口</span><span class="sxs-lookup"><span data-stu-id="15794-132">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="15794-133">IHostIoCompletionManager 接口</span><span class="sxs-lookup"><span data-stu-id="15794-133">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
