---
title: ICorDebugThread::GetAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetAppDomain
helpviewer_keywords:
- GetAppDomain method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetAppDomain method [.NET Framework debugging]
ms.assetid: 415b3d34-8b35-4b60-a318-140646cc83f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12a37ee8367006975b0f8ee4fa638ae3d72f9486
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487741"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="b5f98-102">ICorDebugThread::GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="b5f98-102">ICorDebugThread::GetAppDomain Method</span></span>
<span data-ttu-id="b5f98-103">获取此 ICorDebugThread 当前执行的应用程序域、 一个接口指针。</span><span class="sxs-lookup"><span data-stu-id="b5f98-103">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5f98-104">语法</span><span class="sxs-lookup"><span data-stu-id="b5f98-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5f98-105">参数</span><span class="sxs-lookup"><span data-stu-id="b5f98-105">Parameters</span></span>  
 `ppAppDomain`  
 <span data-ttu-id="b5f98-106">[out]指向表示此线程当前执行的应用程序域的 ICorDebugAppDomain 对象的指针。</span><span class="sxs-lookup"><span data-stu-id="b5f98-106">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5f98-107">要求</span><span class="sxs-lookup"><span data-stu-id="b5f98-107">Requirements</span></span>  
 <span data-ttu-id="b5f98-108">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b5f98-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5f98-109">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b5f98-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b5f98-110">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5f98-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b5f98-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5f98-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
