---
title: IMetaDataEmit::SetFieldProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ace278e0031d3e673418f50356f173c473a4832d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494319"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="880e6-102">IMetaDataEmit::SetFieldProps 方法</span><span class="sxs-lookup"><span data-stu-id="880e6-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="880e6-103">设置或更新指定的字段标记所引用的字段的默认值。</span><span class="sxs-lookup"><span data-stu-id="880e6-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="880e6-104">语法</span><span class="sxs-lookup"><span data-stu-id="880e6-104">Syntax</span></span>  
  
```  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="880e6-105">参数</span><span class="sxs-lookup"><span data-stu-id="880e6-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="880e6-106">[in]目标字段的标记。</span><span class="sxs-lookup"><span data-stu-id="880e6-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="880e6-107">[in]字段特性。</span><span class="sxs-lookup"><span data-stu-id="880e6-107">[in] Field attributes.</span></span> <span data-ttu-id="880e6-108">这是一个位掩码的`CorFieldAttr`值。</span><span class="sxs-lookup"><span data-stu-id="880e6-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="880e6-109">[in]`ELEMENT_TYPE_` *\** 的常量值。</span><span class="sxs-lookup"><span data-stu-id="880e6-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="880e6-110">这是`CorElementType`值。</span><span class="sxs-lookup"><span data-stu-id="880e6-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="880e6-111">如果未定义一个常量，将此值设置为`ELEMENT_TYPE_END`。</span><span class="sxs-lookup"><span data-stu-id="880e6-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="880e6-112">[in]字段的常量值。</span><span class="sxs-lookup"><span data-stu-id="880e6-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="880e6-113">[in]大小，以 Unicode 字符的`pValue`。</span><span class="sxs-lookup"><span data-stu-id="880e6-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="880e6-114">要求</span><span class="sxs-lookup"><span data-stu-id="880e6-114">Requirements</span></span>  
 <span data-ttu-id="880e6-115">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="880e6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="880e6-116">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="880e6-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="880e6-117">**库：** 用作 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="880e6-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="880e6-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="880e6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="880e6-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="880e6-119">See also</span></span>
- [<span data-ttu-id="880e6-120">IMetaDataEmit Interface</span><span class="sxs-lookup"><span data-stu-id="880e6-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="880e6-121">IMetaDataEmit2 Interface</span><span class="sxs-lookup"><span data-stu-id="880e6-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
