---
title: 为 ASP.NET AJAX 创建 WCF 服务
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: 2ec4d2f1f2fb3a6a184a524ed0134360407b4649
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964056"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a><span data-ttu-id="70c15-102">为 ASP.NET AJAX 创建 WCF 服务</span><span class="sxs-lookup"><span data-stu-id="70c15-102">Creating WCF Services for ASP.NET AJAX</span></span>

<span data-ttu-id="70c15-103">使用 Microsoft ASP.NET AJAX，可以通过快速响应的熟悉用户界面元素快速创建包括丰富用户体验的网页。</span><span class="sxs-lookup"><span data-stu-id="70c15-103">Microsoft ASP.NET AJAX enables you to quickly create Web pages that include a rich user experience with responsive and familiar user interface elements.</span></span> <span data-ttu-id="70c15-104">ASP.NET AJAX 提供了并入跨浏览器 ECMAScript (JavaScript) 和动态 HTML (DHTML) 技术的客户端脚本库，并将其与基于 ASP.NET 2.0 服务器的开发平台集成在一起。</span><span class="sxs-lookup"><span data-stu-id="70c15-104">ASP.NET AJAX provides client-script libraries that incorporate cross-browser ECMAScript (JavaScript) and dynamic HTML (DHTML) technologies, and it integrates them with the ASP.NET 2.0 server-based development platform.</span></span> <span data-ttu-id="70c15-105">通过使用 ASP.NET AJAX，可以改进用户体验和 Web 应用程序的效率。</span><span class="sxs-lookup"><span data-stu-id="70c15-105">By using ASP.NET AJAX, you can improve the user experience and the efficiency of your Web applications.</span></span>

<span data-ttu-id="70c15-106">ASP.NET AJAX 由客户端脚本库和集成的服务器组件组成，以提供稳定的开发框架。</span><span class="sxs-lookup"><span data-stu-id="70c15-106">ASP.NET AJAX consists of client-script libraries and of server components that are integrated to provide a robust development framework.</span></span> <span data-ttu-id="70c15-107">从 ASP.NET 页访问服务：将服务 URL 添加到页上的 ASP.NET 脚本管理器控件后，就可以使用看起来与常规 JavaScript 函数调用完全相同的 JavaScript 代码调用服务操作。</span><span class="sxs-lookup"><span data-stu-id="70c15-107">To access a service from an ASP.NET page: once the service URL is added to the ASP.NET Script Manager control on the page, service operations may be invoked using JavaScript code that looks exactly like a regular JavaScript function call.</span></span>

<span data-ttu-id="70c15-108">大多数 Windows Communication Foundation （WCF）服务可以通过添加适当的 ASP.NET AJAX 终结点作为与 ASP.NET AJAX 兼容的服务公开。</span><span class="sxs-lookup"><span data-stu-id="70c15-108">Most Windows Communication Foundation (WCF) services may be exposed as a service compatible with ASP.NET AJAX by adding an appropriate ASP.NET AJAX endpoint.</span></span>

<span data-ttu-id="70c15-109">如果你使用的是 Visual Studio，则在使用 ASP.NET 网站或 Web 应用程序时，可以在 "**添加新项**" 对话框中为启用了 AJAX 的 WCF 服务使用预先生成的模板。</span><span class="sxs-lookup"><span data-stu-id="70c15-109">If you are using Visual Studio, you may use a pre-built template for AJAX-enabled WCF services, available in the **Add New Item** dialog when working with ASP.NET Web Sites or Web Applications.</span></span>

<span data-ttu-id="70c15-110">如果未使用 Visual Studio 模板，则创建 ASP.NET AJAX 终结点有以下两种方法：</span><span class="sxs-lookup"><span data-stu-id="70c15-110">If you are not using the Visual Studio templates, there are two ways to create an ASP.NET AJAX endpoint:</span></span>

- <span data-ttu-id="70c15-111">使用动态主机激活（而不使用任何配置）创建终结点。</span><span class="sxs-lookup"><span data-stu-id="70c15-111">Create the endpoint using dynamic host activation without using any configuration.</span></span> <span data-ttu-id="70c15-112">如果您不熟悉 WCF 配置系统，则这是最基本的方法。</span><span class="sxs-lookup"><span data-stu-id="70c15-112">This is the most basic approach if you are unfamiliar with the WCF configuration system.</span></span> <span data-ttu-id="70c15-113">有关详细信息，请参阅[如何：在不使用配置的情况下添加 ASP.NET AJAX 终结点](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="70c15-113">For more information, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>

- <span data-ttu-id="70c15-114">使用配置将支持 AJAX 的终结点添加到 WCF 服务。</span><span class="sxs-lookup"><span data-stu-id="70c15-114">Add an AJAX-enabled endpoint to a WCF service using configuration.</span></span> <span data-ttu-id="70c15-115">有关详细信息，请参阅[如何：使用配置添加 ASP.NET AJAX 终结点](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="70c15-115">For more information, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>

<span data-ttu-id="70c15-116">[WCF WEB HTTP 编程模型概述](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)中所述的 Web 编程模型可以与 ASP.NET AJAX services 一起使用。</span><span class="sxs-lookup"><span data-stu-id="70c15-116">The Web Programming Model described in the [WCF Web HTTP Programming Model Overview](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) may be used with ASP.NET AJAX services.</span></span> <span data-ttu-id="70c15-117">具体而言：</span><span class="sxs-lookup"><span data-stu-id="70c15-117">Specifically:</span></span>

- <span data-ttu-id="70c15-118">可以使用 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性在 HTTP GET 和 HTTP POST 动词之间进行选择。</span><span class="sxs-lookup"><span data-stu-id="70c15-118">You can use the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to select between HTTP GET and HTTP POST verbs.</span></span> <span data-ttu-id="70c15-119">如果正确使用它们，则这可能会大大提高应用程序的性能。</span><span class="sxs-lookup"><span data-stu-id="70c15-119">If used correctly, this may significantly improve your application’s performance.</span></span> <span data-ttu-id="70c15-120">有关详细信息，请参阅[如何：在 ASP.NET AJAX 终结点的 HTTP POST 和 HTTP GET 请求之间进行选择](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="70c15-120">For more information, see [How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).</span></span>

- <span data-ttu-id="70c15-121">可以使用 <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> 属性使服务返回 XML 数据而不是默认的 JavaScript 对象表示法 (JSON)。</span><span class="sxs-lookup"><span data-stu-id="70c15-121">You can use the <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> and <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> properties to cause your service to return XML data instead of the default JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="70c15-122">使用 ASP.NET AJAX 框架执行此操作可导致 JavaScript 客户端接收 XML DOM 对象。</span><span class="sxs-lookup"><span data-stu-id="70c15-122">Doing this with the ASP.NET AJAX framework causes the JavaScript client to receive an XML DOM object.</span></span>

  > [!WARNING]
  > <span data-ttu-id="70c15-123">您的操作必须将内容类型设置为文本/xml 才能生效。</span><span class="sxs-lookup"><span data-stu-id="70c15-123">Your operation must set the content type to text/xml for this to work.</span></span> <span data-ttu-id="70c15-124">否则，JavaScript 客户端会接收包含 XML 的字符串而不是 XML DOM 对象。</span><span class="sxs-lookup"><span data-stu-id="70c15-124">Otherwise, the JavaScript client will receive a string containing the XML instead of an XML DOM object.</span></span>

    <span data-ttu-id="70c15-125">下面是返回正确设置了内容类型的 XML 数据的操作示例：</span><span class="sxs-lookup"><span data-stu-id="70c15-125">The following is an example of an operation that returns XML data with the content type set appropriately:</span></span>

  ```csharp
  [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]
  public XElement GetData()
  {
      XElement x;
      //Get some data here...

      WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";
      return x;
  }
  ```

- <span data-ttu-id="70c15-126">如果要求与 ASP.NET AJAX 兼容，则不能更改 <xref:System.ServiceModel.Web.WebGetAttribute> 和 <xref:System.ServiceModel.Web.WebInvokeAttribute> 特性上的任何其他属性。</span><span class="sxs-lookup"><span data-stu-id="70c15-126">No other properties on the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes can be changed if compatibility with ASP.NET AJAX is required.</span></span> <span data-ttu-id="70c15-127">只要不违反 ASP.NET AJAX 调用约定，就可以使用 Web 编程模型的其他方面。</span><span class="sxs-lookup"><span data-stu-id="70c15-127">Other aspects of the Web Programming Model can be used as long as the ASP.NET AJAX calling conventions are not violated.</span></span>

 <span data-ttu-id="70c15-128">更高级的方案需要了解 WCF 中 AJAX 支持的一些其他详细信息：</span><span class="sxs-lookup"><span data-stu-id="70c15-128">More advanced scenarios require some additional details of AJAX support in WCF be understood:</span></span>

- <span data-ttu-id="70c15-129">若要了解如何使用 JavaScript 在 AJAX 页面客户端和 WCF 服务之间传输数据，以及如何将 .NET Framework 类型映射到 JavaScript 类型的详细信息，请参阅对[JSON 和其他数据传输格式的支持](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md)。</span><span class="sxs-lookup"><span data-stu-id="70c15-129">To understand how data is transferred between an AJAX page client and a WCF service using JavaScript, and for details on how .NET Framework types map to JavaScript types, see [Support for JSON and Other Data Transfer Formats](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md).</span></span>

- <span data-ttu-id="70c15-130">若要利用 ASP.NET 功能（例如，基于 URL 的身份验证和访问 ASP.NET 会话信息），可能希望通过配置启用 ASP.NET 兼容性模式。</span><span class="sxs-lookup"><span data-stu-id="70c15-130">To take advantage of ASP.NET features, for example, URL-based authentication and accessing the ASP.NET session information, you may want to enable the ASP.NET Compatibility Mode through configuration.</span></span>

<span data-ttu-id="70c15-131">即使没有 ASP.NET AJAX framework，WCF 中的 AJAX 终结点也可能会被使用。</span><span class="sxs-lookup"><span data-stu-id="70c15-131">AJAX endpoints in WCF may even be consumed without the ASP.NET AJAX framework.</span></span> <span data-ttu-id="70c15-132">这样做需要了解 WCF 中 AJAX 支持的支持体系结构。</span><span class="sxs-lookup"><span data-stu-id="70c15-132">Doing so requires an understanding of the support architecture of AJAX support in WCF.</span></span> <span data-ttu-id="70c15-133">有关此体系结构的讨论，请参阅[WCF WEB HTTP 编程对象模型](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="70c15-133">For a discussion of this architecture, see [WCF Web HTTP Programming Object Model](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md).</span></span> <span data-ttu-id="70c15-134">有关演示此方法的代码示例，请参阅[具有 JSON 和 XML 的 AJAX 服务](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="70c15-134">For a code sample demonstrating this approach, see the [AJAX Service with JSON and XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70c15-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="70c15-135">See also</span></span>

- [<span data-ttu-id="70c15-136">WCF Web HTTP 编程模型</span><span class="sxs-lookup"><span data-stu-id="70c15-136">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="70c15-137">如何：在不使用配置的情况下添加 ASP.NET AJAX 终结点</span><span class="sxs-lookup"><span data-stu-id="70c15-137">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)
- [<span data-ttu-id="70c15-138">如何：使用配置来添加 ASP.NET AJAX 终结点</span><span class="sxs-lookup"><span data-stu-id="70c15-138">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
- [<span data-ttu-id="70c15-139">如何：在 ASP.NET AJAX 终结点的 HTTP POST 和 HTTP GET 请求之间进行选择</span><span class="sxs-lookup"><span data-stu-id="70c15-139">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
