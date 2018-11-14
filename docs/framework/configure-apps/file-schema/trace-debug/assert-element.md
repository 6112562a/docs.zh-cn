---
title: '&lt;断言&gt;元素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b15e569ff6e42298c0a1de02f77ab7c302c70d86
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192676"
---
# <a name="ltassertgt-element"></a>&lt;断言&gt;元素
指定调用 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法时是否显示消息框；另外指定要写入消息的文件的名称。  
  
 \<configuration>  
\<system.diagnostics >  
\<断言 >  
  
## <a name="syntax"></a>语法  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|`assertuienabled`|可选特性。<br /><br /> 指定是否显示消息框何时**Debug.Assert**方法的计算结果为**false**。|  
|`logfilename`|可选特性。<br /><br /> 指定要将消息写到如果的文件的名称**Debug.Assert**的计算结果为**false**。|  
  
## <a name="assertuienabled-attribute"></a>assertuienabled 属性  
  
|“值”|描述|  
|-----------|-----------------|  
|`true`|显示消息框。 这是默认设置。|  
|`false`|不显示消息框。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。|  
|`system.diagnostics`|指定用于收集、存储和路由消息的跟踪侦听器以及对跟踪开关设置的级别。|  
  
## <a name="remarks"></a>备注  
 在这两个属性 **\<assert >** 元素是可选的。 您可以禁用消息框，而无需指定要将消息写入的文件，也可以指定要写入消息时保留启用的消息框的文件。  
  
## <a name="example"></a>示例  
 下面的示例演示如何在调用时禁用显示消息框**Debug.Assert**并将消息写入`c:\log.txt`。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Diagnostics.Debug>  
 [跟踪和调试设置架构](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
