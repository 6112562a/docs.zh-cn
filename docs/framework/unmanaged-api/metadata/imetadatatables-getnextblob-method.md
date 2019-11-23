---
title: IMetaDataTables::GetNextBlob 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
ms.openlocfilehash: 145fdde302e7e942ea77049b3faeabf60894dd94
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448408"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="be199-102">IMetaDataTables::GetNextBlob 方法</span><span class="sxs-lookup"><span data-stu-id="be199-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="be199-103">Gets the index of the next binary large object (BLOB) in the table.</span><span class="sxs-lookup"><span data-stu-id="be199-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be199-104">语法</span><span class="sxs-lookup"><span data-stu-id="be199-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be199-105">参数</span><span class="sxs-lookup"><span data-stu-id="be199-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="be199-106">[in] The index, as returned from a column of BLOBs.</span><span class="sxs-lookup"><span data-stu-id="be199-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="be199-107">[out] A pointer to the index of the next BLOB.</span><span class="sxs-lookup"><span data-stu-id="be199-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be199-108">要求</span><span class="sxs-lookup"><span data-stu-id="be199-108">Requirements</span></span>  
 <span data-ttu-id="be199-109">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be199-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be199-110">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="be199-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be199-111">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be199-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be199-112">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be199-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be199-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="be199-113">See also</span></span>

- [<span data-ttu-id="be199-114">IMetaDataTables 接口</span><span class="sxs-lookup"><span data-stu-id="be199-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="be199-115">IMetaDataTables2 接口</span><span class="sxs-lookup"><span data-stu-id="be199-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
