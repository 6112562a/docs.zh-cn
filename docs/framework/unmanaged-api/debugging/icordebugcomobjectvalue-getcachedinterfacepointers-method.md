---
title: ICorDebugComObjectValue::GetCachedInterfacePointers 方法
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
ms.openlocfilehash: 9d1d6d2f506086dd3204053b0b635da2e7cdc87e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783954"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="b89c1-102">ICorDebugComObjectValue::GetCachedInterfacePointers 方法</span><span class="sxs-lookup"><span data-stu-id="b89c1-102">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>
<span data-ttu-id="b89c1-103">获取缓存在当前运行时可调用包装器（RCW）上的原始接口指针。</span><span class="sxs-lookup"><span data-stu-id="b89c1-103">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b89c1-104">语法</span><span class="sxs-lookup"><span data-stu-id="b89c1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b89c1-105">参数</span><span class="sxs-lookup"><span data-stu-id="b89c1-105">Parameters</span></span>  
 `bIInspectableOnly`  
 <span data-ttu-id="b89c1-106">中一个值，该值指示方法是只返回 Windows 运行时接口（`IInspectable` 接口）还是运行时可调用包装器（RCW）缓存的所有 COM 接口。</span><span class="sxs-lookup"><span data-stu-id="b89c1-106">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="b89c1-107">中要检索其地址的对象的数目。</span><span class="sxs-lookup"><span data-stu-id="b89c1-107">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b89c1-108">弄一个指针，指向 `ptrs`中实际返回 `CORDB_ADDRESS` 值的数量。</span><span class="sxs-lookup"><span data-stu-id="b89c1-108">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="b89c1-109">一个指针，指向包含缓存接口对象地址的 `CORDB_ADDRESS` 值数组的起始地址。</span><span class="sxs-lookup"><span data-stu-id="b89c1-109">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b89c1-110">备注</span><span class="sxs-lookup"><span data-stu-id="b89c1-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b89c1-111">需求</span><span class="sxs-lookup"><span data-stu-id="b89c1-111">Requirements</span></span>  
 <span data-ttu-id="b89c1-112">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b89c1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b89c1-113">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b89c1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b89c1-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b89c1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b89c1-115">**.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b89c1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b89c1-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b89c1-116">See also</span></span>

- [<span data-ttu-id="b89c1-117">ICorDebugComObjectValue 接口</span><span class="sxs-lookup"><span data-stu-id="b89c1-117">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="b89c1-118">调试接口</span><span class="sxs-lookup"><span data-stu-id="b89c1-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
