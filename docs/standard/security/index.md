---
title: .NET 中的安全性
ms.date: 06/04/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, security
- security [.NET], about security
- application development [.NET], security
- security [.NET Framework]
- security [.NET]
ms.assetid: 9a9621d7-8883-4a4f-a874-65e8e09e20a6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e60f463d5a691cb84a30c169e471aa905b2db17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61860550"
---
# <a name="security-in-net"></a><span data-ttu-id="7be29-102">.NET 中的安全性</span><span class="sxs-lookup"><span data-stu-id="7be29-102">Security in .NET</span></span>
<span data-ttu-id="7be29-103">公共语言运行时和.NET 提供了许多有用的类和服务，使开发人员能够轻松地编写安全代码，并使系统管理员可以自定义，以便它可以访问代码授予的权限受保护的资源。</span><span class="sxs-lookup"><span data-stu-id="7be29-103">The common language runtime and the .NET provide many useful classes and services that enable developers to easily write secure code and enable system administrators to customize the permissions granted to code so that it can access protected resources.</span></span> <span data-ttu-id="7be29-104">此外，运行时和.NET 提供有用的类和服务，以方便使用加密和基于角色的安全性。</span><span class="sxs-lookup"><span data-stu-id="7be29-104">In addition, the runtime and the .NET provide useful classes and services that facilitate the use of cryptography and role-based security.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7be29-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="7be29-105">In This Section</span></span>  

 [<span data-ttu-id="7be29-106">安全性的基础概念</span><span class="sxs-lookup"><span data-stu-id="7be29-106">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="7be29-107">概述公共语言运行时的安全功能。</span><span class="sxs-lookup"><span data-stu-id="7be29-107">Provides an overview of common language runtime security features.</span></span> <span data-ttu-id="7be29-108">本节是开发人员和系统管理员感兴趣的内容。</span><span class="sxs-lookup"><span data-stu-id="7be29-108">This section is of interest to developers and system administrators.</span></span>  
  
 [<span data-ttu-id="7be29-109">基于角色的安全性</span><span class="sxs-lookup"><span data-stu-id="7be29-109">Role-Based Security</span></span>](../../../docs/standard/security/role-based-security.md)  
 <span data-ttu-id="7be29-110">描述如何在代码中与基于角色的安全性进行交互。</span><span class="sxs-lookup"><span data-stu-id="7be29-110">Describes how to interact with role-based security in your code.</span></span> <span data-ttu-id="7be29-111">本节是开发人员感兴趣的内容。</span><span class="sxs-lookup"><span data-stu-id="7be29-111">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="7be29-112">加密模型</span><span class="sxs-lookup"><span data-stu-id="7be29-112">Cryptography Model</span></span>](../../../docs/standard/security/cryptography-model.md)  
 <span data-ttu-id="7be29-113">概述.NET 提供的加密服务。</span><span class="sxs-lookup"><span data-stu-id="7be29-113">Provides an overview of cryptographic services provided by .NET.</span></span> <span data-ttu-id="7be29-114">本节是开发人员感兴趣的内容。</span><span class="sxs-lookup"><span data-stu-id="7be29-114">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="7be29-115">安全编码准则</span><span class="sxs-lookup"><span data-stu-id="7be29-115">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="7be29-116">介绍了一些用于创建可靠的.NET 应用程序的最佳实践。</span><span class="sxs-lookup"><span data-stu-id="7be29-116">Describes some of the best practices for creating reliable .NET applications.</span></span> <span data-ttu-id="7be29-117">本节是开发人员感兴趣的内容。</span><span class="sxs-lookup"><span data-stu-id="7be29-117">This section is of interest to developers.</span></span>  
  
 [<span data-ttu-id="7be29-118">非托管代码的安全编码指南</span><span class="sxs-lookup"><span data-stu-id="7be29-118">Secure Coding Guidelines for Unmanaged Code</span></span>](../../../docs/framework/security/secure-coding-guidelines-for-unmanaged-code.md)  
 <span data-ttu-id="7be29-119">描述在调用非托管代码时的一些最佳做法和安全问题。</span><span class="sxs-lookup"><span data-stu-id="7be29-119">Describes some of the best practices and security concerns when calling unmanaged code.</span></span>  
  
 [<span data-ttu-id="7be29-120">Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="7be29-120">Windows Identity Foundation</span></span>](../../../docs/framework/security/index.md)  
 <span data-ttu-id="7be29-121">描述如何在应用程序中实现基于声明的标识。</span><span class="sxs-lookup"><span data-stu-id="7be29-121">Describes how you can implement claims-based identity in your applications.</span></span>  

<span data-ttu-id="7be29-122">[安全更改](../../../docs/framework/security/security-changes.md)描述对.NET Framework 安全系统的重要更改。</span><span class="sxs-lookup"><span data-stu-id="7be29-122">[Security Changes](../../../docs/framework/security/security-changes.md) Describes important changes to the .NET Framework security system.</span></span>

## <a name="related-sections"></a><span data-ttu-id="7be29-123">相关章节</span><span class="sxs-lookup"><span data-stu-id="7be29-123">Related Sections</span></span>  
 [<span data-ttu-id="7be29-124">开发指南</span><span class="sxs-lookup"><span data-stu-id="7be29-124">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
 <span data-ttu-id="7be29-125">提供了有关应用程序开发的所有关键技术区域和任务（包括创建、配置、调试、保护和部署应用程序）的指南，以及有关动态编程、互操作性、扩展性、内存管理和线程处理的信息。</span><span class="sxs-lookup"><span data-stu-id="7be29-125">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
