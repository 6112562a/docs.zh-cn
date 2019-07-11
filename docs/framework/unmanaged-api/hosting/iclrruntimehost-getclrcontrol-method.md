---
title: ICLRRuntimeHost::GetCLRControl 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b697e2cf7688767ac58c6bd2a3f18d781ab439b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768752"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="3e5a3-102">ICLRRuntimeHost::GetCLRControl 方法</span><span class="sxs-lookup"><span data-stu-id="3e5a3-102">ICLRRuntimeHost::GetCLRControl Method</span></span>
<span data-ttu-id="3e5a3-103">获取类型的接口指针[ICLRControl 接口](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)主机可用于自定义的公共语言运行时 (CLR) 方面。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-103">Gets an interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e5a3-104">语法</span><span class="sxs-lookup"><span data-stu-id="3e5a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e5a3-105">参数</span><span class="sxs-lookup"><span data-stu-id="3e5a3-105">Parameters</span></span>  
 `pCLRControl`  
 <span data-ttu-id="3e5a3-106">[out]类型的接口指针[ICLRControl 接口](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)，使主机的 CLR 的其他方面进行配置。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-106">[out] An interface pointer of type [ICLRControl Interface](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e5a3-107">返回值</span><span class="sxs-lookup"><span data-stu-id="3e5a3-107">Return Value</span></span>  
  
|<span data-ttu-id="3e5a3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3e5a3-108">HRESULT</span></span>|<span data-ttu-id="3e5a3-109">描述</span><span class="sxs-lookup"><span data-stu-id="3e5a3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3e5a3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e5a3-110">S_OK</span></span>|<span data-ttu-id="3e5a3-111">`GetCLRControl` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="3e5a3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3e5a3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3e5a3-113">CLR 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3e5a3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3e5a3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3e5a3-115">呼叫已超时。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-115">The call timed out.</span></span>|  
|<span data-ttu-id="3e5a3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3e5a3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3e5a3-117">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3e5a3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3e5a3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3e5a3-119">事件已取消时被阻塞的线程或纤程正在等待它。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3e5a3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3e5a3-120">E_FAIL</span></span>|<span data-ttu-id="3e5a3-121">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3e5a3-122">如果方法返回 E_FAIL，CLR 不再在该过程中可用。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3e5a3-123">对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3e5a3-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="3e5a3-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="3e5a3-125">CLR 已启动。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e5a3-126">备注</span><span class="sxs-lookup"><span data-stu-id="3e5a3-126">Remarks</span></span>  
 <span data-ttu-id="3e5a3-127">`ICLRControl` 提供了[GetCLRManager 方法](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法，使宿主能够访问管理器类型的接口指针。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-127">`ICLRControl` provides the [GetCLRManager Method](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e5a3-128">要求</span><span class="sxs-lookup"><span data-stu-id="3e5a3-128">Requirements</span></span>  
 <span data-ttu-id="3e5a3-129">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3e5a3-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e5a3-130">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e5a3-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e5a3-131">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="3e5a3-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e5a3-132">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e5a3-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e5a3-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="3e5a3-133">See also</span></span>

- [<span data-ttu-id="3e5a3-134">ICLRControl 接口</span><span class="sxs-lookup"><span data-stu-id="3e5a3-134">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="3e5a3-135">ICLRRuntimeHost 接口</span><span class="sxs-lookup"><span data-stu-id="3e5a3-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
