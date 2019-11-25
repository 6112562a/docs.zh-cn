---
title: 如何：配置 WCF 服务以便与 WSE 3.0 客户端进行互操作
ms.date: 03/30/2017
ms.assetid: 0f38c4a0-49a6-437c-bdde-ad1d138d3c4a
ms.openlocfilehash: bd9f2bec94ca45f76590f64366428a00edd5d6ea
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141742"
---
# <a name="how-to-configure-wcf-services-to-interoperate-with-wse-30-clients"></a>如何：配置 WCF 服务以便与 WSE 3.0 客户端进行互操作

当 WCF 服务配置为使用8月2004版的 WS-ADDRESSING 规范时，Windows Communication Foundation （WCF）服务与用于 Microsoft .NET （WSE）客户端的 Web 服务增强3.0 线路级别兼容。

### <a name="to-enable-a-wcf-service-to-interoperate-with-wse-30-clients"></a>使 WCF 服务与 WSE 3.0 客户端进行互操作

1. 定义 WCF 服务的自定义绑定。

    若要指定将 WS-Addressing 规范的 2004 年 8 月版用于消息编码，必须创建自定义绑定。

    1. 将子[\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)添加到服务的配置文件[\<绑定](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)。

    2. 通过将[\<绑定 >](../../configure-apps/file-schema/wcf/bindings.md)添加到[\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)并设置 `name` 属性，指定绑定的名称。

    3. 通过将子[\<安全 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)添加到[\<绑定 >](../../configure-apps/file-schema/wcf/bindings.md)，指定身份验证模式和用于保护与 WSE 3.0 兼容的消息的 WS 安全规范的版本。

        若要设置身份验证模式，请设置[\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)的 `authenticationMode` 属性。 身份验证模式大致等效于 WSE 3.0 中的关守安全断言。 下表将 WCF 中的身份验证模式映射到 WSE 3.0 中的交钥匙安全声明。

        |WCF 身份验证模式|WSE 3.0 关守安全断言|
        |-----------------------------|----------------------------------------|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate>|`anonymousForCertificateSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.Kerberos>|`kerberosSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate10Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate>|`mutualCertificate11Security`*|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameOverTransport>|`usernameOverTransportSecurity`|
        |<xref:System.ServiceModel.Configuration.AuthenticationMode.UserNameForCertificate>|`usernameForCertificateSecurity`|

        \* `mutualCertificate10Security` 和 `mutualCertificate11Security` 交钥匙安全声明的主要区别之一是 WSE 用于保护 SOAP 消息的 WS 安全规范的版本。 `mutualCertificate10Security` 使用 WS-Security 1.0，而 WS-Security 1.1 用于 `mutualCertificate11Security`。 对于 WCF，将在[\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)的 `messageSecurityVersion` 特性中指定 WS 安全规范的版本。

        若要设置用于保护 SOAP 消息的 WS 安全规范的版本，请设置[\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)的 `messageSecurityVersion` 属性。 若要与 WSE 3.0 进行互操作，请将 `messageSecurityVersion` 属性的值设置为 <xref:System.ServiceModel.MessageSecurityVersion.WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10%2A>。

    4. 指定 WCF 将使用8月2004版的 WS-ADDRESSING 规范，方法是添加一个[\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)并将 `messageVersion` 设置为 <xref:System.ServiceModel.Channels.MessageVersion.Soap11WSAddressingAugust2004%2A>值。

        > [!NOTE]
        > 在使用 SOAP 1.2 时，请将 `messageVersion` 属性设置为 <xref:System.ServiceModel.Channels.MessageVersion.Soap12WSAddressingAugust2004%2A>。

2. 指定该服务使用自定义绑定。

    1. 将[\<终结点 >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)元素的 `binding` 属性设置为 "`customBinding`"。

    2. 将[\<终结点 >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)元素的 `bindingConfiguration` 特性设置为自定义绑定\<[绑定 >](../../configure-apps/file-schema/wcf/bindings.md)的 `name` 特性中指定的值。

## <a name="example"></a>示例

下面的代码示例指定 `Service.HelloWorldService` 使用自定义绑定与 WSE 3.0 客户端进行互操作。 自定义绑定指定使用 WS-Addressing 的 2004 年 8 月版本和 WS-Security 1.1 规范集对所交换的消息进行编码。 使用 <xref:System.ServiceModel.Configuration.AuthenticationMode.AnonymousForCertificate> 身份验证模式保证消息的安全。

```xml
<configuration>
  <system.serviceModel>
    <services>
      <service
        behaviorConfiguration="ServiceBehavior"
        name="Service.HelloWorldService">
        <endpoint binding="customBinding" address=""
          bindingConfiguration="ServiceBinding"
          contract="Service.IHelloWorld"></endpoint>
      </service>
    </services>

    <bindings>
      <customBinding>
        <binding name="ServiceBinding">
          <security authenticationMode="AnonymousForCertificate"
                  messageProtectionOrder="SignBeforeEncrypt"
                  messageSecurityVersion="WSSecurity11WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10"
                  requireDerivedKeys="false">
          </security>
          <textMessageEncoding messageVersion ="Soap11WSAddressingAugust2004"></textMessageEncoding>
          <httpTransport/>
        </binding>
      </customBinding>
    </bindings>
    <behaviors>
      <behavior name="ServiceBehavior" returnUnknownExceptionsAsFaults="true">
        <serviceCredentials>
          <serviceCertificate findValue="CN=WCFQuickstartServer" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName"/>
        </serviceCredentials>
      </behavior>
    </behaviors>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>请参阅

- [如何：自定义系统提供的绑定](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)
