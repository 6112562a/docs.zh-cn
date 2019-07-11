---
title: ICorDebugSymbolProvider2::GetFrameProps 方法
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 274da030bbbb7c614709b5150f08f37ddf5aaf5a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771161"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="52e97-102">ICorDebugSymbolProvider2::GetFrameProps 方法</span><span class="sxs-lookup"><span data-stu-id="52e97-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="52e97-103">返回启动方法相对虚拟地址的方法和具有代码相对虚拟地址的父框架。</span><span class="sxs-lookup"><span data-stu-id="52e97-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52e97-104">语法</span><span class="sxs-lookup"><span data-stu-id="52e97-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52e97-105">参数</span><span class="sxs-lookup"><span data-stu-id="52e97-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="52e97-106">[in] 代码相对虚拟地址。</span><span class="sxs-lookup"><span data-stu-id="52e97-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="52e97-107">[out] 指向方法的启动相对虚拟地址的指针。</span><span class="sxs-lookup"><span data-stu-id="52e97-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="52e97-108">[out] 指向框架的启动相对虚拟地址的指针。</span><span class="sxs-lookup"><span data-stu-id="52e97-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52e97-109">备注</span><span class="sxs-lookup"><span data-stu-id="52e97-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52e97-110">此方法仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="52e97-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52e97-111">要求</span><span class="sxs-lookup"><span data-stu-id="52e97-111">Requirements</span></span>  
 <span data-ttu-id="52e97-112">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="52e97-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52e97-113">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52e97-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52e97-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52e97-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52e97-115">**.NET Framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52e97-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e97-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="52e97-116">See also</span></span>

- [<span data-ttu-id="52e97-117">ICorDebugSymbolProvider2 接口</span><span class="sxs-lookup"><span data-stu-id="52e97-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="52e97-118">调试接口</span><span class="sxs-lookup"><span data-stu-id="52e97-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
