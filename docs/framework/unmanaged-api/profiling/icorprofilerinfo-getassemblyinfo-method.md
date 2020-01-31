---
title: ICorProfilerInfo::GetAssemblyInfo 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetAssemblyInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyInfo Method
helpviewer_keywords:
- GetAssemblyInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetAssemblyInfo method [.NET Framework profiling]
ms.assetid: 7a3c97c3-1e31-47b1-bf23-386785c509c4
topic_type:
- apiref
ms.openlocfilehash: 1e08d246136b33ffaaea91367d428e0bf2db99c1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864123"
---
# <a name="icorprofilerinfogetassemblyinfo-method"></a><span data-ttu-id="ffce8-102">ICorProfilerInfo::GetAssemblyInfo 方法</span><span class="sxs-lookup"><span data-stu-id="ffce8-102">ICorProfilerInfo::GetAssemblyInfo Method</span></span>
<span data-ttu-id="ffce8-103">接受程序集 ID，并返回此程序集的名称及其清单模块的 ID。</span><span class="sxs-lookup"><span data-stu-id="ffce8-103">Accepts an assembly ID, and returns the assembly's name and the ID of its manifest module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffce8-104">语法</span><span class="sxs-lookup"><span data-stu-id="ffce8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyInfo(  
    [in]  AssemblyID  assemblyId,  
    [in]  ULONG       cchName,  
    [out] ULONG       *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR       szName[] ,  
    [out] AppDomainID *pAppDomainId,  
    [out] ModuleID    *pModuleId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ffce8-105">参数</span><span class="sxs-lookup"><span data-stu-id="ffce8-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="ffce8-106">[in] 程序集的标识符。</span><span class="sxs-lookup"><span data-stu-id="ffce8-106">[in] The identifier of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ffce8-107">[in] `szName` 的长度（以字符为单位）。</span><span class="sxs-lookup"><span data-stu-id="ffce8-107">[in] The length, in characters, of `szName`.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ffce8-108">[out] 指向程序集名称的总字符长度的指针。</span><span class="sxs-lookup"><span data-stu-id="ffce8-108">[out] A pointer to the total character length of the assembly's name.</span></span>  
  
 `szName`  
 <span data-ttu-id="ffce8-109">[out] 调用方提供的宽字符缓冲区。</span><span class="sxs-lookup"><span data-stu-id="ffce8-109">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="ffce8-110">函数返回时将包含程序集名称。</span><span class="sxs-lookup"><span data-stu-id="ffce8-110">When the function returns, it will contain the assembly's name.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="ffce8-111">[out] 指向包含程序集的应用程序域 ID 的指针。</span><span class="sxs-lookup"><span data-stu-id="ffce8-111">[out] A pointer to the ID of the application domain that contains the assembly.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="ffce8-112">[out] 指向程序集的清单模块 ID 的指针。</span><span class="sxs-lookup"><span data-stu-id="ffce8-112">[out] A pointer to the ID of the assembly's manifest module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffce8-113">备注</span><span class="sxs-lookup"><span data-stu-id="ffce8-113">Remarks</span></span>  
 <span data-ttu-id="ffce8-114">此方法返回后，必须验证 `szName` 缓冲区大小是否足以包含程序集全名。</span><span class="sxs-lookup"><span data-stu-id="ffce8-114">After this method returns, you must verify that the `szName` buffer was large enough to contain the full name of the assembly.</span></span> <span data-ttu-id="ffce8-115">为此，请比较 `pcchName` 指向的值和 `cchName` 参数的值。</span><span class="sxs-lookup"><span data-stu-id="ffce8-115">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="ffce8-116">如果 `pcchName` 指向的值大于 `cchName`，请分配更大的 `szName` 缓冲区，并用新的、更大的大小更新 `cchName`，然后再次调用 `GetAssemblyInfo`。</span><span class="sxs-lookup"><span data-stu-id="ffce8-116">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetAssemblyInfo` again.</span></span>  
  
 <span data-ttu-id="ffce8-117">或者，可以先用长度为零的 `szName` 缓冲区调用 `GetAssemblyInfo` 以获取正确的缓冲区大小。</span><span class="sxs-lookup"><span data-stu-id="ffce8-117">Alternatively, you can first call `GetAssemblyInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="ffce8-118">然后可根据 `pcchName` 中返回的值调整缓冲区大小，并再次调用 `GetAssemblyInfo`。</span><span class="sxs-lookup"><span data-stu-id="ffce8-118">You can then adjust the buffer size based on the value returned in `pcchName` and call `GetAssemblyInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffce8-119">需求</span><span class="sxs-lookup"><span data-stu-id="ffce8-119">Requirements</span></span>  
 <span data-ttu-id="ffce8-120">**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ffce8-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffce8-121">**头文件：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ffce8-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ffce8-122">**库：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ffce8-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ffce8-123">**.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffce8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffce8-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ffce8-124">See also</span></span>

- [<span data-ttu-id="ffce8-125">ICorProfilerInfo 接口</span><span class="sxs-lookup"><span data-stu-id="ffce8-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="ffce8-126">Profiling 接口</span><span class="sxs-lookup"><span data-stu-id="ffce8-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ffce8-127">分析</span><span class="sxs-lookup"><span data-stu-id="ffce8-127">Profiling</span></span>](index.md)
