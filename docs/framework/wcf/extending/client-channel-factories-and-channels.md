---
title: 客户端：通道工厂和通道
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 25e2c034d1fefc7728667231040a97c3aeecabbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185692"
---
# <a name="client-channel-factories-and-channels"></a><span data-ttu-id="32876-102">客户端：通道工厂和通道</span><span class="sxs-lookup"><span data-stu-id="32876-102">Client: Channel Factories and Channels</span></span>
<span data-ttu-id="32876-103">本主题介绍通道工厂和通道的创建。</span><span class="sxs-lookup"><span data-stu-id="32876-103">This topic discusses the creation of channel factories and channels.</span></span>  
  
## <a name="channel-factories-and-channels"></a><span data-ttu-id="32876-104">通道工厂和通道</span><span class="sxs-lookup"><span data-stu-id="32876-104">Channel Factories and Channels</span></span>  
 <span data-ttu-id="32876-105">通道工厂负责创建通道。</span><span class="sxs-lookup"><span data-stu-id="32876-105">Channel factories are responsible for creating channels.</span></span> <span data-ttu-id="32876-106">由通道工厂创建的通道用于发送消息。</span><span class="sxs-lookup"><span data-stu-id="32876-106">Channels created by channel factories are used for sending messages.</span></span> <span data-ttu-id="32876-107">这些通道负责获取来自上一层的消息，对消息进行必要的处理，然后将消息发送到下一层。</span><span class="sxs-lookup"><span data-stu-id="32876-107">These channels are responsible for getting the message from the layer above, performing whatever processing is necessary, then sending the message to the layer below.</span></span> <span data-ttu-id="32876-108">下图演示此过程。</span><span class="sxs-lookup"><span data-stu-id="32876-108">The following graphic illustrates this process.</span></span>  
  
 <span data-ttu-id="32876-109">![客户端工厂和通道](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span><span class="sxs-lookup"><span data-stu-id="32876-109">![Client Factories and Channels](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")</span></span>  
<span data-ttu-id="32876-110">通道工厂创建通道。</span><span class="sxs-lookup"><span data-stu-id="32876-110">A channel factory creates channels.</span></span>  
  
 <span data-ttu-id="32876-111">通道工厂在关闭时负责关闭其创建的但尚未关闭的所有通道。</span><span class="sxs-lookup"><span data-stu-id="32876-111">When closed, channel factories are responsible for closing any channels they created that are not yet closed.</span></span> <span data-ttu-id="32876-112">请注意，此处的模型是非对称的，原因是当通道侦听器关闭时，它仅停止接受新通道，而使现有通道保持打开状态以便继续接收消息。</span><span class="sxs-lookup"><span data-stu-id="32876-112">Note that the model is asymmetric here because when a channel listener is closed, it only stops accepting new channels but leaves existing channels open so that they can continue receiving messages.</span></span>  
  
 <span data-ttu-id="32876-113">WCF 为此过程提供基类帮助程序。</span><span class="sxs-lookup"><span data-stu-id="32876-113">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="32876-114">（有关本主题中讨论的通道帮助器类的图表，请参阅[通道模型概述](channel-model-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="32876-114">(For a diagram of the channel helper classes discussed in this topic, see [Channel Model Overview](channel-model-overview.md).)</span></span>  
  
- <span data-ttu-id="32876-115">该<xref:System.ServiceModel.Channels.CommunicationObject>类实现<xref:System.ServiceModel.ICommunicationObject>并强制执行[开发通道](developing-channels.md)步骤 2 中描述的状态机。</span><span class="sxs-lookup"><span data-stu-id="32876-115">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>  
  
- <span data-ttu-id="32876-116"><xref:System.ServiceModel.Channels.ChannelManagerBase> 类实现 <xref:System.ServiceModel.Channels.CommunicationObject> 并为 <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> 和 <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType> 提供统一的基类。</span><span class="sxs-lookup"><span data-stu-id="32876-116">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> and <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="32876-117"><xref:System.ServiceModel.Channels.ChannelManagerBase> 类与 <xref:System.ServiceModel.Channels.ChannelBase>（用来实现 <xref:System.ServiceModel.Channels.IChannel> 的基类）结合使用。</span><span class="sxs-lookup"><span data-stu-id="32876-117">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>
  
- <span data-ttu-id="32876-118">类<xref:System.ServiceModel.Channels.ChannelFactoryBase>实现<xref:System.ServiceModel.Channels.ChannelManagerBase>并<xref:System.ServiceModel.Channels.IChannelFactory>合并`CreateChannel`重载到一个`OnCreateChannel`抽象方法中。</span><span class="sxs-lookup"><span data-stu-id="32876-118">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>
  
- <span data-ttu-id="32876-119"><xref:System.ServiceModel.Channels.ChannelListenerBase> 类实现 <xref:System.ServiceModel.Channels.IChannelListener>。</span><span class="sxs-lookup"><span data-stu-id="32876-119">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="32876-120">它负责执行基本状态管理。</span><span class="sxs-lookup"><span data-stu-id="32876-120">It takes care of basic state management.</span></span>
  
 <span data-ttu-id="32876-121">以下讨论基于[传输：UDP](../samples/transport-udp.md)示例。</span><span class="sxs-lookup"><span data-stu-id="32876-121">The following discussion is based upon the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>  
  
### <a name="creating-a-channel-factory"></a><span data-ttu-id="32876-122">创建通道工厂</span><span class="sxs-lookup"><span data-stu-id="32876-122">Creating a Channel Factory</span></span>  
 <span data-ttu-id="32876-123">`UdpChannelFactory` 派生自 <xref:System.ServiceModel.Channels.ChannelFactoryBase>。</span><span class="sxs-lookup"><span data-stu-id="32876-123">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="32876-124">该示例重写 <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> 以提供对消息编码器的消息版本的访问。</span><span class="sxs-lookup"><span data-stu-id="32876-124">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="32876-125">该示例还重写 <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> 以在状态机转变时拆开 <xref:System.ServiceModel.Channels.BufferManager> 的实例。</span><span class="sxs-lookup"><span data-stu-id="32876-125">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> to tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="32876-126">UDP 输出通道</span><span class="sxs-lookup"><span data-stu-id="32876-126">The UDP Output Channel</span></span>  
 <span data-ttu-id="32876-127">`UdpOutputChannel` 实现 <xref:System.ServiceModel.Channels.IOutputChannel>。</span><span class="sxs-lookup"><span data-stu-id="32876-127">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="32876-128">构造函数对自变量进行验证，并基于传入的 <xref:System.Net.EndPoint> 来构造目标 <xref:System.ServiceModel.EndpointAddress> 对象。</span><span class="sxs-lookup"><span data-stu-id="32876-128">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
 <span data-ttu-id="32876-129">重写 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> 将创建用于向此 <xref:System.Net.EndPoint> 发送消息的套接字。</span><span class="sxs-lookup"><span data-stu-id="32876-129">The override of <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> creates a socket that is used to send messages to this <xref:System.Net.EndPoint>.</span></span>  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 <span data-ttu-id="32876-130">通道可以正常关闭或非正常关闭。</span><span class="sxs-lookup"><span data-stu-id="32876-130">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="32876-131">如果通道正常关闭，则套接字也将关闭，并调用基类 `OnClose` 方法。</span><span class="sxs-lookup"><span data-stu-id="32876-131">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="32876-132">如果引发异常，则基础结构将调用 `Abort` 以确保清理该通道。</span><span class="sxs-lookup"><span data-stu-id="32876-132">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 <span data-ttu-id="32876-133">实现`Send()``BeginSend()`/`EndSend()`和 。</span><span class="sxs-lookup"><span data-stu-id="32876-133">Implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="32876-134">这将分解为两个主要部分。</span><span class="sxs-lookup"><span data-stu-id="32876-134">This breaks down into two main sections.</span></span> <span data-ttu-id="32876-135">首先，将消息序列化为字节数组：</span><span class="sxs-lookup"><span data-stu-id="32876-135">First serialize the message into a byte array:</span></span>  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="32876-136">然后，在网络上发送生成的数据：</span><span class="sxs-lookup"><span data-stu-id="32876-136">Then send the resulting data on the wire:</span></span>  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,
  messageBuffer.Offset,
  messageBuffer.Count,
  SocketFlags.None,
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="32876-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="32876-137">See also</span></span>

- [<span data-ttu-id="32876-138">开发通道</span><span class="sxs-lookup"><span data-stu-id="32876-138">Developing Channels</span></span>](developing-channels.md)
