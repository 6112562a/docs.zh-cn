---
title: ICorProfilerThreadEnum 接口
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 47359cd71460732100364f07e0dc5efacc44c760
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092040"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="4c5d8-102">ICorProfilerThreadEnum 接口</span><span class="sxs-lookup"><span data-stu-id="4c5d8-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="4c5d8-103">提供方法以按顺序循环访问公共语言运行时中的线程集合。</span><span class="sxs-lookup"><span data-stu-id="4c5d8-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c5d8-104">方法</span><span class="sxs-lookup"><span data-stu-id="4c5d8-104">Methods</span></span>  
  
|<span data-ttu-id="4c5d8-105">方法</span><span class="sxs-lookup"><span data-stu-id="4c5d8-105">Method</span></span>|<span data-ttu-id="4c5d8-106">描述</span><span class="sxs-lookup"><span data-stu-id="4c5d8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c5d8-107">Clone 方法</span><span class="sxs-lookup"><span data-stu-id="4c5d8-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="4c5d8-108">获取指向此 `ICorProfilerThreadEnum` 接口副本的接口指针。</span><span class="sxs-lookup"><span data-stu-id="4c5d8-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="4c5d8-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="4c5d8-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="4c5d8-110">获取应用程序使用的线程数。</span><span class="sxs-lookup"><span data-stu-id="4c5d8-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="4c5d8-111">Next 方法</span><span class="sxs-lookup"><span data-stu-id="4c5d8-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="4c5d8-112">从线程的序列集合获取指定的连续线程数，从序列中枚举器的当前位置开始。</span><span class="sxs-lookup"><span data-stu-id="4c5d8-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="4c5d8-113">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="4c5d8-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="4c5d8-114">将枚举器的光标移动到序列的起始位置。</span><span class="sxs-lookup"><span data-stu-id="4c5d8-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="4c5d8-115">Skip 方法</span><span class="sxs-lookup"><span data-stu-id="4c5d8-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="4c5d8-116">从当前位置前移枚举器的光标，以便跳过指定的元素数量。</span><span class="sxs-lookup"><span data-stu-id="4c5d8-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c5d8-117">备注</span><span class="sxs-lookup"><span data-stu-id="4c5d8-117">Remarks</span></span>  
 <span data-ttu-id="4c5d8-118">`ICorProfilerThreadEnum` 接口是一个枚举器。</span><span class="sxs-lookup"><span data-stu-id="4c5d8-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="4c5d8-119">它可以让数组接收器以其合适的速率从发送器拉取元素。</span><span class="sxs-lookup"><span data-stu-id="4c5d8-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="4c5d8-120">换而言之，接收器可以显式控制数组元素流，从而避免将大型数组作为方法形参传递方面的相关问题。</span><span class="sxs-lookup"><span data-stu-id="4c5d8-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c5d8-121">要求</span><span class="sxs-lookup"><span data-stu-id="4c5d8-121">Requirements</span></span>  
 <span data-ttu-id="4c5d8-122">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4c5d8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c5d8-123">**标头：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4c5d8-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c5d8-124">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c5d8-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c5d8-125">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c5d8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c5d8-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="4c5d8-126">See also</span></span>

- [<span data-ttu-id="4c5d8-127">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="4c5d8-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="4c5d8-128">Profiling 接口</span><span class="sxs-lookup"><span data-stu-id="4c5d8-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
