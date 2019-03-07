---
title: CreateDebuggingInterfaceFromVersion 函数
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e518834e018f0532f769c984befe7378a93b3f53
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491277"
---
# <a name="createdebugginginterfacefromversion-function"></a><span data-ttu-id="2ba24-102">CreateDebuggingInterfaceFromVersion 函数</span><span class="sxs-lookup"><span data-stu-id="2ba24-102">CreateDebuggingInterfaceFromVersion Function</span></span>
<span data-ttu-id="2ba24-103">创建[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)对象根据指定的版本信息。</span><span class="sxs-lookup"><span data-stu-id="2ba24-103">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 <span data-ttu-id="2ba24-104">此函数已过时中[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2ba24-104">This function is obsolete in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="2ba24-105">相反，若要获取公共语言运行时 (CLR) 2.0 接口，请使用[iclrruntimeinfo:: Getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)方法并指定类标识符 CLSID_CLRDebuggingLegacy 和 IID_ICorDebug 的接口标识符。</span><span class="sxs-lookup"><span data-stu-id="2ba24-105">Instead, to get an interface for the common language runtime (CLR) 2.0, use the [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) method and specify the class identifier CLSID_CLRDebuggingLegacy and the interface identifier IID_ICorDebug.</span></span> <span data-ttu-id="2ba24-106">若要获取接口供 CLR 4 或更高版本，调用[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)函数并指定类标识符 CLSID_CLRDebugging 和 IID_ICLRDebugging 的接口标识符。</span><span class="sxs-lookup"><span data-stu-id="2ba24-106">To get an interface for CLR 4 or later, call the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function and specify the class identifier CLSID_CLRDebugging and the interface identifier IID_ICLRDebugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ba24-107">语法</span><span class="sxs-lookup"><span data-stu-id="2ba24-107">Syntax</span></span>  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ba24-108">参数</span><span class="sxs-lookup"><span data-stu-id="2ba24-108">Parameters</span></span>  
 `iDebuggerVersion`  
 <span data-ttu-id="2ba24-109">[in]版本的`ICorDebug`这预期的调试器。</span><span class="sxs-lookup"><span data-stu-id="2ba24-109">[in] The version of `ICorDebug` that is expected by the debugger.</span></span> <span data-ttu-id="2ba24-110">请参阅[CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)枚举为有效的值。</span><span class="sxs-lookup"><span data-stu-id="2ba24-110">See the [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) enumeration for valid values.</span></span>  
  
 `szDebuggeeVersion`  
 <span data-ttu-id="2ba24-111">[in]与要调试的应用程序或进程关联的公共语言运行时版本。</span><span class="sxs-lookup"><span data-stu-id="2ba24-111">[in] The common language runtime version associated with the application or process to be debugged.</span></span> <span data-ttu-id="2ba24-112">请参阅[GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)或[GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)检索此值的信息的方法。</span><span class="sxs-lookup"><span data-stu-id="2ba24-112">See the [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) or [GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) method for information on retrieving this value.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="2ba24-113">[out]接收指向指针的位置`ICorDebug`对象。</span><span class="sxs-lookup"><span data-stu-id="2ba24-113">[out] The location that receives a pointer to the `ICorDebug` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ba24-114">返回值</span><span class="sxs-lookup"><span data-stu-id="2ba24-114">Return Value</span></span>  
 <span data-ttu-id="2ba24-115">除了以下值在 WinError.h 文件中定义时，此方法将返回标准 COM 错误代码。</span><span class="sxs-lookup"><span data-stu-id="2ba24-115">This method returns standard COM error codes as defined in the WinError.h file in addition to the following values.</span></span>  
  
|<span data-ttu-id="2ba24-116">返回代码</span><span class="sxs-lookup"><span data-stu-id="2ba24-116">Return code</span></span>|<span data-ttu-id="2ba24-117">描述</span><span class="sxs-lookup"><span data-stu-id="2ba24-117">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2ba24-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ba24-118">S_OK</span></span>|<span data-ttu-id="2ba24-119">该方法已成功完成。</span><span class="sxs-lookup"><span data-stu-id="2ba24-119">The method completed successfully.</span></span>|  
|<span data-ttu-id="2ba24-120">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="2ba24-120">E_INVALIDARG</span></span>|<span data-ttu-id="2ba24-121">`szDebuggeeVersion` 或`ppCordb`是 null 或版本字符串不正确。</span><span class="sxs-lookup"><span data-stu-id="2ba24-121">`szDebuggeeVersion` or `ppCordb` is null, or the version string is incorrect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ba24-122">备注</span><span class="sxs-lookup"><span data-stu-id="2ba24-122">Remarks</span></span>  
 <span data-ttu-id="2ba24-123">`szDebuggeeVersion`参数将映射到 MSCorDbi.dll 的相应版本。</span><span class="sxs-lookup"><span data-stu-id="2ba24-123">The `szDebuggeeVersion` parameter maps to the corresponding version of MSCorDbi.dll.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ba24-124">要求</span><span class="sxs-lookup"><span data-stu-id="2ba24-124">Requirements</span></span>  
 <span data-ttu-id="2ba24-125">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2ba24-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ba24-126">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ba24-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ba24-127">**库：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ba24-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ba24-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ba24-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ba24-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="2ba24-129">See also</span></span>
- [<span data-ttu-id="2ba24-130">弃用的 CLR 承载函数</span><span class="sxs-lookup"><span data-stu-id="2ba24-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
