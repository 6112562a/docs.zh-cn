---
title: IMetaDataImport::GetMethodProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27b2867019085bf5b44f2ee364c07af66144d4b5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782332"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="c5985-102">IMetaDataImport::GetMethodProps 方法</span><span class="sxs-lookup"><span data-stu-id="c5985-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="c5985-103">获取与指定的 MethodDef 标记引用的方法关联的元数据。</span><span class="sxs-lookup"><span data-stu-id="c5985-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5985-104">语法</span><span class="sxs-lookup"><span data-stu-id="c5985-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5985-105">参数</span><span class="sxs-lookup"><span data-stu-id="c5985-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="c5985-106">[in]表示要返回的元数据的方法的 MethodDef 标记。</span><span class="sxs-lookup"><span data-stu-id="c5985-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="c5985-107">[out]指向表示实现方法的类型的 TypeDef 标记的指针。</span><span class="sxs-lookup"><span data-stu-id="c5985-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="c5985-108">[out]指向方法的名称的缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="c5985-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="c5985-109">[in]请求的大小`szMethod`。</span><span class="sxs-lookup"><span data-stu-id="c5985-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="c5985-110">[out]一个指向宽字符为单位的大小`szMethod`，或发生截断时，实际方法名称中的宽字符数。</span><span class="sxs-lookup"><span data-stu-id="c5985-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="c5985-111">[out]一个指向与方法关联的任何标志。</span><span class="sxs-lookup"><span data-stu-id="c5985-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="c5985-112">[out]指向方法的二进制元数据签名的指针。</span><span class="sxs-lookup"><span data-stu-id="c5985-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="c5985-113">[out]指向以字节为单位的大小的`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="c5985-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="c5985-114">[out]指向方法的相对虚拟地址的指针。</span><span class="sxs-lookup"><span data-stu-id="c5985-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="c5985-115">[out]指向方法的任何实现标志的指针。</span><span class="sxs-lookup"><span data-stu-id="c5985-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5985-116">要求</span><span class="sxs-lookup"><span data-stu-id="c5985-116">Requirements</span></span>  
 <span data-ttu-id="c5985-117">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5985-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5985-118">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c5985-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5985-119">**库：** 包含为 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="c5985-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c5985-120">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5985-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5985-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="c5985-121">See also</span></span>

- [<span data-ttu-id="c5985-122">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="c5985-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c5985-123">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="c5985-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
