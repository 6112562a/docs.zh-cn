---
title: '&lt;超时&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: e39deeb251865b87eb7734e4447088ca2f221d1d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148326"
---
# <a name="lttimeoutsgt"></a>&lt;超时&gt;
表示一个配置元素，该元素指定允许服务主机打开或关闭的时间间隔。  
  
 \<system.ServiceModel>  
\<客户端 >  
\<终结点 >  
\<主机 >  
\<超时 >  
  
## <a name="syntax"></a>语法  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`closeTimeout`|一个 <xref:System.TimeSpan> 值，指定为关闭服务主机预留的时间间隔。|  
|`openTimeout`|一个 <xref:System.TimeSpan> 值，指定为打开或关闭服务主机预留的时间间隔。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<主机 >](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|一个指定服务主机设置的配置元素。|  
  
## <a name="see-also"></a>请参阅  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [承载](../../../../../docs/framework/wcf/feature-details/hosting.md)
