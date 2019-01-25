---
title: IValidator::Validate 方法
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03a8bf7e215794f4a2951fe4e2d54a791bda20e8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594052"
---
# <a name="ivalidatorvalidate-method"></a><span data-ttu-id="c17ea-102">IValidator::Validate 方法</span><span class="sxs-lookup"><span data-stu-id="c17ea-102">IValidator::Validate Method</span></span>
<span data-ttu-id="c17ea-103">验证指定的可移植可执行 (PE) 或 Microsoft 中间语言 (MSIL) 文件。</span><span class="sxs-lookup"><span data-stu-id="c17ea-103">Validates the specified portable executable (PE) or Microsoft intermediate language (MSIL) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c17ea-104">语法</span><span class="sxs-lookup"><span data-stu-id="c17ea-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c17ea-105">参数</span><span class="sxs-lookup"><span data-stu-id="c17ea-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="c17ea-106">[in]一个指向`IVEHandler`处理验证错误的实例。</span><span class="sxs-lookup"><span data-stu-id="c17ea-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="c17ea-107">[in]指向在其中加载的文件的应用程序域的指针。</span><span class="sxs-lookup"><span data-stu-id="c17ea-107">[in] A pointer to the application domain in which the file is loaded.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="c17ea-108">[in]按位组合[ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)值，指示应执行的验证。</span><span class="sxs-lookup"><span data-stu-id="c17ea-108">[in] A bitwise combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the validations that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="c17ea-109">[in]最大允许在退出验证之前的错误数。</span><span class="sxs-lookup"><span data-stu-id="c17ea-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="c17ea-110">[in]不使用。</span><span class="sxs-lookup"><span data-stu-id="c17ea-110">[in] Not used.</span></span>  
  
 `fileName`  
 <span data-ttu-id="c17ea-111">[in]一个字符串，指定要验证的文件的名称。</span><span class="sxs-lookup"><span data-stu-id="c17ea-111">[in] A string that specifies the name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="c17ea-112">[in]指向在其中存储文件的内存缓冲区的指针。</span><span class="sxs-lookup"><span data-stu-id="c17ea-112">[in] A pointer to the memory buffer in which the file is stored.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="c17ea-113">[in]以字节为单位，要验证的文件的大小。</span><span class="sxs-lookup"><span data-stu-id="c17ea-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c17ea-114">要求</span><span class="sxs-lookup"><span data-stu-id="c17ea-114">Requirements</span></span>  
 <span data-ttu-id="c17ea-115">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c17ea-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c17ea-116">**标头：** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="c17ea-116">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="c17ea-117">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="c17ea-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c17ea-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c17ea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c17ea-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="c17ea-119">See also</span></span>

