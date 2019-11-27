---
title: IMetaDataImport::EnumEvents 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: 4faf8646b81f92ddf65eff15fdc610d275b37864
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440007"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="a15da-102">IMetaDataImport::EnumEvents 方法</span><span class="sxs-lookup"><span data-stu-id="a15da-102">IMetaDataImport::EnumEvents Method</span></span>
<span data-ttu-id="a15da-103">枚举指定的 TypeDef 标记的事件定义标记。</span><span class="sxs-lookup"><span data-stu-id="a15da-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a15da-104">语法</span><span class="sxs-lookup"><span data-stu-id="a15da-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (   
   [in, out] HCORENUM    *phEnum,   
   [in]      mdTypeDef   td,   
   [out]     mdEvent     rEvents[],   
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a15da-105">参数</span><span class="sxs-lookup"><span data-stu-id="a15da-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a15da-106">[in，out]指向枚举器的指针。</span><span class="sxs-lookup"><span data-stu-id="a15da-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="a15da-107">中要枚举其事件定义的 TypeDef 标记。</span><span class="sxs-lookup"><span data-stu-id="a15da-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="a15da-108">弄返回的事件的数组。</span><span class="sxs-lookup"><span data-stu-id="a15da-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a15da-109">[in] `rEvents` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="a15da-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="a15da-110">弄`rEvents`中返回的实际事件数。</span><span class="sxs-lookup"><span data-stu-id="a15da-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a15da-111">返回值</span><span class="sxs-lookup"><span data-stu-id="a15da-111">Return Value</span></span>  
  
|<span data-ttu-id="a15da-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a15da-112">HRESULT</span></span>|<span data-ttu-id="a15da-113">说明</span><span class="sxs-lookup"><span data-stu-id="a15da-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a15da-114">`EnumEvents` 成功返回。</span><span class="sxs-lookup"><span data-stu-id="a15da-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a15da-115">没有要枚举的事件。</span><span class="sxs-lookup"><span data-stu-id="a15da-115">There are no events to enumerate.</span></span> <span data-ttu-id="a15da-116">在这种情况下，`pcEvents` 为零。</span><span class="sxs-lookup"><span data-stu-id="a15da-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a15da-117">要求</span><span class="sxs-lookup"><span data-stu-id="a15da-117">Requirements</span></span>  
 <span data-ttu-id="a15da-118">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a15da-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a15da-119">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="a15da-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a15da-120">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="a15da-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a15da-121">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a15da-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a15da-122">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a15da-122">See also</span></span>

- [<span data-ttu-id="a15da-123">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="a15da-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a15da-124">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="a15da-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
