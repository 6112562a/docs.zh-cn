---
title: 基本和摘要式身份验证
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], classes
- Basic authentication
- authentication [.NET Framework], basic
- client authentication, basic
- user authentication, basic
- authentication [.NET Framework], digest
- receiving data, authentication
- client authentication, digest
- Internet, authentication
- digest authentication
- sending data, authentication
- network resources, authentication
- user authentication, digest
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
ms.openlocfilehash: 4f70d2aef3bb064a3df9db9c87671040776332a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089817"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="8376c-102">基本和摘要式身份验证</span><span class="sxs-lookup"><span data-stu-id="8376c-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="8376c-103">基本和摘要式身份验证的 <xref:System.Net> 实现遵循 RFC2617 – HTTP 身份验证：基本和摘要式身份验证（可在[万维网联合会](https://www.w3.org)网站上找到）。</span><span class="sxs-lookup"><span data-stu-id="8376c-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="8376c-104">若要使用基本身份验证和摘要式身份验证，应用程序必须在 <xref:System.Net.WebRequest> 对象的 <xref:System.Net.WebRequest.Credentials%2A> 属性中提供用户名和密码，该对象用于从 Internet 中请求数据，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="8376c-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
WReq.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword);  
```  
  
> [!CAUTION]
>  <span data-ttu-id="8376c-105">使用基本和摘要式身份验证发送的数据不会加密，因此攻击者会看到数据。</span><span class="sxs-lookup"><span data-stu-id="8376c-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="8376c-106">此外，基本身份验证凭据（用户名和密码）是以明文形式发送的，会被截取。</span><span class="sxs-lookup"><span data-stu-id="8376c-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8376c-107">请参阅</span><span class="sxs-lookup"><span data-stu-id="8376c-107">See also</span></span>

- [<span data-ttu-id="8376c-108">NTLM 和 Kerberos 身份验证</span><span class="sxs-lookup"><span data-stu-id="8376c-108">NTLM and Kerberos Authentication</span></span>](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="8376c-109">Internet 身份验证</span><span class="sxs-lookup"><span data-stu-id="8376c-109">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
