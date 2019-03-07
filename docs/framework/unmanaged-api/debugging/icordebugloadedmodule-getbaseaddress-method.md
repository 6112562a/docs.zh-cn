---
title: ICorDebugLoadedModule::GetBaseAddress 方法
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31b398080c1355441a35871d0685283783efcd52
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501222"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="6a67f-102">ICorDebugLoadedModule::GetBaseAddress 方法</span><span class="sxs-lookup"><span data-stu-id="6a67f-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="6a67f-103">获取已加载模块的基址。</span><span class="sxs-lookup"><span data-stu-id="6a67f-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a67f-104">语法</span><span class="sxs-lookup"><span data-stu-id="6a67f-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a67f-105">参数</span><span class="sxs-lookup"><span data-stu-id="6a67f-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="6a67f-106">[out] 指向已加载模块的基址的指针。</span><span class="sxs-lookup"><span data-stu-id="6a67f-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a67f-107">备注</span><span class="sxs-lookup"><span data-stu-id="6a67f-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a67f-108">此方法仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="6a67f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a67f-109">要求</span><span class="sxs-lookup"><span data-stu-id="6a67f-109">Requirements</span></span>  
 <span data-ttu-id="6a67f-110">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a67f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a67f-111">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a67f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a67f-112">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a67f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a67f-113">**.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a67f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a67f-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="6a67f-114">See also</span></span>
- [<span data-ttu-id="6a67f-115">ICorDebugLoadedModule 接口</span><span class="sxs-lookup"><span data-stu-id="6a67f-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="6a67f-116">调试接口</span><span class="sxs-lookup"><span data-stu-id="6a67f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
