---
title: ICorDebug::EnumerateProcesses 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.EnumerateProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10741ef9d329986d869665ef3aae14196946bb22
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724416"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="2501b-102">ICorDebug::EnumerateProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="2501b-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="2501b-103">获取正在调试的进程的枚举数。</span><span class="sxs-lookup"><span data-stu-id="2501b-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2501b-104">语法</span><span class="sxs-lookup"><span data-stu-id="2501b-104">Syntax</span></span>  
  
```  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2501b-105">参数</span><span class="sxs-lookup"><span data-stu-id="2501b-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="2501b-106">指向一个 ICorDebugProcessEnum 对象，它正在调试的进程的枚举器的地址的指针。</span><span class="sxs-lookup"><span data-stu-id="2501b-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2501b-107">要求</span><span class="sxs-lookup"><span data-stu-id="2501b-107">Requirements</span></span>  
 <span data-ttu-id="2501b-108">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2501b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2501b-109">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2501b-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2501b-110">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2501b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2501b-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2501b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2501b-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="2501b-112">See also</span></span>
- [<span data-ttu-id="2501b-113">ICorDebug 接口</span><span class="sxs-lookup"><span data-stu-id="2501b-113">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
