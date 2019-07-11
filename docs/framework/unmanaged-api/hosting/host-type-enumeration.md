---
title: HOST_TYPE 枚举
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caf76fa7962de9392b06591777ac862aa548d20d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779555"
---
# <a name="hosttype-enumeration"></a>HOST_TYPE 枚举
包含指定的启动应用程序的宿主类型的值。  
  
## <a name="syntax"></a>语法  
  
```cpp  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a>成员  
  
|成员|描述|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|启动从 AppLaunch.exe 应用程序。<br /><br /> 对于部分受信任的应用程序中使用此值。|  
|`HOST_TYPE_CORFLAG`|直接启动应用程序。 也就是说，启动应用程序从其自己的.exe 文件。<br /><br /> 此值用于完全受信任的应用程序。|  
|`HOST_TYPE_DEFAULT`|HOST_TYPE_APPLAUNCH 相同。|  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** MSCorEE.dll  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [承载枚举](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
