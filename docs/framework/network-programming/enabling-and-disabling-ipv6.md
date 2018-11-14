---
title: 启用和禁用 IPv6
ms.date: 03/30/2017
ms.assetid: 6408d3ef-c9ba-49d9-b15e-fe74bd3ef031
ms.openlocfilehash: 9dbbbbb522628de81be3d3d1382867de99c570d0
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2018
ms.locfileid: "50183082"
---
# <a name="enabling-and-disabling-ipv6"></a>启用和禁用 IPv6
若要使用 IPv6 协议，请确保当前运行的操作系统版本支持 IPv6，并确保正确配置了操作系统和网络类。  
  
## <a name="configuration-steps"></a>配置步骤  
 下表列出了各种配置  
  
|支持 IPv6 的操作系统？|支持 IPv6 的网络类？|描述|  
|-------------------------------------|---------------------------------------|-----------------|  
|否|否|可以分析 IPv6 地址。|  
|否|是|可以分析 IPv6 地址。|  
|是|否|使用未标记为过时的名称解析方法，可以分析并解析 IPv6 地址。|  
|是|是|使用所有方法（包含标记为过时的方法），可以分析并解析 IPv6 地址。|  
  
 请注意，要为 System.Net 命名空间中的所有类启用 IPv6 支持，必须修改计算机配置文件或应用程序的配置文件。 应用程序的配置文件优先于计算机配置文件。  
  
 有关如何修改计算机配置文件 machine.config 以启用 Ipv6 支持的示例，请参阅[如何：修改计算机配置文件以启用 IPv6 支持](../../../docs/framework/network-programming/how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)。 此外，请确保操作系统启用了 IPv6 支持。  
  
 .NET Framework 在配置文件中具有如下配置开关设置  
  
```xml  
<system.net>…  
    <settings>…  
        <ipv6 enabled="true"/>…  
    </settings>…  
</system.net>  
```  
  
 对于 .NET Framework 1.1 及更早版本，ipv6 enabled 配置开关的值指定 <xref:System.Net.Dns?displayProperty=nameWithType> 类的成员是否返回 IPv6 地址。  
  
 对于 .NET Framework 2.0 和更高版本，如果 Windows 支持 IPv6，则 <xref:System.Net.Dns?displayProperty=nameWithType> 类的成员（例如 <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> 方法）将返回含一个限制的 IPv6 地址。 DNS <xref:System.Net.Dns?displayProperty=nameWithType> 的已过时成员（例如，<xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> 方法）将读取并识别配置文件中 ipv6 enabled 设置的值。  
  
## <a name="see-also"></a>请参阅  
 [Internet 协议版本 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [套接字](../../../docs/framework/network-programming/sockets.md)  
 [网络设置架构](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<ipv6> 元素（网络设置）](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)
