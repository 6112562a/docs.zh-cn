---
title: ICorPublishProcess::IsManaged 方法
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee3a0c27d350dec8e9f3e9448174d978c7d50e81
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775685"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="c9df9-102">ICorPublishProcess::IsManaged 方法</span><span class="sxs-lookup"><span data-stu-id="c9df9-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="c9df9-103">获取一个值，该值指示是否引用的进程这[ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)已知具有托管代码。</span><span class="sxs-lookup"><span data-stu-id="c9df9-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9df9-104">语法</span><span class="sxs-lookup"><span data-stu-id="c9df9-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9df9-105">参数</span><span class="sxs-lookup"><span data-stu-id="c9df9-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="c9df9-106">[out]指向一个布尔值，该值指示是否处理具有托管代码的指针。</span><span class="sxs-lookup"><span data-stu-id="c9df9-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="c9df9-107">值是`true`如果进程具有托管代码; 否则为`false`。</span><span class="sxs-lookup"><span data-stu-id="c9df9-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9df9-108">备注</span><span class="sxs-lookup"><span data-stu-id="c9df9-108">Remarks</span></span>  
 <span data-ttu-id="c9df9-109">由于当前版本的`ICorPublishProcess`仅允许访问具有托管代码中，进程`IsManaged`始终返回`true`。</span><span class="sxs-lookup"><span data-stu-id="c9df9-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9df9-110">要求</span><span class="sxs-lookup"><span data-stu-id="c9df9-110">Requirements</span></span>  
 <span data-ttu-id="c9df9-111">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9df9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9df9-112">**标头：** CorPub.idl CorPub.h</span><span class="sxs-lookup"><span data-stu-id="c9df9-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c9df9-113">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9df9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9df9-114">**.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9df9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9df9-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="c9df9-115">See also</span></span>

- [<span data-ttu-id="c9df9-116">ICorPublishProcess 接口</span><span class="sxs-lookup"><span data-stu-id="c9df9-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
