---
title: IAssemblyName::SetProperty 方法
ms.date: 03/30/2017
api_name:
- IAssemblyName.SetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::SetProperty
helpviewer_keywords:
- IAssemblyName::SetProperty method [.NET Framework fusion]
- SetProperty method [.NET Framework fusion]
ms.assetid: 496c3add-f60b-4073-943f-d1bcf33330cb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40953d03904e3268770c8a1b6e212873ec66d2dd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761844"
---
# <a name="iassemblynamesetproperty-method"></a><span data-ttu-id="be5bd-102">IAssemblyName::SetProperty 方法</span><span class="sxs-lookup"><span data-stu-id="be5bd-102">IAssemblyName::SetProperty Method</span></span>
<span data-ttu-id="be5bd-103">设置引用的指定的属性标识符的属性的值。</span><span class="sxs-lookup"><span data-stu-id="be5bd-103">Sets the value of the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be5bd-104">语法</span><span class="sxs-lookup"><span data-stu-id="be5bd-104">Syntax</span></span>  
  
```cpp  
HRESULT SetProperty (  
    [in] DWORD  PropertyId,  
    [in] LPVOID pvProperty,  
    [in] DWORD  cbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be5bd-105">参数</span><span class="sxs-lookup"><span data-stu-id="be5bd-105">Parameters</span></span>  
 `PropertyId`  
 <span data-ttu-id="be5bd-106">[in]将设置其值的属性的唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="be5bd-106">[in] The unique identifier of the property whose value will be set.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="be5bd-107">[in]要设置所引用的属性值`PropertyId`。</span><span class="sxs-lookup"><span data-stu-id="be5bd-107">[in] The value to which to set the property referenced by `PropertyId`.</span></span>  
  
 `cbProperty`  
 <span data-ttu-id="be5bd-108">[in]大小，以字节为单位的`pvProperty`。</span><span class="sxs-lookup"><span data-stu-id="be5bd-108">[in] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be5bd-109">要求</span><span class="sxs-lookup"><span data-stu-id="be5bd-109">Requirements</span></span>  
 <span data-ttu-id="be5bd-110">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="be5bd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be5bd-111">**标头：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="be5bd-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="be5bd-112">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be5bd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be5bd-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="be5bd-113">See also</span></span>

- [<span data-ttu-id="be5bd-114">IAssemblyName 接口</span><span class="sxs-lookup"><span data-stu-id="be5bd-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
