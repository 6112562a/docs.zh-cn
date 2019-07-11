---
title: ICLRRuntimeInfo::GetProcAddress 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c196eafbc2ff1d851471355a630b860c7c02ba1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765538"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="3beef-102">ICLRRuntimeInfo::GetProcAddress 方法</span><span class="sxs-lookup"><span data-stu-id="3beef-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="3beef-103">获取指定的函数导出从公共语言运行时 (CLR) 与此接口关联的地址。</span><span class="sxs-lookup"><span data-stu-id="3beef-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="3beef-104">此方法取代[GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)函数。</span><span class="sxs-lookup"><span data-stu-id="3beef-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3beef-105">语法</span><span class="sxs-lookup"><span data-stu-id="3beef-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3beef-106">参数</span><span class="sxs-lookup"><span data-stu-id="3beef-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="3beef-107">[in]导出函数的名称。</span><span class="sxs-lookup"><span data-stu-id="3beef-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="3beef-108">[out]导出函数的地址。</span><span class="sxs-lookup"><span data-stu-id="3beef-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3beef-109">返回值</span><span class="sxs-lookup"><span data-stu-id="3beef-109">Return Value</span></span>  
 <span data-ttu-id="3beef-110">此方法返回以下特定 HRESULT 以及表示方法失败的 HRESULT 错误。</span><span class="sxs-lookup"><span data-stu-id="3beef-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="3beef-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3beef-111">HRESULT</span></span>|<span data-ttu-id="3beef-112">描述</span><span class="sxs-lookup"><span data-stu-id="3beef-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3beef-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="3beef-113">S_OK</span></span>|<span data-ttu-id="3beef-114">该方法已成功完成。</span><span class="sxs-lookup"><span data-stu-id="3beef-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="3beef-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3beef-115">E_POINTER</span></span>|<span data-ttu-id="3beef-116">`pszProcName` 或 `ppProc` 为 null。</span><span class="sxs-lookup"><span data-stu-id="3beef-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="3beef-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="3beef-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="3beef-118">指定的函数不是导出的函数。</span><span class="sxs-lookup"><span data-stu-id="3beef-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3beef-119">备注</span><span class="sxs-lookup"><span data-stu-id="3beef-119">Remarks</span></span>  
 <span data-ttu-id="3beef-120">此方法会导致 CLR 加载，但未初始化。</span><span class="sxs-lookup"><span data-stu-id="3beef-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3beef-121">要求</span><span class="sxs-lookup"><span data-stu-id="3beef-121">Requirements</span></span>  
 <span data-ttu-id="3beef-122">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3beef-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3beef-123">**标头：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3beef-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3beef-124">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="3beef-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3beef-125">**.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3beef-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3beef-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="3beef-126">See also</span></span>

- [<span data-ttu-id="3beef-127">ICLRRuntimeInfo 接口</span><span class="sxs-lookup"><span data-stu-id="3beef-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="3beef-128">承载接口</span><span class="sxs-lookup"><span data-stu-id="3beef-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="3beef-129">承载</span><span class="sxs-lookup"><span data-stu-id="3beef-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
