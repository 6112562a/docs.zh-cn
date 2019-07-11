---
title: ICorProfilerInfo7::GetInMemorySymbolsLength 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03c70b97e7af9fdc76c579c5940e2436232f6bc2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748649"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7::GetInMemorySymbolsLength 方法
[仅在 .NET Framework 4.6.1 及更高版本中受支持]  
  
 返回内存中的符号流的长度。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a>参数  
 `moduleId`  
 [in]包含内存中流的模块标识符。  
  
 pCountSymbolBytes  
 [out]一个指向`DWORD`值，该值，方法返回时，包含以字节为单位的流的长度。  
  
## <a name="return-value"></a>返回值  
 该方法将返回`S_OK`如果内存流的长度就可以确定，即使它是零 (0)。  
  
 该方法返回`CORPROF_E_MODULE_IS_DYNAMIC`如果该方法使用创建<xref:System.Reflection.Emit?displayProperty=nameWithType>。  
  
## <a name="remarks"></a>备注  
 如果模块有内存中的符号，流的长度位于`pCountSymbolBytes`。 如果该模块没有内存中的符号， `*pCountSymbolBytes = 0`。  
  
> [!NOTE]
>  当前实现不支持 Reflection.Emit。 如果通过使用 Reflection.Emit 创建模块，该方法返回`CORPROF_E_MODULE_IS_DYNAMIC`。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerInfo7 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
