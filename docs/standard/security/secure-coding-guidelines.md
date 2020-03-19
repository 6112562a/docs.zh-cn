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
# <a name="secure-coding-guidelines"></a>安全编码指南

基于证据的安全性和代码访问安全性提供非常强大的显式机制来实现安全。 大多数应用程序代码只能使用 .NET 实现的基础结构。 在某些情况下，需要额外的应用程序特定的安全性，或通过扩展安全系统或通过使用全新临时方法构建。

在代码中使用 .NET 强制权限和其他强制，应设置障碍，以防止恶意代码访问不希望其拥有的信息或执行其他不可取的操作。 此外，必须在使用受信任代码的所有预期方案中平衡安全性和可用性。

本概述介绍代码可以用于处理安全系统的不同方式。

## <a name="securing-resource-access"></a>保护资源访问

设计和编写代码时，尤其是在使用或调用来源未知的代码时，需要保护和限制该代码对资源的访问。 因此，请记住以下可确保代码安全的方法：

- 不使用代码访问安全性 (CAS)。

- 不使用部分信任的代码。

- 不要使用["允许部分受信任的调用方"](xref:System.Security.AllowPartiallyTrustedCallersAttribute)属性 （APTCA）。

- 不使用 .NET 远程处理。

- 不使用分布式组件对象模型 (DCOM)。

- 不使用二进制格式化程序。

代码访问安全和安全透明代码不支持作为具有部分受信任代码的安全边界。 建议在未实施其他安全措施的情况下，不要加载和执行未知来源的代码。 其他安全措施包括：

- 虚拟化

- AppContainers

- 操作系统 (OS) 用户和权限

- Hyper-V 容器

## <a name="security-neutral-code"></a>安全中立代码

非特定于安全性的代码不对任何安全系统进行显示处理。 它通过所接收的任何权限来运行。 尽管无法捕获与受保护操作（如使用文件、网络等）关联的安全异常的应用程序可能会导致未处理的异常，但安全中立代码仍利用 .NET 中的安全技术.

非特定于安全性的库具有你应了解的特殊性质。 假设您的库提供使用文件或调用非托管代码的 API 元素。 如果代码没有相应的权限，则代码不会按照所述运行。 但是，即使代码具有权限，调用它的任何应用程序代码必须具有相同的权限才能正常运行。 如果调用代码没有正确的权限，则 作为代码访问安全<xref:System.Security.SecurityException>堆栈遍历的结果将出现 。

## <a name="application-code-that-isnt-a-reusable-component"></a>不是可重用组件的应用程序代码

如果代码是其他代码不会调用的应用程序的一部分，则安全性很简单，并且可能不需要特殊编码。 但请记住，恶意代码可以调用你的代码。 代码访问安全性可能会阻止恶意代码访问资源，而此类代码仍然可以读取你的字段或可能包含敏感信息的属性的值。

此外，如果你的代码接受来自 Internet 或其他不可靠来源的用户输入，则务必要小心恶意输入。

## <a name="managed-wrapper-to-native-code-implementation"></a>托管包装到本机代码实现

通常在这种情况下，某些有用功能是在你想要提供给托管代码的本机代码中实现的。 托管包装器可通过使用平台调用或 COM 互操作轻松写入。 但如果你这样做，包装器的调用方必须具有非托管代码权限才能成功。 在默认策略下，这意味着从 Intranet 或 Internet 下载的代码将不能与包装器配合使用。

与其将非托管代码权限授予使用这些包装器的所有应用程序，不如仅将这些权限授予包装代码。 如果基础功能没有公开任何资源，且实现同样也安全，则包装器只需断言其权限，这可使任何代码通过它进行调用。 当涉及资源时，安全编码应该与下一节中所述的库代码案例相同。 因为包装器可能对这些资源公开调用方，所以仔细验证本机代码的安全性是必要的，这是包装器的责任。

## <a name="library-code-that-exposes-protected-resources"></a>公开受保护资源的库代码

以下方法是安全编码最强大且具有潜在危险（如果处理不正确）：您的库充当其他代码访问某些不可用资源的接口，就像 .NET 类强制他们使用的资源的权限。 只要公开资源，你的代码首先就必须要求相应资源的权限（也就是说，必须执行安全检查），然后通常断言其权限来执行实际的操作。

## <a name="related-topics"></a>相关主题

|标题|说明|
|-----------|-----------------|
|[保护状态数据](securing-state-data.md)|说明如何保护私有成员。|
|[安全性和用户输入](security-and-user-input.md)|说明用于接受用户输入的应用程序的安全问题。|
|[安全性和争用条件](security-and-race-conditions.md)|说明如何避免代码中的争用条件。|
|[安全性和进行中的代码生成](security-and-on-the-fly-code-generation.md)|说明用于生成动态代码的应用程序的安全问题。|
|[基于角色的安全性](role-based-security.md)|详细介绍了基于 .NET 角色的安全性，并提供了在代码中使用它的说明。|
