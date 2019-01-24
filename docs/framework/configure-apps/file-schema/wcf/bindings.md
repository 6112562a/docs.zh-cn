---
title: '&lt;bindings&gt;'
ms.date: 03/30/2017
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: b7ef15f768e3eb5484bbc75eeaf988fd36fc155b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690223"
---
# <a name="ltbindingsgt"></a><span data-ttu-id="3e4ce-102">&lt;bindings&gt;</span><span class="sxs-lookup"><span data-stu-id="3e4ce-102">&lt;bindings&gt;</span></span>
<span data-ttu-id="3e4ce-103">此节包含标准绑定和自定义绑定的集合。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-103">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="3e4ce-104">每一项都是一个可由其唯一 `binding` 进行标识的 `name` 元素。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-104">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="3e4ce-105">服务通过用 `name` 与绑定进行链接来使用绑定。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-105">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="3e4ce-106">从 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 开始，不要求绑定和行为具有名称。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="3e4ce-107">有关默认配置以及无名称绑定和行为的详细信息，请参阅[Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)并[WCF 服务的简化配置](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="3e4ce-108">系统提供的绑定</span><span class="sxs-lookup"><span data-stu-id="3e4ce-108">System-Provided Binding</span></span>  
 <span data-ttu-id="3e4ce-109">系统提供的绑定可以消除 WCF 消息堆栈的复杂性。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-109">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="3e4ce-110">使用系统提供的绑定的应用程序不需要对堆栈的完全控制权限。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-110">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="3e4ce-111">在每个系统提供的绑定上公开的属性最适合绑定所针对的使用方案。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-111">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="3e4ce-112">每个系统提供的绑定的配置节可以定义用于配置此绑定的一些配置。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-112">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="3e4ce-113">每个配置均由唯一的名称进行标识。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-113">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="3e4ce-114">无法向系统提供的绑定添加元素或属性。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-114">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="3e4ce-115">为此，应该按照本主题的“自定义绑定”节中的描述来实现自定义绑定。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-115">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="3e4ce-116">可以定义一个自定义绑定，该自定义绑定将完全模仿系统提供的绑定，并添加用户应用程序希望获得其控制权限的一些设置。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-116">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
 <span data-ttu-id="3e4ce-117">有关系统提供的绑定的列表，请参阅[System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-117">For a list of system-provided bindings, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="3e4ce-118">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="3e4ce-118">Custom Binding</span></span>  
 <span data-ttu-id="3e4ce-119">自定义绑定提供了对 WCF 消息堆栈的完全控制。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-119">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="3e4ce-120">单个绑定按照堆栈元素在堆栈上出现的顺序来指定它们的配置元素，从而定义消息堆栈。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-120">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="3e4ce-121">每个元素都定义和配置了该堆栈的一个元素。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-121">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="3e4ce-122">在每个自定义绑定中，必须有且只能有一个 `transport` 元素。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-122">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="3e4ce-123">如果没有该元素，消息堆栈将是不完整的。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-123">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="3e4ce-124">元素在堆栈中出现的顺序非常重要，因为在将操作应用于消息时会采用该顺序。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-124">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="3e4ce-125">所需的堆栈元素顺序如下：</span><span class="sxs-lookup"><span data-stu-id="3e4ce-125">The required order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="3e4ce-126">事务（可选）</span><span class="sxs-lookup"><span data-stu-id="3e4ce-126">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="3e4ce-127">可靠消息（可选）</span><span class="sxs-lookup"><span data-stu-id="3e4ce-127">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="3e4ce-128">安全（可选）</span><span class="sxs-lookup"><span data-stu-id="3e4ce-128">Security (optional)</span></span>  
  
4.  <span data-ttu-id="3e4ce-129">编码器</span><span class="sxs-lookup"><span data-stu-id="3e4ce-129">Encoder</span></span>  
  
5.  <span data-ttu-id="3e4ce-130">传输</span><span class="sxs-lookup"><span data-stu-id="3e4ce-130">Transport</span></span>  
  
 <span data-ttu-id="3e4ce-131">自定义绑定由其 `name` 特性来标识。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-131">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="3e4ce-132">自定义绑定的详细信息，请参阅[自定义绑定](../../../../../docs/framework/wcf/extending/custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="3e4ce-132">For more information on custom bindings, see [Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e4ce-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="3e4ce-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- [<span data-ttu-id="3e4ce-134">绑定</span><span class="sxs-lookup"><span data-stu-id="3e4ce-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="3e4ce-135">自定义绑定</span><span class="sxs-lookup"><span data-stu-id="3e4ce-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3e4ce-136">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3e4ce-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="3e4ce-137">\<binding></span><span class="sxs-lookup"><span data-stu-id="3e4ce-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
