---
title: ICorDebugStringValue::GetString 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type:
- apiref
ms.openlocfilehash: e23133176cbd703a58c92f9bf1ead530b0bbb8a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178497"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="7501f-102">ICorDebugStringValue::GetString 方法</span><span class="sxs-lookup"><span data-stu-id="7501f-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="7501f-103">获取此 ICorDebugStringValue 引用的字符串。</span><span class="sxs-lookup"><span data-stu-id="7501f-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7501f-104">语法</span><span class="sxs-lookup"><span data-stu-id="7501f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7501f-105">parameters</span><span class="sxs-lookup"><span data-stu-id="7501f-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="7501f-106">[in] `szString` 数组的大小。</span><span class="sxs-lookup"><span data-stu-id="7501f-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="7501f-107">[出]指向数组中返回的字符数的`szString`指针。</span><span class="sxs-lookup"><span data-stu-id="7501f-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="7501f-108">[出]存储检索的字符串的数组。</span><span class="sxs-lookup"><span data-stu-id="7501f-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7501f-109">要求</span><span class="sxs-lookup"><span data-stu-id="7501f-109">Requirements</span></span>  
 <span data-ttu-id="7501f-110">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7501f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7501f-111">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7501f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7501f-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7501f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7501f-113">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7501f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
