---
title: StackOverflowType 枚举
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44d5b7fdb2908678671505649bb906c0c5f740e3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751132"
---
# <a name="stackoverflowtype-enumeration"></a>StackOverflowType 枚举
包含堆栈溢出事件的根本原因的值。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`SO_ClrEngine`|由执行引擎引发堆栈溢出。|  
|`SO_Managed`|由托管代码导致堆栈溢出。|  
|`SO_Other`|由非托管代码导致堆栈溢出。|  
  
## <a name="remarks"></a>备注  
 此信息传递到主机上，通过调用[iactiononclrevent:: Onevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)方法。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** MSCorEE.dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [承载枚举](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
