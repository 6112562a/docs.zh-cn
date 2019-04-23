---
title: EInitializeNewDomainFlags 枚举
ms.date: 03/30/2017
api_name:
- EInitializeNewDomainFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EInitializeNewDomainFlags
helpviewer_keywords:
- EInitializeNewDomainFlags enumeration [.NET Framework hosting]
ms.assetid: 3a120ab2-f5ef-4c9b-8595-d3ed7247c342
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04b0d9989d66888c33de0359e4c93529fcfbf8d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59095355"
---
# <a name="einitializenewdomainflags-enumeration"></a><span data-ttu-id="03a99-102">EInitializeNewDomainFlags 枚举</span><span class="sxs-lookup"><span data-stu-id="03a99-102">EInitializeNewDomainFlags Enumeration</span></span>
<span data-ttu-id="03a99-103">使宿主能够在运行时提供的应用程序域初始化信息。</span><span class="sxs-lookup"><span data-stu-id="03a99-103">Enables the host to provide the runtime with information about the initialization of an application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03a99-104">语法</span><span class="sxs-lookup"><span data-stu-id="03a99-104">Syntax</span></span>  
  
```  
typedef enum {  
    eInitializeNewDomainFlags_None              = 0x0000,  
    eInitializeNewDomainFlags_NoSecurityChanges = 0x0002  
} EInitializeNewDomainFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="03a99-105">成员</span><span class="sxs-lookup"><span data-stu-id="03a99-105">Members</span></span>  
  
|<span data-ttu-id="03a99-106">成员</span><span class="sxs-lookup"><span data-stu-id="03a99-106">Member</span></span>|<span data-ttu-id="03a99-107">描述</span><span class="sxs-lookup"><span data-stu-id="03a99-107">Description</span></span>|  
|------------|-----------------|  
|`eInitializeNewDomainFlags_None`|<span data-ttu-id="03a99-108">无标志。</span><span class="sxs-lookup"><span data-stu-id="03a99-108">No flags.</span></span>|  
|`eInitializeNewDomainFlags_NoSecurityChanges`|<span data-ttu-id="03a99-109">通知公共语言运行时 (CLR) 主机中的应用程序域的安全状态将不进行更改<xref:System.AppDomainManager.InitializeNewDomain%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="03a99-109">Informs the common language runtime (CLR) that the host will not make changes to the security state of the application domain in the <xref:System.AppDomainManager.InitializeNewDomain%2A> method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03a99-110">备注</span><span class="sxs-lookup"><span data-stu-id="03a99-110">Remarks</span></span>  
 <span data-ttu-id="03a99-111">[Iclrdomainmanager:: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)方法采用一个参数类型`EInitializeNewDomainFlags`。</span><span class="sxs-lookup"><span data-stu-id="03a99-111">The [ICLRDomainManager::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md) method takes a parameter of type `EInitializeNewDomainFlags`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03a99-112">要求</span><span class="sxs-lookup"><span data-stu-id="03a99-112">Requirements</span></span>  
 <span data-ttu-id="03a99-113">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03a99-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03a99-114">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="03a99-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03a99-115">**库：** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03a99-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03a99-116">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03a99-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a99-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="03a99-117">See also</span></span>

- [<span data-ttu-id="03a99-118">承载枚举</span><span class="sxs-lookup"><span data-stu-id="03a99-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="03a99-119">SetAppDomainManagerType 方法</span><span class="sxs-lookup"><span data-stu-id="03a99-119">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)
