---
title: ICorDebugAppDomain4::GetObjectForCCW 方法
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 10d32314e46aba4f030b294cadc3cbb36e8742f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179054"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="eec57-102">ICorDebugAppDomain4::GetObjectForCCW 方法</span><span class="sxs-lookup"><span data-stu-id="eec57-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="eec57-103">从 COM 可调用包装器 (CCW) 指针获取托管对象。</span><span class="sxs-lookup"><span data-stu-id="eec57-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eec57-104">语法</span><span class="sxs-lookup"><span data-stu-id="eec57-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eec57-105">parameters</span><span class="sxs-lookup"><span data-stu-id="eec57-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="eec57-106">[in] COM 可调用包装器 (CCW) 指针。</span><span class="sxs-lookup"><span data-stu-id="eec57-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="eec57-107">[出]指向"ICorDebugValue"对象地址的指针，该对象表示对应于给定 CCW 指针的托管对象。</span><span class="sxs-lookup"><span data-stu-id="eec57-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eec57-108">备注</span><span class="sxs-lookup"><span data-stu-id="eec57-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eec57-109">要求</span><span class="sxs-lookup"><span data-stu-id="eec57-109">Requirements</span></span>  
 <span data-ttu-id="eec57-110">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eec57-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eec57-111">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eec57-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eec57-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eec57-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eec57-113">**.NET 框架版本：**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eec57-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eec57-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eec57-114">See also</span></span>

- [<span data-ttu-id="eec57-115">ICorDebugAppDomain4 接口</span><span class="sxs-lookup"><span data-stu-id="eec57-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="eec57-116">调试接口</span><span class="sxs-lookup"><span data-stu-id="eec57-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
