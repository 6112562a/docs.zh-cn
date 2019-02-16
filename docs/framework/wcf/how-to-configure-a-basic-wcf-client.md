---
title: 如何：配置基本 Windows Communication Foundation 客户端
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], configuring
ms.assetid: d067b86d-afb0-47bf-94f6-45180a3d8d78
ms.openlocfilehash: 18acec48b2af78877f99335da38ccb0ae8942824
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332309"
---
# <a name="how-to-configure-a-basic-windows-communication-foundation-client"></a>如何：配置基本 Windows Communication Foundation 客户端

这是创建基本 Windows Communication Foundation (WCF) 应用程序所需的六项任务的第 5 个。 有关全部六项任务的概述，请参阅[入门教程](../../../docs/framework/wcf/getting-started-tutorial.md)主题。

本主题讨论使用生成的客户端配置文件**添加服务引用**Visual Studio 的功能或[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。 配置客户端包括指定客户端用于访问服务的终结点。 终结点有一个地址、 绑定和协定，并且必须配置客户端的过程中指定其中每项功能。

## <a name="configure-a-windows-communication-foundation-client"></a>配置 Windows Communication Foundation 客户端

从 GettingStartedClient 项目打开生成的配置文件 (App.config)。 下面的示例显示了生成的配置文件。 下[ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)部分中，找到[\<终结点 >](../configure-apps/file-schema/wcf/endpoint-element.md)元素。

```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
        <startup>
          <!-- specifies the version of WCF to use-->
            <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5,Profile=Client" />
        </startup>
        <system.serviceModel>
            <bindings>
                <!-- Uses wsHttpBinding-->
                <wsHttpBinding>
                    <binding name="WSHttpBinding_ICalculator" />
                </wsHttpBinding>
            </bindings>
            <client>
                <!-- specifies the endpoint to use when calling the service -->
                <endpoint address="http://localhost:8000/ServiceModelSamples/Service/CalculatorService"
                    binding="wsHttpBinding" bindingConfiguration="WSHttpBinding_ICalculator"
                    contract="ServiceReference1.ICalculator" name="WSHttpBinding_ICalculator">
                    <identity>
                        <userPrincipalName value="migree@redmond.corp.microsoft.com" />
                    </identity>
                </endpoint>
            </client>
        </system.serviceModel>
    </configuration>
```

此示例将配置客户端用于访问位于以下地址的服务的终结点： `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`。

该终结点元素指定 `ServiceReference1.ICalculator` 服务约定用于 WCF 客户端和服务之间的通信。 使用系统提供的 <xref:System.ServiceModel.WSHttpBinding> 配置 WCF 通道。 此约定使用生成**添加服务引用**Visual Studio 中。 它基本上是在 GettingStartedLib 项目中定义的约定的副本。 
  <xref:System.ServiceModel.WSHttpBinding> 绑定指定 HTTP 作为传输协议、可互操作安全性以及其他配置详细信息。

有关如何使用此配置中使用生成的客户端的详细信息，请参阅[如何：使用客户端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)。

## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [如何：使用 WCF 客户端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)

## <a name="see-also"></a>请参阅

- [使用绑定配置服务和客户端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [ServiceModel 元数据实用工具 (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [如何：创建客户端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [入门](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [自承载](../../../docs/framework/wcf/samples/self-host.md)