---
title: '&lt;compositeDuplex&gt;'
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: e00cc6f3214dc9a040a9b6170271b1f4188d1631
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601618"
---
# <a name="ltcompositeduplexgt"></a>&lt;compositeDuplex&gt;
定义绑定元素，客户端在必须公开一个终结点以使服务可以将消息发送回客户端时使用此元素。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<compositeDuplex>  
  
## <a name="syntax"></a>语法  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a>特性和元素  
 下列各节描述了特性、子元素和父元素。  
  
### <a name="attributes"></a>特性  
  
|特性|描述|  
|---------------|-----------------|  
|clientBaseAddress|一个在双工模式下设置反向通道地址的 URI。 服务使用该地址与客户端进行联系和建立连接。<br /><br /> 如果此属性未设置，默认地址"`full qualified name+default port\TemporaryIndigoAddress\guid`"生成。 默认值为 `null`。|  
  
### <a name="child-elements"></a>子元素  
 无  
  
### <a name="parent-elements"></a>父元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|定义自定义绑定的所有绑定功能。|  
  
## <a name="remarks"></a>备注  
 此配置元素与本身不允许进行双工通信的传输（例如，HTTP）一起使用。 与此相反，TCP 本身允许进行双工通信，并且不要求服务在将消息发送回客户端时使用此绑定元素。  
  
 客户端必须公开一个地址，以便服务进行联系和建立连接。 此客户端地址由 `clientBaseAddress` 属性提供。 请注意，如果用户未显式设置 ClientBaseAddress，则 Windows Communication Foundation (WCF) 将自动生成一个 ClientBaseAddress。  
  
## <a name="example"></a>示例  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a>请参阅
- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [绑定](../../../../../docs/framework/wcf/bindings.md)
- [扩展绑定](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [自定义绑定](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
