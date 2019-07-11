---
title: ICLRStrongName::StrongNameKeyDelete 方法
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 540fda24a8085a3066dc0485228d3ea3bc56fb98
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747787"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="66e1a-102">ICLRStrongName::StrongNameKeyDelete 方法</span><span class="sxs-lookup"><span data-stu-id="66e1a-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="66e1a-103">删除指定的密钥容器。</span><span class="sxs-lookup"><span data-stu-id="66e1a-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e1a-104">语法</span><span class="sxs-lookup"><span data-stu-id="66e1a-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66e1a-105">参数</span><span class="sxs-lookup"><span data-stu-id="66e1a-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="66e1a-106">[in]若要删除的密钥容器的名称。</span><span class="sxs-lookup"><span data-stu-id="66e1a-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66e1a-107">返回值</span><span class="sxs-lookup"><span data-stu-id="66e1a-107">Return Value</span></span>  
 <span data-ttu-id="66e1a-108">`S_OK` 如果成功，则完成的方法否则为指示失败的 HRESULT 值 (请参阅[常见的 HRESULT 值](https://go.microsoft.com/fwlink/?LinkId=213878)列表)。</span><span class="sxs-lookup"><span data-stu-id="66e1a-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66e1a-109">备注</span><span class="sxs-lookup"><span data-stu-id="66e1a-109">Remarks</span></span>  
 <span data-ttu-id="66e1a-110">使用[iclrstrongname:: Strongnamekeyinstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)方法来导入容器的公钥/私钥对。</span><span class="sxs-lookup"><span data-stu-id="66e1a-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66e1a-111">要求</span><span class="sxs-lookup"><span data-stu-id="66e1a-111">Requirements</span></span>  
 <span data-ttu-id="66e1a-112">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="66e1a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66e1a-113">**标头：** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="66e1a-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="66e1a-114">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="66e1a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66e1a-115">**.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66e1a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e1a-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="66e1a-116">See also</span></span>

- [<span data-ttu-id="66e1a-117">StrongNameKeyInstall 方法</span><span class="sxs-lookup"><span data-stu-id="66e1a-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="66e1a-118">ICLRStrongName 接口</span><span class="sxs-lookup"><span data-stu-id="66e1a-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
