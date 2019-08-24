---
title: 路由简介
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: eaf09c0d724521c3c69fde0e90ecd7cd5aadb253
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988673"
---
# <a name="routing-introduction"></a><span data-ttu-id="9369f-102">路由简介</span><span class="sxs-lookup"><span data-stu-id="9369f-102">Routing Introduction</span></span>
<span data-ttu-id="9369f-103">路由服务提供的泛型可插入 SOAP 中介能够根据消息内容路由消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-103">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="9369f-104">使用路由服务，您可以创建复杂的路由逻辑，以便实现服务聚合、服务版本管理、优先级路由和多播路由等方案。</span><span class="sxs-lookup"><span data-stu-id="9369f-104">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="9369f-105">路由服务还提供了错误处理功能，使您可以设置备份终结点的列表。如果将消息发送到主目标终结点时失败，则会发送到这些备份终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-105">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>  
  
 <span data-ttu-id="9369f-106">本主题面向不熟悉路由服务的人员，其中涵盖了路由服务的基本配置和承载等内容。</span><span class="sxs-lookup"><span data-stu-id="9369f-106">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="9369f-107">配置</span><span class="sxs-lookup"><span data-stu-id="9369f-107">Configuration</span></span>  
 <span data-ttu-id="9369f-108">路由服务作为公开一个或多个服务终结点的 WCF 服务实现，这些服务终结点接收来自客户端应用程序的消息，并将消息路由到一个或多个目标终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-108">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="9369f-109">该服务提供应用于服务公开的服务终结点的 <xref:System.ServiceModel.Routing.RoutingBehavior>。</span><span class="sxs-lookup"><span data-stu-id="9369f-109">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="9369f-110">此行为用于配置服务运行方式的各个方面。</span><span class="sxs-lookup"><span data-stu-id="9369f-110">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="9369f-111">为了便于在使用配置文件时进行配置, 请在**RoutingBehavior**上指定参数。</span><span class="sxs-lookup"><span data-stu-id="9369f-111">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="9369f-112">在基于代码的方案中, 这些参数将被指定为<xref:System.ServiceModel.Routing.RoutingConfiguration>对象的一部分, 然后可以将该对象传递给**RoutingBehavior**。</span><span class="sxs-lookup"><span data-stu-id="9369f-112">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>  
  
 <span data-ttu-id="9369f-113">在启动时，该行为向客户端终结点添加 <xref:System.ServiceModel.Routing.SoapProcessingBehavior>，用于对消息执行 SOAP 处理。</span><span class="sxs-lookup"><span data-stu-id="9369f-113">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="9369f-114">这允许路由服务将消息传输到需要的**MessageVersion**不同于接收消息的终结点的终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-114">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="9369f-115">**RoutingBehavior**还会注册一个服务扩展, <xref:System.ServiceModel.Routing.RoutingExtension>后者提供了一个可访问点, 用于在运行时修改路由服务配置。</span><span class="sxs-lookup"><span data-stu-id="9369f-115">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>  
  
 <span data-ttu-id="9369f-116">**RoutingConfiguration**类提供了一种一致的方式来配置和更新路由服务的配置。</span><span class="sxs-lookup"><span data-stu-id="9369f-116">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="9369f-117">它包含一些参数, 这些参数用作路由服务的设置, 并用于在服务启动时配置**RoutingBehavior** , 或将其传递给**RoutingExtension**以在运行时修改路由配置。</span><span class="sxs-lookup"><span data-stu-id="9369f-117">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>  
  
 <span data-ttu-id="9369f-118">通过将多个 <xref:System.ServiceModel.Dispatcher.MessageFilter> 对象全部组合到筛选器表（<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> 对象）中，可以定义用于对消息执行基于内容的路由的路由逻辑。</span><span class="sxs-lookup"><span data-stu-id="9369f-118">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="9369f-119">将针对筛选器表中包含的消息筛选器以及与消息匹配的每个**MessageFilter**来计算传入消息, 并将其转发到目标终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-119">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="9369f-120">用于路由消息的筛选器表是通过在配置中使用**RoutingBehavior**或使用**RoutingConfiguration**对象通过代码指定的。</span><span class="sxs-lookup"><span data-stu-id="9369f-120">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>  
  
### <a name="defining-endpoints"></a><span data-ttu-id="9369f-121">定义终结点</span><span class="sxs-lookup"><span data-stu-id="9369f-121">Defining Endpoints</span></span>  
 <span data-ttu-id="9369f-122">在开始配置时，您似乎应先定义将要使用的路由逻辑，但是，首要步骤实际应是：确定消息将路由至的目标终结点的形状。</span><span class="sxs-lookup"><span data-stu-id="9369f-122">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="9369f-123">路由服务采用协定来定义用于收发消息的通道的形状，因此，输入通道的形状必须与输出通道的形状相匹配。</span><span class="sxs-lookup"><span data-stu-id="9369f-123">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="9369f-124">例如，如果要路由至的目标终结点采用请求-答复通道形状，您必须在入站终结点上使用兼容协定，例如，<xref:System.ServiceModel.Routing.IRequestReplyRouter>。</span><span class="sxs-lookup"><span data-stu-id="9369f-124">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>  
  
 <span data-ttu-id="9369f-125">这意味着，如果目标终结点使用具有多种通信模式（例如单向和双向混合运行模式）的协定，您无法创建单一服务终结点来接收消息并将消息路由到所有目标终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-125">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="9369f-126">您必须确定哪些终结点具有兼容形状，并定义一个或多个服务终结点，这些服务终结点将用于接收要路由到目标终结点的消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-126">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9369f-127">当使用指定了多种通信模式（例如，单向和双向混合运行模式）的协定时，一种解决方法是在路由服务中使用双工协定，例如，<xref:System.ServiceModel.Routing.IDuplexSessionRouter>。</span><span class="sxs-lookup"><span data-stu-id="9369f-127">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="9369f-128">这意味着绑定必须支持双工通信，而这并非在所有情况下都能够实现。</span><span class="sxs-lookup"><span data-stu-id="9369f-128">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="9369f-129">在不可能实现双工通信的情况下，可能需要在多个终结点中考虑通信方式，或者修改应用程序。</span><span class="sxs-lookup"><span data-stu-id="9369f-129">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>  
  
 <span data-ttu-id="9369f-130">有关路由约定的详细信息, 请参阅[路由约定](routing-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="9369f-130">For more information about routing contracts, see [Routing Contracts](routing-contracts.md).</span></span>  
  
 <span data-ttu-id="9369f-131">定义服务终结点后, 可以使用**RoutingBehavior**将特定**RoutingConfiguration**与终结点相关联。</span><span class="sxs-lookup"><span data-stu-id="9369f-131">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="9369f-132">使用配置文件配置路由服务时, 将使用**RoutingBehavior**来指定筛选器表, 该表包含用于处理此终结点上接收的消息的路由逻辑。</span><span class="sxs-lookup"><span data-stu-id="9369f-132">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="9369f-133">如果以编程方式配置路由服务, 则可以使用**RoutingConfiguration**指定筛选器表。</span><span class="sxs-lookup"><span data-stu-id="9369f-133">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>  
  
 <span data-ttu-id="9369f-134">下面的示例定义路由服务按编程方式或通过使用配置文件来使用的服务和客户端终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-134">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>  
  
```xml  
    <services>  
      <!--ROUTING SERVICE -->  
      <service behaviorConfiguration="routingData"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/routingservice/router"/>  
          </baseAddresses>  
        </host>  
        <!-- Define the service endpoints that are receive messages -->  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  name="reqReplyEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="routingData">  
          <serviceMetadata httpGetEnabled="True"/>  
          <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
          <routing filterTableName="routingTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <client>  
    <!-- Define the client endpoint(s) to route messages to -->  
      <endpoint name="CalculatorService"  
                address="http://localhost:8000/servicemodelsamples/service"  
                binding="wsHttpBinding" contract="*" />  
    </client>  
```  
  
```csharp  
//set up some communication defaults  
string clientAddress = "http://localhost:8000/servicemodelsamples/service";  
string routerAddress = "http://localhost:8000/routingservice/router";  
Binding routerBinding = new WSHttpBinding();  
Binding clientBinding = new WSHttpBinding();  
//add the endpoint the router uses to receive messages  
serviceHost.AddServiceEndpoint(  
     typeof(IRequestReplyRouter),   
     routerBinding,   
     routerAddress);  
//create the client endpoint the router routes messages to  
ContractDescription contract = ContractDescription.GetContract(  
     typeof(IRequestReplyRouter));  
ServiceEndpoint client = new ServiceEndpoint(  
     contract,   
     clientBinding,   
     new EndpointAddress(clientAddress));  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
….  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
//attach the behavior to the service host  
serviceHost.Description.Behaviors.Add(  
     new RoutingBehavior(rc));  
```  
  
 <span data-ttu-id="9369f-135">此示例将路由服务配置为公开单个终结点`http://localhost:8000/routingservice/router`, 该地址用于接收要路由的消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-135">This example configures the Routing Service to expose a single endpoint with an address of `http://localhost:8000/routingservice/router`, which is used to receive messages to be routed.</span></span> <span data-ttu-id="9369f-136">由于消息路由到请求-答复终结点，因此该服务终结点使用 <xref:System.ServiceModel.Routing.IRequestReplyRouter> 协定。</span><span class="sxs-lookup"><span data-stu-id="9369f-136">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="9369f-137">此配置还定义将消息路由到的`http://localhost:8000/servicemodelsample/service`单个客户端终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-137">This configuration also defines a single client endpoint of `http://localhost:8000/servicemodelsample/service` that messages are routed to.</span></span> <span data-ttu-id="9369f-138">名为 "routingTable1" 的筛选器表 (未显示) 包含用于路由消息的路由逻辑, 并通过使用**RoutingBehavior** (适用于配置文件) 或**RoutingConfiguration** (适用于编程配置)。</span><span class="sxs-lookup"><span data-stu-id="9369f-138">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>  
  
### <a name="routing-logic"></a><span data-ttu-id="9369f-139">路由逻辑</span><span class="sxs-lookup"><span data-stu-id="9369f-139">Routing Logic</span></span>  
 <span data-ttu-id="9369f-140">若要定义用于路由消息的路由逻辑，必须确定传入消息包含的哪些数据可以采用唯一方式执行操作。</span><span class="sxs-lookup"><span data-stu-id="9369f-140">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="9369f-141">例如，如果要路由到的所有目标终结点共享相同的 SOAP 操作，则消息中包含的 Action 的值无法很好地指示应将消息路由到的特定终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-141">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="9369f-142">如果必须以唯一方式将消息路由至某一特定终结点，您应当根据唯一标识消息将路由至的目标终结点的数据进行筛选。</span><span class="sxs-lookup"><span data-stu-id="9369f-142">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>  
  
 <span data-ttu-id="9369f-143">路由服务提供多个**MessageFilter**实现, 这些实现检查消息中的特定值, 如地址、操作、终结点名称甚至是 XPath 查询。</span><span class="sxs-lookup"><span data-stu-id="9369f-143">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="9369f-144">如果这些实现都不能满足你的需求, 则可以创建自定义**MessageFilter**实现。</span><span class="sxs-lookup"><span data-stu-id="9369f-144">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="9369f-145">有关消息筛选器和路由服务使用的实现比较的详细信息, 请参阅[消息筛选](message-filters.md)器和[选择筛选器](choosing-a-filter.md)。</span><span class="sxs-lookup"><span data-stu-id="9369f-145">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](message-filters.md) and [Choosing a Filter](choosing-a-filter.md).</span></span>  
  
 <span data-ttu-id="9369f-146">多个消息筛选器组合到不同的筛选器表中, 后者将每个**MessageFilter**与目标终结点相关联。</span><span class="sxs-lookup"><span data-stu-id="9369f-146">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="9369f-147">或者，也可以使用筛选器表指定一个备份终结点列表，当传输失败时，路由服务将尝试向这些终结点发送消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-147">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>  
  
 <span data-ttu-id="9369f-148">默认情况下，将同时计算筛选器表中的所有消息筛选器；但是，您可以指定 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A>，以便按特定顺序计算消息筛选器。</span><span class="sxs-lookup"><span data-stu-id="9369f-148">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="9369f-149">将首先计算具有最高优先级的所有条目，如果在较高优先级级别中找到匹配项，则不会计算具有较低优先级的消息筛选器。</span><span class="sxs-lookup"><span data-stu-id="9369f-149">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="9369f-150">有关筛选器表的详细信息, 请参阅[消息筛选器](message-filters.md)。</span><span class="sxs-lookup"><span data-stu-id="9369f-150">For more information about filter tables, see [Message Filters](message-filters.md).</span></span>  
  
 <span data-ttu-id="9369f-151">下面的示例使用 <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>，它对所有消息的计算结果均为 `true`。</span><span class="sxs-lookup"><span data-stu-id="9369f-151">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="9369f-152">此**MessageFilter**将添加到 "routingTable1" 筛选器表, 该表将**MessageFilter**与名为 "CalculatorService" 的客户端终结点相关联。</span><span class="sxs-lookup"><span data-stu-id="9369f-152">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="9369f-153">然后, **RoutingBehavior**指定应使用该表来路由由服务终结点处理的消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-153">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="routingData">  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->  
      <routing filterTableName="routingTable1" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
//create a new routing configuration object  
RoutingConfiguration rc = new RoutingConfiguration();  
//create the endpoint list that contains the endpoints to route to  
//in this case we have only one  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
//add a MatchAll filter to the Router's filter table  
//map it to the endpoint list defined earlier  
//when a message matches this filter, it is sent to the endpoint contained in the list  
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
```  
  
> [!NOTE]
> <span data-ttu-id="9369f-154">默认情况下，路由服务仅计算消息标头。</span><span class="sxs-lookup"><span data-stu-id="9369f-154">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="9369f-155">若要使筛选器访问消息正文，必须将 <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> 设置为 `false`。</span><span class="sxs-lookup"><span data-stu-id="9369f-155">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>  
  
 <span data-ttu-id="9369f-156">**路**</span><span class="sxs-lookup"><span data-stu-id="9369f-156">**Multicast**</span></span>  
  
 <span data-ttu-id="9369f-157">许多路由服务配置都采用将消息仅路由至一个特定终结点的专有筛选器逻辑，但是，您可能需要将给定消息路由至多个目标终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-157">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="9369f-158">若要将消息多播到多个目标，必须满足以下条件：</span><span class="sxs-lookup"><span data-stu-id="9369f-158">To multicast a message to multiple destinations, the following conditions must be true:</span></span>  
  
- <span data-ttu-id="9369f-159">通道形状不能为请求-答复（但可以为单向或双工），因为客户端应用程序在响应请求时只能接收一个答复。</span><span class="sxs-lookup"><span data-stu-id="9369f-159">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>  
  
- <span data-ttu-id="9369f-160">多个筛选器在计算消息时必须返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="9369f-160">Multiple filters must return `true` when evaluating the message.</span></span>  
  
 <span data-ttu-id="9369f-161">如果满足这些条件，则将消息路由至计算结果为 `true` 的所有筛选器的所有终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-161">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="9369f-162">下面的示例定义路由的配置会导致消息同时路由至两个终结点，如果消息中的终结点地址为 `http://localhost:8000/routingservice/router/rounding` 。</span><span class="sxs-lookup"><span data-stu-id="9369f-162">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is `http://localhost:8000/routingservice/router/rounding`.</span></span>  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
    <filter name="RoundingFilter1" filterType="EndpointAddress"  
            filterData="http://localhost:8000/routingservice/router/rounding" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />  
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);  
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(  
    "http://localhost:8000/routingservice/router/rounding")),  
    roundingCalcEndpointList);  
```  
  
### <a name="soap-processing"></a><span data-ttu-id="9369f-163">SOAP 处理</span><span class="sxs-lookup"><span data-stu-id="9369f-163">SOAP Processing</span></span>  
 <span data-ttu-id="9369f-164">为了支持在不同协议之间路由消息, 默认情况下, **RoutingBehavior**将添加<xref:System.ServiceModel.Routing.SoapProcessingBehavior>到消息路由到的所有客户端终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-164">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="9369f-165">此行为在将消息路由到终结点之前, 会自动创建新的**MessageVersion** , 并在将其返回给发出请求的客户端应用程序之前为任何响应文档创建兼容的**MessageVersion** 。</span><span class="sxs-lookup"><span data-stu-id="9369f-165">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>  
  
 <span data-ttu-id="9369f-166">为出站消息创建新**MessageVersion**所采取的步骤如下所示:</span><span class="sxs-lookup"><span data-stu-id="9369f-166">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>  
  
 <span data-ttu-id="9369f-167">**请求处理**</span><span class="sxs-lookup"><span data-stu-id="9369f-167">**Request processing**</span></span>  
  
- <span data-ttu-id="9369f-168">获取出站绑定/通道的**MessageVersion** 。</span><span class="sxs-lookup"><span data-stu-id="9369f-168">Get the **MessageVersion** of the outbound binding/channel.</span></span>  
  
- <span data-ttu-id="9369f-169">获取原始消息的正文读取器。</span><span class="sxs-lookup"><span data-stu-id="9369f-169">Get the body reader for the original message.</span></span>  
  
- <span data-ttu-id="9369f-170">使用相同操作、正文读取器和新的**MessageVersion**创建一条新消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-170">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>  
  
- <span data-ttu-id="9369f-171">如果<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! =**寻址**, 则将从、从、FaultTo 和 RelatesTo 标头复制到新消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-171">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
- <span data-ttu-id="9369f-172">将所有消息属性复制到新消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-172">Copy all message properties to the new message.</span></span>  
  
- <span data-ttu-id="9369f-173">存储原始请求消息，以备在处理响应时使用。</span><span class="sxs-lookup"><span data-stu-id="9369f-173">Store the original request message to use when processing the response.</span></span>  
  
- <span data-ttu-id="9369f-174">返回新的请求消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-174">Return the new request message.</span></span>  
  
 <span data-ttu-id="9369f-175">**响应处理**</span><span class="sxs-lookup"><span data-stu-id="9369f-175">**Response processing**</span></span>  
  
- <span data-ttu-id="9369f-176">获取原始请求消息的**MessageVersion** 。</span><span class="sxs-lookup"><span data-stu-id="9369f-176">Get the **MessageVersion** of the original request message.</span></span>  
  
- <span data-ttu-id="9369f-177">获取接收的响应消息的正文读取器。</span><span class="sxs-lookup"><span data-stu-id="9369f-177">Get the body reader for the received response message.</span></span>  
  
- <span data-ttu-id="9369f-178">使用相同操作、正文读取器和原始请求消息的**MessageVersion**创建新的响应消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-178">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>  
  
- <span data-ttu-id="9369f-179">如果<xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> ! =**寻址**, 则将从、从、FaultTo 和 RelatesTo 标头复制到新消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-179">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>  
  
- <span data-ttu-id="9369f-180">将所有消息属性复制到新消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-180">Copy the message properties to the new message.</span></span>  
  
- <span data-ttu-id="9369f-181">返回新的响应消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-181">Return the new response message.</span></span>  
  
 <span data-ttu-id="9369f-182">默认情况下, <xref:System.ServiceModel.Routing.RoutingBehavior>当服务启动时, SoapProcessingBehavior 会自动添加到客户端终结点; 但是, 你可以通过使用<xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A>属性来控制是否将 SOAP 处理添加到所有客户端终结点.</span><span class="sxs-lookup"><span data-stu-id="9369f-182">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="9369f-183">此外，如果需要更为精细地控制 SOAP 处理，您还可以向特定终结点直接添加该行为，并在终结点级别上启用或禁用该行为。</span><span class="sxs-lookup"><span data-stu-id="9369f-183">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9369f-184">对于所需的 MessageVersion 不同于原始请求消息的 MessageVersion 的终结点，如果要禁用 SOAP 处理，则必须提供自定义机制，以便在将消息发送到目标终结点之前执行所有必要的 SOAP 修改。</span><span class="sxs-lookup"><span data-stu-id="9369f-184">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>  
  
 <span data-ttu-id="9369f-185">在下面的示例中, **soapProcessingEnabled**属性用于阻止**SoapProcessingBehavior**自动添加到所有客户端终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-185">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>  
  
```xml  
<behaviors>  
  <!--default routing service behavior definition-->  
  <serviceBehaviors>  
    <behavior name="routingConfiguration">  
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
```csharp  
//create the default RoutingConfiguration  
RoutingConfiguration rc = new RoutingConfiguration();  
rc.SoapProcessingEnabled = false;  
```  
  
### <a name="dynamic-configuration"></a><span data-ttu-id="9369f-186">动态配置</span><span class="sxs-lookup"><span data-stu-id="9369f-186">Dynamic Configuration</span></span>  
 <span data-ttu-id="9369f-187">当添加其他客户端终结点或需要修改用于路由消息的筛选器时，您必须采用某种方法在运行时动态更新配置，以免中断当前正在通过路由服务接收消息的终结点的服务。</span><span class="sxs-lookup"><span data-stu-id="9369f-187">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="9369f-188">修改配置文件或宿主应用程序的代码不一定能够始终满足需求，这是因为两种方法都需要回收应用程序，这可能导致丢失当前正在传输的任何消息，并可能在等待服务重新启动时发生停机。</span><span class="sxs-lookup"><span data-stu-id="9369f-188">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>  
  
 <span data-ttu-id="9369f-189">只能以编程方式修改**RoutingConfiguration** 。</span><span class="sxs-lookup"><span data-stu-id="9369f-189">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="9369f-190">虽然最初可以使用配置文件来配置服务, 但只能在运行时通过构造新的**RoutingConfiguration**并将其作为参数传递给公开<xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> <xref:System.ServiceModel.Routing.RoutingExtension>的方法来修改配置。服务扩展。</span><span class="sxs-lookup"><span data-stu-id="9369f-190">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfiguration** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="9369f-191">当前正在传输的任何消息都将继续使用以前的配置进行路由, 而在对**ApplyConfiguration**的调用后收到的消息将使用新的配置。</span><span class="sxs-lookup"><span data-stu-id="9369f-191">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="9369f-192">下面的示例演示如何创建路由服务的实例并随后修改配置。</span><span class="sxs-lookup"><span data-stu-id="9369f-192">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>  
  
```csharp  
RoutingConfiguration routingConfig = new RoutingConfiguration();  
routingConfig.RouteOnHeadersOnly = true;  
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);  
RoutingBehavior routing = new RoutingBehavior(routingConfig);  
routerHost.Description.Behaviors.Add(routing);  
routerHost.Open();  
// Construct a new RoutingConfiguration  
RoutingConfiguration rc2 = new RoutingConfiguration();  
ServiceEndpoint clientEndpoint = new ServiceEndpoint();  
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();  
// Add filters to the FilterTable in the new configuration  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint });  
rc2.FilterTable.add(new MatchAllMessageFilter(),  
       new List<ServiceEndpoint>() { clientEndpoint2 });  
rc2.RouteOnHeadersOnly = false;  
// Apply the new configuration to the Routing Service hosted in  
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);  
```  
  
> [!NOTE]
> <span data-ttu-id="9369f-193">如果采用此种方式更新路由服务，则只能传递新配置。</span><span class="sxs-lookup"><span data-stu-id="9369f-193">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="9369f-194">无法仅修改当前配置的选定元素，也不能向现有配置追加新条目；必须创建并传递用于替换现有配置的新配置。</span><span class="sxs-lookup"><span data-stu-id="9369f-194">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9369f-195">使用以前的配置打开的所有会话都将继续使用以前的配置。</span><span class="sxs-lookup"><span data-stu-id="9369f-195">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="9369f-196">新配置仅用于新会话。</span><span class="sxs-lookup"><span data-stu-id="9369f-196">The new configuration is only used by new sessions.</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="9369f-197">错误处理</span><span class="sxs-lookup"><span data-stu-id="9369f-197">Error Handling</span></span>  
 <span data-ttu-id="9369f-198">如果在尝试发送消息时遇到任何 <xref:System.ServiceModel.CommunicationException>，将会进行错误处理。</span><span class="sxs-lookup"><span data-stu-id="9369f-198">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="9369f-199">这些异常通常指示在尝试与定义的客户端终结点进行通信时遇到了问题，例如 <xref:System.ServiceModel.EndpointNotFoundException>、<xref:System.ServiceModel.ServerTooBusyException> 或 <xref:System.ServiceModel.CommunicationObjectFaultedException>。</span><span class="sxs-lookup"><span data-stu-id="9369f-199">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="9369f-200">错误处理-代码还将捕获并尝试在<xref:System.TimeoutException>发生时重试发送, 这是不是派生自**CommunicationException**的另一个常见异常。</span><span class="sxs-lookup"><span data-stu-id="9369f-200">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>  
  
 <span data-ttu-id="9369f-201">如果发生上述一种异常，路由服务会向备份终结点列表进行故障转移。</span><span class="sxs-lookup"><span data-stu-id="9369f-201">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="9369f-202">如果所有备份终结点均失败并出现通信故障，或者如果某个终结点返回指示目标服务内部故障的异常，路由服务则会向客户端应用程序返回错误。</span><span class="sxs-lookup"><span data-stu-id="9369f-202">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9369f-203">错误处理功能捕获并处理在尝试发送消息和尝试关闭通道时发生的异常。</span><span class="sxs-lookup"><span data-stu-id="9369f-203">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="9369f-204">错误处理代码不用于检测或处理由其通信的应用程序终结点所创建的异常;服务<xref:System.ServiceModel.FaultException>引发的由**FaultMessage**在路由服务中显示, 并流向客户端。</span><span class="sxs-lookup"><span data-stu-id="9369f-204">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>  
>   
>  <span data-ttu-id="9369f-205">如果在路由服务尝试中继消息时出现错误，则您可能会在客户端收到 <xref:System.ServiceModel.FaultException>，而不是在缺少路由服务时通常收到的 <xref:System.ServiceModel.EndpointNotFoundException>。</span><span class="sxs-lookup"><span data-stu-id="9369f-205">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="9369f-206">路由服务因而可能屏蔽异常，不会提供完全透明度，除非您检查嵌套异常。</span><span class="sxs-lookup"><span data-stu-id="9369f-206">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>  
  
### <a name="tracing-exceptions"></a><span data-ttu-id="9369f-207">跟踪异常</span><span class="sxs-lookup"><span data-stu-id="9369f-207">Tracing Exceptions</span></span>  
 <span data-ttu-id="9369f-208">当向列表中的终结点发送消息失败时, 路由服务将跟踪产生的异常数据, 并将异常详细信息作为名为 exception的消息属性附加。</span><span class="sxs-lookup"><span data-stu-id="9369f-208">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="9369f-209">这可以保存异常数据，并允许用户通过消息检查器进行编程访问。</span><span class="sxs-lookup"><span data-stu-id="9369f-209">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="9369f-210">异常数据根据消息存储在字典中，该字段将终结点名称映射到在尝试向其发送消息时遇到的异常的详细信息。</span><span class="sxs-lookup"><span data-stu-id="9369f-210">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>  
  
### <a name="backup-endpoints"></a><span data-ttu-id="9369f-211">备份终结点</span><span class="sxs-lookup"><span data-stu-id="9369f-211">Backup Endpoints</span></span>  
 <span data-ttu-id="9369f-212">筛选器表中的各个筛选器条目可以选择指定一个备份终结点列表，如果在向主终结点发送消息时出现传输故障，则会使用这些备份终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-212">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="9369f-213">如果出现此类故障，路由服务会尝试将消息传输到备份终结点列表中的第一个条目。</span><span class="sxs-lookup"><span data-stu-id="9369f-213">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="9369f-214">如果此发送尝试同样遇到传输故障，则会尝试备份列表中的下一个终结点。</span><span class="sxs-lookup"><span data-stu-id="9369f-214">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="9369f-215">路由服务将继续向列表中的每个终结点发送消息，直到成功接收此消息、所有终结点均返回传输故障或某个终结点返回非传输故障为止。</span><span class="sxs-lookup"><span data-stu-id="9369f-215">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>  
  
 <span data-ttu-id="9369f-216">下面的示例将路由服务配置为使用备份列表。</span><span class="sxs-lookup"><span data-stu-id="9369f-216">The following examples configure the Routing Service to use a backup list.</span></span>  
  
```xml  
<routing>  
  <filters>  
    <!-- Create a MatchAll filter that catches all messages -->  
    <filter name="MatchAllFilter1" filterType="MatchAll" />  
  </filters>  
  <filterTables>  
    <!-- Set up the Routing Service's Message Filter Table -->  
    <filterTable name="filterTable1">  
        <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->  
        <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->  
        <!-- Listed in the backupEndpointList -->  
        <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>  
    </filterTable>  
  </filterTables>  
  <!-- Create the backup endpoint list -->  
  <backupLists>  
    <!-- Add an endpoint list that contains the backup destinations -->  
    <backupList name="backupEndpointList">  
      <add endpointName="realDestination" />  
      <add endpointName="backupDestination" />  
    </backupList>  
  </backupLists>  
</routing>  
```  
  
```csharp  
//create the endpoint list that contains the service endpoints we want to route to  
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();  
//add the endpoints in the order that the Routing Service should contact them  
//first add the endpoint that we know is down  
//clearly, normally you wouldn't know that this endpoint was down by default  
backupList.Add(fakeDestination);  
//then add the real Destination endpoint  
//the Routing Service attempts to send to this endpoint only if it   
//encounters a TimeOutException or CommunicationException when sending  
//to the previous endpoint in the list.  
backupList.Add(realDestination);  
//add the backupDestination endpoint  
//the Routing Service attempts to send to this endpoint only if it  
//encounters a TimeOutException or CommunicationsException when sending  
//to the previous endpoints in the list  
backupList.Add(backupDestination);  
//create the default RoutingConfiguration option              
RoutingConfiguration rc = new RoutingConfiguration();  
//add a MatchAll filter to the Routing Configuration's filter table  
//map it to the list of endpoints defined above  
//when a message matches this filter, it is sent to the endpoints in the list in order  
//if an endpoint is down or does not respond (which the first endpoint won't  
//since the client does not exist), the Routing Service automatically moves the message  
//to the next endpoint in the list and try again.  
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);  
```  
  
### <a name="supported-error-patterns"></a><span data-ttu-id="9369f-217">支持的错误模式</span><span class="sxs-lookup"><span data-stu-id="9369f-217">Supported Error Patterns</span></span>  
 <span data-ttu-id="9369f-218">下表说明了与使用备份终结点列表相兼容的模式，并提供了特定模式的错误处理详细信息的说明。</span><span class="sxs-lookup"><span data-stu-id="9369f-218">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>  
  
|<span data-ttu-id="9369f-219">模式</span><span class="sxs-lookup"><span data-stu-id="9369f-219">Pattern</span></span>|<span data-ttu-id="9369f-220">会话</span><span class="sxs-lookup"><span data-stu-id="9369f-220">Session</span></span>|<span data-ttu-id="9369f-221">事务</span><span class="sxs-lookup"><span data-stu-id="9369f-221">Transaction</span></span>|<span data-ttu-id="9369f-222">接收上下文</span><span class="sxs-lookup"><span data-stu-id="9369f-222">Receive Context</span></span>|<span data-ttu-id="9369f-223">是否支持备份列表</span><span class="sxs-lookup"><span data-stu-id="9369f-223">Backup List Supported</span></span>|<span data-ttu-id="9369f-224">说明</span><span class="sxs-lookup"><span data-stu-id="9369f-224">Notes</span></span>|  
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|  
|<span data-ttu-id="9369f-225">单向</span><span class="sxs-lookup"><span data-stu-id="9369f-225">One-Way</span></span>||||<span data-ttu-id="9369f-226">是</span><span class="sxs-lookup"><span data-stu-id="9369f-226">Yes</span></span>|<span data-ttu-id="9369f-227">尝试在备份终结点上重新发送消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-227">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="9369f-228">如果正在多播此消息，则仅将故障通道上的消息移至其备份目标。</span><span class="sxs-lookup"><span data-stu-id="9369f-228">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|  
|<span data-ttu-id="9369f-229">单向</span><span class="sxs-lookup"><span data-stu-id="9369f-229">One-Way</span></span>||<span data-ttu-id="9369f-230">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-230">✓</span></span>||<span data-ttu-id="9369f-231">No</span><span class="sxs-lookup"><span data-stu-id="9369f-231">No</span></span>|<span data-ttu-id="9369f-232">引发异常，并回滚事务。</span><span class="sxs-lookup"><span data-stu-id="9369f-232">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="9369f-233">单向</span><span class="sxs-lookup"><span data-stu-id="9369f-233">One-Way</span></span>|||<span data-ttu-id="9369f-234">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-234">✓</span></span>|<span data-ttu-id="9369f-235">是</span><span class="sxs-lookup"><span data-stu-id="9369f-235">Yes</span></span>|<span data-ttu-id="9369f-236">尝试在备份终结点上重新发送消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-236">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="9369f-237">成功接收消息后，完成所有接收上下文。</span><span class="sxs-lookup"><span data-stu-id="9369f-237">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="9369f-238">如果任何终结点未成功接收消息，则不会完成接收上下文。</span><span class="sxs-lookup"><span data-stu-id="9369f-238">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="9369f-239">如果正在多播此消息，仅当至少有一个终结点（主终结点或备份终结点）已成功接收消息时，才会完成接收上下文。</span><span class="sxs-lookup"><span data-stu-id="9369f-239">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="9369f-240">如果所有多播路径中没有任何终结点成功接收消息，则不会完成接收上下文。</span><span class="sxs-lookup"><span data-stu-id="9369f-240">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|  
|<span data-ttu-id="9369f-241">单向</span><span class="sxs-lookup"><span data-stu-id="9369f-241">One-Way</span></span>||<span data-ttu-id="9369f-242">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-242">✓</span></span>|<span data-ttu-id="9369f-243">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-243">✓</span></span>|<span data-ttu-id="9369f-244">是</span><span class="sxs-lookup"><span data-stu-id="9369f-244">Yes</span></span>|<span data-ttu-id="9369f-245">中止先前事务，创建新事务，并重新发送所有消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-245">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="9369f-246">遇到错误的消息将传输到备份目标。</span><span class="sxs-lookup"><span data-stu-id="9369f-246">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="9369f-247">在创建已成功完成其中的所有传输的事务之后，完成接收上下文并提交该事务。</span><span class="sxs-lookup"><span data-stu-id="9369f-247">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|  
|<span data-ttu-id="9369f-248">单向</span><span class="sxs-lookup"><span data-stu-id="9369f-248">One-Way</span></span>|<span data-ttu-id="9369f-249">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-249">✓</span></span>|||<span data-ttu-id="9369f-250">是</span><span class="sxs-lookup"><span data-stu-id="9369f-250">Yes</span></span>|<span data-ttu-id="9369f-251">尝试在备份终结点上重新发送消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-251">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="9369f-252">在多播情况下，仅向备份目标重新发送已遇到错误或其会话关闭失败的消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-252">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|  
|<span data-ttu-id="9369f-253">单向</span><span class="sxs-lookup"><span data-stu-id="9369f-253">One-Way</span></span>|<span data-ttu-id="9369f-254">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-254">✓</span></span>|<span data-ttu-id="9369f-255">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-255">✓</span></span>||<span data-ttu-id="9369f-256">No</span><span class="sxs-lookup"><span data-stu-id="9369f-256">No</span></span>|<span data-ttu-id="9369f-257">引发异常，并回滚事务。</span><span class="sxs-lookup"><span data-stu-id="9369f-257">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="9369f-258">单向</span><span class="sxs-lookup"><span data-stu-id="9369f-258">One-Way</span></span>|<span data-ttu-id="9369f-259">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-259">✓</span></span>||<span data-ttu-id="9369f-260">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-260">✓</span></span>|<span data-ttu-id="9369f-261">是</span><span class="sxs-lookup"><span data-stu-id="9369f-261">Yes</span></span>|<span data-ttu-id="9369f-262">尝试在备份终结点上重新发送消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-262">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="9369f-263">在完成所有消息发送操作且未发生错误之后，会话将指示没有任何其他消息，路由服务将成功关闭所有出站会话通道，将完成所有接收上下文，并关闭入站会话通道。</span><span class="sxs-lookup"><span data-stu-id="9369f-263">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|  
|<span data-ttu-id="9369f-264">单向</span><span class="sxs-lookup"><span data-stu-id="9369f-264">One-Way</span></span>|<span data-ttu-id="9369f-265">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-265">✓</span></span>|<span data-ttu-id="9369f-266">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-266">✓</span></span>|<span data-ttu-id="9369f-267">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-267">✓</span></span>|<span data-ttu-id="9369f-268">是</span><span class="sxs-lookup"><span data-stu-id="9369f-268">Yes</span></span>|<span data-ttu-id="9369f-269">中止当前事务，并创建新事务。</span><span class="sxs-lookup"><span data-stu-id="9369f-269">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="9369f-270">重新发送会话中以前的所有消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-270">Resend all previous messages in the session.</span></span> <span data-ttu-id="9369f-271">在创建已成功发送其中的所有消息的事务，并且会话指示没有任何其他消息之后，将关闭所有出站会话通道，使用事务完成所有接收上下文，关闭入站会话通道，并提交该事务。</span><span class="sxs-lookup"><span data-stu-id="9369f-271">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="9369f-272">如果会话是多播会话，无任何错误的消息将重新发送到与以前相同的目标，而遇到错误的消息将发送到备份目标。</span><span class="sxs-lookup"><span data-stu-id="9369f-272">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|  
|<span data-ttu-id="9369f-273">双向</span><span class="sxs-lookup"><span data-stu-id="9369f-273">Two-Way</span></span>||||<span data-ttu-id="9369f-274">是</span><span class="sxs-lookup"><span data-stu-id="9369f-274">Yes</span></span>|<span data-ttu-id="9369f-275">发送到备份目标。</span><span class="sxs-lookup"><span data-stu-id="9369f-275">Send to a backup destination.</span></span>  <span data-ttu-id="9369f-276">在通道返回响应消息之后，系统会将响应返回到原始客户端。</span><span class="sxs-lookup"><span data-stu-id="9369f-276">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="9369f-277">双向</span><span class="sxs-lookup"><span data-stu-id="9369f-277">Two-Way</span></span>|<span data-ttu-id="9369f-278">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-278">✓</span></span>|||<span data-ttu-id="9369f-279">是</span><span class="sxs-lookup"><span data-stu-id="9369f-279">Yes</span></span>|<span data-ttu-id="9369f-280">将通道中的所有消息发送到备份目标。</span><span class="sxs-lookup"><span data-stu-id="9369f-280">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="9369f-281">在通道返回响应消息之后，系统会将响应返回到原始客户端。</span><span class="sxs-lookup"><span data-stu-id="9369f-281">After a channel returns a response message, return the response to the original client.</span></span>|  
|<span data-ttu-id="9369f-282">双向</span><span class="sxs-lookup"><span data-stu-id="9369f-282">Two-Way</span></span>||<span data-ttu-id="9369f-283">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-283">✓</span></span>||<span data-ttu-id="9369f-284">No</span><span class="sxs-lookup"><span data-stu-id="9369f-284">No</span></span>|<span data-ttu-id="9369f-285">引发异常，并回滚事务。</span><span class="sxs-lookup"><span data-stu-id="9369f-285">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="9369f-286">双向</span><span class="sxs-lookup"><span data-stu-id="9369f-286">Two-Way</span></span>|<span data-ttu-id="9369f-287">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-287">✓</span></span>|<span data-ttu-id="9369f-288">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-288">✓</span></span>||<span data-ttu-id="9369f-289">No</span><span class="sxs-lookup"><span data-stu-id="9369f-289">No</span></span>|<span data-ttu-id="9369f-290">引发异常，并回滚事务。</span><span class="sxs-lookup"><span data-stu-id="9369f-290">An exception is thrown and the transaction is rolled back.</span></span>|  
|<span data-ttu-id="9369f-291">双工</span><span class="sxs-lookup"><span data-stu-id="9369f-291">Duplex</span></span>||||<span data-ttu-id="9369f-292">No</span><span class="sxs-lookup"><span data-stu-id="9369f-292">No</span></span>|<span data-ttu-id="9369f-293">当前不支持非会话双工通信。</span><span class="sxs-lookup"><span data-stu-id="9369f-293">Non-session duplex communication is not currently supported.</span></span>|  
|<span data-ttu-id="9369f-294">双工</span><span class="sxs-lookup"><span data-stu-id="9369f-294">Duplex</span></span>|<span data-ttu-id="9369f-295">✓</span><span class="sxs-lookup"><span data-stu-id="9369f-295">✓</span></span>|||<span data-ttu-id="9369f-296">是</span><span class="sxs-lookup"><span data-stu-id="9369f-296">Yes</span></span>|<span data-ttu-id="9369f-297">发送到备份目标。</span><span class="sxs-lookup"><span data-stu-id="9369f-297">Send to a backup destination.</span></span>|  
  
## <a name="hosting"></a><span data-ttu-id="9369f-298">宿主</span><span class="sxs-lookup"><span data-stu-id="9369f-298">Hosting</span></span>  
 <span data-ttu-id="9369f-299">由于路由服务是作为 WCF 服务实现的，因此它必须自承载在应用程序中，或者由 IIS 或 WAS 承载。</span><span class="sxs-lookup"><span data-stu-id="9369f-299">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="9369f-300">建议在 IIS、WAS 或 Windows 服务应用程序中承载路由服务，以便利用这些宿主环境中提供的自动启动和生命周期管理功能。</span><span class="sxs-lookup"><span data-stu-id="9369f-300">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>  
  
 <span data-ttu-id="9369f-301">下面的示例演示如何在应用程序中承载路由服务。</span><span class="sxs-lookup"><span data-stu-id="9369f-301">The following example demonstrates hosting the Routing Service in an application.</span></span>  
  
```csharp  
using (ServiceHost serviceHost =  
                new ServiceHost(typeof(RoutingService)))  
```  
  
 <span data-ttu-id="9369f-302">若要在 IIS 或 WAS 中承载路由服务，您必须创建服务文件 (.svc) 或使用基于配置的服务激活功能。</span><span class="sxs-lookup"><span data-stu-id="9369f-302">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="9369f-303">当使用服务文件时，必须使用 Service 参数指定 <xref:System.ServiceModel.Routing.RoutingService>。</span><span class="sxs-lookup"><span data-stu-id="9369f-303">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="9369f-304">下面的示例包含一个示例服务文件，它可用于在 IIS 或 WAS 中承载路由服务。</span><span class="sxs-lookup"><span data-stu-id="9369f-304">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>  
  
```  
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,   
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,   
     PublicKeyToken=31bf3856ad364e35" %>  
```  
  
## <a name="routing-service-and-impersonation"></a><span data-ttu-id="9369f-305">路由服务和模拟</span><span class="sxs-lookup"><span data-stu-id="9369f-305">Routing Service and Impersonation</span></span>  
 <span data-ttu-id="9369f-306">WCF 路由服务可以与模拟结合使用来发送和接收消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-306">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="9369f-307">模拟的所有常用 Windows 约束将适用。</span><span class="sxs-lookup"><span data-stu-id="9369f-307">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="9369f-308">如果您在编写自己的服务时需要设置服务或帐户权限才能使用模拟，则必须执行这些相同步骤，从而将模拟用于路由服务。</span><span class="sxs-lookup"><span data-stu-id="9369f-308">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="9369f-309">有关详细信息, 请参阅[委派和模拟](delegation-and-impersonation-with-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="9369f-309">For more information, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>  
  
 <span data-ttu-id="9369f-310">将模拟用于路由服务要求在 ASP.NET 兼容模式下使用 ASP.NET 模拟，或使用已配置为允许模拟的 Windows 凭据。</span><span class="sxs-lookup"><span data-stu-id="9369f-310">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="9369f-311">有关 ASP.NET 兼容模式的详细信息, 请参阅[WCF 服务和 ASP.NET](wcf-services-and-aspnet.md)。</span><span class="sxs-lookup"><span data-stu-id="9369f-311">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="9369f-312">WCF 路由服务不支持将模拟用于基本身份验证。</span><span class="sxs-lookup"><span data-stu-id="9369f-312">The WCF Routing Service does not support impersonation with basic authentication.</span></span>  
  
 <span data-ttu-id="9369f-313">要将 ASP 模拟用于路由服务，可对服务承载环境启用 ASP.NET 兼容模式。</span><span class="sxs-lookup"><span data-stu-id="9369f-313">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="9369f-314">路由服务已被标记为允许 ASP.NET 兼容模式，并且模拟会自动启用。</span><span class="sxs-lookup"><span data-stu-id="9369f-314">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="9369f-315">模拟是将 ASP.NET 与路由服务相集成的唯一支持的用法。</span><span class="sxs-lookup"><span data-stu-id="9369f-315">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>  
  
 <span data-ttu-id="9369f-316">要将 Windows 凭据模拟用于路由服务，您需要同时配置凭据和服务。</span><span class="sxs-lookup"><span data-stu-id="9369f-316">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="9369f-317">客户端凭据对象（<xref:System.ServiceModel.Security.WindowsClientCredential>，可从 <xref:System.ServiceModel.ChannelFactory> 访问）定义了一个 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 属性，此属性必须设置为允许模拟。</span><span class="sxs-lookup"><span data-stu-id="9369f-317">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="9369f-318">最后，您需要在服务上配置 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 行为，以便将 `ImpersonateCallerForAllOperations` 设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="9369f-318">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="9369f-319">路由服务使用此标志来决定是否创建客户端，以便转发启用模拟的消息。</span><span class="sxs-lookup"><span data-stu-id="9369f-319">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9369f-320">请参阅</span><span class="sxs-lookup"><span data-stu-id="9369f-320">See also</span></span>

- [<span data-ttu-id="9369f-321">消息筛选器</span><span class="sxs-lookup"><span data-stu-id="9369f-321">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="9369f-322">路由协定</span><span class="sxs-lookup"><span data-stu-id="9369f-322">Routing Contracts</span></span>](routing-contracts.md)
- [<span data-ttu-id="9369f-323">选择筛选器</span><span class="sxs-lookup"><span data-stu-id="9369f-323">Choosing a Filter</span></span>](choosing-a-filter.md)
