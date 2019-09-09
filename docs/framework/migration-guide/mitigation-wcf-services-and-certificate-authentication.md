---
title: 缓解：WCF 服务和证书身份验证
ms.date: 03/30/2017
ms.assetid: ef19c91a-b9df-4bf0-a28e-eb1e99c4bc95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fcb4de714c8a0f1f2c61f3a12815a5a0a3ddc83
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789819"
---
# <a name="mitigation-wcf-services-and-certificate-authentication"></a><span data-ttu-id="44470-102">缓解：WCF 服务和证书身份验证</span><span class="sxs-lookup"><span data-stu-id="44470-102">Mitigation: WCF Services and Certificate Authentication</span></span>

<span data-ttu-id="44470-103">.NET Framework 4.6 向 WCF SSL 协议默认列表添加了 TLS 1.1 和 TLS 1.2。</span><span class="sxs-lookup"><span data-stu-id="44470-103">The .NET Framework 4.6 adds TLS 1.1 and TLS 1.2 to the WCF SSL protocol default list.</span></span> <span data-ttu-id="44470-104">客户端和服务器计算机都安装了 .NET Framework 4.6 或更高版本时，TLS 1.2 用于协商。</span><span class="sxs-lookup"><span data-stu-id="44470-104">When both client and server machines have  the .NET Framework 4.6 or later installed, TLS 1.2 is used for negotiation.</span></span>

## <a name="impact"></a><span data-ttu-id="44470-105">影响</span><span class="sxs-lookup"><span data-stu-id="44470-105">Impact</span></span>

<span data-ttu-id="44470-106">TLS 1.2 不支持 MD5 证书身份验证。</span><span class="sxs-lookup"><span data-stu-id="44470-106">TLS 1.2 does not support MD5 certificate authentication.</span></span> <span data-ttu-id="44470-107">因此，如果客户使用的 SSL 证书对哈希算法使用 MD5，WCF 客户端就无法连接 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="44470-107">As a result, if a customer uses an SSL  certificate which uses MD5 for the hash algorithm, the WCF client fails to connect to the WCF service.</span></span> <span data-ttu-id="44470-108">有关详细信息，请参阅[缓解：WCF 服务和证书身份验证](mitigation-wcf-services-and-certificate-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="44470-108">For more information, see [Mitigation: WCF Services and Certificate Authentication](mitigation-wcf-services-and-certificate-authentication.md).</span></span>

## <a name="mitigation"></a><span data-ttu-id="44470-109">缓解</span><span class="sxs-lookup"><span data-stu-id="44470-109">Mitigation</span></span>

<span data-ttu-id="44470-110">可以通过执行下列任一操作来解决此问题，以便 WCF 客户端可以连接 WCF 服务器：</span><span class="sxs-lookup"><span data-stu-id="44470-110">You can work around this issue so that a WCF client can connect to a WCF server by doing any of the following:</span></span>

- <span data-ttu-id="44470-111">将证书更新为不使用 MD5 算法。</span><span class="sxs-lookup"><span data-stu-id="44470-111">Update the certificate to not use the MD5 algorithm.</span></span> <span data-ttu-id="44470-112">建议采用此解决方案。</span><span class="sxs-lookup"><span data-stu-id="44470-112">This is the recommended solution.</span></span>

- <span data-ttu-id="44470-113">如果未在源代码中动态配置绑定，将应用程序的配置文件更新为使用 TLS 1.1 或更低版本的协议。</span><span class="sxs-lookup"><span data-stu-id="44470-113">If the binding is not dynamically configured in source code, update the application's configuration file to use TLS 1.1 or an earlier version of the protocol.</span></span> <span data-ttu-id="44470-114">这样便可以继续将证书和 MD5 哈希算法结合使用。</span><span class="sxs-lookup"><span data-stu-id="44470-114">This allows you to continue to use a certificate with the MD5 hash algorithm.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="44470-115">不建议采用此解决方法，因为使用 MD5 哈希算法的证书被视为不安全。</span><span class="sxs-lookup"><span data-stu-id="44470-115">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

  <span data-ttu-id="44470-116">下面的配置文件就采用了此解决方法：</span><span class="sxs-lookup"><span data-stu-id="44470-116">The following configuration file does this:</span></span>

  ```xml
  <configuration>
      <system.serviceModel>
          <bindings>
              <netTcpBinding>
                  <binding>
                      <security mode= "None|Transport|Message|TransportWithMessageCredential" >
                          <transport clientCredentialType="None|Windows|Certificate"
                                              protectionLevel="None|Sign|EncryptAndSign"
                                              sslProtocols="Ssl3|Tls1|Tls11">
                          </transport>
                      </security>
                  </binding>
              </netTcpBinding>
          </bindings>
      </system.ServiceModel>
  </configuration>
  ```

- <span data-ttu-id="44470-117">如果在源代码中动态配置了绑定，将 <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> 属性更新为使用 TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) 或源代码中的早期版本协议。</span><span class="sxs-lookup"><span data-stu-id="44470-117">If the binding is dynamically configured in source code, update the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property to use TLS 1.1 (<xref:System.Security.Authentication.SslProtocols.Tls11?displayProperty=nameWithType>) or an  earlier version of the protocol in the source code.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="44470-118">不建议采用此解决方法，因为使用 MD5 哈希算法的证书被视为不安全。</span><span class="sxs-lookup"><span data-stu-id="44470-118">This workaround is not recommended, since a certificate with the MD5 hash algorithm is considered insecure.</span></span>

## <a name="see-also"></a><span data-ttu-id="44470-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="44470-119">See also</span></span>

- [<span data-ttu-id="44470-120">运行时更改</span><span class="sxs-lookup"><span data-stu-id="44470-120">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
