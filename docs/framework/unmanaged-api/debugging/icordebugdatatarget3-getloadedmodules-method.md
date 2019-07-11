---
title: ICorDebugDataTarget3::GetLoadedModules 方法
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc62618c5872a2c3e3740be4c60ae02e386c1868
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750026"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="41d27-102">ICorDebugDataTarget3::GetLoadedModules 方法</span><span class="sxs-lookup"><span data-stu-id="41d27-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>
<span data-ttu-id="41d27-103">获取到目前为止已加载的模块的列表。</span><span class="sxs-lookup"><span data-stu-id="41d27-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41d27-104">语法</span><span class="sxs-lookup"><span data-stu-id="41d27-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41d27-105">参数</span><span class="sxs-lookup"><span data-stu-id="41d27-105">Parameters</span></span>  
 `cRequestedModules`  
 <span data-ttu-id="41d27-106">[in] 请求了其信息的模块数。</span><span class="sxs-lookup"><span data-stu-id="41d27-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="41d27-107">[out] 指向返回了相关信息的模块数的指针。</span><span class="sxs-lookup"><span data-stu-id="41d27-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="41d27-108">[out]指向数组的指针[ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)提供有关的信息的对象加载的模块。</span><span class="sxs-lookup"><span data-stu-id="41d27-108">[out] A pointer to an array of [ICorDebugLoadedModule](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41d27-109">备注</span><span class="sxs-lookup"><span data-stu-id="41d27-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41d27-110">此方法仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="41d27-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41d27-111">要求</span><span class="sxs-lookup"><span data-stu-id="41d27-111">Requirements</span></span>  
 <span data-ttu-id="41d27-112">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="41d27-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41d27-113">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41d27-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41d27-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41d27-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41d27-115">**.NET Framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41d27-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d27-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="41d27-116">See also</span></span>

- [<span data-ttu-id="41d27-117">ICorDebugDataTarget3 接口</span><span class="sxs-lookup"><span data-stu-id="41d27-117">ICorDebugDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)
- [<span data-ttu-id="41d27-118">调试接口</span><span class="sxs-lookup"><span data-stu-id="41d27-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
