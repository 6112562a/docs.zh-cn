---
title: ICLROnEventManager 接口
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
ms.openlocfilehash: a1b22e77fe20d5e2d755efcd7a63c8f2bdc781e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140838"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="aeb83-102">ICLROnEventManager 接口</span><span class="sxs-lookup"><span data-stu-id="aeb83-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="aeb83-103">提供允许主机注册和注销公共语言运行时（CLR）事件的回调的方法。</span><span class="sxs-lookup"><span data-stu-id="aeb83-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aeb83-104">方法</span><span class="sxs-lookup"><span data-stu-id="aeb83-104">Methods</span></span>  
  
|<span data-ttu-id="aeb83-105">方法</span><span class="sxs-lookup"><span data-stu-id="aeb83-105">Method</span></span>|<span data-ttu-id="aeb83-106">描述</span><span class="sxs-lookup"><span data-stu-id="aeb83-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aeb83-107">RegisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="aeb83-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="aeb83-108">为指定事件注册回调指针。</span><span class="sxs-lookup"><span data-stu-id="aeb83-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="aeb83-109">UnregisterActionOnEvent 方法</span><span class="sxs-lookup"><span data-stu-id="aeb83-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="aeb83-110">为指定的事件注销先前注册的回调指针。</span><span class="sxs-lookup"><span data-stu-id="aeb83-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeb83-111">备注</span><span class="sxs-lookup"><span data-stu-id="aeb83-111">Remarks</span></span>  
 <span data-ttu-id="aeb83-112">若要注册和注销事件回调，主机可通过调用[ICLRControl：： GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)方法获取对 `ICLROnEventManager` 的引用。</span><span class="sxs-lookup"><span data-stu-id="aeb83-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aeb83-113">[EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)描述的事件可以从不同的线程激发一次，以指示卸载或禁用 CLR。</span><span class="sxs-lookup"><span data-stu-id="aeb83-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeb83-114">要求</span><span class="sxs-lookup"><span data-stu-id="aeb83-114">Requirements</span></span>  
 <span data-ttu-id="aeb83-115">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aeb83-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeb83-116">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="aeb83-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aeb83-117">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="aeb83-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aeb83-118">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeb83-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb83-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="aeb83-119">See also</span></span>

- [<span data-ttu-id="aeb83-120">EClrEvent 枚举</span><span class="sxs-lookup"><span data-stu-id="aeb83-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="aeb83-121">IActionOnCLREvent 接口</span><span class="sxs-lookup"><span data-stu-id="aeb83-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="aeb83-122">ICLRControl 接口</span><span class="sxs-lookup"><span data-stu-id="aeb83-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="aeb83-123">承载接口</span><span class="sxs-lookup"><span data-stu-id="aeb83-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
