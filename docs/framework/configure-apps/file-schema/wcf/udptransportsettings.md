---
title: <udpTransportSettings>
ms.date: 03/30/2017
ms.assetid: 842d92e9-6199-4ec5-b2d1-58533054e1f0
ms.openlocfilehash: bb2ec84caa79f33e1e469592d0eca63d8f461dac
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854859"
---
# <a name="udptransportsettings"></a><span data-ttu-id="cd2dd-101">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="cd2dd-101">\<udpTransportSettings></span></span>
<span data-ttu-id="cd2dd-102">此配置元素显示[ \<udpDiscoveryEndpoint >](udpdiscoveryendpoint.md)的 UDP 传输设置。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-102">This configuration element exposes UDP transport settings for [\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md).</span></span>  
  
<span data-ttu-id="cd2dd-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cd2dd-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cd2dd-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cd2dd-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cd2dd-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="cd2dd-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="cd2dd-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<udpDiscoveryEndpoint >** ](udpdiscoveryendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="cd2dd-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<udpDiscoveryEndpoint>**](udpdiscoveryendpoint.md)</span></span>\
<span data-ttu-id="cd2dd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<updTransportSettings >**</span><span class="sxs-lookup"><span data-stu-id="cd2dd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<updTransportSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd2dd-108">语法</span><span class="sxs-lookup"><span data-stu-id="cd2dd-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint>
        <updTransportSettings duplicateMessageHistoryLength="Integer"
                              maxBufferPoolSize="Integer"
                              maxMulticastRetransmitCount="Integer"
                              maxPendingMessageCount="Integer"
                              maxReceivedMessageSize="Integer"
                              maxUnicastRetransmitCount="Integer"
                              multicastInterfaceId="String"
                              socketReceiveBufferSize="Integer"
                              timeToLive="Integer" />
      </standardEndpoint>
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd2dd-109">特性和元素</span><span class="sxs-lookup"><span data-stu-id="cd2dd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cd2dd-110">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd2dd-111">特性</span><span class="sxs-lookup"><span data-stu-id="cd2dd-111">Attributes</span></span>  
  
|<span data-ttu-id="cd2dd-112">特性</span><span class="sxs-lookup"><span data-stu-id="cd2dd-112">Attribute</span></span>|<span data-ttu-id="cd2dd-113">描述</span><span class="sxs-lookup"><span data-stu-id="cd2dd-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd2dd-114">duplicateMessageHistoryLength</span><span class="sxs-lookup"><span data-stu-id="cd2dd-114">duplicateMessageHistoryLength</span></span>|<span data-ttu-id="cd2dd-115">一个整数，指定传输用于标识重复消息的最大消息哈希数。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-115">An integer that specifies the maximum number of message hashes used by the transport for identifying duplicate messages.</span></span>  <span data-ttu-id="cd2dd-116">将在 TransportManager 级别进行重复检测。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-116">Duplicate detection will be done at the TransportManager level.</span></span> <span data-ttu-id="cd2dd-117">将此属性设置为 0 即可禁用重复检测。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-117">Setting this property to 0 disables duplicate detection.</span></span><br /><br /> <span data-ttu-id="cd2dd-118">系统管理员或开发人员可以使用此特性关闭重复消息检测算法。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-118">This attribute allows system administrators or developers to turn off duplicate message detection algorithms.</span></span> <span data-ttu-id="cd2dd-119">如果您希望实现自己的重复检测算法，可能需要这一功能。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-119">This may be desirable if you want to implement your own duplicate detection algorithm.</span></span><br /><br /> <span data-ttu-id="cd2dd-120">默认值为 4112。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-120">The default is 4112.</span></span>|  
|<span data-ttu-id="cd2dd-121">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="cd2dd-121">maxBufferPoolSize</span></span>|<span data-ttu-id="cd2dd-122">一个整数，指定传输使用的任何缓冲池的最大大小。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-122">An integer that specifies the maximum size of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="cd2dd-123">maxMulticastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="cd2dd-123">maxMulticastRetransmitCount</span></span>|<span data-ttu-id="cd2dd-124">一个整数，指定应重新传输消息的最大次数（包括第一次发送）。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-124">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span><br /><br /> <span data-ttu-id="cd2dd-125">默认值为 2。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-125">The default is 2.</span></span>|  
|<span data-ttu-id="cd2dd-126">maxPendingMessageCount</span><span class="sxs-lookup"><span data-stu-id="cd2dd-126">maxPendingMessageCount</span></span>|<span data-ttu-id="cd2dd-127">一个整数，指定已经接收但尚未从单个通道实例的 InputQueue 中移除的最大消息数。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-127">An integer that specifies the maximum number of messages that have been received but not yet removed from the InputQueue for an individual channel instance.</span></span>  <span data-ttu-id="cd2dd-128">如果 InputQueue 已达到挂起消息计数上限，则将丢弃消息。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-128">If the InputQueue has hit its pending message count limit, the message will be dropped.</span></span><br /><br /> <span data-ttu-id="cd2dd-129">默认值为 32。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-129">The default is 32.</span></span>|  
|<span data-ttu-id="cd2dd-130">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="cd2dd-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="cd2dd-131">一个整数，指定绑定可处理的消息的最大大小。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-131">An integer that specifies the maximum size for a message that can be processed by the binding.</span></span><br /><br /> <span data-ttu-id="cd2dd-132">默认值为 65507。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-132">The default value is 65507.</span></span>|  
|<span data-ttu-id="cd2dd-133">maxUnicastRetransmitCount</span><span class="sxs-lookup"><span data-stu-id="cd2dd-133">maxUnicastRetransmitCount</span></span>|<span data-ttu-id="cd2dd-134">一个整数，指定应重新传输消息的最大次数（包括第一次发送）。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-134">An integer that specifies the maximum number of times the message should be retransmitted (in addition to the first send).</span></span>  <span data-ttu-id="cd2dd-135">如果将消息发送到单播地址，并且收到的响应消息中带有相应的 RelatesTo 标头，重新传输可能会提前终止（在达到配置的重新传输次数之前）。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-135">If the message is sent to a unicast address and a response message is received with a corresponding RelatesTo header, then retransmission may terminate early (before retransmitting the configured number of times).</span></span><br /><br /> <span data-ttu-id="cd2dd-136">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-136">The default value is 1.</span></span>|  
|<span data-ttu-id="cd2dd-137">multicastInterfaceId</span><span class="sxs-lookup"><span data-stu-id="cd2dd-137">multicastInterfaceId</span></span>|<span data-ttu-id="cd2dd-138">一个字符串，唯一标识在多宿主计算机上发送和接收多播流量时应使用的网络适配器。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-138">A string that uniquely identifies the network adapter that should be used when sending and receiving multicast traffic on multi-homed machines.</span></span> <span data-ttu-id="cd2dd-139">在运行时，传输将使用此特性值来查找接口索引，然后使用该索引设置 `IP_MULTICAST_IF` 和 `IPV6_MULTICAST_IF` 套接字选项。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-139">At runtime, the transport will use this attribute value to lookup the interface index, which is then used to set the `IP_MULTICAST_IF` and `IPV6_MULTICAST_IF` socket options.</span></span>  <span data-ttu-id="cd2dd-140">加入多播组时将使用相同的接口索引（如果适用）。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-140">The same interface index will be used when joining a multicast group, if applicable.</span></span><br /><br /> <span data-ttu-id="cd2dd-141">默认值为 `null`。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-141">The default value is `null`.</span></span>|  
|<span data-ttu-id="cd2dd-142">socketReceiveBufferSize</span><span class="sxs-lookup"><span data-stu-id="cd2dd-142">socketReceiveBufferSize</span></span>|<span data-ttu-id="cd2dd-143">一个整数，指定基础 WinSock 套接字上接收缓冲区的大小。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-143">An integer that specifies the receive buffer size on the underlying WinSock socket.</span></span><br /><br /> <span data-ttu-id="cd2dd-144">接收通道的用户可以对绑定使用此特性，以控制系统在接收数据时的行为。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-144">A user of a receiving channel can use this attribute on the Binding to control how the system behaves when it receives data.</span></span>  <span data-ttu-id="cd2dd-145">例如，假定应用程序使用入站 WCF 消息时达到了最大阈值，对此特性使用较高的值将允许消息在等待应用程序处理时在 WinSock 缓冲区中堆叠。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-145">For example, given an application that is consuming inbound WCF messages at the maximum threshold, using a higher value for this attribute would allow messages to stack up in the WinSock buffer while waiting for the application to be able to process them.</span></span>  <span data-ttu-id="cd2dd-146">在同样的情况下，使用较低的值将导致消息被丢弃。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-146">Using a lower value in the same situation would result in messages getting dropped.</span></span> <span data-ttu-id="cd2dd-147">此属性公开基础 WinSock `SO_RCVBUF`套接字选项。此属性值必须至少为的`maxReceivedMessageSize`大小。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-147">This attribute exposes the underlying WinSock `SO_RCVBUF` socket option.This attribute value must be at least the size of `maxReceivedMessageSize`.</span></span>   <span data-ttu-id="cd2dd-148">如果将其设置为小于的`maxReceivedMessageSize`值，则会导致运行时异常。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-148">Setting it to a value smaller than the `maxReceivedMessageSize` will result in a runtime exception.</span></span><br /><br /> <span data-ttu-id="cd2dd-149">默认值为 65536。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-149">The default value is 65536.</span></span>|  
|<span data-ttu-id="cd2dd-150">timeToLive</span><span class="sxs-lookup"><span data-stu-id="cd2dd-150">timeToLive</span></span>|<span data-ttu-id="cd2dd-151">一个整数，指定多播数据包可以遍历的网络段跃点数。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-151">An integer that specifies the number of network segment hops that a multicast packet can traverse.</span></span>  <span data-ttu-id="cd2dd-152">此特性公开与 `IP_MULTICAST_TTL` 和 `IP_TTL` 套接字选项关联的功能。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-152">This attribute exposes the functionality associated with the `IP_MULTICAST_TTL` and `IP_TTL` socket options.</span></span><br /><br /> <span data-ttu-id="cd2dd-153">默认值为 1。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-153">The default value is 1.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd2dd-154">子元素</span><span class="sxs-lookup"><span data-stu-id="cd2dd-154">Child Elements</span></span>  
 <span data-ttu-id="cd2dd-155">无。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd2dd-156">父元素</span><span class="sxs-lookup"><span data-stu-id="cd2dd-156">Parent Elements</span></span>  
  
|<span data-ttu-id="cd2dd-157">元素</span><span class="sxs-lookup"><span data-stu-id="cd2dd-157">Element</span></span>|<span data-ttu-id="cd2dd-158">描述</span><span class="sxs-lookup"><span data-stu-id="cd2dd-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd2dd-159">\<udpDiscoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="cd2dd-159">\<udpDiscoveryEndpoint></span></span>](udpdiscoveryendpoint.md)|<span data-ttu-id="cd2dd-160">具有固定发现协定和 UDP 传输绑定的标准终结点。</span><span class="sxs-lookup"><span data-stu-id="cd2dd-160">A standard endpoint that has fixed discovery contract and UDP transport binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd2dd-161">请参阅</span><span class="sxs-lookup"><span data-stu-id="cd2dd-161">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpTransportSettings>
