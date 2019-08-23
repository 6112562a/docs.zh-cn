---
title: ICLRGCManager2 接口
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c54707d4c767fbb644ed892767be8351d2fd95b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966188"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="d8367-102">ICLRGCManager2 接口</span><span class="sxs-lookup"><span data-stu-id="d8367-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="d8367-103">提供允许主机与公共语言运行时的垃圾回收系统交互的方法。</span><span class="sxs-lookup"><span data-stu-id="d8367-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d8367-104">方法</span><span class="sxs-lookup"><span data-stu-id="d8367-104">Methods</span></span>  
  
|<span data-ttu-id="d8367-105">方法</span><span class="sxs-lookup"><span data-stu-id="d8367-105">Method</span></span>|<span data-ttu-id="d8367-106">描述</span><span class="sxs-lookup"><span data-stu-id="d8367-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d8367-107">SetGCStartupLimitsEx 方法</span><span class="sxs-lookup"><span data-stu-id="d8367-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="d8367-108">设置垃圾回收段的大小以及垃圾回收系统的第0代的最大大小。</span><span class="sxs-lookup"><span data-stu-id="d8367-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="d8367-109">启用0代和大于`DWORD`的段大小。</span><span class="sxs-lookup"><span data-stu-id="d8367-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8367-110">备注</span><span class="sxs-lookup"><span data-stu-id="d8367-110">Remarks</span></span>  
 <span data-ttu-id="d8367-111">此接口继承自[ICLRGCManager 接口](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="d8367-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="d8367-112">公共语言运行时 (CLR) 实现了托管<xref:System.GC>类型的垃圾回收机制。</span><span class="sxs-lookup"><span data-stu-id="d8367-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="d8367-113">有关垃圾回收系统的详细信息, 请参阅[垃圾](../../../standard/garbage-collection/index.md)回收。</span><span class="sxs-lookup"><span data-stu-id="d8367-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8367-114">要求</span><span class="sxs-lookup"><span data-stu-id="d8367-114">Requirements</span></span>  
 <span data-ttu-id="d8367-115">**适用**请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8367-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8367-116">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d8367-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d8367-117">**类库**作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="d8367-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8367-118">**.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8367-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8367-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="d8367-119">See also</span></span>

- [<span data-ttu-id="d8367-120">自动内存管理</span><span class="sxs-lookup"><span data-stu-id="d8367-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="d8367-121">COR_GC_STATS 结构</span><span class="sxs-lookup"><span data-stu-id="d8367-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="d8367-122">ICLRControl 接口</span><span class="sxs-lookup"><span data-stu-id="d8367-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="d8367-123">.NET Framework 4 和 4.5 中添加的 CLR 承载接口</span><span class="sxs-lookup"><span data-stu-id="d8367-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="d8367-124">承载接口</span><span class="sxs-lookup"><span data-stu-id="d8367-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="d8367-125">承载</span><span class="sxs-lookup"><span data-stu-id="d8367-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
