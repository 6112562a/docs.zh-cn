---
title: IMetaDataImport::EnumMethodImpls 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethodImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethodImpls
helpviewer_keywords:
- EnumMethodImpls method [.NET Framework metadata]
- IMetaDataImport::EnumMethodImpls method [.NET Framework metadata]
ms.assetid: 4e0f865d-88b5-44bd-be35-492622e5e08e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8be30e8c3b6bc7c03ede5f897f176e04153003b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781968"
---
# <a name="imetadataimportenummethodimpls-method"></a><span data-ttu-id="2f0c6-102">IMetaDataImport::EnumMethodImpls 方法</span><span class="sxs-lookup"><span data-stu-id="2f0c6-102">IMetaDataImport::EnumMethodImpls Method</span></span>
<span data-ttu-id="2f0c6-103">枚举表示指定类型的方法的 MethodBody 和 MethodDeclaration 标记。</span><span class="sxs-lookup"><span data-stu-id="2f0c6-103">Enumerates MethodBody and MethodDeclaration tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f0c6-104">语法</span><span class="sxs-lookup"><span data-stu-id="2f0c6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodImpls (  
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdToken     rMethodBody[],   
   [out]     mdToken     rMethodDecl[],   
   [in]      ULONG       cMax,   
   [in]      ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f0c6-105">参数</span><span class="sxs-lookup"><span data-stu-id="2f0c6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2f0c6-106">[in、 out]一个指向枚举器。</span><span class="sxs-lookup"><span data-stu-id="2f0c6-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2f0c6-107">对于首次调用此方法，这必须为 NULL。</span><span class="sxs-lookup"><span data-stu-id="2f0c6-107">This must be NULL for the first call of this method.</span></span>  
  
 `td`  
 <span data-ttu-id="2f0c6-108">[in]TypeDef 的类型的令牌要枚举的方法实现。</span><span class="sxs-lookup"><span data-stu-id="2f0c6-108">[in] A TypeDef token for the type whose method implementations to enumerate.</span></span>  
  
 `rMethodBody`  
 <span data-ttu-id="2f0c6-109">[out]要存储 MethodBody 令牌的数组。</span><span class="sxs-lookup"><span data-stu-id="2f0c6-109">[out] The array to store the MethodBody tokens.</span></span>  
  
 `rMethodDecl`  
 <span data-ttu-id="2f0c6-110">[out]要存储 MethodDeclaration 标记的数组。</span><span class="sxs-lookup"><span data-stu-id="2f0c6-110">[out] The array to store the MethodDeclaration tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2f0c6-111">[in]最大大小`rMethodBody`和`rMethodDecl`数组。</span><span class="sxs-lookup"><span data-stu-id="2f0c6-111">[in] The maximum size of the `rMethodBody` and `rMethodDecl` arrays.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="2f0c6-112">[in]方法中返回的实际数量`rMethodBody`和`rMethodDecl`。</span><span class="sxs-lookup"><span data-stu-id="2f0c6-112">[in] The actual number of methods returned in `rMethodBody` and `rMethodDecl`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f0c6-113">返回值</span><span class="sxs-lookup"><span data-stu-id="2f0c6-113">Return Value</span></span>  
  
|<span data-ttu-id="2f0c6-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f0c6-114">HRESULT</span></span>|<span data-ttu-id="2f0c6-115">描述</span><span class="sxs-lookup"><span data-stu-id="2f0c6-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2f0c6-116">`EnumMethodImpls` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="2f0c6-116">`EnumMethodImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2f0c6-117">没有要枚举的方法标记。</span><span class="sxs-lookup"><span data-stu-id="2f0c6-117">There are no method tokens to enumerate.</span></span> <span data-ttu-id="2f0c6-118">在这种情况下，`pcTokens`为零。</span><span class="sxs-lookup"><span data-stu-id="2f0c6-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f0c6-119">要求</span><span class="sxs-lookup"><span data-stu-id="2f0c6-119">Requirements</span></span>  
 <span data-ttu-id="2f0c6-120">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2f0c6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f0c6-121">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2f0c6-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2f0c6-122">**库：** 包含为 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="2f0c6-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2f0c6-123">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f0c6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f0c6-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="2f0c6-124">See also</span></span>

- [<span data-ttu-id="2f0c6-125">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="2f0c6-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2f0c6-126">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="2f0c6-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
