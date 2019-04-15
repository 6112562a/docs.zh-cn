---
title: IPv6 自动配置
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: 4dc7a148364c9f96a0f6c68c8af71f7668e797b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170056"
---
# <a name="ipv6-auto-configuration"></a><span data-ttu-id="4b1b1-102">IPv6 自动配置</span><span class="sxs-lookup"><span data-stu-id="4b1b1-102">IPv6 Auto-Configuration</span></span>
<span data-ttu-id="4b1b1-103">IPv6 的一个重要目标是支持节点即插即用。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-103">One important goal for IPv6 is to support node Plug and Play.</span></span> <span data-ttu-id="4b1b1-104">也就是说，可以将节点插入 IPv6 网络，让其自动进行配置，无需任何人为干预。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-104">That is, it should be possible to plug a node into an IPv6 network and have it automatically configured without any human intervention.</span></span>  
  
## <a name="type-of-auto-configuration"></a><span data-ttu-id="4b1b1-105">自动配置类型</span><span class="sxs-lookup"><span data-stu-id="4b1b1-105">Type of Auto-Configuration</span></span>  
 <span data-ttu-id="4b1b1-106">IPv6 支持以下自动配置类型：</span><span class="sxs-lookup"><span data-stu-id="4b1b1-106">IPv6 supports the following types of auto-configuration:</span></span>  
  
-   <span data-ttu-id="4b1b1-107">有状态自动配置。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-107">**Stateful auto-configuration**.</span></span> <span data-ttu-id="4b1b1-108">这种类型的配置需要一定程度的人为干预，因其需要 IPv6 动态主机配置协议 (DHCPv6) 服务器来安装和管理节点。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-108">This type of configuration requires a certain level of human intervention because it needs a Dynamic Host Configuration Protocol for IPv6 (DHCPv6) server for the installation and administration of the nodes.</span></span> <span data-ttu-id="4b1b1-109">DHCPv6 服务器保存向其提供配置信息的节点列表。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-109">The DHCPv6 server keeps a list of nodes to which it supplies configuration information.</span></span> <span data-ttu-id="4b1b1-110">它还维护状态信息，这样服务器知道每个地址的使用时间，以及何时可用于重新分配。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-110">It also maintains state information so the server knows how long each address is in use, and when it might be available for reassignment.</span></span>  
  
-   <span data-ttu-id="4b1b1-111">无状态自动配置。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-111">**Stateless auto-configuration**.</span></span> <span data-ttu-id="4b1b1-112">这种配置类型适用于小型组织和个人。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-112">This type of configuration is suitable for small organizations and individuals.</span></span> <span data-ttu-id="4b1b1-113">这种情况下，每个主机通过接收的路由器播发的内容确定其地址。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-113">In this case, each host determines its addresses from the contents of received router advertisements.</span></span> <span data-ttu-id="4b1b1-114">使用 IEEE EUI-64 标准来定义地址的网络 ID 部分，可以合理地假定链接上主机地址的唯一性。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-114">Using the IEEE EUI-64 standard to define the network ID portion of the address, it is reasonable to assume the uniqueness of the host address on the link.</span></span>  
  
 <span data-ttu-id="4b1b1-115">无论如何确定地址，节点必须验证可能的地址对于本地链接是否唯一。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-115">Regardless of how the address is determined, the node must verify that its potential address is unique to the local link.</span></span> <span data-ttu-id="4b1b1-116">通过向可能的地址发送邻居请求消息可完成此操作。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-116">This is done by sending a neighbor solicitation message to the potential address.</span></span> <span data-ttu-id="4b1b1-117">如果节点收到任何响应，就知道该地址已在使用，并且必须确定其他地址。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-117">If the node receives any response, it knows that the address is already in use and must determine another address.</span></span>  
  
## <a name="ipv6-mobility"></a><span data-ttu-id="4b1b1-118">IPv6 移动性</span><span class="sxs-lookup"><span data-stu-id="4b1b1-118">IPv6 Mobility</span></span>  
 <span data-ttu-id="4b1b1-119">移动设备的广泛应用催生了新的要求：设备必须能够随意改变 IPv6 Internet 上的位置，但是仍然保持现有连接。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-119">The proliferation of mobile devices has introduced a new requirement: A device must be able to arbitrarily change locations on the IPv6 Internet and still maintain existing connections.</span></span> <span data-ttu-id="4b1b1-120">为实现此功能，向移动节点分配一个始终可以到达的主地址。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-120">To provide this functionality, a mobile node is assigned a home address at which it can always be reached.</span></span> <span data-ttu-id="4b1b1-121">当移动节点在其中时，它连接到主链接并使用其主地址。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-121">When the mobile node is at home, it connects to the home link and uses its home address.</span></span> <span data-ttu-id="4b1b1-122">当移动节点离开时，主代理（通常是路由器）在移动节点和其正与之通信的节点之间中继消息。</span><span class="sxs-lookup"><span data-stu-id="4b1b1-122">When the mobile node is away from home, a home agent, which is usually a router, relays messages between the mobile node and nodes with which it is communicating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b1b1-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="4b1b1-123">See also</span></span>

- [<span data-ttu-id="4b1b1-124">Internet 协议版本 6</span><span class="sxs-lookup"><span data-stu-id="4b1b1-124">Internet Protocol Version 6</span></span>](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [<span data-ttu-id="4b1b1-125">套接字</span><span class="sxs-lookup"><span data-stu-id="4b1b1-125">Sockets</span></span>](../../../docs/framework/network-programming/sockets.md)
