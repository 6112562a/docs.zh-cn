---
title: IHostTaskManager::GetCurrentTask 方法
ms.date: 03/30/2017
api_name:
- IHostTaskManager.GetCurrentTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::GetCurrentTask
helpviewer_keywords:
- GetCurrentTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::GetCurrentTask method [.NET Framework hosting]
ms.assetid: f17bca49-90bd-4dee-a5e1-b9a57ea46f85
topic_type:
- apiref
ms.openlocfilehash: d1d6ddfe7834a1c6f22b9195042d32363d6ea6cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133046"
---
# <a name="ihosttaskmanagergetcurrenttask-method"></a><span data-ttu-id="50844-102">IHostTaskManager::GetCurrentTask 方法</span><span class="sxs-lookup"><span data-stu-id="50844-102">IHostTaskManager::GetCurrentTask Method</span></span>
<span data-ttu-id="50844-103">获取一个接口指针，该指针指向正在进行此调用的操作系统线程上当前正在执行的任务。</span><span class="sxs-lookup"><span data-stu-id="50844-103">Gets an interface pointer to the task that is currently executing on the operating system thread from which this call is made.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50844-104">语法</span><span class="sxs-lookup"><span data-stu-id="50844-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentTask (  
    [out] IHostTask **pTask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50844-105">参数</span><span class="sxs-lookup"><span data-stu-id="50844-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="50844-106">弄指向表示当前正在执行的任务的[IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)实例的地址的指针; 如果当前没有执行任何任务，则为 null。</span><span class="sxs-lookup"><span data-stu-id="50844-106">[out] A pointer to the address of an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance that represents the currently executing task, or null, if no task is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50844-107">返回值</span><span class="sxs-lookup"><span data-stu-id="50844-107">Return Value</span></span>  
  
|<span data-ttu-id="50844-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50844-108">HRESULT</span></span>|<span data-ttu-id="50844-109">描述</span><span class="sxs-lookup"><span data-stu-id="50844-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50844-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="50844-110">S_OK</span></span>|<span data-ttu-id="50844-111">`GetCurrentTask` 成功返回。</span><span class="sxs-lookup"><span data-stu-id="50844-111">`GetCurrentTask` returned successfully.</span></span>|  
|<span data-ttu-id="50844-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50844-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50844-113">公共语言运行时（CLR）未加载到进程中，或 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="50844-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="50844-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="50844-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="50844-115">调用超时。</span><span class="sxs-lookup"><span data-stu-id="50844-115">The call timed out.</span></span>|  
|<span data-ttu-id="50844-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="50844-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="50844-117">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="50844-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="50844-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="50844-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="50844-119">已阻止的线程或纤程正在等待某个事件时，该事件被取消。</span><span class="sxs-lookup"><span data-stu-id="50844-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="50844-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50844-120">E_FAIL</span></span>|<span data-ttu-id="50844-121">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="50844-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50844-122">当方法返回 E_FAIL 时，CLR 在该进程内将不再可用。</span><span class="sxs-lookup"><span data-stu-id="50844-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="50844-123">对宿主方法的后续调用会返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="50844-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="50844-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="50844-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="50844-125">在宿主控件之外的操作系统线程上调用了 `GetCurrentTask`。</span><span class="sxs-lookup"><span data-stu-id="50844-125">`GetCurrentTask` was called on an operating system thread outside the control of the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50844-126">备注</span><span class="sxs-lookup"><span data-stu-id="50844-126">Remarks</span></span>  
 <span data-ttu-id="50844-127">宿主还可以将 `pTask` 参数设置为 null，以防止它在进入 CLR 时未启动的任务。</span><span class="sxs-lookup"><span data-stu-id="50844-127">The host can also set the `pTask` parameter to null to prevent a task that it did not initiate from entering the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50844-128">要求</span><span class="sxs-lookup"><span data-stu-id="50844-128">Requirements</span></span>  
 <span data-ttu-id="50844-129">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50844-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50844-130">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="50844-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50844-131">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="50844-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50844-132">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50844-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50844-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="50844-133">See also</span></span>

- [<span data-ttu-id="50844-134">ICLRTask 接口</span><span class="sxs-lookup"><span data-stu-id="50844-134">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="50844-135">ICLRTaskManager 接口</span><span class="sxs-lookup"><span data-stu-id="50844-135">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="50844-136">IHostTask 接口</span><span class="sxs-lookup"><span data-stu-id="50844-136">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="50844-137">IHostTaskManager 接口</span><span class="sxs-lookup"><span data-stu-id="50844-137">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
