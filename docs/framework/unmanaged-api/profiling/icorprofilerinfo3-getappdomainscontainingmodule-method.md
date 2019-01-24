---
title: ICorProfilerInfo3::GetAppDomainsContainingModule 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 343834492776fdb09a68210fb80138ec2c588773
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54741147"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="1f6d6-102">ICorProfilerInfo3::GetAppDomainsContainingModule 方法</span><span class="sxs-lookup"><span data-stu-id="1f6d6-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="1f6d6-103">获取其中已加载给定模块的应用程序域的标识符。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f6d6-104">语法</span><span class="sxs-lookup"><span data-stu-id="1f6d6-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f6d6-105">参数</span><span class="sxs-lookup"><span data-stu-id="1f6d6-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="1f6d6-106">[in] 已加载模块的 ID。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="1f6d6-107">[in] `appDomainIds` 数组的大小。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="1f6d6-108">[out] 指向所返回元素总数的指针。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="1f6d6-109">[out] 应用程序域 ID 值的数组。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f6d6-110">备注</span><span class="sxs-lookup"><span data-stu-id="1f6d6-110">Remarks</span></span>  
 <span data-ttu-id="1f6d6-111">此方法使用调用方分配的缓冲区。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f6d6-112">要求</span><span class="sxs-lookup"><span data-stu-id="1f6d6-112">Requirements</span></span>  
 <span data-ttu-id="1f6d6-113">**平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1f6d6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f6d6-114">**标头：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1f6d6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1f6d6-115">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f6d6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f6d6-116">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f6d6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f6d6-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="1f6d6-117">See also</span></span>
- [<span data-ttu-id="1f6d6-118">ICorProfilerFunctionEnum 接口</span><span class="sxs-lookup"><span data-stu-id="1f6d6-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="1f6d6-119">ICorProfilerInfo3 接口</span><span class="sxs-lookup"><span data-stu-id="1f6d6-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="1f6d6-120">Profiling 接口</span><span class="sxs-lookup"><span data-stu-id="1f6d6-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="1f6d6-121">分析</span><span class="sxs-lookup"><span data-stu-id="1f6d6-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
