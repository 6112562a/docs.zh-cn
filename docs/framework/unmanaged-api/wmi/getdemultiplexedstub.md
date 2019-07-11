---
title: GetDemultiplexedStub 函数 （非托管 API 参考）
description: GetDemultiplexedStub 函数创建对象转发器接收器以帮助客户端在从 Windows 管理接收异步调用。
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b519ea4062682a56b5b4e277de22b14799f65d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783219"
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub 函数
创建对象转发器接收器，帮助客户端从 Windows Management 接收异步调用。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a>参数

`pObject`  
[in]客户端的过程中实现的指针[IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)。

`isLocal`  
[in]一个标志，指示事件是否是本地 (`true`); 否则为`false`。

`ppObject`  
[out]若要帮助在异步调用从 Windows 管理的客户端对象转发器接收器。

## <a name="return-value"></a>返回值

如果函数成功，返回值是`S_OK`(0)。

如果函数失败，返回值是一个非零错误代码。 若要获得扩展错误信息，请调用[GetErrorInfo](geterrorinfo.md)函数。
    
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** WMINet_Utils.idl  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>请参阅

- [WMI 和性能计数器 （非托管 API 参考）](index.md)
