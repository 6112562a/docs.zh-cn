---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52a58f75ca7abd1bd1f871bcf4637bfd7eb7bdcd
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300544"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="8d1d8-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 方法</span><span class="sxs-lookup"><span data-stu-id="8d1d8-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>
<span data-ttu-id="8d1d8-103">[.NET Framework 4.6 和更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="8d1d8-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="8d1d8-104">启用或禁用某些类型的[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)异常回调。</span><span class="sxs-lookup"><span data-stu-id="8d1d8-104">Enables or disables certain types of [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d1d8-105">语法</span><span class="sxs-lookup"><span data-stu-id="8d1d8-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d1d8-106">参数</span><span class="sxs-lookup"><span data-stu-id="8d1d8-106">Parameters</span></span>  
 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="8d1d8-107">[in]</span><span class="sxs-lookup"><span data-stu-id="8d1d8-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d1d8-108">备注</span><span class="sxs-lookup"><span data-stu-id="8d1d8-108">Remarks</span></span>  
 <span data-ttu-id="8d1d8-109">如果 `enableExceptionsOutsideOfJMC` 的值是 `false`：</span><span class="sxs-lookup"><span data-stu-id="8d1d8-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="8d1d8-110">DEBUG_EXCEPTION_FIRST_CHANCE 异常不会导致回调到调试器。</span><span class="sxs-lookup"><span data-stu-id="8d1d8-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="8d1d8-111">DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 异常不会导致回调到调试器如果异常不会转义到用户代码 （即，从异常源到异常处理程序的路径有没有标记为 JustMyCode 或 JMC 的方法）。</span><span class="sxs-lookup"><span data-stu-id="8d1d8-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="8d1d8-112">`enableExceptionsOutsideOfJMC` 的默认值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="8d1d8-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d1d8-113">要求</span><span class="sxs-lookup"><span data-stu-id="8d1d8-113">Requirements</span></span>  
 <span data-ttu-id="8d1d8-114">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8d1d8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d1d8-115">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d1d8-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d1d8-116">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d1d8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d1d8-117">**.NET Framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d1d8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d1d8-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="8d1d8-118">See also</span></span>

- [<span data-ttu-id="8d1d8-119">ICorDebugProcess8 接口</span><span class="sxs-lookup"><span data-stu-id="8d1d8-119">ICorDebugProcess8 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)
- [<span data-ttu-id="8d1d8-120">调试接口</span><span class="sxs-lookup"><span data-stu-id="8d1d8-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
