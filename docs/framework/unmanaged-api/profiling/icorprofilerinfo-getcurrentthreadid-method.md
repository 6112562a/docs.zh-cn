---
title: ICorProfilerInfo::GetCurrentThreadID 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db5ed871734205d59c602cc8b5c0cc9e8ac4682a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762869"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a>ICorProfilerInfo::GetCurrentThreadID 方法
如果它是一个托管的线程，请获取当前线程的 ID。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a>参数  
 `pThreadId`  
 [out]指向返回的托管线程 ID 的指针。  
  
## <a name="remarks"></a>备注  
 如果当前线程是一个内部运行时线程或其他非托管的线程`GetCurrentThreadID`HRESULT，并返回的值的形式返回 CORPROF_E_NOT_MANAGED_THREAD`pThreadId`参数为 null。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorProf.idl, CorProf.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorProfilerInfo 接口](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
