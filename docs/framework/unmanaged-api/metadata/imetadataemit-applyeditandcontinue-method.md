---
title: IMetaDataEmit::ApplyEditAndContinue 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bee6b9cde81b71b5229ef5c4e939d0aea6b9a014
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711702"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="6f317-102">IMetaDataEmit::ApplyEditAndContinue 方法</span><span class="sxs-lookup"><span data-stu-id="6f317-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="6f317-103">使用指定的元数据中所做的更改更新当前程序集作用域。</span><span class="sxs-lookup"><span data-stu-id="6f317-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f317-104">语法</span><span class="sxs-lookup"><span data-stu-id="6f317-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f317-105">参数</span><span class="sxs-lookup"><span data-stu-id="6f317-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="6f317-106">\[在中\]指针，指向[IUnknown](/cpp/atl/iunknown)对象，表示从可移植可执行 (PE) 文件的增量元数据。</span><span class="sxs-lookup"><span data-stu-id="6f317-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="6f317-107">增量元数据是元数据，其中包括对模块的实际元数据的副本所做的更改的块。</span><span class="sxs-lookup"><span data-stu-id="6f317-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f317-108">要求</span><span class="sxs-lookup"><span data-stu-id="6f317-108">Requirements</span></span>  
 <span data-ttu-id="6f317-109">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f317-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f317-110">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6f317-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f317-111">**库：** 用作 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="6f317-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f317-112">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f317-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f317-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="6f317-113">See also</span></span>
- [<span data-ttu-id="6f317-114">IMetaDataEmit Interface</span><span class="sxs-lookup"><span data-stu-id="6f317-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="6f317-115">IMetaDataEmit2 Interface</span><span class="sxs-lookup"><span data-stu-id="6f317-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
