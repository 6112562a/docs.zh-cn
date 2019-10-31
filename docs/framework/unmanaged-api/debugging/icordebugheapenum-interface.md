---
title: ICorDebugHeapEnum 接口
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
ms.openlocfilehash: e8d1948a7d0ff23410ba8670628424a4067fb47d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138491"
---
# <a name="icordebugheapenum-interface"></a><span data-ttu-id="1a4f5-102">ICorDebugHeapEnum 接口</span><span class="sxs-lookup"><span data-stu-id="1a4f5-102">ICorDebugHeapEnum Interface</span></span>
<span data-ttu-id="1a4f5-103">提供针对托管堆上的对象的枚举器。</span><span class="sxs-lookup"><span data-stu-id="1a4f5-103">Provides an enumerator for objects on the managed heap.</span></span> <span data-ttu-id="1a4f5-104">此接口是 ICorDebugEnum 接口的子类。</span><span class="sxs-lookup"><span data-stu-id="1a4f5-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a4f5-105">方法</span><span class="sxs-lookup"><span data-stu-id="1a4f5-105">Methods</span></span>  
  
|<span data-ttu-id="1a4f5-106">方法</span><span class="sxs-lookup"><span data-stu-id="1a4f5-106">Method</span></span>|<span data-ttu-id="1a4f5-107">描述</span><span class="sxs-lookup"><span data-stu-id="1a4f5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a4f5-108">Next 方法</span><span class="sxs-lookup"><span data-stu-id="1a4f5-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|<span data-ttu-id="1a4f5-109">获取指定数量的[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)实例，这些实例包含有关托管堆上的对象的信息。</span><span class="sxs-lookup"><span data-stu-id="1a4f5-109">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a4f5-110">备注</span><span class="sxs-lookup"><span data-stu-id="1a4f5-110">Remarks</span></span>  
 <span data-ttu-id="1a4f5-111">`ICorDebugHeapEnum` 接口实现 ICorDebugEnum 接口。</span><span class="sxs-lookup"><span data-stu-id="1a4f5-111">The `ICorDebugHeapEnum` interface implements the ICorDebugEnum interface.</span></span>  
  
 <span data-ttu-id="1a4f5-112">`ICorDebugHeapEnum` 实例通过调用[ICorDebugProcess5：： EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)方法填充[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)实例。</span><span class="sxs-lookup"><span data-stu-id="1a4f5-112">An `ICorDebugHeapEnum` instance is populated with [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span> <span data-ttu-id="1a4f5-113">集合中的每个[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)实例都表示堆上的一个活动对象，或表示一个对象，该对象不是任何对象的根路径，但尚未由垃圾回收器收集。</span><span class="sxs-lookup"><span data-stu-id="1a4f5-113">Each [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instance in the collection represents either a live object on the heap or an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span> <span data-ttu-id="1a4f5-114">可以通过调用[ICorDebugHeapEnum：： Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)方法来枚举集合中的[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)对象。</span><span class="sxs-lookup"><span data-stu-id="1a4f5-114">The [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects in the collection can be enumerated by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a4f5-115">要求</span><span class="sxs-lookup"><span data-stu-id="1a4f5-115">Requirements</span></span>  
 <span data-ttu-id="1a4f5-116">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1a4f5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a4f5-117">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a4f5-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a4f5-118">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a4f5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a4f5-119">**.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a4f5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a4f5-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="1a4f5-120">See also</span></span>

- [<span data-ttu-id="1a4f5-121">调试接口</span><span class="sxs-lookup"><span data-stu-id="1a4f5-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
