---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: d32db2180e06cba6662ed853ab1a259805680ea1
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397825"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="4ad61-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="4ad61-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="4ad61-102">指定用于通过 HTTPS 进行的 WS-MetadataExchange (WS-MEX) 消息交换的绑定的设置。</span><span class="sxs-lookup"><span data-stu-id="4ad61-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="4ad61-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4ad61-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4ad61-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4ad61-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4ad61-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<绑定 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4ad61-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4ad61-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding >**</span><span class="sxs-lookup"><span data-stu-id="4ad61-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ad61-107">语法</span><span class="sxs-lookup"><span data-stu-id="4ad61-107">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ad61-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="4ad61-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4ad61-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4ad61-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ad61-110">特性</span><span class="sxs-lookup"><span data-stu-id="4ad61-110">Attributes</span></span>  
  
|<span data-ttu-id="4ad61-111">特性</span><span class="sxs-lookup"><span data-stu-id="4ad61-111">Attribute</span></span>|<span data-ttu-id="4ad61-112">描述</span><span class="sxs-lookup"><span data-stu-id="4ad61-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="4ad61-113">一个 <xref:System.TimeSpan> 值，指定为完成关闭操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="4ad61-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4ad61-114">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="4ad61-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4ad61-115">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="4ad61-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="4ad61-116">一个包含绑定的配置名称的字符串。</span><span class="sxs-lookup"><span data-stu-id="4ad61-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4ad61-117">因为此值用作绑定的标识，所以它应该是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4ad61-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4ad61-118">每个绑定都具有 `name` 和 `namespace` 属性，它们共同在服务的元数据中唯一标识每个绑定。</span><span class="sxs-lookup"><span data-stu-id="4ad61-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="4ad61-119">此外，在同一类型的绑定中，此名称是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4ad61-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="4ad61-120">从 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 开始，不要求绑定和行为具有名称。</span><span class="sxs-lookup"><span data-stu-id="4ad61-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4ad61-121">有关默认配置和无值绑定和行为的详细信息，请参阅[WCF 服务的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)[简化配置](../../../wcf/simplified-configuration.md)和简化配置。</span><span class="sxs-lookup"><span data-stu-id="4ad61-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="4ad61-122">一个 <xref:System.TimeSpan> 值，指定为完成打开操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="4ad61-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4ad61-123">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="4ad61-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4ad61-124">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="4ad61-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="4ad61-125">一个 <xref:System.TimeSpan> 值，指定为完成接收操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="4ad61-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4ad61-126">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="4ad61-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4ad61-127">默认值为 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="4ad61-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="4ad61-128">一个 <xref:System.TimeSpan> 值，指定为完成发送操作提供的时间间隔。</span><span class="sxs-lookup"><span data-stu-id="4ad61-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4ad61-129">此值应大于或等于 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="4ad61-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4ad61-130">默认值为 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="4ad61-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ad61-131">子元素</span><span class="sxs-lookup"><span data-stu-id="4ad61-131">Child Elements</span></span>  
 <span data-ttu-id="4ad61-132">无。</span><span class="sxs-lookup"><span data-stu-id="4ad61-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4ad61-133">父元素</span><span class="sxs-lookup"><span data-stu-id="4ad61-133">Parent Elements</span></span>  
  
|<span data-ttu-id="4ad61-134">元素</span><span class="sxs-lookup"><span data-stu-id="4ad61-134">Element</span></span>|<span data-ttu-id="4ad61-135">描述</span><span class="sxs-lookup"><span data-stu-id="4ad61-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ad61-136">\<bindings></span><span class="sxs-lookup"><span data-stu-id="4ad61-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="4ad61-137">此元素包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="4ad61-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ad61-138">备注</span><span class="sxs-lookup"><span data-stu-id="4ad61-138">Remarks</span></span>  
 <span data-ttu-id="4ad61-139">此绑定实质上是支持使用证书的传输级安全性的 `WSHttpBinding` 绑定。</span><span class="sxs-lookup"><span data-stu-id="4ad61-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="4ad61-140">有关配置和使用此类元数据终结点的详细信息[，请参阅如何：配置自定义 WS-Metadata Exchange 绑定](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)， [如何：通过非 MEX 绑定](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)检索元数据，并使用示例[自定义安全元数据终结点](../../../wcf/samples/custom-secure-metadata-endpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="4ad61-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad61-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="4ad61-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="4ad61-142">如何：使用配置文件发布服务的元数据</span><span class="sxs-lookup"><span data-stu-id="4ad61-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="4ad61-143">通过自定义绑定发布和检索元数据</span><span class="sxs-lookup"><span data-stu-id="4ad61-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="4ad61-144">如何：配置自定义 WS-Metadata Exchange 绑定</span><span class="sxs-lookup"><span data-stu-id="4ad61-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="4ad61-145">如何：通过非 MEX 绑定检索元数据</span><span class="sxs-lookup"><span data-stu-id="4ad61-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="4ad61-146">自定义元数据终结点</span><span class="sxs-lookup"><span data-stu-id="4ad61-146">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="4ad61-147">元数据</span><span class="sxs-lookup"><span data-stu-id="4ad61-147">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="4ad61-148">绑定</span><span class="sxs-lookup"><span data-stu-id="4ad61-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4ad61-149">配置系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="4ad61-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4ad61-150">使用绑定配置服务和客户端</span><span class="sxs-lookup"><span data-stu-id="4ad61-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4ad61-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="4ad61-151">\<binding></span></span>](../../../misc/binding.md)
