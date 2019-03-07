---
title: ICorDebugThread::GetActiveFrame 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 051491173bbcef3d87d9a3dbe854eece46c49e0d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468775"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="a6697-102">ICorDebugThread::GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="a6697-102">ICorDebugThread::GetActiveFrame Method</span></span>
<span data-ttu-id="a6697-103">获取此 ICorDebugThread 对象上活动的 （最新的） 帧的接口指针。</span><span class="sxs-lookup"><span data-stu-id="a6697-103">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6697-104">语法</span><span class="sxs-lookup"><span data-stu-id="a6697-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6697-105">参数</span><span class="sxs-lookup"><span data-stu-id="a6697-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="a6697-106">[out]指向表示框架的 ICorDebugFrame 接口对象地址的指针。</span><span class="sxs-lookup"><span data-stu-id="a6697-106">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6697-107">备注</span><span class="sxs-lookup"><span data-stu-id="a6697-107">Remarks</span></span>  
 <span data-ttu-id="a6697-108">`ppFrame`参数为 null，如果没有框架当前处于活动状态。</span><span class="sxs-lookup"><span data-stu-id="a6697-108">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6697-109">要求</span><span class="sxs-lookup"><span data-stu-id="a6697-109">Requirements</span></span>  
 <span data-ttu-id="a6697-110">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6697-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6697-111">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6697-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6697-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6697-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6697-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6697-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
