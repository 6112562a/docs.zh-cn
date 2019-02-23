---
title: Windows 窗体安全
ms.date: 03/30/2017
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
ms.openlocfilehash: 1da8e2c6ed8091b5931e8b0a881b54329228e82a
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746780"
---
# <a name="windows-forms-security"></a><span data-ttu-id="55b31-102">Windows 窗体安全</span><span class="sxs-lookup"><span data-stu-id="55b31-102">Windows Forms Security</span></span>
<span data-ttu-id="55b31-103">Windows 窗体的功能是基于代码的 （安全级别设置为代码，而不考虑运行代码的用户） 的安全模型。</span><span class="sxs-lookup"><span data-stu-id="55b31-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="55b31-104">其中不包括任何可能已在您的计算机系统中的安全架构。</span><span class="sxs-lookup"><span data-stu-id="55b31-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="55b31-105">其中可能包括那些在浏览器 （如基于区域的安全在 Internet Explorer 中可用） 或操作系统 （例如基于凭据的 Windows NT 的安全性）。</span><span class="sxs-lookup"><span data-stu-id="55b31-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55b31-106">本节内容</span><span class="sxs-lookup"><span data-stu-id="55b31-106">In This Section</span></span>  
 [<span data-ttu-id="55b31-107">Windows 窗体中的安全性概述</span><span class="sxs-lookup"><span data-stu-id="55b31-107">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 <span data-ttu-id="55b31-108">简要介绍了.NET Framework 安全模型并要确保你的应用程序中的 Windows 窗体所需的基本步骤的安全。</span><span class="sxs-lookup"><span data-stu-id="55b31-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="55b31-109">在 Windows 窗体中提高文件和数据访问的安全性</span><span class="sxs-lookup"><span data-stu-id="55b31-109">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="55b31-110">介绍如何访问文件和不完全受信任环境中的数据。</span><span class="sxs-lookup"><span data-stu-id="55b31-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="55b31-111">Windows 窗体中更加安全的打印</span><span class="sxs-lookup"><span data-stu-id="55b31-111">More Secure Printing in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="55b31-112">介绍如何访问部分信任的环境中的打印功能。</span><span class="sxs-lookup"><span data-stu-id="55b31-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="55b31-113">Windows 窗体中额外的安全注意事项</span><span class="sxs-lookup"><span data-stu-id="55b31-113">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="55b31-114">介绍使用剪贴板，并调用非托管代码在部分信任的环境中执行窗口操作。</span><span class="sxs-lookup"><span data-stu-id="55b31-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="55b31-115">相关章节</span><span class="sxs-lookup"><span data-stu-id="55b31-115">Related Sections</span></span>  
 <span data-ttu-id="55b31-116">[默认安全策略](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55b31-116">[Default Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span></span>  
 <span data-ttu-id="55b31-117">列出了授予完全信任、 本地 Intranet 和 Internet 权限集的默认权限。</span><span class="sxs-lookup"><span data-stu-id="55b31-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 <span data-ttu-id="55b31-118">[常规安全策略管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55b31-118">[General Security Policy Administration](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span></span>  
 <span data-ttu-id="55b31-119">提供有关管理的.NET Framework 安全策略和提升权限的信息。</span><span class="sxs-lookup"><span data-stu-id="55b31-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="55b31-120">危险权限和策略管理</span><span class="sxs-lookup"><span data-stu-id="55b31-120">Dangerous Permissions and Policy Administration</span></span>](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="55b31-121">讨论一些可能允许绕过安全系统的.net Framework 权限。</span><span class="sxs-lookup"><span data-stu-id="55b31-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="55b31-122">安全编码准则</span><span class="sxs-lookup"><span data-stu-id="55b31-122">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="55b31-123">这些主题介绍用于安全地编写针对.NET Framework 代码的最佳做法的链接。</span><span class="sxs-lookup"><span data-stu-id="55b31-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 <span data-ttu-id="55b31-124">[请求权限](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55b31-124">[Requesting Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span></span>  
 <span data-ttu-id="55b31-125">介绍如何使用属性告知运行时知道你的代码需要运行哪些权限。</span><span class="sxs-lookup"><span data-stu-id="55b31-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="55b31-126">安全性的基础概念</span><span class="sxs-lookup"><span data-stu-id="55b31-126">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="55b31-127">链接到介绍代码安全性的基本方面的主题。</span><span class="sxs-lookup"><span data-stu-id="55b31-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="55b31-128">代码访问安全性基础知识</span><span class="sxs-lookup"><span data-stu-id="55b31-128">Code Access Security Basics</span></span>](../../../docs/framework/misc/code-access-security-basics.md)  
 <span data-ttu-id="55b31-129">讨论使用运行时安全策略的.NET Framework 的基础知识。</span><span class="sxs-lookup"><span data-stu-id="55b31-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 <span data-ttu-id="55b31-130">[确定何时修改安全策略](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55b31-130">[Determining When to Modify Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span></span>  
 <span data-ttu-id="55b31-131">介绍如何确定您的应用程序需要从默认的安全策略发生偏离。</span><span class="sxs-lookup"><span data-stu-id="55b31-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 <span data-ttu-id="55b31-132">[部署安全性策略](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="55b31-132">[Deploying Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span></span>  
 <span data-ttu-id="55b31-133">讨论用于部署的安全策略更改的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="55b31-133">Discusses the best manner for deploying security policy changes.</span></span>
