---
title: <gcServer> 元素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19ebad32ad8c7018b910a3d230f43031008dcdc7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927386"
---
# <a name="gcserver-element"></a>\<r > 元素
指定公共语言运行时是否运行服务器垃圾回收。  
  
 \<configuration>  
\<运行时 >  
\<gcServer>  
  
## <a name="syntax"></a>语法  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`enabled`|必需的特性。<br /><br /> 指定运行时是否运行服务器垃圾回收。|  
  
## <a name="enabled-attribute"></a>enabled 特性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|请勿运行服务器垃圾回收。 这是默认设置。|  
|`true`|运行服务器垃圾回收。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`runtime`|包含有关程序集绑定和垃圾回收的信息。|  
  
## <a name="remarks"></a>备注  
 公共语言运行时 (CLR) 支持两种类型的垃圾回收：工作站垃圾回收（适用于所有系统）和服务器垃圾回收（适用于多处理器系统）。 使用 `<gcServer>` 元素以控制 CLR 执行的垃圾回收类型。 使用 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> 属性以确定是否启用服务器垃圾回收。  
  
 对于单处理器计算机，默认的工作站垃圾回收应该是最快捷的选项。 对于双处理器计算机，最快捷的选项既可以是工作站垃圾回收又可以是服务器垃圾回收。 对于两个以上处理器的计算机，服务器垃圾回收应该是最快捷的选项。  
  
 此元素只能在应用程序配置文件中使用；如果此元素在计算机配置文件中，请忽略。  
  
> [!NOTE]
> 在 .NET Framework 4 和更低版本中，启用服务器垃圾回收之后，并发垃圾回收不可用。 从 .NET Framework 4.5 开始，服务器垃圾回收将并发执行。 若要使用非并发服务器垃圾回收, 请将`<gcServer>`元素设置`true`为, 并[ \<将 t > 元素](gcconcurrent-element.md)设置为`false`。  
  
## <a name="example"></a>示例  
 下面的示例启用服务器垃圾回收。  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [运行时设置架构](index.md)
- [配置文件架构](../index.md)
- [禁用并发垃圾回收](gcconcurrent-element.md#to-disable-background-garbage-collection)
