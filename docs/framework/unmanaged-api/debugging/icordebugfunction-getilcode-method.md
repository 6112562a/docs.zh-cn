---
title: ICorDebugFunction::GetILCode 方法
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e32ce10b708afa5741d83cbd05f14accb4b2014f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754677"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="109af-102">ICorDebugFunction::GetILCode 方法</span><span class="sxs-lookup"><span data-stu-id="109af-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="109af-103">获取表示与此 ICorDebugFunction 对象关联的 Microsoft 中间语言 (MSIL) 代码的 ICorDebugCode 实例。</span><span class="sxs-lookup"><span data-stu-id="109af-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="109af-104">语法</span><span class="sxs-lookup"><span data-stu-id="109af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="109af-105">参数</span><span class="sxs-lookup"><span data-stu-id="109af-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="109af-106">[out]一个指向`ICorDebugCode`实例，则为 null，如果该函数不编译为 MSIL。</span><span class="sxs-lookup"><span data-stu-id="109af-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="109af-107">备注</span><span class="sxs-lookup"><span data-stu-id="109af-107">Remarks</span></span>  
 <span data-ttu-id="109af-108">如果已对此函数，允许编辑并继续`GetILCode`方法将获取对应于此函数的已编辑版本的公共语言运行时 (CLR) 中的代码的 MSIL 代码。</span><span class="sxs-lookup"><span data-stu-id="109af-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="109af-109">要求</span><span class="sxs-lookup"><span data-stu-id="109af-109">Requirements</span></span>  
 <span data-ttu-id="109af-110">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="109af-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="109af-111">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="109af-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="109af-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="109af-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="109af-113">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="109af-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
