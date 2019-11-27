---
title: IMetaDataImport::EnumTypeRefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeRefs
helpviewer_keywords:
- EnumTypeRefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeRefs method [.NET Framework metadata]
ms.assetid: b4896b8f-8e97-469c-8089-e72a025661b5
topic_type:
- apiref
ms.openlocfilehash: 778ebf1d4fad0c8703964be88fdc3ff8c033bc28
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449980"
---
# <a name="imetadataimportenumtyperefs-method"></a><span data-ttu-id="c257e-102">IMetaDataImport::EnumTypeRefs 方法</span><span class="sxs-lookup"><span data-stu-id="c257e-102">IMetaDataImport::EnumTypeRefs Method</span></span>
<span data-ttu-id="c257e-103">枚举当前元数据范围内定义的 TypeRef 标记。</span><span class="sxs-lookup"><span data-stu-id="c257e-103">Enumerates TypeRef tokens defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c257e-104">语法</span><span class="sxs-lookup"><span data-stu-id="c257e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeRefs (  
   [in, out] HCORENUM    *phEnum,   
   [out] mdTypeRef       rTypeRefs[],  
   [in]  ULONG           cMax,   
   [out] ULONG           *pcTypeRefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c257e-105">参数</span><span class="sxs-lookup"><span data-stu-id="c257e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="c257e-106">[in，out]指向枚举器的指针。</span><span class="sxs-lookup"><span data-stu-id="c257e-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="c257e-107">第一次调用此方法时，此值必须为 NULL。</span><span class="sxs-lookup"><span data-stu-id="c257e-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeRefs`  
 <span data-ttu-id="c257e-108">弄用于存储 TypeRef 标记的数组。</span><span class="sxs-lookup"><span data-stu-id="c257e-108">[out] The array used to store the TypeRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="c257e-109">[in] `rTypeRefs` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="c257e-109">[in] The maximum size of the `rTypeRefs` array.</span></span>  
  
 `pcTypeRefs`  
 <span data-ttu-id="c257e-110">弄一个指针，指向 `rTypeRefs`中返回的 TypeRef 标记的数目。</span><span class="sxs-lookup"><span data-stu-id="c257e-110">[out] A pointer to the number of TypeRef tokens returned in `rTypeRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c257e-111">返回值</span><span class="sxs-lookup"><span data-stu-id="c257e-111">Return Value</span></span>  
  
|<span data-ttu-id="c257e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c257e-112">HRESULT</span></span>|<span data-ttu-id="c257e-113">说明</span><span class="sxs-lookup"><span data-stu-id="c257e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c257e-114">`EnumTypeRefs` 成功返回。</span><span class="sxs-lookup"><span data-stu-id="c257e-114">`EnumTypeRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c257e-115">没有要枚举的令牌。</span><span class="sxs-lookup"><span data-stu-id="c257e-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="c257e-116">在这种情况下，`pcTypeRefs` 为零。</span><span class="sxs-lookup"><span data-stu-id="c257e-116">In that case, `pcTypeRefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c257e-117">备注</span><span class="sxs-lookup"><span data-stu-id="c257e-117">Remarks</span></span>  
 <span data-ttu-id="c257e-118">TypeRef 标记表示对类型的引用。</span><span class="sxs-lookup"><span data-stu-id="c257e-118">A TypeRef token represents a reference to a type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c257e-119">要求</span><span class="sxs-lookup"><span data-stu-id="c257e-119">Requirements</span></span>  
 <span data-ttu-id="c257e-120">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c257e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c257e-121">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="c257e-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c257e-122">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="c257e-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c257e-123">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c257e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c257e-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c257e-124">See also</span></span>

- [<span data-ttu-id="c257e-125">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="c257e-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c257e-126">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="c257e-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
