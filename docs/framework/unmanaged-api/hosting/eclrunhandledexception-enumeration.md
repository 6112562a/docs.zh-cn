---
title: EClrUnhandledException 枚举
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: 302db0d029b3811d151473323a7a60bd16a00ec1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131237"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="fd0b0-102">EClrUnhandledException 枚举</span><span class="sxs-lookup"><span data-stu-id="fd0b0-102">EClrUnhandledException Enumeration</span></span>
<span data-ttu-id="fd0b0-103">介绍用于管理用户代码中未经处理的异常的可用选项。</span><span class="sxs-lookup"><span data-stu-id="fd0b0-103">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd0b0-104">语法</span><span class="sxs-lookup"><span data-stu-id="fd0b0-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="fd0b0-105">Members</span><span class="sxs-lookup"><span data-stu-id="fd0b0-105">Members</span></span>  
  
|<span data-ttu-id="fd0b0-106">成员</span><span class="sxs-lookup"><span data-stu-id="fd0b0-106">Member</span></span>|<span data-ttu-id="fd0b0-107">描述</span><span class="sxs-lookup"><span data-stu-id="fd0b0-107">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="fd0b0-108">指定发生默认行为。</span><span class="sxs-lookup"><span data-stu-id="fd0b0-108">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="fd0b0-109">进程已被破坏。</span><span class="sxs-lookup"><span data-stu-id="fd0b0-109">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="fd0b0-110">指定公共语言运行时（CLR）忽略未经处理的异常，并允许主机确定任何进一步的操作。</span><span class="sxs-lookup"><span data-stu-id="fd0b0-110">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd0b0-111">备注</span><span class="sxs-lookup"><span data-stu-id="fd0b0-111">Remarks</span></span>  
 <span data-ttu-id="fd0b0-112">若要指定 CLR 的行为类似于早期版本，请使用 `eHostDeterminedPolicy` 成员。</span><span class="sxs-lookup"><span data-stu-id="fd0b0-112">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd0b0-113">要求</span><span class="sxs-lookup"><span data-stu-id="fd0b0-113">Requirements</span></span>  
 <span data-ttu-id="fd0b0-114">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd0b0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd0b0-115">**标头：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fd0b0-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd0b0-116">**库：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fd0b0-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd0b0-117">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd0b0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd0b0-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="fd0b0-118">See also</span></span>

- [<span data-ttu-id="fd0b0-119">EClrFailure 枚举</span><span class="sxs-lookup"><span data-stu-id="fd0b0-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="fd0b0-120">EClrOperation 枚举</span><span class="sxs-lookup"><span data-stu-id="fd0b0-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="fd0b0-121">ICLRPolicyManager 接口</span><span class="sxs-lookup"><span data-stu-id="fd0b0-121">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="fd0b0-122">SetUnhandledExceptionPolicy 方法</span><span class="sxs-lookup"><span data-stu-id="fd0b0-122">SetUnhandledExceptionPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="fd0b0-123">IHostPolicyManager 接口</span><span class="sxs-lookup"><span data-stu-id="fd0b0-123">IHostPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [<span data-ttu-id="fd0b0-124">承载枚举</span><span class="sxs-lookup"><span data-stu-id="fd0b0-124">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
