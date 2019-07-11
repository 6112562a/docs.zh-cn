---
title: IHostIoCompletionManager::CloseIoCompletionPort 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cceced01b34f10cf38b41cfcb2a17059650f9ad9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736538"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="e7cec-102">IHostIoCompletionManager::CloseIoCompletionPort 方法</span><span class="sxs-lookup"><span data-stu-id="e7cec-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="e7cec-103">请求主机关闭以前通过调用到打开的端口[CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)。</span><span class="sxs-lookup"><span data-stu-id="e7cec-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7cec-104">语法</span><span class="sxs-lookup"><span data-stu-id="e7cec-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7cec-105">参数</span><span class="sxs-lookup"><span data-stu-id="e7cec-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="e7cec-106">[in]要关闭的端口的句柄。</span><span class="sxs-lookup"><span data-stu-id="e7cec-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e7cec-107">返回值</span><span class="sxs-lookup"><span data-stu-id="e7cec-107">Return Value</span></span>  
  
|<span data-ttu-id="e7cec-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e7cec-108">HRESULT</span></span>|<span data-ttu-id="e7cec-109">描述</span><span class="sxs-lookup"><span data-stu-id="e7cec-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7cec-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e7cec-110">S_OK</span></span>|<span data-ttu-id="e7cec-111">`CloseIoCompletionPort` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="e7cec-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="e7cec-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e7cec-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e7cec-113">公共语言运行时 (CLR) 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="e7cec-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e7cec-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e7cec-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e7cec-115">呼叫已超时。</span><span class="sxs-lookup"><span data-stu-id="e7cec-115">The call timed out.</span></span>|  
|<span data-ttu-id="e7cec-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e7cec-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e7cec-117">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="e7cec-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e7cec-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e7cec-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e7cec-119">事件已取消时被阻塞的线程或纤程正在等待它。</span><span class="sxs-lookup"><span data-stu-id="e7cec-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e7cec-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e7cec-120">E_FAIL</span></span>|<span data-ttu-id="e7cec-121">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="e7cec-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e7cec-122">如果某方法返回 E_FAIL，CLR 不再在进程内可用。</span><span class="sxs-lookup"><span data-stu-id="e7cec-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e7cec-123">对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="e7cec-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e7cec-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e7cec-124">E_INVALIDARG</span></span>|<span data-ttu-id="e7cec-125">传递了无效的端口句柄。</span><span class="sxs-lookup"><span data-stu-id="e7cec-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7cec-126">备注</span><span class="sxs-lookup"><span data-stu-id="e7cec-126">Remarks</span></span>  
 <span data-ttu-id="e7cec-127">`hPort` 必须由以前通过调用创建的端口的句柄`CreateIoCompletionPort`。</span><span class="sxs-lookup"><span data-stu-id="e7cec-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7cec-128">要求</span><span class="sxs-lookup"><span data-stu-id="e7cec-128">Requirements</span></span>  
 <span data-ttu-id="e7cec-129">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e7cec-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7cec-130">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e7cec-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7cec-131">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="e7cec-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7cec-132">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7cec-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7cec-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="e7cec-133">See also</span></span>

- [<span data-ttu-id="e7cec-134">ICLRIoCompletionManager 接口</span><span class="sxs-lookup"><span data-stu-id="e7cec-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="e7cec-135">IHostIoCompletionManager 接口</span><span class="sxs-lookup"><span data-stu-id="e7cec-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
