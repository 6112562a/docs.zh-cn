---
title: ICorDebugNativeFrame 接口
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
ms.openlocfilehash: 04bdbc49217236bc6c05a718cb4d42067cafd8bf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096678"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="5d7b3-102">ICorDebugNativeFrame 接口</span><span class="sxs-lookup"><span data-stu-id="5d7b3-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="5d7b3-103">用于本机帧的 ICorDebugFrame 的专用实现。</span><span class="sxs-lookup"><span data-stu-id="5d7b3-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d7b3-104">方法</span><span class="sxs-lookup"><span data-stu-id="5d7b3-104">Methods</span></span>  
  
|<span data-ttu-id="5d7b3-105">方法</span><span class="sxs-lookup"><span data-stu-id="5d7b3-105">Method</span></span>|<span data-ttu-id="5d7b3-106">描述</span><span class="sxs-lookup"><span data-stu-id="5d7b3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d7b3-107">CanSetIP 方法</span><span class="sxs-lookup"><span data-stu-id="5d7b3-107">CanSetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="5d7b3-108">获取一个值，该值指示是否可以安全地将指令指针设置为本机代码中的指定偏移位置。</span><span class="sxs-lookup"><span data-stu-id="5d7b3-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="5d7b3-109">GetIP 方法</span><span class="sxs-lookup"><span data-stu-id="5d7b3-109">GetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getip-method.md)|<span data-ttu-id="5d7b3-110">获取堆栈帧到本机代码的偏移量。</span><span class="sxs-lookup"><span data-stu-id="5d7b3-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="5d7b3-111">GetLocalDoubleRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="5d7b3-111">GetLocalDoubleRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="5d7b3-112">获取一个指向 ICorDebugValue 的指针，该指针表示存储在本机帧的两个内存寄存器中的参数或局部变量的值。</span><span class="sxs-lookup"><span data-stu-id="5d7b3-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="5d7b3-113">GetLocalMemoryRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="5d7b3-113">GetLocalMemoryRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="5d7b3-114">获取一个指向 `ICorDebugValue` 的指针，该指针表示本地变量的值，其中低位存储在指定的寄存器中，高位存储在指定的内存地址。</span><span class="sxs-lookup"><span data-stu-id="5d7b3-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="5d7b3-115">GetLocalMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="5d7b3-115">GetLocalMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="5d7b3-116">获取一个指向 `ICorDebugValue` 的指针，该指针表示存储在指定内存地址中的局部变量的值。</span><span class="sxs-lookup"><span data-stu-id="5d7b3-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="5d7b3-117">GetLocalRegisterMemoryValue 方法</span><span class="sxs-lookup"><span data-stu-id="5d7b3-117">GetLocalRegisterMemoryValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="5d7b3-118">获取一个指向 `ICorDebugValue` 的指针，该指针表示本地变量的值，其中高位存储在指定的寄存器中，低位存储在指定的内存地址</span><span class="sxs-lookup"><span data-stu-id="5d7b3-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="5d7b3-119">GetLocalRegisterValue 方法</span><span class="sxs-lookup"><span data-stu-id="5d7b3-119">GetLocalRegisterValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="5d7b3-120">获取一个指向 `ICorDebugValue` 的指针，该指针表示存储在指定本机寄存器中的参数值或本地变量的值。</span><span class="sxs-lookup"><span data-stu-id="5d7b3-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="5d7b3-121">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="5d7b3-121">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="5d7b3-122">获取一个指向[ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)的指针，该指针表示此 `ICorDebugNativeFrame`的注册集。</span><span class="sxs-lookup"><span data-stu-id="5d7b3-122">Gets a pointer to an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="5d7b3-123">SetIP 方法</span><span class="sxs-lookup"><span data-stu-id="5d7b3-123">SetIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-setip-method.md)|<span data-ttu-id="5d7b3-124">将指令指针设置为本机代码中的指定偏移位置。</span><span class="sxs-lookup"><span data-stu-id="5d7b3-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d7b3-125">备注</span><span class="sxs-lookup"><span data-stu-id="5d7b3-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d7b3-126">此接口不支持跨计算机或跨进程远程调用。</span><span class="sxs-lookup"><span data-stu-id="5d7b3-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d7b3-127">要求</span><span class="sxs-lookup"><span data-stu-id="5d7b3-127">Requirements</span></span>  
 <span data-ttu-id="5d7b3-128">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5d7b3-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d7b3-129">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d7b3-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d7b3-130">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d7b3-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d7b3-131">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d7b3-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d7b3-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="5d7b3-132">See also</span></span>

- [<span data-ttu-id="5d7b3-133">调试接口</span><span class="sxs-lookup"><span data-stu-id="5d7b3-133">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
