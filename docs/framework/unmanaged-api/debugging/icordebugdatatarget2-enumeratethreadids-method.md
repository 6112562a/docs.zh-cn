---
title: ICorDebugDataTarget2::EnumerateThreadIDs 方法
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 4a65b76f384cdad68cba75af524dbe672c309624
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976481"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a>ICorDebugDataTarget2::EnumerateThreadIDs 方法
返回一组活动线程 ID。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a>参数  
 cThreadID  
 [输入] 线程 ID 可返回的上限数。  
  
 pcThreadID  
 [输出] `ULONG32` 指针显示写入 `pThreadIds` 阵列的线程 ID 的实际数目。  
  
 pThreadID  
 一组线程标识符。  
  
## <a name="remarks"></a>备注  
  
> [!NOTE]
> 此方法仅适用于 .NET Native。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。**标头：** Cordebug.idl，Cordebug.idl  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>另请参阅

- [“ICor调试数据目标2”接口](icordebugdatatarget2-interface.md)
- [调试接口](debugging-interfaces.md)
