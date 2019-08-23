---
title: <serviceActivations>
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: fb7c699612ef12aae39aaeadaf170d0e8f2553cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936449"
---
# <a name="serviceactivations"></a><span data-ttu-id="04234-101">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="04234-101">\<serviceActivations></span></span>

<span data-ttu-id="04234-102">一个配置元素, 允许您添加用于定义映射到 Windows Communication Foundation (WCF) 服务类型的虚拟服务激活设置的设置。</span><span class="sxs-lookup"><span data-stu-id="04234-102">A configuration element that allows you to add settings that define virtual service activation settings that map to your Windows Communication Foundation (WCF) service types.</span></span> <span data-ttu-id="04234-103">使用此配置元素可以在不使用 .svc 文件的情况下激活承载在 WAS/IIS 中的服务。</span><span class="sxs-lookup"><span data-stu-id="04234-103">This makes it possible to activate services hosted in WAS/IIS without an .svc file.</span></span>

<span data-ttu-id="04234-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="04234-104">\<system.ServiceModel></span></span>\
<span data-ttu-id="04234-105">\<serviceHostingEnvironment > </span><span class="sxs-lookup"><span data-stu-id="04234-105">\<serviceHostingEnvironment></span></span>\
<span data-ttu-id="04234-106">\<serviceActivations></span><span class="sxs-lookup"><span data-stu-id="04234-106">\<serviceActivations></span></span>

## <a name="syntax"></a><span data-ttu-id="04234-107">语法</span><span class="sxs-lookup"><span data-stu-id="04234-107">Syntax</span></span>

```xml
<serviceHostingEnvironment>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="04234-108">特性和元素</span><span class="sxs-lookup"><span data-stu-id="04234-108">Attributes and Elements</span></span>

<span data-ttu-id="04234-109">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="04234-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="04234-110">特性</span><span class="sxs-lookup"><span data-stu-id="04234-110">Attributes</span></span>

<span data-ttu-id="04234-111">无。</span><span class="sxs-lookup"><span data-stu-id="04234-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="04234-112">子元素</span><span class="sxs-lookup"><span data-stu-id="04234-112">Child Elements</span></span>

|<span data-ttu-id="04234-113">元素</span><span class="sxs-lookup"><span data-stu-id="04234-113">Element</span></span>|<span data-ttu-id="04234-114">描述</span><span class="sxs-lookup"><span data-stu-id="04234-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04234-115">\<add></span><span class="sxs-lookup"><span data-stu-id="04234-115">\<add></span></span>](add-of-serviceactivations.md)|<span data-ttu-id="04234-116">添加一个指定激活服务应用程序的配置元素。</span><span class="sxs-lookup"><span data-stu-id="04234-116">Adds a configuration element that specifies the activation of a service application.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="04234-117">父元素</span><span class="sxs-lookup"><span data-stu-id="04234-117">Parent Elements</span></span>

|<span data-ttu-id="04234-118">元素</span><span class="sxs-lookup"><span data-stu-id="04234-118">Element</span></span>|<span data-ttu-id="04234-119">描述</span><span class="sxs-lookup"><span data-stu-id="04234-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="04234-120">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="04234-120">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="04234-121">定义服务承载环境要为特定传输实例化的类型。</span><span class="sxs-lookup"><span data-stu-id="04234-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|

## <a name="remarks"></a><span data-ttu-id="04234-122">备注</span><span class="sxs-lookup"><span data-stu-id="04234-122">Remarks</span></span>

<span data-ttu-id="04234-123">下面的示例演示如何在 web.config 文件中配置激活设置。</span><span class="sxs-lookup"><span data-stu-id="04234-123">The following example shows how to configure activation settings within your web.config file.</span></span>

```xml
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```

<span data-ttu-id="04234-124">使用此配置，您可以在不使用 .svc 文件的情况下激活 GreetingService。</span><span class="sxs-lookup"><span data-stu-id="04234-124">Using this configuration, you can activate the GreetingService without using an .svc file.</span></span>

<span data-ttu-id="04234-125">请注意，`<serviceHostingEnvironment>` 是应用程序级配置。</span><span class="sxs-lookup"><span data-stu-id="04234-125">Note that `<serviceHostingEnvironment>` is an application level configuration.</span></span> <span data-ttu-id="04234-126">必须将包含此配置的 `web.config` 放置到虚拟应用程序的根目录下。</span><span class="sxs-lookup"><span data-stu-id="04234-126">You have to place the `web.config` containing the configuration under the root of the virtual Application.</span></span> <span data-ttu-id="04234-127">此外, `serviceHostingEnvironment`是 machineToApplication 可继承部分。</span><span class="sxs-lookup"><span data-stu-id="04234-127">In addition, `serviceHostingEnvironment` is a machineToApplication inheritable section.</span></span> <span data-ttu-id="04234-128">如果在计算机的根目录中注册了一个服务，应用程序中的每个服务都将继承此服务。</span><span class="sxs-lookup"><span data-stu-id="04234-128">If you register a single service in the root of the machine, every service in the application will inherit this service.</span></span>

<span data-ttu-id="04234-129">基于配置的激活支持通过 http 协议和非 http 协议进行激活。</span><span class="sxs-lookup"><span data-stu-id="04234-129">Configuration-based activation supports activation over both http and non-http protocol.</span></span> <span data-ttu-id="04234-130">它需要 relativeAddress 中的扩展, 如 xoml 或 .xamlx。</span><span class="sxs-lookup"><span data-stu-id="04234-130">It requires extensions in the relativeAddress i.e. .svc, .xoml or .xamlx.</span></span> <span data-ttu-id="04234-131">您可以将自己的扩展名映射到已知的 buildProviders，然后就可以通过任意扩展名激活服务。</span><span class="sxs-lookup"><span data-stu-id="04234-131">You can map your own extensions to the know buildProviders, which will then enable you to activate service over any extension.</span></span> <span data-ttu-id="04234-132">如果发生冲突，`<serviceActivations>` 节将重写 .svc 注册。</span><span class="sxs-lookup"><span data-stu-id="04234-132">Upon conflict, the `<serviceActivations>` section overrides .svc registrations.</span></span>

## <a name="see-also"></a><span data-ttu-id="04234-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="04234-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
