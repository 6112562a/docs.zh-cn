---
title: 如何：使用 Windows 凭据保护服务的安全
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
ms.assetid: d171b5ca-96ef-47ff-800c-c138023cf76e
ms.openlocfilehash: 19ac9da94ce6e405632293a7d569698c9d866bef
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856060"
---
# <a name="how-to-secure-a-service-with-windows-credentials"></a><span data-ttu-id="1871f-102">如何：使用 Windows 凭据保护服务的安全</span><span class="sxs-lookup"><span data-stu-id="1871f-102">How to: Secure a Service with Windows Credentials</span></span>

<span data-ttu-id="1871f-103">本主题演示如何在驻留于 Windows 域中并由同一域中的客户端调用的 Windows Communication Foundation （WCF）服务上启用传输安全。</span><span class="sxs-lookup"><span data-stu-id="1871f-103">This topic shows how to enable transport security on a Windows Communication Foundation (WCF) service that resides in a Windows domain and is called by clients in the same domain.</span></span> <span data-ttu-id="1871f-104">有关此方案的详细信息，请参阅[采用 Windows 身份验证的传输安全](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="1871f-104">For more information about this scenario, see [Transport Security with Windows Authentication](../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md).</span></span> <span data-ttu-id="1871f-105">有关示例应用程序，请参阅[WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md)示例。</span><span class="sxs-lookup"><span data-stu-id="1871f-105">For a sample application, see the [WSHttpBinding](../../../docs/framework/wcf/samples/wshttpbinding.md) sample.</span></span>

<span data-ttu-id="1871f-106">本主题假定您已定义一个现有的协定接口和实现及其加载项。</span><span class="sxs-lookup"><span data-stu-id="1871f-106">This topic assumes you have an existing contract interface and implementation already defined, and adds on to that.</span></span> <span data-ttu-id="1871f-107">您还可以修改一个现有的服务和客户端。</span><span class="sxs-lookup"><span data-stu-id="1871f-107">You can also modify an existing service and client.</span></span>

<span data-ttu-id="1871f-108">你完全可以在代码中使用 Windows 凭据来保护服务。</span><span class="sxs-lookup"><span data-stu-id="1871f-108">You can secure a service with Windows credentials completely in code.</span></span> <span data-ttu-id="1871f-109">或者，也可以通过使用配置文件省略某些代码。</span><span class="sxs-lookup"><span data-stu-id="1871f-109">Alternatively, you can omit some of the code by using a configuration file.</span></span> <span data-ttu-id="1871f-110">本主题演示了这两种方法。</span><span class="sxs-lookup"><span data-stu-id="1871f-110">This topic shows both ways.</span></span> <span data-ttu-id="1871f-111">请务必仅使用其中一种方法，而不是同时使用两种方法。</span><span class="sxs-lookup"><span data-stu-id="1871f-111">Be sure you only use one of the ways, not both.</span></span>

<span data-ttu-id="1871f-112">前三个过程演示如何使用代码保护服务。</span><span class="sxs-lookup"><span data-stu-id="1871f-112">The first three procedures show how to secure the service using code.</span></span> <span data-ttu-id="1871f-113">第四个和第五个过程演示如何使用配置文件保护服务。</span><span class="sxs-lookup"><span data-stu-id="1871f-113">The fourth and fifth procedure shows how to do it with a configuration file.</span></span>

## <a name="using-code"></a><span data-ttu-id="1871f-114">使用代码</span><span class="sxs-lookup"><span data-stu-id="1871f-114">Using Code</span></span>

<span data-ttu-id="1871f-115">服务和客户端的完整代码位于本主题末尾的“示例”一节中。</span><span class="sxs-lookup"><span data-stu-id="1871f-115">The complete code for the service and the client is in the Example section at the end of this topic.</span></span>

<span data-ttu-id="1871f-116">第一个过程演练如何在代码中创建和配置 <xref:System.ServiceModel.WSHttpBinding> 类。</span><span class="sxs-lookup"><span data-stu-id="1871f-116">The first procedure walks through creating and configuring a <xref:System.ServiceModel.WSHttpBinding> class in code.</span></span> <span data-ttu-id="1871f-117">该绑定使用 HTTP 传输。</span><span class="sxs-lookup"><span data-stu-id="1871f-117">The binding uses the HTTP transport.</span></span> <span data-ttu-id="1871f-118">在客户端上使用了同一绑定。</span><span class="sxs-lookup"><span data-stu-id="1871f-118">The same binding is used on the client.</span></span>

#### <a name="to-create-a-wshttpbinding-that-uses-windows-credentials-and-message-security"></a><span data-ttu-id="1871f-119">创建使用 Windows 凭据和消息安全的 WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="1871f-119">To create a WSHttpBinding that uses Windows credentials and message security</span></span>

1. <span data-ttu-id="1871f-120">在“示例”一节的服务代码中，将此过程的代码插入到 `Run` 类的 `Test` 方法开头。</span><span class="sxs-lookup"><span data-stu-id="1871f-120">This procedure's code is inserted at the beginning of the `Run` method of the `Test` class in the service code in the Example section.</span></span>

2. <span data-ttu-id="1871f-121">创建 <xref:System.ServiceModel.WSHttpBinding> 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="1871f-121">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

3. <span data-ttu-id="1871f-122">将 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> 类的 <xref:System.ServiceModel.WSHttpSecurity> 属性设置为 <xref:System.ServiceModel.SecurityMode.Message>。</span><span class="sxs-lookup"><span data-stu-id="1871f-122">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property of the <xref:System.ServiceModel.WSHttpSecurity> class to <xref:System.ServiceModel.SecurityMode.Message>.</span></span>

4. <span data-ttu-id="1871f-123">将 <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> 类的 <xref:System.ServiceModel.MessageSecurityOverHttp> 属性设置为 <xref:System.ServiceModel.MessageCredentialType.Windows>。</span><span class="sxs-lookup"><span data-stu-id="1871f-123">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property of the <xref:System.ServiceModel.MessageSecurityOverHttp> class to <xref:System.ServiceModel.MessageCredentialType.Windows>.</span></span>

5. <span data-ttu-id="1871f-124">此过程的代码如下：</span><span class="sxs-lookup"><span data-stu-id="1871f-124">The code for this procedure is as follows:</span></span>

    [!code-csharp[c_SecureWindowsService#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#1)]
    [!code-vb[c_SecureWindowsService#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#1)]

### <a name="using-the-binding-in-a-service"></a><span data-ttu-id="1871f-125">在服务中使用该绑定</span><span class="sxs-lookup"><span data-stu-id="1871f-125">Using the Binding in a Service</span></span>

<span data-ttu-id="1871f-126">这是第二个过程，演示如何在自承载服务中使用该绑定。</span><span class="sxs-lookup"><span data-stu-id="1871f-126">This is the second procedure, which shows how to use the binding in a self-hosted service.</span></span> <span data-ttu-id="1871f-127">有关托管服务的详细信息，请参阅[托管服务](../../../docs/framework/wcf/hosting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1871f-127">For more information about hosting services see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>

##### <a name="to-use-a-binding-in-a-service"></a><span data-ttu-id="1871f-128">在服务中使用绑定</span><span class="sxs-lookup"><span data-stu-id="1871f-128">To use a binding in a service</span></span>

1. <span data-ttu-id="1871f-129">在上一过程的代码之后插入此过程的代码。</span><span class="sxs-lookup"><span data-stu-id="1871f-129">Insert this procedure's code after the code from the preceding procedure.</span></span>

2. <span data-ttu-id="1871f-130">创建一个名为 <xref:System.Type> 的 `contractType` 变量，并为其分配接口类型 (`ICalculator`)。</span><span class="sxs-lookup"><span data-stu-id="1871f-130">Create a <xref:System.Type> variable named `contractType` and assign it the type of the interface (`ICalculator`).</span></span> <span data-ttu-id="1871f-131">使用 Visual Basic 时，请使用`GetType`运算符; 使用时C#，请使用`typeof`关键字。</span><span class="sxs-lookup"><span data-stu-id="1871f-131">When using Visual Basic, use the `GetType` operator; when using C#, use the `typeof` keyword.</span></span>

3. <span data-ttu-id="1871f-132">创建另一个名为 <xref:System.Type> 的 `serviceType` 变量，并为其分配所实现的协定的类型 (`Calculator`)。</span><span class="sxs-lookup"><span data-stu-id="1871f-132">Create a second <xref:System.Type> variable named `serviceType` and assign it the type of the implemented contract (`Calculator`).</span></span>

4. <span data-ttu-id="1871f-133">使用该服务的基址创建 <xref:System.Uri> 类的一个实例，该实例名为 `baseAddress`。</span><span class="sxs-lookup"><span data-stu-id="1871f-133">Create an instance of the <xref:System.Uri> class named `baseAddress` with the base address of the service.</span></span> <span data-ttu-id="1871f-134">基址必须具有与传输匹配的方案。</span><span class="sxs-lookup"><span data-stu-id="1871f-134">The base address must have a scheme that matches the transport.</span></span> <span data-ttu-id="1871f-135">在这种情况下，传输方案为 HTTP，地址包含特殊的统一资源标识符（URI） "localhost" 和端口号（8036）以及基本终结点地址（"serviceModelSamples/）： `http://localhost:8036/serviceModelSamples/`"。</span><span class="sxs-lookup"><span data-stu-id="1871f-135">In this case, the transport scheme is HTTP, and the address includes the special Uniform Resource Identifier (URI) "localhost" and a port number (8036) as well as a base endpoint address ("serviceModelSamples/): `http://localhost:8036/serviceModelSamples/`.</span></span>

5. <span data-ttu-id="1871f-136">使用 <xref:System.ServiceModel.ServiceHost> 和 `serviceType` 变量创建 `baseAddress` 类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="1871f-136">Create an instance of the <xref:System.ServiceModel.ServiceHost> class with the `serviceType` and `baseAddress` variables.</span></span>

6. <span data-ttu-id="1871f-137">使用 `contractType`、绑定和终结点名称 (secureCalculator) 将一个终结点添加到服务中。</span><span class="sxs-lookup"><span data-stu-id="1871f-137">Add an endpoint to the service using the `contractType`, binding, and an endpoint name (secureCalculator).</span></span> <span data-ttu-id="1871f-138">在启动对服务的调用时，客户端必须将基址和终结点名称连接起来。</span><span class="sxs-lookup"><span data-stu-id="1871f-138">A client must concatenate the base address and the endpoint name when initiating a call to the service.</span></span>

7. <span data-ttu-id="1871f-139">调用 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> 方法以启动该服务。</span><span class="sxs-lookup"><span data-stu-id="1871f-139">Call the <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> method to start the service.</span></span> <span data-ttu-id="1871f-140">此过程的代码如下所示：</span><span class="sxs-lookup"><span data-stu-id="1871f-140">The code for this procedure is shown here:</span></span>

    [!code-csharp[c_SecureWindowsService#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#2)]
    [!code-vb[c_SecureWindowsService#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsservice/vb/secureservice.vb#2)]

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="1871f-141">在客户端中使用该绑定</span><span class="sxs-lookup"><span data-stu-id="1871f-141">Using the Binding in a Client</span></span>

<span data-ttu-id="1871f-142">此过程演示如何生成与服务进行通信的代理。</span><span class="sxs-lookup"><span data-stu-id="1871f-142">This procedure shows how to generate a proxy that communicates with the service.</span></span> <span data-ttu-id="1871f-143">该代理使用的[元数据实用工具（svcutil.exe）](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)生成，该工具使用服务元数据创建代理。</span><span class="sxs-lookup"><span data-stu-id="1871f-143">The proxy is generated with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) which uses the service metadata to create the proxy.</span></span>

<span data-ttu-id="1871f-144">此过程还创建 <xref:System.ServiceModel.WSHttpBinding> 类的实例以便与服务进行通信，然后调用服务。</span><span class="sxs-lookup"><span data-stu-id="1871f-144">This procedure also creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class to communicate with the service, and then calls the service.</span></span>

<span data-ttu-id="1871f-145">本示例仅使用代码来创建客户端。</span><span class="sxs-lookup"><span data-stu-id="1871f-145">This example uses only code to create the client.</span></span> <span data-ttu-id="1871f-146">另一种方法是使用配置文件，如此过程之后的一节所示。</span><span class="sxs-lookup"><span data-stu-id="1871f-146">As an alternative, you can use a configuration file, which is shown in the section following this procedure.</span></span>

##### <a name="to-use-a-binding-in-a-client-with-code"></a><span data-ttu-id="1871f-147">通过代码在客户端中使用绑定</span><span class="sxs-lookup"><span data-stu-id="1871f-147">To use a binding in a client with code</span></span>

1. <span data-ttu-id="1871f-148">使用 SvcUtil.exe 工具根据服务的元数据生成代理代码。</span><span class="sxs-lookup"><span data-stu-id="1871f-148">Use the SvcUtil.exe tool to generate the proxy code from the service's metadata.</span></span> <span data-ttu-id="1871f-149">有关详细信息，请参阅[如何：创建客户端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="1871f-149">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="1871f-150">生成的代理代码是从<xref:System.ServiceModel.ClientBase%601>类继承的，这可确保每个客户端都具有所需的构造函数、方法和属性以与 WCF 服务进行通信。</span><span class="sxs-lookup"><span data-stu-id="1871f-150">The generated proxy code inherits from the <xref:System.ServiceModel.ClientBase%601> class, which ensures that every client has the necessary constructors, methods, and properties to communicate with a WCF service.</span></span> <span data-ttu-id="1871f-151">在本示例中，生成的代码包括 `CalculatorClient` 类，该类实现了 `ICalculator` 接口，以便与服务代码兼容。</span><span class="sxs-lookup"><span data-stu-id="1871f-151">In this example, the generated code includes the `CalculatorClient` class, which implements the `ICalculator` interface, enabling compatibility with the service code.</span></span>

2. <span data-ttu-id="1871f-152">在客户端程序的 `Main` 方法的开头插入此过程的代码。</span><span class="sxs-lookup"><span data-stu-id="1871f-152">This procedure's code is inserted at the beginning of the `Main` method of the client program.</span></span>

3. <span data-ttu-id="1871f-153">创建 <xref:System.ServiceModel.WSHttpBinding> 类的一个实例，并且将其安全模式设置为 `Message`，将其客户端凭据类型设置为 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="1871f-153">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to `Message` and its client credential type to `Windows`.</span></span> <span data-ttu-id="1871f-154">本示例将变量命名为 `clientBinding`。</span><span class="sxs-lookup"><span data-stu-id="1871f-154">The example names the variable `clientBinding`.</span></span>

4. <span data-ttu-id="1871f-155">创建 <xref:System.ServiceModel.EndpointAddress> 类的一个实例，该实例名为 `serviceAddress`。</span><span class="sxs-lookup"><span data-stu-id="1871f-155">Create an instance of the <xref:System.ServiceModel.EndpointAddress> class named `serviceAddress`.</span></span> <span data-ttu-id="1871f-156">将基址与终结点名称连接起来以初始化该实例。</span><span class="sxs-lookup"><span data-stu-id="1871f-156">Initialize the instance with the base address concatenated with the endpoint name.</span></span>

5. <span data-ttu-id="1871f-157">使用 `serviceAddress` 和 `clientBinding` 变量创建所生成的客户端类的一个实例。</span><span class="sxs-lookup"><span data-stu-id="1871f-157">Create an instance of the generated client class with the `serviceAddress` and the `clientBinding` variables.</span></span>

6. <span data-ttu-id="1871f-158">调用 <xref:System.ServiceModel.ClientBase%601.Open%2A> 方法，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="1871f-158">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

7. <span data-ttu-id="1871f-159">调用服务并显示结果。</span><span class="sxs-lookup"><span data-stu-id="1871f-159">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#1)]
    [!code-vb[c_secureWindowsClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#1)]

## <a name="using-the-configuration-file"></a><span data-ttu-id="1871f-160">使用配置文件</span><span class="sxs-lookup"><span data-stu-id="1871f-160">Using the Configuration File</span></span>

<span data-ttu-id="1871f-161">如果不用程序代码创建绑定，还可以使用下面所示的配置文件绑定节的代码。</span><span class="sxs-lookup"><span data-stu-id="1871f-161">Instead of creating the binding with procedural code, you can use the following code shown for the bindings section of the configuration file.</span></span>

<span data-ttu-id="1871f-162">如果还没有定义服务，请参阅[设计和实现服务](../../../docs/framework/wcf/designing-and-implementing-services.md)和[配置服务](../../../docs/framework/wcf/configuring-services.md)。</span><span class="sxs-lookup"><span data-stu-id="1871f-162">If you do not already have a service defined, see [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Configuring Services](../../../docs/framework/wcf/configuring-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1871f-163">此配置代码在服务和客户端配置文件中使用。</span><span class="sxs-lookup"><span data-stu-id="1871f-163">This configuration code is used in both the service and client configuration files.</span></span>

#### <a name="to-enable-transfer-security-on-a-service-in-a-windows-domain-using-configuration"></a><span data-ttu-id="1871f-164">使用配置在 Windows 域中的服务上启用传输安全</span><span class="sxs-lookup"><span data-stu-id="1871f-164">To enable transfer security on a service in a Windows domain using configuration</span></span>

1. <span data-ttu-id="1871f-165">将 wsHttpBinding > 元素添加到[配置文件的绑定>元素部分。\<](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) [ \<](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="1871f-165">Add a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section of the configuration file.</span></span>

2. <span data-ttu-id="1871f-166">将 <`binding`> 元素添加到 <`WSHttpBinding` `configurationName` > 元素，并将属性设置为适合于应用程序的值。</span><span class="sxs-lookup"><span data-stu-id="1871f-166">Add a <`binding`> element to the <`WSHttpBinding`> element and set the `configurationName` attribute to a value appropriate to your application.</span></span>

3. <span data-ttu-id="1871f-167">添加一个 <`security`> 元素，并`mode`将属性设置为 Message。</span><span class="sxs-lookup"><span data-stu-id="1871f-167">Add a <`security`> element and set the `mode` attribute to Message.</span></span>

4. <span data-ttu-id="1871f-168">添加一个 <`message`> 元素，并`clientCredentialType`将属性设置为 Windows。</span><span class="sxs-lookup"><span data-stu-id="1871f-168">Add a <`message`> element and set the `clientCredentialType` attribute to Windows.</span></span>

5. <span data-ttu-id="1871f-169">在服务的配置文件中，使用下面的代码替换 `<bindings>` 节。</span><span class="sxs-lookup"><span data-stu-id="1871f-169">In the service's configuration file, replace the `<bindings>` section with the following code.</span></span> <span data-ttu-id="1871f-170">如果还没有服务配置文件，请参阅[使用绑定配置服务和客户端](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="1871f-170">If you do not already have a service configuration file, see [Using Bindings to Configure Services and Clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md).</span></span>

    ```xml
    <bindings>
      <wsHttpBinding>
       <binding name = "wsHttpBinding_Calculator">
         <security mode="Message">
           <message clientCredentialType="Windows"/>
         </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    ```

### <a name="using-the-binding-in-a-client"></a><span data-ttu-id="1871f-171">在客户端中使用该绑定</span><span class="sxs-lookup"><span data-stu-id="1871f-171">Using the Binding in a Client</span></span>

<span data-ttu-id="1871f-172">此过程演示如何生成两个文件：一个与服务进行通信的代理和一个配置文件。</span><span class="sxs-lookup"><span data-stu-id="1871f-172">This procedure shows how to generate two files: a proxy that communicates with the service and a configuration file.</span></span> <span data-ttu-id="1871f-173">此过程还描述对客户端程序所做的更改，这是在客户端使用的第三个文件。</span><span class="sxs-lookup"><span data-stu-id="1871f-173">It also describes changes to the client program, which is the third file used on the client.</span></span>

##### <a name="to-use-a-binding-in-a-client-with-configuration"></a><span data-ttu-id="1871f-174">通过配置在客户端中使用绑定</span><span class="sxs-lookup"><span data-stu-id="1871f-174">To use a binding in a client with configuration</span></span>

1. <span data-ttu-id="1871f-175">使用 SvcUtil.exe 工具根据服务的元数据生成代理代码和配置文件。</span><span class="sxs-lookup"><span data-stu-id="1871f-175">Use the SvcUtil.exe tool to generate the proxy code and configuration file from the service's metadata.</span></span> <span data-ttu-id="1871f-176">有关详细信息，请参阅[如何：创建客户端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="1871f-176">For more information, see [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>

2. <span data-ttu-id="1871f-177">将生成的配置文件中的[绑定>节替换为上一节中的配置代码。\<](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="1871f-177">Replace the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) section of the generated configuration file with the configuration code from the preceding section.</span></span>

3. <span data-ttu-id="1871f-178">在客户端程序的 `Main` 方法的开头插入程序代码。</span><span class="sxs-lookup"><span data-stu-id="1871f-178">Procedural code is inserted at the beginning of the `Main` method of the client program.</span></span>

4. <span data-ttu-id="1871f-179">通过将配置文件中的绑定名称作为输入参数进行传递，创建所生成的客户端类的实例。</span><span class="sxs-lookup"><span data-stu-id="1871f-179">Create an instance of the generated client class passing the name of the binding in the configuration file as an input parameter.</span></span>

5. <span data-ttu-id="1871f-180">调用 <xref:System.ServiceModel.ClientBase%601.Open%2A> 方法，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="1871f-180">Call the <xref:System.ServiceModel.ClientBase%601.Open%2A> method, as shown in the following code.</span></span>

6. <span data-ttu-id="1871f-181">调用服务并显示结果。</span><span class="sxs-lookup"><span data-stu-id="1871f-181">Call the service and display the results.</span></span>

    [!code-csharp[c_secureWindowsClient#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#2)]

## <a name="example"></a><span data-ttu-id="1871f-182">示例</span><span class="sxs-lookup"><span data-stu-id="1871f-182">Example</span></span>

[!code-csharp[c_SecureWindowsService#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsservice/cs/secureservice.cs#0)]

[!code-csharp[c_SecureWindowsClient#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewindowsclient/cs/secureclient.cs#0)]
[!code-vb[c_SecureWindowsClient#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewindowsclient/vb/secureclient.vb#0)]

## <a name="see-also"></a><span data-ttu-id="1871f-183">请参阅</span><span class="sxs-lookup"><span data-stu-id="1871f-183">See also</span></span>

- <xref:System.ServiceModel.WSHttpBinding>
- [<span data-ttu-id="1871f-184">ServiceModel 元数据实用工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="1871f-184">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="1871f-185">如何：创建客户端</span><span class="sxs-lookup"><span data-stu-id="1871f-185">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="1871f-186">保护服务</span><span class="sxs-lookup"><span data-stu-id="1871f-186">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="1871f-187">安全性概述</span><span class="sxs-lookup"><span data-stu-id="1871f-187">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
