---
title: IHostIoCompletionManager::CreateIoCompletionPort 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CreateIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CreateIoCompletionPort method [.NET Framework hosting]
- CreateIoCompletionPort method [.NET Framework hosting]
ms.assetid: 907a2b43-68db-44a7-acac-89e792e7bb3c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d50ea76c4d6448173002f720e1779233522ef499
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736522"
---
# <a name="ihostiocompletionmanagercreateiocompletionport-method"></a><span data-ttu-id="d37c2-102">IHostIoCompletionManager::CreateIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="d37c2-102">IHostIoCompletionManager::CreateIoCompletionPort Method</span></span>
<span data-ttu-id="d37c2-103">主机创建新的 I/O 完成端口的请求。</span><span class="sxs-lookup"><span data-stu-id="d37c2-103">Requests that the host create a new I/O completion port.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d37c2-104">语法</span><span class="sxs-lookup"><span data-stu-id="d37c2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateIoCompletionPort (  
    [out] HANDLE *phPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d37c2-105">参数</span><span class="sxs-lookup"><span data-stu-id="d37c2-105">Parameters</span></span>  
 `phPort`  
 <span data-ttu-id="d37c2-106">[out]指向新创建的 I/O 完成端口或 0 （零），如果无法创建该端口的句柄的指针。</span><span class="sxs-lookup"><span data-stu-id="d37c2-106">[out] A pointer to a handle to the newly created I/O completion port, or 0 (zero), if the port could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d37c2-107">返回值</span><span class="sxs-lookup"><span data-stu-id="d37c2-107">Return Value</span></span>  
  
|<span data-ttu-id="d37c2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d37c2-108">HRESULT</span></span>|<span data-ttu-id="d37c2-109">描述</span><span class="sxs-lookup"><span data-stu-id="d37c2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d37c2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d37c2-110">S_OK</span></span>|<span data-ttu-id="d37c2-111">`CreateIoCompletionPort` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="d37c2-111">`CreateIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="d37c2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d37c2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d37c2-113">公共语言运行时 (CLR) 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="d37c2-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d37c2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d37c2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d37c2-115">呼叫已超时。</span><span class="sxs-lookup"><span data-stu-id="d37c2-115">The call timed out.</span></span>|  
|<span data-ttu-id="d37c2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d37c2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d37c2-117">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="d37c2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d37c2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d37c2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d37c2-119">事件已取消时被阻塞的线程或纤程正在等待它。</span><span class="sxs-lookup"><span data-stu-id="d37c2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d37c2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d37c2-120">E_FAIL</span></span>|<span data-ttu-id="d37c2-121">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="d37c2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d37c2-122">如果某方法返回 E_FAIL，CLR 不再在进程内可用。</span><span class="sxs-lookup"><span data-stu-id="d37c2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d37c2-123">对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="d37c2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d37c2-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="d37c2-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="d37c2-125">没有足够的内存是可用于分配请求的资源。</span><span class="sxs-lookup"><span data-stu-id="d37c2-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d37c2-126">备注</span><span class="sxs-lookup"><span data-stu-id="d37c2-126">Remarks</span></span>  
 <span data-ttu-id="d37c2-127">CLR 调用`CreateIoCompletionPort`方法来请求主机创建新的 I/O 完成端口。</span><span class="sxs-lookup"><span data-stu-id="d37c2-127">The CLR calls the `CreateIoCompletionPort` method to request that the host create a new I/O completion port.</span></span> <span data-ttu-id="d37c2-128">它将 I/O 操作绑定到此端口通过调用[ihostiocompletionmanager:: Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="d37c2-128">It binds I/O operations to this port through a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span> <span data-ttu-id="d37c2-129">在宿主报告状态返回给 CLR 通过调用[iclriocompletionmanager:: Oncomplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d37c2-129">The host reports status back to the CLR by calling [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d37c2-130">要求</span><span class="sxs-lookup"><span data-stu-id="d37c2-130">Requirements</span></span>  
 <span data-ttu-id="d37c2-131">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d37c2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d37c2-132">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d37c2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d37c2-133">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="d37c2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d37c2-134">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d37c2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d37c2-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="d37c2-135">See also</span></span>

- [<span data-ttu-id="d37c2-136">ICLRIoCompletionManager 接口</span><span class="sxs-lookup"><span data-stu-id="d37c2-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="d37c2-137">IHostIoCompletionManager 接口</span><span class="sxs-lookup"><span data-stu-id="d37c2-137">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
