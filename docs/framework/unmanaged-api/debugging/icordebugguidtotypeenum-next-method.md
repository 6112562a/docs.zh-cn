---
title: ICorDebugGuidToTypeEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f334b4a28b0573fa938c2fda340c0c03175ff18
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756874"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="c5ef9-102">ICorDebugGuidToTypeEnum::Next 方法</span><span class="sxs-lookup"><span data-stu-id="c5ef9-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="c5ef9-103">获取指定的数目的[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)映射 Guid 类型信息的实例。</span><span class="sxs-lookup"><span data-stu-id="c5ef9-103">Gets the specified number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5ef9-104">语法</span><span class="sxs-lookup"><span data-stu-id="c5ef9-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5ef9-105">参数</span><span class="sxs-lookup"><span data-stu-id="c5ef9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c5ef9-106">[in]要检索的 GUID 类型映射对象的数目。</span><span class="sxs-lookup"><span data-stu-id="c5ef9-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="c5ef9-107">[out]一个指针，其中每个指向数组[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)将 Windows 运行时 GUID 映射到其相应的 ICorDebugType 对象的对象。</span><span class="sxs-lookup"><span data-stu-id="c5ef9-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c5ef9-108">[out]指向数[CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)对象中实际返回`values`。</span><span class="sxs-lookup"><span data-stu-id="c5ef9-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5ef9-109">备注</span><span class="sxs-lookup"><span data-stu-id="c5ef9-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5ef9-110">要求</span><span class="sxs-lookup"><span data-stu-id="c5ef9-110">Requirements</span></span>  
 <span data-ttu-id="c5ef9-111">**平台：** Windows 运行时</span><span class="sxs-lookup"><span data-stu-id="c5ef9-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="c5ef9-112">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5ef9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5ef9-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5ef9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5ef9-114">**.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5ef9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5ef9-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="c5ef9-115">See also</span></span>

- [<span data-ttu-id="c5ef9-116">ICorDebugGuidToTypeEnum 接口</span><span class="sxs-lookup"><span data-stu-id="c5ef9-116">ICorDebugGuidToTypeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="c5ef9-117">调试接口</span><span class="sxs-lookup"><span data-stu-id="c5ef9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
