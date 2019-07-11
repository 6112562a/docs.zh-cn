---
title: ICorDebugEval::NewArray 方法
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9597d05e46c2d41ab1f24a073c028561e944fb59
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753027"
---
# <a name="icordebugevalnewarray-method"></a>ICorDebugEval::NewArray 方法
分配的指定的元素类型和维度的一个新数组。  
  
 此方法是在.NET Framework 2.0 版中已过时。 使用[ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)相反。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a>参数  
 `elementType`  
 [in]CorElementType 枚举，用于指定数组的元素类型的值。  
  
 `pElementClass`  
 [in]指向一个指定的元素的类的 ICorDebugClass 对象的指针。 此值可能为 null 的基元类型的元素类型时。  
  
 `rank`  
 [in]数组的维度数。 在.NET Framework 2.0 中，此值必须为 1。  
  
 `dims`  
 [in]以字节为单位，每个维度的数组大小。  
  
 `lowBounds`  
 [in] 可选。 数组的每个维度的下限。 如果省略此值，下限为零则假定为每个维度。  
  
## <a name="remarks"></a>备注  
 始终在线程当前执行的应用程序域中创建数组。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CorDebug.idl、 CorDebug.h  
  
 **库：** CorGuids.lib  
  
 **.NET framework 版本：** 1.1, 1.0
