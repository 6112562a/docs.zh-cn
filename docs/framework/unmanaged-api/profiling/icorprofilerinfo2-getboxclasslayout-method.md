---
title: ICorProfilerInfo2::GetBoxClassLayout 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d00c28862036c21c44f46c23fb09e947628dcf3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783049"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="b4bfe-102">ICorProfilerInfo2::GetBoxClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="b4bfe-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="b4bfe-103">获取有关进行装箱时指定的值类型所在的位置信息。</span><span class="sxs-lookup"><span data-stu-id="b4bfe-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4bfe-104">语法</span><span class="sxs-lookup"><span data-stu-id="b4bfe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4bfe-105">参数</span><span class="sxs-lookup"><span data-stu-id="b4bfe-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="b4bfe-106">[in]类，用于描述进行装箱的值类型的 ID。</span><span class="sxs-lookup"><span data-stu-id="b4bfe-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="b4bfe-107">[out]一个整数，表示相对于值类型的装箱的对象 ID 指针的偏移量。</span><span class="sxs-lookup"><span data-stu-id="b4bfe-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4bfe-108">备注</span><span class="sxs-lookup"><span data-stu-id="b4bfe-108">Remarks</span></span>  
 <span data-ttu-id="b4bfe-109">`pBufferOffset`值是一个框中的值类型的位置。</span><span class="sxs-lookup"><span data-stu-id="b4bfe-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="b4bfe-110">之后`pBufferOffset`应用到的已装箱对象的值类型的类布局可用于将对象的值解释。</span><span class="sxs-lookup"><span data-stu-id="b4bfe-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4bfe-111">要求</span><span class="sxs-lookup"><span data-stu-id="b4bfe-111">Requirements</span></span>  
 <span data-ttu-id="b4bfe-112">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4bfe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4bfe-113">**标头：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b4bfe-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b4bfe-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4bfe-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4bfe-115">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4bfe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4bfe-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="b4bfe-116">See also</span></span>

- [<span data-ttu-id="b4bfe-117">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="b4bfe-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="b4bfe-118">ICorProfilerInfo2 接口</span><span class="sxs-lookup"><span data-stu-id="b4bfe-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
