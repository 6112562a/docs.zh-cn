---
title: EBindPolicyLevels 枚举
ms.date: 03/30/2017
api_name:
- EBindPolicyLevels
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EBindPolicyLevels
helpviewer_keywords:
- EBindPolicyLevels enumeration [.NET Framework hosting]
ms.assetid: a9e00b4f-b6d0-4257-bd88-4fe9af97b8fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e61acbb15844c5ddfc8b7aa98c41bb18c6e9ade5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769758"
---
# <a name="ebindpolicylevels-enumeration"></a><span data-ttu-id="bc083-102">EBindPolicyLevels 枚举</span><span class="sxs-lookup"><span data-stu-id="bc083-102">EBindPolicyLevels Enumeration</span></span>
<span data-ttu-id="bc083-103">提供用于指定要应用或修改的程序集策略级别的标志。</span><span class="sxs-lookup"><span data-stu-id="bc083-103">Provides flags to specify the level at which to apply or modify assembly policy.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc083-104">语法</span><span class="sxs-lookup"><span data-stu-id="bc083-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    ePolicyLevelNone         = 0x0,  
    ePolicyLevelRetargetable = 0x1,  
    ePolicyUnifiedToCLR      = 0x2,  
    ePolicyLevelApp          = 0x4,  
    ePolicyLevelPublisher    = 0x8,  
    ePolicyLevelHost         = 0x10,  
    ePolicyLevelAdmin        = 0x20  
    ePolicyPortability       = 0x40  
} EBindPolicyLevels;  
```  
  
## <a name="members"></a><span data-ttu-id="bc083-105">成员</span><span class="sxs-lookup"><span data-stu-id="bc083-105">Members</span></span>  
  
|<span data-ttu-id="bc083-106">成员</span><span class="sxs-lookup"><span data-stu-id="bc083-106">Member</span></span>|<span data-ttu-id="bc083-107">描述</span><span class="sxs-lookup"><span data-stu-id="bc083-107">Description</span></span>|  
|------------|-----------------|  
|`ePolicyLevelAdmin`|<span data-ttu-id="bc083-108">指定应在管理员级别应用策略。</span><span class="sxs-lookup"><span data-stu-id="bc083-108">Specifies that policy should be applied at the administrator level.</span></span>|  
|`ePolicyLevelApp`|<span data-ttu-id="bc083-109">指定应在应用程序级别应用策略。</span><span class="sxs-lookup"><span data-stu-id="bc083-109">Specifies that policy should be applied at the application level.</span></span>|  
|`ePolicyLevelHost`|<span data-ttu-id="bc083-110">指定应在主机级别应用策略。</span><span class="sxs-lookup"><span data-stu-id="bc083-110">Specifies that policy should be applied at the host level.</span></span>|  
|`ePolicyLevelNone`|<span data-ttu-id="bc083-111">指定没有策略级别的标志。</span><span class="sxs-lookup"><span data-stu-id="bc083-111">Specifies no policy-level flags.</span></span>|  
|`ePolicyLevelPublisher`|<span data-ttu-id="bc083-112">指定应在发布服务器级别应用策略。</span><span class="sxs-lookup"><span data-stu-id="bc083-112">Specifies that policy should be applied at the publisher level.</span></span>|  
|`ePolicyLevelRetargetable`|<span data-ttu-id="bc083-113">指定策略应适用变量级别。</span><span class="sxs-lookup"><span data-stu-id="bc083-113">Specifies that policy should be applicable at variable levels.</span></span>|  
|`ePolicyPortability`|<span data-ttu-id="bc083-114">指定策略应支持的.NET Framework 程序集实现之间的可移植性。</span><span class="sxs-lookup"><span data-stu-id="bc083-114">Specifies that policy should support portability between implementations of a .NET Framework assembly.</span></span> <span data-ttu-id="bc083-115">请参阅[ \<supportPortability >](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)配置文件元素。</span><span class="sxs-lookup"><span data-stu-id="bc083-115">See the [\<supportPortability>](../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md) configuration file element.</span></span>|  
|`ePolicyUnifiedToCLR`|<span data-ttu-id="bc083-116">指定策略应统一到，公共语言运行时 (CLR)。</span><span class="sxs-lookup"><span data-stu-id="bc083-116">Specifies that policy should be unified to that of the common language runtime (CLR).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc083-117">备注</span><span class="sxs-lookup"><span data-stu-id="bc083-117">Remarks</span></span>  
 <span data-ttu-id="bc083-118">此枚举传递给方法的[ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)接口以在应用程序策略中指定的更改。</span><span class="sxs-lookup"><span data-stu-id="bc083-118">This enumeration is passed to methods of the [ICLRHostBindingPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) interface to specify changes in application policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc083-119">要求</span><span class="sxs-lookup"><span data-stu-id="bc083-119">Requirements</span></span>  
 <span data-ttu-id="bc083-120">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bc083-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc083-121">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bc083-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bc083-122">**库：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bc083-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc083-123">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc083-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc083-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="bc083-124">See also</span></span>

- [<span data-ttu-id="bc083-125">ICLRAssemblyIdentityManager 接口</span><span class="sxs-lookup"><span data-stu-id="bc083-125">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="bc083-126">承载枚举</span><span class="sxs-lookup"><span data-stu-id="bc083-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
