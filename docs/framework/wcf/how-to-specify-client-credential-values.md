---
title: 如何：指定客户端凭据值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 2417c2dd16224d6cbf00d3f1f4a8958420830b6c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319865"
---
# <a name="how-to-specify-client-credential-values"></a>如何：指定客户端凭据值

使用 Windows Communication Foundation （WCF），服务可以指定如何向服务验证客户端。 例如，服务可以规定客户端使用证书进行身份验证。

## <a name="to-determine-the-client-credential-type"></a>确定客户端凭据类型

1. 从服务的元数据终结点检索元数据。 通常，元数据包括两个文件：采用所选编程语言（默认情况下为 Visual C#）的客户端代码和一个 XML 配置文件。 检索元数据的方法之一是使用 Svcutil.exe 工具返回客户端代码和客户端配置。 有关详细信息，请参阅[检索元](./feature-details/retrieving-metadata.md)数据和[元数据实用工具（svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)。

2. 打开 XML 配置文件。 如果使用的是 Svcutil.exe 工具，则文件的默认名称为 Output.config。

3. 找到具有**mode**特性的 **\<security >** 元素（ **\<security mode =** `MessageOrTransport` **>** ，其中 `MessageOrTransport` 设置为其中一种安全模式。

4. 找到与模式值匹配的子元素。 例如，如果模式设置为 "**消息**"，则查找 **\<security >** 元素中包含的 **\<message >** 元素。

5. 请注意分配给**clientCredentialType**特性的值。 实际值取决于所使用的模式（传输或消息）。

下面的 XML 代码演示了对使用消息安全性并要求使用证书对客户端进行身份验证的客户端的配置。

```xml
<security mode="Message">
    <transport clientCredentialType="Windows" proxyCredentialType="None"
        realm="" />
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"
    algorithmSuite="Default" establishSecurityContext="true" />
</security>
```

## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>示例：TCP 传输模式，使用证书作为客户端凭据

此示例将安全模式设置为“传输”模式，并将客户端凭据值设置为 X.509 证书。 下面的过程演示如何在代码和配置中设置客户端上的客户端凭据值。 这假定你已使用配置的[元数据实用工具（svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)从服务返回元数据（代码和配置）。 有关详细信息，请参阅[如何：创建客户端](how-to-create-a-wcf-client.md)。

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>在代码中指定客户端上的客户端凭据值

1. 使用配置的[元数据实用工具（svcutil.exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)从服务生成代码和配置。

2. 使用生成的代码创建 WCF 客户端的实例。

3. 在客户端类上，将 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 类的 <xref:System.ServiceModel.ClientBase%601> 属性设置为适当的值。 本示例使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 类的 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> 方法将该属性设置为 X.509 证书。

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     可以使用 <xref:System.Security.Cryptography.X509Certificates.X509FindType> 类的任何枚举。 如果该证书发生更改（由于超过到期日期），则在此处使用主题名称。 使用主题名称，基础结构可以再次查找该证书。

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>在配置中指定客户端上的客户端凭据值

1. 将[\<behavior >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)元素添加到[\<behaviors >](../configure-apps/file-schema/wcf/behaviors.md)元素。

2. 将[\<clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md)元素添加到[\<behaviors >](../configure-apps/file-schema/wcf/behaviors.md)元素。 请确保将必需的 `name` 属性设置为适当的值。

3. 将[\<clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)元素添加到[\<clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md)元素。

4. 将下列特性设置为适当的值：`storeLocation`、`storeName`、`x509FindType` 和 `findValue`，如下面的代码中所示。 有关证书的详细信息，请参阅[使用证书](./feature-details/working-with-certificates.md)。

    ```xml
    <behaviors>
       <endpointBehaviors>
          <behavior name="endpointCredentialBehavior">
            <clientCredentials>
              <clientCertificate findValue="Contoso.com"
                                 storeLocation="LocalMachine"
                                 storeName="TrustedPeople"
                                 x509FindType="FindBySubjectName" />
            </clientCredentials>
          </behavior>
       </endpointBehaviors>
    </behaviors>
    ```

5. 在配置客户端时，通过设置 `behaviorConfiguration` 元素的 `<endpoint>` 特性来指定该行为，如下面的代码中所示。 终结点元素是[\<client >](../configure-apps/file-schema/wcf/client.md)元素的子元素。 同时还要通过将 `bindingConfiguration` 特性设置为客户端的绑定来指定绑定配置的名称。 如果使用的是生成的配置文件，则自动生成该绑定的名称。 在本示例中，该名称为 `"tcpBindingWithCredential"`。

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a>请参阅

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [WCF 安全编程](./feature-details/programming-wcf-security.md)
- [选择凭据类型](./feature-details/selecting-a-credential-type.md)
- [ServiceModel 元数据实用工具 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [使用证书](./feature-details/working-with-certificates.md)
- [如何：创建客户端](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<security >](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message >](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors >](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md)
