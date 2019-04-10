---
title: IDebuggerThreadControl::StartBlockingForDebugger 方法
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.StartBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfc94c2de1a14842cc017e5c4ef6023154c20f2a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194027"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="413f1-102">IDebuggerThreadControl::StartBlockingForDebugger 方法</span><span class="sxs-lookup"><span data-stu-id="413f1-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="413f1-103">通知主机调试服务即将启动阻塞所有线程。</span><span class="sxs-lookup"><span data-stu-id="413f1-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="413f1-104">语法</span><span class="sxs-lookup"><span data-stu-id="413f1-104">Syntax</span></span>  
  
```  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="413f1-105">参数</span><span class="sxs-lookup"><span data-stu-id="413f1-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="413f1-106">[in]保留供将来使用。</span><span class="sxs-lookup"><span data-stu-id="413f1-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="413f1-107">备注</span><span class="sxs-lookup"><span data-stu-id="413f1-107">Remarks</span></span>  
 <span data-ttu-id="413f1-108">`StartBlockingForDebugger`无法在运行时线程上调用方法。</span><span class="sxs-lookup"><span data-stu-id="413f1-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="413f1-109">要求</span><span class="sxs-lookup"><span data-stu-id="413f1-109">Requirements</span></span>  
 <span data-ttu-id="413f1-110">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="413f1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="413f1-111">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="413f1-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="413f1-112">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="413f1-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="413f1-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="413f1-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="413f1-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="413f1-114">See also</span></span>

- [<span data-ttu-id="413f1-115">IDebuggerThreadControl 接口</span><span class="sxs-lookup"><span data-stu-id="413f1-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
