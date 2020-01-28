---
title: 메시지 보안을 사용하여 메시지에 보안 설정
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
ms.openlocfilehash: a6b062d0d6a74ce2a2ff9afa7e8a0a18853dbd22
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746444"
---
# <a name="securing-messages-using-message-security"></a><span data-ttu-id="fbc9c-102">메시지 보안을 사용하여 메시지에 보안 설정</span><span class="sxs-lookup"><span data-stu-id="fbc9c-102">Securing Messages Using Message Security</span></span>
<span data-ttu-id="fbc9c-103">本部分讨论使用 <xref:System.ServiceModel.NetMsmqBinding>时的 WCF 消息安全性。</span><span class="sxs-lookup"><span data-stu-id="fbc9c-103">This section discusses WCF message security when using <xref:System.ServiceModel.NetMsmqBinding>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fbc9c-104">在阅读本主题之前，建议你阅读[安全概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="fbc9c-104">Before reading through this topic, it is recommended that you read [Security Concepts](../../../../docs/framework/wcf/feature-details/security-concepts.md).</span></span>  
  
 <span data-ttu-id="fbc9c-105">下图提供了使用 WCF 进行排队通信的概念模型。</span><span class="sxs-lookup"><span data-stu-id="fbc9c-105">The following illustration provides a conceptual model of queued communication using WCF.</span></span> <span data-ttu-id="fbc9c-106">이 그림과 용어는 전송 보안 개념을</span><span class="sxs-lookup"><span data-stu-id="fbc9c-106">This illustration and terminology are used to explain</span></span>  
  
 <span data-ttu-id="fbc9c-107">설명하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-107">transport security concepts.</span></span>  
  
 <span data-ttu-id="fbc9c-108">![排队应用程序关系图](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "분산 큐 그림")</span><span class="sxs-lookup"><span data-stu-id="fbc9c-108">![Queued Application Diagram](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Distributed-Queue-Figure")</span></span>  
  
 <span data-ttu-id="fbc9c-109">当使用 WCF 发送排队消息时，WCF 消息将附加为消息队列（MSMQ）消息的正文。</span><span class="sxs-lookup"><span data-stu-id="fbc9c-109">When sending queued messages using WCF, the WCF message is attached as a body of the Message Queuing (MSMQ) message.</span></span> <span data-ttu-id="fbc9c-110">전송 보안은 MSMQ 메시지 전체를 보호하지만, 메시지(또는 SOAP) 보안은 MSMQ 메시지의 본문만 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-110">While transport security secures the entire MSMQ message, message (or SOAP) security only secures the body of the MSMQ message.</span></span>  
  
 <span data-ttu-id="fbc9c-111">클라이언트에서 대상 큐의 메시지를 보호하는 전송 보안과 달리, 메시지 보안의 핵심 개념은 클라이언트에서 받는 애플리케이션(서비스)의 메시지를 보호하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-111">The key concept of message security is that the client secures the message for the receiving application (service), unlike transport security where the client secures the message for the Target Queue.</span></span> <span data-ttu-id="fbc9c-112">因此，在使用消息安全保护 WCF 消息时，MSMQ 不起作用。</span><span class="sxs-lookup"><span data-stu-id="fbc9c-112">As such, MSMQ plays no part when securing the WCF message using message security.</span></span>  
  
 <span data-ttu-id="fbc9c-113">WCF 消息安全将安全标头添加到 WCF 消息，该消息与现有安全基础结构（如证书或 Kerberos 协议）集成。</span><span class="sxs-lookup"><span data-stu-id="fbc9c-113">WCF message security adds security headers to the WCF message that integrate with existing security infrastructures, such as a certificate or the Kerberos protocol.</span></span>  
  
## <a name="message-credential-type"></a><span data-ttu-id="fbc9c-114">메시지 자격 증명 형식</span><span class="sxs-lookup"><span data-stu-id="fbc9c-114">Message Credential Type</span></span>  
 <span data-ttu-id="fbc9c-115">메시지 보안을 사용하면 서비스 및 클라이언트에서 서로 자격 증명을 제출하여 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-115">Using message security, the service and client can present credentials to authenticate each another.</span></span> <span data-ttu-id="fbc9c-116"><xref:System.ServiceModel.NetMsmqBinding.Security%2A> 모드를 `Message` 또는 `Both`(즉, 전송 보안과 메시지 보안 모두 사용)로 설정하면 메시지 보안을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-116">You can select message security by setting the <xref:System.ServiceModel.NetMsmqBinding.Security%2A> mode to `Message` or `Both` (that is, use both transport security and message security).</span></span>  
  
 <span data-ttu-id="fbc9c-117">서비스에서 <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> 속성을 사용하여 클라이언트 인증에 사용되는 자격 증명을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-117">The service can use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to inspect the credential used to authenticate the client.</span></span> <span data-ttu-id="fbc9c-118">이 방법을 사용하여 서비스에서 구현하는 추가 인증 검사를 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-118">This can also be used for further authorization checks that the service chooses to implement.</span></span>  
  
 <span data-ttu-id="fbc9c-119">이 절에서는 서로 다른 자격 증명 형식과 큐에서 그러한 형식을 사용하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-119">This section explains the different credential types and how to use them with queues.</span></span>  
  
### <a name="certificate"></a><span data-ttu-id="fbc9c-120">인증서</span><span class="sxs-lookup"><span data-stu-id="fbc9c-120">Certificate</span></span>  
 <span data-ttu-id="fbc9c-121">Certificate 자격 증명 형식에서는 X.509 인증서를 사용하여 서비스와 클라이언트를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-121">The certificate credential type uses an X.509 certificate to identify the service and the client.</span></span>  
  
 <span data-ttu-id="fbc9c-122">일반적인 시나리오에서 클라이언트와 서비스에는 신뢰할 수 있는 인증 기관의 유효한 인증서가 발급됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-122">In a typical scenario, the client and the service are issued a valid certificate by a trusted certification authority.</span></span> <span data-ttu-id="fbc9c-123">그런 다음 연결이 설정되고, 클라이언트에서 서비스의 인증서를 통해 서비스의 유효성을 인증하여 서비스 신뢰 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-123">Then the connection is established, the client authenticates the validity of the service using the service's certificate to decide whether it can trust the service.</span></span> <span data-ttu-id="fbc9c-124">마찬가지로 서비스에서는 클라이언트의 인증서를 사용하여 클라이언트 신뢰를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-124">Similarly, the service uses the client's certificate to validate the client trust.</span></span>  
  
 <span data-ttu-id="fbc9c-125">연결되지 않은 쿼리의 성질을 생각하면, 클라이언트와 서비스는 동시에 온라인 상태가 아닐 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-125">Given the disconnected nature of queues, the client and the service may not be online at the same time.</span></span> <span data-ttu-id="fbc9c-126">따라서 클라이언트와 서비스는 out-of-band로 인증서를 교환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-126">As such, the client and service have to exchange certificates out-of-band.</span></span> <span data-ttu-id="fbc9c-127">특히 신뢰할 수 있는 저장소에 서비스의 인증서(인증 기관에 체인으로 연결 가능)를 가지고 있는 클라이언트는 올바른 서비스와 통신하고 있는 것을 신뢰해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-127">In particular, the client, by virtue of holding the service's certificate (which can be chained to a certification authority) in its trusted store, must trust that it is communicating with the correct service.</span></span> <span data-ttu-id="fbc9c-128">클라이언트 인증의 경우 서비스에서는 메시지와 함께 첨부된 X.509 인증서를 저장소에 있는 인증서와 비교하여 클라이언트를 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-128">For authenticating the client, the service uses the X.509 certificate attached with the message to matches it with the certificate in its store to verify the authenticity of the client.</span></span> <span data-ttu-id="fbc9c-129">인증서는 인증 기관에 연결되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-129">Again, the certificate must be chained to a certification authority.</span></span>  
  
 <span data-ttu-id="fbc9c-130">Windows를 실행하는 컴퓨터에서 인증서는 다양한 종류의 저장소에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-130">On a computer running Windows, certificates are held in several kinds of stores.</span></span> <span data-ttu-id="fbc9c-131">有关不同存储的详细信息，请参阅[证书存储](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="fbc9c-131">For more information about the different stores, see [Certificate stores](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10)).</span></span>  
  
### <a name="windows"></a><span data-ttu-id="fbc9c-132">Windows</span><span class="sxs-lookup"><span data-stu-id="fbc9c-132">Windows</span></span>  
 <span data-ttu-id="fbc9c-133">Windows 메시지 자격 증명 형식에는 Kerberos 프로토콜이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-133">Windows message credential type uses the Kerberos protocol.</span></span>  
  
 <span data-ttu-id="fbc9c-134">Kerberos 프로토콜은 도메인에서 사용자를 인증하고 인증된 사용자가 도메인에 있는 다른 엔터티와 보안 컨텍스트를 구성할 수 있게 해 주는 보안 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-134">The Kerberos protocol is a security mechanism that authenticates users on a domain and allows the authenticated users to establish secure contexts with other entities on a domain.</span></span>  
  
 <span data-ttu-id="fbc9c-135">대기 중인 통신에 Kerberos 프로토콜을 사용하는 경우의 문제는 KDC(키 배포 센터)에서 배포하는 클라이언트 ID가 포함된 티켓의 수명이 비교적 짧다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-135">The problem with using the Kerberos protocol for queued communication is that the tickets that contain client identity that the Key Distribution Center (KDC) distributes are relatively short-lived.</span></span> <span data-ttu-id="fbc9c-136">*生存期*与指示票证有效性的 Kerberos 票证关联。</span><span class="sxs-lookup"><span data-stu-id="fbc9c-136">A *lifetime* is associated with the Kerberos ticket that indicates the validity of the ticket.</span></span> <span data-ttu-id="fbc9c-137">따라서 대기 시간이 긴 경우에는 클라이언트를 인증하는 서비스에서 토큰이 여전히 유효한지 확신할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-137">As such, given high latency, you cannot be sure that the token is still valid for the service that authenticates the client.</span></span>  
  
 <span data-ttu-id="fbc9c-138">이 자격 증명 형식을 사용하는 경우 서비스는 SERVICE 계정에서 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-138">Note that when using this credential type, the service must be running under the SERVICE account.</span></span>  
  
 <span data-ttu-id="fbc9c-139">메시지 자격 증명을 선택할 때, 기본적으로 Kerberos 프로토콜이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-139">The Kerberos protocol is used by default when choosing message credential.</span></span>
  
### <a name="username-password"></a><span data-ttu-id="fbc9c-140">Username Password</span><span class="sxs-lookup"><span data-stu-id="fbc9c-140">Username Password</span></span>  
 <span data-ttu-id="fbc9c-141">이 속성을 이용하면 메시지의 보안 헤더에 사용자 이름 암호를 사용하여 클라이언트를 서버에 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-141">Using this property, the client can authenticate to the server using a username password in the security header of the message.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="fbc9c-142">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="fbc9c-142">IssuedToken</span></span>  
 <span data-ttu-id="fbc9c-143">클라이언트에서는 보안 토큰 서비스를 사용하여 서비스에서 클라이언트에 사용할 메시지에 첨부되는 토큰을 발급할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-143">The client can use the security token service to issue a token that can then be attached to the message for the service to authenticate the client.</span></span>  
  
## <a name="using-transport-and-message-security"></a><span data-ttu-id="fbc9c-144">전송 및 메시지 보안 사용</span><span class="sxs-lookup"><span data-stu-id="fbc9c-144">Using Transport and Message Security</span></span>  
 <span data-ttu-id="fbc9c-145">전송 보안과 메시지 보안을 모두 사용하는 경우에는 전송과 SOAP 메시지 수준 모두에서 메시지 보호에 사용되는 인증서가 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fbc9c-145">When using both transport security and message security, the certificate used to secure the message both at the transport and the SOAP message level must be the same.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc9c-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="fbc9c-146">See also</span></span>

- [<span data-ttu-id="fbc9c-147">전송 보안을 사용하여 메시지에 보안 설정</span><span class="sxs-lookup"><span data-stu-id="fbc9c-147">Securing Messages Using Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)
- [<span data-ttu-id="fbc9c-148">메시지 큐에 대한 메시지 보안</span><span class="sxs-lookup"><span data-stu-id="fbc9c-148">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
- [<span data-ttu-id="fbc9c-149">보안 개념</span><span class="sxs-lookup"><span data-stu-id="fbc9c-149">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [<span data-ttu-id="fbc9c-150">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="fbc9c-150">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
