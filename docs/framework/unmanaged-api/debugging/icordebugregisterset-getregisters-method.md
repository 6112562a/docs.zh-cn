---
title: ICorDebugRegisterSet::GetRegisters 方法
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegisters
helpviewer_keywords:
- GetRegisters method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetRegisters method [.NET Framework debugging]
ms.assetid: fdf91864-48ea-4aa6-b70c-361b7a3184c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: daee6c46c247bcd21073f779cada8c843947a949
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747248"
---
# <a name="icordebugregistersetgetregisters-method"></a>ICorDebugRegisterSet::GetRegisters 方法
获取每个寄存器的值 （上当前正在执行代码的计算机） 指定的位掩码。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetRegisters (  
    [in] ULONG64       mask,   
    [in] ULONG32       regCount,  
    [out, size_is(regCount), length_is(regCount)]  
        CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="parameters"></a>参数  
 `mask`  
 [in]一个位掩码，它指定要从中检索值的哪一寄存器。 每位对应于寄存器。 如果有些设置为 1，则检索寄存器的值;否则，不会检索寄存器的值。  
  
 `regCount`  
 [in]要检索的注册值的数目。  
  
 `regBuffer`  
 [out]一个数组`CORDB_REGISTER`对象，其中每个接收寄存器的值。  
  
## <a name="remarks"></a>备注  
 数组的大小应等于的位数设置为一个位掩码中。 `regCount`参数指定将接收寄存器值的缓冲区中的元素数。 如果`regCount`值指示掩码的寄存器数太小，将从集合中截断的更高版本的带编号的寄存器。 如果`regCount`该值太大，而未使用`regBuffer`元素将保持不变。  
  
 如果位掩码指定寄存器不可用，`GetRegisters`返回为该寄存器不确定的值。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugRegisterSet 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
