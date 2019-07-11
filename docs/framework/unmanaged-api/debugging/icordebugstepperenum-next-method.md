---
title: ICorDebugStepperEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum::Next
helpviewer_keywords:
- Next method, ICorDebugStepperEnum interface [.NET Framework debugging]
- ICorDebugStepperEnum::Next method [.NET Framework debugging]
ms.assetid: d0ea0f30-e8d2-48b0-8477-e1a029ceb4dd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58f148eb4c3206ba12eed41df670846d7beab77a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771634"
---
# <a name="icordebugstepperenumnext-method"></a><span data-ttu-id="9be5e-102">ICorDebugStepperEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="9be5e-102">ICorDebugStepperEnum::Next Method</span></span>
<span data-ttu-id="9be5e-103">从当前位置开始枚举中获取指定的数量的 ICorDebugStepper 实例。</span><span class="sxs-lookup"><span data-stu-id="9be5e-103">Gets the specified number of ICorDebugStepper instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9be5e-104">语法</span><span class="sxs-lookup"><span data-stu-id="9be5e-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugStepper *steppers[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9be5e-105">参数</span><span class="sxs-lookup"><span data-stu-id="9be5e-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9be5e-106">[in]数`ICorDebugStepper`要检索的实例。</span><span class="sxs-lookup"><span data-stu-id="9be5e-106">[in] The number of `ICorDebugStepper` instances to be retrieved.</span></span>  
  
 `steppers`  
 <span data-ttu-id="9be5e-107">[out]一个指针，其中每个指向数组`ICorDebugStepper`对象。</span><span class="sxs-lookup"><span data-stu-id="9be5e-107">[out] An array of pointers, each of which points to an `ICorDebugStepper` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9be5e-108">[out]指向数`ICorDebugStepper`实际返回的实例。</span><span class="sxs-lookup"><span data-stu-id="9be5e-108">[out] Pointer to the number of `ICorDebugStepper` instances actually returned.</span></span> <span data-ttu-id="9be5e-109">此值可能为 null 如果`celt`是其中一个。</span><span class="sxs-lookup"><span data-stu-id="9be5e-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9be5e-110">要求</span><span class="sxs-lookup"><span data-stu-id="9be5e-110">Requirements</span></span>  
 <span data-ttu-id="9be5e-111">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9be5e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9be5e-112">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9be5e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9be5e-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9be5e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9be5e-114">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9be5e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
