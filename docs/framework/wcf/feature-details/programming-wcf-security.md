---
title: WCF 보안 프로그래밍
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: e19f858818866f16b8af44abe462ddb826d43b69
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741476"
---
# <a name="programming-wcf-security"></a><span data-ttu-id="cb6fd-102">WCF 보안 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="cb6fd-102">Programming WCF Security</span></span>
<span data-ttu-id="cb6fd-103">本主题介绍用于创建安全 Windows Communication Foundation （WCF）应用程序的基本编程任务。</span><span class="sxs-lookup"><span data-stu-id="cb6fd-103">This topic describes the fundamental programming tasks used to create a secure Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="cb6fd-104">本主题仅介绍身份验证、机密性和完整性，共同称为*传输安全性*。</span><span class="sxs-lookup"><span data-stu-id="cb6fd-104">This topic covers only authentication, confidentiality, and integrity, collectively known as *transfer security*.</span></span> <span data-ttu-id="cb6fd-105">本主题不涉及授权（控制对资源或服务的访问权限）;有关授权的信息，请参阅[授权](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="cb6fd-105">This topic does not cover authorization (the control of access to resources or services); for information on authorization, see [Authorization](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cb6fd-106">有关安全概念的重要介绍（特别是在 WCF 方面），请参阅 MSDN 上的模式和实践教程集，以了解[Web 服务增强（WSE）3.0 的方案、模式和实现指南](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10))。</span><span class="sxs-lookup"><span data-stu-id="cb6fd-106">For a valuable introduction to security concepts, especially in regard to WCF, see the set of patterns and practices tutorials on MSDN at [Scenarios, Patterns, and Implementation Guidance for Web Services Enhancements (WSE) 3.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="cb6fd-107">WCF 安全编程基于三个步骤设置：安全模式、客户端凭据类型和凭据值。</span><span class="sxs-lookup"><span data-stu-id="cb6fd-107">Programming WCF security is based on three steps setting the following: the security mode, a client credential type, and the credential values.</span></span> <span data-ttu-id="cb6fd-108">코드 또는 구성을 통해 이러한 단계를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-108">You can perform these steps either through code or configuration.</span></span>  
  
## <a name="setting-the-security-mode"></a><span data-ttu-id="cb6fd-109">보안 모드 설정</span><span class="sxs-lookup"><span data-stu-id="cb6fd-109">Setting the Security Mode</span></span>  
 <span data-ttu-id="cb6fd-110">下面说明了在 WCF 中用安全模式编程的一般步骤：</span><span class="sxs-lookup"><span data-stu-id="cb6fd-110">The following explains the general steps for programming with the security mode in WCF:</span></span>  
  
1. <span data-ttu-id="cb6fd-111">애플리케이션 요구 사항에 적합한 미리 정의된 바인딩 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-111">Select one of the predefined bindings appropriate to your application requirements.</span></span> <span data-ttu-id="cb6fd-112">有关绑定选项的列表，请参阅[系统提供的绑定](../../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="cb6fd-112">For a list of the binding choices, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="cb6fd-113">기본적으로 거의 모든 바인딩에서 보안을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-113">By default, nearly every binding has security enabled.</span></span> <span data-ttu-id="cb6fd-114">一个例外是 <xref:System.ServiceModel.BasicHttpBinding> 类（使用配置、 [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)）。</span><span class="sxs-lookup"><span data-stu-id="cb6fd-114">The one exception is the <xref:System.ServiceModel.BasicHttpBinding> class (using configuration, the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).</span></span>  
  
     <span data-ttu-id="cb6fd-115">선택한 바인딩에 따라 전송이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-115">The binding you select determines the transport.</span></span> <span data-ttu-id="cb6fd-116">예를 들어, <xref:System.ServiceModel.WSHttpBinding>에서는 HTTP를 전송으로 사용하고 <xref:System.ServiceModel.NetTcpBinding>에서는 TCP를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-116">For example, <xref:System.ServiceModel.WSHttpBinding> uses HTTP as the transport; <xref:System.ServiceModel.NetTcpBinding> uses TCP.</span></span>  
  
2. <span data-ttu-id="cb6fd-117">바인딩에 대한 보안 모드 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-117">Select one of the security modes for the binding.</span></span> <span data-ttu-id="cb6fd-118">선택한 바인딩에 따라 사용 가능한 모드 선택 사항이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-118">Note that the binding you select determines the available mode choices.</span></span> <span data-ttu-id="cb6fd-119">예를 들어, <xref:System.ServiceModel.WSDualHttpBinding>에서는 전송 보안을 허용하지 않으므로, 전송 보안은 옵션이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-119">For example, the <xref:System.ServiceModel.WSDualHttpBinding> does not allow transport security (it is not an option).</span></span> <span data-ttu-id="cb6fd-120">마찬가지로 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>과 <xref:System.ServiceModel.NetNamedPipeBinding>에서는 모두 메시지 보안을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-120">Similarly, neither the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> nor the <xref:System.ServiceModel.NetNamedPipeBinding> allows message security.</span></span>  
  
     <span data-ttu-id="cb6fd-121">다음과 같은 세 가지 선택 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-121">You have three choices:</span></span>  
  
    1. `Transport`  
  
         <span data-ttu-id="cb6fd-122">전송 보안은 선택한 바인딩에서 사용하는 메커니즘에 종속됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-122">Transport security depends on the mechanism that the binding you have selected uses.</span></span> <span data-ttu-id="cb6fd-123">예를 들어, `WSHttpBinding`을 사용하는 경우 보안 메커니즘은 SSL(Secure Sockets Layer)(또한 HTTPS에 대한 메커니즘)입니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-123">For example, if you are using `WSHttpBinding` then the security mechanism is Secure Sockets Layer (SSL) (also the mechanism for the HTTPS protocol).</span></span> <span data-ttu-id="cb6fd-124">일반적으로 전송 보안의 주요 이점은 사용 중인 전송에 관계 없이 처리 능력이 우수하다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-124">Generally speaking, the main advantage of transport security is that it delivers good throughput no matter which transport you are using.</span></span> <span data-ttu-id="cb6fd-125">그러나 두 가지 제한이 있습니다. 첫째, 전송 메커니즘이 사용자를 인증하는 데 사용되는 자격 증명 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-125">However, it does have two limitations: The first is that the transport mechanism dictates the credential type used to authenticate a user.</span></span> <span data-ttu-id="cb6fd-126">이는 서비스가 다른 형식의 자격 증명을 요구하는 다른 서비스와 상호 작용해야 하는 경우에만 단점이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-126">This is a drawback only if a service needs to interoperate with other services that demand different types of credentials.</span></span> <span data-ttu-id="cb6fd-127">둘째는 메시지 수준에서 보안이 적용되지 않기 때문에 엔드투엔드 방식 대신 hop-by-hop 방식으로 보안이 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-127">The second is that, because the security is not applied at the message level, security is implemented in a hop-by-hop manner rather than end-to-end.</span></span> <span data-ttu-id="cb6fd-128">이 제한은 클라이언트와 서비스 사이의 메시지 경로에 매개자가 포함되어 있는 경우에만 문제가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-128">This latter limitation is an issue only if the message path between client and service includes intermediaries.</span></span> <span data-ttu-id="cb6fd-129">有关使用哪种传输的详细信息，请参阅[选择传输](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)。</span><span class="sxs-lookup"><span data-stu-id="cb6fd-129">For more information about which transport to use, see [Choosing a Transport](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md).</span></span> <span data-ttu-id="cb6fd-130">有关使用传输安全的详细信息，请参阅[传输安全概述](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="cb6fd-130">For more information about using transport security, see [Transport Security Overview](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).</span></span>  
  
    2. `Message`  
  
         <span data-ttu-id="cb6fd-131">메시지 보안은 모든 메시지에 메시지를 보안된 상태로 유지하는 데 필요한 헤더와 데이터가 포함되어 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-131">Message security means that every message includes the necessary headers and data to keep the message secure.</span></span> <span data-ttu-id="cb6fd-132">헤더의 구성이 다양하므로 여러 자격 증명을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-132">Because the composition of the headers varies, you can include any number of credentials.</span></span> <span data-ttu-id="cb6fd-133">이는 전송 메커니즘이 제공할 수 없는 특정 자격 증명 형식을 요구하는 다른 서비스와 상호 작용할 경우나 서비스마다 다른 자격 증명 형식을 요구하는 여러 서비스에서 메시지를 사용해야 하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-133">This becomes a factor if you are interoperating with other services that demand a specific credential type that a transport mechanism can't supply, or if the message must be used with more than one service, where each service demands a different credential type.</span></span>  
  
         <span data-ttu-id="cb6fd-134">有关详细信息，请参阅[消息安全](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="cb6fd-134">For more information, see [Message Security](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
    3. `TransportWithMessageCredential`  
  
         <span data-ttu-id="cb6fd-135">이 선택 옵션에서는 전송 계층을 사용하여 메시지 전송을 보안하지만, 모든 메시지에 다른 서비스에 필요한 풍부한 자격 증명이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-135">This choice uses the transport layer to secure the message transfer, while every message includes the rich credentials other services need.</span></span> <span data-ttu-id="cb6fd-136">이 옵션은 전송 보안의 성능 이점과 메시지 보안의 풍부한 자격 증명 이점을 결합합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-136">This combines the performance advantage of transport security with the rich credentials advantage of message security.</span></span> <span data-ttu-id="cb6fd-137"><xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding> 및 <xref:System.ServiceModel.WSHttpBinding> 바인딩에서 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-137">This is available with the following bindings: <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSFederationHttpBinding>, <xref:System.ServiceModel.NetPeerTcpBinding>, and <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3. <span data-ttu-id="cb6fd-138">HTTP(HTTPS)에 대해 전송 보안을 사용하려면 SSL 인증서를 사용하여 호스트를 구성하고 포트에서 SSL을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-138">If you decide to use transport security for HTTP (in other words, HTTPS), you must also configure the host with an SSL certificate and enable SSL on a port.</span></span> <span data-ttu-id="cb6fd-139">有关详细信息，请参阅[HTTP 传输安全](../../../../docs/framework/wcf/feature-details/http-transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="cb6fd-139">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
4. <span data-ttu-id="cb6fd-140"><xref:System.ServiceModel.WSHttpBinding>을 사용하고 보안 세션을 설정할 필요가 없는 경우 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> 속성을 `false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-140">If you are using the <xref:System.ServiceModel.WSHttpBinding> and do not need to establish a secure session, set the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="cb6fd-141">클라이언트와 서비스에서 대칭 키를 사용하여 채널을 만들 때(클라이언트와 서버가 대화 상자가 닫힐 때까지 대화 기간 동안 동일한 키를 사용), 보안 세션이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-141">A secure session occurs when a client and service create a channel using a symmetric key (both client and server use the same key for the length of a conversation, until the dialog is closed).</span></span>  
  
## <a name="setting-the-client-credential-type"></a><span data-ttu-id="cb6fd-142">클라이언트 자격 증명 형식 설정</span><span class="sxs-lookup"><span data-stu-id="cb6fd-142">Setting the Client Credential Type</span></span>  
 <span data-ttu-id="cb6fd-143">클라이언트 자격 증명 형식을 적절하게 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-143">Select a client credential type as appropriate.</span></span> <span data-ttu-id="cb6fd-144">有关详细信息，请参阅[选择凭据类型](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)。</span><span class="sxs-lookup"><span data-stu-id="cb6fd-144">For more information, see [Selecting a Credential Type](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).</span></span> <span data-ttu-id="cb6fd-145">다음과 같은 클라이언트 자격 증명 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-145">The following client credential types are available:</span></span>  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 <span data-ttu-id="cb6fd-146">모드 설정 방법에 따라 자격 증명 형식을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-146">Depending on how you set the mode, you must set the credential type.</span></span> <span data-ttu-id="cb6fd-147">다음 구성 예제에 표시된 것처럼 `wsHttpBinding`을 선택하고 모드를 "Message"로 설정한 경우 메시지 요소의 `clientCredentialType` 특성 값을 `None`, `Windows`, `UserName`, `Certificate`, `IssuedToken` 중 하나로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-147">For example, if you have selected the `wsHttpBinding`, and have set the mode to "Message," then you can also set the `clientCredentialType` attribute of the Message element to one of the following values: `None`, `Windows`, `UserName`, `Certificate`, and `IssuedToken`, as shown in the following configuration example.</span></span>  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>  
</bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="cb6fd-148">코드</span><span class="sxs-lookup"><span data-stu-id="cb6fd-148">Or in code:</span></span>  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a><span data-ttu-id="cb6fd-149">서비스 자격 증명 값 설정</span><span class="sxs-lookup"><span data-stu-id="cb6fd-149">Setting Service Credential Values</span></span>  
 <span data-ttu-id="cb6fd-150">클라이언트 자격 증명 형식을 선택한 경우 사용할 서비스 및 클라이언트에 대한 실제 자격 증명을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-150">Once you select a client credential type, you must set the actual credentials for the service and client to use.</span></span> <span data-ttu-id="cb6fd-151">서비스에서 자격 증명은 <xref:System.ServiceModel.Description.ServiceCredentials> 클래스를 사용하여 설정하고 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> 클래스의 <xref:System.ServiceModel.ServiceHostBase> 속성에 의해 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-151">On the service, credentials are set using the <xref:System.ServiceModel.Description.ServiceCredentials> class and returned by the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property of the <xref:System.ServiceModel.ServiceHostBase> class.</span></span> <span data-ttu-id="cb6fd-152">사용 중인 바인딩은 서비스 자격 증명 형식, 선택한 보안 모드 및 클라이언트 자격 증명 형식을 함축합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-152">The binding in use implies the service credential type, the security mode chosen, and the type of the client credential.</span></span> <span data-ttu-id="cb6fd-153">다음 코드에서는 서비스 자격 증명에 대한 인증서를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-153">The following code sets a certificate for a service credential.</span></span>  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a><span data-ttu-id="cb6fd-154">클라이언트 자격 증명 값 설정</span><span class="sxs-lookup"><span data-stu-id="cb6fd-154">Setting Client Credential Values</span></span>  
 <span data-ttu-id="cb6fd-155">클라이언트에서 클라이언트 자격 증명 값은 <xref:System.ServiceModel.Description.ClientCredentials> 클래스를 사용하여 설정하고 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 클래스의 <xref:System.ServiceModel.ClientBase%601> 속성에 의해 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-155">On the client, set client credential values using the <xref:System.ServiceModel.Description.ClientCredentials> class and returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class.</span></span> <span data-ttu-id="cb6fd-156">다음 코드에서는 TCP 프로토콜을 사용하여 인증서를 클라이언트에 대한 자격 증명으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="cb6fd-156">The following code sets a certificate as a credential on a client using the TCP protocol.</span></span>  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cb6fd-157">另请参阅</span><span class="sxs-lookup"><span data-stu-id="cb6fd-157">See also</span></span>

- [<span data-ttu-id="cb6fd-158">기본 WCF 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="cb6fd-158">Basic WCF Programming</span></span>](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [<span data-ttu-id="cb6fd-159">일반적인 보안 시나리오</span><span class="sxs-lookup"><span data-stu-id="cb6fd-159">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
