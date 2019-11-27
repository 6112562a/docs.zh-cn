---
title: IMetaDataImport::FindTypeDefByName 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeDefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeDefByName
helpviewer_keywords:
- FindTypeDefByName method [.NET Framework metadata]
- IMetaDataImport::FindTypeDefByName method [.NET Framework metadata]
ms.assetid: f4c2cd88-ac28-4bad-9ab1-2cf9d2de41e6
topic_type:
- apiref
ms.openlocfilehash: b1b1c557eea62cae6d2ad09303441e4635abc899
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437839"
---
# <a name="imetadataimportfindtypedefbyname-method"></a><span data-ttu-id="0aa9d-102">IMetaDataImport::FindTypeDefByName 方法</span><span class="sxs-lookup"><span data-stu-id="0aa9d-102">IMetaDataImport::FindTypeDefByName Method</span></span>
<span data-ttu-id="0aa9d-103">获取一个指针，该指针指向具有指定名称的 <xref:System.Type> 的 TypeDef 元数据标记。</span><span class="sxs-lookup"><span data-stu-id="0aa9d-103">Gets a pointer to the TypeDef metadata token for the <xref:System.Type> with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa9d-104">语法</span><span class="sxs-lookup"><span data-stu-id="0aa9d-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeDefByName  
   [in]  LPCWSTR       szTypeDef,  
   [in]  mdToken       tkEnclosingClass,  
   [out] mdTypeDef     *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0aa9d-105">参数</span><span class="sxs-lookup"><span data-stu-id="0aa9d-105">Parameters</span></span>  
 `szTypeDef`  
 <span data-ttu-id="0aa9d-106">中要为其获取 TypeDef 标记的类型的名称。</span><span class="sxs-lookup"><span data-stu-id="0aa9d-106">[in] The name of the type for which to get the TypeDef token.</span></span>  
  
 `tkEnclosingClass`  
 <span data-ttu-id="0aa9d-107">中表示封闭类的 TypeDef 或 TypeRef 标记。</span><span class="sxs-lookup"><span data-stu-id="0aa9d-107">[in] A TypeDef or TypeRef token representing the enclosing class.</span></span> <span data-ttu-id="0aa9d-108">如果要查找的类型不是嵌套类，请将此值设置为 NULL。</span><span class="sxs-lookup"><span data-stu-id="0aa9d-108">If the type to find is not a nested class, set this value to NULL.</span></span>  
  
 `ptd`  
 <span data-ttu-id="0aa9d-109">弄指向匹配的 TypeDef 标记的指针。</span><span class="sxs-lookup"><span data-stu-id="0aa9d-109">[out] A pointer to the matching TypeDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aa9d-110">要求</span><span class="sxs-lookup"><span data-stu-id="0aa9d-110">Requirements</span></span>  
 <span data-ttu-id="0aa9d-111">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0aa9d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aa9d-112">**标头：** Cor</span><span class="sxs-lookup"><span data-stu-id="0aa9d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0aa9d-113">**库：** 作为资源包括在 Mscoree.dll 中</span><span class="sxs-lookup"><span data-stu-id="0aa9d-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0aa9d-114">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aa9d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa9d-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0aa9d-115">See also</span></span>

- [<span data-ttu-id="0aa9d-116">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="0aa9d-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="0aa9d-117">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="0aa9d-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
