---
title: ICLRStrongName::GetHashFromHandle 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8f6878d714704370c3f43451c9995a7c5adb5d1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748146"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="8cc25-102">ICLRStrongName::GetHashFromHandle 方法</span><span class="sxs-lookup"><span data-stu-id="8cc25-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="8cc25-103">生成具有指定的文件句柄，使用指定的哈希算法的文件的内容哈希代码。</span><span class="sxs-lookup"><span data-stu-id="8cc25-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cc25-104">语法</span><span class="sxs-lookup"><span data-stu-id="8cc25-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cc25-105">参数</span><span class="sxs-lookup"><span data-stu-id="8cc25-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="8cc25-106">[in]要进行哈希处理的文件句柄。</span><span class="sxs-lookup"><span data-stu-id="8cc25-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="8cc25-107">[in、 out]一个常量，它指定哈希算法。</span><span class="sxs-lookup"><span data-stu-id="8cc25-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="8cc25-108">使用默认的算法为零。</span><span class="sxs-lookup"><span data-stu-id="8cc25-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="8cc25-109">[out]返回的哈希缓冲区中。</span><span class="sxs-lookup"><span data-stu-id="8cc25-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="8cc25-110">[in]请求的最大大小的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="8cc25-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="8cc25-111">[out]大小 （字节），则返回的`pbHash`。</span><span class="sxs-lookup"><span data-stu-id="8cc25-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cc25-112">返回值</span><span class="sxs-lookup"><span data-stu-id="8cc25-112">Return Value</span></span>  
 <span data-ttu-id="8cc25-113">`S_OK` 如果成功，则完成的方法否则为指示失败的 HRESULT 值 (请参阅[常见的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)列表)。</span><span class="sxs-lookup"><span data-stu-id="8cc25-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cc25-114">要求</span><span class="sxs-lookup"><span data-stu-id="8cc25-114">Requirements</span></span>  
 <span data-ttu-id="8cc25-115">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8cc25-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cc25-116">**标头：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8cc25-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8cc25-117">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="8cc25-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8cc25-118">**.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cc25-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc25-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="8cc25-119">See also</span></span>

- [<span data-ttu-id="8cc25-120">ICLRStrongName 接口</span><span class="sxs-lookup"><span data-stu-id="8cc25-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
