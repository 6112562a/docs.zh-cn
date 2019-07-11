---
title: ICorDebugReferenceValue::IsNull 方法
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed37e6eae3ec4f6e69215be6a42afe7fe86ff393
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768654"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="04be3-102">ICorDebugReferenceValue::IsNull 方法</span><span class="sxs-lookup"><span data-stu-id="04be3-102">ICorDebugReferenceValue::IsNull Method</span></span>
<span data-ttu-id="04be3-103">获取一个值，该值指示是否此 ICorDebugReferenceValue 为 null 值，在这种情况下`ICorDebugReferenceValue`不指向对象。</span><span class="sxs-lookup"><span data-stu-id="04be3-103">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04be3-104">语法</span><span class="sxs-lookup"><span data-stu-id="04be3-104">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04be3-105">参数</span><span class="sxs-lookup"><span data-stu-id="04be3-105">Parameters</span></span>  
 `pbNull`  
 <span data-ttu-id="04be3-106">[out]一个布尔值，是一个指向`true`如果此`ICorDebugReferenceValue`对象是 null; 否则为`pbNull`是`false`。</span><span class="sxs-lookup"><span data-stu-id="04be3-106">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04be3-107">要求</span><span class="sxs-lookup"><span data-stu-id="04be3-107">Requirements</span></span>  
 <span data-ttu-id="04be3-108">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04be3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04be3-109">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04be3-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04be3-110">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04be3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04be3-111">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04be3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
