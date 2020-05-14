---
title: IXCLRDataProcess：： EnumMethodInstanceByAddress 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: f3800a5980304394dd648111fe23a3bb0890c575
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395112"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a>IXCLRDataProcess：： EnumMethodInstanceByAddress 方法

枚举此进程的方法实例（从地址偏移量开始）。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>语法

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a>参数

`handle`\
中枚举方法实例的句柄。

`mod`\
弄枚举的方法实例。

## <a name="remarks"></a>备注

提供的方法是接口的一部分 `IXCLRDataProcess` ，并且对应于虚拟方法表的第29个槽。

## <a name="requirements"></a>要求

**平台：** 请参阅[系统要求](../../../../docs/framework/get-started/system-requirements.md)。
**标头：** 无**库：** 无 **.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>请参阅

- [CLRDataSourceType 枚举](clrdatasourcetype-enumeration.md)
- [调试](index.md)
- [IXCLRDataProcess 接口](ixclrdataprocess-interface.md)
