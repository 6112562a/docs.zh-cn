---
title: ICorDebugArrayValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b8e9e9c9f43b45bf4f5d65bf80394c0fcd71325
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559263"
---
# <a name="icordebugarrayvalue-interface1"></a><span data-ttu-id="bf804-102">ICorDebugArrayValue Interface1</span><span class="sxs-lookup"><span data-stu-id="bf804-102">ICorDebugArrayValue Interface1</span></span>
<span data-ttu-id="bf804-103">表示一维或多维数组的 ICorDebugHeapValue 子类。</span><span class="sxs-lookup"><span data-stu-id="bf804-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf804-104">方法</span><span class="sxs-lookup"><span data-stu-id="bf804-104">Methods</span></span>  
  
|<span data-ttu-id="bf804-105">方法</span><span class="sxs-lookup"><span data-stu-id="bf804-105">Method</span></span>|<span data-ttu-id="bf804-106">描述</span><span class="sxs-lookup"><span data-stu-id="bf804-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf804-107">GetBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="bf804-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="bf804-108">获取数组中的每个维的基索引。</span><span class="sxs-lookup"><span data-stu-id="bf804-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="bf804-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="bf804-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="bf804-110">获取数组中的元素总数。</span><span class="sxs-lookup"><span data-stu-id="bf804-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="bf804-111">GetDimensions 方法</span><span class="sxs-lookup"><span data-stu-id="bf804-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="bf804-112">获取数组的维数。</span><span class="sxs-lookup"><span data-stu-id="bf804-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="bf804-113">GetElement 方法</span><span class="sxs-lookup"><span data-stu-id="bf804-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="bf804-114">获取表示给定的数组中元素的值。</span><span class="sxs-lookup"><span data-stu-id="bf804-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="bf804-115">GetElementAtPosition 方法</span><span class="sxs-lookup"><span data-stu-id="bf804-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="bf804-116">获取位于给定位置，将数组视为从零开始的一维数组的元素。</span><span class="sxs-lookup"><span data-stu-id="bf804-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="bf804-117">GetElementType 方法</span><span class="sxs-lookup"><span data-stu-id="bf804-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="bf804-118">获取数组中元素的简单类型。</span><span class="sxs-lookup"><span data-stu-id="bf804-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="bf804-119">GetRank 方法</span><span class="sxs-lookup"><span data-stu-id="bf804-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="bf804-120">获取数组中的维度数。</span><span class="sxs-lookup"><span data-stu-id="bf804-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="bf804-121">HasBaseIndicies 方法</span><span class="sxs-lookup"><span data-stu-id="bf804-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="bf804-122">确定数组是否具有基索引。</span><span class="sxs-lookup"><span data-stu-id="bf804-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf804-123">备注</span><span class="sxs-lookup"><span data-stu-id="bf804-123">Remarks</span></span>  
 <span data-ttu-id="bf804-124">`ICorDebugArrayValue` 支持单维度和多维数组。</span><span class="sxs-lookup"><span data-stu-id="bf804-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf804-125">此接口不支持跨计算机或跨进程远程调用。</span><span class="sxs-lookup"><span data-stu-id="bf804-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf804-126">要求</span><span class="sxs-lookup"><span data-stu-id="bf804-126">Requirements</span></span>  
 <span data-ttu-id="bf804-127">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bf804-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf804-128">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf804-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf804-129">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf804-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf804-130">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf804-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf804-131">请参阅</span><span class="sxs-lookup"><span data-stu-id="bf804-131">See also</span></span>
- [<span data-ttu-id="bf804-132">调试接口</span><span class="sxs-lookup"><span data-stu-id="bf804-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
