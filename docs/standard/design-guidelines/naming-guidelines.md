---
title: 命名准则
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], about naming guidelines
- naming guidelines [.NET Framework]
- class library design guidelines [.NET Framework], names
- formatting [.NET Framework], names
- identifiers, class library element names
- names [.NET Framework]
- format naming guidelines [.NET Framework]
ms.assetid: fc076d66-9b5f-42d3-aa65-61d970c794a3
author: KrzysztofCwalina
ms.openlocfilehash: 4c7f411bdf538762de18873007c839f66911f96a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127701"
---
# <a name="naming-guidelines"></a><span data-ttu-id="df691-102">命名准则</span><span class="sxs-lookup"><span data-stu-id="df691-102">Naming Guidelines</span></span>
<span data-ttu-id="df691-103">在框架开发中遵循一套一致的命名约定可极大地提升框架的可用性。</span><span class="sxs-lookup"><span data-stu-id="df691-103">Following a consistent set of naming conventions in the development of a framework can be a major contribution to the framework’s usability.</span></span> <span data-ttu-id="df691-104">通过这种方式，框架便可供许多开发人员广泛用于各种不同的项目。</span><span class="sxs-lookup"><span data-stu-id="df691-104">It allows the framework to be used by many developers on widely separated projects.</span></span> <span data-ttu-id="df691-105">除了形式的一致性外，框架元素的名称必须易于理解，且须能够传达每个元素的功能。</span><span class="sxs-lookup"><span data-stu-id="df691-105">Beyond consistency of form, names of framework elements must be easily understood and must convey the function of each element.</span></span>  
  
 <span data-ttu-id="df691-106">本文的目的是提供一组一致的命名约定，用于生成便于开发人员理解和使用的名称。</span><span class="sxs-lookup"><span data-stu-id="df691-106">The goal of this chapter is to provide a consistent set of naming conventions that results in names that make immediate sense to developers.</span></span>  
  
 <span data-ttu-id="df691-107">虽然采用这些命名约定并将其用作常规代码开发准则，可以在整个代码中实现更一致的命名，但要求仅将其用于向公共领域公开的 API（公共或受保护的类型和成员以及显式实现的接口）。</span><span class="sxs-lookup"><span data-stu-id="df691-107">Although adopting these naming conventions as general code development guidelines would result in more consistent naming throughout your code, you are required only to apply them to APIs that are publicly exposed (public or protected types and members, and explicitly implemented interfaces).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df691-108">本节内容</span><span class="sxs-lookup"><span data-stu-id="df691-108">In This Section</span></span>  
 [<span data-ttu-id="df691-109">大小写约定</span><span class="sxs-lookup"><span data-stu-id="df691-109">Capitalization Conventions</span></span>](../../../docs/standard/design-guidelines/capitalization-conventions.md)  
 [<span data-ttu-id="df691-110">通用命名约定</span><span class="sxs-lookup"><span data-stu-id="df691-110">General Naming Conventions</span></span>](../../../docs/standard/design-guidelines/general-naming-conventions.md)  
 [<span data-ttu-id="df691-111">程序集和 DLL 的名称</span><span class="sxs-lookup"><span data-stu-id="df691-111">Names of Assemblies and DLLs</span></span>](../../../docs/standard/design-guidelines/names-of-assemblies-and-dlls.md)  
 [<span data-ttu-id="df691-112">命名空间的名称</span><span class="sxs-lookup"><span data-stu-id="df691-112">Names of Namespaces</span></span>](../../../docs/standard/design-guidelines/names-of-namespaces.md)  
 [<span data-ttu-id="df691-113">类、结构和接口的名称</span><span class="sxs-lookup"><span data-stu-id="df691-113">Names of Classes, Structs, and Interfaces</span></span>](../../../docs/standard/design-guidelines/names-of-classes-structs-and-interfaces.md)  
 [<span data-ttu-id="df691-114">类型成员的名称</span><span class="sxs-lookup"><span data-stu-id="df691-114">Names of Type Members</span></span>](../../../docs/standard/design-guidelines/names-of-type-members.md)  
 [<span data-ttu-id="df691-115">命名参数</span><span class="sxs-lookup"><span data-stu-id="df691-115">Naming Parameters</span></span>](../../../docs/standard/design-guidelines/naming-parameters.md)  
 [<span data-ttu-id="df691-116">命名资源</span><span class="sxs-lookup"><span data-stu-id="df691-116">Naming Resources</span></span>](../../../docs/standard/design-guidelines/naming-resources.md)  
 <span data-ttu-id="df691-117">*部分版权 © 2005, 2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="df691-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="df691-118">*通过从 Pearson Education，Inc.的权限重新打印[Framework 设计准则：约定、 语法和模式的可重用.NET 库，第 2 版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，作为 Microsoft Windows 开发系列的一部分发布 2008 年 10 月 22 日由 Addison-wesley 专业人员。*</span><span class="sxs-lookup"><span data-stu-id="df691-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df691-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="df691-119">See also</span></span>

- [<span data-ttu-id="df691-120">框架设计指南</span><span class="sxs-lookup"><span data-stu-id="df691-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
