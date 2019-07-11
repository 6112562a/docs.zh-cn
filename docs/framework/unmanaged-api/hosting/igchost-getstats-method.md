---
title: IGCHost::GetStats 方法
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3e374c03ca90c904cd4ef8a4585cb35ccf43cb43
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766525"
---
# <a name="igchostgetstats-method"></a>IGCHost::GetStats 方法
获取垃圾回收系统的当前状态的统计信息。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>参数  
 `pStats`  
 [in、 out]一个指向[COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)结构，其中包含垃圾回收系统的当前状态的统计信息。  
  
## <a name="remarks"></a>备注  
 统计信息可以由智能分配系统，用于帮助垃圾回收系统进行操作。 例如，分配系统可能会确定，请查看统计信息，它需要添加更多内存或强制回收后。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** GCHost.idl GCHost.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [IGCHost 接口](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
