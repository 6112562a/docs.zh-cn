---
title: StrongNameSignatureGenerationEx 函数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9d2d5786ee7db334b8b9b0817c2319a6257dc9e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751744"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="0f663-102">StrongNameSignatureGenerationEx 函数</span><span class="sxs-lookup"><span data-stu-id="0f663-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="0f663-103">为指定的程序集，根据指定的标志生成的强名称签名。</span><span class="sxs-lookup"><span data-stu-id="0f663-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="0f663-104">此函数已弃用。</span><span class="sxs-lookup"><span data-stu-id="0f663-104">This function has been deprecated.</span></span> <span data-ttu-id="0f663-105">使用[iclrstrongname:: Strongnamesignaturegenerationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)方法相反。</span><span class="sxs-lookup"><span data-stu-id="0f663-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f663-106">语法</span><span class="sxs-lookup"><span data-stu-id="0f663-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f663-107">参数</span><span class="sxs-lookup"><span data-stu-id="0f663-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="0f663-108">[in]包含为其生成强名称签名的程序集的清单文件的路径。</span><span class="sxs-lookup"><span data-stu-id="0f663-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="0f663-109">[in]包含公钥/私钥对的密钥容器的名称。</span><span class="sxs-lookup"><span data-stu-id="0f663-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="0f663-110">如果`pbKeyBlob`为 null，`wszKeyContainer`必须指定加密服务提供商 (CSP) 内有效的容器。</span><span class="sxs-lookup"><span data-stu-id="0f663-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="0f663-111">在这种情况下，使用容器中存储的密钥对文件进行签名。</span><span class="sxs-lookup"><span data-stu-id="0f663-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="0f663-112">如果`pbKeyBlob`不为 null，则假定为密钥对要包含在密钥二进制大型对象 (BLOB) 中。</span><span class="sxs-lookup"><span data-stu-id="0f663-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="0f663-113">[in]一个指向公钥/私钥对。</span><span class="sxs-lookup"><span data-stu-id="0f663-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="0f663-114">此对的格式创建的 Win32`CryptExportKey`函数。</span><span class="sxs-lookup"><span data-stu-id="0f663-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="0f663-115">如果`pbKeyBlob`是 null，指定的密钥容器`wszKeyContainer`假定包含密钥对。</span><span class="sxs-lookup"><span data-stu-id="0f663-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="0f663-116">[in]大小，以字节为单位的`pbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="0f663-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="0f663-117">[out]指向该签名返回到公共语言运行时的位置的指针。</span><span class="sxs-lookup"><span data-stu-id="0f663-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="0f663-118">如果`ppbSignatureBlob`是 null，则运行时存储签名中指定的文件`wszFilePath`。</span><span class="sxs-lookup"><span data-stu-id="0f663-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="0f663-119">如果`ppbSignatureBlob`是不为 null，公共语言运行时分配用于返回签名的空间。</span><span class="sxs-lookup"><span data-stu-id="0f663-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="0f663-120">调用方必须释放此空间使用[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函数。</span><span class="sxs-lookup"><span data-stu-id="0f663-120">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="0f663-121">[out]以字节为单位，返回的签名的大小。</span><span class="sxs-lookup"><span data-stu-id="0f663-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0f663-122">[in]一个或多个以下值：</span><span class="sxs-lookup"><span data-stu-id="0f663-122">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="0f663-123">`SN_SIGN_ALL_FILES` (0x00000001) 的重新计算链接的模块的所有哈希值。</span><span class="sxs-lookup"><span data-stu-id="0f663-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="0f663-124">`SN_TEST_SIGN` (0x00000002) — 测试签名程序集。</span><span class="sxs-lookup"><span data-stu-id="0f663-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f663-125">返回值</span><span class="sxs-lookup"><span data-stu-id="0f663-125">Return Value</span></span>  
 <span data-ttu-id="0f663-126">`true` 在成功完成;否则为`false`。</span><span class="sxs-lookup"><span data-stu-id="0f663-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f663-127">备注</span><span class="sxs-lookup"><span data-stu-id="0f663-127">Remarks</span></span>  
 <span data-ttu-id="0f663-128">指定为 null`wszFilePath`来计算而无需创建签名的签名的大小。</span><span class="sxs-lookup"><span data-stu-id="0f663-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="0f663-129">可直接在文件中，存储或返回给调用方签名。</span><span class="sxs-lookup"><span data-stu-id="0f663-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="0f663-130">如果`SN_SIGN_ALL_FILES`指定但尚未包含的公共密钥 (同时`pbKeyBlob`和`wszFilePath`均为 null)，重新计算链接的模块的哈希值，但不重新签名程序集。</span><span class="sxs-lookup"><span data-stu-id="0f663-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="0f663-131">如果`SN_TEST_SIGN`指定，则公共语言运行时标头尚未修改以指示该程序集具有强名称签名。</span><span class="sxs-lookup"><span data-stu-id="0f663-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="0f663-132">如果`StrongNameSignatureGenerationEx`函数不成功完成，则调用[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函数检索最后一个生成的错误。</span><span class="sxs-lookup"><span data-stu-id="0f663-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f663-133">要求</span><span class="sxs-lookup"><span data-stu-id="0f663-133">Requirements</span></span>  
 <span data-ttu-id="0f663-134">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0f663-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f663-135">**标头：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="0f663-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0f663-136">**库：** 包含为 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="0f663-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f663-137">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f663-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f663-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="0f663-138">See also</span></span>

- [<span data-ttu-id="0f663-139">StrongNameSignatureGenerationEx 方法</span><span class="sxs-lookup"><span data-stu-id="0f663-139">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="0f663-140">StrongNameSignatureGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="0f663-140">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="0f663-141">ICLRStrongName 接口</span><span class="sxs-lookup"><span data-stu-id="0f663-141">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
