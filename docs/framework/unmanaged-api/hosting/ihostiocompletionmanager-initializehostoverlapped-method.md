---
title: IHostIoCompletionManager::InitializeHostOverlapped 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d27799e427efd3659dc2864e7d1e8e2061c5c19
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780777"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="1db2e-102">IHostIoCompletionManager::InitializeHostOverlapped 方法</span><span class="sxs-lookup"><span data-stu-id="1db2e-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>
<span data-ttu-id="1db2e-103">为宿主提供初始化要追加到 Win32 的任何自定义数据的机会`OVERLAPPED`用于异步 I/O 请求的结构。</span><span class="sxs-lookup"><span data-stu-id="1db2e-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1db2e-104">语法</span><span class="sxs-lookup"><span data-stu-id="1db2e-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1db2e-105">参数</span><span class="sxs-lookup"><span data-stu-id="1db2e-105">Parameters</span></span>  
 `pvOverlapped`  
 <span data-ttu-id="1db2e-106">[in]一个指向 Win32`OVERLAPPED`结构将包括 I/O 请求。</span><span class="sxs-lookup"><span data-stu-id="1db2e-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1db2e-107">返回值</span><span class="sxs-lookup"><span data-stu-id="1db2e-107">Return Value</span></span>  
  
|<span data-ttu-id="1db2e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1db2e-108">HRESULT</span></span>|<span data-ttu-id="1db2e-109">描述</span><span class="sxs-lookup"><span data-stu-id="1db2e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1db2e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1db2e-110">S_OK</span></span>|<span data-ttu-id="1db2e-111">`InitializeHostOverlapped` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="1db2e-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="1db2e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1db2e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1db2e-113">公共语言运行时 (CLR) 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="1db2e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1db2e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1db2e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1db2e-115">呼叫已超时。</span><span class="sxs-lookup"><span data-stu-id="1db2e-115">The call timed out.</span></span>|  
|<span data-ttu-id="1db2e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1db2e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1db2e-117">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="1db2e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1db2e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1db2e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1db2e-119">事件已取消时被阻塞的线程或纤程正在等待它。</span><span class="sxs-lookup"><span data-stu-id="1db2e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1db2e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1db2e-120">E_FAIL</span></span>|<span data-ttu-id="1db2e-121">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="1db2e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1db2e-122">如果某方法返回 E_FAIL，CLR 不再在进程内可用。</span><span class="sxs-lookup"><span data-stu-id="1db2e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1db2e-123">对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="1db2e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1db2e-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1db2e-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1db2e-125">没有足够的内存是可用于分配请求的资源。</span><span class="sxs-lookup"><span data-stu-id="1db2e-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1db2e-126">备注</span><span class="sxs-lookup"><span data-stu-id="1db2e-126">Remarks</span></span>  
 <span data-ttu-id="1db2e-127">Windows 平台函数使用`OVERLAPPED`结构存储异步 I/O 请求的状态。</span><span class="sxs-lookup"><span data-stu-id="1db2e-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="1db2e-128">CLR 调用`InitializeHostOverlapped`方法，从而使主机能够自定义将数据追加到`OVERLAPPED`实例。</span><span class="sxs-lookup"><span data-stu-id="1db2e-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1db2e-129">若要获取对其自定义数据块的开头，主机必须设置偏移量的大小`OVERLAPPED`结构 (`sizeof(OVERLAPPED)`)。</span><span class="sxs-lookup"><span data-stu-id="1db2e-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="1db2e-130">返回值 E_OUTOFMEMORY 指示主机无法初始化其自定义数据。</span><span class="sxs-lookup"><span data-stu-id="1db2e-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="1db2e-131">在这种情况下，CLR 将报告错误并调用失败。</span><span class="sxs-lookup"><span data-stu-id="1db2e-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1db2e-132">要求</span><span class="sxs-lookup"><span data-stu-id="1db2e-132">Requirements</span></span>  
 <span data-ttu-id="1db2e-133">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1db2e-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1db2e-134">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1db2e-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1db2e-135">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="1db2e-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1db2e-136">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1db2e-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db2e-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="1db2e-137">See also</span></span>

- [<span data-ttu-id="1db2e-138">ICLRIoCompletionManager 接口</span><span class="sxs-lookup"><span data-stu-id="1db2e-138">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="1db2e-139">GetHostOverlappedSize 方法</span><span class="sxs-lookup"><span data-stu-id="1db2e-139">GetHostOverlappedSize Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="1db2e-140">IHostIoCompletionManager 接口</span><span class="sxs-lookup"><span data-stu-id="1db2e-140">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
