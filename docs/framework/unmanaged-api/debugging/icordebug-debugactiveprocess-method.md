---
title: ICorDebug::DebugActiveProcess 方法
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe94203d315c32b62a191adf294a9c1310fe28e0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738260"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="10c1c-102">ICorDebug::DebugActiveProcess 方法</span><span class="sxs-lookup"><span data-stu-id="10c1c-102">ICorDebug::DebugActiveProcess Method</span></span>
<span data-ttu-id="10c1c-103">将调试器附加到现有进程。</span><span class="sxs-lookup"><span data-stu-id="10c1c-103">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10c1c-104">语法</span><span class="sxs-lookup"><span data-stu-id="10c1c-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10c1c-105">参数</span><span class="sxs-lookup"><span data-stu-id="10c1c-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="10c1c-106">[in]调试程序要附加的进程 ID。</span><span class="sxs-lookup"><span data-stu-id="10c1c-106">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="10c1c-107">[in]布尔值，设置为该值`true`如果调试程序应将用作 Win32 调试器进程和调度的非托管的回叫; 否则为`false`。</span><span class="sxs-lookup"><span data-stu-id="10c1c-107">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="10c1c-108">[out]指向表示调试器已附加到进程"ICorDebugProcess"对象的地址的指针。</span><span class="sxs-lookup"><span data-stu-id="10c1c-108">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10c1c-109">备注</span><span class="sxs-lookup"><span data-stu-id="10c1c-109">Remarks</span></span>  
 <span data-ttu-id="10c1c-110">不支持 Win9x 和非 x86 平台，例如基于 IA-64 和 AMD64 基于平台进行互操作调试。</span><span class="sxs-lookup"><span data-stu-id="10c1c-110">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10c1c-111">要求</span><span class="sxs-lookup"><span data-stu-id="10c1c-111">Requirements</span></span>  
 <span data-ttu-id="10c1c-112">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="10c1c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10c1c-113">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10c1c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10c1c-114">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10c1c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10c1c-115">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10c1c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10c1c-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="10c1c-116">See also</span></span>

- [<span data-ttu-id="10c1c-117">ICorDebug 接口</span><span class="sxs-lookup"><span data-stu-id="10c1c-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
