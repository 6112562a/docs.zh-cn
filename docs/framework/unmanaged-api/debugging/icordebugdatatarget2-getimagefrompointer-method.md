---
title: ICorDebugDataTarget2::GetImageFromPointer 方法
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: 58ad041b1243fabdc1948342730c81c5b8ff0991
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122146"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="cc623-102">ICorDebugDataTarget2::GetImageFromPointer 方法</span><span class="sxs-lookup"><span data-stu-id="cc623-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="cc623-103">返回该模块地址中的模块基址和大小。</span><span class="sxs-lookup"><span data-stu-id="cc623-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc623-104">语法</span><span class="sxs-lookup"><span data-stu-id="cc623-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc623-105">参数</span><span class="sxs-lookup"><span data-stu-id="cc623-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="cc623-106">一个表示模块中的地址的[CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值。</span><span class="sxs-lookup"><span data-stu-id="cc623-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="cc623-107">弄一个[CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)值，该值表示模块的基址。</span><span class="sxs-lookup"><span data-stu-id="cc623-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="cc623-108">指针指向模块大小。</span><span class="sxs-lookup"><span data-stu-id="cc623-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc623-109">备注</span><span class="sxs-lookup"><span data-stu-id="cc623-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc623-110">此方法仅适用于 .NET Native。</span><span class="sxs-lookup"><span data-stu-id="cc623-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc623-111">要求</span><span class="sxs-lookup"><span data-stu-id="cc623-111">Requirements</span></span>  
 <span data-ttu-id="cc623-112">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cc623-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc623-113">**标头**：CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc623-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc623-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc623-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc623-115">**.NET Framework 版本：** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc623-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc623-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="cc623-116">See also</span></span>

- [<span data-ttu-id="cc623-117">ICorDebugDataTarget2 接口</span><span class="sxs-lookup"><span data-stu-id="cc623-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="cc623-118">调试接口</span><span class="sxs-lookup"><span data-stu-id="cc623-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
