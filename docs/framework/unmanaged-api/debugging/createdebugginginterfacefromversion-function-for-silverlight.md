---
title: Silverlight 的 CreateDebuggingInterfaceFromVersion 函数
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96968956b513e1ae80a25f5fb4afea48bf888876
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739261"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="c7d22-102">Silverlight 的 CreateDebuggingInterfaceFromVersion 函数</span><span class="sxs-lookup"><span data-stu-id="c7d22-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="c7d22-103">接受从返回的公共语言运行时 (CLR) 版本字符串[CreateVersionStringFromModule 函数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)，并返回相应的调试器接口 (通常情况下， [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md))。</span><span class="sxs-lookup"><span data-stu-id="c7d22-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7d22-104">语法</span><span class="sxs-lookup"><span data-stu-id="c7d22-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7d22-105">参数</span><span class="sxs-lookup"><span data-stu-id="c7d22-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="c7d22-106">[in]目标调试对象，该值由返回的 CLR 版本字符串[CreateVersionStringFromModule 函数](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)。</span><span class="sxs-lookup"><span data-stu-id="c7d22-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="c7d22-107">[out] 指向“COM 对象的指针”的指针 (`IUnknown`)。</span><span class="sxs-lookup"><span data-stu-id="c7d22-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="c7d22-108">此对象强制转换为[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)对象返回前。</span><span class="sxs-lookup"><span data-stu-id="c7d22-108">This object will be cast to an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7d22-109">返回值</span><span class="sxs-lookup"><span data-stu-id="c7d22-109">Return Value</span></span>  
 <span data-ttu-id="c7d22-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7d22-110">S_OK</span></span>  
 <span data-ttu-id="c7d22-111">`ppCordb` 引用有效的对象实现[ICorDebug 接口](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)接口。</span><span class="sxs-lookup"><span data-stu-id="c7d22-111">`ppCordb` references a valid object that implements the [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="c7d22-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c7d22-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="c7d22-113">`szDebuggeeVersion` 或 `ppCordb` 为 null。</span><span class="sxs-lookup"><span data-stu-id="c7d22-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="c7d22-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="c7d22-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="c7d22-115">找不到 CLR 调试所需的组件。</span><span class="sxs-lookup"><span data-stu-id="c7d22-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="c7d22-116">这意味着未能在与目标 CoreCLR.dll 相同的目录中找到 mscordbi.dll 或 mscordaccore.dll。</span><span class="sxs-lookup"><span data-stu-id="c7d22-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="c7d22-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="c7d22-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="c7d22-118">mscordbi.dll 或 mscordaccore.dll 与目标 CoreCLR.dll 版本不一致。</span><span class="sxs-lookup"><span data-stu-id="c7d22-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="c7d22-119">E_FAIL（或其他 E_ 返回代码）</span><span class="sxs-lookup"><span data-stu-id="c7d22-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c7d22-120">无法返回[ICorDebug 接口](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="c7d22-120">Unable to return an [ICorDebug interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7d22-121">备注</span><span class="sxs-lookup"><span data-stu-id="c7d22-121">Remarks</span></span>  
 <span data-ttu-id="c7d22-122">返回的接口提供用于附加到目标进程中的 CLR 和调试 CLR 正在运行的托管代码的功能。</span><span class="sxs-lookup"><span data-stu-id="c7d22-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7d22-123">要求</span><span class="sxs-lookup"><span data-stu-id="c7d22-123">Requirements</span></span>  
 <span data-ttu-id="c7d22-124">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c7d22-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7d22-125">**标头：** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="c7d22-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="c7d22-126">**库：** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="c7d22-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="c7d22-127">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="c7d22-127">**.NET Framework Versions:** 3.5 SP1</span></span>
