---
title: ICLRStrongName::StrongNameKeyInstall 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 415df9928572e095c529119bf2e726fa383577b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224944"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="ef759-102">ICLRStrongName::StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="ef759-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="ef759-103">将公钥/私钥对导入容器。</span><span class="sxs-lookup"><span data-stu-id="ef759-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef759-104">语法</span><span class="sxs-lookup"><span data-stu-id="ef759-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef759-105">参数</span><span class="sxs-lookup"><span data-stu-id="ef759-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="ef759-106">[in]密钥容器的名称。</span><span class="sxs-lookup"><span data-stu-id="ef759-106">[in] The name of the key container.</span></span> `wszKeyContainer` <span data-ttu-id="ef759-107">必须为非空字符串。</span><span class="sxs-lookup"><span data-stu-id="ef759-107">must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ef759-108">[in]二进制密钥对。</span><span class="sxs-lookup"><span data-stu-id="ef759-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ef759-109">[in]大小，以字节为单位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="ef759-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef759-110">返回值</span><span class="sxs-lookup"><span data-stu-id="ef759-110">Return Value</span></span>  
 `S_OK` <span data-ttu-id="ef759-111">如果成功，则完成的方法否则为指示失败的 HRESULT 值 (请参阅[常见的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)列表)。</span><span class="sxs-lookup"><span data-stu-id="ef759-111">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef759-112">备注</span><span class="sxs-lookup"><span data-stu-id="ef759-112">Remarks</span></span>  
 <span data-ttu-id="ef759-113">使用[iclrstrongname:: Strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)方法来删除密钥容器。</span><span class="sxs-lookup"><span data-stu-id="ef759-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef759-114">要求</span><span class="sxs-lookup"><span data-stu-id="ef759-114">Requirements</span></span>  
 <span data-ttu-id="ef759-115">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef759-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef759-116">**标头：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ef759-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ef759-117">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="ef759-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="ef759-118">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="ef759-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ef759-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="ef759-119">See also</span></span>

- [<span data-ttu-id="ef759-120">StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="ef759-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="ef759-121">ICLRStrongName 接口</span><span class="sxs-lookup"><span data-stu-id="ef759-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
