---
title: ICorDebugRegisterSet::SetRegisters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::SetRegisters
helpviewer_keywords:
- SetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::SetRegisters method [.NET Framework debugging]
ms.assetid: ac6244b9-54ba-475f-b72a-abed6afc46ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 200ea1b9c046b8743699a549c07c0baaf285be39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965026"
---
# <a name="icordebugregistersetsetregisters-method"></a><span data-ttu-id="1a629-102">ICorDebugRegisterSet::SetRegisters 方法</span><span class="sxs-lookup"><span data-stu-id="1a629-102">ICorDebugRegisterSet::SetRegisters Method</span></span>
<span data-ttu-id="1a629-103">`SetRegisters`在 .NET Framework 版本2.0 中未实现。</span><span class="sxs-lookup"><span data-stu-id="1a629-103">`SetRegisters` is not implemented in the .NET Framework version 2.0.</span></span> <span data-ttu-id="1a629-104">请勿调用此方法。</span><span class="sxs-lookup"><span data-stu-id="1a629-104">Do not call this method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a629-105">使用较高级别的操作, 如[ICorDebugILFrame:: setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)或[ICorDebugNativeFrame:: setip](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)。</span><span class="sxs-lookup"><span data-stu-id="1a629-105">Use the higher-level operations such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or [ICorDebugNativeFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a629-106">语法</span><span class="sxs-lookup"><span data-stu-id="1a629-106">Syntax</span></span>  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG64   mask,  
    [in] ULONG32   regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1a629-107">要求</span><span class="sxs-lookup"><span data-stu-id="1a629-107">Requirements</span></span>  
 <span data-ttu-id="1a629-108">**适用**请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1a629-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a629-109">**标头：** Cordebug.idl, Cordebug.idl</span><span class="sxs-lookup"><span data-stu-id="1a629-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a629-110">**类库**CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a629-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a629-111">**.NET Framework 版本:** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="1a629-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a629-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="1a629-112">See also</span></span>

- [<span data-ttu-id="1a629-113">ICorDebugRegisterSet 接口</span><span class="sxs-lookup"><span data-stu-id="1a629-113">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [<span data-ttu-id="1a629-114">ICorDebugRegisterSet2 接口</span><span class="sxs-lookup"><span data-stu-id="1a629-114">ICorDebugRegisterSet2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
