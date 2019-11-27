---
title: 可靠消息传送协议版本 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 9320787317131f42c4a82c6114a16fdea87567f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283310"
---
# <a name="reliable-messaging-protocol-version-11"></a><span data-ttu-id="ec4e7-102">可靠消息传送协议版本 1.1</span><span class="sxs-lookup"><span data-stu-id="ec4e7-102">Reliable Messaging Protocol version 1.1</span></span>

<span data-ttu-id="ec4e7-103">本主题介绍了使用 HTTP 传输进行互操作所需的 WS-RELIABLEMESSAGING 2007 （版本1.1）协议的 Windows Communication Foundation （WCF）实现的详细信息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-ReliableMessaging February 2007 (version 1.1) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="ec4e7-104">WCF 遵循了 WS-RELIABLEMESSAGING 规范以及本主题中所述的约束和说明。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-104">WCF follows the WS-ReliableMessaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="ec4e7-105">请注意，从 .NET Framework 3.5 开始实现 WS-RELIABLEMESSAGING 版本1.1 协议。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-105">Note that the WS-ReliableMessaging version 1.1 protocol is implemented starting with .NET Framework 3.5.</span></span>

<span data-ttu-id="ec4e7-106">Ws-reliablemessaging 2007 年2月版协议是在 WCF 中由 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>实现的。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-106">The WS-ReliableMessaging February 2007 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="ec4e7-107">为方便起见，本主题使用以下角色：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="ec4e7-108">发起方：启动 WS-Reliable Message 序列创建的客户端。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-108">Initiator: The client that initiates WS-Reliable Message sequence creation.</span></span>

- <span data-ttu-id="ec4e7-109">响应方：接收发起方请求的服务。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-109">Responder: The service that receives the initiator's requests.</span></span>

 <span data-ttu-id="ec4e7-110">本文档使用下表中的前缀和命名空间。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="ec4e7-111">前缀</span><span class="sxs-lookup"><span data-stu-id="ec4e7-111">Prefix</span></span>|<span data-ttu-id="ec4e7-112">命名空间</span><span class="sxs-lookup"><span data-stu-id="ec4e7-112">Namespace</span></span>|
|-|-|
|<span data-ttu-id="ec4e7-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="ec4e7-113">wsrm</span></span>|http://docs.oasis-open.org/ws-rx/wsrm/200702|
|<span data-ttu-id="ec4e7-114">netrm</span><span class="sxs-lookup"><span data-stu-id="ec4e7-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|
|<span data-ttu-id="ec4e7-115">s</span><span class="sxs-lookup"><span data-stu-id="ec4e7-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|
|<span data-ttu-id="ec4e7-116">wsa</span><span class="sxs-lookup"><span data-stu-id="ec4e7-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|<span data-ttu-id="ec4e7-117">wsse</span><span class="sxs-lookup"><span data-stu-id="ec4e7-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|
|<span data-ttu-id="ec4e7-118">wsrmp</span><span class="sxs-lookup"><span data-stu-id="ec4e7-118">wsrmp</span></span>|http://docs.oasis-open.org/ws-rx/wsrmp/200702|
|<span data-ttu-id="ec4e7-119">netrmp</span><span class="sxs-lookup"><span data-stu-id="ec4e7-119">netrmp</span></span>|http://schemas.microsoft.com/ws-rx/wsrmp/200702|
|<span data-ttu-id="ec4e7-120">wsp</span><span class="sxs-lookup"><span data-stu-id="ec4e7-120">wsp</span></span>|<span data-ttu-id="ec4e7-121">（WS-Policy 1.2 或 WS-Policy 1.5）</span><span class="sxs-lookup"><span data-stu-id="ec4e7-121">(Either WS-Policy 1.2 or WS-Policy 1.5)</span></span>|

## <a name="messaging"></a><span data-ttu-id="ec4e7-122">消息</span><span class="sxs-lookup"><span data-stu-id="ec4e7-122">Messaging</span></span>

### <a name="sequence-creation"></a><span data-ttu-id="ec4e7-123">序列创建</span><span class="sxs-lookup"><span data-stu-id="ec4e7-123">Sequence Creation</span></span>

<span data-ttu-id="ec4e7-124">WCF 实现 `CreateSequence` 和 `CreateSequenceResponse` 消息以建立可靠的消息传递序列。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-124">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable messaging sequence.</span></span> <span data-ttu-id="ec4e7-125">适用以下约束：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-125">The following constraints apply:</span></span>

- <span data-ttu-id="ec4e7-126">B1101： WCF 发起方使用与 `CreateSequence` 消息 `ReplyTo`、`AcksTo` 和 `Offer/Endpoint`相同的终结点引用。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-126">B1101: The WCF Initiator uses the same endpoint reference as the `CreateSequence` message’s `ReplyTo`, `AcksTo` and `Offer/Endpoint`.</span></span>

- <span data-ttu-id="ec4e7-127">R1102：`AcksTo` 消息中的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 终结点引用必须具有包含相同字符串表示的地址值，以便它们与八进制形式匹配。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-127">R1102: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message must have address values with identical string representations such that they match the octet-wise.</span></span>

  - <span data-ttu-id="ec4e7-128">在创建序列之前，WCF 响应方验证 `AcksTo`、`ReplyTo` 和 `Endpoint` 终结点引用的 URI 部分是否相同。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-128">The WCF Responder verifies that the URI portion of the `AcksTo`, `ReplyTo` and `Endpoint` endpoint references are identical before creating a sequence.</span></span>

- <span data-ttu-id="ec4e7-129">R1103：`AcksTo` 消息中的 `ReplyTo`、`Offer/Endpoint` 和 `CreateSequence` 终结点引用应该具有一组相同的引用参数。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-129">R1103: The `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references in the `CreateSequence` message should have the same set of reference parameters.</span></span>

  - <span data-ttu-id="ec4e7-130">WCF 不强制，但假定 `AcksTo`的引用参数、`ReplyTo` 和 `CreateSequence` 上的 `Offer/Endpoint` 终结点引用均相同，并使用来自 `ReplyTo` 终结点引用的引用参数来查找确认消息和反向序列消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-130">WCF does not enforce, but assumes that reference parameters of the `AcksTo`, `ReplyTo` and `Offer/Endpoint` endpoint references on `CreateSequence` are identical and uses reference parameters from the `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="ec4e7-131">B1104： WCF 发起方不会在 `CreateSequence` 消息中生成可选的 `Expires` 或 `Offer/Expires` 元素。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-131">B1104: The WCF Initiator does not generate the optional `Expires` or `Offer/Expires` element in the `CreateSequence` message.</span></span>

- <span data-ttu-id="ec4e7-132">B1105：访问 `CreateSequence` 消息时，WCF 响应程序使用 `CreateSequence` 元素中的 `Expires` 值作为 `CreateSequenceResponse` 元素中的 `Expires` 值。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-132">B1105: When accessing the `CreateSequence` message, the WCF Responder uses the `Expires` value in the `CreateSequence` element as the `Expires` value in the `CreateSequenceResponse` element.</span></span> <span data-ttu-id="ec4e7-133">否则，WCF 响应程序将读取并忽略 `Expires` 和 `Offer/Expires` 值。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-133">Otherwise, the WCF Responder reads and ignores the `Expires` and `Offer/Expires` values.</span></span>

- <span data-ttu-id="ec4e7-134">B1106：访问 `CreateSequenceResponse` 消息时，WCF 发起方将读取可选的 `Expires` 值，但不使用该值。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-134">B1106: When accessing the `CreateSequenceResponse` message, the WCF Initiator reads the optional `Expires` value but does not use it.</span></span>

- <span data-ttu-id="ec4e7-135">B1107： WCF 发起方和响应方始终在 `CreateSequence/Offer` 和 `CreateSequenceResponse` 元素中生成可选的 `IncompleteSequenceBehavior` 元素。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-135">B1107: The WCF Initiator and Responder always generate the optional `IncompleteSequenceBehavior` element in the `CreateSequence/Offer` and `CreateSequenceResponse` elements.</span></span>

- <span data-ttu-id="ec4e7-136">B1108： WCF 仅使用 `IncompleteSequenceBehavior` 元素中的 `DiscardFollowingFirstGap` 和 `NoDiscard` 值。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-136">B1108: WCF uses only the `DiscardFollowingFirstGap` and `NoDiscard` values in the `IncompleteSequenceBehavior` element.</span></span>

  - <span data-ttu-id="ec4e7-137">WS-ReliableMessaging 利用 `Offer` 机制建立构成会话的两个相反的相关序列。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-137">WS-ReliableMessaging utilizes the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="ec4e7-138">B1109：如果 `CreateSequence` 包含一个 `Offer` 元素，则通过使用没有 `Accept` 元素的 `CreateSequenceResponse` 进行响应，WCF 响应程序会拒绝所提供的序列。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-138">B1109: If `CreateSequence` contains an `Offer` element, the one way WCF Responder rejects the offered sequence by responding with a `CreateSequenceResponse` without an `Accept` element.</span></span>

- <span data-ttu-id="ec4e7-139">B1110：如果可靠消息响应程序拒绝所提供的序列，WCF 发起方会错误地创建新的序列。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-139">B1110: If a Reliable Messaging Responder rejects the offered sequence, the WCF Initiator faults the newly established sequence.</span></span>

- <span data-ttu-id="ec4e7-140">B1111：如果 `CreateSequence` 不包含 `Offer` 元素，则双向 WCF 响应程序通过用 `CreateSequenceRefused` 错误响应来拒绝所提供的序列。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-140">B1111: If `CreateSequence` does not contain an `Offer` element, the two-way WCF Responder rejects the offered sequence by responding with a `CreateSequenceRefused` fault.</span></span>

- <span data-ttu-id="ec4e7-141">R1112：使用 `Offer` 机制建立两个相反序列时，`[address]` 终结点引用的 `CreateSequenceResponse/Accept/AcksTo` 属性必须与 `CreateSequence` 消息的目标 URI 逐字节匹配。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-141">R1112: When two converse sequences are established using the `Offer` mechanism, the `[address]` property of the `CreateSequenceResponse/Accept/AcksTo` endpoint reference must match the destination URI of the `CreateSequence` message byte for byte.</span></span>

- <span data-ttu-id="ec4e7-142">R1113：使用 `Offer` 机制建立两个相反序列时，从发起方流向响应方的两个序列上的所有消息都必须发送到同一终结点引用。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-142">R1113: When two converse sequences are established using the `Offer` mechanism, all messages on both sequences flowing from the Initiator to the Responder must be sent to the same endpoint reference.</span></span>

<span data-ttu-id="ec4e7-143">WCF 使用 ws-reliablemessaging 在发起方和响应方之间建立可靠会话。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-143">WCF uses WS-ReliableMessaging to establish reliable sessions between the Initiator and the Responder.</span></span> <span data-ttu-id="ec4e7-144">WCF Ws-reliablemessaging 实现为单向、请求-答复和全双工消息传递模式提供可靠的会话。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-144">The WCF WS-ReliableMessaging implementation provides a reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="ec4e7-145">`Offer` 和 `CreateSequence` 上的 WS-ReliableMessaging `CreateSequenceResponse` 机制允许您建立两个相关的相反序列，并提供适合于所有消息终结点的会话协议。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-145">The WS-ReliableMessaging `Offer` mechanism on `CreateSequence` and `CreateSequenceResponse` lets you establish two correlated converse sequences and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="ec4e7-146">因为 WCF 为此类会话提供安全保证，包括会话完整性的端到端保护，所以确保用于同一参与方的消息到达同一目标是不切实际的。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-146">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure that messages intended for the same party arrive at the same destination.</span></span> <span data-ttu-id="ec4e7-147">这还允许应用程序消息上序列确认的“非法携带”。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-147">This also allows "piggy-backing" of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="ec4e7-148">因此，约束 R1102、R1112 和 R1113 适用于 WCF。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-148">Therefore, constraints R1102, R1112, and R1113 apply to WCF.</span></span>

<span data-ttu-id="ec4e7-149">`CreateSequence` 消息的一个示例。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-149">An example of a `CreateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>
    <wsa:ReplyTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
      </wsrm:AcksTo>
      <wsrm:Offer>
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>
        <wsrm:Endpoint>
          <wsa:Address>http://Business456.com/clientA</wsa:Address>
        </wsrm:Endpoint>
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      </wsrm:Offer>
    </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="ec4e7-150">`CreateSequenceResponse` 消息的一个示例。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-150">An example of a `CreateSequenceResponse` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      <wsrm:Accept>
        <wsrm:AcksTo>
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>
        </wsrm:AcksTo>
      </wsrm:Accept>
    </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="closing-a-sequence"></a><span data-ttu-id="ec4e7-151">关闭序列</span><span class="sxs-lookup"><span data-stu-id="ec4e7-151">Closing a Sequence</span></span>

<span data-ttu-id="ec4e7-152">WCF 将 `CloseSequence` 和 `CloseSequenceResponse` 消息用于可靠消息源启动的关闭。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-152">WCF uses the `CloseSequence` and `CloseSequenceResponse` messages for a Reliable Messaging source-initiated shutdown.</span></span> <span data-ttu-id="ec4e7-153">WCF 可靠消息传送目标不会启动关闭，并且 WCF 可靠消息源不支持可靠消息目标启动的关闭。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-153">The WCF Reliable Messaging destination does not initiate shutdown and the WCF Reliable Messaging source does not support a Reliable Messaging destination-initiated shutdown.</span></span> <span data-ttu-id="ec4e7-154">适用以下约束：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-154">The following constraints apply:</span></span>

- <span data-ttu-id="ec4e7-155">B1201： WCF 可靠消息源始终发送 `CloseSequence` 消息以关闭序列。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-155">B1201: The WCF Reliable Messaging source always sends a `CloseSequence` message to shut down the sequence.</span></span>

- <span data-ttu-id="ec4e7-156">B1202：可靠消息源在发送 `CloseSequence` 消息之前，等待确认全部的序列消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-156">B1202: The Reliable Messaging source waits for acknowledgement of the full range of sequence messages before sending the `CloseSequence` message.</span></span>

- <span data-ttu-id="ec4e7-157">B1203：除非序列不包含消息，否则可靠消息源始终包括可选的 `LastMsgNumber` 元素。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-157">B1203: The Reliable Messaging source always includes the optional `LastMsgNumber` element unless the sequence does not contain messages.</span></span>

- <span data-ttu-id="ec4e7-158">R1204：可靠消息目标不得通过发送 `CloseSequence` 消息启动关闭。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-158">R1204: The Reliable Messaging destination must not initiate shutdown by sending a `CloseSequence` message.</span></span>

- <span data-ttu-id="ec4e7-159">B1205：收到 `CloseSequence` 消息后，WCF 可靠消息源会将序列视为不完整并发送错误。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-159">B1205: Upon receiving a `CloseSequence` message, the WCF Reliable Messaging source considers the sequence incomplete and sends a fault.</span></span>

 <span data-ttu-id="ec4e7-160">`CloseSequence` 消息的一个示例。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-160">An example of a `CloseSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
    </wsrm:CloseSequence>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="ec4e7-161">`CloseSequenceResponse` 消息示例：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-161">Example `CloseSequenceResponse` message:</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:CloseSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence-termination"></a><span data-ttu-id="ec4e7-162">序列终止</span><span class="sxs-lookup"><span data-stu-id="ec4e7-162">Sequence Termination</span></span>

<span data-ttu-id="ec4e7-163">在完成 `CloseSequence/CloseSequenceResponse` 握手后，WCF 主要使用 `TerminateSequence/TerminateSequenceResponse` 握手。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-163">WCF primarily uses the `TerminateSequence/TerminateSequenceResponse` handshake after completing the `CloseSequence/CloseSequenceResponse` handshake.</span></span> <span data-ttu-id="ec4e7-164">WCF 可靠消息传送目标不启动终止，可靠消息源不支持可靠消息目标启动的终止。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-164">The WCF Reliable Messaging destination does not initiate termination and the Reliable Messaging source does not support a Reliable Messaging destination-initiated termination.</span></span> <span data-ttu-id="ec4e7-165">适用以下约束：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-165">The following constraints apply:</span></span>

- <span data-ttu-id="ec4e7-166">B1301： WCF 发起方仅在成功完成 `CloseSequence/CloseSequenceResponse` 握手后发送 `TerminateSequence` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-166">B1301: The WCF Initiator only sends the `TerminateSequence` message after the successful completion of the `CloseSequence/CloseSequenceResponse` handshake.</span></span>

- <span data-ttu-id="ec4e7-167">R1302： WCF 在给定序列的所有 `CloseSequence` 和 `TerminateSequence` 消息中验证 `LastMsgNumber` 元素是否一致。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-167">R1302: WCF validates that the `LastMsgNumber` element is consistent across all `CloseSequence` and `TerminateSequence` messages for a given sequence.</span></span> <span data-ttu-id="ec4e7-168">这意味着 `LastMsgNumber` 并不存在于所有 `CloseSequence` 和 `TerminateSequence` 消息上，或者它存在于所有 `CloseSequence` 和 `TerminateSequence` 消息上且完全相同。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-168">This means that `LastMsgNumber` is either not present on all `CloseSequence` and `TerminateSequence` messages, or it is present and identical on all `CloseSequence` and `TerminateSequence` messages.</span></span>

- <span data-ttu-id="ec4e7-169">B1303：在 `TerminateSequence` 握手后收到 `CloseSequence/CloseSequenceResponse` 消息时，可靠消息目标通过 `TerminateSequenceResponse` 消息进行响应。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-169">B1303: When receiving a `TerminateSequence` message after the `CloseSequence/CloseSequenceResponse` handshake, the Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="ec4e7-170">由于可靠消息源在发送 `TerminateSequence` 消息之前具有最终确认，因此可靠消息目标可毫无疑问地知道序列将结束，并立即回收资源。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-170">Because the Reliable Messaging source has the final acknowledgement before sending the `TerminateSequence` message, the Reliable Messaging destination knows without doubt that the sequence ends, and reclaims resources immediately.</span></span>

- <span data-ttu-id="ec4e7-171">B1304：在 `CloseSequence/CloseSequenceResponse` 握手之前接收 `TerminateSequence` 消息时，WCF 可靠消息目标将使用 `TerminateSequenceResponse` 消息进行响应。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-171">B1304: When receiving a `TerminateSequence` message prior to the `CloseSequence/CloseSequenceResponse` handshake, the WCF Reliable Messaging destination responds with a `TerminateSequenceResponse` message.</span></span> <span data-ttu-id="ec4e7-172">如果可靠消息目标确定序列中没有不一致之处，则可靠消息目标将在回收资源之前等待应用程序目标指定的时间，以便客户端有机会接收最终确认。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-172">If the Reliable Messaging destination determines that there are no inconsistencies in the sequence, the Reliable Messaging destination waits for an application destination-specified time before reclaiming resources, to allow the client the chance to receive the final acknowledgement.</span></span> <span data-ttu-id="ec4e7-173">否则，可靠消息目标立即回收资源，并通过引发 `Faulted` 事件向应用程序目标指出序列结束但存有疑问。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-173">Otherwise, the Reliable Messaging destination reclaims resources immediately and indicates to the application destination that the sequence ends with doubt by raising the `Faulted` event.</span></span>

<span data-ttu-id="ec4e7-174">`TerminateSequence` 消息的一个示例。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-174">An example of a `TerminateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
      </wsrm:TerminateSequence>
  </s:Body>
</s:Envelope>
```

<span data-ttu-id="ec4e7-175">`TerminateSequenceResponse` 消息示例：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-175">Example `TerminateSequenceResponse` message:</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:TerminateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequences"></a><span data-ttu-id="ec4e7-176">序列</span><span class="sxs-lookup"><span data-stu-id="ec4e7-176">Sequences</span></span>

<span data-ttu-id="ec4e7-177">以下是适用于序列的约束的列表：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-177">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="ec4e7-178">B1401： WCF 生成并访问的序列号不高于 `xs:long`的最大非独占值9223372036854775807。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-178">B1401:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

<span data-ttu-id="ec4e7-179">`Sequence` 标头的一个示例。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-179">An example of a `Sequence` header.</span></span>

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a><span data-ttu-id="ec4e7-180">请求确认</span><span class="sxs-lookup"><span data-stu-id="ec4e7-180">Request Acknowledgement</span></span>

<span data-ttu-id="ec4e7-181">WCF 使用 `AckRequested` 标头作为 keep-alive 机制。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-181">WCF uses the `AckRequested` header as a keep-alive mechanism.</span></span>

<span data-ttu-id="ec4e7-182">`AckRequested` 标头的一个示例。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-182">An example of an `AckRequested` header.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a><span data-ttu-id="ec4e7-183">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="ec4e7-183">SequenceAcknowledgement</span></span>

<span data-ttu-id="ec4e7-184">WCF 将 "非法携带" 机制用于在 WS-TRUST 消息中提供的序列确认。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-184">WCF uses a "piggy-back" mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span> <span data-ttu-id="ec4e7-185">适用以下约束：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-185">The following constraints apply:</span></span>

- <span data-ttu-id="ec4e7-186">R1601：使用 `Offer` 机制建立两个反向序列时，可以将 `SequenceAcknowledgement` 标头包含在传输给目标接收方的任何应用程序消息中。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-186">R1601: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span> <span data-ttu-id="ec4e7-187">远程终结点必须能够访问非法携带的 `SequenceAcknowledgement` 标头。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-187">The remote endpoint must be able to access a piggybacked `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="ec4e7-188">B1602： WCF 不生成包含 `Nack` 元素 `SequenceAcknowledgement` 标头。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-188">B1602: WCF does not generate `SequenceAcknowledgement` headers that contain `Nack` elements.</span></span> <span data-ttu-id="ec4e7-189">WCF 将验证每个 `Nack` 元素是否包含序列号，否则将忽略 `Nack` 元素和值。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-189">WCF validates that each `Nack` element contains a sequence number, but otherwise ignores the `Nack` element and value.</span></span>

 <span data-ttu-id="ec4e7-190">`SequenceAcknowledgement` 标头的一个示例。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-190">An example of a `SequenceAcknowledgement` header.</span></span>

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="ec4e7-191">WS-ReliableMessaging 错误</span><span class="sxs-lookup"><span data-stu-id="ec4e7-191">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="ec4e7-192">下面是适用于 WS-RELIABLEMESSAGING 错误的 WCF 实现的约束列表。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-192">The following is a list of constraints that apply to the WCF implementation of WS-ReliableMessaging faults.</span></span> <span data-ttu-id="ec4e7-193">适用以下约束：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-193">The following constraints apply:</span></span>

- <span data-ttu-id="ec4e7-194">B1701： WCF 不产生 `MessageNumberRollover` 错误。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-194">B1701: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="ec4e7-195">B1702：通过 SOAP 1.2，当服务终结点达到其连接限制并且无法处理新连接时，WCF 将生成嵌套 `CreateSequenceRefused` 错误子代码，`netrm:ConnectionLimitReached`，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-195">B1702: Over SOAP 1.2, when the service endpoint reaches its connection limit and cannot process new connections, WCF generates a nested `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>
  </s:Header>
  <s:Body>
    <s:Fault>
      <s:Code>
        <s:Value>s:Receiver</s:Value>
        <s:Subcode>
          <s:Value>wsrm:CreateSequenceRefused</s:Value>
          <s:Subcode>
            <s:Value>netrm:ConnectionLimitReached</s:Value>
          </s:Subcode>
        </s:Subcode>
      </s:Code>
      <s:Reason>
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>
      </s:Reason>
    </s:Fault>
  </s:Body>
</s:Envelope>
```

### <a name="ws-addressing-faults"></a><span data-ttu-id="ec4e7-196">WS-Addressing 错误</span><span class="sxs-lookup"><span data-stu-id="ec4e7-196">WS-Addressing Faults</span></span>

<span data-ttu-id="ec4e7-197">由于 ws-reliablemessaging 使用 WS-ADDRESSING，因此 WCF ws-reliablemessaging 实现可以生成和传输 WS-ADDRESSING 错误。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-197">Because WS-ReliableMessaging uses WS-Addressing, the WCF WS-ReliableMessaging implementation may generate and transmit WS-Addressing faults.</span></span> <span data-ttu-id="ec4e7-198">本部分介绍 WCF 在 WS-RELIABLEMESSAGING 层显式生成和传输的 WS-ADDRESSING 错误：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-198">This section covers the WS-Addressing faults that WCF explicitly generates and transmits at the WS-ReliableMessaging layer:</span></span>

- <span data-ttu-id="ec4e7-199">B1801：当满足以下任一条件时，WCF 将生成并传输 `Message Addressing Header Required` 错误：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-199">B1801:WCF generates and transmits the `Message Addressing Header Required` fault when one of the following is true:</span></span>

  - <span data-ttu-id="ec4e7-200">`CreateSequence``CloseSequence` 或 `TerminateSequence` 消息缺少 `MessageId` 头。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-200">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="ec4e7-201">`CreateSequence``CloseSequence` 或 `TerminateSequence` 消息缺少 `ReplyTo` 头。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-201">A `CreateSequence`, `CloseSequence` or `TerminateSequence` message is missing a `ReplyTo` header.</span></span>

  - <span data-ttu-id="ec4e7-202">`CreateSequenceResponse`、`CloseSequenceResponse` 或 `TerminateSequenceResponse` 消息缺少 `RelatesTo` 头。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-202">A `CreateSequenceResponse`, `CloseSequenceResponse`, or `TerminateSequenceResponse` message is missing a `RelatesTo` header.</span></span>

- <span data-ttu-id="ec4e7-203">B1802： WCF 生成并传输 `Endpoint Unavailable` 错误，以指示没有终结点侦听，可根据对 `CreateSequence` 消息中的寻址标头的检查来处理序列。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-203">B1802:WCF generates and transmits the `Endpoint Unavailable` fault to indicate there is no endpoint listening that can process the sequence based on examination of the addressing headers in the `CreateSequence` message.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="ec4e7-204">协议组合</span><span class="sxs-lookup"><span data-stu-id="ec4e7-204">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="ec4e7-205">与 WS-Addressing 组合</span><span class="sxs-lookup"><span data-stu-id="ec4e7-205">Composition with WS-Addressing</span></span>

<span data-ttu-id="ec4e7-206">WCF 支持两个版本的 WS-ADDRESSING： WS-ADDRESSING 2004/08 [WS-ADDRESSING] 和 W3C WS 寻址1.0 建议 [WS-ATOMICTRANSACTION] 和 [WS-ADDRESSING-SOAP]。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-206">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="ec4e7-207">尽管 WS-ReliableMessaging 规范仅提及 WS-Addressing 2004/08，但是它不限制要使用的 WS-Addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-207">While the WS-ReliableMessaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="ec4e7-208">下面列出了适用于 WCF 的约束：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-208">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="ec4e7-209">R2101：WS-Addressing 2004/08 和 WS-Addressing 1.0 都可以与 WS-Reliable Messaging 一起使用。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-209">R2101: Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="ec4e7-210">R2102：在整个的给定 WS-ReliableMessaging 序列或通过使用 `Offer` 机制关联的一对相反序列中，必须使用 WS-Addressing 的单个版本。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-210">R2102: A single version of WS-Addressing must be used throughout a given WS-ReliableMessaging sequence or a pair of converse sequences correlated by using the `Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="ec4e7-211">与 SOAP 组合</span><span class="sxs-lookup"><span data-stu-id="ec4e7-211">Composition with SOAP</span></span>

<span data-ttu-id="ec4e7-212">WCF 支持将 SOAP 1.1 和 SOAP 1.2 同时用于 WS-TRUST 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-212">WCF supports the use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="ec4e7-213">与 WS-Security 和 WS-SecureConversation 组合</span><span class="sxs-lookup"><span data-stu-id="ec4e7-213">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="ec4e7-214">WCF 通过使用安全传输（HTTPS）、使用 WS-MANAGEMENT 组合和结合 WS 安全会话来为 ws-reliablemessaging 序列提供保护。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-214">WCF provides protection for WS-ReliableMessaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="ec4e7-215">WS-ReliableMessaging 1.1 协议、WS-Security 1.1 和 WS-Secure Conversation 1.3 协议应该一起使用。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-215">The WS-ReliableMessaging 1.1 protocol, WS-Security 1.1 and WS-Secure Conversation 1.3 protocol should be used together.</span></span> <span data-ttu-id="ec4e7-216">下面列出了适用于 WCF 的约束：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-216">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="ec4e7-217">R2301：若要保护 WS-RELIABLEMESSAGING 序列的完整性，以及单个消息的完整性和保密性，WCF 需要使用 WS 安全对话。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-217">R2301: To protect the integrity of a WS-ReliableMessaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="ec4e7-218">R2302：必须在建立 WS-ReliableMessaging 序列之前建立 WS-Secure Conversation 会话。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-218">R2302:AWS-Secure Conversation session must be established prior to establishing WS-ReliableMessaging sequence(s).</span></span>

- <span data-ttu-id="ec4e7-219">R2303：如果 WS-ReliableMessaging 序列生存期超过了 WS-Secure Conversation 会话的生存期，则必须通过使用对应的 WS-Secure Conversation 续订绑定来续订通过使用 WS-Secure Conversation 建立的 `SecurityContextToken`。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-219">R2303: If the WS-ReliableMessaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="ec4e7-220">B2304：WS-ReliableMessaging 序列或一对相关的相反序列始终绑定到单个 WS-SecureConversation 会话。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-220">B2304:WS-ReliableMessaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

- <span data-ttu-id="ec4e7-221">R2305：在用 WS 安全会话撰写时，WCF 响应程序要求 `CreateSequence` 消息包含 `wsse:SecurityTokenReference` 元素和 `wsrm:UsesSequenceSTR` 标头。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-221">R2305: When composed with WS-Secure Conversation, the WCF responder requires that the `CreateSequence` message contain the `wsse:SecurityTokenReference` element and the `wsrm:UsesSequenceSTR` header.</span></span>

 <span data-ttu-id="ec4e7-222">`UsesSequenceSTR` 标头的一个示例。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-222">An example of a `UsesSequenceSTR` header.</span></span>

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a><span data-ttu-id="ec4e7-223">与 SSL/TLS 会话组合</span><span class="sxs-lookup"><span data-stu-id="ec4e7-223">Composition with SSL/TLS sessions</span></span>

<span data-ttu-id="ec4e7-224">WCF 不支持与 SSL/TLS 会话组合：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-224">WCF does not support composition with SSL/TLS sessions:</span></span>

- <span data-ttu-id="ec4e7-225">B2401： WCF 不生成 `wsrm:UsesSequenceSSL` 标头。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-225">B2401: WCF does not generate the `wsrm:UsesSequenceSSL` header.</span></span>

- <span data-ttu-id="ec4e7-226">R2402：可靠消息发起方不得将具有 `wsrm:UsesSequenceSSL` 标头的 `CreateSequence` 消息发送给 WCF 响应方。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-226">R2402: A Reliable Messaging Initiator must not send a `CreateSequence` message with a `wsrm:UsesSequenceSSL` header to a WCF Responder.</span></span>

### <a name="composition-with-ws-policy"></a><span data-ttu-id="ec4e7-227">与 WS-Policy 组合</span><span class="sxs-lookup"><span data-stu-id="ec4e7-227">Composition with WS-Policy</span></span>

<span data-ttu-id="ec4e7-228">WCF 支持两个版本的 WS 策略： WS 策略1.2 和 WS 策略1.5。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-228">WCF supports two versions of WS-Policy: WS-Policy 1.2 and WS-Policy 1.5.</span></span>

## <a name="ws-reliablemessaging-ws-policy-assertion"></a><span data-ttu-id="ec4e7-229">WS-ReliableMessaging WS-Policy 断言</span><span class="sxs-lookup"><span data-stu-id="ec4e7-229">WS-ReliableMessaging WS-Policy Assertion</span></span>

<span data-ttu-id="ec4e7-230">WCF 使用 ws-reliablemessaging WS 策略断言 `wsrm:RMAssertion` 来描述终结点功能。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-230">WCF uses WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="ec4e7-231">下面列出了适用于 WCF 的约束：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-231">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="ec4e7-232">B3001： WCF 将 `wsrmn:RMAssertion` WS 策略断言附加到 `wsdl:binding` 元素。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-232">B3001: WCF attaches `wsrmn:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="ec4e7-233">WCF 支持对 `wsdl:binding` 和 `wsdl:port` 元素的附件。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-233">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="ec4e7-234">B3002： WCF 从不生成 `wsp:Optional` 标记。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-234">B3002: WCF never generates the `wsp:Optional` tag.</span></span>

- <span data-ttu-id="ec4e7-235">B3003：访问 `wsrmp:RMAssertion` WS 策略断言时，WCF 将忽略 `wsp:Optional` 标记，并将 WS-RM 策略视为必需项。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-235">B3003: When accessing the `wsrmp:RMAssertion` WS-Policy Assertion, WCF ignores the `wsp:Optional` tag and treats the WS-RM policy as mandatory.</span></span>

- <span data-ttu-id="ec4e7-236">R3004：因为 WCF 不与 SSL/TLS 会话组合，WCF 不接受指定 `wsrmp:SequenceTransportSecurity`的策略。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-236">R3004: Because WCF does not compose with SSL/TLS sessions, WCF does not accept policy that specifies `wsrmp:SequenceTransportSecurity`.</span></span>

- <span data-ttu-id="ec4e7-237">B3005： WCF 始终生成 `wsrmp:DeliveryAssurance` 元素。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-237">B3005: WCF always generates the `wsrmp:DeliveryAssurance` element.</span></span>

- <span data-ttu-id="ec4e7-238">B3006： WCF 始终指定 `wsrmp:ExactlyOnce` 传递保障。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-238">B3006: WCF always specifies the `wsrmp:ExactlyOnce` delivery assurance.</span></span>

- <span data-ttu-id="ec4e7-239">B3007： WCF 生成并读取 WS-RELIABLEMESSAGING 断言的以下属性，并在 WCF`ReliableSessionBindingElement`上提供对这些属性的控制：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-239">B3007: WCF generates and reads the following properties of the WS-ReliableMessaging assertion and provides control over them on the WCF`ReliableSessionBindingElement`:</span></span>

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

  <span data-ttu-id="ec4e7-240">`RMAssertion` 的一个示例。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-240">An example of a `RMAssertion`.</span></span>

  ```xml
  <wsrmp:RMAssertion>
    <wsp:Policy>
      <wsrmp:SequenceSTR/>
      <wsrmp:DeliveryAssurance>
        <wsp:Policy>
          <wsrmp:ExactlyOnce/>
          <wsrmp:InOrder/>
        </wsp:Policy>
      </wsrmp:DeliveryAssurance>
    </wsp:Policy>
    <netrmp:InactivityTimeout Milliseconds="600000"/>
    <netrmp:AcknowledgementInterval Milliseconds="200"/>
  </wsrmp:RMAssertion>
  ```

## <a name="flow-control-ws-reliablemessaging-extension"></a><span data-ttu-id="ec4e7-241">流控制 WS-ReliableMessaging 扩展</span><span class="sxs-lookup"><span data-stu-id="ec4e7-241">Flow Control WS-ReliableMessaging Extension</span></span>

<span data-ttu-id="ec4e7-242">WCF 使用 WS-RELIABLEMESSAGING 扩展性提供对序列消息流的其他更严格的控制。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-242">WCF uses WS-ReliableMessaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="ec4e7-243">启用流控制，方法是将 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-243">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="ec4e7-244">下面列出了适用于 WCF 的约束：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-244">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="ec4e7-245">B4001：启用可靠消息流控制时，WCF 会在 `SequenceAcknowledgement` 标头的元素扩展性中生成 `netrm:BufferRemaining` 元素，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-245">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="ec4e7-246">B4002：即使在启用可靠消息流控制时，WCF 也不需要 `SequenceAcknowledgement` 标头中的 `netrm:BufferRemaining` 元素。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-246">B4002: Even when Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element in the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="ec4e7-247">B4003： WCF 可靠消息传送目标使用 `netrm:BufferRemaining` 来指示它可以缓冲多少条新消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-247">B4003: WCF Reliable Messaging Destination uses `netrm:BufferRemaining` to indicate how many new messages it can buffer.</span></span>

- <span data-ttu-id="ec4e7-248">B4004：启用可靠消息流控制时，WCF 可靠消息源使用 `netrm:BufferRemaining` 的值来限制消息传输。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-248">B4004:When Reliable Messaging Flow Control is enabled, the WCF Reliable Messaging Source uses the value of `netrm:BufferRemaining` to throttle message transmission.</span></span>

- <span data-ttu-id="ec4e7-249">B4005： WCF `netrm:BufferRemaining` 生成的整数值介于0和4096之间（含0和），并读取0到 `xs:int`的 `maxInclusive` 值214748364（含）之间的整数值。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-249">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="ec4e7-250">消息交换模式</span><span class="sxs-lookup"><span data-stu-id="ec4e7-250">Message Exchange Patterns</span></span>

<span data-ttu-id="ec4e7-251">本节介绍当 WS-RELIABLEMESSAGING 用于不同消息交换模式时，WCF 的行为。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-251">This section describes WCF's behavior when WS-ReliableMessaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="ec4e7-252">对于每个消息交换模式，可以考虑下面的两个部署方案：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-252">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="ec4e7-253">不可寻址的发起方：发起方位于防火墙背后；响应方只能在 HTTP 响应上将消息传递到发起方。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-253">Non-Addressable Initiator: Initiator is behind a firewall; Responder can deliver messages to the Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="ec4e7-254">可寻址的发起方：发起方和响应方都可以发送 HTTP 请求；换句话说，可以建立两个相反的 HTTP 连接。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-254">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="ec4e7-255">单向、不可寻址的发起方</span><span class="sxs-lookup"><span data-stu-id="ec4e7-255">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ec4e7-256">绑定</span><span class="sxs-lookup"><span data-stu-id="ec4e7-256">Binding</span></span>

<span data-ttu-id="ec4e7-257">WCF 通过一个 HTTP 通道使用一个序列来提供单向消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-257">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="ec4e7-258">WCF 使用 HTTP 请求将所有消息从发起方传输到响应方，并使用 HTTP 响应将所有消息从响应方传输到发起方。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-258">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ec4e7-259">CreateSequence 交换</span><span class="sxs-lookup"><span data-stu-id="ec4e7-259">CreateSequence Exchange</span></span>

<span data-ttu-id="ec4e7-260">WCF 发起方在 HTTP 请求上传输没有 `Offer` 元素的 `CreateSequence` 消息，并在 HTTP 响应上期望 `CreateSequenceResponse` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-260">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="ec4e7-261">WCF 响应程序创建一个序列，并在 HTTP 响应上传输 `CreateSequenceResponse` 消息，不包含任何 `Accept` 元素。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-261">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on the HTTP response.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="ec4e7-262">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="ec4e7-262">SequenceAcknowledgement</span></span>

<span data-ttu-id="ec4e7-263">WCF 发起方处理除 `CreateSequence` 消息和错误消息以外的所有消息的答复的确认。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-263">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="ec4e7-264">WCF 响应方始终将对 HTTP 响应的独立确认传输到所有序列和 `AckRequested` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-264">The WCF Responder always transmits a stand-alone acknowledgement on the HTTP response to all sequence and `AckRequested` messages.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="ec4e7-265">CloseSequence 交换</span><span class="sxs-lookup"><span data-stu-id="ec4e7-265">CloseSequence Exchange</span></span>

<span data-ttu-id="ec4e7-266">WCF 发起方在 HTTP 请求上传输 `CloseSequence` 消息，并在 HTTP 响应上期望 `CreateSequenceResponse` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-266">The WCF Initiator transmits a `CloseSequence` message on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="ec4e7-267">WCF 响应程序在 HTTP 响应上传输 `CloseSequenceResponse` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-267">The WCF Responder transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="ec4e7-268">TerminateSequence 交换</span><span class="sxs-lookup"><span data-stu-id="ec4e7-268">TerminateSequence Exchange</span></span>

<span data-ttu-id="ec4e7-269">WCF 发起方在 HTTP 请求上传输 `TerminateSequence` 消息，并在 HTTP 响应上期望 `TerminateSequenceResponse` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-269">The WCF Initiator transmits a `TerminateSequence` message on an HTTP request and expects the `TerminateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="ec4e7-270">WCF 响应程序在 HTTP 响应上传输 `TerminateSequenceResponse` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-270">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="ec4e7-271">单向、可寻址的发起方</span><span class="sxs-lookup"><span data-stu-id="ec4e7-271">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ec4e7-272">绑定</span><span class="sxs-lookup"><span data-stu-id="ec4e7-272">Binding</span></span>

<span data-ttu-id="ec4e7-273">WCF 通过一个入站和一个出站 HTTP 通道使用一个序列来提供单向消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-273">WCF provides a one-way message exchange pattern using one sequence over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="ec4e7-274">WCF 使用 HTTP 请求传输所有消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-274">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ec4e7-275">所有 HTTP 响应的正文都为空，并且具有 HTTP 202 状态代码。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-275">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ec4e7-276">CreateSequence 交换</span><span class="sxs-lookup"><span data-stu-id="ec4e7-276">CreateSequence Exchange</span></span>

<span data-ttu-id="ec4e7-277">WCF 发起方在 HTTP 请求上传输没有 `Offer` 元素的 `CreateSequence` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-277">The WCF Initiator transmits a `CreateSequence` message with no `Offer` element on an HTTP request.</span></span> <span data-ttu-id="ec4e7-278">WCF 响应程序创建一个序列，并在 HTTP 请求上传输没有 `Accept` 元素的 `CreateSequenceResponse` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-278">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with no `Accept` element on an HTTP request.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="ec4e7-279">双工、可寻址的发起方</span><span class="sxs-lookup"><span data-stu-id="ec4e7-279">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ec4e7-280">绑定</span><span class="sxs-lookup"><span data-stu-id="ec4e7-280">Binding</span></span>

<span data-ttu-id="ec4e7-281">WCF 通过一个入站和一个出站 HTTP 通道提供使用两个序列的完全异步的双向消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-281">WCF provides a fully-asynchronous, two-way message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="ec4e7-282">此消息交换模式可以与 `Request/Reply`、`Addressable` 发起方消息交换模式以有限方式混合使用。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-282">This message exchange pattern can be mixed with the `Request/Reply`, `Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="ec4e7-283">WCF 使用 HTTP 请求传输所有消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-283">WCF uses HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ec4e7-284">所有 HTTP 响应的正文都为空，并且具有 HTTP 202 状态代码。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-284">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ec4e7-285">CreateSequence 交换</span><span class="sxs-lookup"><span data-stu-id="ec4e7-285">CreateSequence Exchange</span></span>

<span data-ttu-id="ec4e7-286">WCF 发起方在 HTTP 请求上传输具有 `Offer` 元素的 `CreateSequence` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-286">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="ec4e7-287">WCF 响应程序确保 `CreateSequence` 具有 `Offer` 元素，然后创建一个序列并使用 `Accept` 元素传输 `CreateSequenceResponse` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-287">The WCF Responder ensures that the `CreateSequence` has an `Offer` element, then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="ec4e7-288">序列生存期</span><span class="sxs-lookup"><span data-stu-id="ec4e7-288">Sequence Lifetime</span></span>

<span data-ttu-id="ec4e7-289">WCF 将两个序列视为一个全双工会话。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-289">WCF treats the two sequences as one fully-duplex session.</span></span>

<span data-ttu-id="ec4e7-290">生成出错的错误时，WCF 要求远程终结点对这两个序列进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-290">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="ec4e7-291">读取出错一序列的错误时，WCF 会对这两个序列进行故障排除。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-291">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="ec4e7-292">WCF 可以关闭其出站序列并继续处理其入站序列上的消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-292">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="ec4e7-293">相反，WCF 可以处理入站序列的关闭，并继续按其出站序列发送消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-293">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-and-one-way-non-addressable-initiator"></a><span data-ttu-id="ec4e7-294">请求-答复和单向、不可寻址的发起方</span><span class="sxs-lookup"><span data-stu-id="ec4e7-294">Request-Reply and One-Way, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ec4e7-295">绑定</span><span class="sxs-lookup"><span data-stu-id="ec4e7-295">Binding</span></span>

<span data-ttu-id="ec4e7-296">WCF 提供在一个 HTTP 通道上使用两个序列的单向和请求-答复消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-296">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="ec4e7-297">WCF 使用 HTTP 请求将所有消息从发起方传输到响应方，并使用 HTTP 响应将所有消息从响应方传输到发起方。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-297">WCF uses HTTP requests to transmit all messages from the Initiator to the Responder and HTTP responses to transmit all messages from the Responder to the Initiator.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ec4e7-298">CreateSequence 交换</span><span class="sxs-lookup"><span data-stu-id="ec4e7-298">CreateSequence Exchange</span></span>

<span data-ttu-id="ec4e7-299">WCF 发起方在 HTTP 请求上传输带有 `Offer` 元素的 `CreateSequence` 消息，并在 HTTP 响应上期望 `CreateSequenceResponse` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-299">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request and expects the `CreateSequenceResponse` message on the HTTP response.</span></span> <span data-ttu-id="ec4e7-300">WCF 响应方创建一个序列，并在 HTTP 响应中使用 `Accept` 元素来传输 `CreateSequenceResponse` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-300">The WCF Responder creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element on the HTTP response.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="ec4e7-301">单向消息</span><span class="sxs-lookup"><span data-stu-id="ec4e7-301">One-way Message</span></span>

<span data-ttu-id="ec4e7-302">若要成功完成单向消息交换，WCF 发起方会在 http 请求上传输请求序列消息，并在 HTTP 响应上接收独立的 `SequenceAcknowledgement` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-302">To complete a one-way message exchange successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="ec4e7-303">`SequenceAcknowledgement` 必须确认已传输的消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-303">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="ec4e7-304">WCF 响应方可以使用确认、错误或具有空正文和 HTTP 202 状态代码的响应来答复请求。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-304">The WCF Responder may reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="ec4e7-305">双向消息</span><span class="sxs-lookup"><span data-stu-id="ec4e7-305">Two Way Messages</span></span>

<span data-ttu-id="ec4e7-306">若要成功完成双向消息交换协议，WCF 发起方会在 http 请求上传输请求序列消息，并在 HTTP 响应上接收答复序列消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-306">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="ec4e7-307">响应必须包含一个确认已传输的请求序列消息的 `SequenceAcknowledgement`。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-307">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="ec4e7-308">WCF 响应方可以使用应用程序答复、错误或正文为空的响应和 HTTP 202 状态代码来回复请求。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-308">The WCF Responder may reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="ec4e7-309">由于存在单向消息和应用程序答复的计时，因此请求序列消息的序列号与响应消息的序列号不相关联。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-309">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="ec4e7-310">重试答复</span><span class="sxs-lookup"><span data-stu-id="ec4e7-310">Retrying Replies</span></span>

<span data-ttu-id="ec4e7-311">WCF 依赖 HTTP 请求-答复相关性进行双向消息交换协议关联。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-311">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="ec4e7-312">因此，当确认请求序列消息时，WCF 发起方不会停止重试请求序列消息，而是在 HTTP 响应携带 `SequenceAcknowledgement`、应用程序答复或错误时停止。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-312">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries a `SequenceAcknowledgement`, application reply, or fault.</span></span> <span data-ttu-id="ec4e7-313">WCF 响应方在答复关联到的请求的 HTTP 响应上重试响应。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-313">The WCF Responder retries replies on the HTTP response of the request to which the reply is correlated.</span></span>

#### <a name="closesequence-exchange"></a><span data-ttu-id="ec4e7-314">CloseSequence 交换</span><span class="sxs-lookup"><span data-stu-id="ec4e7-314">CloseSequence Exchange</span></span>

<span data-ttu-id="ec4e7-315">接收所有单向请求序列消息的所有答复序列消息和确认之后，WCF 发起程序会针对 HTTP 请求传输请求序列的 `CloseSequence` 消息，并在 HTTP 响应中要求 `CloseSequenceResponse`。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-315">After receiving all reply sequence messages and acknowledgements for all one way request sequence messages, the WCF Initiator transmits a `CloseSequence` message for the request sequence on an HTTP request and expects the `CloseSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="ec4e7-316">关闭请求序列将隐式关闭答复序列。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-316">Closing the request sequence implicitly closes the reply sequence.</span></span> <span data-ttu-id="ec4e7-317">这意味着 WCF 发起方在 `CloseSequence` 消息上包括答复序列的最终 `SequenceAcknowledgement`，而答复序列没有 `CloseSequence` 的交换。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-317">This means the WCF Initiator includes the reply sequence’s Final `SequenceAcknowledgement` on the `CloseSequence` message and the reply sequence does not have a `CloseSequence` exchange.</span></span>

<span data-ttu-id="ec4e7-318">WCF 响应程序确保所有答复都得到确认，并在 HTTP 响应上传输 `CloseSequenceResponse` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-318">The WCF Responder ensures all replies are acknowledged and transmits the `CloseSequenceResponse` message on the HTTP response.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="ec4e7-319">TerminateSequence 交换</span><span class="sxs-lookup"><span data-stu-id="ec4e7-319">TerminateSequence Exchange</span></span>

<span data-ttu-id="ec4e7-320">接收到 `CloseSequenceResponse` 消息后，WCF 发起程序将针对 HTTP 请求传输请求序列的 `TerminateSequence` 消息，并在 HTTP 响应中要求 `TerminateSequenceResponse`。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-320">After receiving the `CloseSequenceResponse` message, the WCF Initiator transmits a `TerminateSequence` message for the request sequence on an HTTP request and expects the `TerminateSequenceResponse` on the HTTP response.</span></span>

<span data-ttu-id="ec4e7-321">与 `CloseSequence` 交换一样，终止请求序列将隐式终止答复序列。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-321">Like the `CloseSequence` exchange, terminating the request sequence implicitly terminates the reply sequence.</span></span> <span data-ttu-id="ec4e7-322">这意味着 WCF 发起方在 `TerminateSequence` 消息上包括答复序列的最终 `SequenceAcknowledgement`，而答复序列没有 `TerminateSequence` 的交换。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-322">This means the WCF Initiator includes the reply sequence’s final `SequenceAcknowledgement` on the `TerminateSequence` message and the reply sequence does not have a `TerminateSequence` exchange.</span></span>

<span data-ttu-id="ec4e7-323">WCF 响应程序在 HTTP 响应上传输 `TerminateSequenceResponse` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-323">The WCF Responder transmits the `TerminateSequenceResponse` message on the HTTP response.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="ec4e7-324">请求/答复、可寻址的发起方</span><span class="sxs-lookup"><span data-stu-id="ec4e7-324">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="ec4e7-325">绑定</span><span class="sxs-lookup"><span data-stu-id="ec4e7-325">Binding</span></span>

<span data-ttu-id="ec4e7-326">WCF 通过一个入站和一个出站 HTTP 通道使用两个序列提供请求-答复消息交换模式。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-326">WCF provides a request-reply message exchange pattern using two sequences over one inbound and one outbound HTTP channel.</span></span> <span data-ttu-id="ec4e7-327">此消息交换模式可以与 `Duplex, Addressable` 发起方消息交换模式以有限方式混合使用。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-327">This message exchange pattern can be mixed with the `Duplex, Addressable` Initiator message exchange pattern in a limited way.</span></span> <span data-ttu-id="ec4e7-328">WCF 使用 HTTP 请求传输所有消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-328">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="ec4e7-329">所有 HTTP 响应的正文都为空，并且具有 HTTP 202 状态代码。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-329">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="ec4e7-330">CreateSequence 交换</span><span class="sxs-lookup"><span data-stu-id="ec4e7-330">CreateSequence Exchange</span></span>

<span data-ttu-id="ec4e7-331">WCF 发起方在 HTTP 请求上传输具有 `Offer` 元素的 `CreateSequence` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-331">The WCF Initiator transmits a `CreateSequence` message with an `Offer` element on an HTTP request.</span></span> <span data-ttu-id="ec4e7-332">WCF 响应程序确保 `CreateSequence` 具有 `Offer` 元素，然后创建一个序列并使用 `Accept` 元素传输 `CreateSequenceResponse` 消息。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-332">The WCF Responder ensures that the `CreateSequence` has an `Offer` element then creates a sequence and transmits the `CreateSequenceResponse` message with an `Accept` element.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="ec4e7-333">请求/答复关联</span><span class="sxs-lookup"><span data-stu-id="ec4e7-333">Request/Reply Correlation</span></span>

<span data-ttu-id="ec4e7-334">以下内容适用于所有关联的请求和答复：</span><span class="sxs-lookup"><span data-stu-id="ec4e7-334">The following applies to all correlated requests and replies:</span></span>

- <span data-ttu-id="ec4e7-335">WCF 确保所有应用程序请求消息都具有 `ReplyTo` 终结点引用和 `MessageId`。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-335">WCF ensures all application request messages bear a `ReplyTo` endpoint reference and a `MessageId`.</span></span>

- <span data-ttu-id="ec4e7-336">每个应用程序请求消息的 `ReplyTo`，WCF 都应用本地终结点引用。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-336">WCF applies the local endpoint reference as each application request message’s `ReplyTo`.</span></span> <span data-ttu-id="ec4e7-337">本地终结点引用是发起方的 `CreateSequence` 消息的 `ReplyTo` 和响应方的 `CreateSequence` 消息的 `To`。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-337">The local endpoint reference is the `CreateSequence` message’s `ReplyTo` for the Initiator and the `CreateSequence` message’s `To` for the Responder.</span></span>

- <span data-ttu-id="ec4e7-338">WCF 确保传入请求消息的 `MessageId` 和 `ReplyTo`。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-338">WCF ensures that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span>

- <span data-ttu-id="ec4e7-339">WCF 确保所有应用程序请求消息 `ReplyTo` 终结点引用的 URI 与前面定义的本地终结点引用匹配。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-339">WCF ensures the `ReplyTo` endpoint reference’s URI of all application request messages match the local endpoint reference as defined earlier.</span></span>

- <span data-ttu-id="ec4e7-340">WCF 可确保所有答复都在 `wsa` 请求/答复相关规则后，按正确的 `RelatesTo` 和 `To` 标头进行。</span><span class="sxs-lookup"><span data-stu-id="ec4e7-340">WCF ensures that all replies bear the correct `RelatesTo` and `To` headers following `wsa` request/reply correlation rules.</span></span>
