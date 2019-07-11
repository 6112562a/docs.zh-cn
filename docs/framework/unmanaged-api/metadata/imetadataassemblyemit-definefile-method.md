---
title: IMetaDataAssemblyEmit::DefineFile 方法
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineFile
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineFile method [.NET Framework metadata]
- DefineFile method [.NET Framework metadata]
ms.assetid: c065aadf-c1ca-4981-bde6-597042cb29c4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 54d5a233da2bf033d960fd02961ac89eb57151d2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776283"
---
# <a name="imetadataassemblyemitdefinefile-method"></a><span data-ttu-id="6b92b-102">IMetaDataAssemblyEmit::DefineFile 方法</span><span class="sxs-lookup"><span data-stu-id="6b92b-102">IMetaDataAssemblyEmit::DefineFile Method</span></span>
<span data-ttu-id="6b92b-103">创建包含此程序集引用的程序集的元数据的 `File` 元数据结构，并返回关联的元数据标记。</span><span class="sxs-lookup"><span data-stu-id="6b92b-103">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b92b-104">语法</span><span class="sxs-lookup"><span data-stu-id="6b92b-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineFile (  
    [in]  LPCWSTR        szName,   
    [in]  const void     *pbHashValue,   
    [in]  ULONG          cbHashValue,  
    [in]  DWORD          dwFileFlags,  
    [out] mdFile         *pmdf  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b92b-105">参数</span><span class="sxs-lookup"><span data-stu-id="6b92b-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="6b92b-106">[in]要使用的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="6b92b-106">[in] The name of the file to be consumed.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="6b92b-107">[in]指向与该程序集关联的哈希数据的指针。</span><span class="sxs-lookup"><span data-stu-id="6b92b-107">[in] A pointer to the hash data associated with the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="6b92b-108">[in]以字节为单位的大小`pbHashValue`。</span><span class="sxs-lookup"><span data-stu-id="6b92b-108">[in] The size in bytes of `pbHashValue`.</span></span>  
  
 `dwFileFlags`  
 <span data-ttu-id="6b92b-109">[in]按位组合`FileFlags`指定属性设置的值。</span><span class="sxs-lookup"><span data-stu-id="6b92b-109">[in] A bitwise combination of `FileFlags` values that specify property settings.</span></span>  
  
 `pmdf`  
 <span data-ttu-id="6b92b-110">[out]指向返回的指针`File`令牌。</span><span class="sxs-lookup"><span data-stu-id="6b92b-110">[out] A pointer to the returned `File` token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b92b-111">备注</span><span class="sxs-lookup"><span data-stu-id="6b92b-111">Remarks</span></span>  
 <span data-ttu-id="6b92b-112">一个`File`必须已在生成此程序集时，不包括包含的元数据的文件时此程序集的一部分的每个文件定义元数据结构。</span><span class="sxs-lookup"><span data-stu-id="6b92b-112">One `File` metadata structure must be defined for each file that was part of this assembly at the time that this assembly was built, excluding the file that contains the metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b92b-113">要求</span><span class="sxs-lookup"><span data-stu-id="6b92b-113">Requirements</span></span>  
 <span data-ttu-id="6b92b-114">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b92b-114">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b92b-115">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6b92b-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b92b-116">**库：** 用作 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="6b92b-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b92b-117">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b92b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b92b-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="6b92b-118">See also</span></span>

- [<span data-ttu-id="6b92b-119">IMetaDataAssemblyEmit 接口</span><span class="sxs-lookup"><span data-stu-id="6b92b-119">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
