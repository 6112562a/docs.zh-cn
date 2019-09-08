---
title: 如何：导出自定义策略断言
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
ms.openlocfilehash: 992133ff9922e36b00683f4f48db88e1c2b91c1d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795663"
---
# <a name="how-to-export-custom-policy-assertions"></a><span data-ttu-id="555a2-102">如何：导出自定义策略断言</span><span class="sxs-lookup"><span data-stu-id="555a2-102">How to: Export Custom Policy Assertions</span></span>
<span data-ttu-id="555a2-103">策略断言说明服务终结点的功能和要求。</span><span class="sxs-lookup"><span data-stu-id="555a2-103">Policy assertions describe the capabilities and requirements of a service endpoint.</span></span> <span data-ttu-id="555a2-104">服务应用程序可以在服务元数据中使用自定义策略断言，来将终结点、绑定或协定自定义信息传递到客户端应用程序。</span><span class="sxs-lookup"><span data-stu-id="555a2-104">Service applications can use custom policy assertions in service metadata to communicate endpoint, binding or contract customization information to the client application.</span></span> <span data-ttu-id="555a2-105">您可以使用 Windows Communication Foundation （WCF）在终结点、操作或消息主题的 WSDL 绑定中附加的策略表达式中导出断言，具体取决于您所通信的功能或要求。</span><span class="sxs-lookup"><span data-stu-id="555a2-105">You can use Windows Communication Foundation (WCF) to export assertions in policy expressions attached in WSDL bindings at the endpoint, operation, or message subjects, depending upon the capabilities or requirements you are communicating.</span></span>  
  
 <span data-ttu-id="555a2-106">可以通过以下方式导出自定义策略断言：在 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> 上实现 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> 接口，然后或者将绑定元素直接插入到服务终结点的绑定，或者在应用程序配置文件中注册绑定元素。</span><span class="sxs-lookup"><span data-stu-id="555a2-106">Custom policy assertions are exported by implementing the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and either inserting the binding element directly into the binding of the service endpoint or by registering the binding element in your application configuration file.</span></span> <span data-ttu-id="555a2-107">策略导出实现应将自定义策略断言作为 <xref:System.Xml.XmlElement?displayProperty=nameWithType> 实例添加到传入 <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> 方法的 <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> 上的相应 <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A>。</span><span class="sxs-lookup"><span data-stu-id="555a2-107">Your policy export implementation should add your custom policy assertion as a <xref:System.Xml.XmlElement?displayProperty=nameWithType> instance to the appropriate <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=nameWithType> on the <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> passed into the <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> method.</span></span>  
  
 <span data-ttu-id="555a2-108">另外，您需要检查 <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> 类的 <xref:System.ServiceModel.Description.WsdlExporter> 属性，并根据指定的策略版本导出正确的命名空间中的嵌套策略表达式和策略框架属性。</span><span class="sxs-lookup"><span data-stu-id="555a2-108">In addition you must check the <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> property of the <xref:System.ServiceModel.Description.WsdlExporter> class and export nested policy expressions and policy framework attributes in the correct namespace based on the policy version specified.</span></span>  
  
 <span data-ttu-id="555a2-109">若要导入自定义策略<xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType>断言[，请参阅和如何：导入自定义](how-to-import-custom-policy-assertions.md)策略断言。</span><span class="sxs-lookup"><span data-stu-id="555a2-109">To import custom policy assertions, see <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> and [How to: Import Custom Policy Assertions](how-to-import-custom-policy-assertions.md).</span></span>  
  
### <a name="to-export-custom-policy-assertions"></a><span data-ttu-id="555a2-110">导出自定义策略断言</span><span class="sxs-lookup"><span data-stu-id="555a2-110">To export custom policy assertions</span></span>  
  
1. <span data-ttu-id="555a2-111">在 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> 上实现 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> 接口。</span><span class="sxs-lookup"><span data-stu-id="555a2-111">Implement the <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> interface on a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>.</span></span> <span data-ttu-id="555a2-112">下面的代码示例演示了在绑定级别实现自定义策略断言。</span><span class="sxs-lookup"><span data-stu-id="555a2-112">The following code example shows the implementation of a custom policy assertion at the binding level.</span></span>  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2. <span data-ttu-id="555a2-113">以编程方式或者使用应用程序配置文件将绑定元素插入到终结点绑定。</span><span class="sxs-lookup"><span data-stu-id="555a2-113">Insert the binding element into the endpoint binding either programmatically or using an application configuration file.</span></span> <span data-ttu-id="555a2-114">请参见下面的过程。</span><span class="sxs-lookup"><span data-stu-id="555a2-114">See the following procedures.</span></span>  
  
### <a name="to-insert-a-binding-element-using-an-application-configuration-file"></a><span data-ttu-id="555a2-115">使用应用程序配置文件插入绑定元素</span><span class="sxs-lookup"><span data-stu-id="555a2-115">To insert a binding element using an application configuration file</span></span>  
  
1. <span data-ttu-id="555a2-116">为自定义策略断言绑定元素实现 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="555a2-116">Implement <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=nameWithType> for your custom policy assertion binding element.</span></span>  
  
2. <span data-ttu-id="555a2-117">[使用\<bindingElementExtensions >](../../configure-apps/file-schema/wcf/bindingelementextensions.md)元素将绑定元素扩展添加到配置文件。</span><span class="sxs-lookup"><span data-stu-id="555a2-117">Add the binding element extension to the configuration file using the [\<bindingElementExtensions>](../../configure-apps/file-schema/wcf/bindingelementextensions.md) element.</span></span>  
  
3. <span data-ttu-id="555a2-118">使用 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> 生成一个自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="555a2-118">Build a custom binding using the <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-insert-a-binding-element-programmatically"></a><span data-ttu-id="555a2-119">以编程方式插入绑定元素</span><span class="sxs-lookup"><span data-stu-id="555a2-119">To insert a binding element programmatically</span></span>  
  
1. <span data-ttu-id="555a2-120">创建一个新的 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> 并将其添加到 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="555a2-120">Create a new <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> and add it to a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="555a2-121">将步骤 1 中的自定义绑定添加</span><span class="sxs-lookup"><span data-stu-id="555a2-121">Add the custom binding from step 1.</span></span> <span data-ttu-id="555a2-122">到一个新的终结点，并通过调用 <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> 方法将该新服务终结点添加到 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A>。</span><span class="sxs-lookup"><span data-stu-id="555a2-122">to a new endpoint and add that new service endpoint to the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> by calling the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
3. <span data-ttu-id="555a2-123">打开 <xref:System.ServiceModel.ServiceHost>。</span><span class="sxs-lookup"><span data-stu-id="555a2-123">Open the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="555a2-124">下面的代码示例演示如何创建自定义绑定以及如何以编程方式插入绑定元素。</span><span class="sxs-lookup"><span data-stu-id="555a2-124">The following code example shows the creation of a custom binding and the programmatic insertion of binding elements.</span></span>  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="555a2-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="555a2-125">See also</span></span>

- <xref:System.ServiceModel.Description.IPolicyImportExtension>
- <xref:System.ServiceModel.Description.IPolicyExportExtension>
- [<span data-ttu-id="555a2-126">如何：导入自定义策略断言</span><span class="sxs-lookup"><span data-stu-id="555a2-126">How to: Import Custom Policy Assertions</span></span>](how-to-import-custom-policy-assertions.md)
