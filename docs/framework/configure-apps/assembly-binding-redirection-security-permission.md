---
title: 程序集绑定重定向安全权限
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d4483d11903d61135585a2b6c2c33eff48300151
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616009"
---
# <a name="assembly-binding-redirection-security-permission"></a><span data-ttu-id="a0a32-102">程序集绑定重定向安全权限</span><span class="sxs-lookup"><span data-stu-id="a0a32-102">Assembly Binding Redirection Security Permission</span></span>
<span data-ttu-id="a0a32-103">应用程序配置文件中的显式程序集绑定重定向需要安全权限。</span><span class="sxs-lookup"><span data-stu-id="a0a32-103">Explicit assembly binding redirection in an application configuration file requires a security permission.</span></span> <span data-ttu-id="a0a32-104">这适用于对 .NET Framework 程序集和来自第三方的程序集的重定向。</span><span class="sxs-lookup"><span data-stu-id="a0a32-104">This applies to redirection of .NET Framework assemblies and assemblies from third parties.</span></span> <span data-ttu-id="a0a32-105">通过设置授予权限<xref:System.Security.Permissions.SecurityPermissionFlag>标志<xref:System.Security.Permissions.SecurityPermission>。</span><span class="sxs-lookup"><span data-stu-id="a0a32-105">The permission is granted by setting the <xref:System.Security.Permissions.SecurityPermissionFlag> flag on the <xref:System.Security.Permissions.SecurityPermission>.</span></span> <span data-ttu-id="a0a32-106">托管程序集默认情况下没有任何权限。</span><span class="sxs-lookup"><span data-stu-id="a0a32-106">Managed assemblies have no permissions by default.</span></span>  
  
 <span data-ttu-id="a0a32-107">安全权限授予受信任的区域 （本地计算机） 和 Intranet 区域中运行的应用程序。</span><span class="sxs-lookup"><span data-stu-id="a0a32-107">The security permission is granted to applications running in the Trusted Zone (local machine) and Intranet Zone.</span></span> <span data-ttu-id="a0a32-108">在 Internet 区域中运行的应用程序严格禁止执行程序集绑定重定向。</span><span class="sxs-lookup"><span data-stu-id="a0a32-108">Applications running in the Internet Zone are strictly prohibited from performing assembly binding redirection.</span></span>  
  
 <span data-ttu-id="a0a32-109">如果在发布服务器策略文件控制的组件发布服务器，或由管理员控制计算机配置文件中执行程序集重定向，则不需要该权限。</span><span class="sxs-lookup"><span data-stu-id="a0a32-109">The permission is not required if assembly redirection is performed in a publisher policy file that is controlled by the component publisher, or in the machine configuration file that is controlled by the administrator.</span></span> <span data-ttu-id="a0a32-110">但是，该权限是以显式忽略发行者策略使用的应用需要[ \<apply ="no"/ >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)应用程序配置文件中的元素。</span><span class="sxs-lookup"><span data-stu-id="a0a32-110">However, the permission is required for an application to explicitly ignore publisher policy using the [\<publisherPolicy apply="no"/>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element in the application configuration file.</span></span>  
  
 <span data-ttu-id="a0a32-111">下表显示的默认安全设置**BindingRedirects**标志。</span><span class="sxs-lookup"><span data-stu-id="a0a32-111">The following table shows the default security settings for the **BindingRedirects** flag.</span></span>  
  
|<span data-ttu-id="a0a32-112">区域</span><span class="sxs-lookup"><span data-stu-id="a0a32-112">Zone</span></span>|<span data-ttu-id="a0a32-113">BindingRedirects 标志设置</span><span class="sxs-lookup"><span data-stu-id="a0a32-113">BindingRedirects flag setting</span></span>|  
|----------|-----------------------------------|  
|<span data-ttu-id="a0a32-114">受信任的区域 （本地计算机）</span><span class="sxs-lookup"><span data-stu-id="a0a32-114">Trusted Zone (local machine)</span></span>|<span data-ttu-id="a0a32-115">**ON**</span><span class="sxs-lookup"><span data-stu-id="a0a32-115">**ON**</span></span>|  
|<span data-ttu-id="a0a32-116">Intranet 区域</span><span class="sxs-lookup"><span data-stu-id="a0a32-116">Intranet Zone</span></span>|<span data-ttu-id="a0a32-117">**ON**</span><span class="sxs-lookup"><span data-stu-id="a0a32-117">**ON**</span></span>|  
|<span data-ttu-id="a0a32-118">Internet 区域</span><span class="sxs-lookup"><span data-stu-id="a0a32-118">Internet Zone</span></span>|<span data-ttu-id="a0a32-119">**OFF**</span><span class="sxs-lookup"><span data-stu-id="a0a32-119">**OFF**</span></span>|  
|<span data-ttu-id="a0a32-120">不受信任的区域</span><span class="sxs-lookup"><span data-stu-id="a0a32-120">Untrusted zones</span></span>|<span data-ttu-id="a0a32-121">**OFF**</span><span class="sxs-lookup"><span data-stu-id="a0a32-121">**OFF**</span></span>|  
  
 <span data-ttu-id="a0a32-122">管理员可以更改这些安全设置，以支持或限制给定计算机上的特定方案。</span><span class="sxs-lookup"><span data-stu-id="a0a32-122">An administrator can change these security settings to support or restrict specific scenarios on a given computer.</span></span> <span data-ttu-id="a0a32-123">有工具可用于更改**BindingRedirects**标志设置从默认设置; 管理员必须手动编辑用户的计算机上的 Security.config 文件。</span><span class="sxs-lookup"><span data-stu-id="a0a32-123">There are no tools for changing the **BindingRedirects** flag setting from the default; an administrator must manually edit the Security.config file on a user's computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0a32-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="a0a32-124">See also</span></span>
- [<span data-ttu-id="a0a32-125">发布服务器策略文件和通过并行执行</span><span class="sxs-lookup"><span data-stu-id="a0a32-125">Publisher Policy Files and Side-by-Side Execution</span></span>](https://msdn.microsoft.com/library/97a042be-4d72-40c3-91c0-76fd36bdf133)
- [<span data-ttu-id="a0a32-126">如何：启用和禁用自动绑定重定向</span><span class="sxs-lookup"><span data-stu-id="a0a32-126">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="a0a32-127">并行执行</span><span class="sxs-lookup"><span data-stu-id="a0a32-127">Side-by-Side Execution</span></span>](../../../docs/framework/deployment/side-by-side-execution.md)
