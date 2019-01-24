---
title: 篡改
ms.date: 03/30/2017
ms.assetid: 3bad93be-60bb-4f89-96ab-a1c3dc7c0fad
ms.openlocfilehash: 86446778008782c733629ef94e6b192501bee2da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607181"
---
# <a name="tampering"></a><span data-ttu-id="06da1-102">篡改</span><span class="sxs-lookup"><span data-stu-id="06da1-102">Tampering</span></span>
<span data-ttu-id="06da1-103">*篡改*是一条消息或传送的消息时，更改，并且为它的本来目的使用更改后的消息的行为。</span><span class="sxs-lookup"><span data-stu-id="06da1-103">*Tampering* is the act of altering a message, or the delivery of a message, and using the altered message for a purpose other than what it was intended for.</span></span>  
  
## <a name="do-not-disable-ws-addressing"></a><span data-ttu-id="06da1-104">不要禁用 WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="06da1-104">Do Not Disable WS-Addressing</span></span>  
 <span data-ttu-id="06da1-105">WS-Addressing 规范在每条消息中提供了地址标头，从而允许消息接收方验证消息的发送方。</span><span class="sxs-lookup"><span data-stu-id="06da1-105">The WS-Addressing specification provides address headers on each message, allowing a message recipient to verify the sender of the message.</span></span> <span data-ttu-id="06da1-106">将 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 属性设置为 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A> 可禁用此功能。</span><span class="sxs-lookup"><span data-stu-id="06da1-106">You can disable this feature by setting the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="06da1-107">当安全模式设置为“消息”并且禁用了 WS-Addressing 时，攻击者就能获取来自客户端的请求，并将其发送到另一个服务，而第二个服务无法检测该消息是否来自于原客户端。</span><span class="sxs-lookup"><span data-stu-id="06da1-107">When the security mode is set to Message, and if WS-Addressing is disabled, an attacker could take a request from a client and send it to another service, and the second service has no way of detecting that the message came from the original client.</span></span> <span data-ttu-id="06da1-108">实际上，第一个服务在与第二个服务通信时，可假装它是一个客户端。</span><span class="sxs-lookup"><span data-stu-id="06da1-108">In effect, the first service can pretend that it is a client when talking to the second service.</span></span>  
  
 <span data-ttu-id="06da1-109">为了避免这个问题，请不要将 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 属性设置为 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>，并避免使用 <xref:System.ServiceModel.Channels.MessageVersion>，如静态 <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> 属性，它会将 <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> 属性设置为 <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>。</span><span class="sxs-lookup"><span data-stu-id="06da1-109">To mitigate this, never set the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>, and avoid the use of <xref:System.ServiceModel.Channels.MessageVersion>, such as the static <xref:System.ServiceModel.Channels.MessageVersion.Soap12%2A> property, which sets the <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> property to <xref:System.ServiceModel.Channels.AddressingVersion.None%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06da1-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="06da1-110">See also</span></span>
- [<span data-ttu-id="06da1-111">安全注意事项</span><span class="sxs-lookup"><span data-stu-id="06da1-111">Security Considerations</span></span>](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [<span data-ttu-id="06da1-112">信息泄漏</span><span class="sxs-lookup"><span data-stu-id="06da1-112">Information Disclosure</span></span>](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [<span data-ttu-id="06da1-113">特权提升</span><span class="sxs-lookup"><span data-stu-id="06da1-113">Elevation of Privilege</span></span>](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [<span data-ttu-id="06da1-114">拒绝服务</span><span class="sxs-lookup"><span data-stu-id="06da1-114">Denial of Service</span></span>](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [<span data-ttu-id="06da1-115">不支持的方案</span><span class="sxs-lookup"><span data-stu-id="06da1-115">Unsupported Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
- [<span data-ttu-id="06da1-116">重放攻击</span><span class="sxs-lookup"><span data-stu-id="06da1-116">Replay Attacks</span></span>](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
