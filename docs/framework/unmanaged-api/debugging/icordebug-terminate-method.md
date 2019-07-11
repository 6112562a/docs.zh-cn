---
title: ICorDebug::Terminate 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Terminate
helpviewer_keywords:
- Terminate method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Terminate method [.NET Framework debugging]
ms.assetid: fffe5616-0896-4426-ab5e-21869b514883
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3037fc704ffc3aac4d050cef7857261f138f7d35
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738072"
---
# <a name="icordebugterminate-method"></a><span data-ttu-id="ee08e-102">ICorDebug::Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="ee08e-102">ICorDebug::Terminate Method</span></span>
<span data-ttu-id="ee08e-103">终止`ICorDebug`对象。</span><span class="sxs-lookup"><span data-stu-id="ee08e-103">Terminates the `ICorDebug` object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee08e-104">`Terminate` 不应调用直到[icordebugmanagedcallback:: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)回调收到的所有正在调试的进程。</span><span class="sxs-lookup"><span data-stu-id="ee08e-104">`Terminate` should not be called until an [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback has been received for all processes being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee08e-105">语法</span><span class="sxs-lookup"><span data-stu-id="ee08e-105">Syntax</span></span>  
  
```cpp  
HRESULT Terminate ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ee08e-106">备注</span><span class="sxs-lookup"><span data-stu-id="ee08e-106">Remarks</span></span>  
 <span data-ttu-id="ee08e-107">`Terminate` 时，必须调用`ICorDebug`不再需要对象。</span><span class="sxs-lookup"><span data-stu-id="ee08e-107">`Terminate` must be called when the `ICorDebug` object is no longer needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee08e-108">要求</span><span class="sxs-lookup"><span data-stu-id="ee08e-108">Requirements</span></span>  
 <span data-ttu-id="ee08e-109">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ee08e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee08e-110">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee08e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee08e-111">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee08e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee08e-112">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee08e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee08e-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="ee08e-113">See also</span></span>

- [<span data-ttu-id="ee08e-114">ICorDebug 接口</span><span class="sxs-lookup"><span data-stu-id="ee08e-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
