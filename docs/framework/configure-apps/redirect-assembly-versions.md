---
title: 重定向程序集版本
ms.date: 03/30/2017
helpviewer_keywords:
- assembly binding, redirection
- redirecting assembly binding to earlier version
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], binding redirection
ms.assetid: 88fb1a17-6ac9-4b57-8028-193aec1f727c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: bc193402120780c605f6139feac6f0d60a34118e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674151"
---
# <a name="redirecting-assembly-versions"></a><span data-ttu-id="68f5d-102">重定向程序集版本</span><span class="sxs-lookup"><span data-stu-id="68f5d-102">Redirecting Assembly Versions</span></span>

<span data-ttu-id="68f5d-103">你可以将编译时绑定引用重定向到 .NET Framework 程序集、第三方程序集或你自己的应用的程序集。</span><span class="sxs-lookup"><span data-stu-id="68f5d-103">You can redirect compile-time binding references to .NET Framework assemblies, third-party assemblies, or your own app's assemblies.</span></span> <span data-ttu-id="68f5d-104">你还可以重定向应用，以通过多种方式使用不同版本的程序集：通过发布服务器策略、通过应用配置文件或通过计算机配置文件。</span><span class="sxs-lookup"><span data-stu-id="68f5d-104">You can redirect your app to use a different version of an assembly in a number of ways: through publisher policy, through an app configuration file; or through the machine configuration file.</span></span> <span data-ttu-id="68f5d-105">本文讨论了程序集绑定在 .NET Framework 中的工作原理以及如何对其进行配置。</span><span class="sxs-lookup"><span data-stu-id="68f5d-105">This article discusses how assembly binding works in the .NET Framework and how it can be configured.</span></span>

<a name="BKMK_Assemblyunificationanddefaultbinding"></a>
## <a name="assembly-unification-and-default-binding"></a><span data-ttu-id="68f5d-106">程序集统一和默认绑定</span><span class="sxs-lookup"><span data-stu-id="68f5d-106">Assembly unification and default binding</span></span>
 <span data-ttu-id="68f5d-107">到 .NET Framework 程序集的绑定有时会通过称为 *“程序集统一”* 的过程进行重定向。</span><span class="sxs-lookup"><span data-stu-id="68f5d-107">Bindings to .NET Framework assemblies are sometimes redirected through a process called *assembly unification*.</span></span> <span data-ttu-id="68f5d-108">.NET Framework 包括一个公共语言运行时版本和构成类型库的约二十个 .NET Framework 程序集。</span><span class="sxs-lookup"><span data-stu-id="68f5d-108">The .NET Framework consists of a version of the common language runtime and about two dozen .NET Framework assemblies that make up the type library.</span></span> <span data-ttu-id="68f5d-109">运行时将这些 .NET Framework 程序集视为单个单元。</span><span class="sxs-lookup"><span data-stu-id="68f5d-109">These .NET Framework assemblies are treated by the runtime as a single unit.</span></span> <span data-ttu-id="68f5d-110">默认情况下，当启动应用时，由运行时运行的所有对代码中的类型的引用都将定向到具有与进程中加载的运行时相同的版本号的 .NET Framework 程序集。</span><span class="sxs-lookup"><span data-stu-id="68f5d-110">By default, when an app is launched, all references to types in code run by the runtime are directed to .NET Framework assemblies that have the same version number as the runtime that is loaded in a process.</span></span> <span data-ttu-id="68f5d-111">此模型发生的重定向是运行时的默认行为。</span><span class="sxs-lookup"><span data-stu-id="68f5d-111">The redirections that occur with this model are the default behavior for the runtime.</span></span>

 <span data-ttu-id="68f5d-112">例如，如果你的应用引用 System.XML 命名空间中的类型并使用 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]生成，则它包含对 System.XML 程序集（随附运行时版本 4.5）的静态引用。</span><span class="sxs-lookup"><span data-stu-id="68f5d-112">For example, if your app references types in the System.XML namespace and was built by using the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], it contains static references to the System.XML assembly that ships with runtime version 4.5.</span></span> <span data-ttu-id="68f5d-113">如果想要重定向绑定引用，以指向 System.XML 程序集（随附 .NET Framework 4），你可以将重定向信息放在应用配置文件中。</span><span class="sxs-lookup"><span data-stu-id="68f5d-113">If you want to redirect the binding reference to point to the System.XML assembly that ship with the .NET Framework 4, you can put redirect information in the app configuration file.</span></span> <span data-ttu-id="68f5d-114">统一的 .NET Framework 程序集的配置文件中的绑定重定向将取消该程序集的统一。</span><span class="sxs-lookup"><span data-stu-id="68f5d-114">A binding redirection in a configuration file for a unified .NET Framework assembly cancels the unification for that assembly.</span></span>

 <span data-ttu-id="68f5d-115">此外，如果有多个可用版本，可能需要手动重定向第三方程序集的程序集绑定。</span><span class="sxs-lookup"><span data-stu-id="68f5d-115">In addition, you may want to manually redirect assembly binding for third-party assemblies if there are multiple versions available.</span></span>

<a name="BKMK_Redirectingassemblyversionsbyusingpublisherpolicy"></a>
## <a name="redirecting-assembly-versions-by-using-publisher-policy"></a><span data-ttu-id="68f5d-116">通过使用发布者策略重定向程序集版本</span><span class="sxs-lookup"><span data-stu-id="68f5d-116">Redirecting assembly versions by using publisher policy</span></span>
 <span data-ttu-id="68f5d-117">程序集的供应商可以通过包括发布服务器策略文件与新的程序集，将应用定向到较新版本的程序集。</span><span class="sxs-lookup"><span data-stu-id="68f5d-117">Vendors of assemblies can direct apps to a newer version of an assembly by including a publisher policy file with the new assembly.</span></span> <span data-ttu-id="68f5d-118">位于全局程序集缓存中的发布服务器策略文件包含程序集重定向设置。</span><span class="sxs-lookup"><span data-stu-id="68f5d-118">The publisher policy file, which is located in the global assembly cache, contains assembly redirection settings.</span></span>

 <span data-ttu-id="68f5d-119">每个 *主要*、*次要* 版本的程序集都具有其自己的发布服务器策略文件。</span><span class="sxs-lookup"><span data-stu-id="68f5d-119">Each *major*.*minor* version of an assembly has its own publisher policy file.</span></span> <span data-ttu-id="68f5d-120">例如，从版本 2.0.2.222 到 2.0.3.000 和从版本 2.0.2.321 到版本 2.0.3.000 的重定向都转到同一文件中，因为它们与版本 2.0 相关联。</span><span class="sxs-lookup"><span data-stu-id="68f5d-120">For example, redirections from version 2.0.2.222 to 2.0.3.000 and from version 2.0.2.321 to version 2.0.3.000 both go into the same file, because they are associated with version 2.0.</span></span> <span data-ttu-id="68f5d-121">但是，从版本 3.0.0.999 到版本 4.0.0.000 的重定向则转入版本 3.0.999 的文件。</span><span class="sxs-lookup"><span data-stu-id="68f5d-121">However, a redirection from version 3.0.0.999 to version 4.0.0.000 goes into the file for version 3.0.999.</span></span> <span data-ttu-id="68f5d-122">每个主要版本的 .NET Framework 都具有其自己的发布服务器策略文件。</span><span class="sxs-lookup"><span data-stu-id="68f5d-122">Each major version of the .NET Framework has its own publisher policy file.</span></span>

 <span data-ttu-id="68f5d-123">如果存在某一程序集的发布服务器策略文件，则在检查过该程序集的清单和应用配置文件后，运行时将检查该文件。</span><span class="sxs-lookup"><span data-stu-id="68f5d-123">If a publisher policy file exists for an assembly, the runtime checks this file after checking the assembly's manifest and app configuration file.</span></span> <span data-ttu-id="68f5d-124">仅当新的程序集与被重定向的程序集向后兼容时，供应商才会使用发布服务器策略文件。</span><span class="sxs-lookup"><span data-stu-id="68f5d-124">Vendors should use publisher policy files only when the new assembly is backward compatible with the assembly being redirected.</span></span>

 <span data-ttu-id="68f5d-125">你通过在应用配置文件指定设置，跳过应用的发布服务器策略，如 [跳过发布者策略部分](#bypass_PP)中所述。</span><span class="sxs-lookup"><span data-stu-id="68f5d-125">You can bypass publisher policy for your app by specifying settings in the app configuration file, as discussed in the [Bypassing publisher policy section](#bypass_PP).</span></span>

<a name="BKMK_Redirectingassemblyversionsattheapplevel"></a>
## <a name="redirecting-assembly-versions-at-the-app-level"></a><span data-ttu-id="68f5d-126">在应用级别重定向程序集版本</span><span class="sxs-lookup"><span data-stu-id="68f5d-126">Redirecting assembly versions at the app level</span></span>
 <span data-ttu-id="68f5d-127">通过应用配置文件，有几种不同的技术来更改你的应用绑定行为：你可以手动编辑该文件、可以依赖于自动绑定重定向或可以通过跳过发布服务器策略指定绑定行为。</span><span class="sxs-lookup"><span data-stu-id="68f5d-127">There are a few different techniques for changing the binding behavior for your app through the app configuration file: you can manually edit the file, you can rely on automatic binding redirection, or you can specify binding behavior by bypassing publisher policy.</span></span>

### <a name="manually-editing-the-app-config-file"></a><span data-ttu-id="68f5d-128">手动编辑应用配置文件</span><span class="sxs-lookup"><span data-stu-id="68f5d-128">Manually editing the app config file</span></span>
 <span data-ttu-id="68f5d-129">你可以手动编辑应用配置文件，解决程序集问题。</span><span class="sxs-lookup"><span data-stu-id="68f5d-129">You can manually edit the app configuration file to resolve assembly issues.</span></span> <span data-ttu-id="68f5d-130">例如，供应商可能会发布你的应用使用的较新版本的程序集，而没有提供发布服务器策略，因为他们不保证向后兼容性，你可以通过将程序集绑定信息放置在如下所示的应用配置文件中，定向你的应用，以使用较新的程序集版本。</span><span class="sxs-lookup"><span data-stu-id="68f5d-130">For example, if a vendor might release a newer version of an assembly that your app uses without supplying a publisher policy, because they do not guarantee backward compatibility, you can direct your app to use the newer version of the assembly by putting assembly binding information in your app's configuration file as follows.</span></span>

```xml
<dependentAssembly>
  <assemblyIdentity name="someAssembly"
    publicKeyToken="32ab4ba45e0a69a1"
    culture="en-us" />
  <bindingRedirect oldVersion="7.0.0.0" newVersion="8.0.0.0" />
</dependentAssembly>
```

### <a name="relying-on-automatic-binding-redirection"></a><span data-ttu-id="68f5d-131">依赖于自动绑定重定向</span><span class="sxs-lookup"><span data-stu-id="68f5d-131">Relying on automatic binding redirection</span></span>

<span data-ttu-id="68f5d-132">当您创建桌面应用程序在 Visual Studio 中面向[!INCLUDE[net_v451](../../../includes/net-v451-md.md)]或更高版本，该应用使用自动绑定重定向。</span><span class="sxs-lookup"><span data-stu-id="68f5d-132">When you create a desktop app in Visual Studio that targets the [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] or a later version, the app uses automatic binding redirection.</span></span> <span data-ttu-id="68f5d-133">这意味着如果两个组件引用同一强名称程序集的不同版本，则运行时会自动添加绑定重定向到输出应用配置 (app.config) 文件中的程序集的较新版本。</span><span class="sxs-lookup"><span data-stu-id="68f5d-133">This means that if two components reference different versions of the same strong-named assembly, the runtime automatically adds a binding redirection to the newer version of the assembly in the output app configuration (app.config) file.</span></span> <span data-ttu-id="68f5d-134">此重定向将重写可能会发生的程序集统一。</span><span class="sxs-lookup"><span data-stu-id="68f5d-134">This redirection overrides the assembly unification that might otherwise take place.</span></span> <span data-ttu-id="68f5d-135">不修改源 app.config 文件。</span><span class="sxs-lookup"><span data-stu-id="68f5d-135">The source app.config file is not modified.</span></span> <span data-ttu-id="68f5d-136">例如，假设你的应用直接引用带外 .NET Framework 组件，但使用面向同一组件的较旧版本的第三方库。</span><span class="sxs-lookup"><span data-stu-id="68f5d-136">For example, let's say that your app directly references an out-of-band .NET Framework component but uses a third-party library that targets an older version of the same component.</span></span> <span data-ttu-id="68f5d-137">在编译该应用时，将修改输出应用配置文件以包含绑定重定向到较新版本的组件。</span><span class="sxs-lookup"><span data-stu-id="68f5d-137">When you compile the app, the output app configuration file is modified to contain a binding redirection to the newer version of the component.</span></span> <span data-ttu-id="68f5d-138">如果创建一个 Web 应用，你将收到有关绑定冲突的生成警告，这反过来将为你提供将必要的绑定重定向添加到源 Web 配置文件的选项。</span><span class="sxs-lookup"><span data-stu-id="68f5d-138">If you create a web app, you receive a build warning regarding the binding conflict, which in turn, gives you the option to add the necessary binding redirect to the source web configuration file.</span></span>

<span data-ttu-id="68f5d-139">如果你手动添加绑定重定向到源 app.config 文件中，在编译时，Visual Studio 会尝试将基于你添加绑定重定向的程序集统一。</span><span class="sxs-lookup"><span data-stu-id="68f5d-139">If you manually add binding redirects to the source app.config file, at compile time, Visual Studio tries to unify the assemblies based on the binding redirects you added.</span></span> <span data-ttu-id="68f5d-140">例如，假设你对某一程序集插入以下绑定重定向：</span><span class="sxs-lookup"><span data-stu-id="68f5d-140">For example, let's say you insert the following binding redirect for an assembly:</span></span>

`<bindingRedirect oldVersion="3.0.0.0" newVersion="2.0.0.0" />`

<span data-ttu-id="68f5d-141">如果你的应用中的另一个项目引用了同一程序集的版本 1.0.0.0，则自动绑定重定向将添加以下条目到输出 app.config 文件，以便该应用在此程序集的版本 2.0.0.0 上统一：</span><span class="sxs-lookup"><span data-stu-id="68f5d-141">If another project in your app references version 1.0.0.0 of the same assembly, automatic binding redirection adds the following entry to the output app.config file so that the app is unified on version 2.0.0.0 of this assembly:</span></span>

`<bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />`

<span data-ttu-id="68f5d-142">如果你的应用面向.NET Framework 的较旧版本，则可以启用自动绑定重定向。</span><span class="sxs-lookup"><span data-stu-id="68f5d-142">You can enable automatic binding redirection if your app targets older versions of the .NET Framework.</span></span> <span data-ttu-id="68f5d-143">通过在 app.config 文件中的绑定重定向信息提供任何程序集，或通过关闭绑定重定向功能，可以重写此默认行为。</span><span class="sxs-lookup"><span data-stu-id="68f5d-143">You can override this default behavior by providing binding redirection information in the app.config file for any assembly, or by turning off the binding redirection feature.</span></span> <span data-ttu-id="68f5d-144">有关如何启用或禁用此功能的信息，请参阅[如何：启用和禁用自动绑定重定向](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)。</span><span class="sxs-lookup"><span data-stu-id="68f5d-144">For information about how to turn this feature on or off, see [How to: Enable and Disable Automatic Binding Redirection](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).</span></span>

<a name="bypass_PP"></a>
### <a name="bypassing-publisher-policy"></a><span data-ttu-id="68f5d-145">跳过发布服务器策略</span><span class="sxs-lookup"><span data-stu-id="68f5d-145">Bypassing publisher policy</span></span>
 <span data-ttu-id="68f5d-146">如有必要，你可以在应用配置文件中重写发布服务器策略。</span><span class="sxs-lookup"><span data-stu-id="68f5d-146">You can override publisher policy in the app configuration file if necessary.</span></span> <span data-ttu-id="68f5d-147">例如，声称向后兼容的程序集的新版本也会中断应用。</span><span class="sxs-lookup"><span data-stu-id="68f5d-147">For example, new versions of assemblies that claim to be backward compatible can still break an app.</span></span> <span data-ttu-id="68f5d-148">如果你想要跳过发行者策略，将添加[ \<publisherPolicy >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)元素[ \<dependentAssembly >](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)中的应用程序配置文件，并设置元素**应用**归于**没有**，将覆盖任何以前**是**设置。</span><span class="sxs-lookup"><span data-stu-id="68f5d-148">If you want to bypass publisher policy, add a [\<publisherPolicy>](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element to the [\<dependentAssembly>](../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md) element in the app configuration file, and set the **apply** attribute to **no**, which overrides any previous **yes** settings.</span></span>

 `<publisherPolicy apply="no" />`

 <span data-ttu-id="68f5d-149">跳过发布服务器策略来保持应用为你的用户运行，但要确保将问题报告给程序集供应商。</span><span class="sxs-lookup"><span data-stu-id="68f5d-149">Bypass publisher policy to keep your app running for your users, but make sure you report the problem to the assembly vendor.</span></span> <span data-ttu-id="68f5d-150">如果程序集具有发布服务器策略文件，则供应商应确保该程序集向后兼容并且该客户端可以尽可能多的使用新版本。</span><span class="sxs-lookup"><span data-stu-id="68f5d-150">If an assembly has a publisher policy file, the vendor should make sure that the assembly is backward compatible and that clients can use the new version as much as possible.</span></span>

<a name="BKMK_Redirectingassemblyversionsatthemachinelevel"></a>
## <a name="redirecting-assembly-versions-at-the-machine-level"></a><span data-ttu-id="68f5d-151">在计算机级别重定向程序集版本</span><span class="sxs-lookup"><span data-stu-id="68f5d-151">Redirecting assembly versions at the machine level</span></span>
 <span data-ttu-id="68f5d-152">可能存在极少数情况，当计算机管理员想要计算机上所有的应用都使用程序集的某一特定版本时。</span><span class="sxs-lookup"><span data-stu-id="68f5d-152">There might be rare cases when a machine administrator wants all apps on a computer to use a specific version of an assembly.</span></span> <span data-ttu-id="68f5d-153">例如，管理员可能希望每个应用都使用特定的程序集版本，因为该版本可修复安全漏洞。</span><span class="sxs-lookup"><span data-stu-id="68f5d-153">For example, the administrator might want every app to use a particular assembly version, because that version fixes a security hole.</span></span> <span data-ttu-id="68f5d-154">如果某个程序集在计算机配置文件中进行重定向，则该计算机上的所有使用旧版本的应用都将被定向为使用新版本。</span><span class="sxs-lookup"><span data-stu-id="68f5d-154">If an assembly is redirected in the machine's configuration file, all apps on that machine that use the old version will be directed to use the new version.</span></span> <span data-ttu-id="68f5d-155">计算机配置文件将重写应用配置文件和发布服务器策略文件。</span><span class="sxs-lookup"><span data-stu-id="68f5d-155">The machine configuration file overrides the app configuration file and the publisher policy file.</span></span> <span data-ttu-id="68f5d-156">此文件位于 %*runtime install path*%\Config 目录中。</span><span class="sxs-lookup"><span data-stu-id="68f5d-156">This file is located in the %*runtime install path*%\Config directory.</span></span> <span data-ttu-id="68f5d-157">通常，.NET Framework 安装在 %drive%\Windows\Microsoft.NET\Framework 目录中。</span><span class="sxs-lookup"><span data-stu-id="68f5d-157">Typically, the .NET Framework is installed in the %drive%\Windows\Microsoft.NET\Framework directory.</span></span>

<a name="BKMK_Specifyingassemblybindinginconfigurationfiles"></a>
## <a name="specifying-assembly-binding-in-configuration-files"></a><span data-ttu-id="68f5d-158">在配置文件中指定程序集绑定</span><span class="sxs-lookup"><span data-stu-id="68f5d-158">Specifying assembly binding in configuration files</span></span>
 <span data-ttu-id="68f5d-159">使用相同的 XML 格式指定绑定重定向，无论它位于应用配置文件、计算机配置文件还是位于发布服务器策略文件中。</span><span class="sxs-lookup"><span data-stu-id="68f5d-159">You use the same XML format to specify binding redirects whether it’s in the app configuration file, the machine configuration file, or the publisher policy file.</span></span> <span data-ttu-id="68f5d-160">若要将一个程序集版本重定向到另一个，请使用[ \<bindingRedirect >](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="68f5d-160">To redirect one assembly version to another, use the [\<bindingRedirect>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md) element.</span></span> <span data-ttu-id="68f5d-161">**oldVersion** 特性可以指定单个程序集版本或一系列版本。</span><span class="sxs-lookup"><span data-stu-id="68f5d-161">The **oldVersion** attribute can specify a single assembly version or a range of versions.</span></span> <span data-ttu-id="68f5d-162">`newVersion` 特性将指定单个版本。</span><span class="sxs-lookup"><span data-stu-id="68f5d-162">The `newVersion` attribute should specify a single version.</span></span>  <span data-ttu-id="68f5d-163">例如， `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` 指定运行时应使用版本 2.0.0.0 而不是 1.1.0.0 和 1.2.0.0 之间的程序集版本。</span><span class="sxs-lookup"><span data-stu-id="68f5d-163">For example, `<bindingRedirect oldVersion="1.1.0.0-1.2.0.0" newVersion="2.0.0.0"/>` specifies that the runtime should use version 2.0.0.0 instead of the assembly versions between 1.1.0.0 and 1.2.0.0.</span></span>

 <span data-ttu-id="68f5d-164">以下代码示例演示了各种绑定重定向方案。</span><span class="sxs-lookup"><span data-stu-id="68f5d-164">The following code example demonstrates a variety of binding redirect scenarios.</span></span> <span data-ttu-id="68f5d-165">该示例对一系列 `myAssembly`的版本指定了一个重定向，并对 `mySecondAssembly`指定了一个单一绑定重定向。</span><span class="sxs-lookup"><span data-stu-id="68f5d-165">The example specifies a redirect for a range of versions for `myAssembly`, and a single binding redirect for `mySecondAssembly`.</span></span> <span data-ttu-id="68f5d-166">该示例还指定发布服务器策略文件不会代替 `myThirdAssembly`的绑定重定向。</span><span class="sxs-lookup"><span data-stu-id="68f5d-166">The example also specifies that publisher policy file will not override the binding redirects for `myThirdAssembly`.</span></span>

 <span data-ttu-id="68f5d-167">若要绑定程序集，必须指定的字符串"urn： 架构-microsoft-com:asm.v1"与**xmlns**属性中[ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)标记。</span><span class="sxs-lookup"><span data-stu-id="68f5d-167">To bind an assembly, you must specify the string "urn:schemas-microsoft-com:asm.v1" with the **xmlns** attribute in the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) tag.</span></span>

```xml
<configuration>
  <runtime>
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
      <dependentAssembly>
        <assemblyIdentity name="myAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
        <!-- Assembly versions can be redirected in app,
          publisher policy, or machine configuration files. -->
        <bindingRedirect oldVersion="1.0.0.0-2.0.0.0" newVersion="3.0.0.0" />
      </dependentAssembly>
  <dependentAssembly>
        <assemblyIdentity name="mySecondAssembly"
          publicKeyToken="32ab4ba45e0a69a1"
          culture="en-us" />
             <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0" />
      </dependentAssembly>
      <dependentAssembly>
      <assemblyIdentity name="myThirdAssembly"
        publicKeyToken="32ab4ba45e0a69a1"
        culture="en-us" />
        <!-- Publisher policy can be set only in the app
          configuration file. -->
        <publisherPolicy apply="no" />
      </dependentAssembly>
    </assemblyBinding>
  </runtime>
</configuration>
```

### <a name="limiting-assembly--bindings-to-a-specific-version"></a><span data-ttu-id="68f5d-168">限制到特定版本的程序集绑定</span><span class="sxs-lookup"><span data-stu-id="68f5d-168">Limiting assembly  bindings to a specific version</span></span>
 <span data-ttu-id="68f5d-169">可以使用**appliesTo**特性，可以在[ \<assemblyBinding >](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)到特定版本的.NET 程序集绑定引用重定向的应用程序配置文件中的元素框架。</span><span class="sxs-lookup"><span data-stu-id="68f5d-169">You can use the **appliesTo** attribute on the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element in an app configuration file to redirect assembly binding references to a specific version of the .NET Framework.</span></span> <span data-ttu-id="68f5d-170">此可选特性用 .NET Framework 版本号来指示其适用的版本。</span><span class="sxs-lookup"><span data-stu-id="68f5d-170">This optional attribute uses a .NET Framework version number to indicate what version it applies to.</span></span> <span data-ttu-id="68f5d-171">如果没有指定 **appliesTo** 特性，[\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) 元素将适用于 .NET Framework 的所有版本。</span><span class="sxs-lookup"><span data-stu-id="68f5d-171">If no **appliesTo** attribute is specified, the [\<assemblyBinding>](../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md) element applies to all versions of the .NET Framework.</span></span>

 <span data-ttu-id="68f5d-172">例如，若要重定向 .NET Framework 3.5 程序集的程序集绑定，应在你的应用配置文件中包括以下 XML 代码。</span><span class="sxs-lookup"><span data-stu-id="68f5d-172">For example, to redirect assembly binding for a .NET Framework 3.5 assembly, you would include the following XML code in your app configuration file.</span></span>

```xml
<runtime>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1"
    appliesTo="v3.5">
    <dependentAssembly>
      <!-- assembly information goes here -->
    </dependentAssembly>
  </assemblyBinding>
</runtime>
```

 <span data-ttu-id="68f5d-173">应按版本顺序输入重定向信息。</span><span class="sxs-lookup"><span data-stu-id="68f5d-173">You should enter redirection information in version order.</span></span> <span data-ttu-id="68f5d-174">例如，先输入 .NET Framework 3.5 程序集的程序集绑定重定向信息，再输入 .NET Framework 4.5 程序集的绑定重定向信息。</span><span class="sxs-lookup"><span data-stu-id="68f5d-174">For example, enter assembly binding redirection information for .NET Framework 3.5 assemblies followed by .NET Framework 4.5 assemblies.</span></span> <span data-ttu-id="68f5d-175">最后，输入任何因不使用 **appliesTo** 特性而适用于所有版本的 .NET Framework 的.NET Framework 程序集重定向的程序集绑定重定向信息。</span><span class="sxs-lookup"><span data-stu-id="68f5d-175">Finally, enter assembly binding redirection information for any .NET Framework assembly redirection that does not use the **appliesTo** attribute and therefore applies to all versions of the .NET Framework.</span></span> <span data-ttu-id="68f5d-176">如果发生重定向冲突，请使用配置文件中的第一个匹配的重定向语句。</span><span class="sxs-lookup"><span data-stu-id="68f5d-176">If there is a conflict in redirection, the first matching redirection statement in the configuration file is used.</span></span>

 <span data-ttu-id="68f5d-177">例如，若要将一个引用重定向到 .NET Framework 3.5 程序集，而将另一个引用重定向到 .NET Framework 4 程序集，则使用以下伪代码中所示的模式。</span><span class="sxs-lookup"><span data-stu-id="68f5d-177">For example, to redirect one reference to a .NET Framework 3.5 assembly and another reference to a .NET Framework 4 assembly, use the pattern shown in the following pseudocode.</span></span>

```xml
<assemblyBinding xmlns="..." appliesTo="v3.5 ">
  <!--.NET Framework version 3.5 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="..." appliesTo="v4.0.30319">
  <!--.NET Framework version 4.0 redirects here -->
</assemblyBinding>

<assemblyBinding xmlns="...">
  <!-- redirects meant for all versions of the runtime -->
</assemblyBinding>
```

## <a name="see-also"></a><span data-ttu-id="68f5d-178">请参阅</span><span class="sxs-lookup"><span data-stu-id="68f5d-178">See also</span></span>

- [<span data-ttu-id="68f5d-179">如何：启用和禁用自动绑定重定向</span><span class="sxs-lookup"><span data-stu-id="68f5d-179">How to: Enable and Disable Automatic Binding Redirection</span></span>](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
- [<span data-ttu-id="68f5d-180">\<bindingRedirect > 元素</span><span class="sxs-lookup"><span data-stu-id="68f5d-180">\<bindingRedirect> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)
- [<span data-ttu-id="68f5d-181">程序集绑定重定向安全权限</span><span class="sxs-lookup"><span data-stu-id="68f5d-181">Assembly Binding Redirection Security Permission</span></span>](../../../docs/framework/configure-apps/assembly-binding-redirection-security-permission.md)
- <span data-ttu-id="68f5d-182">[Assemblies in the Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)（公共语言运行时中的程序集）</span><span class="sxs-lookup"><span data-stu-id="68f5d-182">[Assemblies in the Common Language Runtime](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)</span></span>
- [<span data-ttu-id="68f5d-183">使用程序集编程</span><span class="sxs-lookup"><span data-stu-id="68f5d-183">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="68f5d-184">运行时如何定位程序集</span><span class="sxs-lookup"><span data-stu-id="68f5d-184">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="68f5d-185">配置应用程序</span><span class="sxs-lookup"><span data-stu-id="68f5d-185">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)
- [<span data-ttu-id="68f5d-186">运行时设置架构</span><span class="sxs-lookup"><span data-stu-id="68f5d-186">Runtime Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="68f5d-187">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="68f5d-187">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="68f5d-188">如何：创建发布服务器策略</span><span class="sxs-lookup"><span data-stu-id="68f5d-188">How to: Create a Publisher Policy</span></span>](../../../docs/framework/configure-apps/how-to-create-a-publisher-policy.md)
