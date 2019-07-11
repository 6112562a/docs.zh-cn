---
title: GetRequestedRuntimeVersion 函数
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4083440903e6147ae645f2d6420f19160471841c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779576"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="7abbe-102">GetRequestedRuntimeVersion 函数</span><span class="sxs-lookup"><span data-stu-id="7abbe-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="7abbe-103">获取公共语言运行时 (CLR) 请求指定的应用程序的版本号。</span><span class="sxs-lookup"><span data-stu-id="7abbe-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="7abbe-104">如果未安装该版本，获取所请求的版本之前已安装的最新版本。</span><span class="sxs-lookup"><span data-stu-id="7abbe-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="7abbe-105">.NET Framework 4 中已弃用此函数。</span><span class="sxs-lookup"><span data-stu-id="7abbe-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7abbe-106">语法</span><span class="sxs-lookup"><span data-stu-id="7abbe-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7abbe-107">参数</span><span class="sxs-lookup"><span data-stu-id="7abbe-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="7abbe-108">[in]应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="7abbe-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="7abbe-109">[out]包含成功完成后的版本字符串的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="7abbe-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7abbe-110">[in]版本缓冲区的长度。</span><span class="sxs-lookup"><span data-stu-id="7abbe-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="7abbe-111">[out]指向的版本号字符串长度的指针。</span><span class="sxs-lookup"><span data-stu-id="7abbe-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7abbe-112">返回值</span><span class="sxs-lookup"><span data-stu-id="7abbe-112">Return Value</span></span>  
 <span data-ttu-id="7abbe-113">此方法返回标准的组件对象模型 (COM) 错误代码，定义在 WinError.h，除了以下值。</span><span class="sxs-lookup"><span data-stu-id="7abbe-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="7abbe-114">返回代码</span><span class="sxs-lookup"><span data-stu-id="7abbe-114">Return code</span></span>|<span data-ttu-id="7abbe-115">描述</span><span class="sxs-lookup"><span data-stu-id="7abbe-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7abbe-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="7abbe-116">S_OK</span></span>|<span data-ttu-id="7abbe-117">该方法已成功完成。</span><span class="sxs-lookup"><span data-stu-id="7abbe-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="7abbe-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="7abbe-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="7abbe-119">版本缓冲区不足够空间来存储的版本字符串。</span><span class="sxs-lookup"><span data-stu-id="7abbe-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="7abbe-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7abbe-120">E_POINTER</span></span>|<span data-ttu-id="7abbe-121">`pdwLength` 为 null。</span><span class="sxs-lookup"><span data-stu-id="7abbe-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7abbe-122">要求</span><span class="sxs-lookup"><span data-stu-id="7abbe-122">Requirements</span></span>  
 <span data-ttu-id="7abbe-123">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7abbe-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7abbe-124">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7abbe-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7abbe-125">**库：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7abbe-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7abbe-126">**.NET Framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7abbe-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7abbe-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="7abbe-127">See also</span></span>

- [<span data-ttu-id="7abbe-128">GetRequestedRuntimeInfo 函数</span><span class="sxs-lookup"><span data-stu-id="7abbe-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="7abbe-129">GetVersionFromProcess 函数</span><span class="sxs-lookup"><span data-stu-id="7abbe-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="7abbe-130">弃用的 CLR 承载函数</span><span class="sxs-lookup"><span data-stu-id="7abbe-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
