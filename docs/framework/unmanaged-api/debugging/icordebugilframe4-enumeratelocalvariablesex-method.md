---
title: ICorDebugILFrame4::EnumerateLocalVariablesEx 方法
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3deb497c3e842e25bcaa46a867dd61ea4a1c3804
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926824"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a>ICorDebugILFrame4::EnumerateLocalVariablesEx 方法
[仅在 .NET Framework 4.5.2 及更高版本中受支持]  
  
 获取帧中局部变量的枚举，并且（可选）包括在探查器 ReJIT 检测中添加的变量。  
  
## <a name="syntax"></a>语法  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,   
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>参数  
 `flags`  
 中一个[ILCodeKind](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)枚举成员，用于指定在探查器 ReJIT 检测中添加的变量是否包含在帧中。  
  
 `ppValueEnum`  
 弄一个指向 "ICorDebugValueEnum" 对象地址的指针，该对象是此帧中局部变量的枚举器。  
  
## <a name="remarks"></a>备注  
 此方法类似于[EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)方法，不同之处在于它可以访问在探查器 ReJIT 检测中添加的变量。 将`flags`设置`ILCODE_ORIGINAL_IL`为等效于调用[ICorDebugILFrame：： EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)。 将 `flags` 设置为 `ILCODE_REJIT_IL` 使调试器能够访问在探查器 ReJIT 检测中添加的局部变量。 如果未检测到中间语言 (IL)，则枚举为空且该方法将返回 `S_OK`。  
  
 由于某些局部变量可能未处于活动状态，因此枚举器可能不包括正在运行的方法中的所有局部变量。  
  
## <a name="requirements"></a>要求  
 **适用**请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** Cordebug.idl，Cordebug.idl  
  
 **类库**CorGuids.lib  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICorDebugILFrame4 接口](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [调试接口](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT操作方法指南](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
