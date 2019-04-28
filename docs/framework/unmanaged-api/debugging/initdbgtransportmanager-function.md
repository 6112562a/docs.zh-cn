---
title: InitDbgTransportManager 函数
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74cb2c7d1f79d23e1331cc7192ba2d6acfd9835c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761645"
---
# <a name="initdbgtransportmanager-function"></a>InitDbgTransportManager 函数
初始化传输管理器以连接到进程和运行时枚举的远程目标。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a>返回值  
 S_OK  
 成功。  
  
 E_OUTOFMEMORY  
 该函数不能为传输管理器分配内存。  
  
 E_FAIL（或其他 E_ 返回代码）  
 其他故障。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** CoreClrRemoteDebuggingInterfaces.h  
  
 **库：** mscordbi_macx86.dll  
  
 **.NET framework 版本：** 3.5 SP1
