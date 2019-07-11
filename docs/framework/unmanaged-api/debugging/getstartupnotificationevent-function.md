---
title: GetStartupNotificationEvent 函数
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f67f3ef57b4996eb4a956c596b76fb94b1bdfd7a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738884"
---
# <a name="getstartupnotificationevent-function"></a>GetStartupNotificationEvent 函数
创建或打开一个事件句柄，由在指定目标进程中加载的公共语言运行时 (CLR) 对其发出信号。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a>参数  
 `debuggeePID`  
 [in] 从其中接收 CLR 启动通知的目标进程的进程标识符。  
  
 `phStartupEvent`  
 [out] 指向在启动时由 CLR 发出信号通知的句柄的指针。  
  
## <a name="return-value"></a>返回值  
 S_OK  
 成功获取启动通知事件的句柄。  
  
 E_INVALIDARG  
 `phStartupEvent` 为 null 或 `debuggeePID` 不引用当前正在运行的进程。  
  
 E_FAIL（或其他 E_ 返回代码）  
 无法获取启动通知事件的句柄。  
  
## <a name="remarks"></a>备注  
 在 Windows 操作系统上，`debuggeePID` 映射到 OS 进程标识符。  
  
 在发出信号通知事件的 CLR 执行任何托管代码之前，对该事件发出了信号。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** dbgshim.h  
  
 **库：** dbgshim.dll  
  
 **.NET framework 版本：** 3.5 SP1
