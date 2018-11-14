---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 907e764cf032e595c7aba455fd4808a640f68016
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194769"
---
# <a name="wsattracerecord"></a>WSAT_TraceRecord
WSAT_TraceRecord  
  
## <a name="syntax"></a>语法  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a>方法  
 WSAT_TraceRecord 类未定义任何方法。  
  
## <a name="properties"></a>属性  
 WSAT_TraceRecord 类具有以下属性：  
  
### <a name="activityid"></a>ActivityID  
 数据类型：object  
访问类型：只读  
  
 跟踪记录的活动 ID。  
  
### <a name="eventid"></a>事件 ID  
 数据类型：sint32  
访问类型：只读  
  
 跟踪记录的事件 ID。  
  
### <a name="tracerecord"></a>TraceRecord  
 数据类型：String  
访问类型：只读  
  
 跟踪记录  
  
## <a name="requirements"></a>要求  
  
|MOF|已在 Servicemodel.mof 中声明。|  
|---------|-----------------------------------|  
|命名空间|已在 root\ServiceModel 中定义|
