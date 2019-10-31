---
title: ICLRStrongName2 接口
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
ms.openlocfilehash: bc871c29f53a9ea4451a0fc1c747939724b0da87
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092247"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="3c9bf-102">ICLRStrongName2 接口</span><span class="sxs-lookup"><span data-stu-id="3c9bf-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="3c9bf-103">提供使用 SHA-1 安全哈希算法（SHA-256、SHA-384 和 SHA-512）组创建强名称的功能。</span><span class="sxs-lookup"><span data-stu-id="3c9bf-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3c9bf-104">方法</span><span class="sxs-lookup"><span data-stu-id="3c9bf-104">Methods</span></span>  
  
|<span data-ttu-id="3c9bf-105">方法</span><span class="sxs-lookup"><span data-stu-id="3c9bf-105">Method</span></span>|<span data-ttu-id="3c9bf-106">描述</span><span class="sxs-lookup"><span data-stu-id="3c9bf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c9bf-107">StrongNameGetPublicKeyEx 方法</span><span class="sxs-lookup"><span data-stu-id="3c9bf-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="3c9bf-108">获取公钥/私钥对中的公钥，并指定哈希算法和签名算法。</span><span class="sxs-lookup"><span data-stu-id="3c9bf-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="3c9bf-109">StrongNameSignatureVerificationEx2 方法</span><span class="sxs-lookup"><span data-stu-id="3c9bf-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="3c9bf-110">验证强名称程序集的签名，并提供从 ECMA 密钥到实际密钥的映射。</span><span class="sxs-lookup"><span data-stu-id="3c9bf-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c9bf-111">备注</span><span class="sxs-lookup"><span data-stu-id="3c9bf-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c9bf-112">要求</span><span class="sxs-lookup"><span data-stu-id="3c9bf-112">Requirements</span></span>  
 <span data-ttu-id="3c9bf-113">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c9bf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c9bf-114">**标头：** MetaHost</span><span class="sxs-lookup"><span data-stu-id="3c9bf-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3c9bf-115">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="3c9bf-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3c9bf-116">**.NET Framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c9bf-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
