---
title: ICorThreadpool::CorGetAvailableThreads 方法
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type:
- apiref
ms.openlocfilehash: 40da8e67c705378c9e44398f6a0f519296da03e4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133262"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="41522-102">ICorThreadpool::CorGetAvailableThreads 方法</span><span class="sxs-lookup"><span data-stu-id="41522-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="41522-103">此方法支持 .NET Framework 基础结构，但不适合直接在代码中使用。</span><span class="sxs-lookup"><span data-stu-id="41522-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41522-104">语法</span><span class="sxs-lookup"><span data-stu-id="41522-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="41522-105">要求</span><span class="sxs-lookup"><span data-stu-id="41522-105">Requirements</span></span>  
 <span data-ttu-id="41522-106">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41522-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41522-107">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="41522-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41522-108">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="41522-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41522-109">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41522-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41522-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="41522-110">See also</span></span>

- [<span data-ttu-id="41522-111">ICorThreadpool 接口</span><span class="sxs-lookup"><span data-stu-id="41522-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
