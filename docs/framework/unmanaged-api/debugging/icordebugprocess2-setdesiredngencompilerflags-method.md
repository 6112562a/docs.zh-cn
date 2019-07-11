---
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags 方法
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3582ebf2acee02d49aabafb03604c84249c4ce13
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747372"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="82222-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags 方法</span><span class="sxs-lookup"><span data-stu-id="82222-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="82222-103">设置必须按顺序运行时便会将该映像加载到当前进程的预编译映像中嵌入的标志。</span><span class="sxs-lookup"><span data-stu-id="82222-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82222-104">语法</span><span class="sxs-lookup"><span data-stu-id="82222-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82222-105">参数</span><span class="sxs-lookup"><span data-stu-id="82222-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="82222-106">[in]值为[CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)枚举，用于指定编译器标志用于选择正确的预编译的映像。</span><span class="sxs-lookup"><span data-stu-id="82222-106">[in] A value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82222-107">备注</span><span class="sxs-lookup"><span data-stu-id="82222-107">Remarks</span></span>  
 <span data-ttu-id="82222-108">`SetDesiredNGENCompilerFlags`方法指定，以便在运行时将该图像加载到此过程必须预编译的图像中嵌入的标志。</span><span class="sxs-lookup"><span data-stu-id="82222-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="82222-109">此方法设置的标志仅用于选择正确的预编译的映像。</span><span class="sxs-lookup"><span data-stu-id="82222-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="82222-110">如果不存在任何此类映像，在运行时将加载 Microsoft 中间语言 (MSIL) 映像，并在实时 (JIT) 编译器。</span><span class="sxs-lookup"><span data-stu-id="82222-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="82222-111">在这种情况下，仍必须使用调试器[ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)方法以根据需要进行 JIT 编译设置标志。</span><span class="sxs-lookup"><span data-stu-id="82222-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="82222-112">如果已加载图像，但某些 JIT 编译，则必须执行对该映像 （这也是如此，如果映像包含泛型），由指定的编译器标志`SetDesiredNGENCompilerFlags`方法将应用到额外的 JIT 编译。</span><span class="sxs-lookup"><span data-stu-id="82222-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="82222-113">`SetDesiredNGENCompilerFlags`必须在调用方法[icordebugmanagedcallback:: Createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)回调。</span><span class="sxs-lookup"><span data-stu-id="82222-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="82222-114">尝试调用`SetDesiredNGENCompilerFlags`方法之后将失败。</span><span class="sxs-lookup"><span data-stu-id="82222-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="82222-115">此外，尝试设置标志，也可以定义在`CorDebugJITCompilerFlags`枚举或不合法给定进程将失败。</span><span class="sxs-lookup"><span data-stu-id="82222-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82222-116">要求</span><span class="sxs-lookup"><span data-stu-id="82222-116">Requirements</span></span>  
 <span data-ttu-id="82222-117">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="82222-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82222-118">**标头：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82222-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82222-119">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82222-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82222-120">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82222-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82222-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="82222-121">See also</span></span>

- [<span data-ttu-id="82222-122">ICorDebug 接口</span><span class="sxs-lookup"><span data-stu-id="82222-122">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="82222-123">ICorDebugManagedCallback 接口</span><span class="sxs-lookup"><span data-stu-id="82222-123">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
