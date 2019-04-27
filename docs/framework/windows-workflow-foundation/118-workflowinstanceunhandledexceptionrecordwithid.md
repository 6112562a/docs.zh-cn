---
title: 118 - WorkflowInstanceUnhandledExceptionRecordWithId
ms.date: 03/30/2017
ms.assetid: 2ce4b193-e141-4cc4-86a3-2e8c984c110d
ms.openlocfilehash: eb69fc4760cd89294e24680b5aab83fcd058feb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009872"
---
# <a name="118---workflowinstanceunhandledexceptionrecordwithid"></a>118 - WorkflowInstanceUnhandledExceptionRecordWithId
## <a name="properties"></a>属性  
  
|||  
|-|-|  
|Id|118|  
|关键字|HealthMonitoring、WFTracking|  
|级别|Error|  
|通道|Microsoft-Windows-应用程序服务器-应用程序/分析|  
  
## <a name="description"></a>描述  
 当工作流实例发出 WorkflowInstanceUnhandledExceptionRecord 时，ETW 跟踪参与者将发出此事件。  
  
## <a name="message"></a>消息  
 TrackRecord = WorkflowInstanceUnhandledExceptionRecord，InstanceID = %1，RecordNumber = %2，EventTime = %3，ActivityDefinitionId = %4，SourceName = %5，SourceId = %6，SourceInstanceId = %7，SourceTypeName = %8，异常 = %9，批注 = %10，ProfileName =%11，WorkflowDefinitionIdentity = %12  
  
## <a name="details"></a>详细信息  
  
|数据项名称|数据项类型|描述|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|工作流的实例 ID|  
|RecordNumber|xs:long|发出的记录的序列号|  
|EventTime|xs:dateTime|发出该事件时的 UTC 时间|  
|ActivityDefinitionId|xs:string|工作流中根活动的名称|  
|SourceName|xs:string|导致 unhandledException 的出错源活动的名称|  
|SourceId|xs:string|出错源活动的活动 ID|  
|SourceInstanceId|xs:string|出错源活动的活动实例 ID|  
|SourceTypeName|xs:string|导致 unhandledException 的出错源活动类型名称|  
|例外|xs:string|未经处理的异常的异常详细信息|  
|状态|xs:string|工作流的当前状态。|  
|批注|xs:string|已添加到此事件中的批注。 值存储在一个 xml 元素中的格式\<项 >\<项名称 ="annotationName"type="System.String"> annotationValue\</i > \< /i t e >。 如果不指定任何批注，则该字符串包含\<项 / >。 ETW 事件大小受到 ETW 缓冲区大小或 ETW 事件最大负载的限制。 如果事件大小超出 ETW 限制，则通过丢弃批注并将替换为批注值来截断事件\<项 >... \< /i t e >。|  
|ProfileName|xs:string|导致发出此事件的跟踪配置文件的名称|  
|WorkflowDefinitionIdentity|xs:string|工作流定义 ID|  
|应用程序域|xs:string|由 AppDomain.CurrentDomain.FriendlyName 返回的字符串。|
