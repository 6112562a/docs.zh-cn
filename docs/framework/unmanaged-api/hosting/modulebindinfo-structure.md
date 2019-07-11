---
title: ModuleBindInfo 结构
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e0e877402daf27c375aedddf8922e919a546ae5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781181"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="0d629-102">ModuleBindInfo 结构</span><span class="sxs-lookup"><span data-stu-id="0d629-102">ModuleBindInfo Structure</span></span>
<span data-ttu-id="0d629-103">提供有关引用的模块和包含它的程序集的详细的信息。</span><span class="sxs-lookup"><span data-stu-id="0d629-103">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d629-104">语法</span><span class="sxs-lookup"><span data-stu-id="0d629-104">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="0d629-105">成员</span><span class="sxs-lookup"><span data-stu-id="0d629-105">Members</span></span>  
  
|<span data-ttu-id="0d629-106">成员</span><span class="sxs-lookup"><span data-stu-id="0d629-106">Member</span></span>|<span data-ttu-id="0d629-107">描述</span><span class="sxs-lookup"><span data-stu-id="0d629-107">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="0d629-108">唯一标识符`IStream`对的调用返回[ihostassemblystore:: Providemodule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md)是要加载引用的模块的方法。</span><span class="sxs-lookup"><span data-stu-id="0d629-108">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="0d629-109">包含引用的模块的程序集唯一标识符。</span><span class="sxs-lookup"><span data-stu-id="0d629-109">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="0d629-110">引用的模块的名称。</span><span class="sxs-lookup"><span data-stu-id="0d629-110">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d629-111">备注</span><span class="sxs-lookup"><span data-stu-id="0d629-111">Remarks</span></span>  
 <span data-ttu-id="0d629-112">`ModuleBindInfo` 作为参数传递`IHostAssemblyStore::ProvideModule`。</span><span class="sxs-lookup"><span data-stu-id="0d629-112">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="0d629-113">主机提供的唯一标识符`dwAppDomainId`到公共语言运行时 (CLR)。</span><span class="sxs-lookup"><span data-stu-id="0d629-113">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="0d629-114">在调用[ihostassemblystore:: Provideassembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md)方法返回时，运行时使用标识符来确定是否的内容`IStream`已映射。</span><span class="sxs-lookup"><span data-stu-id="0d629-114">After a call to the [IHostAssemblyStore::ProvideAssembly](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="0d629-115">如果是这样，在运行时加载的现有副本，而不是无需重新映射该流。</span><span class="sxs-lookup"><span data-stu-id="0d629-115">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="0d629-116">运行时也使用此标识符作为从调用返回的流的查找键`IHostAssemblyStore::ProvideAssembly`方法。</span><span class="sxs-lookup"><span data-stu-id="0d629-116">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="0d629-117">因此，标识符必须是唯一的模块的请求与程序集请求。</span><span class="sxs-lookup"><span data-stu-id="0d629-117">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d629-118">要求</span><span class="sxs-lookup"><span data-stu-id="0d629-118">Requirements</span></span>  
 <span data-ttu-id="0d629-119">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d629-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d629-120">**标头：** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="0d629-120">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="0d629-121">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="0d629-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d629-122">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d629-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d629-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="0d629-123">See also</span></span>

- [<span data-ttu-id="0d629-124">承载结构</span><span class="sxs-lookup"><span data-stu-id="0d629-124">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="0d629-125">AssemblyBindInfo 结构</span><span class="sxs-lookup"><span data-stu-id="0d629-125">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)
- [<span data-ttu-id="0d629-126">ICLRAssemblyIdentityManager 接口</span><span class="sxs-lookup"><span data-stu-id="0d629-126">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="0d629-127">ICLRAssemblyReferenceList 接口</span><span class="sxs-lookup"><span data-stu-id="0d629-127">ICLRAssemblyReferenceList Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="0d629-128">IHostAssemblyManager 接口</span><span class="sxs-lookup"><span data-stu-id="0d629-128">IHostAssemblyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)
