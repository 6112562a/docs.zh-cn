---
title: 使用 WCF 客户端访问服务
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: ae589e1c418b1cf13fe9f5b34648bdf7a2210eed
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855676"
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="73c3b-102">使用 WCF 客户端访问服务</span><span class="sxs-lookup"><span data-stu-id="73c3b-102">Accessing Services Using a WCF Client</span></span>

<span data-ttu-id="73c3b-103">创建服务后，下一步是创建 WCF 客户端代理。</span><span class="sxs-lookup"><span data-stu-id="73c3b-103">After you create a service, the next step is to create a WCF client proxy.</span></span> <span data-ttu-id="73c3b-104">客户端应用程序使用 WCF 客户端代理与服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="73c3b-104">A client application uses the WCF client proxy to communicate with the service.</span></span> <span data-ttu-id="73c3b-105">客户端应用程序通常会导入服务的元数据，以生成可用于调用服务的 WCF 客户端代码。</span><span class="sxs-lookup"><span data-stu-id="73c3b-105">Client applications usually import a service's metadata to generate WCF client code that can be used to invoke the service.</span></span>

 <span data-ttu-id="73c3b-106">创建 WCF 客户端的基本步骤如下所示：</span><span class="sxs-lookup"><span data-stu-id="73c3b-106">The basic steps for creating a WCF client include the following:</span></span>

1. <span data-ttu-id="73c3b-107">编译服务代码。</span><span class="sxs-lookup"><span data-stu-id="73c3b-107">Compile the service code.</span></span>

2. <span data-ttu-id="73c3b-108">生成 WCF 客户端代理。</span><span class="sxs-lookup"><span data-stu-id="73c3b-108">Generate the WCF client proxy.</span></span>

3. <span data-ttu-id="73c3b-109">实例化 WCF 客户端代理。</span><span class="sxs-lookup"><span data-stu-id="73c3b-109">Instantiate the WCF client proxy.</span></span>

<span data-ttu-id="73c3b-110">通过使用服务模型元数据实用工具（Svcutil.exe），可以手动生成 WCF 客户端代理。有关详细信息，请参阅 ""[元数据实用工具（svcutil.exe）](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="73c3b-110">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="73c3b-111">还可以使用**添加服务引用**功能在 Visual Studio 中生成 WCF 客户端代理。</span><span class="sxs-lookup"><span data-stu-id="73c3b-111">The WCF client proxy can also be generated within Visual Studio using the **Add Service Reference**  feature.</span></span> <span data-ttu-id="73c3b-112">若要使用上述两种方法中的一种生成 WCF 客户端代理，必须运行该服务。</span><span class="sxs-lookup"><span data-stu-id="73c3b-112">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="73c3b-113">如果服务是自承载服务，则必须运行主机。</span><span class="sxs-lookup"><span data-stu-id="73c3b-113">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="73c3b-114">如果服务是在 IIS/WAS 中承载的，则无需执行任何其他操作。</span><span class="sxs-lookup"><span data-stu-id="73c3b-114">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>

## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="73c3b-115">ServiceModel 元数据实用工具</span><span class="sxs-lookup"><span data-stu-id="73c3b-115">ServiceModel Metadata Utility Tool</span></span>
 <span data-ttu-id="73c3b-116">[Svcutil.exe 元数据实用工具（）](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)是一个命令行工具，用于从元数据生成代码。</span><span class="sxs-lookup"><span data-stu-id="73c3b-116">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="73c3b-117">下面是一个基本 Svcutil.exe 命令示例。</span><span class="sxs-lookup"><span data-stu-id="73c3b-117">The following use is an example of a basic Svcutil.exe command.</span></span>

```console
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 <span data-ttu-id="73c3b-118">另外，还可以使用 Svcutil.exe 来处理文件系统中的 Web 服务描述语言 (WSDL) 和 XML 架构定义语言 (XSD) 文件。</span><span class="sxs-lookup"><span data-stu-id="73c3b-118">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>

```console
Svcutil.exe <list of WSDL and XSD files on file system>
```

 <span data-ttu-id="73c3b-119">结果是一个代码文件，其中包含客户端应用程序可用于调用服务的 WCF 客户端代码。</span><span class="sxs-lookup"><span data-stu-id="73c3b-119">The result is a code file that contains WCF client code that the client application can use to invoke the service.</span></span>

 <span data-ttu-id="73c3b-120">您还可以使用该工具生成配置文件。</span><span class="sxs-lookup"><span data-stu-id="73c3b-120">You can also use the tool to generate configuration files.</span></span>

```console
Svcutil.exe <file1 [,file2]>
```

 <span data-ttu-id="73c3b-121">如果仅提供了一个文件名，则该文件名是输出文件的名称。</span><span class="sxs-lookup"><span data-stu-id="73c3b-121">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="73c3b-122">如果提供了两个文件名，则第一个文件是输入配置文件，其内容将与生成的配置合并，然后写出到第二个文件中。</span><span class="sxs-lookup"><span data-stu-id="73c3b-122">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> <span data-ttu-id="73c3b-123">有关配置的详细信息，请参阅[配置服务的绑定](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="73c3b-123">For more information about configuration, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="73c3b-124">不安全的元数据请求以与任何不安全的网络请求相同的方式来带来某些风险：如果你不确定要与之通信的终结点是谁说，你检索的信息可能是来自恶意服务的元数据。</span><span class="sxs-lookup"><span data-stu-id="73c3b-124">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>

## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="73c3b-125">Visual Studio 中的“添加服务引用”功能</span><span class="sxs-lookup"><span data-stu-id="73c3b-125">Add Service Reference in Visual Studio</span></span>

 <span data-ttu-id="73c3b-126">在运行服务的情况下，右键单击将包含 WCF 客户端代理的项目，然后选择 "**添加** > **服务引用**"。</span><span class="sxs-lookup"><span data-stu-id="73c3b-126">With the service running, right click the project that will contain the WCF client proxy and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="73c3b-127">在 "**添加服务引用" 对话框**中，键入要调用的服务的 URL，然后单击 "**开始**" 按钮。</span><span class="sxs-lookup"><span data-stu-id="73c3b-127">In the **Add Service Reference Dialog**, type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="73c3b-128">该对话框将显示在您指定的地址上提供的服务列表。</span><span class="sxs-lookup"><span data-stu-id="73c3b-128">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="73c3b-129">双击服务以查看可用的协定和操作，为生成的代码指定命名空间，然后单击 **"确定"** 按钮。</span><span class="sxs-lookup"><span data-stu-id="73c3b-129">Double click the service to see the contracts and operations available, specify a namespace for the generated code, and click the **OK** button.</span></span>

## <a name="example"></a><span data-ttu-id="73c3b-130">示例</span><span class="sxs-lookup"><span data-stu-id="73c3b-130">Example</span></span>
 <span data-ttu-id="73c3b-131">下面的代码示例演示为服务创建的一个服务协定。</span><span class="sxs-lookup"><span data-stu-id="73c3b-131">The following code example shows a service contract created for a service.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```

```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```

 <span data-ttu-id="73c3b-132">在 Visual Studio 中的元数据实用工具工具和**添加服务引用**生成以下 WCF 客户端类。</span><span class="sxs-lookup"><span data-stu-id="73c3b-132">The ServiceModel Metadata utility tool and **Add Service Reference** in Visual Studio generates the following WCF client class.</span></span> <span data-ttu-id="73c3b-133">该类从 <xref:System.ServiceModel.ClientBase%601> 泛型类继承，并实现 `ICalculator` 接口。</span><span class="sxs-lookup"><span data-stu-id="73c3b-133">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="73c3b-134">该工具还生成 `ICalculator` 接口（此处未演示）。</span><span class="sxs-lookup"><span data-stu-id="73c3b-134">The tool also generates the `ICalculator` interface (not shown here).</span></span>

```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```

```vb
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```

## <a name="using-the-wcf-client"></a><span data-ttu-id="73c3b-135">使用 WCF 客户端</span><span class="sxs-lookup"><span data-stu-id="73c3b-135">Using the WCF Client</span></span>
 <span data-ttu-id="73c3b-136">若要使用 WCF 客户端，请创建 WCF 客户端的实例，然后调用其方法，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="73c3b-136">To use the WCF client, create an instance of the WCF client, and then call its methods, as shown in the following code.</span></span>

```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```

## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="73c3b-137">调试客户端引发的异常</span><span class="sxs-lookup"><span data-stu-id="73c3b-137">Debugging Exceptions Thrown by a Client</span></span>

<span data-ttu-id="73c3b-138">WCF 客户端引发的许多异常由服务上的异常引起。</span><span class="sxs-lookup"><span data-stu-id="73c3b-138">Many exceptions thrown by a WCF client are caused by an exception on the service.</span></span> <span data-ttu-id="73c3b-139">以下是这种情况的一些示例：</span><span class="sxs-lookup"><span data-stu-id="73c3b-139">Some examples of this are:</span></span>

- <span data-ttu-id="73c3b-140"><xref:System.Net.Sockets.SocketException>：远程主机强行关闭了现有连接。</span><span class="sxs-lookup"><span data-stu-id="73c3b-140"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>

- <span data-ttu-id="73c3b-141"><xref:System.ServiceModel.CommunicationException>：基础连接意外关闭。</span><span class="sxs-lookup"><span data-stu-id="73c3b-141"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>

- <span data-ttu-id="73c3b-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>：套接字连接已中止。</span><span class="sxs-lookup"><span data-stu-id="73c3b-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="73c3b-143">这可能是由于处理消息时出错或远程主机超过接收超时或者潜在的网络资源问题导致的。</span><span class="sxs-lookup"><span data-stu-id="73c3b-143">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>

<span data-ttu-id="73c3b-144">当发生这些类型的异常时，解决问题的最佳方式是在服务端启用跟踪并确定服务端发生了何种异常。</span><span class="sxs-lookup"><span data-stu-id="73c3b-144">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> <span data-ttu-id="73c3b-145">有关跟踪的详细信息，请参阅[跟踪](../../../docs/framework/wcf/diagnostics/tracing/index.md)和[使用跟踪对应用程序进行故障排除](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)。</span><span class="sxs-lookup"><span data-stu-id="73c3b-145">For more information about tracing, see [Tracing](../../../docs/framework/wcf/diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73c3b-146">请参阅</span><span class="sxs-lookup"><span data-stu-id="73c3b-146">See also</span></span>

- [<span data-ttu-id="73c3b-147">如何：创建客户端</span><span class="sxs-lookup"><span data-stu-id="73c3b-147">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="73c3b-148">如何：使用双工协定访问服务</span><span class="sxs-lookup"><span data-stu-id="73c3b-148">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="73c3b-149">如何：以异步方式调用服务操作</span><span class="sxs-lookup"><span data-stu-id="73c3b-149">How to: Call Service Operations Asynchronously</span></span>](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [<span data-ttu-id="73c3b-150">如何：使用单向和请求-答复协定访问服务</span><span class="sxs-lookup"><span data-stu-id="73c3b-150">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [<span data-ttu-id="73c3b-151">如何：访问 WSE 3.0 服务</span><span class="sxs-lookup"><span data-stu-id="73c3b-151">How to: Access a WSE 3.0 Service</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [<span data-ttu-id="73c3b-152">了解生成的客户端代码</span><span class="sxs-lookup"><span data-stu-id="73c3b-152">Understanding Generated Client Code</span></span>](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [<span data-ttu-id="73c3b-153">如何：使用 XmlSerializer 改善 WCF 客户端应用程序的启动时间</span><span class="sxs-lookup"><span data-stu-id="73c3b-153">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [<span data-ttu-id="73c3b-154">指定客户端运行时行为</span><span class="sxs-lookup"><span data-stu-id="73c3b-154">Specifying Client Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="73c3b-155">配置客户端行为</span><span class="sxs-lookup"><span data-stu-id="73c3b-155">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)
