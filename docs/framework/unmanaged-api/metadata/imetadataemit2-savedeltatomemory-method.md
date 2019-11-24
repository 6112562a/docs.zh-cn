---
title: IMetaDataEmit2::SaveDeltaToMemory 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
ms.openlocfilehash: d0718ff9a7e288ffc6a856032aa47949fda443f5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447885"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="bdc84-102">IMetaDataEmit2::SaveDeltaToMemory 方法</span><span class="sxs-lookup"><span data-stu-id="bdc84-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="bdc84-103">Saves changes from the current edit-and-continue session to memory.</span><span class="sxs-lookup"><span data-stu-id="bdc84-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdc84-104">语法</span><span class="sxs-lookup"><span data-stu-id="bdc84-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdc84-105">参数</span><span class="sxs-lookup"><span data-stu-id="bdc84-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="bdc84-106">[out] The address at which to begin writing the metadata delta.</span><span class="sxs-lookup"><span data-stu-id="bdc84-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="bdc84-107">[in] The size of the changes.</span><span class="sxs-lookup"><span data-stu-id="bdc84-107">[in] The size of the changes.</span></span> <span data-ttu-id="bdc84-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span><span class="sxs-lookup"><span data-stu-id="bdc84-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdc84-109">要求</span><span class="sxs-lookup"><span data-stu-id="bdc84-109">Requirements</span></span>  
 <span data-ttu-id="bdc84-110">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bdc84-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdc84-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bdc84-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bdc84-112">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bdc84-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bdc84-113">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdc84-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdc84-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="bdc84-114">See also</span></span>

- [<span data-ttu-id="bdc84-115">IMetaDataEmit2 Interface</span><span class="sxs-lookup"><span data-stu-id="bdc84-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="bdc84-116">IMetaDataEmit Interface</span><span class="sxs-lookup"><span data-stu-id="bdc84-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
