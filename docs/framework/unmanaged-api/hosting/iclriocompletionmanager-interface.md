---
title: ICLRIoCompletionManager 接口
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
ms.openlocfilehash: b63d4269a8d48ee49016a4c51d63bf81bdba8da2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141030"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="1db83-102">ICLRIoCompletionManager 接口</span><span class="sxs-lookup"><span data-stu-id="1db83-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="1db83-103">实现一个回调方法，该方法允许宿主向公共语言运行时（CLR）通知指定 i/o 请求的状态。</span><span class="sxs-lookup"><span data-stu-id="1db83-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1db83-104">方法</span><span class="sxs-lookup"><span data-stu-id="1db83-104">Methods</span></span>  
  
|<span data-ttu-id="1db83-105">方法</span><span class="sxs-lookup"><span data-stu-id="1db83-105">Method</span></span>|<span data-ttu-id="1db83-106">描述</span><span class="sxs-lookup"><span data-stu-id="1db83-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1db83-107">OnComplete 方法</span><span class="sxs-lookup"><span data-stu-id="1db83-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="1db83-108">使用对[IHostIoCompletionManager：： Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)方法的调用，将发出的 i/o 请求状态通知给 CLR。</span><span class="sxs-lookup"><span data-stu-id="1db83-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1db83-109">备注</span><span class="sxs-lookup"><span data-stu-id="1db83-109">Remarks</span></span>  
 <span data-ttu-id="1db83-110">宿主通过使用[IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)接口实现 i/o 完成抽象。</span><span class="sxs-lookup"><span data-stu-id="1db83-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="1db83-111">CLR 通过此接口发出 i/o 请求，主机通过使用 `ICLRIoCompletionManager` 接口来通知运行时此类请求的结果。</span><span class="sxs-lookup"><span data-stu-id="1db83-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1db83-112">要求</span><span class="sxs-lookup"><span data-stu-id="1db83-112">Requirements</span></span>  
 <span data-ttu-id="1db83-113">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1db83-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1db83-114">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1db83-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1db83-115">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="1db83-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1db83-116">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1db83-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db83-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="1db83-117">See also</span></span>

- [<span data-ttu-id="1db83-118">IHostIoCompletionManager 接口</span><span class="sxs-lookup"><span data-stu-id="1db83-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="1db83-119">IHostThreadPoolManager 接口</span><span class="sxs-lookup"><span data-stu-id="1db83-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="1db83-120">承载接口</span><span class="sxs-lookup"><span data-stu-id="1db83-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
