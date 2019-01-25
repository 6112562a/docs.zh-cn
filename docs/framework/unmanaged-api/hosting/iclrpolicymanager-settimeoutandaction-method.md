---
title: ICLRPolicyManager::SetTimeoutAndAction 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetTimeoutAndAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetTimeoutAndAction
helpviewer_keywords:
- ICLRPolicyManager::SetTimeoutAndAction method [.NET Framework hosting]
- SetTimeoutAndAction method [.NET Framework hosting]
ms.assetid: 60454f91-d855-4ddf-bb6d-60a02f5eabab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cc8c980c3f9dbfa0b262b30a56756f148676de7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602242"
---
# <a name="iclrpolicymanagersettimeoutandaction-method"></a><span data-ttu-id="71f80-102">ICLRPolicyManager::SetTimeoutAndAction 方法</span><span class="sxs-lookup"><span data-stu-id="71f80-102">ICLRPolicyManager::SetTimeoutAndAction Method</span></span>
<span data-ttu-id="71f80-103">设置指定的操作的超时值，并指定该操作发生时，应执行公共语言运行时 (CLR) 的策略操作。</span><span class="sxs-lookup"><span data-stu-id="71f80-103">Sets a timeout value for the specified operation, and specifies the policy action the common language runtime (CLR) should take when the operation occurs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71f80-104">语法</span><span class="sxs-lookup"><span data-stu-id="71f80-104">Syntax</span></span>  
  
```  
HRESULT SetTimeoutAndAction (  
    [in] EClrOperation operation,  
    [in] DWORD dwMilliseconds,  
    [in] EPolicyAction action  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71f80-105">参数</span><span class="sxs-lookup"><span data-stu-id="71f80-105">Parameters</span></span>  
 `operation`  
 <span data-ttu-id="71f80-106">[in]之一[EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)值，它指示要为其设置的超时和策略操作`action`。</span><span class="sxs-lookup"><span data-stu-id="71f80-106">[in] One of the [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) values, indicating the operation for which to set the timeout and policy `action`.</span></span> <span data-ttu-id="71f80-107">支持以下值：</span><span class="sxs-lookup"><span data-stu-id="71f80-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="71f80-108">OPR_AppDomainUnload</span><span class="sxs-lookup"><span data-stu-id="71f80-108">OPR_AppDomainUnload</span></span>  
  
-   <span data-ttu-id="71f80-109">OPR_ProcessExit</span><span class="sxs-lookup"><span data-stu-id="71f80-109">OPR_ProcessExit</span></span>  
  
-   <span data-ttu-id="71f80-110">OPR_ThreadRudeAbortInCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="71f80-110">OPR_ThreadRudeAbortInCriticalRegion</span></span>  
  
-   <span data-ttu-id="71f80-111">OPR_ThreadRudeAbortInNonCriticalRegion</span><span class="sxs-lookup"><span data-stu-id="71f80-111">OPR_ThreadRudeAbortInNonCriticalRegion</span></span>  
  
 `dwMilliseconds`  
 <span data-ttu-id="71f80-112">[in]新的超时值，以毫秒为单位。</span><span class="sxs-lookup"><span data-stu-id="71f80-112">[in] The new timeout value, in milliseconds.</span></span> <span data-ttu-id="71f80-113">值为无限原因`operation`永远不会为超时时间。</span><span class="sxs-lookup"><span data-stu-id="71f80-113">A value of INFINITE causes `operation` never to time out.</span></span>  
  
 `action`  
 <span data-ttu-id="71f80-114">[in]之一[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，指示 CLR 应执行时指定的策略操作`operation`时发生。</span><span class="sxs-lookup"><span data-stu-id="71f80-114">[in] One of the [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md) values, indicating the policy action that the CLR should take when `operation` occurs.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71f80-115">返回值</span><span class="sxs-lookup"><span data-stu-id="71f80-115">Return Value</span></span>  
  
|<span data-ttu-id="71f80-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71f80-116">HRESULT</span></span>|<span data-ttu-id="71f80-117">描述</span><span class="sxs-lookup"><span data-stu-id="71f80-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71f80-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="71f80-118">S_OK</span></span>|<span data-ttu-id="71f80-119">`SetTimeoutAndAction` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="71f80-119">`SetTimeoutAndAction` returned successfully.</span></span>|  
|<span data-ttu-id="71f80-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="71f80-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="71f80-121">CLR 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="71f80-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="71f80-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="71f80-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="71f80-123">呼叫已超时。</span><span class="sxs-lookup"><span data-stu-id="71f80-123">The call timed out.</span></span>|  
|<span data-ttu-id="71f80-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="71f80-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="71f80-125">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="71f80-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="71f80-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="71f80-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="71f80-127">事件已取消时被阻塞的线程或纤程正在等待它。</span><span class="sxs-lookup"><span data-stu-id="71f80-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="71f80-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="71f80-128">E_FAIL</span></span>|<span data-ttu-id="71f80-129">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="71f80-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="71f80-130">方法返回 E_FAIL 后，CLR 不再在进程中使用。</span><span class="sxs-lookup"><span data-stu-id="71f80-130">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="71f80-131">对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="71f80-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="71f80-132">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="71f80-132">E_INVALIDARG</span></span>|<span data-ttu-id="71f80-133">超时值不能设置为指定`operation`，或对于提供的值无效`action`。</span><span class="sxs-lookup"><span data-stu-id="71f80-133">A timeout cannot be set for the specified `operation`, or an invalid value was supplied for `action`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71f80-134">备注</span><span class="sxs-lookup"><span data-stu-id="71f80-134">Remarks</span></span>  
 <span data-ttu-id="71f80-135">`SetTimeoutAndAction` 封装的功能[iclrpolicymanager:: Settimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md)并[iclrpolicymanager:: Setactionontimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)方法，并且可以调用来对这两种方法的顺序调用替代。</span><span class="sxs-lookup"><span data-stu-id="71f80-135">`SetTimeoutAndAction` encapsulates the capabilities of the [ICLRPolicyManager::SetTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeout-method.md) and [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) methods, and can be called in place of sequential calls to these two methods.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="71f80-136">并非所有策略操作值可以都指定为对于 CLR 操作的超时行为。</span><span class="sxs-lookup"><span data-stu-id="71f80-136">Not all policy action values can be specified as the timeout behavior for CLR operations.</span></span> <span data-ttu-id="71f80-137">请参阅有关有效值的这两种方法的主题的备注部分。</span><span class="sxs-lookup"><span data-stu-id="71f80-137">See the Remarks sections of the topics for these two methods for valid values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71f80-138">要求</span><span class="sxs-lookup"><span data-stu-id="71f80-138">Requirements</span></span>  
 <span data-ttu-id="71f80-139">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="71f80-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71f80-140">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="71f80-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71f80-141">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="71f80-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71f80-142">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71f80-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f80-143">请参阅</span><span class="sxs-lookup"><span data-stu-id="71f80-143">See also</span></span>
- [<span data-ttu-id="71f80-144">EClrOperation 枚举</span><span class="sxs-lookup"><span data-stu-id="71f80-144">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="71f80-145">EPolicyAction 枚举</span><span class="sxs-lookup"><span data-stu-id="71f80-145">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="71f80-146">ICLRPolicyManager 接口</span><span class="sxs-lookup"><span data-stu-id="71f80-146">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="71f80-147">SetActionOnTimeout 方法</span><span class="sxs-lookup"><span data-stu-id="71f80-147">SetActionOnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md)
- [<span data-ttu-id="71f80-148">ICLRPolicyManager::SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="71f80-148">ICLRPolicyManager::SetTimeoutAndAction</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-settimeoutandaction-method.md)
