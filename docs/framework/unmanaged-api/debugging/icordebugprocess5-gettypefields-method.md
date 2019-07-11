---
title: ICorDebugProcess5::GetTypeFields 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d413b17da0b6f241f9078bfeb3bd035d4d07a81
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767631"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="d4a3f-102">ICorDebugProcess5::GetTypeFields 方法</span><span class="sxs-lookup"><span data-stu-id="d4a3f-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="d4a3f-103">提供有关属于一种类型的字段信息。</span><span class="sxs-lookup"><span data-stu-id="d4a3f-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4a3f-104">语法</span><span class="sxs-lookup"><span data-stu-id="d4a3f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4a3f-105">参数</span><span class="sxs-lookup"><span data-stu-id="d4a3f-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="d4a3f-106">[in]检索其字段信息的类型的标识符。</span><span class="sxs-lookup"><span data-stu-id="d4a3f-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="d4a3f-107">[in]数[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)其字段信息是要检索的对象。</span><span class="sxs-lookup"><span data-stu-id="d4a3f-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="d4a3f-108">[out]一个数组[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)对象，它提供有关属于该类型的字段的信息。</span><span class="sxs-lookup"><span data-stu-id="d4a3f-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="d4a3f-109">[out]指向数[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)中包含的对象`fields`。</span><span class="sxs-lookup"><span data-stu-id="d4a3f-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4a3f-110">备注</span><span class="sxs-lookup"><span data-stu-id="d4a3f-110">Remarks</span></span>  
 <span data-ttu-id="d4a3f-111">`celt`参数，用于指定该方法用来填充其字段信息的字段数目`fields`，应与对应的值`COR_TYPE_LAYOUT::numFields`字段。</span><span class="sxs-lookup"><span data-stu-id="d4a3f-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4a3f-112">要求</span><span class="sxs-lookup"><span data-stu-id="d4a3f-112">Requirements</span></span>  
 <span data-ttu-id="d4a3f-113">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4a3f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4a3f-114">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4a3f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4a3f-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4a3f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4a3f-116">**.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4a3f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4a3f-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="d4a3f-117">See also</span></span>

- [<span data-ttu-id="d4a3f-118">ICorDebugProcess5 接口</span><span class="sxs-lookup"><span data-stu-id="d4a3f-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="d4a3f-119">调试接口</span><span class="sxs-lookup"><span data-stu-id="d4a3f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
