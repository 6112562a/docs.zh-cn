---
title: ICorDebugGCReferenceEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ef4ced1abd5b37af204ab3511a7cf8259303e8c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755552"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="f67ef-102">ICorDebugGCReferenceEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="f67ef-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="f67ef-103">获取指定的数目的[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)包含将进行垃圾回收的对象的信息的实例。</span><span class="sxs-lookup"><span data-stu-id="f67ef-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f67ef-104">语法</span><span class="sxs-lookup"><span data-stu-id="f67ef-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f67ef-105">参数</span><span class="sxs-lookup"><span data-stu-id="f67ef-105">Parameters</span></span>  
 <span data-ttu-id="f67ef-106">celt</span><span class="sxs-lookup"><span data-stu-id="f67ef-106">celt</span></span>  
 <span data-ttu-id="f67ef-107">[in]要检索的根的数目。</span><span class="sxs-lookup"><span data-stu-id="f67ef-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="f67ef-108">根</span><span class="sxs-lookup"><span data-stu-id="f67ef-108">roots</span></span>  
 <span data-ttu-id="f67ef-109">[out]一个指针，其中每个指向数组[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)表示的对象进行垃圾回收根的对象。</span><span class="sxs-lookup"><span data-stu-id="f67ef-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="f67ef-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="f67ef-110">pceltFetched</span></span>  
 <span data-ttu-id="f67ef-111">[out]指向数[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md)对象中实际返回`roots`。</span><span class="sxs-lookup"><span data-stu-id="f67ef-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="f67ef-112">如果 `celt` 为 1，此值可能为 `null`。</span><span class="sxs-lookup"><span data-stu-id="f67ef-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f67ef-113">备注</span><span class="sxs-lookup"><span data-stu-id="f67ef-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f67ef-114">要求</span><span class="sxs-lookup"><span data-stu-id="f67ef-114">Requirements</span></span>  
 <span data-ttu-id="f67ef-115">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f67ef-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f67ef-116">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f67ef-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f67ef-117">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f67ef-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f67ef-118">**.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f67ef-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f67ef-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="f67ef-119">See also</span></span>

- [<span data-ttu-id="f67ef-120">ICorDebugGCReferenceEnum 接口</span><span class="sxs-lookup"><span data-stu-id="f67ef-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="f67ef-121">调试接口</span><span class="sxs-lookup"><span data-stu-id="f67ef-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
