---
title: StrongNameGetPublicKey 函数
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d38879fbb296fa2ce0058e137499e25cd78cdb87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702335"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="37ef6-102">StrongNameGetPublicKey 函数</span><span class="sxs-lookup"><span data-stu-id="37ef6-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="37ef6-103">从私钥/公钥对中获取公钥。</span><span class="sxs-lookup"><span data-stu-id="37ef6-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="37ef6-104">加密服务提供商 (CSP) 中的密钥容器名称或作为原始字节的集合，可提供的密钥对。</span><span class="sxs-lookup"><span data-stu-id="37ef6-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="37ef6-105">此函数已弃用。</span><span class="sxs-lookup"><span data-stu-id="37ef6-105">This function has been deprecated.</span></span> <span data-ttu-id="37ef6-106">使用[iclrstrongname:: Strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)方法相反。</span><span class="sxs-lookup"><span data-stu-id="37ef6-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ef6-107">语法</span><span class="sxs-lookup"><span data-stu-id="37ef6-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37ef6-108">参数</span><span class="sxs-lookup"><span data-stu-id="37ef6-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="37ef6-109">[in]包含公钥/私钥对的密钥容器的名称。</span><span class="sxs-lookup"><span data-stu-id="37ef6-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="37ef6-110">如果`pbKeyBlob`为 null，`szKeyContainer`必须指定有效的 CSP 中的容器。</span><span class="sxs-lookup"><span data-stu-id="37ef6-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="37ef6-111">在这种情况下，`StrongNameGetPublicKey`从容器中存储的密钥对中提取的公钥。</span><span class="sxs-lookup"><span data-stu-id="37ef6-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="37ef6-112">如果`pbKeyBlob`不为 null，则假定为密钥对要包含在密钥二进制大型对象 (BLOB) 中。</span><span class="sxs-lookup"><span data-stu-id="37ef6-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="37ef6-113">键必须是 1024年位 Rivest 仅使用 Adleman (RSA) 签名密钥。</span><span class="sxs-lookup"><span data-stu-id="37ef6-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="37ef6-114">目前不支持任何其他类型的密钥。</span><span class="sxs-lookup"><span data-stu-id="37ef6-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="37ef6-115">[in]一个指向公钥/私钥对。</span><span class="sxs-lookup"><span data-stu-id="37ef6-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="37ef6-116">此对的格式创建的 Win32`CryptExportKey`函数。</span><span class="sxs-lookup"><span data-stu-id="37ef6-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="37ef6-117">如果`pbKeyBlob`是 null，指定的密钥容器`szKeyContainer`假定包含密钥对。</span><span class="sxs-lookup"><span data-stu-id="37ef6-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="37ef6-118">[in]大小，以字节为单位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="37ef6-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="37ef6-119">[out]返回的公钥 BLOB。</span><span class="sxs-lookup"><span data-stu-id="37ef6-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="37ef6-120">`ppbPublicKeyBlob`参数是分配的公共语言运行时，返回到调用方。</span><span class="sxs-lookup"><span data-stu-id="37ef6-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="37ef6-121">调用方必须使用释放内存[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函数。</span><span class="sxs-lookup"><span data-stu-id="37ef6-121">The caller must free the memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="37ef6-122">[out]返回公钥 BLOB 的大小。</span><span class="sxs-lookup"><span data-stu-id="37ef6-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37ef6-123">返回值</span><span class="sxs-lookup"><span data-stu-id="37ef6-123">Return Value</span></span>  
 <span data-ttu-id="37ef6-124">`true` 在成功完成;否则为`false`。</span><span class="sxs-lookup"><span data-stu-id="37ef6-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37ef6-125">备注</span><span class="sxs-lookup"><span data-stu-id="37ef6-125">Remarks</span></span>  
 <span data-ttu-id="37ef6-126">中包含的公钥[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)结构。</span><span class="sxs-lookup"><span data-stu-id="37ef6-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="37ef6-127">如果`StrongNameGetPublicKey`函数不成功完成，则调用[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函数检索最后一个生成的错误。</span><span class="sxs-lookup"><span data-stu-id="37ef6-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37ef6-128">要求</span><span class="sxs-lookup"><span data-stu-id="37ef6-128">Requirements</span></span>  
 <span data-ttu-id="37ef6-129">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="37ef6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37ef6-130">**标头：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="37ef6-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="37ef6-131">**库：** 包含为 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="37ef6-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="37ef6-132">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37ef6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37ef6-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="37ef6-133">See also</span></span>
- [<span data-ttu-id="37ef6-134">StrongNameGetPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="37ef6-134">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="37ef6-135">StrongNameTokenFromPublicKey 方法</span><span class="sxs-lookup"><span data-stu-id="37ef6-135">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="37ef6-136">ICLRStrongName 接口</span><span class="sxs-lookup"><span data-stu-id="37ef6-136">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="37ef6-137">PublicKeyBlob Strong Naming</span><span class="sxs-lookup"><span data-stu-id="37ef6-137">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
