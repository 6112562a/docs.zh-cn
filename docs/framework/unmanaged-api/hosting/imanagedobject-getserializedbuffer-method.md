---
title: IManagedObject::GetSerializedBuffer 方法
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a94891b91f6ac14469e18ed6840a083ce5e9d64d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516910"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a>IManagedObject::GetSerializedBuffer 方法
获取此托管对象的字符串表示形式。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
#### <a name="parameters"></a>参数  
 `pBSTR`  
 [out]指向为序列化的对象的字符串的指针。  
  
## <a name="remarks"></a>备注  
 `GetSerializedBuffer`方法序列化的对象，因此它可以封送到客户端。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅
- [IManagedObject 接口](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
