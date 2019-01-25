---
title: StrongNameKeyGenEx 函数
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a77ede995b08aba0822e9d86607e0d1e37bd6f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557326"
---
# <a name="strongnamekeygenex-function"></a><span data-ttu-id="6b9a7-102">StrongNameKeyGenEx 函数</span><span class="sxs-lookup"><span data-stu-id="6b9a7-102">StrongNameKeyGenEx Function</span></span>
<span data-ttu-id="6b9a7-103">生成新公钥/私钥对与指定的密钥大小，用于强名称。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-103">Generates a new public/private key pair with the specified key size, for strong name use.</span></span>  
  
 <span data-ttu-id="6b9a7-104">此函数已弃用。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-104">This function has been deprecated.</span></span> <span data-ttu-id="6b9a7-105">使用[iclrstrongname:: Strongnamekeygenex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)方法相反。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-105">Use the [ICLRStrongName::StrongNameKeyGenEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b9a7-106">语法</span><span class="sxs-lookup"><span data-stu-id="6b9a7-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b9a7-107">参数</span><span class="sxs-lookup"><span data-stu-id="6b9a7-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="6b9a7-108">[in]请求的密钥容器名称。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-108">[in] The requested key container name.</span></span> <span data-ttu-id="6b9a7-109">`wszKeyContainer` 必须为非空字符串，或空值，以生成一个临时名称。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-109">`wszKeyContainer` must be a non-empty string, or null to generate a temporary name.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6b9a7-110">[in]指定是否保留注册密钥。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-110">[in] Specifies whether to leave the key registered.</span></span> <span data-ttu-id="6b9a7-111">支持以下值：</span><span class="sxs-lookup"><span data-stu-id="6b9a7-111">The following values are supported:</span></span>  
  
-   <span data-ttu-id="6b9a7-112">0x00000000-时使用`wszKeyContainer`为 null 以生成一个临时密钥容器名称。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-112">0x00000000 - Used when `wszKeyContainer` is null to generate a temporary key container name.</span></span>  
  
-   <span data-ttu-id="6b9a7-113">0x00000001 (`SN_LEAVE_KEY`)-指定应保持注册密钥。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-113">0x00000001 (`SN_LEAVE_KEY`) - Specifies that the key should be left registered.</span></span>  
  
 `dwKeySize`  
 <span data-ttu-id="6b9a7-114">[in]请求的密钥，以位为单位的大小。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-114">[in] The requested size of the key, in bits.</span></span>  
  
 `ppbKeyBlob`  
 <span data-ttu-id="6b9a7-115">[out]返回的公共/专用密钥对。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-115">[out] The returned public/private key pair.</span></span>  
  
 `pcbKeyBlob`  
 <span data-ttu-id="6b9a7-116">[out]大小，以字节为单位的`ppbKeyBlob`。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-116">[out] The size, in bytes, of `ppbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b9a7-117">返回值</span><span class="sxs-lookup"><span data-stu-id="6b9a7-117">Return Value</span></span>  
 <span data-ttu-id="6b9a7-118">`true` 在成功完成;否则为`false`。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-118">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b9a7-119">备注</span><span class="sxs-lookup"><span data-stu-id="6b9a7-119">Remarks</span></span>  
 <span data-ttu-id="6b9a7-120">.NET framework 1.0 和 1.1 版需要`dwKeySize`1024 位使用强名称; 程序集进行签名的版本 2.0 添加为 2048年位密钥的支持。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-120">The .NET Framework versions 1.0 and 1.1 require a `dwKeySize` of 1024 bits to sign an assembly with a strong name; version 2.0 adds supports for 2048-bit keys.</span></span>  
  
 <span data-ttu-id="6b9a7-121">正在检索密钥后，应调用[StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)函数，以释放已分配的内存。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-121">After the key is retrieved, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="6b9a7-122">如果`StrongNameKeyGenEx`函数不成功完成，则调用[StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)函数检索最后一个生成的错误。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-122">If the `StrongNameKeyGenEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b9a7-123">要求</span><span class="sxs-lookup"><span data-stu-id="6b9a7-123">Requirements</span></span>  
 <span data-ttu-id="6b9a7-124">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b9a7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b9a7-125">**标头：** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6b9a7-125">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6b9a7-126">**库：** 包含为 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="6b9a7-126">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b9a7-127">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b9a7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b9a7-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="6b9a7-128">See also</span></span>
- [<span data-ttu-id="6b9a7-129">StrongNameKeyGenEx 方法</span><span class="sxs-lookup"><span data-stu-id="6b9a7-129">StrongNameKeyGenEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [<span data-ttu-id="6b9a7-130">StrongNameKeyGen 方法</span><span class="sxs-lookup"><span data-stu-id="6b9a7-130">StrongNameKeyGen Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)
- [<span data-ttu-id="6b9a7-131">ICLRStrongName 接口</span><span class="sxs-lookup"><span data-stu-id="6b9a7-131">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
