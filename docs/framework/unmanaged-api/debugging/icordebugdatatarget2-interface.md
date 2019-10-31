---
title: “ICor调试数据目标2”接口
ms.date: 03/30/2017
ms.assetid: 13f11388-2f91-48d8-98d6-6a4a63cb5746
ms.openlocfilehash: 3c59752949ca29cbd0ed5a34ec7aeb3d98b6f9b6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136483"
---
# <a name="icordebugdatatarget2-interface"></a><span data-ttu-id="8a3d3-102">“ICor调试数据目标2”接口</span><span class="sxs-lookup"><span data-stu-id="8a3d3-102">ICorDebugDataTarget2 Interface</span></span>
<span data-ttu-id="8a3d3-103">对[ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)接口进行逻辑扩展。</span><span class="sxs-lookup"><span data-stu-id="8a3d3-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a3d3-104">方法</span><span class="sxs-lookup"><span data-stu-id="8a3d3-104">Methods</span></span>  
  
|<span data-ttu-id="8a3d3-105">方法</span><span class="sxs-lookup"><span data-stu-id="8a3d3-105">Method</span></span>|<span data-ttu-id="8a3d3-106">描述</span><span class="sxs-lookup"><span data-stu-id="8a3d3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a3d3-107">CreateVirtualUnwinder 方法</span><span class="sxs-lookup"><span data-stu-id="8a3d3-107">CreateVirtualUnwinder Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-createvirtualunwinder-method.md)|<span data-ttu-id="8a3d3-108">创建一个从初始上下文（不一定是线程叶）开始展开的新堆栈开卷机。</span><span class="sxs-lookup"><span data-stu-id="8a3d3-108">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>|  
|[<span data-ttu-id="8a3d3-109">EnumerateThreadIDs 方法</span><span class="sxs-lookup"><span data-stu-id="8a3d3-109">EnumerateThreadIDs Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-enumeratethreadids-method.md)|<span data-ttu-id="8a3d3-110">返回一组活动线程 ID。</span><span class="sxs-lookup"><span data-stu-id="8a3d3-110">Returns a list of active thread IDs.</span></span>|  
|[<span data-ttu-id="8a3d3-111">GetImageFromPointer 方法</span><span class="sxs-lookup"><span data-stu-id="8a3d3-111">GetImageFromPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagefrompointer-method.md)|<span data-ttu-id="8a3d3-112">返回该模块地址中的模块基址和大小。</span><span class="sxs-lookup"><span data-stu-id="8a3d3-112">Returns the module base address and size from an address in that module.</span></span>|  
|[<span data-ttu-id="8a3d3-113">GetImageLocation 方法</span><span class="sxs-lookup"><span data-stu-id="8a3d3-113">GetImageLocation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getimagelocation-method.md)|<span data-ttu-id="8a3d3-114">返回模块基址中的模块路径。</span><span class="sxs-lookup"><span data-stu-id="8a3d3-114">Returns the path of a module from the module's base address.</span></span>|  
|[<span data-ttu-id="8a3d3-115">GetSymbolProviderForImage 方法</span><span class="sxs-lookup"><span data-stu-id="8a3d3-115">GetSymbolProviderForImage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-getsymbolproviderforimage-method.md)|<span data-ttu-id="8a3d3-116">返回该模块基址中的模块符号提供程序。</span><span class="sxs-lookup"><span data-stu-id="8a3d3-116">Returns the symbol-provider for a module from the base address of that module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a3d3-117">备注</span><span class="sxs-lookup"><span data-stu-id="8a3d3-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a3d3-118">此接口仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="8a3d3-118">This interface is available with .NET Native only.</span></span> <span data-ttu-id="8a3d3-119">如果在 .NET Native 外为 ICorDebug 方案实现此接口，则公共语言运行时将忽略此接口。</span><span class="sxs-lookup"><span data-stu-id="8a3d3-119">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a3d3-120">要求</span><span class="sxs-lookup"><span data-stu-id="8a3d3-120">Requirements</span></span>  
 <span data-ttu-id="8a3d3-121">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8a3d3-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a3d3-122">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a3d3-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a3d3-123">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a3d3-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a3d3-124">**.NET Framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a3d3-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a3d3-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="8a3d3-125">See also</span></span>

- [<span data-ttu-id="8a3d3-126">调试接口</span><span class="sxs-lookup"><span data-stu-id="8a3d3-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8a3d3-127">调试</span><span class="sxs-lookup"><span data-stu-id="8a3d3-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
