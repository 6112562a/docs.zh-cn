---
title: 从 .NET 远程处理迁移到 WCF
ms.date: 03/30/2017
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
ms.openlocfilehash: 4b6996b01da6312486649482ffbb812fcb021306
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452547"
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="c67f0-102">从 .NET 远程处理迁移到 WCF</span><span class="sxs-lookup"><span data-stu-id="c67f0-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="c67f0-103">本文介绍如何迁移借助 .NET 远程处理来使用 Windows Communication Foundation (WCF) 的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c67f0-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="c67f0-104">本文对这些产品之间的相似概念进行比较，并介绍如何在 WCF 中完成若干常见的远程处理方案。</span><span class="sxs-lookup"><span data-stu-id="c67f0-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="c67f0-105">.NET 远程处理是一项传统技术，仅支持向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="c67f0-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="c67f0-106">由于它无法保持客户端和服务器之间的单独信任级别，因此它在混合信任环境中并不安全。</span><span class="sxs-lookup"><span data-stu-id="c67f0-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="c67f0-107">例如，你绝不应将 .NET 远程处理终结点公开到 Internet 或不受信任的客户端中。</span><span class="sxs-lookup"><span data-stu-id="c67f0-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="c67f0-108">我们建议将现有的远程处理应用程序迁移到更新和更安全的技术中。</span><span class="sxs-lookup"><span data-stu-id="c67f0-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="c67f0-109">如果应用程序的设计仅使用 HTTP 并且为 RESTful，那么我们建议迁移到 ASP.NET Web API。</span><span class="sxs-lookup"><span data-stu-id="c67f0-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="c67f0-110">有关详细信息，请参阅 ASP.NET Web API。</span><span class="sxs-lookup"><span data-stu-id="c67f0-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="c67f0-111">如果应用程序基于 SOAP，或者需要非 Http 协议（如 TCP），那么我们建议迁移到 WCF。</span><span class="sxs-lookup"><span data-stu-id="c67f0-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="c67f0-112">比较 .NET 远程处理与 WCF</span><span class="sxs-lookup"><span data-stu-id="c67f0-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="c67f0-113">本节将对 .NET 远程处理的基本构建基块与其 WCF 等效物进行比较。</span><span class="sxs-lookup"><span data-stu-id="c67f0-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="c67f0-114">稍后我们将使用这些构建基块在 WCF 中创建一些常见的客户端服务器方案。</span><span class="sxs-lookup"><span data-stu-id="c67f0-114">We will use these building blocks later to create some common client-server scenarios in WCF.</span></span> <span data-ttu-id="c67f0-115">下表总结了 .NET 远程处理与 WCF 之间的主要相似性和差异。</span><span class="sxs-lookup"><span data-stu-id="c67f0-115">The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="c67f0-116">.NET 远程处理</span><span class="sxs-lookup"><span data-stu-id="c67f0-116">.NET Remoting</span></span>|<span data-ttu-id="c67f0-117">WCF</span><span class="sxs-lookup"><span data-stu-id="c67f0-117">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="c67f0-118">服务器类型</span><span class="sxs-lookup"><span data-stu-id="c67f0-118">Server type</span></span>|<span data-ttu-id="c67f0-119">子类 MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="c67f0-119">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="c67f0-120">标记为具有 [ServiceContract] 属性</span><span class="sxs-lookup"><span data-stu-id="c67f0-120">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="c67f0-121">服务操作</span><span class="sxs-lookup"><span data-stu-id="c67f0-121">Service operations</span></span>|<span data-ttu-id="c67f0-122">服务器类型上的公共方法</span><span class="sxs-lookup"><span data-stu-id="c67f0-122">Public methods on server type</span></span>|<span data-ttu-id="c67f0-123">标记为具有 [OperationContract] 属性</span><span class="sxs-lookup"><span data-stu-id="c67f0-123">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="c67f0-124">序列化</span><span class="sxs-lookup"><span data-stu-id="c67f0-124">Serialization</span></span>|<span data-ttu-id="c67f0-125">ISerializable 或 [Serializable]</span><span class="sxs-lookup"><span data-stu-id="c67f0-125">ISerializable or [Serializable]</span></span>|<span data-ttu-id="c67f0-126">DataContractSerializer 或 XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="c67f0-126">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="c67f0-127">传递的对象</span><span class="sxs-lookup"><span data-stu-id="c67f0-127">Objects passed</span></span>|<span data-ttu-id="c67f0-128">按值或按引用</span><span class="sxs-lookup"><span data-stu-id="c67f0-128">By-value or by-reference</span></span>|<span data-ttu-id="c67f0-129">仅按值</span><span class="sxs-lookup"><span data-stu-id="c67f0-129">By-value only</span></span>|  
|<span data-ttu-id="c67f0-130">错误/异常</span><span class="sxs-lookup"><span data-stu-id="c67f0-130">Errors/exceptions</span></span>|<span data-ttu-id="c67f0-131">任何可序列化的异常</span><span class="sxs-lookup"><span data-stu-id="c67f0-131">Any serializable exception</span></span>|<span data-ttu-id="c67f0-132">FaultContract\<TDetail ></span><span class="sxs-lookup"><span data-stu-id="c67f0-132">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="c67f0-133">客户端代理对象</span><span class="sxs-lookup"><span data-stu-id="c67f0-133">Client proxy objects</span></span>|<span data-ttu-id="c67f0-134">从 MarshalByRefObjects 自动创建强类型透明代理</span><span class="sxs-lookup"><span data-stu-id="c67f0-134">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="c67f0-135">强类型代理按需使用 ChannelFactory\<TChannel 生成 ></span><span class="sxs-lookup"><span data-stu-id="c67f0-135">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="c67f0-136">所需平台</span><span class="sxs-lookup"><span data-stu-id="c67f0-136">Platform required</span></span>|<span data-ttu-id="c67f0-137">客户端和服务器必须使用 Microsoft 操作系统和 .NET</span><span class="sxs-lookup"><span data-stu-id="c67f0-137">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="c67f0-138">跨平台</span><span class="sxs-lookup"><span data-stu-id="c67f0-138">Cross-platform</span></span>|  
|<span data-ttu-id="c67f0-139">消息格式</span><span class="sxs-lookup"><span data-stu-id="c67f0-139">Message format</span></span>|<span data-ttu-id="c67f0-140">专用</span><span class="sxs-lookup"><span data-stu-id="c67f0-140">Private</span></span>|<span data-ttu-id="c67f0-141">行业标准（SOAP、WS-\* 等。）</span><span class="sxs-lookup"><span data-stu-id="c67f0-141">Industry standards (SOAP, WS-\*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="c67f0-142">服务器实现比较</span><span class="sxs-lookup"><span data-stu-id="c67f0-142">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="c67f0-143">在 .NET 远程处理中创建服务器</span><span class="sxs-lookup"><span data-stu-id="c67f0-143">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="c67f0-144">.NET 远程处理服务器类型必须从 MarshalByRefObject 中派生，并定义客户端可以调用的方法，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c67f0-144">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="c67f0-145">此服务器类型的公共方法是客户端可使用的公开协定。</span><span class="sxs-lookup"><span data-stu-id="c67f0-145">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="c67f0-146">一种类型会处理服务器公共接口和其实现，而无需分离。</span><span class="sxs-lookup"><span data-stu-id="c67f0-146">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="c67f0-147">一旦定义了服务器类型，其便可用于客户端，如下面示例所示：</span><span class="sxs-lookup"><span data-stu-id="c67f0-147">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),   
    "RemotingServer",   
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="c67f0-148">使远程处理类型作为服务器可用有多种方法，其中一种方法为使用配置文件。</span><span class="sxs-lookup"><span data-stu-id="c67f0-148">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="c67f0-149">这只是一个示例。</span><span class="sxs-lookup"><span data-stu-id="c67f0-149">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="c67f0-150">在 WCF 中创建服务器</span><span class="sxs-lookup"><span data-stu-id="c67f0-150">Creating a Server in WCF</span></span>  
 <span data-ttu-id="c67f0-151">WCF 中的等效步骤涉及创建两种类型 -- 公共“服务协定”类和具体实现。</span><span class="sxs-lookup"><span data-stu-id="c67f0-151">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="c67f0-152">第一种类型为接口类，标记为 [ServiceContract]。</span><span class="sxs-lookup"><span data-stu-id="c67f0-152">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="c67f0-153">客户端可用的方法都标有 [OperationContract]：</span><span class="sxs-lookup"><span data-stu-id="c67f0-153">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="c67f0-154">服务器的实现则定义在单独的具体的类中，如下面示例所示：</span><span class="sxs-lookup"><span data-stu-id="c67f0-154">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="c67f0-155">完成定义这些类型后，WCF 服务器便可提供给客户端，如下面示例所示：</span><span class="sxs-lookup"><span data-stu-id="c67f0-155">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine($"The WCF server is ready at {baseAddress}.");
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="c67f0-156">这两个示例中的 TCP 用于使它们尽可能保持类似。</span><span class="sxs-lookup"><span data-stu-id="c67f0-156">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="c67f0-157">请参阅本主题稍后的使用 HTTP 的示例方案演练。</span><span class="sxs-lookup"><span data-stu-id="c67f0-157">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="c67f0-158">有多种方法来配置和承载 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="c67f0-158">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="c67f0-159">这仅仅是举一个例子，例如称为“自承载”的方法。</span><span class="sxs-lookup"><span data-stu-id="c67f0-159">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="c67f0-160">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="c67f0-160">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="c67f0-161">如何：定义服务协定</span><span class="sxs-lookup"><span data-stu-id="c67f0-161">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
- [<span data-ttu-id="c67f0-162">使用配置文件配置服务</span><span class="sxs-lookup"><span data-stu-id="c67f0-162">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
- [<span data-ttu-id="c67f0-163">托管服务</span><span class="sxs-lookup"><span data-stu-id="c67f0-163">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="c67f0-164">客户端实现比较</span><span class="sxs-lookup"><span data-stu-id="c67f0-164">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="c67f0-165">在 .NET 远程处理中创建客户端</span><span class="sxs-lookup"><span data-stu-id="c67f0-165">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="c67f0-166">一旦 .NET 远程处理服务器对象已经可用，其便可用于客户端，如下面示例所示：</span><span class="sxs-lookup"><span data-stu-id="c67f0-166">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine($"Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="c67f0-167">从 Activator.GetObject() 返回的 RemotingServer 实例称为“透明代理”。</span><span class="sxs-lookup"><span data-stu-id="c67f0-167">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="c67f0-168">它会实现客户端中的 RemotingServer 类型的公共 API，但所有方法都会调用运行在不同进程或计算机中的服务器对象。</span><span class="sxs-lookup"><span data-stu-id="c67f0-168">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="c67f0-169">在 WCF 中创建客户端</span><span class="sxs-lookup"><span data-stu-id="c67f0-169">Creating a Client in WCF</span></span>  
 <span data-ttu-id="c67f0-170">WCF 中的等效步骤涉及使用通道工厂显式创建代理。</span><span class="sxs-lookup"><span data-stu-id="c67f0-170">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="c67f0-171">与远程处理相同，代理对象可用于调用服务器中的操作，如下面示例所示：</span><span class="sxs-lookup"><span data-stu-id="c67f0-171">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
```  
  
 <span data-ttu-id="c67f0-172">此示例演示通道级编程，因为它非常类似于远程处理示例。</span><span class="sxs-lookup"><span data-stu-id="c67f0-172">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="c67f0-173">此外，还提供了 Visual Studio 中的**添加服务引用**方法，该方法生成代码以简化客户端编程。</span><span class="sxs-lookup"><span data-stu-id="c67f0-173">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="c67f0-174">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="c67f0-174">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="c67f0-175">客户端通道级编程</span><span class="sxs-lookup"><span data-stu-id="c67f0-175">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
- [<span data-ttu-id="c67f0-176">如何：添加、更新或移除服务引用</span><span class="sxs-lookup"><span data-stu-id="c67f0-176">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="c67f0-177">序列化用法</span><span class="sxs-lookup"><span data-stu-id="c67f0-177">Serialization Usage</span></span>  
 <span data-ttu-id="c67f0-178">.NET 远程处理和 WCF 均使用序列化发送客户端和服务器之间的对象，但它们在这些重要的方面有所区别：</span><span class="sxs-lookup"><span data-stu-id="c67f0-178">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1. <span data-ttu-id="c67f0-179">它们使用不同的序列化程序和约定来指示如何序列化。</span><span class="sxs-lookup"><span data-stu-id="c67f0-179">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2. <span data-ttu-id="c67f0-180">.NET 远程处理支持“按引用”序列化，即允许一个层上的方法或属性访问执行另一个层上的代码；此为跨安全边界。</span><span class="sxs-lookup"><span data-stu-id="c67f0-180">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="c67f0-181">这种功能会公开安全漏洞，并且也是为什么远程处理终结点应永远不向不受信任的客户端公开的主要原因之一。</span><span class="sxs-lookup"><span data-stu-id="c67f0-181">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3. <span data-ttu-id="c67f0-182">远程处理使用的序列化会选择退出（显式排除不进行序列化的成员）和 WCF 序列化会选择性加入（显式标记要序列化的成员）。</span><span class="sxs-lookup"><span data-stu-id="c67f0-182">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="c67f0-183">.NET 远程处理中的序列化</span><span class="sxs-lookup"><span data-stu-id="c67f0-183">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="c67f0-184">.NET 远程处理支持两种序列化和反序列化客户端和服务器之间的对象的方法：</span><span class="sxs-lookup"><span data-stu-id="c67f0-184">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
- <span data-ttu-id="c67f0-185">*按值*–对象的值将跨层边界序列化，并在另一层上创建该对象的新实例。</span><span class="sxs-lookup"><span data-stu-id="c67f0-185">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="c67f0-186">对该新实例的方法或属性的任何调用只是在本地执行，并不影响原始对象或层。</span><span class="sxs-lookup"><span data-stu-id="c67f0-186">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
- <span data-ttu-id="c67f0-187">*按引用*–一种特殊的 "对象引用" 跨层边界序列化。</span><span class="sxs-lookup"><span data-stu-id="c67f0-187">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="c67f0-188">当一个层与该对象的方法或属性进行交互时，此层会传输回至原始层上的原始对象。</span><span class="sxs-lookup"><span data-stu-id="c67f0-188">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="c67f0-189">按引用对象可以在任一方向 – 服务器到客户端或客户端到服务器中流动。</span><span class="sxs-lookup"><span data-stu-id="c67f0-189">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="c67f0-190">远程处理中按值类型会标记为 [Serializable] 属性或实现 ISerializable，如下面示例所示：</span><span class="sxs-lookup"><span data-stu-id="c67f0-190">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="c67f0-191">按引用类型派生于 MarshalByRefObject 类，如下面示例所示：</span><span class="sxs-lookup"><span data-stu-id="c67f0-191">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="c67f0-192">了解远程处理中按引用对象的影响尤其重要。</span><span class="sxs-lookup"><span data-stu-id="c67f0-192">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="c67f0-193">如果任一层（客户端或服务器）将按引用对象发送至其他层，那么所有方法调用会在拥有此对象的层中进行执行。</span><span class="sxs-lookup"><span data-stu-id="c67f0-193">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="c67f0-194">例如，调用服务器返回的按引用对象中方法的客户端将在服务器中执行代码。</span><span class="sxs-lookup"><span data-stu-id="c67f0-194">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="c67f0-195">同样，调用客户端提供的按引用对象中方法的服务器将在客户端中执行代码。</span><span class="sxs-lookup"><span data-stu-id="c67f0-195">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="c67f0-196">因此，建议只在完全信任环境中使用 .NET 远程处理。</span><span class="sxs-lookup"><span data-stu-id="c67f0-196">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="c67f0-197">向不受信任的客户端公开公共 .NET 远程处理终结点将使远程处理服务器容易受到攻击。</span><span class="sxs-lookup"><span data-stu-id="c67f0-197">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="c67f0-198">WCF 中的序列化</span><span class="sxs-lookup"><span data-stu-id="c67f0-198">Serialization in WCF</span></span>  
 <span data-ttu-id="c67f0-199">WCF 仅支持按值序列化。</span><span class="sxs-lookup"><span data-stu-id="c67f0-199">WCF supports only by-value serialization.</span></span> <span data-ttu-id="c67f0-200">定义客户端和服务器之间交换的类型的最常见方法，如下面示例所示：</span><span class="sxs-lookup"><span data-stu-id="c67f0-200">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="c67f0-201">[DataContract] 特性标识此类型为可在客户端和服务器之间进行序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="c67f0-201">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="c67f0-202">[DataMember] 特性标识要序列化的单个属性或字段。</span><span class="sxs-lookup"><span data-stu-id="c67f0-202">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="c67f0-203">当 WCF 跨多个层发送某个对象时，它仅序列化值并在另一个层上创建此对象的新实例。</span><span class="sxs-lookup"><span data-stu-id="c67f0-203">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="c67f0-204">与此对象的值进行的任何交互仅发生在本地 – 它们不能如 .NET 远程处理中的按引用对象一样与其他层进行通信。</span><span class="sxs-lookup"><span data-stu-id="c67f0-204">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="c67f0-205">有关详细信息，请参阅[序列化和反序列](./feature-details/serialization-and-deserialization.md)化。</span><span class="sxs-lookup"><span data-stu-id="c67f0-205">For more information, see [Serialization and Deserialization](./feature-details/serialization-and-deserialization.md).</span></span>  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="c67f0-206">异常处理功能</span><span class="sxs-lookup"><span data-stu-id="c67f0-206">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="c67f0-207">.NET 远程处理中的异常</span><span class="sxs-lookup"><span data-stu-id="c67f0-207">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="c67f0-208">由远程处理服务器引发的异常会进行序列化、发送到客户端并如同其他异常一样引发在本地的客户端中。</span><span class="sxs-lookup"><span data-stu-id="c67f0-208">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="c67f0-209">可通过子类分类异常类型，并将其标记为 [Serializable] 来创建自定义异常。</span><span class="sxs-lookup"><span data-stu-id="c67f0-209">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="c67f0-210">多数 Framework 异常已以这种方法进行了标记，从而使多数异常由服务器引发、进行序列化并在客户端重新引发。</span><span class="sxs-lookup"><span data-stu-id="c67f0-210">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="c67f0-211">尽管这种设计在开发过程中的确方便，但服务器端信息却可以意外地泄露至客户端中。</span><span class="sxs-lookup"><span data-stu-id="c67f0-211">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="c67f0-212">这是应仅在完全信任环境中使用远程处理的许多原因之一。</span><span class="sxs-lookup"><span data-stu-id="c67f0-212">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="c67f0-213">WCF 中的异常和错误</span><span class="sxs-lookup"><span data-stu-id="c67f0-213">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="c67f0-214">WCF 不允许任意异常类型从服务器返回到客户端，因为可能导致意外的信息泄露。</span><span class="sxs-lookup"><span data-stu-id="c67f0-214">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="c67f0-215">如果服务操作引发了意外的异常，则会导致在客户端引发一般用途的 FaultException。</span><span class="sxs-lookup"><span data-stu-id="c67f0-215">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="c67f0-216">此异常不会带有关于问题产生的原因或地点的任何信息，并且对于一些应用程序来讲，这些信息也就足够了。</span><span class="sxs-lookup"><span data-stu-id="c67f0-216">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="c67f0-217">通过定义错误协定，需要将更丰富的错误信息传递给客户端的应用程序会进行此操作。</span><span class="sxs-lookup"><span data-stu-id="c67f0-217">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="c67f0-218">若要执行此操作，请首先创建 [DataContract] 类型，以执行故障信息。</span><span class="sxs-lookup"><span data-stu-id="c67f0-218">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 <span data-ttu-id="c67f0-219">指定要用于每个服务操作的错误协定。</span><span class="sxs-lookup"><span data-stu-id="c67f0-219">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="c67f0-220">服务器会通过引发 FaultException 从而报告错误条件。</span><span class="sxs-lookup"><span data-stu-id="c67f0-220">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 <span data-ttu-id="c67f0-221">只要客户端向服务器发出请求，都可以作为正常异常进行捕获。</span><span class="sxs-lookup"><span data-stu-id="c67f0-221">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine($"Fault received: {fault.Detail.ErrorMessage}");
}  
```  
  
 <span data-ttu-id="c67f0-222">有关故障协定的详细信息，请参阅 <xref:System.ServiceModel.FaultException>。</span><span class="sxs-lookup"><span data-stu-id="c67f0-222">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="c67f0-223">安全注意事项</span><span class="sxs-lookup"><span data-stu-id="c67f0-223">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="c67f0-224">.NET 远程处理的安全性</span><span class="sxs-lookup"><span data-stu-id="c67f0-224">Security in .NET Remoting</span></span>  
 <span data-ttu-id="c67f0-225">某些 .NET 远程处理信道支持安全功能，比如通道层（IPC 和 TCP）中的身份验证和加密。</span><span class="sxs-lookup"><span data-stu-id="c67f0-225">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="c67f0-226">HTTP 通道依赖于身份验证和加密的 Internet Information Services (IIS)。</span><span class="sxs-lookup"><span data-stu-id="c67f0-226">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="c67f0-227">即使有这种支持，你仍应该将 .NET 远程处理认定为不安全的通信协议并只在完全信任的环境中使用。</span><span class="sxs-lookup"><span data-stu-id="c67f0-227">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="c67f0-228">永远不要将公共远程处理终结点公开到 Internet 或不受信任的客户端中。</span><span class="sxs-lookup"><span data-stu-id="c67f0-228">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="c67f0-229">WCF 中的安全性</span><span class="sxs-lookup"><span data-stu-id="c67f0-229">Security in WCF</span></span>  
 <span data-ttu-id="c67f0-230">WCF 中对于安全性的设计是为了解决出现在 .NET 远程处理中各种的漏洞。</span><span class="sxs-lookup"><span data-stu-id="c67f0-230">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="c67f0-231">WCF 提供了传输和消息级别的安全性，并提供了多个用于身份验证、授权、加密等的选项。</span><span class="sxs-lookup"><span data-stu-id="c67f0-231">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="c67f0-232">有关详细信息，请参阅下列主题：</span><span class="sxs-lookup"><span data-stu-id="c67f0-232">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="c67f0-233">安全性</span><span class="sxs-lookup"><span data-stu-id="c67f0-233">Security</span></span>](./feature-details/security.md)  
  
- [<span data-ttu-id="c67f0-234">WCF 安全指南</span><span class="sxs-lookup"><span data-stu-id="c67f0-234">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="c67f0-235">迁移到 WCF</span><span class="sxs-lookup"><span data-stu-id="c67f0-235">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="c67f0-236">为什么从远程处理迁移到 WCF？</span><span class="sxs-lookup"><span data-stu-id="c67f0-236">Why Migrate from Remoting to WCF?</span></span>  
  
- <span data-ttu-id="c67f0-237">**.NET 远程处理是一种旧产品。**</span><span class="sxs-lookup"><span data-stu-id="c67f0-237">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="c67f0-238">如[.Net 远程处理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29)中所述，它被视为旧产品，不建议用于新的开发。</span><span class="sxs-lookup"><span data-stu-id="c67f0-238">As described in [.NET Remoting](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507%28v=vs.100%29), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="c67f0-239">对于新的和现有的应用程序建议使用 WCF 或 ASP.NET Web API。</span><span class="sxs-lookup"><span data-stu-id="c67f0-239">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
- <span data-ttu-id="c67f0-240">**WCF 使用跨平台标准。**</span><span class="sxs-lookup"><span data-stu-id="c67f0-240">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="c67f0-241">WCF 设计的跨平台互操作性支持许多行业标准（SOAP、Ws-security、Ws-trust 等。）。</span><span class="sxs-lookup"><span data-stu-id="c67f0-241">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="c67f0-242">除了运行 Windows 操作系统的客户端之外，WCF 服务还可以与运行其他操作系统的客户端进行互操作。</span><span class="sxs-lookup"><span data-stu-id="c67f0-242">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="c67f0-243">远程处理主要针对使用 Windows 操作系统上的 .NET Framework 运行服务器和客户端应用程序的环境。</span><span class="sxs-lookup"><span data-stu-id="c67f0-243">Remoting was designed primarily for environments where both the server and client applications run using .NET Framework on a Windows operating system.</span></span>
  
- <span data-ttu-id="c67f0-244">**WCF 具有内置安全性。**</span><span class="sxs-lookup"><span data-stu-id="c67f0-244">**WCF has built-in security.**</span></span> <span data-ttu-id="c67f0-245">WCF 的设计考虑到了安全性，并提供了许多用于身份验证、传输级别安全性、消息级别安全性等的选项。远程处理旨在使应用程序更易于互操作，但并不是在不受信任的环境中保证安全。</span><span class="sxs-lookup"><span data-stu-id="c67f0-245">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="c67f0-246">WCF 设计为可以在受信任和不受信任的两种环境中工作。</span><span class="sxs-lookup"><span data-stu-id="c67f0-246">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="c67f0-247">迁移建议</span><span class="sxs-lookup"><span data-stu-id="c67f0-247">Migration Recommendations</span></span>  
 <span data-ttu-id="c67f0-248">若要从 .NET 远程处理迁移到 WCF，建议步骤如下所示：</span><span class="sxs-lookup"><span data-stu-id="c67f0-248">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
- <span data-ttu-id="c67f0-249">**创建服务协定。**</span><span class="sxs-lookup"><span data-stu-id="c67f0-249">**Create the service contract.**</span></span> <span data-ttu-id="c67f0-250">定义服务接口类型，并将其标记为 [ServiceContract] 属性。标记所有允许客户端利用 [OperationContract] 调用的方法。</span><span class="sxs-lookup"><span data-stu-id="c67f0-250">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
- <span data-ttu-id="c67f0-251">**创建数据协定。**</span><span class="sxs-lookup"><span data-stu-id="c67f0-251">**Create the data contract.**</span></span> <span data-ttu-id="c67f0-252">定义将在服务器和客户端之间进行交换的数据类型，并将其标记为 [DataContract] 属性。</span><span class="sxs-lookup"><span data-stu-id="c67f0-252">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="c67f0-253">标记允许客户端利用 [DataMember] 使用的所有字段和属性。</span><span class="sxs-lookup"><span data-stu-id="c67f0-253">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
- <span data-ttu-id="c67f0-254">**创建错误协定（可选）。**</span><span class="sxs-lookup"><span data-stu-id="c67f0-254">**Create the fault contract (optional).**</span></span> <span data-ttu-id="c67f0-255">遇到错误时，请创建将在服务器和客户端之间进行交换的类型。</span><span class="sxs-lookup"><span data-stu-id="c67f0-255">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="c67f0-256">将这些类型标记为 [DataContract] 和 [DataMember] 以使其可序列化。</span><span class="sxs-lookup"><span data-stu-id="c67f0-256">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="c67f0-257">对于标记为 [OperationContract] 的所有服务操作，还可将其标记为 [FaultContract]，以指示它们可能会返回哪些错误。</span><span class="sxs-lookup"><span data-stu-id="c67f0-257">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
- <span data-ttu-id="c67f0-258">**配置并托管该服务。**</span><span class="sxs-lookup"><span data-stu-id="c67f0-258">**Configure and host the service.**</span></span> <span data-ttu-id="c67f0-259">完成创建服务协定后，下一步则是配置一个绑定以公开终结点中的服务。</span><span class="sxs-lookup"><span data-stu-id="c67f0-259">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="c67f0-260">有关详细信息，请参阅[终结点：地址、绑定和协定](./feature-details/endpoints-addresses-bindings-and-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="c67f0-260">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="c67f0-261">将远程处理应用程序迁移到 WCF 后，删除 .NET 远程处理中的依赖仍然很重要。</span><span class="sxs-lookup"><span data-stu-id="c67f0-261">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="c67f0-262">这可确保删除应用程序中的任何远程处理漏洞。</span><span class="sxs-lookup"><span data-stu-id="c67f0-262">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="c67f0-263">这些步骤包括：</span><span class="sxs-lookup"><span data-stu-id="c67f0-263">These steps include the following:</span></span>  
  
- <span data-ttu-id="c67f0-264">**停止使用 MarshalByRefObject。**</span><span class="sxs-lookup"><span data-stu-id="c67f0-264">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="c67f0-265">MarshalByRefObject 类型仅因远程处理而存在并且 WCF 并不使用此类型。</span><span class="sxs-lookup"><span data-stu-id="c67f0-265">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="c67f0-266">应删除或更改子类 MarshalByRefObject 的任何应用程序类型。</span><span class="sxs-lookup"><span data-stu-id="c67f0-266">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
- <span data-ttu-id="c67f0-267">**停止使用 [Serializable] 和 ISerializable。**</span><span class="sxs-lookup"><span data-stu-id="c67f0-267">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="c67f0-268">[Serializable] 属性和 ISerializable 接口最初用于在受信任的环境中序列化类型，并为远程处理所用。</span><span class="sxs-lookup"><span data-stu-id="c67f0-268">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="c67f0-269">WCF 序列化依赖于标记为 [DataContract] 和 [DataMember] 的类型。</span><span class="sxs-lookup"><span data-stu-id="c67f0-269">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="c67f0-270">若要使用 [DataContract]，而不是使用 ISerializable 或 [Serializable]，则应修改应用程序使用的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c67f0-270">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="c67f0-271">迁移方案</span><span class="sxs-lookup"><span data-stu-id="c67f0-271">Migration Scenarios</span></span>  
 <span data-ttu-id="c67f0-272">现在让我们了解如何完成以下 WCF 中的常见远程处理方案：</span><span class="sxs-lookup"><span data-stu-id="c67f0-272">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1. <span data-ttu-id="c67f0-273">服务器将对象按值返回到客户端</span><span class="sxs-lookup"><span data-stu-id="c67f0-273">Server returns an object by-value to the client</span></span>  
  
2. <span data-ttu-id="c67f0-274">服务器将对象按引用返回到客户端</span><span class="sxs-lookup"><span data-stu-id="c67f0-274">Server returns an object by-reference to the client</span></span>  
  
3. <span data-ttu-id="c67f0-275">客户端按值向服务器发送对象</span><span class="sxs-lookup"><span data-stu-id="c67f0-275">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c67f0-276">WCF 中不允许从客户端将对象按引用发送到服务器。</span><span class="sxs-lookup"><span data-stu-id="c67f0-276">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="c67f0-277">阅读这些方案后，假定 .NET 远程处理的基线接口将如下面示例所示。</span><span class="sxs-lookup"><span data-stu-id="c67f0-277">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="c67f0-278">由于在这里仅想说明如何使用 WCF 实现等效功能，因此 .NET 远程处理实现在此并不重要。</span><span class="sxs-lookup"><span data-stu-id="c67f0-278">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="c67f0-279">方案 1：服务按值返回对象</span><span class="sxs-lookup"><span data-stu-id="c67f0-279">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="c67f0-280">此方案演示服务器按值将对象返回至客户端。</span><span class="sxs-lookup"><span data-stu-id="c67f0-280">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="c67f0-281">WCF 始终按值从服务器中返回对象，因此以下步骤仅描述了如何创建普通 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="c67f0-281">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1. <span data-ttu-id="c67f0-282">首先定义 WCF 服务的公共接口并标记 [ServiceContract] 属性。</span><span class="sxs-lookup"><span data-stu-id="c67f0-282">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="c67f0-283">使用 [OperationContract] 标识客户端将调用的服务器端方法。</span><span class="sxs-lookup"><span data-stu-id="c67f0-283">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2. <span data-ttu-id="c67f0-284">下一步则是创建此服务的数据约定。</span><span class="sxs-lookup"><span data-stu-id="c67f0-284">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="c67f0-285">通过创建具有 [DataContract] 属性标记的类（非接口）来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="c67f0-285">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="c67f0-286">希望对客户端和服务器可见的单独属性或字段标记为 [DataMember]。</span><span class="sxs-lookup"><span data-stu-id="c67f0-286">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="c67f0-287">如果希望使用允许派生的类型，则必须使用 [KnownType] 属性来进行标记。</span><span class="sxs-lookup"><span data-stu-id="c67f0-287">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="c67f0-288">WCF 中允许为此服务进行序列化或反序列化的唯一类型是服务接口类型和“已知类型”。</span><span class="sxs-lookup"><span data-stu-id="c67f0-288">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="c67f0-289">拒绝尝试交换不在此列表中的任何其他类型。</span><span class="sxs-lookup"><span data-stu-id="c67f0-289">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer   
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3. <span data-ttu-id="c67f0-290">接下来，将提供服务接口的实现。</span><span class="sxs-lookup"><span data-stu-id="c67f0-290">Next, we provide the implementation for the service interface.</span></span>  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4. <span data-ttu-id="c67f0-291">若要运行 WCF 服务，则需要声明终结点将公开使用特定 WCF 绑定的特定 URL 中的该服务接口。</span><span class="sxs-lookup"><span data-stu-id="c67f0-291">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="c67f0-292">这通常通过向服务器项目的 web.config 文件中添加以下各节而实现的。</span><span class="sxs-lookup"><span data-stu-id="c67f0-292">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5. <span data-ttu-id="c67f0-293">然后，可用下面的代码中启动 WCF 服务：</span><span class="sxs-lookup"><span data-stu-id="c67f0-293">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="c67f0-294">当启动此 ServiceHost 时，它会使用 web.config 文件以建立适当的协定、绑定和终结点。</span><span class="sxs-lookup"><span data-stu-id="c67f0-294">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="c67f0-295">有关配置文件的详细信息，请参阅[使用配置文件配置服务](./configuring-services-using-configuration-files.md)。</span><span class="sxs-lookup"><span data-stu-id="c67f0-295">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="c67f0-296">这种启动服务器的样式称为自我托管。</span><span class="sxs-lookup"><span data-stu-id="c67f0-296">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="c67f0-297">若要了解有关承载 WCF 服务的其他选项的详细信息，请参阅[托管服务](./hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c67f0-297">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6. <span data-ttu-id="c67f0-298">客户端项目的 app.config 必须声明匹配服务终结点的绑定信息。</span><span class="sxs-lookup"><span data-stu-id="c67f0-298">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="c67f0-299">在 Visual Studio 中执行此操作的最简单方法是使用**添加服务引用**，这将自动更新 app.config 文件。</span><span class="sxs-lookup"><span data-stu-id="c67f0-299">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="c67f0-300">或者，可以手动添加这些相同的更改。</span><span class="sxs-lookup"><span data-stu-id="c67f0-300">Alternatively, these same changes can be added manually.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="c67f0-301">有关使用**添加服务引用**的详细信息，请参阅[如何：添加、更新或删除服务引用](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)。</span><span class="sxs-lookup"><span data-stu-id="c67f0-301">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7. <span data-ttu-id="c67f0-302">现在可以从客户端中调用 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="c67f0-302">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="c67f0-303">可通过创建该服务的通道工厂、要求提供通道以及直接调用想要用在该通道中的方法实现此操作。</span><span class="sxs-lookup"><span data-stu-id="c67f0-303">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="c67f0-304">可进行此操作的原因是通道可实现服务接口，并为我们处理基础的请求/答复逻辑。</span><span class="sxs-lookup"><span data-stu-id="c67f0-304">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="c67f0-305">此方法调用的返回值是服务器响应的反序列化副本。</span><span class="sxs-lookup"><span data-stu-id="c67f0-305">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine($"  Customer {customer.FirstName} {customer.LastName} received.");
   ```  
  
 <span data-ttu-id="c67f0-306">由 WCF 从服务器返回到客户端的对象始终为按值返回。</span><span class="sxs-lookup"><span data-stu-id="c67f0-306">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="c67f0-307">对象是由服务器发送的数据反序列化副本。</span><span class="sxs-lookup"><span data-stu-id="c67f0-307">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="c67f0-308">客户端可以对这些本地副本调用方法，而无需担心通过回调调用服务器。</span><span class="sxs-lookup"><span data-stu-id="c67f0-308">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="c67f0-309">方案 2：服务器按按引用返回对象</span><span class="sxs-lookup"><span data-stu-id="c67f0-309">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="c67f0-310">此方案演示服务器按引用向客户端提供对象。</span><span class="sxs-lookup"><span data-stu-id="c67f0-310">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="c67f0-311">在 .NET 远程处理中，这会自动处理任何派生自 MarshalByRefObject 的类型，即序列化的引用。</span><span class="sxs-lookup"><span data-stu-id="c67f0-311">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="c67f0-312">此方案的一个示例是允许多个客户端拥有独立会话的服务端对象。</span><span class="sxs-lookup"><span data-stu-id="c67f0-312">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="c67f0-313">正如前面所述，WCF 服务返回的对象始终按值返回，因此并没有直接对等的按引用对象，但是有可能实现类似于使用 <xref:System.ServiceModel.EndpointAddress10> 对象的按引用语义。</span><span class="sxs-lookup"><span data-stu-id="c67f0-313">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="c67f0-314">这是客户端用于获取服务器上会话按引用对象的可序列化的值对象。</span><span class="sxs-lookup"><span data-stu-id="c67f0-314">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="c67f0-315">这将使多个客户端拥有独立会话的服务器端对象的方案得以实现。</span><span class="sxs-lookup"><span data-stu-id="c67f0-315">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1. <span data-ttu-id="c67f0-316">首先，需要定义与会话对象本身对应的 WCF 服务协定。</span><span class="sxs-lookup"><span data-stu-id="c67f0-316">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    > <span data-ttu-id="c67f0-317">请注意该会话对象用 [ServiceContract] 进行了标记，使其成为普通的 WCF 服务接口。</span><span class="sxs-lookup"><span data-stu-id="c67f0-317">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="c67f0-318">设置 SessionMode 属性指示其将为会话服务。</span><span class="sxs-lookup"><span data-stu-id="c67f0-318">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="c67f0-319">在 WCF 中，会话是使两个终结点之间发送的多个消息关联的一种方法。</span><span class="sxs-lookup"><span data-stu-id="c67f0-319">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="c67f0-320">这意味着一旦客户端获取与此服务的连接，将会建立客户端和服务器之间的会话。</span><span class="sxs-lookup"><span data-stu-id="c67f0-320">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="c67f0-321">对于此单个会话中的所有交互，客户端都将使用服务器端对象的单个唯一实例。</span><span class="sxs-lookup"><span data-stu-id="c67f0-321">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2. <span data-ttu-id="c67f0-322">接下来，需要提供此服务接口的实现。</span><span class="sxs-lookup"><span data-stu-id="c67f0-322">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="c67f0-323">通过使用 [ServiceBehavior] 进行表示，并设置 InstanceContextMode，将告知 WCF 希望使用每个会话的此类型的唯一实例。</span><span class="sxs-lookup"><span data-stu-id="c67f0-323">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
   ```csharp
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
       public class MySessionBoundObject : ISessionBoundObject  
       {  
           private string _value;  
  
           public string GetCurrentValue()  
           {  
               return _value;  
           }  
  
           public void SetCurrentValue(string val)  
           {  
               _value = val;  
           }  
  
       }  
   ```  
  
3. <span data-ttu-id="c67f0-324">现在，需要一种方法以获取此会话对象的实例。</span><span class="sxs-lookup"><span data-stu-id="c67f0-324">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="c67f0-325">通过创建返回 EndpointAddress10 对象的另一个 WCF 服务接口来执行此操作。</span><span class="sxs-lookup"><span data-stu-id="c67f0-325">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="c67f0-326">这是一种客户端可用来创建会话对象的终结点的可序列化形式。</span><span class="sxs-lookup"><span data-stu-id="c67f0-326">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="c67f0-327">并且，我们实现此 WCF 服务：</span><span class="sxs-lookup"><span data-stu-id="c67f0-327">And we implement this WCF service:</span></span>  
  
   ```csharp
   public class SessionBoundFactory : ISessionBoundFactory  
       {  
           public static ChannelFactory<ISessionBoundObject> _factory =   
               new ChannelFactory<ISessionBoundObject>("sessionbound");  
 
           public SessionBoundFactory()  
           {  
           }  
  
           public EndpointAddress10 GetInstanceAddress()  
           {  
               IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
               return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
           }  
       }  
   ```  
  
     <span data-ttu-id="c67f0-328">此实现维护单一实例通道工厂以创建会话对象。</span><span class="sxs-lookup"><span data-stu-id="c67f0-328">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="c67f0-329">当调用 GetInstanceAddress() 时，它会创建一个通道，并创建一个有效地指向与此通道关联的远程地址的 EndpointAddress10 对象。</span><span class="sxs-lookup"><span data-stu-id="c67f0-329">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="c67f0-330">EndpointAddress10 只是一种可按值返回至客户端的数据类型。</span><span class="sxs-lookup"><span data-stu-id="c67f0-330">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4. <span data-ttu-id="c67f0-331">需要通过执行以下两个事件，修改服务器的配置文件，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="c67f0-331">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1. <span data-ttu-id="c67f0-332">声明描述会话对象的终结点的 \<客户端 > 部分。</span><span class="sxs-lookup"><span data-stu-id="c67f0-332">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="c67f0-333">此声明是必需的，原因是在此情况下此服务器还可作为客户端。</span><span class="sxs-lookup"><span data-stu-id="c67f0-333">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2. <span data-ttu-id="c67f0-334">声明工厂和会话对象的终结点。</span><span class="sxs-lookup"><span data-stu-id="c67f0-334">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="c67f0-335">此声明是必需，原因是这可允许客户端与服务终结点通信以获取 EndpointAddress10 并创建会话通道。</span><span class="sxs-lookup"><span data-stu-id="c67f0-335">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
         <client>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
        </client>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
          <service name="Server.MySessionBoundObject">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundObject" />  
          </service>  
          <service name="Server.SessionBoundFactory">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundFactory" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="c67f0-336">然后便可启动这些服务：</span><span class="sxs-lookup"><span data-stu-id="c67f0-336">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5. <span data-ttu-id="c67f0-337">可通过声明其项目 app.config 文件中这些相同的终结点配置客户端。</span><span class="sxs-lookup"><span data-stu-id="c67f0-337">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
          <endpoint name="factory"  
                    address="net.tcp://localhost:8081/SessionBoundFactory"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundFactory"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
6. <span data-ttu-id="c67f0-338">为了创建和使用此会话对象，客户端必须执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="c67f0-338">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1. <span data-ttu-id="c67f0-339">创建 ISessionBoundFactory 服务的通道。</span><span class="sxs-lookup"><span data-stu-id="c67f0-339">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2. <span data-ttu-id="c67f0-340">使用该通道调用该服务，以获取 EndpointAddress10。</span><span class="sxs-lookup"><span data-stu-id="c67f0-340">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3. <span data-ttu-id="c67f0-341">使用 EndpointAddress10 创建一个通道，以获取会话对象。</span><span class="sxs-lookup"><span data-stu-id="c67f0-341">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4. <span data-ttu-id="c67f0-342">与会话对象进行交互，以演示多次调用间保持的同一个实例。</span><span class="sxs-lookup"><span data-stu-id="c67f0-342">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =   
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 <span data-ttu-id="c67f0-343">WCF 将始终返回按值的对象，但是通过使用 EndpointAddress10 有可能支持按引用语义的等效项。</span><span class="sxs-lookup"><span data-stu-id="c67f0-343">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="c67f0-344">这将允许客户端请求会话的 WCF 服务实例，此后客户端可以与此实例进行交互，与其他 WCF 服务并无差异。</span><span class="sxs-lookup"><span data-stu-id="c67f0-344">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="c67f0-345">方案 3：客户端向服务器发送按值实例</span><span class="sxs-lookup"><span data-stu-id="c67f0-345">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="c67f0-346">此方案演示客户端按值向服务器发送一个非基元对象实例。</span><span class="sxs-lookup"><span data-stu-id="c67f0-346">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="c67f0-347">由于 WCF 仅发送按值对象，因此此方案演示正常使用 WCF 的情况。</span><span class="sxs-lookup"><span data-stu-id="c67f0-347">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1. <span data-ttu-id="c67f0-348">使用与方案 1 中相同的 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="c67f0-348">Use the same WCF Service from Scenario 1.</span></span>  
  
2. <span data-ttu-id="c67f0-349">使用客户端创建一个新的按值对象（客户）、创建与 ICustomerService 服务进行通信的通道，并向其发送该对象。</span><span class="sxs-lookup"><span data-stu-id="c67f0-349">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {   
   FirstName = "Bob",   
   LastName = "Jones",   
   CustomerId = 43,   
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine($"  Server returned {success}.");
   ```  
  
     <span data-ttu-id="c67f0-350">将序列化客户对象，并将其发送到服务器，在其中将其反序列化为该对象的新副本。</span><span class="sxs-lookup"><span data-stu-id="c67f0-350">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c67f0-351">此代码还说明了发送派生的类型 (PremiumCustomer)。</span><span class="sxs-lookup"><span data-stu-id="c67f0-351">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="c67f0-352">服务接口需要 Customer 对象，但 Customer 类上的 [KnownType] 属性指示也允许使用 PremiumCustomer。</span><span class="sxs-lookup"><span data-stu-id="c67f0-352">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="c67f0-353">WCF 通过此服务接口进行序列化或反序列化任何其他类型的尝试将失败。</span><span class="sxs-lookup"><span data-stu-id="c67f0-353">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="c67f0-354">正常的 WCF 数据交换是按值进行的。</span><span class="sxs-lookup"><span data-stu-id="c67f0-354">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="c67f0-355">这可确保其中某个数据对象上的调用方法仅在本地执行 – 它将不会调用其他层上的代码。</span><span class="sxs-lookup"><span data-stu-id="c67f0-355">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="c67f0-356">尽管可以实现*从*服务器返回的类似于引用对象的内容，但客户端无法将按引用对象传递*到*服务器。</span><span class="sxs-lookup"><span data-stu-id="c67f0-356">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="c67f0-357">在 WCF 中使用双工服务可实现需要在客户端和服务器间来回会话的方案。</span><span class="sxs-lookup"><span data-stu-id="c67f0-357">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="c67f0-358">有关详细信息，请参阅[双工服务](./feature-details/duplex-services.md)。</span><span class="sxs-lookup"><span data-stu-id="c67f0-358">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="c67f0-359">摘要</span><span class="sxs-lookup"><span data-stu-id="c67f0-359">Summary</span></span>  
 <span data-ttu-id="c67f0-360">.NET 远程处理是一种通信框架，仅用于完全信任的环境中。</span><span class="sxs-lookup"><span data-stu-id="c67f0-360">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="c67f0-361">它是一项传统技术，仅支持向后兼容性。</span><span class="sxs-lookup"><span data-stu-id="c67f0-361">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="c67f0-362">它不应用于生成新的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c67f0-362">It should not be used to build new applications.</span></span> <span data-ttu-id="c67f0-363">相反，WCF 融入了安全性，并建议将其用于生成新的和现有的应用程序。</span><span class="sxs-lookup"><span data-stu-id="c67f0-363">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="c67f0-364">Microsoft 建议将现有的远程处理应用程序迁移到使用 WCF 或 ASP.NET Web API。</span><span class="sxs-lookup"><span data-stu-id="c67f0-364">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>
