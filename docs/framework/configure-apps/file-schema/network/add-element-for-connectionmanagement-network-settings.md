---
title: '&lt;添加&gt;connectionManagement （网络设置） 的元素'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9f9b1b13c0a45d7a2e34a04b44f13be12947993f
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/16/2018
ms.locfileid: "49349025"
---
# <a name="ltaddgt-element-for-connectionmanagement-network-settings"></a>&lt;添加&gt;connectionManagement （网络设置） 的元素
将 IP 地址或 DNS 名称添加到连接管理列表。  
  
 \<configuration>  
\<system.net>  
\<connectionManagement >  
\<add>  
  
## <a name="syntax"></a>语法  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|**特性**|**说明**|  
|-------------------|---------------------|  
|`address`|描述 IP 地址或 DNS 名称的字符串。|  
|`maxconnection`|允许连接至服务器的最大连接数。 如果未提供，则默认为 2。|  
  
### <a name="child-elements"></a>子元素  
 无。  
  
### <a name="parent-elements"></a>父元素  
  
|**元素**|**说明**|  
|-----------------|---------------------|  
|[connectionManagement](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|指定到网络主机的最大连接数。|  
  
## <a name="remarks"></a>备注  
 `address` 特性的值应该是一个星号以指示所有连接，或为 `<schema>://<idn_hostname>[:<port>]` 格式的字符串。  
  
 如果传递到任何 HTTP API 的 URI 包含 Unicode，那么将使用 <xref:System.Uri.DnsSafeHost%2A> 内部转换名称，这可能会返回一个 punicode 字符串（行为取决于当前 IDN 配置）。  
  
## <a name="configuration-files"></a>配置文件  
 此元素可在应用程序配置文件或计算机配置文件 (Machine.config) 中使用。  
  
## <a name="example"></a>示例  
 下面的示例配置应用程序使用与服务器的四个连接`www.contoso.com`和两个连接到所有其他服务器。  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [网络设置架构](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
