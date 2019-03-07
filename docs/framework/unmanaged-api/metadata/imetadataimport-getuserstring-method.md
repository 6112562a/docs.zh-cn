---
title: IMetaDataImport::GetUserString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetUserString
helpviewer_keywords:
- IMetaDataImport::GetUserString method [.NET Framework metadata]
- GetUserString method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 0fd3bb47-58b5-4083-b241-b9719df7a285
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d610385cfbfcb6a625e0e1893f97525f6f5430c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500598"
---
# <a name="imetadataimportgetuserstring-method"></a><span data-ttu-id="186bc-102">IMetaDataImport::GetUserString 方法</span><span class="sxs-lookup"><span data-stu-id="186bc-102">IMetaDataImport::GetUserString Method</span></span>
<span data-ttu-id="186bc-103">获取指定元数据标记所表示的文字字符串。</span><span class="sxs-lookup"><span data-stu-id="186bc-103">Gets the literal string represented by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="186bc-104">语法</span><span class="sxs-lookup"><span data-stu-id="186bc-104">Syntax</span></span>  
  
```  
HRESULT GetUserString (  
   [in]   mdString    stk,  
   [out]  LPWSTR      szString,  
   [in]   ULONG       cchString,  
   [out]  ULONG       *pchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="186bc-105">参数</span><span class="sxs-lookup"><span data-stu-id="186bc-105">Parameters</span></span>  
 `stk`  
 <span data-ttu-id="186bc-106">[in]要返回的关联的字符串的字符串标记。</span><span class="sxs-lookup"><span data-stu-id="186bc-106">[in] The String token to return the associated string for.</span></span>  
  
 `szString`  
 <span data-ttu-id="186bc-107">[out]所需字符串的副本。</span><span class="sxs-lookup"><span data-stu-id="186bc-107">[out] A copy of the requested string.</span></span>  
  
 `cchString`  
 <span data-ttu-id="186bc-108">[in]以宽字符为单位的所请求的最大大小`szString`。</span><span class="sxs-lookup"><span data-stu-id="186bc-108">[in] The maximum size in wide characters of the requested `szString`.</span></span>  
  
 `pchString`  
 <span data-ttu-id="186bc-109">[out]以宽字符为单位返回大小`szString`。</span><span class="sxs-lookup"><span data-stu-id="186bc-109">[out] The size in wide characters of the returned `szString`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="186bc-110">要求</span><span class="sxs-lookup"><span data-stu-id="186bc-110">Requirements</span></span>  
 <span data-ttu-id="186bc-111">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="186bc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="186bc-112">**标头：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="186bc-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="186bc-113">**库：** 包含为 MsCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="186bc-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="186bc-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="186bc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="186bc-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="186bc-115">See also</span></span>
- [<span data-ttu-id="186bc-116">IMetaDataImport 接口</span><span class="sxs-lookup"><span data-stu-id="186bc-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="186bc-117">IMetaDataImport2 接口</span><span class="sxs-lookup"><span data-stu-id="186bc-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
