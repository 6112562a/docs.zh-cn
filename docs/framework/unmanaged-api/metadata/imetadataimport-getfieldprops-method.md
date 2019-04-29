---
title: IMetaDataImport::GetFieldProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7f8cccf8d583645982eb37f6afcb553914679ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777749"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="ef729-102">IMetaDataImport::GetFieldProps 方法</span><span class="sxs-lookup"><span data-stu-id="ef729-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="ef729-103">获取与指定 FieldDef 标记引用的字段关联的元数据。</span><span class="sxs-lookup"><span data-stu-id="ef729-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef729-104">语法</span><span class="sxs-lookup"><span data-stu-id="ef729-104">Syntax</span></span>  
  
```  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef729-105">参数</span><span class="sxs-lookup"><span data-stu-id="ef729-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="ef729-106">[in]表示要获取关联的元数据的字段的 FieldDef 标记。</span><span class="sxs-lookup"><span data-stu-id="ef729-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="ef729-107">[out]指向表示字段所属的类类型的 TypeDef 标记的指针。</span><span class="sxs-lookup"><span data-stu-id="ef729-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="ef729-108">[out]字段的名称。</span><span class="sxs-lookup"><span data-stu-id="ef729-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="ef729-109">[in]在宽字符的缓冲区的大小*szField*。</span><span class="sxs-lookup"><span data-stu-id="ef729-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="ef729-110">[out]返回缓冲区的实际大小。</span><span class="sxs-lookup"><span data-stu-id="ef729-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="ef729-111">[out]与该字段的元数据关联的标志。</span><span class="sxs-lookup"><span data-stu-id="ef729-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="ef729-112">[in]指向描述字段的二进制元数据值的指针。</span><span class="sxs-lookup"><span data-stu-id="ef729-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="ef729-113">[out]以字节为单位的大小`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="ef729-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="ef729-114">[out]一个标志，指定该字段的值类型。</span><span class="sxs-lookup"><span data-stu-id="ef729-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="ef729-115">[out]字段的常量值。</span><span class="sxs-lookup"><span data-stu-id="ef729-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="ef729-116">[out]以字符为单位的大小`ppValue`，或如果不存在任何字符串则为零。</span><span class="sxs-lookup"><span data-stu-id="ef729-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef729-117">要求</span><span class="sxs-lookup"><span data-stu-id="ef729-117">Requirements</span></span>  
 <span data-ttu-id="ef729-118">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef729-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef729-119">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ef729-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef729-120">**库：** 包含为 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="ef729-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ef729-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef729-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef729-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="ef729-122">See also</span></span>

- [<span data-ttu-id="ef729-123">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="ef729-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ef729-124">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="ef729-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
