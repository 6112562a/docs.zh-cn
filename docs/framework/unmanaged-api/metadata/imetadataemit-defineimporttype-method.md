---
title: IMetaDataEmit::DefineImportType 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineImportType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineImportType
helpviewer_keywords:
- DefineImportType method [.NET Framework metadata]
- IMetaDataEmit::DefineImportType method [.NET Framework metadata]
ms.assetid: 37fd27af-8062-4904-ace4-51bb78ec600a
topic_type:
- apiref
ms.openlocfilehash: 6825a5198976cc7ab2c04ebd6e782418dcf4a8f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177682"
---
# <a name="imetadataemitdefineimporttype-method"></a><span data-ttu-id="f72f1-102">IMetaDataEmit::DefineImportType 方法</span><span class="sxs-lookup"><span data-stu-id="f72f1-102">IMetaDataEmit::DefineImportType Method</span></span>
<span data-ttu-id="f72f1-103">创建对在当前作用域之外定义的指定类型的引用，并为该引用定义令牌。</span><span class="sxs-lookup"><span data-stu-id="f72f1-103">Creates a reference to the specified type that is defined outside the current scope, and defines a token for that reference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f72f1-104">语法</span><span class="sxs-lookup"><span data-stu-id="f72f1-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineImportType (
    [in]  IMetaDataAssemblyImport  *pAssemImport,
    [in]  const void               *pbHashValue,
    [in]  ULONG                    cbHashValue,
    [in]  IMetaDataImport          *pImport,
    [in]  mdTypeDef                tdImport,
    [in]  IMetaDataAssemblyEmit    *pAssemEmit,
    [out] mdTypeRef                *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f72f1-105">parameters</span><span class="sxs-lookup"><span data-stu-id="f72f1-105">Parameters</span></span>  
 `pAssemImport`  
 <span data-ttu-id="f72f1-106">[在][IMetaDataAssemblyImport 接口](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)，表示从中导入目标类型的程序集。</span><span class="sxs-lookup"><span data-stu-id="f72f1-106">[in] An [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface that represents the assembly from which the target type is imported.</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="f72f1-107">[在]包含 的数组，其中包含 由 指定的`pAssemImport`程序集的哈希值。</span><span class="sxs-lookup"><span data-stu-id="f72f1-107">[in] An array that contains the hash for the assembly specified by `pAssemImport`.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="f72f1-108">[in] `pbHashValue` 数组中的字节数。</span><span class="sxs-lookup"><span data-stu-id="f72f1-108">[in] The number of bytes in the `pbHashValue` array.</span></span>  
  
 `pImport`  
 <span data-ttu-id="f72f1-109">[在][IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)接口，表示从中导入目标类型的元数据范围。</span><span class="sxs-lookup"><span data-stu-id="f72f1-109">[in] An [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface that represents the metadata scope from which the target type is imported.</span></span>  
  
 `tdImport`  
 <span data-ttu-id="f72f1-110">[在]指定`mdTypeDef`目标类型的令牌。</span><span class="sxs-lookup"><span data-stu-id="f72f1-110">[in] An `mdTypeDef` token that specifies the target type.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="f72f1-111">[在][IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)接口，表示将目标类型导入到的程序集。</span><span class="sxs-lookup"><span data-stu-id="f72f1-111">[in] An [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md) interface that represents the assembly into which the target type is imported.</span></span>  
  
 `ptr`  
 <span data-ttu-id="f72f1-112">[出]类型`mdTypeRef`引用的当前作用域中定义的令牌。</span><span class="sxs-lookup"><span data-stu-id="f72f1-112">[out] The `mdTypeRef` token that is defined in the current scope for the type reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f72f1-113">备注</span><span class="sxs-lookup"><span data-stu-id="f72f1-113">Remarks</span></span>  
 <span data-ttu-id="f72f1-114">在调用[IMetaDataEmit：:DefineImportI成员](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md)方法之前，可以使用`DefineImportType`该方法为成员的父类或父接口在当前作用域中创建类型引用。</span><span class="sxs-lookup"><span data-stu-id="f72f1-114">Prior to calling the [IMetaDataEmit::DefineImportMember](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimportmember-method.md) method, you can use the `DefineImportType` method to create a type reference, in the current scope, for the member's parent class or parent interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f72f1-115">要求</span><span class="sxs-lookup"><span data-stu-id="f72f1-115">Requirements</span></span>  
 <span data-ttu-id="f72f1-116">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f72f1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f72f1-117">**标题：** 科尔赫</span><span class="sxs-lookup"><span data-stu-id="f72f1-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f72f1-118">**库：** 用作 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="f72f1-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f72f1-119">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f72f1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f72f1-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f72f1-120">See also</span></span>

- [<span data-ttu-id="f72f1-121">IMetaDataEmit Interface</span><span class="sxs-lookup"><span data-stu-id="f72f1-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f72f1-122">IMetaDataEmit2 Interface</span><span class="sxs-lookup"><span data-stu-id="f72f1-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
