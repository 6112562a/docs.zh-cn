---
title: IMetaDataEmit::TranslateSigWithScope 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1243a5ed1a3b741f1691cc4f0847ddcf17ac9669
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478383"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="fc2b4-102">IMetaDataEmit::TranslateSigWithScope 方法</span><span class="sxs-lookup"><span data-stu-id="fc2b4-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>
<span data-ttu-id="fc2b4-103">将程序集导入到当前作用域和合并的作用域获取新的元数据签名。</span><span class="sxs-lookup"><span data-stu-id="fc2b4-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc2b4-104">语法</span><span class="sxs-lookup"><span data-stu-id="fc2b4-104">Syntax</span></span>  
  
```  
HRESULT TranslateSigWithScope (   
    [in]  IMetaDataAssemblyImport   *pAssemImport,   
    [in]  const void                *pbHashValue,   
    [in]  ULONG                     cbHashValue,   
    [in]  IMetaDataImport           *import,   
    [in]  PCCOR_SIGNATURE           pbSigBlob,   
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,   
    [in]  IMetaDataEmit             *emit,   
    [out] PCOR_SIGNATURE            pvTranslatedSig,   
    [in]  ULONG                     cbTranslatedSigMax,   
    [out] ULONG                     *pcbTranslatedSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc2b4-105">参数</span><span class="sxs-lookup"><span data-stu-id="fc2b4-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="fc2b4-106">[in]用于导入程序集 （其中定义签名） 的接口。</span><span class="sxs-lookup"><span data-stu-id="fc2b4-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="fc2b4-107">[in]程序集哈希 blob。</span><span class="sxs-lookup"><span data-stu-id="fc2b4-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="fc2b4-108">[in]中的字节计数`pbHashValue`。</span><span class="sxs-lookup"><span data-stu-id="fc2b4-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="fc2b4-109">[in]用于导入元数据范围的接口。</span><span class="sxs-lookup"><span data-stu-id="fc2b4-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="fc2b4-110">[in]要导入的签名。</span><span class="sxs-lookup"><span data-stu-id="fc2b4-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="fc2b4-111">[in]大小，以字节为单位的`pbSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="fc2b4-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="fc2b4-112">[in]导出程序集的接口。</span><span class="sxs-lookup"><span data-stu-id="fc2b4-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="fc2b4-113">[in]导出元数据范围的接口。</span><span class="sxs-lookup"><span data-stu-id="fc2b4-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="fc2b4-114">[out]要保存已翻译的签名 blob 的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="fc2b4-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="fc2b4-115">[in]容量，以字节为单位的`pvTranslatedSig`。</span><span class="sxs-lookup"><span data-stu-id="fc2b4-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="fc2b4-116">[out]已翻译的签名中的实际字节数。</span><span class="sxs-lookup"><span data-stu-id="fc2b4-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc2b4-117">要求</span><span class="sxs-lookup"><span data-stu-id="fc2b4-117">Requirements</span></span>  
 <span data-ttu-id="fc2b4-118">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fc2b4-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc2b4-119">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fc2b4-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc2b4-120">**库：** 用作 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="fc2b4-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc2b4-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc2b4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2b4-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="fc2b4-122">See also</span></span>
- [<span data-ttu-id="fc2b4-123">IMetaDataAssemblyEmit 接口</span><span class="sxs-lookup"><span data-stu-id="fc2b4-123">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="fc2b4-124">IMetaDataAssemblyImport 接口</span><span class="sxs-lookup"><span data-stu-id="fc2b4-124">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="fc2b4-125">IMetaDataEmit Interface</span><span class="sxs-lookup"><span data-stu-id="fc2b4-125">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fc2b4-126">IMetaDataEmit2 Interface</span><span class="sxs-lookup"><span data-stu-id="fc2b4-126">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="fc2b4-127">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="fc2b4-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
