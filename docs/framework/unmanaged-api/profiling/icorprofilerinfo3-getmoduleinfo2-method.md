---
title: ICorProfilerInfo3::GetModuleInfo2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetModuleInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetModuleInfo2
helpviewer_keywords:
- ICorProfilerInfo3::GetModuleInfo2 method [.NET Framework profiling]
- GetModuleInfo2 method [.NET Framework profiling]
ms.assetid: f1f6b8f3-dcfc-49e8-be76-ea50ea90d5a7
topic_type:
- apiref
ms.openlocfilehash: e2a4df262e076c960640977bea0d22be19802140
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449667"
---
# <a name="icorprofilerinfo3getmoduleinfo2-method"></a>ICorProfilerInfo3::GetModuleInfo2 方法
若给定模块 ID，返回模块的文件名、模块父程序集的 ID 以及描述模块属性的位掩码。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetModuleInfo2(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, annotation("__out_ecount_part(cchName, *pcchName)")]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
    [out] DWORD                 *pdwModuleFlags);  
```  
  
## <a name="parameters"></a>参数  
 `moduleId`  
 [in] 将为其检索信息的模块的 ID。  
  
 `ppBaseLoadAddress`  
 [out] 加载模块的基址。  
  
 `cchName`  
 [in] `szName` 返回缓冲区的长度（以字符为单位）。  
  
 `pcchName`  
 [out] 指向返回的模块文件名总字符长度的指针。  
  
 `szName`  
 [out] 调用方提供的宽字符缓冲区。 方法返回后，此缓冲区包含模块的文件名。  
  
 `pAssemblyId`  
 [out] 指向模块的父程序集的 ID 的指针。  
  
 `pdwModuleFlags`  
 弄指定模块属性的[COR_PRF_MODULE_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)枚举中的值的位掩码。  
  
## <a name="remarks"></a>备注  
 对于动态模块，`szName` 参数是此模块的元数据名称，且基址为 0（零）。 元数据名称是元数据内模块表中名称列的值。 这也会作为 <xref:System.Reflection.Module.ScopeName%2A?displayProperty=nameWithType> 属性公开给托管代码，并作为非托管元数据客户端代码的[IMetaDataImport：： GetScopeProps](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-getscopeprops-method.md)方法的 `szName` 参数。  
  
 尽管只要存在模块的 ID，就可以调用 `GetModuleInfo2` 方法，但在探查器接收到[ICorProfilerCallback：： ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)回调之前，父程序集的 ID 将不可用。  
  
 返回 `GetModuleInfo2` 后，必须验证 `szName` 缓冲区的大小是否足够包含模块的完整文件名。 为此，请比较 `pcchName` 指向的值和 `cchName` 参数的值。 如果 `pcchName` 指向的值大于 `cchName`，请分配更大的 `szName` 缓冲区，并用新的、更大的大小更新 `cchName`，然后再次调用 `GetModuleInfo2`。  
  
 或者，可以先用长度为零的 `GetModuleInfo2` 缓冲区调用 `szName` 以获取正确的缓冲区大小。 然后，可将缓冲区大小设置为 `pcchName` 中返回的值，并再次调用 `GetModuleInfo2`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **头文件：** CorProf.idl、CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [ICorProfilerInfo 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Profiling 接口](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [分析](../../../../docs/framework/unmanaged-api/profiling/index.md)
