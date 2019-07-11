---
title: ICLRDebugManager::EndConnection 方法
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fc9d32f83b4b6384e28f012b9329ea18913a1218
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773159"
---
# <a name="iclrdebugmanagerendconnection-method"></a>ICLRDebugManager::EndConnection 方法
删除任务列表和标识符和友好名称之间的关联。  
  
## <a name="syntax"></a>语法  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a>参数  
 `dwConnectionId`  
 [in]连接和关联的公共语言运行时 (CLR) 任务列表的特定于宿主的标识符。  
  
## <a name="return-value"></a>返回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`EndConnection` 已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未加载到进程中，或处于不能运行托管的代码或已成功处理调用的状态。|  
|HOST_E_TIMEOUT|呼叫已超时。|  
|HOST_E_NOT_OWNER|调用方不拥有该锁。|  
|HOST_E_ABANDONED|事件已取消时被阻塞的线程或纤程正在等待它。|  
|E_FAIL|发生未知的灾难性故障。 方法返回 E_FAIL 后，CLR 不再在进程中使用。 对托管方法的后续调用返回 HOST_E_CLRNOTAVAILABLE。|  
|E_INVALIDARG|[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)永远不会使用调用`dwConnectionId`，或`dwConnectionId`为零。|  
  
## <a name="remarks"></a>备注  
 [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)提供三种方法， `BeginConnection`， [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)，和`EndConnection`，用于将任务列表相关联的标识符和友好名称。  
  
> [!IMPORTANT]
>  必须为每个组的任务特定的顺序调用这三种方法。 `BeginConnection` 首先调用来建立新连接。 `SetConnectionTasks` 将调用下一步来提供要与该连接相关联的任务组。 `EndConnection` 最后调用以删除任务列表的标识符和友好名称之间的关联。但是，可以嵌套调用不同的连接。  
  
## <a name="requirements"></a>要求  
 **平台：** 请参阅[系统需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **标头：** MSCorEE.h  
  
 **库：** 包含为 MSCorEE.dll 中的资源  
  
 **.NET Framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>请参阅

- [ICLRControl 接口](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRDebugManager 接口](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [BeginConnection 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)
- [SetConnectionTasks 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [IHostControl 接口](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
