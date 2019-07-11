---
title: IHostMemoryManager::ReleasedVirtualAddressSpace 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.ReleasedVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5096eb1064485c02b599659cc9ae889e7151581c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767701"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="f5781-102">IHostMemoryManager::ReleasedVirtualAddressSpace 方法</span><span class="sxs-lookup"><span data-stu-id="f5781-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="f5781-103">通知主机公共语言运行时 (CLR) 已完成使用指定的内存。</span><span class="sxs-lookup"><span data-stu-id="f5781-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5781-104">语法</span><span class="sxs-lookup"><span data-stu-id="f5781-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5781-105">参数</span><span class="sxs-lookup"><span data-stu-id="f5781-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="f5781-106">[in]指向要释放的内存的起始地址的指针。</span><span class="sxs-lookup"><span data-stu-id="f5781-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5781-107">备注</span><span class="sxs-lookup"><span data-stu-id="f5781-107">Remarks</span></span>  
 <span data-ttu-id="f5781-108">`ReleasedVirtualAddressSpace`方法是回调方法，必须由主机应用程序的编写器实现。</span><span class="sxs-lookup"><span data-stu-id="f5781-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="f5781-109">它是由 CLR 进行调用。</span><span class="sxs-lookup"><span data-stu-id="f5781-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5781-110">要求</span><span class="sxs-lookup"><span data-stu-id="f5781-110">Requirements</span></span>  
 <span data-ttu-id="f5781-111">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5781-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5781-112">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5781-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5781-113">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="f5781-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5781-114">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5781-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5781-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="f5781-115">See also</span></span>

- [<span data-ttu-id="f5781-116">IHostMemoryManager 接口</span><span class="sxs-lookup"><span data-stu-id="f5781-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
