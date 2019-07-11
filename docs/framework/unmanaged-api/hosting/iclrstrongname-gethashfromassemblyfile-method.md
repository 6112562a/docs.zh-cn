---
title: ICLRStrongName::GetHashFromAssemblyFile 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6d5ea24e40357205051188b68de8b973d2cec18
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748245"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="3b78c-102">ICLRStrongName::GetHashFromAssemblyFile 方法</span><span class="sxs-lookup"><span data-stu-id="3b78c-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="3b78c-103">使用指定的哈希算法获取指定程序集文件的哈希。</span><span class="sxs-lookup"><span data-stu-id="3b78c-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b78c-104">语法</span><span class="sxs-lookup"><span data-stu-id="3b78c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b78c-105">参数</span><span class="sxs-lookup"><span data-stu-id="3b78c-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="3b78c-106">[in]要进行哈希处理的文件路径。</span><span class="sxs-lookup"><span data-stu-id="3b78c-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="3b78c-107">[in、 out]一个常量，它指定哈希算法。</span><span class="sxs-lookup"><span data-stu-id="3b78c-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="3b78c-108">使用默认哈希算法为零。</span><span class="sxs-lookup"><span data-stu-id="3b78c-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="3b78c-109">[out]返回的哈希缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="3b78c-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="3b78c-110">[in]请求的最大大小的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="3b78c-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="3b78c-111">[out]返回的大小，以字节为单位， `pbHash`。</span><span class="sxs-lookup"><span data-stu-id="3b78c-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b78c-112">返回值</span><span class="sxs-lookup"><span data-stu-id="3b78c-112">Return Value</span></span>  
 <span data-ttu-id="3b78c-113">`S_OK` 如果成功，则完成的方法否则为指示失败的 HRESULT 值 (请参阅[常见的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)列表)。</span><span class="sxs-lookup"><span data-stu-id="3b78c-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b78c-114">要求</span><span class="sxs-lookup"><span data-stu-id="3b78c-114">Requirements</span></span>  
 <span data-ttu-id="3b78c-115">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3b78c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b78c-116">**标头：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="3b78c-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3b78c-117">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="3b78c-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b78c-118">**.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b78c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b78c-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="3b78c-119">See also</span></span>

- [<span data-ttu-id="3b78c-120">GetHashFromAssemblyFileW 方法</span><span class="sxs-lookup"><span data-stu-id="3b78c-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="3b78c-121">ICLRStrongName 接口</span><span class="sxs-lookup"><span data-stu-id="3b78c-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
