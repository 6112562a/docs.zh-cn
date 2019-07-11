---
title: IMetaDataAssemblyImport::EnumFiles 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumFiles
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumFiles
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumFiles method [.NET Framework metadata]
- EnumFiles method [.NET Framework metadata]
ms.assetid: f0d721e2-b946-426d-8e20-9124bd04e4cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b32c402b20f9d7f0d370cfa6ec8376603efa8c3f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777991"
---
# <a name="imetadataassemblyimportenumfiles-method"></a><span data-ttu-id="2c9fa-102">IMetaDataAssemblyImport::EnumFiles 方法</span><span class="sxs-lookup"><span data-stu-id="2c9fa-102">IMetaDataAssemblyImport::EnumFiles Method</span></span>
<span data-ttu-id="2c9fa-103">枚举当前程序集清单中引用的文件。</span><span class="sxs-lookup"><span data-stu-id="2c9fa-103">Enumerates the files referenced in the current assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c9fa-104">语法</span><span class="sxs-lookup"><span data-stu-id="2c9fa-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumFiles (  
    [in, out] HCORENUM    *phEnum,   
    [out] mdFile          rFiles[],   
    [in]  ULONG           cMax,   
    [out] ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c9fa-105">参数</span><span class="sxs-lookup"><span data-stu-id="2c9fa-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="2c9fa-106">[in、 out]一个指向枚举器。</span><span class="sxs-lookup"><span data-stu-id="2c9fa-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="2c9fa-107">这必须是首次调用此方法的 null 值。</span><span class="sxs-lookup"><span data-stu-id="2c9fa-107">This must be a null value for the first call of this method.</span></span>  
  
 `rFiles`  
 <span data-ttu-id="2c9fa-108">[out]用于存储数组`mdFile`元数据标记。</span><span class="sxs-lookup"><span data-stu-id="2c9fa-108">[out] The array used to store the `mdFile` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2c9fa-109">[in]最大数目`mdFile`令牌可以置于`rFiles`。</span><span class="sxs-lookup"><span data-stu-id="2c9fa-109">[in] The maximum number of `mdFile` tokens that can be placed in `rFiles`.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="2c9fa-110">[out]数`mdFile`令牌实际置于`rFiles`。</span><span class="sxs-lookup"><span data-stu-id="2c9fa-110">[out] The number of `mdFile` tokens actually placed in `rFiles`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2c9fa-111">返回值</span><span class="sxs-lookup"><span data-stu-id="2c9fa-111">Return Value</span></span>  
  
|<span data-ttu-id="2c9fa-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2c9fa-112">HRESULT</span></span>|<span data-ttu-id="2c9fa-113">描述</span><span class="sxs-lookup"><span data-stu-id="2c9fa-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="2c9fa-114">`EnumFiles` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="2c9fa-114">`EnumFiles` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="2c9fa-115">没有要枚举的标记。</span><span class="sxs-lookup"><span data-stu-id="2c9fa-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="2c9fa-116">在这种情况下，`pcTokens`设置为零。</span><span class="sxs-lookup"><span data-stu-id="2c9fa-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c9fa-117">要求</span><span class="sxs-lookup"><span data-stu-id="2c9fa-117">Requirements</span></span>  
 <span data-ttu-id="2c9fa-118">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c9fa-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c9fa-119">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2c9fa-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c9fa-120">**库：** 用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="2c9fa-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c9fa-121">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c9fa-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c9fa-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="2c9fa-122">See also</span></span>

- [<span data-ttu-id="2c9fa-123">IMetaDataAssemblyImport 接口</span><span class="sxs-lookup"><span data-stu-id="2c9fa-123">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
