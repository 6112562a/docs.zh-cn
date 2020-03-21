---
title: ICLRHostBindingPolicyManager::ModifyApplicationPolicy 方法
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager.ModifyApplicationPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy
helpviewer_keywords:
- ICLRHostBindingPolicyManager::ModifyApplicationPolicy method [.NET Framework hosting]
- ModifyApplicationPolicy method [.NET Framework hosting]
ms.assetid: d82d633e-cce6-427c-8b02-8227e34e12ba
topic_type:
- apiref
ms.openlocfilehash: d8df78e3d5cebe5378dfba11dc0ea93cc8e346eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178104"
---
# <a name="iclrhostbindingpolicymanagermodifyapplicationpolicy-method"></a><span data-ttu-id="ad2da-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="ad2da-102">ICLRHostBindingPolicyManager::ModifyApplicationPolicy Method</span></span>
<span data-ttu-id="ad2da-103">修改指定程序集的绑定策略，并创建策略的新版本。</span><span class="sxs-lookup"><span data-stu-id="ad2da-103">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad2da-104">语法</span><span class="sxs-lookup"><span data-stu-id="ad2da-104">Syntax</span></span>  
  
```cpp  
HRESULT  ModifyApplicationPolicy (  
    [in] LPCWSTR     pwzSourceAssemblyIdentity,
    [in] LPCWSTR     pwzTargetAssemblyIdentity,  
    [in] BYTE       *pbApplicationPolicy,  
    [in] DWORD       cbAppPolicySize,  
    [in] DWORD       dwPolicyModifyFlags,  
    [out, size_is(*pcbNewAppPolicySize)] BYTE *pbNewApplicationPolicy,
    [in, out] DWORD *pcbNewAppPolicySize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad2da-105">parameters</span><span class="sxs-lookup"><span data-stu-id="ad2da-105">Parameters</span></span>  
 `pwzSourceAssemblyIdentity`  
 <span data-ttu-id="ad2da-106">[在]要修改的程序集的标识。</span><span class="sxs-lookup"><span data-stu-id="ad2da-106">[in] The identity of the assembly to modify.</span></span>  
  
 `pwzTargetAssemblyIdentity`  
 <span data-ttu-id="ad2da-107">[在]修改程序集的新标识。</span><span class="sxs-lookup"><span data-stu-id="ad2da-107">[in] The new identity of the modified assembly.</span></span>  
  
 `pbApplicationPolicy`  
 <span data-ttu-id="ad2da-108">[在]指向缓冲区的指针，其中包含要修改的绑定策略数据。</span><span class="sxs-lookup"><span data-stu-id="ad2da-108">[in] A pointer to a buffer that contains the binding policy data for the assembly to modify.</span></span>  
  
 `cbAppPolicySize`  
 <span data-ttu-id="ad2da-109">[在]要替换的绑定策略的大小。</span><span class="sxs-lookup"><span data-stu-id="ad2da-109">[in] The size of the binding policy to be replaced.</span></span>  
  
 `dwPolicyModifyFlags`  
 <span data-ttu-id="ad2da-110">[在][EHostBindingPolicy修改标志](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md)值的逻辑 OR 组合，指示重定向的控制。</span><span class="sxs-lookup"><span data-stu-id="ad2da-110">[in] A logical OR combination of [EHostBindingPolicyModifyFlags](../../../../docs/framework/unmanaged-api/hosting/ehostbindingpolicymodifyflags-enumeration.md) values, indicating control of redirection.</span></span>  
  
 `pbNewApplicationPolicy`  
 <span data-ttu-id="ad2da-111">[出]指向包含新绑定策略数据的缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="ad2da-111">[out] A pointer to a buffer that contains the new binding policy data.</span></span>  
  
 `pcbNewAppPolicySize`  
 <span data-ttu-id="ad2da-112">[进出]指向新绑定策略缓冲区大小的指针。</span><span class="sxs-lookup"><span data-stu-id="ad2da-112">[in, out] A pointer to the size of the new binding policy buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad2da-113">返回值</span><span class="sxs-lookup"><span data-stu-id="ad2da-113">Return Value</span></span>  
  
|<span data-ttu-id="ad2da-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ad2da-114">HRESULT</span></span>|<span data-ttu-id="ad2da-115">说明</span><span class="sxs-lookup"><span data-stu-id="ad2da-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ad2da-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad2da-116">S_OK</span></span>|<span data-ttu-id="ad2da-117">已成功修改策略。</span><span class="sxs-lookup"><span data-stu-id="ad2da-117">The policy was modified successfully.</span></span>|  
|<span data-ttu-id="ad2da-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ad2da-118">E_INVALIDARG</span></span>|<span data-ttu-id="ad2da-119">`pwzSourceAssemblyIdentity`或`pwzTargetAssemblyIdentity`为空引用。</span><span class="sxs-lookup"><span data-stu-id="ad2da-119">`pwzSourceAssemblyIdentity` or `pwzTargetAssemblyIdentity` was a null reference.</span></span>|  
|<span data-ttu-id="ad2da-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="ad2da-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="ad2da-121">`pbNewApplicationPolicy` 太小。</span><span class="sxs-lookup"><span data-stu-id="ad2da-121">`pbNewApplicationPolicy` is too small.</span></span>|  
|<span data-ttu-id="ad2da-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ad2da-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ad2da-123">公共语言运行时 （CLR） 尚未加载到进程中，或者 CLR 处于无法运行托管代码或成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="ad2da-123">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ad2da-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ad2da-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ad2da-125">呼叫超时。</span><span class="sxs-lookup"><span data-stu-id="ad2da-125">The call timed out.</span></span>|  
|<span data-ttu-id="ad2da-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ad2da-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ad2da-127">调用方不拥有锁。</span><span class="sxs-lookup"><span data-stu-id="ad2da-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ad2da-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ad2da-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ad2da-129">当阻塞的线程或光纤等待事件时，事件已被取消。</span><span class="sxs-lookup"><span data-stu-id="ad2da-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ad2da-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ad2da-130">E_FAIL</span></span>|<span data-ttu-id="ad2da-131">发生了未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="ad2da-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ad2da-132">方法返回E_FAIL后，CLR 在进程中不再可用。</span><span class="sxs-lookup"><span data-stu-id="ad2da-132">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ad2da-133">对托管方法的后续调用返回HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="ad2da-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad2da-134">备注</span><span class="sxs-lookup"><span data-stu-id="ad2da-134">Remarks</span></span>  
 <span data-ttu-id="ad2da-135">该方法`ModifyApplicationPolicy`可以调用两次。</span><span class="sxs-lookup"><span data-stu-id="ad2da-135">The `ModifyApplicationPolicy` method can be called twice.</span></span> <span data-ttu-id="ad2da-136">第一个调用应为`pbNewApplicationPolicy`参数提供 null 值。</span><span class="sxs-lookup"><span data-stu-id="ad2da-136">The first call should supply a null value for the `pbNewApplicationPolicy` parameter.</span></span> <span data-ttu-id="ad2da-137">此调用将返回，并带有`pcbNewAppPolicySize`所需的值。</span><span class="sxs-lookup"><span data-stu-id="ad2da-137">This call will return with the necessary value for `pcbNewAppPolicySize`.</span></span> <span data-ttu-id="ad2da-138">第二个调用应为`pcbNewAppPolicySize`提供此值，并指向 该大小的缓冲区。 `pbNewApplicationPolicy`</span><span class="sxs-lookup"><span data-stu-id="ad2da-138">The second call should supply this value for `pcbNewAppPolicySize`, and point to a buffer of that size for `pbNewApplicationPolicy`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad2da-139">要求</span><span class="sxs-lookup"><span data-stu-id="ad2da-139">Requirements</span></span>  
 <span data-ttu-id="ad2da-140">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad2da-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad2da-141">**标题：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ad2da-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ad2da-142">**库：** 作为资源包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="ad2da-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad2da-143">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad2da-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad2da-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ad2da-144">See also</span></span>

- [<span data-ttu-id="ad2da-145">ICLRHostBindingPolicyManager 接口</span><span class="sxs-lookup"><span data-stu-id="ad2da-145">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
