---
title: IMetaDataImport::GetMemberRefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fadc54d74ce6027bd021e148a14cb0c432eb41fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782345"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="f75c5-102">IMetaDataImport::GetMemberRefProps 方法</span><span class="sxs-lookup"><span data-stu-id="f75c5-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="f75c5-103">获取与指定标记引用的成员关联的元数据。</span><span class="sxs-lookup"><span data-stu-id="f75c5-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f75c5-104">语法</span><span class="sxs-lookup"><span data-stu-id="f75c5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,   
   [out] mdToken           *ptk,   
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pbSig   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f75c5-105">参数</span><span class="sxs-lookup"><span data-stu-id="f75c5-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="f75c5-106">[in]要返回关联的元数据的 MemberRef 标记。</span><span class="sxs-lookup"><span data-stu-id="f75c5-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="f75c5-107">[out]表示声明该成员或表示声明该成员或表示成员 MethodDef 的模块类的 ModuleRef 标记的类的 TypeDef 或 TypeRef 或 TypeSpec 标记。</span><span class="sxs-lookup"><span data-stu-id="f75c5-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="f75c5-108">[out]一个成员的名称的字符串缓冲区。</span><span class="sxs-lookup"><span data-stu-id="f75c5-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="f75c5-109">[in]请求的大小以宽字符为单位`szMember`。</span><span class="sxs-lookup"><span data-stu-id="f75c5-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="f75c5-110">[out]在宽字符为单位返回的大小`szMember`。</span><span class="sxs-lookup"><span data-stu-id="f75c5-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="f75c5-111">[out]指向成员的二进制元数据签名的指针。</span><span class="sxs-lookup"><span data-stu-id="f75c5-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="f75c5-112">[out]以字节为单位的大小`ppvSigBlob`。</span><span class="sxs-lookup"><span data-stu-id="f75c5-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f75c5-113">要求</span><span class="sxs-lookup"><span data-stu-id="f75c5-113">Requirements</span></span>  
 <span data-ttu-id="f75c5-114">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f75c5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f75c5-115">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f75c5-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f75c5-116">**库：** 包含为 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="f75c5-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f75c5-117">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f75c5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f75c5-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="f75c5-118">See also</span></span>

- [<span data-ttu-id="f75c5-119">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="f75c5-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f75c5-120">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="f75c5-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
