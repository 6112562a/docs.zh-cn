---
title: IGCHost::GetStats 方法
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b8af1de3daf08a8389a5b0e6ebb278646345f9b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482608"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="1d466-102">IGCHost::GetStats 方法</span><span class="sxs-lookup"><span data-stu-id="1d466-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="1d466-103">获取垃圾回收系统的当前状态的统计信息。</span><span class="sxs-lookup"><span data-stu-id="1d466-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d466-104">语法</span><span class="sxs-lookup"><span data-stu-id="1d466-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d466-105">参数</span><span class="sxs-lookup"><span data-stu-id="1d466-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="1d466-106">[in、 out]一个指向[COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)结构，其中包含垃圾回收系统的当前状态的统计信息。</span><span class="sxs-lookup"><span data-stu-id="1d466-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d466-107">备注</span><span class="sxs-lookup"><span data-stu-id="1d466-107">Remarks</span></span>  
 <span data-ttu-id="1d466-108">统计信息可以由智能分配系统，用于帮助垃圾回收系统进行操作。</span><span class="sxs-lookup"><span data-stu-id="1d466-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="1d466-109">例如，分配系统可能会确定，请查看统计信息，它需要添加更多内存或强制回收后。</span><span class="sxs-lookup"><span data-stu-id="1d466-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d466-110">要求</span><span class="sxs-lookup"><span data-stu-id="1d466-110">Requirements</span></span>  
 <span data-ttu-id="1d466-111">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1d466-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d466-112">**标头：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="1d466-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="1d466-113">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="1d466-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d466-114">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d466-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d466-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="1d466-115">See also</span></span>
- [<span data-ttu-id="1d466-116">IGCHost 接口</span><span class="sxs-lookup"><span data-stu-id="1d466-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
