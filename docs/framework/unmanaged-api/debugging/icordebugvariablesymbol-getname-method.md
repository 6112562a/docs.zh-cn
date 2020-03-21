---
title: ICorDebugVariableSymbol::GetName 方法
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: abc0e368f259df1a3542b0fc8e7fbfd7e06cf6eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178444"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="86b8e-102">ICorDebugVariableSymbol::GetName 方法</span><span class="sxs-lookup"><span data-stu-id="86b8e-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="86b8e-103">获取变量名。</span><span class="sxs-lookup"><span data-stu-id="86b8e-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86b8e-104">语法</span><span class="sxs-lookup"><span data-stu-id="86b8e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86b8e-105">parameters</span><span class="sxs-lookup"><span data-stu-id="86b8e-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="86b8e-106">[in] `szName` 缓冲区中的字符数。</span><span class="sxs-lookup"><span data-stu-id="86b8e-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="86b8e-107">[out] 指向实际写入 `szName` 缓冲区的字符数。缓冲区的字符数的指针。</span><span class="sxs-lookup"><span data-stu-id="86b8e-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="86b8e-108">指向包含变量名的字符数组的指针。</span><span class="sxs-lookup"><span data-stu-id="86b8e-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86b8e-109">备注</span><span class="sxs-lookup"><span data-stu-id="86b8e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86b8e-110">此方法仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="86b8e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86b8e-111">要求</span><span class="sxs-lookup"><span data-stu-id="86b8e-111">Requirements</span></span>  
 <span data-ttu-id="86b8e-112">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="86b8e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86b8e-113">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86b8e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86b8e-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86b8e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86b8e-115">**.NET 框架版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86b8e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b8e-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="86b8e-116">See also</span></span>

- [<span data-ttu-id="86b8e-117">ICorDebugVariableSymbol 接口</span><span class="sxs-lookup"><span data-stu-id="86b8e-117">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="86b8e-118">调试接口</span><span class="sxs-lookup"><span data-stu-id="86b8e-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
