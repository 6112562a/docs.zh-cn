---
title: ICorDebugEval2::NewParameterizedObjectNoConstructor 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObjectNoConstructor
helpviewer_keywords:
- NewParameterizedObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObjectNoConstructor method [.NET Framework debugging]
ms.assetid: f15b5b78-94f4-4eb9-b3b3-a621272f357c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4434f5d0eaa45c9cfcbadb20b29564f0643a2dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754446"
---
# <a name="icordebugeval2newparameterizedobjectnoconstructor-method"></a><span data-ttu-id="7df8a-102">ICorDebugEval2::NewParameterizedObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="7df8a-102">ICorDebugEval2::NewParameterizedObjectNoConstructor Method</span></span>
<span data-ttu-id="7df8a-103">实例化指定的类的新参数化的类型对象，而不会尝试调用构造函数方法。</span><span class="sxs-lookup"><span data-stu-id="7df8a-103">Instantiates a new parameterized type object of the specified class without attempting to call a constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7df8a-104">语法</span><span class="sxs-lookup"><span data-stu-id="7df8a-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObjectNoConstructor (  
    [in] ICorDebugClass        *pClass,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7df8a-105">参数</span><span class="sxs-lookup"><span data-stu-id="7df8a-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="7df8a-106">[in]指向一个 ICorDebugClass 对象，表示要进行实例化的对象的类的指针。</span><span class="sxs-lookup"><span data-stu-id="7df8a-106">[in] A pointer to an ICorDebugClass object that represents the class of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="7df8a-107">[in]传递的类型参数的数目。</span><span class="sxs-lookup"><span data-stu-id="7df8a-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="7df8a-108">[in]一个指针数组，其中每个指向一个 ICorDebugType 对象，表示要实例化的对象的类型参数。</span><span class="sxs-lookup"><span data-stu-id="7df8a-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7df8a-109">备注</span><span class="sxs-lookup"><span data-stu-id="7df8a-109">Remarks</span></span>  
 <span data-ttu-id="7df8a-110">`NewParameterizedObjectNoConstructor`方法将失败，如果类型参数数目不正确或错误类型的类型参数传递。</span><span class="sxs-lookup"><span data-stu-id="7df8a-110">The `NewParameterizedObjectNoConstructor` method will fail if an incorrect number of type arguments or the wrong types of type arguments are passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7df8a-111">要求</span><span class="sxs-lookup"><span data-stu-id="7df8a-111">Requirements</span></span>  
 <span data-ttu-id="7df8a-112">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7df8a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7df8a-113">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7df8a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7df8a-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7df8a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7df8a-115">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7df8a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
