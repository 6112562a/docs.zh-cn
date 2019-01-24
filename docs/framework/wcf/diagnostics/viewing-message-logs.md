---
title: 查看消息日志
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: f368d4f8f2a214feaa24b732513a99edf2e28296
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603564"
---
# <a name="viewing-message-logs"></a><span data-ttu-id="2b7a4-102">查看消息日志</span><span class="sxs-lookup"><span data-stu-id="2b7a4-102">Viewing Message Logs</span></span>
<span data-ttu-id="2b7a4-103">本主题描述如何查看消息日志。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-103">This topic describes how you can view message logs.</span></span>  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a><span data-ttu-id="2b7a4-104">在服务跟踪查看器中查看消息日志</span><span class="sxs-lookup"><span data-stu-id="2b7a4-104">Viewing Message Logs in the Service Trace Viewer</span></span>  
 <span data-ttu-id="2b7a4-105">WCF 处理时，消息会进行转换。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-105">A message will be transformed as it is processed by WCF.</span></span> <span data-ttu-id="2b7a4-106">因此，记录的消息只反映记录时的消息内容，而不是网络上的内容。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-106">Therefore, a message being logged reflects only the message's content at the point it was logged, not the content on the wire.</span></span>  
  
 <span data-ttu-id="2b7a4-107">由于消息日志记录的输出与消息的传输格式无关，因此，消息日志记录始终输出已解码的消息。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-107">Since the output of message logging has no relationship to the transfer format of the message, message logging always outputs the decoded message.</span></span> <span data-ttu-id="2b7a4-108">如果已正确配置消息日志记录，则记录的所有消息都应采用纯文本格式。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-108">If you have configured message logging properly, any logged message should be in plain text.</span></span> <span data-ttu-id="2b7a4-109">例如，使用二进制消息编码器不会影响已记录消息的格式（纯文本）。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-109">For example, the format (plain text) of the logged messages is not affected by the usage of a binary message encoder.</span></span>  
  
 <span data-ttu-id="2b7a4-110">XmlWriterTraceListener 的输出是一个包含一系列 XML 片段的文件。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-110">The output of the XmlWriterTraceListener is a file that contains a sequence of XML fragments.</span></span> <span data-ttu-id="2b7a4-111">请注意，该文件并不是有效的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-111">You should be aware that the file is not a valid XML file.</span></span> <span data-ttu-id="2b7a4-112">建议你使用[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)查看消息日志文件。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-112">It is recommended that you use the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) to view the message log files.</span></span> <span data-ttu-id="2b7a4-113">有关如何使用此工具的详细信息，请参阅[使用服务跟踪查看器查看相关跟踪和故障排除](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-113">For more information on how to use this tool, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="2b7a4-114">在服务跟踪查看器中，消息中列出**消息**选项卡。导致处理错误或与处理错误相关的消息会以黄色（警告级别）或以红色（错误级别）突出显示，具体取决于错误的严重性。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-114">In the Service Trace Viewer, messages are listed in the **Message** tab. Messages that have caused, or are related to, a processing error are highlighted in yellow (warning level) or red (error level), depending on the severity of the error.</span></span> <span data-ttu-id="2b7a4-115">双击消息会显示处理请求上下文中的消息跟踪。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-115">Double-clicking on the message brings up the message trace in the context of the processing request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b7a4-116">如果消息没有标头，则不记录 `<header/>` 标记。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-116">If a message has no header, no `<header/>` tag is logged.</span></span>  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a><span data-ttu-id="2b7a4-117">查看由客户端、中继和服务记录的消息</span><span class="sxs-lookup"><span data-stu-id="2b7a4-117">Viewing Messages Logged by a Client, a Relay, and a Service</span></span>  
 <span data-ttu-id="2b7a4-118">您的环境可能包含客户端，它将消息发送给中继，中继随后将消息转发给服务。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-118">Your environment may contain a client, which sends a message to a relay, that subsequently forwards the message to the service.</span></span> <span data-ttu-id="2b7a4-119">当在所有三个位置上启用消息日志记录和所有三个消息日志中查看[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)同时，消息日志交换不会正确呈现。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-119">When message logging is enabled on all three locations, and all three message logs are viewed in [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) simultaneously, the message log exchanges will be incorrectly rendered.</span></span> <span data-ttu-id="2b7a4-120">这是因为消息头中的 `CorrelationId` 和 `ActivityId` 对于每个发送-接收对并不是唯一的。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-120">This is because the `CorrelationId` and `ActivityId` in the Message header are not unique for every send-receive pair.</span></span>  
  
 <span data-ttu-id="2b7a4-121">您可以使用以下方法之一解决此问题。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-121">You can use either one of the following methods to resolve this problem.</span></span>  
  
-   <span data-ttu-id="2b7a4-122">仅查看三个消息日志中的两个[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)在任何时间。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-122">Only view two of the three message logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at any time.</span></span>  
  
-   <span data-ttu-id="2b7a4-123">如果您必须查看中的所有三个日志[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)在同一时间中，您可以修改中继服务通过创建一个新<xref:System.ServiceModel.Channels.Message>实例。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-123">If you must view all three logs in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) at the same time, you can modify the relay service by creating a new <xref:System.ServiceModel.Channels.Message> instance.</span></span> <span data-ttu-id="2b7a4-124">此实例应该是传入消息正文以及除 `ActivityId` 和 `Action` 标头以外所有标头的副本。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-124">This instance should be a copy of the body of the incoming message, plus all the headers except for the `ActivityId` and `Action` headers.</span></span> <span data-ttu-id="2b7a4-125">下面的示例代码演示如何执行该操作。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-125">The following example code demonstrates how to do this.</span></span>  
  
```csharp
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a><span data-ttu-id="2b7a4-126">不准确消息日志记录内容的异常情况</span><span class="sxs-lookup"><span data-stu-id="2b7a4-126">Exceptional Cases for Inaccurate Message Logging Content</span></span>  
 <span data-ttu-id="2b7a4-127">在以下条件下，记录的消息可能不是网络上存在的八进制流的准确表示形式。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-127">Under the following conditions, messages being logged might not be the exact representation of the octet stream present on the wire.</span></span>  
  
-   <span data-ttu-id="2b7a4-128">对于 BasicHttpBinding，在 /addressing/none 命名空间中记录传入消息的信封标头。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-128">For BasicHttpBinding, envelope headers are logged for the incoming messages in the /addressing/none namespace.</span></span>  
  
-   <span data-ttu-id="2b7a4-129">空白字符可能不匹配。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-129">White spaces can be mismatched.</span></span>  
  
-   <span data-ttu-id="2b7a4-130">对于传入消息，可能用不同形式表示空元素。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-130">For incoming messages, empty elements can be represented differently.</span></span> <span data-ttu-id="2b7a4-131">例如，\<标记 >\</标记 > 而不是\<标记 / ></span><span class="sxs-lookup"><span data-stu-id="2b7a4-131">For example, \<tag>\</tag> instead of  \<tag/></span></span>  
  
-   <span data-ttu-id="2b7a4-132">默认情况下或通过显式设置 enableLoggingKnownPii="true" 已禁用已知 PII 日志记录。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-132">When known PII logging is disabled either by default or explicit setting enableLoggingKnownPii="true".</span></span>  
  
-   <span data-ttu-id="2b7a4-133">已启用编码以转换到 UTF-8。</span><span class="sxs-lookup"><span data-stu-id="2b7a4-133">Encoding is enabled for transforming to UTF-8.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b7a4-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="2b7a4-134">See also</span></span>
- [<span data-ttu-id="2b7a4-135">服务跟踪查看器工具 (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="2b7a4-135">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [<span data-ttu-id="2b7a4-136">使用服务跟踪查看器查看相关跟踪和进行故障排除</span><span class="sxs-lookup"><span data-stu-id="2b7a4-136">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="2b7a4-137">消息日志记录</span><span class="sxs-lookup"><span data-stu-id="2b7a4-137">Message Logging</span></span>](../../../../docs/framework/wcf/diagnostics/message-logging.md)
