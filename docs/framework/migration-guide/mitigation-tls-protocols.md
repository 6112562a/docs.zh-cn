---
title: 缓解：TLS 协议
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abfbea052072f0b90c9d018b520b67878d235701
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506805"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="0db6f-102">缓解：TLS 协议</span><span class="sxs-lookup"><span data-stu-id="0db6f-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="0db6f-103">从 .NET Framework 4.6 开始，允许 <xref:System.Net.ServicePointManager?displayProperty=nameWithType> 和 <xref:System.Net.Security.SslStream?displayProperty=nameWithType> 类使用以下三种协议之一：Tls1.0、Tls1.1 或 Tls1.2。</span><span class="sxs-lookup"><span data-stu-id="0db6f-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="0db6f-104">不支持 SSL3.0 协议和 RC4 密码。</span><span class="sxs-lookup"><span data-stu-id="0db6f-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="0db6f-105">影响</span><span class="sxs-lookup"><span data-stu-id="0db6f-105">Impact</span></span>  
 <span data-ttu-id="0db6f-106">此更改会影响：</span><span class="sxs-lookup"><span data-stu-id="0db6f-106">This change affects:</span></span>  
  
-   <span data-ttu-id="0db6f-107">使用 SSL 与 HTTPS 服务器或与使用以下任何类型的套接字对话的任何应用：<xref:System.Net.Http.HttpClient>、<xref:System.Net.HttpWebRequest>、<xref:System.Net.FtpWebRequest>、<xref:System.Net.Mail.SmtpClient> 和 <xref:System.Net.Security.SslStream>。</span><span class="sxs-lookup"><span data-stu-id="0db6f-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
-   <span data-ttu-id="0db6f-108">不能升级以支持 Tls1.0、Tls1.1 或 Tls 1.2 的任意服务器端应用。</span><span class="sxs-lookup"><span data-stu-id="0db6f-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="0db6f-109">缓解</span><span class="sxs-lookup"><span data-stu-id="0db6f-109">Mitigation</span></span>  
 <span data-ttu-id="0db6f-110">建议的缓解操作是将服务器端应用升级到 Tls1.0、Tls1.1 或 Tls 1.2。</span><span class="sxs-lookup"><span data-stu-id="0db6f-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="0db6f-111">如果这不可行或者如果客户端应用被中断，则可以使用 <xref:System.AppContext> 类并采用如两种方式中的一种来选择退出此功能：</span><span class="sxs-lookup"><span data-stu-id="0db6f-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
-   <span data-ttu-id="0db6f-112">以编程方式使用如下代码段：</span><span class="sxs-lookup"><span data-stu-id="0db6f-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="0db6f-113">由于 <xref:System.Net.ServicePointManager> 对象仅初始化一次，因此定义这些兼容性设置必须是应用程序执行的第一件事。</span><span class="sxs-lookup"><span data-stu-id="0db6f-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
-   <span data-ttu-id="0db6f-114">在 app.config 文件的 [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 部分中添加下面的代码行：</span><span class="sxs-lookup"><span data-stu-id="0db6f-114">By adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="0db6f-115">但请注意，不建议选择退出默认行为，因为这会导致应用程序不太安全。</span><span class="sxs-lookup"><span data-stu-id="0db6f-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db6f-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="0db6f-116">See also</span></span>
- [<span data-ttu-id="0db6f-117">重定目标更改</span><span class="sxs-lookup"><span data-stu-id="0db6f-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
