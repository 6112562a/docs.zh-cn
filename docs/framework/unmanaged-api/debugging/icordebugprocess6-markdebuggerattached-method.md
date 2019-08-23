---
title: ICorDebugProcess6::MarkDebuggerAttached 方法
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c818b196f3252138f2a9c601b04f1d7a6727bc6b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912744"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="54401-102">ICorDebugProcess6::MarkDebuggerAttached 方法</span><span class="sxs-lookup"><span data-stu-id="54401-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>
<span data-ttu-id="54401-103">更改调试对象的内部状态，以便 .NET Framework 类库中的 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 方法返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="54401-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54401-104">语法</span><span class="sxs-lookup"><span data-stu-id="54401-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54401-105">参数</span><span class="sxs-lookup"><span data-stu-id="54401-105">Parameters</span></span>  
 `fIsAttached`  
 <span data-ttu-id="54401-106">如果 `true` 方法指出已连接调试程序，则为<xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>；否则即为 `false`。</span><span class="sxs-lookup"><span data-stu-id="54401-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="54401-107">返回值</span><span class="sxs-lookup"><span data-stu-id="54401-107">Return Value</span></span>  
 <span data-ttu-id="54401-108">该方法可以返回下表所列的值。</span><span class="sxs-lookup"><span data-stu-id="54401-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="54401-109">返回值</span><span class="sxs-lookup"><span data-stu-id="54401-109">Return value</span></span>|<span data-ttu-id="54401-110">描述</span><span class="sxs-lookup"><span data-stu-id="54401-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="54401-111">调试对象已成功更新。</span><span class="sxs-lookup"><span data-stu-id="54401-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="54401-112">程序集包含未加载的 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 方法或一些其他错误（例如元数据丢失），无法被识别。</span><span class="sxs-lookup"><span data-stu-id="54401-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="54401-113">该错误很常见，没有危害。</span><span class="sxs-lookup"><span data-stu-id="54401-113">This error is common and benign.</span></span> <span data-ttu-id="54401-114">你应当在其他程序集加载时再次调用方法。</span><span class="sxs-lookup"><span data-stu-id="54401-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="54401-115">其他失败 `HRESULT` 值。</span><span class="sxs-lookup"><span data-stu-id="54401-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="54401-116">其他值可能表示错误调试程序或编译器组件。</span><span class="sxs-lookup"><span data-stu-id="54401-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54401-117">备注</span><span class="sxs-lookup"><span data-stu-id="54401-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54401-118">此方法仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="54401-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54401-119">要求</span><span class="sxs-lookup"><span data-stu-id="54401-119">Requirements</span></span>  
 <span data-ttu-id="54401-120">**适用**请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="54401-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54401-121">**标头：** Cordebug.idl, Cordebug.idl</span><span class="sxs-lookup"><span data-stu-id="54401-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54401-122">**类库**CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54401-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54401-123">**.NET Framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54401-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54401-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="54401-124">See also</span></span>

- [<span data-ttu-id="54401-125">ICorDebugProcess6 接口</span><span class="sxs-lookup"><span data-stu-id="54401-125">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="54401-126">调试接口</span><span class="sxs-lookup"><span data-stu-id="54401-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
