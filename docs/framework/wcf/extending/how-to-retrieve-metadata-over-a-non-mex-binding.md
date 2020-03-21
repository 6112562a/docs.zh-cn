---
title: 如何：通过非 MEX 绑定检索元数据
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: a006795c87a2ae845d03db90dce296692c4339fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186451"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="dcd3c-102">如何：通过非 MEX 绑定检索元数据</span><span class="sxs-lookup"><span data-stu-id="dcd3c-102">How to: Retrieve Metadata Over a non-MEX Binding</span></span>
<span data-ttu-id="dcd3c-103">本主题介绍如何通过非 MEX 绑定从 MEX 终结点检索元数据。</span><span class="sxs-lookup"><span data-stu-id="dcd3c-103">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="dcd3c-104">此示例中的代码基于[自定义安全元数据终结点](../samples/custom-secure-metadata-endpoint.md)示例。</span><span class="sxs-lookup"><span data-stu-id="dcd3c-104">The code in this sample is based on the [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="dcd3c-105">通过非 MEX 绑定检索元数据</span><span class="sxs-lookup"><span data-stu-id="dcd3c-105">To retrieve metadata over a non-MEX binding</span></span>  
  
1. <span data-ttu-id="dcd3c-106">确定由 MEX 终结点使用的绑定。</span><span class="sxs-lookup"><span data-stu-id="dcd3c-106">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="dcd3c-107">对于 Windows 通信基础 （WCF） 服务，您可以通过访问服务的配置文件来确定 MEX 绑定。</span><span class="sxs-lookup"><span data-stu-id="dcd3c-107">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="dcd3c-108">在本例中，MEX 绑定在以下服务配置中定义。</span><span class="sxs-lookup"><span data-stu-id="dcd3c-108">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
    ```xml  
    <services>  
        <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                behaviorConfiguration="CalculatorServiceBehavior">  
         <!-- Use the base address provided by the host. -->  
         <endpoint address=""  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding2"  
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
         <endpoint address="mex"  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding1"  
           contract="IMetadataExchange" />  
         </service>  
     </services>  
     <bindings>  
       <wsHttpBinding>  
         <binding name="Binding1">  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
         <binding name="Binding2">  
           <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
       </wsHttpBinding>  
     </bindings>  
    ```  
  
2. <span data-ttu-id="dcd3c-109">在客户端配置文件中，配置同样的自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="dcd3c-109">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="dcd3c-110">在该配置文件中，客户端还定义了一个 `clientCredentials` 行为以提供证书，用于在请求 MEX 终结点中的元数据时对服务进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="dcd3c-110">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="dcd3c-111">在使用 Svcutil.exe 通过自定义绑定请求元数据时，应向 Svcutil.exe 的配置文件 (Svcutil.exe.config) 中添加 MEX 终结点配置，并且终结点配置的名称应与 MEX 终结点地址的 URI 架构匹配，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="dcd3c-111">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <client>  
        <endpoint name="http"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientCertificateBehavior"  
                  contract="IMetadataExchange" />  
      </client>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="Certificate"/>  
            </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="ClientCertificateBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
              <serviceCertificate>  
                <authentication certificateValidationMode="PeerOrChainTrust" />  
              </serviceCertificate>  
            </clientCredentials>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>
    </system.serviceModel>  
    ```  
  
3. <span data-ttu-id="dcd3c-112">创建一个 `MetadataExchangeClient` 并调用 `GetMetadata`。</span><span class="sxs-lookup"><span data-stu-id="dcd3c-112">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="dcd3c-113">有两种方法可以完成此操作：在配置中指定自定义绑定，或在代码中指定自定义绑定，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="dcd3c-113">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
    ```csharp
    // The custom binding is specified in configuration.  
    EndpointAddress mexAddress = new EndpointAddress("http://localhost:8000/ServiceModelSamples/Service/mex");  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("http");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mexSet = mexClient.GetMetadata(mexAddress);  
  
    // The custom binding is specified in code.  
    // Specify the Metadata Exchange binding and its security mode.  
    WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
    mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
    // Create a MetadataExchangeClient and set the certificate details.  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
    mexClient.SoapCredentials.ClientCertificate.SetCertificate(  
        StoreLocation.CurrentUser, StoreName.My,  
        X509FindType.FindBySubjectName, "client.com");  
    mexClient.SoapCredentials.ServiceCertificate.Authentication.  
        CertificateValidationMode =  
        X509CertificateValidationMode.PeerOrChainTrust;  
    mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(  
        StoreLocation.CurrentUser, StoreName.TrustedPeople,  
        X509FindType.FindBySubjectName, "localhost");  
    MetadataExchangeClient mexClient2 = new MetadataExchangeClient(customBinding);  
    mexClient2.ResolveMetadataReferences = true;  
    MetadataSet mexSet2 = mexClient2.GetMetadata(mexAddress);  
    ```  
  
4. <span data-ttu-id="dcd3c-114">创建 `WsdlImporter` 并调用 `ImportAllEndpoints`，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="dcd3c-114">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. <span data-ttu-id="dcd3c-115">此时，您拥有服务终结点的集合。</span><span class="sxs-lookup"><span data-stu-id="dcd3c-115">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="dcd3c-116">有关导入元数据的详细信息，请参阅[如何：将元数据导入服务终结点](../feature-details/how-to-import-metadata-into-service-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="dcd3c-116">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcd3c-117">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dcd3c-117">See also</span></span>

- [<span data-ttu-id="dcd3c-118">元</span><span class="sxs-lookup"><span data-stu-id="dcd3c-118">Metadata</span></span>](../feature-details/metadata.md)
