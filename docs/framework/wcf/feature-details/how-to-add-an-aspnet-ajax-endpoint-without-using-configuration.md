---
title: 如何：在不使用配置的情况下添加 ASP.NET AJAX 终结点
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 4a7ff48e529ab58c8744edea22d52ad12a4d7b96
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895075"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="cb3aa-102">如何：在不使用配置的情况下添加 ASP.NET AJAX 终结点</span><span class="sxs-lookup"><span data-stu-id="cb3aa-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="cb3aa-103">Windows Communication Foundation （WCF）允许您创建一个服务，用于公开可从客户端网站上的 JavaScript 中调用的 ASP.NET 支持 AJAX 的终结点。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="cb3aa-104">若要创建这样的终结点，可以使用配置文件（与使用所有其他 WCF 终结点一样），或使用不要求任何配置元素的方法。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="cb3aa-105">本主题演示第二种方法。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="cb3aa-106">若要在不使用配置的情况下创建具有 ASP.NET AJAX 终结点的服务，则必须由 Internet 信息服务 (IIS) 来承载创建的服务。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="cb3aa-107">若要使用此方法激活 ASP.NET AJAX 终结点，请<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>在 .svc 文件中的[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指令中指定作为工厂参数。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="cb3aa-108">此自定义工厂是一个组件，可自动将 ASP.NET AJAX 终结点配置为可以从客户端网站上的 JavaScript 中调用。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="cb3aa-109">有关工作示例，请参阅[不带配置的 AJAX 服务](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="cb3aa-110">有关如何使用配置元素配置 ASP.NET AJAX 终结点的概述，请参阅[如何：使用配置添加 ASP.NET AJAX 终结点](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="cb3aa-111">创建基本 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="cb3aa-111">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="cb3aa-112">使用以<xref:System.ServiceModel.ServiceContractAttribute>特性标记的接口定义基本 WCF 服务协定。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="cb3aa-113">用 <xref:System.ServiceModel.OperationContractAttribute> 标记每个操作。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="cb3aa-114">确保设置 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="cb3aa-115">使用 `ICalculator` 实现 `CalculatorService` 服务协定。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="cb3aa-116">定义 `ICalculator` 和 `CalculatorService` 实现的命名空间，方法是将它们放置在一个命名空间块中。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="cb3aa-117">在不使用配置的情况下在 Internet 信息服务中承载服务</span><span class="sxs-lookup"><span data-stu-id="cb3aa-117">To host the service in Internet Information Services without configuration</span></span>  
  
1. <span data-ttu-id="cb3aa-118">在应用程序中创建一个名为 service 的新文件（扩展名为 .svc）。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="cb3aa-119">通过为服务添加适当[ \@的 ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指令信息来编辑此文件。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-119">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="cb3aa-120">指定要在 ServiceHost 指令中使用以便自动配置 ASP.NET AJAX 终结点。 [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory></span><span class="sxs-lookup"><span data-stu-id="cb3aa-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```text
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. <span data-ttu-id="cb3aa-121">生成服务并从客户端调用该服务。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-121">Build the service and call it from the client.</span></span> <span data-ttu-id="cb3aa-122">在调用该服务时，Internet Information Services (IIS) 会将其激活。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="cb3aa-123">有关在 IIS 中承载的详细信息， [请参阅如何：在 IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)中承载 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="cb3aa-124">调用服务</span><span class="sxs-lookup"><span data-stu-id="cb3aa-124">To call the service</span></span>  
  
1. <span data-ttu-id="cb3aa-125">终结点是在相对于 .svc 文件的空地址处配置的，因此该服务现已可用，可通过将请求发送到 service .svc/\<operation > `Add`来调用服务。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="cb3aa-126">可以通过在 ASP.NET AJAX 脚本管理器控件的“脚本”集合中输入服务 URL 来使用响应的服务。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="cb3aa-127">有关示例，请参阅[不带配置的 AJAX 服务](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb3aa-128">示例</span><span class="sxs-lookup"><span data-stu-id="cb3aa-128">Example</span></span>  
  
 <span data-ttu-id="cb3aa-129">在相对于基 URL 的空地址处创建自动配置的终结点。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="cb3aa-130">使用此方法也可以添加和使用配置文件。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="cb3aa-131">如果配置文件包含终结点定义，则这些终结点将添加到自动配置的终结点中。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="cb3aa-132">例如，service.svc 使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>，而服务目录包含一个 Web.config 文件，该文件在“soap”相对地址处使用 <xref:System.ServiceModel.BasicHttpBinding> 定义同一服务的终结点。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="cb3aa-133">在这种情况下，服务将包括两个终结点：一个在 service.svc 处（该终结点响应 ASP.NET AJAX 请求），另一个在 service.svc/soap 处（该终结点响应 SOAP 请求）。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="cb3aa-134">如果配置文件在空相对地址处定义一个终结点并且使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>，则将引发异常且无法启动服务。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="cb3aa-135">不能使用配置来修改自动配置终结点上的设置。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="cb3aa-136">如果必须修改某些设置（如读取器配额），不得通过从 .svc 文件移除 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 并创建终结点的配置项来使用免配置方法。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="cb3aa-137">如果服务要求 ASP.NET 兼容模式（例如，如果服务使用 <xref:System.Web.HttpContext> 类或 ASP.NET 授权机制），则仍需要配置文件来启用此模式。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="cb3aa-138">所需的配置元素是[ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)元素，必须按如下所示添加该元素。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="cb3aa-139">有关详细信息，请参阅[WCF 服务和 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)主题。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="cb3aa-140"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 类是 <xref:System.ServiceModel.Activation.ServiceHostFactory> 的派生类。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="cb3aa-141">有关服务主机工厂机制的详细说明，请参阅[使用 ServiceHostFactory 扩展托管](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)主题。</span><span class="sxs-lookup"><span data-stu-id="cb3aa-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb3aa-142">请参阅</span><span class="sxs-lookup"><span data-stu-id="cb3aa-142">See also</span></span>

- [<span data-ttu-id="cb3aa-143">为 ASP.NET AJAX 创建 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="cb3aa-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="cb3aa-144">如何：将启用了 AJAX 的 ASP.NET Web 服务迁移到 WCF</span><span class="sxs-lookup"><span data-stu-id="cb3aa-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
