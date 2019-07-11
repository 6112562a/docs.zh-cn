---
title: ICorDebugHeapValue2::CreateHandle 方法
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da5c5a12df5689f113857045ba4bcda696bda8f5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756728"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="439d3-102">ICorDebugHeapValue2::CreateHandle 方法</span><span class="sxs-lookup"><span data-stu-id="439d3-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="439d3-103">创建此 ICorDebugHeapValue2 对象所表示的堆值的指定类型的句柄。</span><span class="sxs-lookup"><span data-stu-id="439d3-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="439d3-104">语法</span><span class="sxs-lookup"><span data-stu-id="439d3-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="439d3-105">参数</span><span class="sxs-lookup"><span data-stu-id="439d3-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="439d3-106">[in]CorDebugHandleType 枚举，指定要创建的句柄的类型的值。</span><span class="sxs-lookup"><span data-stu-id="439d3-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="439d3-107">[out]指向一个 ICorDebugHandleValue 对象，表示此堆值的新句柄的地址的指针。</span><span class="sxs-lookup"><span data-stu-id="439d3-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="439d3-108">备注</span><span class="sxs-lookup"><span data-stu-id="439d3-108">Remarks</span></span>  
 <span data-ttu-id="439d3-109">句柄将与堆值相关联的应用程序域中创建和将变为无效，如果应用程序域被卸载。</span><span class="sxs-lookup"><span data-stu-id="439d3-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="439d3-110">多次调用相同的堆值此函数调用将创建多个句柄。</span><span class="sxs-lookup"><span data-stu-id="439d3-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="439d3-111">句柄的垃圾回收器性能影响，因为调试器应限制自身到相对较少的一次处于活动状态的句柄 (大约 256)。</span><span class="sxs-lookup"><span data-stu-id="439d3-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="439d3-112">要求</span><span class="sxs-lookup"><span data-stu-id="439d3-112">Requirements</span></span>  
 <span data-ttu-id="439d3-113">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="439d3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="439d3-114">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="439d3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="439d3-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="439d3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="439d3-116">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="439d3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
