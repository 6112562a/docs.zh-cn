---
title: GetDemultiplexedStub 函数（非托管 API 参考）
description: GetDemultiplexedStub 函数创建对象转发器接收器，以帮助客户端接收来自 Windows 管理的异步调用。
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
ms.openlocfilehash: 9cc028b3300b43f8a0fb3e29f8b5ac6e1817b8c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127468"
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
中一个指针，指向客户端的[IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)的进程内实现。

`isLocal`  
中指示事件是否为本地事件的标志（`true`）;否则，`false`。

`ppObject`  
弄用于帮助客户端从 Windows 管理接收异步调用的对象转发器接收器。

## <a name="return-value"></a>返回值

如果该函数成功，则返回值为 `S_OK` （0）。

如果函数失败，则返回值为非零错误代码。 若要获取扩展的错误信息，请调用[GetErrorInfo](geterrorinfo.md)函数。
    
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统要求](../../get-started/system-requirements.md)。  
  
 **标头：** WMINet_Utils .idl  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>请参阅

- [WMI 和性能计数器（非托管 API 参考）](index.md)
