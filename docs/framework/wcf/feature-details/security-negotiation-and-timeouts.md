---
title: 安全协商和超时
ms.date: 03/30/2017
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
ms.openlocfilehash: dfabdb05c7658e3cf9eb5b325597360bbc0bb588
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/27/2018
ms.locfileid: "50037793"
---
# <a name="security-negotiation-and-timeouts"></a>安全协商和超时
当客户端和服务进行身份验证时，Windows Communication Foundation (WCF) 支持，对服务凭据协商身份验证的一部分的模式。 在这种情况下，客户端和服务之间将进行潜在多路交换，以便将服务凭据传播到客户端。 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> 属性控制多路交换需要多长时间才能完成。 但此超时仅在交换实际经过的时间超过单个请求响应的时间时才适用。 如果协商在一次往返中完成，则该超时不适用。  
  
## <a name="see-also"></a>请参阅  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [如何：设置最大时钟偏差](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)
