---
title: IMetaDataImport::EnumInterfaceImpls 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumInterfaceImpls
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumInterfaceImpls
helpviewer_keywords:
- IMetaDataImport::EnumInterfaceImpls method [.NET Framework metadata]
- EnumInterfaceImpls method [.NET Framework metadata]
ms.assetid: ba6e178f-128b-4e47-a13c-b4be73eb106c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d0f94949cdc82cdecd52f003f3400c43014fabf
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780464"
---
# <a name="imetadataimportenuminterfaceimpls-method"></a><span data-ttu-id="9c01c-102">IMetaDataImport::EnumInterfaceImpls 方法</span><span class="sxs-lookup"><span data-stu-id="9c01c-102">IMetaDataImport::EnumInterfaceImpls Method</span></span>
<span data-ttu-id="9c01c-103">枚举指定实现的所有接口`TypeDef`。</span><span class="sxs-lookup"><span data-stu-id="9c01c-103">Enumerates all interfaces implemented by the specified `TypeDef`.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="9c01c-104">语法</span><span class="sxs-lookup"><span data-stu-id="9c01c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumInterfaceImpls (  
   [in, out]  HCORENUM       *phEnum,   
   [in]   mdTypeDef          td,  
   [out]  mdInterfaceImpl    rImpls[],   
   [in]   ULONG              cMax,  
   [out]  ULONG*             pcImpls  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c01c-105">参数</span><span class="sxs-lookup"><span data-stu-id="9c01c-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="9c01c-106">[in、 out]一个指向枚举器。</span><span class="sxs-lookup"><span data-stu-id="9c01c-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="9c01c-107">[in]表示接口实现的 MethodDef 标记是要枚举的 TypeDef 标记。</span><span class="sxs-lookup"><span data-stu-id="9c01c-107">[in] The token of the TypeDef whose MethodDef tokens representing interface implementations are to be enumerated.</span></span>  
  
 `rImpls`  
 <span data-ttu-id="9c01c-108">[out]用于存储 MethodDef 标记的数组。</span><span class="sxs-lookup"><span data-stu-id="9c01c-108">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="9c01c-109">[in] `rImpls` 数组的最大大小。</span><span class="sxs-lookup"><span data-stu-id="9c01c-109">[in] The maximum size of the `rImpls` array.</span></span>  
  
 `pcImpls`  
 <span data-ttu-id="9c01c-110">[out]令牌中返回的实际数目`rImpls`。</span><span class="sxs-lookup"><span data-stu-id="9c01c-110">[out] The actual number of tokens returned in `rImpls`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c01c-111">返回值</span><span class="sxs-lookup"><span data-stu-id="9c01c-111">Return Value</span></span>  
  
|<span data-ttu-id="9c01c-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9c01c-112">HRESULT</span></span>|<span data-ttu-id="9c01c-113">描述</span><span class="sxs-lookup"><span data-stu-id="9c01c-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9c01c-114">`EnumInterfaceImpls` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="9c01c-114">`EnumInterfaceImpls` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9c01c-115">没有要枚举的 MethodDef 标记。</span><span class="sxs-lookup"><span data-stu-id="9c01c-115">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="9c01c-116">在这种情况下，`pcImpls`设置为零。</span><span class="sxs-lookup"><span data-stu-id="9c01c-116">In that case, `pcImpls` is set to zero.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="9c01c-117">备注</span><span class="sxs-lookup"><span data-stu-id="9c01c-117">Remarks</span></span>

<span data-ttu-id="9c01c-118">此枚举返回的集合`mdInterfaceImpl`令牌，以实现由指定的每个接口进行`TypeDef`。</span><span class="sxs-lookup"><span data-stu-id="9c01c-118">The enumeration returns a collection of `mdInterfaceImpl` tokens for each interface implemented by the specified `TypeDef`.</span></span> <span data-ttu-id="9c01c-119">指定接口的顺序返回接口标记 (通过`DefineTypeDef`或`SetTypeDefProps`)。</span><span class="sxs-lookup"><span data-stu-id="9c01c-119">Interface tokens are returned in the order the interfaces were specified (through `DefineTypeDef` or `SetTypeDefProps`).</span></span> <span data-ttu-id="9c01c-120">所返回的属性`mdInterfaceImpl`可以使用查询令牌[GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md)。</span><span class="sxs-lookup"><span data-stu-id="9c01c-120">Properties of the returned `mdInterfaceImpl` tokens can be queried using [GetInterfaceImplProps](imetadataimport-getinterfaceimplprops-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="9c01c-121">要求</span><span class="sxs-lookup"><span data-stu-id="9c01c-121">Requirements</span></span>  
 <span data-ttu-id="9c01c-122">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9c01c-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c01c-123">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9c01c-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c01c-124">**库：** 包含为 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="9c01c-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c01c-125">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c01c-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c01c-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="9c01c-126">See also</span></span>

- [<span data-ttu-id="9c01c-127">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="9c01c-127">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9c01c-128">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="9c01c-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
