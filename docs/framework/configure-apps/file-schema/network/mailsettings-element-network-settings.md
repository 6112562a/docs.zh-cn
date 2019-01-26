---
title: '&lt;mailSettings&gt;元素 （网络设置）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: 954755c7576e0ca4dd7946926c77e1e7e18055e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713949"
---
# <a name="ltmailsettingsgt-element-network-settings"></a>&lt;mailSettings&gt;元素 （网络设置）
配置邮件发送选项。  

\<configuration>  
\<system.net>  
\<mailSettings>  
  
## <a name="syntax"></a>语法  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
 无。  
  
### <a name="child-elements"></a>子元素  
  
|特性|描述|  
|---------------|-----------------|  
|[\<smtp > 元素 （网络设置）](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|配置简单邮件传输协议的选项。|  
  
### <a name="parent-elements"></a>父元素  
  
|**元素**|**说明**|  
|-----------------|---------------------|  
|[\<system.Net> 元素（网络设置）](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|包含指定 .NET Framework 如何连接到网络的设置。|  
  
## <a name="example"></a>示例  
 下面的示例指定适当的 SMTP 参数，以使用默认网络凭据发送电子邮件。  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>请参阅
- <xref:System.Net.Mail.SmtpClient>
- [网络设置架构](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
