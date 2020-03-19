---
title: 保护 .NET 的编码准则
description: 设计要使用的代码。NET 强制权限和其他强制，以帮助防止恶意代码访问数据或执行其他操作。
ms.date: 06/28/2018
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET], security
- code security, options
- security-neutral code
- security [.NET], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
ms.openlocfilehash: 05f7e039ecdc0cd33baa015872924fb9e1f078aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187727"
---
# <a name="secure-coding-guidelines"></a><span data-ttu-id="d2aeb-103">安全编码指南</span><span class="sxs-lookup"><span data-stu-id="d2aeb-103">Secure coding guidelines</span></span>

<span data-ttu-id="d2aeb-104">基于证据的安全性和代码访问安全性提供非常强大的显式机制来实现安全。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-104">Evidence-based security and code access security provide very powerful, explicit mechanisms to implement security.</span></span> <span data-ttu-id="d2aeb-105">大多数应用程序代码只能使用 .NET 实现的基础结构。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-105">Most application code can simply use the infrastructure implemented by .NET.</span></span> <span data-ttu-id="d2aeb-106">在某些情况下，需要额外的应用程序特定的安全性，或通过扩展安全系统或通过使用全新临时方法构建。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-106">In some cases, additional application-specific security is required, built either by extending the security system or by using new ad hoc methods.</span></span>

<span data-ttu-id="d2aeb-107">在代码中使用 .NET 强制权限和其他强制，应设置障碍，以防止恶意代码访问不希望其拥有的信息或执行其他不可取的操作。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-107">Using .NET enforced permissions and other enforcement in your code, you should erect barriers to prevent malicious code from accessing information that you don't want it to have or performing other undesirable actions.</span></span> <span data-ttu-id="d2aeb-108">此外，必须在使用受信任代码的所有预期方案中平衡安全性和可用性。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-108">Additionally, you must strike a balance between security and usability in all the expected scenarios using trusted code.</span></span>

<span data-ttu-id="d2aeb-109">本概述介绍代码可以用于处理安全系统的不同方式。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-109">This overview describes the different ways code can be designed to work with the security system.</span></span>

## <a name="securing-resource-access"></a><span data-ttu-id="d2aeb-110">保护资源访问</span><span class="sxs-lookup"><span data-stu-id="d2aeb-110">Securing resource access</span></span>

<span data-ttu-id="d2aeb-111">设计和编写代码时，尤其是在使用或调用来源未知的代码时，需要保护和限制该代码对资源的访问。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-111">When designing and writing your code, you need to protect and limit the access that code has to resources, especially when using or invoking code of unknown origin.</span></span> <span data-ttu-id="d2aeb-112">因此，请记住以下可确保代码安全的方法：</span><span class="sxs-lookup"><span data-stu-id="d2aeb-112">So, keep in mind the following techniques to ensure your code is secure:</span></span>

- <span data-ttu-id="d2aeb-113">不使用代码访问安全性 (CAS)。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-113">Do not use Code Access Security (CAS).</span></span>

- <span data-ttu-id="d2aeb-114">不使用部分信任的代码。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-114">Do not use partial trusted code.</span></span>

- <span data-ttu-id="d2aeb-115">不要使用["允许部分受信任的调用方"](xref:System.Security.AllowPartiallyTrustedCallersAttribute)属性 （APTCA）。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-115">Do not use the [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) attribute (APTCA).</span></span>

- <span data-ttu-id="d2aeb-116">不使用 .NET 远程处理。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-116">Do not use .NET Remoting.</span></span>

- <span data-ttu-id="d2aeb-117">不使用分布式组件对象模型 (DCOM)。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-117">Do not use Distributed Component Object Model (DCOM).</span></span>

- <span data-ttu-id="d2aeb-118">不使用二进制格式化程序。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-118">Do not use binary formatters.</span></span>

<span data-ttu-id="d2aeb-119">代码访问安全和安全透明代码不支持作为具有部分受信任代码的安全边界。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-119">Code Access Security and Security-Transparent Code are not supported as a security boundary with partially trusted code.</span></span> <span data-ttu-id="d2aeb-120">建议在未实施其他安全措施的情况下，不要加载和执行未知来源的代码。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-120">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span> <span data-ttu-id="d2aeb-121">其他安全措施包括：</span><span class="sxs-lookup"><span data-stu-id="d2aeb-121">The alternative security measures are:</span></span>

- <span data-ttu-id="d2aeb-122">虚拟化</span><span class="sxs-lookup"><span data-stu-id="d2aeb-122">Virtualization</span></span>

- <span data-ttu-id="d2aeb-123">AppContainers</span><span class="sxs-lookup"><span data-stu-id="d2aeb-123">AppContainers</span></span>

- <span data-ttu-id="d2aeb-124">操作系统 (OS) 用户和权限</span><span class="sxs-lookup"><span data-stu-id="d2aeb-124">Operating system (OS) users and permissions</span></span>

- <span data-ttu-id="d2aeb-125">Hyper-V 容器</span><span class="sxs-lookup"><span data-stu-id="d2aeb-125">Hyper-V containers</span></span>

## <a name="security-neutral-code"></a><span data-ttu-id="d2aeb-126">安全中立代码</span><span class="sxs-lookup"><span data-stu-id="d2aeb-126">Security-neutral code</span></span>

<span data-ttu-id="d2aeb-127">非特定于安全性的代码不对任何安全系统进行显示处理。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-127">Security-neutral code does nothing explicit with the security system.</span></span> <span data-ttu-id="d2aeb-128">它通过所接收的任何权限来运行。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-128">It runs with whatever permissions it receives.</span></span> <span data-ttu-id="d2aeb-129">尽管无法捕获与受保护操作（如使用文件、网络等）关联的安全异常的应用程序可能会导致未处理的异常，但安全中立代码仍利用 .NET 中的安全技术.</span><span class="sxs-lookup"><span data-stu-id="d2aeb-129">Although applications that fail to catch security exceptions associated with protected operations (such as using files, networking, and so on) can result in an unhandled exception, security-neutral code still takes advantage of the security technologies in .NET.</span></span>

<span data-ttu-id="d2aeb-130">非特定于安全性的库具有你应了解的特殊性质。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-130">A security-neutral library has special characteristics that you should understand.</span></span> <span data-ttu-id="d2aeb-131">假设您的库提供使用文件或调用非托管代码的 API 元素。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-131">Suppose your library provides API elements that use files or call unmanaged code.</span></span> <span data-ttu-id="d2aeb-132">如果代码没有相应的权限，则代码不会按照所述运行。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-132">If your code doesn't have the corresponding permission, it won't run as described.</span></span> <span data-ttu-id="d2aeb-133">但是，即使代码具有权限，调用它的任何应用程序代码必须具有相同的权限才能正常运行。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-133">However, even if the code has the permission, any application code that calls it must have the same permission in order to work.</span></span> <span data-ttu-id="d2aeb-134">如果调用代码没有正确的权限，则 作为代码访问安全<xref:System.Security.SecurityException>堆栈遍历的结果将出现 。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-134">If the calling code doesn't have the right permission, a <xref:System.Security.SecurityException> appears as a result of the code access security stack walk.</span></span>

## <a name="application-code-that-isnt-a-reusable-component"></a><span data-ttu-id="d2aeb-135">不是可重用组件的应用程序代码</span><span class="sxs-lookup"><span data-stu-id="d2aeb-135">Application code that isn't a reusable component</span></span>

<span data-ttu-id="d2aeb-136">如果代码是其他代码不会调用的应用程序的一部分，则安全性很简单，并且可能不需要特殊编码。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-136">If your code is part of an application that won't be called by other code, security is simple and special coding might not be required.</span></span> <span data-ttu-id="d2aeb-137">但请记住，恶意代码可以调用你的代码。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-137">However, remember that malicious code can call your code.</span></span> <span data-ttu-id="d2aeb-138">代码访问安全性可能会阻止恶意代码访问资源，而此类代码仍然可以读取你的字段或可能包含敏感信息的属性的值。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-138">While code access security might stop malicious code from accessing resources, such code could still read values of your fields or properties that might contain sensitive information.</span></span>

<span data-ttu-id="d2aeb-139">此外，如果你的代码接受来自 Internet 或其他不可靠来源的用户输入，则务必要小心恶意输入。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-139">Additionally, if your code accepts user input from the Internet or other unreliable sources, you must be careful about malicious input.</span></span>

## <a name="managed-wrapper-to-native-code-implementation"></a><span data-ttu-id="d2aeb-140">托管包装到本机代码实现</span><span class="sxs-lookup"><span data-stu-id="d2aeb-140">Managed wrapper to native code implementation</span></span>

<span data-ttu-id="d2aeb-141">通常在这种情况下，某些有用功能是在你想要提供给托管代码的本机代码中实现的。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-141">Typically in this scenario, some useful functionality is implemented in native code that you want to make available to managed code.</span></span> <span data-ttu-id="d2aeb-142">托管包装器可通过使用平台调用或 COM 互操作轻松写入。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-142">Managed wrappers are easy to write using either platform invoke or COM interop.</span></span> <span data-ttu-id="d2aeb-143">但如果你这样做，包装器的调用方必须具有非托管代码权限才能成功。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-143">However, if you do this, callers of your wrappers must have unmanaged code rights in order to succeed.</span></span> <span data-ttu-id="d2aeb-144">在默认策略下，这意味着从 Intranet 或 Internet 下载的代码将不能与包装器配合使用。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-144">Under default policy, this means that code downloaded from an intranet or the Internet won't work with the wrappers.</span></span>

<span data-ttu-id="d2aeb-145">与其将非托管代码权限授予使用这些包装器的所有应用程序，不如仅将这些权限授予包装代码。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-145">Instead of giving unmanaged code rights to all applications that use these wrappers, it's better to give these rights only to the wrapper code.</span></span> <span data-ttu-id="d2aeb-146">如果基础功能没有公开任何资源，且实现同样也安全，则包装器只需断言其权限，这可使任何代码通过它进行调用。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-146">If the underlying functionality exposes no resources and the implementation is likewise safe, the wrapper only needs to assert its rights, which enables any code to call through it.</span></span> <span data-ttu-id="d2aeb-147">当涉及资源时，安全编码应该与下一节中所述的库代码案例相同。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-147">When resources are involved, security coding should be the same as the library code case described in the next section.</span></span> <span data-ttu-id="d2aeb-148">因为包装器可能对这些资源公开调用方，所以仔细验证本机代码的安全性是必要的，这是包装器的责任。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-148">Because the wrapper is potentially exposing callers to these resources, careful verification of the safety of the native code is necessary and is the wrapper's responsibility.</span></span>

## <a name="library-code-that-exposes-protected-resources"></a><span data-ttu-id="d2aeb-149">公开受保护资源的库代码</span><span class="sxs-lookup"><span data-stu-id="d2aeb-149">Library code that exposes protected resources</span></span>

<span data-ttu-id="d2aeb-150">以下方法是安全编码最强大且具有潜在危险（如果处理不正确）：您的库充当其他代码访问某些不可用资源的接口，就像 .NET 类强制他们使用的资源的权限。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-150">The following approach is the most powerful and hence potentially dangerous (if done incorrectly) for security coding: your library serves as an interface for other code to access certain resources that aren't otherwise available, just as the .NET classes enforce permissions for the resources they use.</span></span> <span data-ttu-id="d2aeb-151">只要公开资源，你的代码首先就必须要求相应资源的权限（也就是说，必须执行安全检查），然后通常断言其权限来执行实际的操作。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-151">Wherever you expose a resource, your code must first demand the permission appropriate to the resource (that is, it must perform a security check) and then typically assert its rights to perform the actual operation.</span></span>

## <a name="related-topics"></a><span data-ttu-id="d2aeb-152">相关主题</span><span class="sxs-lookup"><span data-stu-id="d2aeb-152">Related topics</span></span>

|<span data-ttu-id="d2aeb-153">标题</span><span class="sxs-lookup"><span data-stu-id="d2aeb-153">Title</span></span>|<span data-ttu-id="d2aeb-154">说明</span><span class="sxs-lookup"><span data-stu-id="d2aeb-154">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="d2aeb-155">保护状态数据</span><span class="sxs-lookup"><span data-stu-id="d2aeb-155">Securing State Data</span></span>](securing-state-data.md)|<span data-ttu-id="d2aeb-156">说明如何保护私有成员。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-156">Describes how to protect private members.</span></span>|
|[<span data-ttu-id="d2aeb-157">安全性和用户输入</span><span class="sxs-lookup"><span data-stu-id="d2aeb-157">Security and User Input</span></span>](security-and-user-input.md)|<span data-ttu-id="d2aeb-158">说明用于接受用户输入的应用程序的安全问题。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-158">Describes security concerns for applications that accept user input.</span></span>|
|[<span data-ttu-id="d2aeb-159">安全性和争用条件</span><span class="sxs-lookup"><span data-stu-id="d2aeb-159">Security and Race Conditions</span></span>](security-and-race-conditions.md)|<span data-ttu-id="d2aeb-160">说明如何避免代码中的争用条件。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-160">Describes how to avoid race conditions in your code.</span></span>|
|[<span data-ttu-id="d2aeb-161">安全性和进行中的代码生成</span><span class="sxs-lookup"><span data-stu-id="d2aeb-161">Security and On-the-Fly Code Generation</span></span>](security-and-on-the-fly-code-generation.md)|<span data-ttu-id="d2aeb-162">说明用于生成动态代码的应用程序的安全问题。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-162">Describes security concerns for applications that generate dynamic code.</span></span>|
|[<span data-ttu-id="d2aeb-163">基于角色的安全性</span><span class="sxs-lookup"><span data-stu-id="d2aeb-163">Role-Based Security</span></span>](role-based-security.md)|<span data-ttu-id="d2aeb-164">详细介绍了基于 .NET 角色的安全性，并提供了在代码中使用它的说明。</span><span class="sxs-lookup"><span data-stu-id="d2aeb-164">Describes .NET role-based security in detail and provides instructions for using it in your code.</span></span>|
