---
title: 利用证书身份验证的传输安全
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 3d726b71-4d8b-4581-a3bb-02b9af51d11b
ms.openlocfilehash: a348fb7989a83ec9ee7903bd38896bedcf86ce3a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074529"
---
# <a name="transport-security-with-certificate-authentication"></a><span data-ttu-id="1d62e-102">利用证书身份验证的传输安全</span><span class="sxs-lookup"><span data-stu-id="1d62e-102">Transport Security with Certificate Authentication</span></span>
<span data-ttu-id="1d62e-103">本主题探讨使用传输安全性时如何使用 X.509 证书进行服务器和客户端身份验证。</span><span class="sxs-lookup"><span data-stu-id="1d62e-103">This topic discusses using X.509 certificates for server and client authentication when using transport security.</span></span> <span data-ttu-id="1d62e-104">有关 X.509 证书的详细信息，请参阅 [X.509 公钥证书](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates)。</span><span class="sxs-lookup"><span data-stu-id="1d62e-104">For more information about X.509 certificates see [X.509 Public Key Certificates](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="1d62e-105">证书必须由证书颁发，这通常是第三方证书颁发机构颁发。</span><span class="sxs-lookup"><span data-stu-id="1d62e-105">Certificates must be issued by a certification authority, which is often a third-party issuer of certificates.</span></span> <span data-ttu-id="1d62e-106">在 Windows Server 域中，可以使用 Active Directory 证书服务向域中的客户端计算机颁发证书。</span><span class="sxs-lookup"><span data-stu-id="1d62e-106">On a Windows Server domain, Active Directory Certificate Services can be used to issue certificates to client computers on the domain.</span></span> <span data-ttu-id="1d62e-107">有关详细信息请参阅[Windows 2008 R2 证书服务](https://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409)。</span><span class="sxs-lookup"><span data-stu-id="1d62e-107">For more information see [Windows 2008 R2 Certificate Services](https://go.microsoft.com/fwlink/?LinkID=209949&clcid=0x409).</span></span> <span data-ttu-id="1d62e-108">在此方案中，该服务承载在使用安全套接字层 (SSL) 配置的 Internet Information Services (IIS) 之下。</span><span class="sxs-lookup"><span data-stu-id="1d62e-108">In this scenario, the service is hosted under Internet Information Services (IIS) which is configured with Secure Sockets Layer (SSL).</span></span> <span data-ttu-id="1d62e-109">该服务使用 SSL (X.509) 证书进行配置，以允许客户端验证服务器的身份。</span><span class="sxs-lookup"><span data-stu-id="1d62e-109">The service is configured with an SSL (X.509) certificate to allow clients to verify the identity of the server.</span></span> <span data-ttu-id="1d62e-110">客户端也使用 X.509 证书进行配置，以允许服务验证客户端的身份。</span><span class="sxs-lookup"><span data-stu-id="1d62e-110">The client is also configured with an X.509 certificate that allows the service to verify the identity of the client.</span></span> <span data-ttu-id="1d62e-111">客户端必须信任服务器的证书，服务器也必须信任客户端的证书。</span><span class="sxs-lookup"><span data-stu-id="1d62e-111">The server’s certificate must be trusted by the client and the client’s certificate must be trusted by the server.</span></span> <span data-ttu-id="1d62e-112">服务和客户端如何验证彼此身份的实际机制不在本主题讨论范围之内。</span><span class="sxs-lookup"><span data-stu-id="1d62e-112">The actual mechanics of how the service and client verifies each other’s identity is beyond the scope of this topic.</span></span> <span data-ttu-id="1d62e-113">有关详细信息请参阅[Wikipedia 上的数字签名](https://go.microsoft.com/fwlink/?LinkId=253157)。</span><span class="sxs-lookup"><span data-stu-id="1d62e-113">For more information see [Digital Signature on Wikipedia](https://go.microsoft.com/fwlink/?LinkId=253157).</span></span>  
  
 <span data-ttu-id="1d62e-114">该方案实现一个请求/回复消息模式，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="1d62e-114">This scenario implements a request/reply message pattern as illustrated by the following diagram.</span></span>  
  
 <span data-ttu-id="1d62e-115">![使用证书确保传输安全](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span><span class="sxs-lookup"><span data-stu-id="1d62e-115">![Secure transfer using certificates](../../../../docs/framework/wcf/feature-details/media/8f7b8968-899f-4538-a9e8-0eaa872a291c.gif "8f7b8968-899f-4538-a9e8-0eaa872a291c")</span></span>  
  
 <span data-ttu-id="1d62e-116">有关与服务使用的证书的详细信息，请参阅[Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)和[如何：使用 SSL 证书配置端口](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="1d62e-116">For more information about using a certificate with a service, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span> <span data-ttu-id="1d62e-117">下表描述了该方案的各项特征。</span><span class="sxs-lookup"><span data-stu-id="1d62e-117">The following table describes the various characteristics of the scenario.</span></span>  
  
|<span data-ttu-id="1d62e-118">特征</span><span class="sxs-lookup"><span data-stu-id="1d62e-118">Characteristic</span></span>|<span data-ttu-id="1d62e-119">描述</span><span class="sxs-lookup"><span data-stu-id="1d62e-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1d62e-120">安全模式</span><span class="sxs-lookup"><span data-stu-id="1d62e-120">Security Mode</span></span>|<span data-ttu-id="1d62e-121">传输</span><span class="sxs-lookup"><span data-stu-id="1d62e-121">Transport</span></span>|  
|<span data-ttu-id="1d62e-122">互操作性</span><span class="sxs-lookup"><span data-stu-id="1d62e-122">Interoperability</span></span>|<span data-ttu-id="1d62e-123">与现有 Web 服务客户端和服务。</span><span class="sxs-lookup"><span data-stu-id="1d62e-123">With existing Web service clients and services.</span></span>|  
|<span data-ttu-id="1d62e-124">身份验证（服务器）</span><span class="sxs-lookup"><span data-stu-id="1d62e-124">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="1d62e-125">身份验证（客户端）</span><span class="sxs-lookup"><span data-stu-id="1d62e-125">Authentication (Client)</span></span>|<span data-ttu-id="1d62e-126">是（使用 SSL 证书）</span><span class="sxs-lookup"><span data-stu-id="1d62e-126">Yes (using an SSL certificate)</span></span><br /><br /> <span data-ttu-id="1d62e-127">是（使用 X.509 证书）</span><span class="sxs-lookup"><span data-stu-id="1d62e-127">Yes (using an X.509 certificate)</span></span>|  
|<span data-ttu-id="1d62e-128">数据完整性</span><span class="sxs-lookup"><span data-stu-id="1d62e-128">Data Integrity</span></span>|<span data-ttu-id="1d62e-129">是</span><span class="sxs-lookup"><span data-stu-id="1d62e-129">Yes</span></span>|  
|<span data-ttu-id="1d62e-130">数据保密性</span><span class="sxs-lookup"><span data-stu-id="1d62e-130">Data Confidentiality</span></span>|<span data-ttu-id="1d62e-131">是</span><span class="sxs-lookup"><span data-stu-id="1d62e-131">Yes</span></span>|  
|<span data-ttu-id="1d62e-132">传输</span><span class="sxs-lookup"><span data-stu-id="1d62e-132">Transport</span></span>|<span data-ttu-id="1d62e-133">HTTPS</span><span class="sxs-lookup"><span data-stu-id="1d62e-133">HTTPS</span></span>|  
|<span data-ttu-id="1d62e-134">绑定</span><span class="sxs-lookup"><span data-stu-id="1d62e-134">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="configure-the-service"></a><span data-ttu-id="1d62e-135">配置服务</span><span class="sxs-lookup"><span data-stu-id="1d62e-135">Configure the Service</span></span>  
 <span data-ttu-id="1d62e-136">由于该方案中的服务承载于 IIS 之下，因此它是使用 web.config 文件配置的。</span><span class="sxs-lookup"><span data-stu-id="1d62e-136">Since the service in this scenario is hosted under IIS, it is configured with a web.config file.</span></span> <span data-ttu-id="1d62e-137">以下 web.config 揭示了如何配置  <xref:System.ServiceModel.WSHttpBinding> 以使用传输安全性和 X.509 客户端凭据。</span><span class="sxs-lookup"><span data-stu-id="1d62e-137">The following web.config shows how to configure the <xref:System.ServiceModel.WSHttpBinding> to use transport security and X.509 client credentials.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <protocolMapping>  
      <add scheme="https" binding="wsHttpBinding" />  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttp binding with Transport security mode and clientCredentialType as Certificate -->  
        <binding>  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>              
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>            
           <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="configure-the-client"></a><span data-ttu-id="1d62e-138">配置客户端</span><span class="sxs-lookup"><span data-stu-id="1d62e-138">Configure the Client</span></span>  
 <span data-ttu-id="1d62e-139">可以在代码中或在 app.config 文件中配置客户端。</span><span class="sxs-lookup"><span data-stu-id="1d62e-139">The client can be configured in code or in an app.config file.</span></span> <span data-ttu-id="1d62e-140">下例揭示了如何在代码中配置客户端。</span><span class="sxs-lookup"><span data-stu-id="1d62e-140">The following example shows how to configure the client in code.</span></span>  
  
```vb  
// Create the binding.  
WSHttpBinding myBinding = new WSHttpBinding();  
myBinding.Security.Mode = SecurityMode.Transport;  
myBinding.Security.Transport.ClientCredentialType =  
   HttpClientCredentialType.Certificate;  
  
// Create the endpoint address. Note that the machine name   
// must match the subject or DNS field of the X.509 certificate  
// used to authenticate the service.   
EndpointAddress ea = new  
   EndpointAddress("https://localhost/CalculatorService/service.svc");  
  
// Create the client. The code for the calculator   
// client is not shown here. See the sample applications  
// for examples of the calculator code.  
CalculatorClient cc =  
   new CalculatorClient(myBinding, ea);  
  
// The client must specify a certificate trusted by the server.  
cc.ClientCredentials.ClientCertificate.SetCertificate(  
    StoreLocation.CurrentUser,  
    StoreName.My,  
    X509FindType.FindBySubjectName,  
    "contoso.com");  
  
// Begin using the client.  
Console.WriteLine(cc.Add(100, 1111));  
//...  
cc.Close();  
```  
  
 <span data-ttu-id="1d62e-141">也可以在 app.config 文件中配置客户端，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="1d62e-141">Alternatively you can configure the client in an App.config file as shown in the following example:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint address=" https://localhost/CalculatorService/service.svc "   
                behaviorConfiguration="endpointCredentialBehavior"  
                binding="wsHttpBinding"   
                bindingConfiguration="Binding1"   
                contract="Microsoft.Samples.TransportSecurity.ICalculator"/>  
    </client>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="contoso.com"  
                               storeLocation="CurrentUser"  
                               storeName="My"  
                               x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <!-- configure wsHttpbinding with Transport security mode  
                   and clientCredentialType as Certificate -->  
        <binding name="Binding1">  
          <security mode="Transport">  
            <transport clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
  
<startup><supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.0"/></startup></configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d62e-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="1d62e-142">See also</span></span>

- [<span data-ttu-id="1d62e-143">安全性概述</span><span class="sxs-lookup"><span data-stu-id="1d62e-143">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="1d62e-144">Windows Server App Fabric 的安全模型</span><span class="sxs-lookup"><span data-stu-id="1d62e-144">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
