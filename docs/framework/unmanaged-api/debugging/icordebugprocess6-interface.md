---
title: “ICor调试进程6”接口
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 518c6ec99e4062bf8432809d3472baa395017da3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948612"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="09e96-102">“ICor调试进程6”接口</span><span class="sxs-lookup"><span data-stu-id="09e96-102">ICorDebugProcess6 Interface</span></span>
<span data-ttu-id="09e96-103">合理扩展 ICorDebugProcess 接口以启用解码托管的调试事件的本机异常调试事件和虚拟模块拆分中编码等功能。</span><span class="sxs-lookup"><span data-stu-id="09e96-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09e96-104">方法</span><span class="sxs-lookup"><span data-stu-id="09e96-104">Methods</span></span>  
  
|<span data-ttu-id="09e96-105">方法</span><span class="sxs-lookup"><span data-stu-id="09e96-105">Method</span></span>|<span data-ttu-id="09e96-106">描述</span><span class="sxs-lookup"><span data-stu-id="09e96-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09e96-107">DecodeEvent 方法</span><span class="sxs-lookup"><span data-stu-id="09e96-107">DecodeEvent Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="09e96-108">对封装于特殊构造的本机异常调试事件有效载荷中的托管调试事件进行解码。</span><span class="sxs-lookup"><span data-stu-id="09e96-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="09e96-109">EnableVirtualModuleSplitting 方法</span><span class="sxs-lookup"><span data-stu-id="09e96-109">EnableVirtualModuleSplitting Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="09e96-110">启用或禁用虚拟模块拆分。</span><span class="sxs-lookup"><span data-stu-id="09e96-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="09e96-111">GetCode 方法</span><span class="sxs-lookup"><span data-stu-id="09e96-111">GetCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|<span data-ttu-id="09e96-112">获取特定代码地址上的托管代码的相关信息。</span><span class="sxs-lookup"><span data-stu-id="09e96-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="09e96-113">GetExportStepInfo 方法</span><span class="sxs-lookup"><span data-stu-id="09e96-113">GetExportStepInfo Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="09e96-114">提供运行时导出功能信息以帮助单步调试托管代码。</span><span class="sxs-lookup"><span data-stu-id="09e96-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="09e96-115">MarkDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="09e96-115">MarkDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="09e96-116">更改调试对象的内部状态，以便 .NET Framework 类库中的 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 方法返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="09e96-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="09e96-117">ProcessStateChanged 方法</span><span class="sxs-lookup"><span data-stu-id="09e96-117">ProcessStateChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="09e96-118">通知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)运行进程。</span><span class="sxs-lookup"><span data-stu-id="09e96-118">Notifies [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09e96-119">备注</span><span class="sxs-lookup"><span data-stu-id="09e96-119">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09e96-120">此接口仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="09e96-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="09e96-121">尝试调用 `QueryInterface` 来检索接口指针会为 .NET Native 外部的 ICorDebug 方案返回 `E_NOINTERFACE`。</span><span class="sxs-lookup"><span data-stu-id="09e96-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09e96-122">要求</span><span class="sxs-lookup"><span data-stu-id="09e96-122">Requirements</span></span>  
 <span data-ttu-id="09e96-123">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09e96-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09e96-124">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09e96-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09e96-125">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09e96-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09e96-126">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09e96-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e96-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="09e96-127">See also</span></span>

- [<span data-ttu-id="09e96-128">调试接口</span><span class="sxs-lookup"><span data-stu-id="09e96-128">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="09e96-129">调试</span><span class="sxs-lookup"><span data-stu-id="09e96-129">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
