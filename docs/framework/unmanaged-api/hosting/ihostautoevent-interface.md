---
title: IHostAutoEvent 接口
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b8cccf395e77c7dfefb85302b522d7e9398ffca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730017"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="e4898-102">IHostAutoEvent 接口</span><span class="sxs-lookup"><span data-stu-id="e4898-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="e4898-103">提供主机的自动重置事件实现的表示的形式。</span><span class="sxs-lookup"><span data-stu-id="e4898-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4898-104">方法</span><span class="sxs-lookup"><span data-stu-id="e4898-104">Methods</span></span>  
  
|<span data-ttu-id="e4898-105">方法</span><span class="sxs-lookup"><span data-stu-id="e4898-105">Method</span></span>|<span data-ttu-id="e4898-106">描述</span><span class="sxs-lookup"><span data-stu-id="e4898-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4898-107">Set 方法</span><span class="sxs-lookup"><span data-stu-id="e4898-107">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|<span data-ttu-id="e4898-108">设置当前`IHostAutoEvent`到已发出信号状态的实例。</span><span class="sxs-lookup"><span data-stu-id="e4898-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="e4898-109">Wait 方法</span><span class="sxs-lookup"><span data-stu-id="e4898-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|<span data-ttu-id="e4898-110">导致当前`IHostAutoEvent`等待，直到该事件所拥有的实例或指定的经历的时间量。</span><span class="sxs-lookup"><span data-stu-id="e4898-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e4898-111">要求</span><span class="sxs-lookup"><span data-stu-id="e4898-111">Requirements</span></span>  
 <span data-ttu-id="e4898-112">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4898-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4898-113">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e4898-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4898-114">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="e4898-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4898-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4898-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4898-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="e4898-116">See also</span></span>
- [<span data-ttu-id="e4898-117">ICLRSyncManager 接口</span><span class="sxs-lookup"><span data-stu-id="e4898-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="e4898-118">IHostManualEvent 接口</span><span class="sxs-lookup"><span data-stu-id="e4898-118">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="e4898-119">IHostSyncManager 接口</span><span class="sxs-lookup"><span data-stu-id="e4898-119">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="e4898-120">承载接口</span><span class="sxs-lookup"><span data-stu-id="e4898-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
