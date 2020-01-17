---
title: AJAX 集成和 JSON 支持
ms.date: 03/30/2017
helpviewer_keywords:
- AJAX integration and JSON support [WCF]
ms.assetid: 3851a8fc-d861-4ac1-873c-96af0343d3a7
ms.openlocfilehash: b2bcd1a677f4f2e329422abe202d4b365ad8dc28
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116645"
---
# <a name="ajax-integration-and-json-support"></a>AJAX 集成和 JSON 支持
Windows Communication Foundation （WCF）对 ASP.NET 异步 JavaScript 和 XML （AJAX）和 JavaScript 对象表示法（JSON）数据格式的支持允许 WCF 服务向 AJAX 客户端公开操作。 AJAX 客户端是运行 JavaScript 代码并使用 HTTP 请求访问这些 WCF 服务的网页。 本节中的主题提供有关此支持以及如何实现此支持的信息。  
  
 有关 ASP.NET AJAX 及其与 ASP.NET 2.0 的集成的详细信息，请参阅[ASP.NET Ajax 概述](https://docs.microsoft.com/previous-versions/aspnet/bb398874(v=vs.100))。  
  
## <a name="in-this-section"></a>本节内容  
 [为 ASP.NET AJAX 创建 WCF 服务](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 介绍如何通过以下方式向 AJAX 客户端公开 WCF 服务：添加适当的 AJAX 终结点：通过配置，或使用自定义的服务主机工厂生成自动配置 AJAX 终结点的服务主机。  
  
 [创建不使用 ASP.NET 的 WCF AJAX 服务](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)  
 介绍如何在不使用 ASP.NET 的情况下创建 WCF 服务。  
  
 [支持 JSON 和其他数据传输格式](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)  
 描述对通常用于与 ASP.NET AJAX 服务进行通信的 JSON 格式（替代 XML）的支持。  
  
 [如何：将支持 AJAX 的 ASP.NET Web 服务迁移到 WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)  
 介绍如何将启用了 AJAX 的 ASP.NET Web 服务迁移到 WCF Web 服务。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>
- [WCF Web HTTP 编程模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
