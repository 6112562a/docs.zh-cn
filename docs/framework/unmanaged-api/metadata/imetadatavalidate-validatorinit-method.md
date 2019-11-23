---
title: IMetaDataValidate::ValidatorInit 方法
ms.date: 03/30/2017
api_name:
- IMetaDataValidate.ValidatorInit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataValidate::ValidatorInit
helpviewer_keywords:
- IMetaDataValidate::ValidatorInit method [.NET Framework metadata]
- ValidatorInit method [.NET Framework metadata]
ms.assetid: 6bafd75a-e2d0-4aea-aed1-074374d5dff6
topic_type:
- apiref
ms.openlocfilehash: 165a57d8029fe03b9de3754fcf7c4db757292cec
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443598"
---
# <a name="imetadatavalidatevalidatorinit-method"></a><span data-ttu-id="94080-102">IMetaDataValidate::ValidatorInit 方法</span><span class="sxs-lookup"><span data-stu-id="94080-102">IMetaDataValidate::ValidatorInit Method</span></span>
<span data-ttu-id="94080-103">设置一个标志，该标志指定当前元数据范围内的模块类型，并注册验证错误的指定回调方法。</span><span class="sxs-lookup"><span data-stu-id="94080-103">Sets a flag that specifies the type of the module in the current metadata scope, and registers the specified callback method for validation errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94080-104">语法</span><span class="sxs-lookup"><span data-stu-id="94080-104">Syntax</span></span>  
  
```cpp  
HRESULT ValidatorInit (  
   [in] DWORD       dwModuleType,  
   [in] IUnknown    *pUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94080-105">参数</span><span class="sxs-lookup"><span data-stu-id="94080-105">Parameters</span></span>  
 `dwModule`  
 <span data-ttu-id="94080-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="94080-106">[in] A value of the [CorValidatorModuleType](../../../../docs/framework/unmanaged-api/metadata/corvalidatormoduletype-enumeration.md) enumeration that specifies the type of the module in the current metadata scope.</span></span>  
  
 `pUnk`  
 <span data-ttu-id="94080-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span><span class="sxs-lookup"><span data-stu-id="94080-107">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) instance that serves as a function callback for validation errors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94080-108">要求</span><span class="sxs-lookup"><span data-stu-id="94080-108">Requirements</span></span>  
 <span data-ttu-id="94080-109">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94080-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94080-110">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="94080-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94080-111">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="94080-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="94080-112">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94080-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94080-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="94080-113">See also</span></span>

- [<span data-ttu-id="94080-114">IMetaDataValidate 接口</span><span class="sxs-lookup"><span data-stu-id="94080-114">IMetaDataValidate Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatavalidate-interface.md)
