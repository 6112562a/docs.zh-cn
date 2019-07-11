---
title: IMetaDataImport::EnumMembers 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 50035799fcfa4c4b08404d63fe91e7dba85722fa
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758833"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="805c7-102">IMetaDataImport::EnumMembers 方法</span><span class="sxs-lookup"><span data-stu-id="805c7-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="805c7-103">枚举表示指定类型的成员的 MemberDef 标记。</span><span class="sxs-lookup"><span data-stu-id="805c7-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="805c7-104">语法</span><span class="sxs-lookup"><span data-stu-id="805c7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (   
   [in, out]  HCORENUM    *phEnum,   
   [in]  mdTypeDef   cl,   
   [out] mdToken     rMembers[],   
   [in]  ULONG       cMax,   
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="805c7-105">参数</span><span class="sxs-lookup"><span data-stu-id="805c7-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="805c7-106">[in、 out]一个指向枚举器。</span><span class="sxs-lookup"><span data-stu-id="805c7-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="805c7-107">[in]表示要枚举其成员的类型的 TypeDef 标记。</span><span class="sxs-lookup"><span data-stu-id="805c7-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="805c7-108">[out]用来保存 MemberDef 标记数组。</span><span class="sxs-lookup"><span data-stu-id="805c7-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="805c7-109">[in] `rMembers` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="805c7-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="805c7-110">[out]MemberDef 标记中返回的实际数目`rMembers`。</span><span class="sxs-lookup"><span data-stu-id="805c7-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="805c7-111">返回值</span><span class="sxs-lookup"><span data-stu-id="805c7-111">Return Value</span></span>  
  
|<span data-ttu-id="805c7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="805c7-112">HRESULT</span></span>|<span data-ttu-id="805c7-113">描述</span><span class="sxs-lookup"><span data-stu-id="805c7-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="805c7-114">`EnumMembers` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="805c7-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="805c7-115">没有要枚举的 MemberDef 标记。</span><span class="sxs-lookup"><span data-stu-id="805c7-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="805c7-116">在这种情况下，`pcTokens`为零。</span><span class="sxs-lookup"><span data-stu-id="805c7-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="805c7-117">备注</span><span class="sxs-lookup"><span data-stu-id="805c7-117">Remarks</span></span>  
 <span data-ttu-id="805c7-118">枚举的成员的类集合时`EnumMembers`仅返回成员 (字段和方法，但**不**属性或事件) 在类中直接定义。</span><span class="sxs-lookup"><span data-stu-id="805c7-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="805c7-119">它不返回任何成员的类继承，即使类提供实现这些继承的成员。</span><span class="sxs-lookup"><span data-stu-id="805c7-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="805c7-120">若要枚举继承的成员，调用方必须显式遍历继承链。</span><span class="sxs-lookup"><span data-stu-id="805c7-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="805c7-121">请注意，继承链的规则可能会有所不同，具体取决于语言或编译器发出的原始元数据。</span><span class="sxs-lookup"><span data-stu-id="805c7-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>
 
 <span data-ttu-id="805c7-122">属性和事件不会枚举`EnumMembers`。</span><span class="sxs-lookup"><span data-stu-id="805c7-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="805c7-123">若要枚举的请使用[EnumProperties](imetadataimport-enumproperties-method.md)或[EnumEvents](imetadataimport-enumevents-method.md)。</span><span class="sxs-lookup"><span data-stu-id="805c7-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="805c7-124">要求</span><span class="sxs-lookup"><span data-stu-id="805c7-124">Requirements</span></span>  
 <span data-ttu-id="805c7-125">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="805c7-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="805c7-126">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="805c7-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="805c7-127">**库：** 包含为 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="805c7-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="805c7-128">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="805c7-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="805c7-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="805c7-129">See also</span></span>

- [<span data-ttu-id="805c7-130">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="805c7-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="805c7-131">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="805c7-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
