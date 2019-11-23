---
title: ICorProfilerInfo::GetAppDomainInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAppDomainInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetAppDomainInfo
helpviewer_keywords:
- ICorProfilerInfo::GetAppDomainInfo method [.NET Framework profiling]
- GetAppDomainInfo method [.NET Framework profiling]
ms.assetid: a6bf5a04-e03e-44f0-917a-96f6a6d3cc96
topic_type:
- apiref
ms.openlocfilehash: 8c13ce443037d706f9eba49760ba76f47c5a6538
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448170"
---
# <a name="icorprofilerinfogetappdomaininfo-method"></a><span data-ttu-id="d8dc3-102">ICorProfilerInfo::GetAppDomainInfo 方法</span><span class="sxs-lookup"><span data-stu-id="d8dc3-102">ICorProfilerInfo::GetAppDomainInfo Method</span></span>
<span data-ttu-id="d8dc3-103">接受应用程序域 ID。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-103">Accepts an application domain ID.</span></span> <span data-ttu-id="d8dc3-104">返回应用程序域名称和包含该域的进程的 ID。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-104">Returns an application domain name and the ID of the process that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8dc3-105">语法</span><span class="sxs-lookup"><span data-stu-id="d8dc3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainInfo(  
    [in]  AppDomainID appDomainId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] ProcessID   *pProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8dc3-106">参数</span><span class="sxs-lookup"><span data-stu-id="d8dc3-106">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="d8dc3-107">[in] 应用程序域的 ID。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-107">[in] The ID of the application domain.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d8dc3-108">[in] `szName` 返回缓冲区的长度（以字符为单位）。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d8dc3-109">[out] 指向应用程序域名称的总字符长度的指针。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-109">[out] A pointer to the total character length of the application domain name.</span></span>  
  
 `szName`  
 <span data-ttu-id="d8dc3-110">[out] 调用方提供的宽字符缓冲区。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="d8dc3-111">当方法返回时，`szName` 将包含整个或部分应用程序域名称。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-111">When the method returns, `szName` will contain the full or partial application domain name.</span></span>  
  
 `pProcessId`  
 <span data-ttu-id="d8dc3-112">[out] 指向包含应用程序域的进程的 ID 的指针。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-112">[out] A pointer to the ID of the process that contains the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8dc3-113">备注</span><span class="sxs-lookup"><span data-stu-id="d8dc3-113">Remarks</span></span>  
 <span data-ttu-id="d8dc3-114">此方法返回后，必须验证 `szName` 缓冲区是否足够大从而可包含应用程序域的完整名称。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the application domain.</span></span> <span data-ttu-id="d8dc3-115">为此，请比较 `pcchName` 指向的值和 `cchName` 参数的值。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="d8dc3-116">如果 `pcchName` 指向的值大于 `cchName`，请分配更大的 `szName` 缓冲区，并用新的、更大的大小更新 `cchName`，然后再次调用 `GetAppDomainInfo`。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAppDomainInfo` again.</span></span>  
  
 <span data-ttu-id="d8dc3-117">或者，可以先用长度为零的 `szName` 缓冲区调用 `GetAppDomainInfo` 以获取正确的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-117">Alternatively, you can first call `GetAppDomainInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d8dc3-118">然后，可将缓冲区大小设置为 `pcchName` 中返回的值，并再次调用 `GetAppDomainInfo`。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-118">You can then set the buffer size to the value returned in `pcchName` and call `GetAppDomainInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8dc3-119">要求</span><span class="sxs-lookup"><span data-stu-id="d8dc3-119">Requirements</span></span>  
 <span data-ttu-id="d8dc3-120">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d8dc3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8dc3-121">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8dc3-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8dc3-122">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8dc3-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8dc3-123">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8dc3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8dc3-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="d8dc3-124">See also</span></span>

- [<span data-ttu-id="d8dc3-125">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="d8dc3-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="d8dc3-126">Profiling 接口</span><span class="sxs-lookup"><span data-stu-id="d8dc3-126">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d8dc3-127">分析</span><span class="sxs-lookup"><span data-stu-id="d8dc3-127">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
