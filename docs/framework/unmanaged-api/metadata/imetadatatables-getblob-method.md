---
title: IMetaDataTables::GetBlob 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
ms.openlocfilehash: f5a736d80f36afb8d0a643d4a4e36c9abff01995
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445439"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="a59cf-102">IMetaDataTables::GetBlob 方法</span><span class="sxs-lookup"><span data-stu-id="a59cf-102">IMetaDataTables::GetBlob Method</span></span>
<span data-ttu-id="a59cf-103">获取一个指针，该指针指向指定列索引处的二进制大型对象（BLOB）。</span><span class="sxs-lookup"><span data-stu-id="a59cf-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a59cf-104">语法</span><span class="sxs-lookup"><span data-stu-id="a59cf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a59cf-105">参数</span><span class="sxs-lookup"><span data-stu-id="a59cf-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="a59cf-106">中从中获取 `ppData`的内存地址。</span><span class="sxs-lookup"><span data-stu-id="a59cf-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="a59cf-107">弄一个指针，指向 `ppData`的大小（以字节为单位）。</span><span class="sxs-lookup"><span data-stu-id="a59cf-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="a59cf-108">弄指向所检索到的二进制数据的指针的指针。</span><span class="sxs-lookup"><span data-stu-id="a59cf-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a59cf-109">要求</span><span class="sxs-lookup"><span data-stu-id="a59cf-109">Requirements</span></span>  
 <span data-ttu-id="a59cf-110">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a59cf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a59cf-111">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="a59cf-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a59cf-112">**库：** 用作 Mscoree.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="a59cf-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a59cf-113">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a59cf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a59cf-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a59cf-114">See also</span></span>

- [<span data-ttu-id="a59cf-115">IMetaDataTables 接口</span><span class="sxs-lookup"><span data-stu-id="a59cf-115">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="a59cf-116">IMetaDataTables2 接口</span><span class="sxs-lookup"><span data-stu-id="a59cf-116">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
