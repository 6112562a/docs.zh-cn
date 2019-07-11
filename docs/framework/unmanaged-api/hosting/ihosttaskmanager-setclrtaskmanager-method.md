---
title: IHostTaskManager::SetCLRTaskManager 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc5008461acc3b0653c53cee70cbfe89c90a440b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749394"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="6c566-102">IHostTaskManager::SetCLRTaskManager 方法</span><span class="sxs-lookup"><span data-stu-id="6c566-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="6c566-103">为宿主提供的接口指针到[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)由公共语言运行时 (CLR) 实现的实例。</span><span class="sxs-lookup"><span data-stu-id="6c566-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c566-104">语法</span><span class="sxs-lookup"><span data-stu-id="6c566-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c566-105">参数</span><span class="sxs-lookup"><span data-stu-id="6c566-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="6c566-106">[in]一个指向`ICLRTaskManager`由公共语言运行时实现的实例。</span><span class="sxs-lookup"><span data-stu-id="6c566-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c566-107">返回值</span><span class="sxs-lookup"><span data-stu-id="6c566-107">Return Value</span></span>  
  
|<span data-ttu-id="6c566-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c566-108">HRESULT</span></span>|<span data-ttu-id="6c566-109">描述</span><span class="sxs-lookup"><span data-stu-id="6c566-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c566-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c566-110">S_OK</span></span>|<span data-ttu-id="6c566-111">`SetCLRTaskManager` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="6c566-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="6c566-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c566-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c566-113">CLR 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="6c566-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c566-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c566-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c566-115">呼叫已超时。</span><span class="sxs-lookup"><span data-stu-id="6c566-115">The call timed out.</span></span>|  
|<span data-ttu-id="6c566-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c566-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c566-117">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="6c566-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c566-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c566-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c566-119">事件已取消时被阻塞的线程或纤程正在等待它。</span><span class="sxs-lookup"><span data-stu-id="6c566-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c566-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c566-120">E_FAIL</span></span>|<span data-ttu-id="6c566-121">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="6c566-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c566-122">如果某方法返回 E_FAIL，CLR 不再在进程内可用。</span><span class="sxs-lookup"><span data-stu-id="6c566-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c566-123">对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="6c566-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c566-124">备注</span><span class="sxs-lookup"><span data-stu-id="6c566-124">Remarks</span></span>  
 <span data-ttu-id="6c566-125">运行时调用`SetCLRTaskManager`若要向主机提供的接口指针到`ICLRTaskManager`实例。</span><span class="sxs-lookup"><span data-stu-id="6c566-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c566-126">要求</span><span class="sxs-lookup"><span data-stu-id="6c566-126">Requirements</span></span>  
 <span data-ttu-id="6c566-127">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c566-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c566-128">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6c566-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c566-129">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="6c566-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c566-130">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c566-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c566-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="6c566-131">See also</span></span>

- [<span data-ttu-id="6c566-132">ICLRTask 接口</span><span class="sxs-lookup"><span data-stu-id="6c566-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="6c566-133">ICLRTaskManager 接口</span><span class="sxs-lookup"><span data-stu-id="6c566-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="6c566-134">IHostTask 接口</span><span class="sxs-lookup"><span data-stu-id="6c566-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="6c566-135">IHostTaskManager 接口</span><span class="sxs-lookup"><span data-stu-id="6c566-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
