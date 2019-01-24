---
title: COR_PRF_HIGH_MONITOR 枚举
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24fde3901f4a866fb14461533a24f0ce265847ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600123"
---
# <a name="corprfhighmonitor-enumeration"></a><span data-ttu-id="923be-102">COR_PRF_HIGH_MONITOR 枚举</span><span class="sxs-lookup"><span data-stu-id="923be-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>
<span data-ttu-id="923be-103">[仅在 .NET Framework 4.5.2 及更高版本中受支持]</span><span class="sxs-lookup"><span data-stu-id="923be-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="923be-104">提供一些标志，除了中的那些[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)探查器可以为指定的枚举[ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法在加载时。</span><span class="sxs-lookup"><span data-stu-id="923be-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="923be-105">语法</span><span class="sxs-lookup"><span data-stu-id="923be-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,     
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,    
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="923be-106">成员</span><span class="sxs-lookup"><span data-stu-id="923be-106">Members</span></span>  
  
|<span data-ttu-id="923be-107">成员</span><span class="sxs-lookup"><span data-stu-id="923be-107">Member</span></span>|<span data-ttu-id="923be-108">描述</span><span class="sxs-lookup"><span data-stu-id="923be-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="923be-109">不设置任何标志。</span><span class="sxs-lookup"><span data-stu-id="923be-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="923be-110">控件[ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)在 CLR 程序集引用闭包审核期间添加程序集引用的回调。</span><span class="sxs-lookup"><span data-stu-id="923be-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="923be-111">控件[ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)回调的更新与内存中模块关联的符号流。</span><span class="sxs-lookup"><span data-stu-id="923be-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="923be-112">控件[ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md)回调，该值指示当动态方法已被垃圾收集和卸载。</span><span class="sxs-lookup"><span data-stu-id="923be-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|   
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="923be-113">表示需要配置增强的映像的所有 `COR_PRF_HIGH_MONITOR` 标志。</span><span class="sxs-lookup"><span data-stu-id="923be-113">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="923be-114">它对应于`COR_PRF_REQUIRE_PROFILE_IMAGE`中的标志[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)枚举。</span><span class="sxs-lookup"><span data-stu-id="923be-114">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="923be-115">表示可以在将探查器附加到运行中的应用之后进行设置的所有 `COR_PRF_HIGH_MONITOR` 标志。</span><span class="sxs-lookup"><span data-stu-id="923be-115">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="923be-116">表示只能在初始化过程中进行设置的所有 `COR_PRF_HIGH_MONITOR` 标志。</span><span class="sxs-lookup"><span data-stu-id="923be-116">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="923be-117">如果尝试从其他位置更改这些标志中的任何一个标志，则会产生一个指示失败的 `HRESULT` 值。</span><span class="sxs-lookup"><span data-stu-id="923be-117">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="923be-118">备注</span><span class="sxs-lookup"><span data-stu-id="923be-118">Remarks</span></span>  
 <span data-ttu-id="923be-119">`COR_PRF_HIGH_MONITOR`与使用标志`pdwEventsHigh`的参数[ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)并[ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="923be-119">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="923be-120">从开始[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)]，值`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`已从 0 到`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`(0x00000002)。</span><span class="sxs-lookup"><span data-stu-id="923be-120">Starting with the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="923be-121">从.NET Framework 4.7.2 开始，其值更改，不再`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`到`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`。</span><span class="sxs-lookup"><span data-stu-id="923be-121">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="923be-122">`COR_PRF_HIGH_MONITOR_IMMUTABLE` 旨在是表示只能在初始化期间设置的所有标志的位掩码。</span><span class="sxs-lookup"><span data-stu-id="923be-122">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="923be-123">尝试更改任何其他位置会导致失败的这些标志`HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="923be-123">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="923be-124">要求</span><span class="sxs-lookup"><span data-stu-id="923be-124">Requirements</span></span>  
 <span data-ttu-id="923be-125">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="923be-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="923be-126">**标头：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="923be-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="923be-127">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="923be-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="923be-128">**.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="923be-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="923be-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="923be-129">See also</span></span>
- [<span data-ttu-id="923be-130">分析枚举</span><span class="sxs-lookup"><span data-stu-id="923be-130">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [<span data-ttu-id="923be-131">COR_PRF_MONITOR 枚举</span><span class="sxs-lookup"><span data-stu-id="923be-131">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)
- [<span data-ttu-id="923be-132">ICorProfilerInfo5 接口</span><span class="sxs-lookup"><span data-stu-id="923be-132">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
