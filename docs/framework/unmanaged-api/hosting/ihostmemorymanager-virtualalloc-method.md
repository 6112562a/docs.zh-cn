---
title: IHostMemoryManager::VirtualAlloc 方法
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a0764cb212a95412a4dcf9455b7648ee863951e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767674"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="9b50c-102">IHostMemoryManager::VirtualAlloc 方法</span><span class="sxs-lookup"><span data-stu-id="9b50c-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="9b50c-103">充当相应的 Win32 函数的逻辑包装。</span><span class="sxs-lookup"><span data-stu-id="9b50c-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="9b50c-104">Win32 实现`VirtualAlloc`保留或提交的调用进程的虚拟地址空间中的页面区域。</span><span class="sxs-lookup"><span data-stu-id="9b50c-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b50c-105">语法</span><span class="sxs-lookup"><span data-stu-id="9b50c-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b50c-106">参数</span><span class="sxs-lookup"><span data-stu-id="9b50c-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="9b50c-107">[in]指向要分配的区域的起始地址的指针。</span><span class="sxs-lookup"><span data-stu-id="9b50c-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="9b50c-108">[in]以字节为单位的区域的大小。</span><span class="sxs-lookup"><span data-stu-id="9b50c-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="9b50c-109">[in]内存分配的类型。</span><span class="sxs-lookup"><span data-stu-id="9b50c-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="9b50c-110">[in]区域页，并将其分配的内存保护。</span><span class="sxs-lookup"><span data-stu-id="9b50c-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="9b50c-111">[in][EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md)值，该值指示发生分配失败的影响。</span><span class="sxs-lookup"><span data-stu-id="9b50c-111">[in] An [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="9b50c-112">[out]指向已分配的内存或如果无法满足请求，则为 null 的起始地址的指针。</span><span class="sxs-lookup"><span data-stu-id="9b50c-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b50c-113">返回值</span><span class="sxs-lookup"><span data-stu-id="9b50c-113">Return Value</span></span>  
  
|<span data-ttu-id="9b50c-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b50c-114">HRESULT</span></span>|<span data-ttu-id="9b50c-115">描述</span><span class="sxs-lookup"><span data-stu-id="9b50c-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b50c-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b50c-116">S_OK</span></span>|<span data-ttu-id="9b50c-117">`VirtualAlloc` 已成功返回。</span><span class="sxs-lookup"><span data-stu-id="9b50c-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="9b50c-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9b50c-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9b50c-119">公共语言运行时 (CLR) 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。</span><span class="sxs-lookup"><span data-stu-id="9b50c-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9b50c-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9b50c-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9b50c-121">呼叫已超时。</span><span class="sxs-lookup"><span data-stu-id="9b50c-121">The call timed out.</span></span>|  
|<span data-ttu-id="9b50c-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9b50c-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9b50c-123">调用方不拥有该锁。</span><span class="sxs-lookup"><span data-stu-id="9b50c-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9b50c-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9b50c-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9b50c-125">事件已取消时被阻塞的线程或纤程正在等待它。</span><span class="sxs-lookup"><span data-stu-id="9b50c-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9b50c-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9b50c-126">E_FAIL</span></span>|<span data-ttu-id="9b50c-127">发生未知的灾难性故障。</span><span class="sxs-lookup"><span data-stu-id="9b50c-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9b50c-128">如果某方法返回 E_FAIL，CLR 不再在进程内可用。</span><span class="sxs-lookup"><span data-stu-id="9b50c-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9b50c-129">对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。</span><span class="sxs-lookup"><span data-stu-id="9b50c-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9b50c-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="9b50c-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="9b50c-131">没有足够的内存已可用于完成分配请求</span><span class="sxs-lookup"><span data-stu-id="9b50c-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b50c-132">备注</span><span class="sxs-lookup"><span data-stu-id="9b50c-132">Remarks</span></span>  
 <span data-ttu-id="9b50c-133">在您的进程的地址空间中调用保留区域`VirtualAlloc`。</span><span class="sxs-lookup"><span data-stu-id="9b50c-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="9b50c-134">`pAddress`参数包含所需的内存块的起始地址。</span><span class="sxs-lookup"><span data-stu-id="9b50c-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="9b50c-135">此参数通常设置为 null。</span><span class="sxs-lookup"><span data-stu-id="9b50c-135">This parameter is typically set to null.</span></span> <span data-ttu-id="9b50c-136">操作系统将保留的可用地址范围供您的进程的记录。</span><span class="sxs-lookup"><span data-stu-id="9b50c-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="9b50c-137">一个`pAddress`的 null 值指示系统在任何它认为合适位置保留区域。</span><span class="sxs-lookup"><span data-stu-id="9b50c-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="9b50c-138">或者，您可以为内存块提供特定的起始地址。</span><span class="sxs-lookup"><span data-stu-id="9b50c-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="9b50c-139">在这两种情况下，输出参数`ppMem`作为指针返回到已分配的内存。</span><span class="sxs-lookup"><span data-stu-id="9b50c-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="9b50c-140">该函数本身返回的 HRESULT 值。</span><span class="sxs-lookup"><span data-stu-id="9b50c-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="9b50c-141">Win32`VirtualAlloc`函数没有`ppMem`参数，并改为返回指向已分配的内存的指针。</span><span class="sxs-lookup"><span data-stu-id="9b50c-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="9b50c-142">有关详细信息，请参阅 Windows 平台文档。</span><span class="sxs-lookup"><span data-stu-id="9b50c-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b50c-143">要求</span><span class="sxs-lookup"><span data-stu-id="9b50c-143">Requirements</span></span>  
 <span data-ttu-id="9b50c-144">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b50c-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b50c-145">**标头：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9b50c-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b50c-146">**库：** 包含为 MSCorEE.dll 中的资源</span><span class="sxs-lookup"><span data-stu-id="9b50c-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b50c-147">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b50c-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b50c-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="9b50c-148">See also</span></span>

- [<span data-ttu-id="9b50c-149">IHostMemoryManager 接口</span><span class="sxs-lookup"><span data-stu-id="9b50c-149">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
