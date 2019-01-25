---
title: “ICor调试异常调试事件”接口
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7d2407e56b029d22d25a4836f4def1c55f979ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54550521"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="95de2-102">“ICor调试异常调试事件”接口</span><span class="sxs-lookup"><span data-stu-id="95de2-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="95de2-103">扩展了[icor 调试调试事件](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)接口以支持异常事件。</span><span class="sxs-lookup"><span data-stu-id="95de2-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95de2-104">方法</span><span class="sxs-lookup"><span data-stu-id="95de2-104">Methods</span></span>  
  
|<span data-ttu-id="95de2-105">方法</span><span class="sxs-lookup"><span data-stu-id="95de2-105">Method</span></span>|<span data-ttu-id="95de2-106">描述</span><span class="sxs-lookup"><span data-stu-id="95de2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95de2-107">GetFlags 方法</span><span class="sxs-lookup"><span data-stu-id="95de2-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="95de2-108">获取指示是否可拦截异常的标志。</span><span class="sxs-lookup"><span data-stu-id="95de2-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="95de2-109">GetNativeIP 方法</span><span class="sxs-lookup"><span data-stu-id="95de2-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="95de2-110">获取此异常调试事件的本机接口指针。</span><span class="sxs-lookup"><span data-stu-id="95de2-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="95de2-111">GetStackPointer 方法</span><span class="sxs-lookup"><span data-stu-id="95de2-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="95de2-112">获取此异常调试事件的堆栈指针。</span><span class="sxs-lookup"><span data-stu-id="95de2-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95de2-113">备注</span><span class="sxs-lookup"><span data-stu-id="95de2-113">Remarks</span></span>  
 <span data-ttu-id="95de2-114">`ICorDebugExceptionDebugEvent` 接口由以下事件类型实现：</span><span class="sxs-lookup"><span data-stu-id="95de2-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
-   [<span data-ttu-id="95de2-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="95de2-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="95de2-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="95de2-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="95de2-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="95de2-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="95de2-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="95de2-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="95de2-119">此接口仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="95de2-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="95de2-120">尝试调用 `QueryInterface` 来检索接口指针会为 .NET Native 外部的 ICorDebug 方案返回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="95de2-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95de2-121">要求</span><span class="sxs-lookup"><span data-stu-id="95de2-121">Requirements</span></span>  
 <span data-ttu-id="95de2-122">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="95de2-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95de2-123">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95de2-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95de2-124">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95de2-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95de2-125">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95de2-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95de2-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="95de2-126">See also</span></span>
- [<span data-ttu-id="95de2-127">调试接口</span><span class="sxs-lookup"><span data-stu-id="95de2-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="95de2-128">调试</span><span class="sxs-lookup"><span data-stu-id="95de2-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
