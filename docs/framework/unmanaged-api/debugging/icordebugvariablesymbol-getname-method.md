---
title: ICorDebugVariableSymbol::GetName 方法
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23637055e493c008db36b23515001895450d6ab9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967901"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="369f3-102">ICorDebugVariableSymbol::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="369f3-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="369f3-103">获取变量名。</span><span class="sxs-lookup"><span data-stu-id="369f3-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="369f3-104">语法</span><span class="sxs-lookup"><span data-stu-id="369f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="369f3-105">参数</span><span class="sxs-lookup"><span data-stu-id="369f3-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="369f3-106">[in] `szName` 缓冲区中的字符数。</span><span class="sxs-lookup"><span data-stu-id="369f3-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="369f3-107">[out] 指向实际写入 `szName` 缓冲区的字符数。缓冲区的字符数的指针。</span><span class="sxs-lookup"><span data-stu-id="369f3-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="369f3-108">指向包含变量名的字符数组的指针。</span><span class="sxs-lookup"><span data-stu-id="369f3-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="369f3-109">备注</span><span class="sxs-lookup"><span data-stu-id="369f3-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="369f3-110">此方法仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="369f3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="369f3-111">要求</span><span class="sxs-lookup"><span data-stu-id="369f3-111">Requirements</span></span>  
 <span data-ttu-id="369f3-112">**适用**请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="369f3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="369f3-113">**标头：** Cordebug.idl, Cordebug.idl</span><span class="sxs-lookup"><span data-stu-id="369f3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="369f3-114">**类库**CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="369f3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="369f3-115">**.NET Framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="369f3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="369f3-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="369f3-116">See also</span></span>

- [<span data-ttu-id="369f3-117">ICorDebugVariableSymbol 接口</span><span class="sxs-lookup"><span data-stu-id="369f3-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="369f3-118">调试接口</span><span class="sxs-lookup"><span data-stu-id="369f3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
