---
title: 使用托管调试助手诊断错误
ms.date: 08/14/2018
f1_keywords:
- EHMDA
helpviewer_keywords:
- run-time error debugging
- managed code, run-time debugging
- resource debugging
- registry, MDAs
- common language runtime, debugging
- MDAs (managed debugging assistants)
- configuration files [.NET Framework], debugging runtime events
- messages, managed debugging assistants
- application configuration files, managed debugging assistants
- debugging [.NET Framework], managed debugging assistants
- environment variables, MDAs
- access violation debugging [.NET Framework]
- diagnostics, managed debugging assistants
- unmanaged code, run-time debugging
- default debug output stream
- memory, debugging
- app.config files, managed debugging assistants
- managed debugging assistants (MDAs)
- debugging [.NET Framework], run-time errors
- trapping events
- runtime, error debugging
- disabling MDAs
- output, managed debugging assistants
- errors [.NET Framework], managed debugging assistants
ms.assetid: 76994ee6-9fa9-4059-b813-26578d24427c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b745fa6a78ab2a7ab0b3a94c9921883d3c56c1b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874611"
---
# <a name="diagnose-errors-with-managed-debugging-assistants"></a><span data-ttu-id="58dc4-102">诊断错误使用托管调试助手</span><span class="sxs-lookup"><span data-stu-id="58dc4-102">Diagnose Errors with Managed Debugging Assistants</span></span>

<span data-ttu-id="58dc4-103">托管调试助手 (MDA) 是调试辅助程序，它与公共语言运行时 (CLR) 一起工作以提供关于运行时状态的信息。</span><span class="sxs-lookup"><span data-stu-id="58dc4-103">Managed debugging assistants (MDAs) are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span> <span data-ttu-id="58dc4-104">这些助手可生成关于你无法通过其他方式捕获的运行时事件的信息性消息。</span><span class="sxs-lookup"><span data-stu-id="58dc4-104">The assistants generate informational messages about runtime events that you cannot otherwise trap.</span></span> <span data-ttu-id="58dc4-105">可以使用 MDA 隔离在托管代码和非托管代码之间转换时发生的、难以发现的应用程序 Bug。</span><span class="sxs-lookup"><span data-stu-id="58dc4-105">You can use MDAs to isolate hard-to-find application bugs that occur when transitioning between managed and unmanaged code.</span></span>

<span data-ttu-id="58dc4-106">你可以[启用或禁用](#enable-and-disable-mdas)通过添加到 Windows 注册表项或通过设置环境变量的所有 Mda。</span><span class="sxs-lookup"><span data-stu-id="58dc4-106">You can [enable or disable](#enable-and-disable-mdas) all MDAs by adding a key to the Windows registry or by setting an environment variable.</span></span> <span data-ttu-id="58dc4-107">可使用应用程序配置设置来启用特定的 MDA。</span><span class="sxs-lookup"><span data-stu-id="58dc4-107">You can enable specific MDAs by using application configuration settings.</span></span> <span data-ttu-id="58dc4-108">可以在应用程序的配置文件中为某些单独的 MDA 设置其他配置设置。</span><span class="sxs-lookup"><span data-stu-id="58dc4-108">You can set additional configuration settings for some individual MDAs in the application's configuration file.</span></span> <span data-ttu-id="58dc4-109">由于将在加载运行时后分析这些配置文件，因此必须在托管应用程序启动之前启用 MDA。</span><span class="sxs-lookup"><span data-stu-id="58dc4-109">Because these configuration files are parsed when the runtime is loaded, you must enable the MDA before the managed application starts.</span></span> <span data-ttu-id="58dc4-110">不能为已经启动的应用程序启用 MDA。</span><span class="sxs-lookup"><span data-stu-id="58dc4-110">You cannot enable it for applications that have already started.</span></span>

<span data-ttu-id="58dc4-111">下表列出了使用.NET Framework 附带的 Mda:</span><span class="sxs-lookup"><span data-stu-id="58dc4-111">The following table lists the MDAs that ship with the .NET Framework:</span></span>

|||
|-|-|
|[<span data-ttu-id="58dc4-112">asynchronousThreadAbort</span><span class="sxs-lookup"><span data-stu-id="58dc4-112">asynchronousThreadAbort</span></span>](../../../docs/framework/debug-trace-profile/asynchronousthreadabort-mda.md)|[<span data-ttu-id="58dc4-113">bindingFailure</span><span class="sxs-lookup"><span data-stu-id="58dc4-113">bindingFailure</span></span>](../../../docs/framework/debug-trace-profile/bindingfailure-mda.md)|
|[<span data-ttu-id="58dc4-114">callbackOnCollectedDelegate</span><span class="sxs-lookup"><span data-stu-id="58dc4-114">callbackOnCollectedDelegate</span></span>](../../../docs/framework/debug-trace-profile/callbackoncollecteddelegate-mda.md)|[<span data-ttu-id="58dc4-115">contextSwitchDeadlock</span><span class="sxs-lookup"><span data-stu-id="58dc4-115">contextSwitchDeadlock</span></span>](../../../docs/framework/debug-trace-profile/contextswitchdeadlock-mda.md)|
|[<span data-ttu-id="58dc4-116">dangerousThreadingAPI</span><span class="sxs-lookup"><span data-stu-id="58dc4-116">dangerousThreadingAPI</span></span>](../../../docs/framework/debug-trace-profile/dangerousthreadingapi-mda.md)|[<span data-ttu-id="58dc4-117">dateTimeInvalidLocalFormat</span><span class="sxs-lookup"><span data-stu-id="58dc4-117">dateTimeInvalidLocalFormat</span></span>](../../../docs/framework/debug-trace-profile/datetimeinvalidlocalformat-mda.md)|
|[<span data-ttu-id="58dc4-118">dirtyCastAndCallOnInterface</span><span class="sxs-lookup"><span data-stu-id="58dc4-118">dirtyCastAndCallOnInterface</span></span>](../../../docs/framework/debug-trace-profile/dirtycastandcalloninterface-mda.md)|[<span data-ttu-id="58dc4-119">disconnectedContext</span><span class="sxs-lookup"><span data-stu-id="58dc4-119">disconnectedContext</span></span>](../../../docs/framework/debug-trace-profile/disconnectedcontext-mda.md)|
|[<span data-ttu-id="58dc4-120">dllMainReturnsFalse</span><span class="sxs-lookup"><span data-stu-id="58dc4-120">dllMainReturnsFalse</span></span>](../../../docs/framework/debug-trace-profile/dllmainreturnsfalse-mda.md)|[<span data-ttu-id="58dc4-121">exceptionSwallowedOnCallFromCom</span><span class="sxs-lookup"><span data-stu-id="58dc4-121">exceptionSwallowedOnCallFromCom</span></span>](../../../docs/framework/debug-trace-profile/exceptionswallowedoncallfromcom-mda.md)|
|[<span data-ttu-id="58dc4-122">failedQI</span><span class="sxs-lookup"><span data-stu-id="58dc4-122">failedQI</span></span>](../../../docs/framework/debug-trace-profile/failedqi-mda.md)|[<span data-ttu-id="58dc4-123">fatalExecutionEngineError</span><span class="sxs-lookup"><span data-stu-id="58dc4-123">fatalExecutionEngineError</span></span>](../../../docs/framework/debug-trace-profile/fatalexecutionengineerror-mda.md)|
|[<span data-ttu-id="58dc4-124">gcManagedToUnmanaged</span><span class="sxs-lookup"><span data-stu-id="58dc4-124">gcManagedToUnmanaged</span></span>](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)|[<span data-ttu-id="58dc4-125">gcUnmanagedToManaged</span><span class="sxs-lookup"><span data-stu-id="58dc4-125">gcUnmanagedToManaged</span></span>](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)|
|[<span data-ttu-id="58dc4-126">illegalPrepareConstrainedRegion</span><span class="sxs-lookup"><span data-stu-id="58dc4-126">illegalPrepareConstrainedRegion</span></span>](../../../docs/framework/debug-trace-profile/illegalprepareconstrainedregion-mda.md)|[<span data-ttu-id="58dc4-127">invalidApartmentStateChange</span><span class="sxs-lookup"><span data-stu-id="58dc4-127">invalidApartmentStateChange</span></span>](../../../docs/framework/debug-trace-profile/invalidapartmentstatechange-mda.md)|
|[<span data-ttu-id="58dc4-128">invalidCERCall</span><span class="sxs-lookup"><span data-stu-id="58dc4-128">invalidCERCall</span></span>](../../../docs/framework/debug-trace-profile/invalidcercall-mda.md)|[<span data-ttu-id="58dc4-129">invalidFunctionPointerInDelegate</span><span class="sxs-lookup"><span data-stu-id="58dc4-129">invalidFunctionPointerInDelegate</span></span>](../../../docs/framework/debug-trace-profile/invalidfunctionpointerindelegate-mda.md)|
|[<span data-ttu-id="58dc4-130">invalidGCHandleCookie</span><span class="sxs-lookup"><span data-stu-id="58dc4-130">invalidGCHandleCookie</span></span>](../../../docs/framework/debug-trace-profile/invalidgchandlecookie-mda.md)|[<span data-ttu-id="58dc4-131">invalidIUnknown</span><span class="sxs-lookup"><span data-stu-id="58dc4-131">invalidIUnknown</span></span>](../../../docs/framework/debug-trace-profile/invalidiunknown-mda.md)|
|[<span data-ttu-id="58dc4-132">invalidMemberDeclaration</span><span class="sxs-lookup"><span data-stu-id="58dc4-132">invalidMemberDeclaration</span></span>](../../../docs/framework/debug-trace-profile/invalidmemberdeclaration-mda.md)|[<span data-ttu-id="58dc4-133">invalidOverlappedToPinvoke</span><span class="sxs-lookup"><span data-stu-id="58dc4-133">invalidOverlappedToPinvoke</span></span>](../../../docs/framework/debug-trace-profile/invalidoverlappedtopinvoke-mda.md)|
|[<span data-ttu-id="58dc4-134">invalidVariant</span><span class="sxs-lookup"><span data-stu-id="58dc4-134">invalidVariant</span></span>](../../../docs/framework/debug-trace-profile/invalidvariant-mda.md)|[<span data-ttu-id="58dc4-135">jitCompilationStart</span><span class="sxs-lookup"><span data-stu-id="58dc4-135">jitCompilationStart</span></span>](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md)|
|[<span data-ttu-id="58dc4-136">loaderLock</span><span class="sxs-lookup"><span data-stu-id="58dc4-136">loaderLock</span></span>](../../../docs/framework/debug-trace-profile/loaderlock-mda.md)|[<span data-ttu-id="58dc4-137">loadFromContext</span><span class="sxs-lookup"><span data-stu-id="58dc4-137">loadFromContext</span></span>](../../../docs/framework/debug-trace-profile/loadfromcontext-mda.md)|
|[<span data-ttu-id="58dc4-138">marshalCleanupError</span><span class="sxs-lookup"><span data-stu-id="58dc4-138">marshalCleanupError</span></span>](../../../docs/framework/debug-trace-profile/marshalcleanuperror-mda.md)|[<span data-ttu-id="58dc4-139">marshaling</span><span class="sxs-lookup"><span data-stu-id="58dc4-139">marshaling</span></span>](../../../docs/framework/debug-trace-profile/marshaling-mda.md)|
|[<span data-ttu-id="58dc4-140">memberInfoCacheCreation</span><span class="sxs-lookup"><span data-stu-id="58dc4-140">memberInfoCacheCreation</span></span>](../../../docs/framework/debug-trace-profile/memberinfocachecreation-mda.md)|[<span data-ttu-id="58dc4-141">moduloObjectHashcode</span><span class="sxs-lookup"><span data-stu-id="58dc4-141">moduloObjectHashcode</span></span>](../../../docs/framework/debug-trace-profile/moduloobjecthashcode-mda.md)|
|[<span data-ttu-id="58dc4-142">nonComVisibleBaseClass</span><span class="sxs-lookup"><span data-stu-id="58dc4-142">nonComVisibleBaseClass</span></span>](../../../docs/framework/debug-trace-profile/noncomvisiblebaseclass-mda.md)|[<span data-ttu-id="58dc4-143">notMarshalable</span><span class="sxs-lookup"><span data-stu-id="58dc4-143">notMarshalable</span></span>](../../../docs/framework/debug-trace-profile/notmarshalable-mda.md)|
|[<span data-ttu-id="58dc4-144">openGenericCERCall</span><span class="sxs-lookup"><span data-stu-id="58dc4-144">openGenericCERCall</span></span>](../../../docs/framework/debug-trace-profile/opengenericcercall-mda.md)|[<span data-ttu-id="58dc4-145">overlappedFreeError</span><span class="sxs-lookup"><span data-stu-id="58dc4-145">overlappedFreeError</span></span>](../../../docs/framework/debug-trace-profile/overlappedfreeerror-mda.md)|
|[<span data-ttu-id="58dc4-146">pInvokeLog</span><span class="sxs-lookup"><span data-stu-id="58dc4-146">pInvokeLog</span></span>](../../../docs/framework/debug-trace-profile/pinvokelog-mda.md)|[<span data-ttu-id="58dc4-147">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="58dc4-147">pInvokeStackImbalance</span></span>](../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)|
|[<span data-ttu-id="58dc4-148">raceOnRCWCleanup</span><span class="sxs-lookup"><span data-stu-id="58dc4-148">raceOnRCWCleanup</span></span>](../../../docs/framework/debug-trace-profile/raceonrcwcleanup-mda.md)|[<span data-ttu-id="58dc4-149">reentrancy</span><span class="sxs-lookup"><span data-stu-id="58dc4-149">reentrancy</span></span>](../../../docs/framework/debug-trace-profile/reentrancy-mda.md)|
|[<span data-ttu-id="58dc4-150">releaseHandleFailed</span><span class="sxs-lookup"><span data-stu-id="58dc4-150">releaseHandleFailed</span></span>](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md)|[<span data-ttu-id="58dc4-151">reportAvOnComRelease</span><span class="sxs-lookup"><span data-stu-id="58dc4-151">reportAvOnComRelease</span></span>](../../../docs/framework/debug-trace-profile/reportavoncomrelease-mda.md)|
|[<span data-ttu-id="58dc4-152">streamWriterBufferedDataLost</span><span class="sxs-lookup"><span data-stu-id="58dc4-152">streamWriterBufferedDataLost</span></span>](../../../docs/framework/debug-trace-profile/streamwriterbuffereddatalost-mda.md)|[<span data-ttu-id="58dc4-153">virtualCERCall</span><span class="sxs-lookup"><span data-stu-id="58dc4-153">virtualCERCall</span></span>](../../../docs/framework/debug-trace-profile/virtualcercall-mda.md)|

<span data-ttu-id="58dc4-154">默认情况下，.NET Framework 会为所有托管调试器激活 MDA 的子集。</span><span class="sxs-lookup"><span data-stu-id="58dc4-154">By default, the .NET Framework activates a subset of MDAs for all managed debuggers.</span></span> <span data-ttu-id="58dc4-155">可以查看通过选择 Visual Studio 中设置的默认**Windows** > **异常设置**上**调试**菜单，然后展开**托管调试助手**列表。</span><span class="sxs-lookup"><span data-stu-id="58dc4-155">You can view the default set in Visual Studio by choosing **Windows** > **Exception Settings** on the **Debug** menu, and then expanding the **Managed Debugging Assistants** list.</span></span>

![在 Visual Studio 中的异常设置窗口](media/diagnosing-errors-with-managed-debugging-assistants/exception-settings-mdas.png)

## <a name="enable-and-disable-mdas"></a><span data-ttu-id="58dc4-157">启用和禁用 Mda</span><span class="sxs-lookup"><span data-stu-id="58dc4-157">Enable and Disable MDAs</span></span>

<span data-ttu-id="58dc4-158">可使用注册表项、环境变量和应用程序配置设置，启用和禁用 MDA。</span><span class="sxs-lookup"><span data-stu-id="58dc4-158">You can enable and disable MDAs by using a registry key, an environment variable, and application configuration settings.</span></span> <span data-ttu-id="58dc4-159">若要使用应用程序配置设置，必须启用注册表项或环境变量。</span><span class="sxs-lookup"><span data-stu-id="58dc4-159">You must enable either the registry key or the environment variable to use the application configuration settings.</span></span>

> [!TIP]
> <span data-ttu-id="58dc4-160">而不是禁用 Mda，可防止 Visual Studio 时收到 MDA 通知时显示 MDA 对话框。</span><span class="sxs-lookup"><span data-stu-id="58dc4-160">Instead of disabling MDAs, you can prevent Visual Studio from displaying the MDA dialog box whenever an MDA notification is received.</span></span> <span data-ttu-id="58dc4-161">为此，请选择**Windows** > **异常设置**上**调试**菜单中，展开**托管调试助手**列表，然后选择或清除**中断时引发**为单个 MDA 的复选框。</span><span class="sxs-lookup"><span data-stu-id="58dc4-161">To do that, choose **Windows** > **Exception Settings** on the **Debug** menu, expand the **Managed Debugging Assistants** list, and then select or clear the **Break When Thrown** check box for the individual MDA.</span></span>

### <a name="registry-key"></a><span data-ttu-id="58dc4-162">注册表项</span><span class="sxs-lookup"><span data-stu-id="58dc4-162">Registry Key</span></span>

<span data-ttu-id="58dc4-163">若要启用 Mda，请添加**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\。NETFramework\MDA** Windows 注册表中的子项 （类型为 REG_SZ，值为 1）。</span><span class="sxs-lookup"><span data-stu-id="58dc4-163">To enable MDAs, add the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\MDA** subkey (type REG_SZ, value 1) in the Windows registry.</span></span> <span data-ttu-id="58dc4-164">将下面的示例复制到一个名为文本文件*MDAEnable.reg*。打开 Windows 注册表编辑器 (RegEdit.exe)，并从**文件**菜单中，选择**导入**。</span><span class="sxs-lookup"><span data-stu-id="58dc4-164">Copy the following example into a text file named *MDAEnable.reg*. Open the Windows Registry Editor (RegEdit.exe), and from the **File** menu choose **Import**.</span></span> <span data-ttu-id="58dc4-165">选择*MDAEnable.reg*文件以在该计算机上启用 Mda。</span><span class="sxs-lookup"><span data-stu-id="58dc4-165">Select the *MDAEnable.reg* file to enable MDAs on that computer.</span></span> <span data-ttu-id="58dc4-166">将子项设置为字符串值**1** (不是 DWORD 值的**1**) 使读取 MDA 设置从*ApplicationName.suffix*。 文件。</span><span class="sxs-lookup"><span data-stu-id="58dc4-166">Setting the subkey to string value of **1** (not DWORD value of **1**) enables the reading of MDA settings from the *ApplicationName.suffix*.mda.config file.</span></span> <span data-ttu-id="58dc4-167">例如，Notepad 的 MDA 配置文件将被命名为 notepad.exe.mda.config。</span><span class="sxs-lookup"><span data-stu-id="58dc4-167">For example, the MDA configuration file for Notepad would be named notepad.exe.mda.config.</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="58dc4-168">如果计算机在 64 位操作系统上运行 32 位应用程序，应按下方所示设置 MDA 密钥：</span><span class="sxs-lookup"><span data-stu-id="58dc4-168">If the computer is running a 32-bit application on a 64-bit operating system, then the MDA key should be set like the following:</span></span>

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework]
"MDA"="1"
```

<span data-ttu-id="58dc4-169">请参阅[特定于应用程序的配置设置](#application-specific-configuration-settings)有关详细信息。</span><span class="sxs-lookup"><span data-stu-id="58dc4-169">See [Application-Specific Configuration Settings](#application-specific-configuration-settings) for more information.</span></span> <span data-ttu-id="58dc4-170">可以使用 COMPLUS_MDA 环境变量重写注册表设置。</span><span class="sxs-lookup"><span data-stu-id="58dc4-170">The registry setting can be overridden by the COMPLUS_MDA environment variable.</span></span> <span data-ttu-id="58dc4-171">请参阅[环境变量](#environment-variable)有关详细信息。</span><span class="sxs-lookup"><span data-stu-id="58dc4-171">See [Environment Variable](#environment-variable) for more information.</span></span>

<span data-ttu-id="58dc4-172">若要禁用 Mda，请将 MDA 子项设置为**0** （零） 使用 Windows 注册表编辑器。</span><span class="sxs-lookup"><span data-stu-id="58dc4-172">To disable MDAs, set the MDA subkey to **0** (zero) using the Windows Registry Editor.</span></span>

<span data-ttu-id="58dc4-173">默认情况下，即使未添加该注册表项，有些 MDA 也会在运行附加到调试器的应用程序时启用。</span><span class="sxs-lookup"><span data-stu-id="58dc4-173">By default, some MDAs are enabled when you run an application that is attached to a debugger, even without adding the registry key.</span></span> <span data-ttu-id="58dc4-174">您可以通过运行禁用这些助手*MDADisable.reg*文件中，如在本部分中前面所述。</span><span class="sxs-lookup"><span data-stu-id="58dc4-174">You can disable these assistants by running the *MDADisable.reg* file as described earlier in this section.</span></span>

### <a name="environment-variable"></a><span data-ttu-id="58dc4-175">环境变量</span><span class="sxs-lookup"><span data-stu-id="58dc4-175">Environment Variable</span></span>

<span data-ttu-id="58dc4-176">还可以通过环境变量 COMPLUS_MDA 控制 MDA 激活，此变量可重写注册表项。</span><span class="sxs-lookup"><span data-stu-id="58dc4-176">MDA activation can also controlled by the environment variable COMPLUS_MDA, which overrides the registry key.</span></span> <span data-ttu-id="58dc4-177">COMPLUS_MDA 字符串是一个区分大小写、以分号分隔的 MDA 名称列表或其他特殊控制字符串。</span><span class="sxs-lookup"><span data-stu-id="58dc4-177">The COMPLUS_MDA string is a case-insensitive, semicolon-delimited list of MDA names or other special control strings.</span></span> <span data-ttu-id="58dc4-178">在托管或非托管调试器下启动将默认启用一组 MDA。</span><span class="sxs-lookup"><span data-stu-id="58dc4-178">Starting under a managed or unmanaged debugger enables a set of MDAs by default.</span></span> <span data-ttu-id="58dc4-179">这是通过在环境变量或注册表项的值前面，隐式附加默认在调试器下启用的、以分号分隔的 MDA 的列表来实现的。</span><span class="sxs-lookup"><span data-stu-id="58dc4-179">This is done by implicitly prepending the semicolon-delimited list of MDAs enabled by default under debuggers to the value of the environment variable or registry key.</span></span> <span data-ttu-id="58dc4-180">特殊控制字符串如下所示：</span><span class="sxs-lookup"><span data-stu-id="58dc4-180">The special control strings are the following:</span></span>

- <span data-ttu-id="58dc4-181">`0` - 停用所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="58dc4-181">`0` - Deactivates all MDAs.</span></span>

- <span data-ttu-id="58dc4-182">`1` - 从 ApplicationName.mda.configg 读取 MDA 设置。</span><span class="sxs-lookup"><span data-stu-id="58dc4-182">`1` - Reads MDA settings from *ApplicationName*.mda.config.</span></span>

- <span data-ttu-id="58dc4-183">`managedDebugger` - 显式激活在调试器下启动托管可执行文件时隐式激活的所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="58dc4-183">`managedDebugger` - Explicitly activates all MDAs that are implicitly activated when a managed executable is started under a debugger.</span></span>

- <span data-ttu-id="58dc4-184">`unmanagedDebugger` - 显式激活在调试器下启动非托管可执行文件时隐式激活的所有 MDA。</span><span class="sxs-lookup"><span data-stu-id="58dc4-184">`unmanagedDebugger` - Explicitly activates all MDAs that are implicitly activated when an unmanaged executable is started under a debugger.</span></span>

<span data-ttu-id="58dc4-185">如果存在冲突的设置，则最新的设置将重写先前的设置：</span><span class="sxs-lookup"><span data-stu-id="58dc4-185">If there are conflicting settings, the most recent settings override previous settings:</span></span>

- <span data-ttu-id="58dc4-186">`COMPLUS_MDA=0` 禁用所有 MDA，包括那些在调试器下隐式启用的 MDA。</span><span class="sxs-lookup"><span data-stu-id="58dc4-186">`COMPLUS_MDA=0` disables all MDAs, including those implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="58dc4-187">除了调试器下隐式启用的所有 MDA，`COMPLUS_MDA=gcUnmanagedToManaged` 还启用 `gcUnmanagedToManaged`。</span><span class="sxs-lookup"><span data-stu-id="58dc4-187">`COMPLUS_MDA=gcUnmanagedToManaged` enables `gcUnmanagedToManaged` in addition to any MDAs that are implicitly enabled under a debugger.</span></span>

- <span data-ttu-id="58dc4-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` 启用 `gcUnmanagedToManaged`，但是禁用将在调试器下隐式启用的 MDA。</span><span class="sxs-lookup"><span data-stu-id="58dc4-188">`COMPLUS_MDA=0;gcUnmanagedToManaged` enables `gcUnmanagedToManaged` but disables MDAs that would otherwise be implicitly enabled under a debugger.</span></span>

### <a name="application-specific-configuration-settings"></a><span data-ttu-id="58dc4-189">特定于应用程序的配置设置</span><span class="sxs-lookup"><span data-stu-id="58dc4-189">Application-Specific Configuration Settings</span></span>

<span data-ttu-id="58dc4-190">可以在应用程序的 MDA 配置文件中单独地启用、禁用和配置某些助手。</span><span class="sxs-lookup"><span data-stu-id="58dc4-190">You can enable, disable, and configure some assistants individually in the MDA configuration file for the application.</span></span> <span data-ttu-id="58dc4-191">若要使用用于配置 MDA 的应用程序配置文件，必须设置 MDA 注册表项或 COMPLUS_MDA 环境变量。</span><span class="sxs-lookup"><span data-stu-id="58dc4-191">To enable the use of an application configuration file for configuring MDAs, either the MDA registry key or the COMPLUS_MDA environment variable must be set.</span></span> <span data-ttu-id="58dc4-192">应用程序配置文件通常与应用程序的可执行文件 (.exe) 位于同一目录中。</span><span class="sxs-lookup"><span data-stu-id="58dc4-192">The application configuration file is typically located in the same directory as the application's executable (.exe) file.</span></span> <span data-ttu-id="58dc4-193">文件名采用“ApplicationName.mda.config”形式；例如，notepad.exe.mda.config。在应用程序配置文件中启用的助手可能包含专门设计用于控制该助手的行为的特性或元素。</span><span class="sxs-lookup"><span data-stu-id="58dc4-193">The file name takes the form *ApplicationName*.mda.config; for example, notepad.exe.mda.config. Assistants that are enabled in the application configuration file may have attributes or elements specifically designed to control that assistant's behavior.</span></span>

<span data-ttu-id="58dc4-194">下面的示例演示如何启用和配置[封送处理](../../../docs/framework/debug-trace-profile/marshaling-mda.md):</span><span class="sxs-lookup"><span data-stu-id="58dc4-194">The following example shows how to enable and configure the [marshaling](../../../docs/framework/debug-trace-profile/marshaling-mda.md):</span></span>

```xml
<mdaConfig>
  <assistants>
    <marshaling>
      <methodFilter>
        <match name="*"/>
      </methodFilter>
      <fieldFilter>
        <match name="*"/>
      </fieldFilter>
    </marshaling>
  </assistants>
</mdaConfig>
```

<span data-ttu-id="58dc4-195">对于应用程序中每个托管到非托管的转换，`Marshaling` MDA 会发出有关正封送到非托管类型的托管类型信息。</span><span class="sxs-lookup"><span data-stu-id="58dc4-195">The `Marshaling` MDA emits information about the managed type that is being marshaled to an unmanaged type for each managed-to-unmanaged transition in the application.</span></span> <span data-ttu-id="58dc4-196">`Marshaling` MDA 还可以筛选的方法的名称，并按提供的结构字段**methodFilter**并**fieldFilter**子元素分别。</span><span class="sxs-lookup"><span data-stu-id="58dc4-196">The `Marshaling` MDA can also filter the names of the method and structure fields supplied in the **methodFilter** and **fieldFilter** child elements, respectively.</span></span>

<span data-ttu-id="58dc4-197">下面的示例演示如何使用其默认设置启用多个 Mda:</span><span class="sxs-lookup"><span data-stu-id="58dc4-197">The following example shows how to enable multiple MDAs by using their default settings:</span></span>

```xml
<mdaConfig>
  <assistants>
    <illegalPrepareConstrainedRegion />
    <invalidCERCall />
    <openGenericCERCall />
    <virtualCERCall />
  </assistants>
</mdaConfig>
```

> [!IMPORTANT]
> <span data-ttu-id="58dc4-198">若在配置文件中指定了多个助手，则必须按字母顺序列出这些助手。</span><span class="sxs-lookup"><span data-stu-id="58dc4-198">When you specify more than one assistant in a configuration file, you must list them in alphabetical order.</span></span> <span data-ttu-id="58dc4-199">例如，若要同时启用 `virtualCERCall` 和 `invalidCERCall` MDA，则必须先添加 `<invalidCERCall />` 项，再添加 `<virtualCERCall />` 项。</span><span class="sxs-lookup"><span data-stu-id="58dc4-199">For example, if you want to enable both the `virtualCERCall` and the `invalidCERCall` MDAs, you must add the `<invalidCERCall />` entry before the `<virtualCERCall />` entry.</span></span> <span data-ttu-id="58dc4-200">如果这些项未按字母顺序排列，将显示未处理的无效配置文件异常消息。</span><span class="sxs-lookup"><span data-stu-id="58dc4-200">If the entries are not in alphabetical order, an unhandled invalid configuration file exception message is displayed.</span></span>

## <a name="mda-exceptions"></a><span data-ttu-id="58dc4-201">MDA 异常</span><span class="sxs-lookup"><span data-stu-id="58dc4-201">MDA exceptions</span></span>

<span data-ttu-id="58dc4-202">启用 MDA 后，它处于活动状态甚至当你的代码是不在调试器下执行。</span><span class="sxs-lookup"><span data-stu-id="58dc4-202">When an MDA is enabled, it's active even when your code is not executing under a debugger.</span></span> <span data-ttu-id="58dc4-203">如果在调试器不存在时引发 MDA 事件，尽管这不是未经处理的异常，事件消息也会出现在未经处理的异常对话框中。</span><span class="sxs-lookup"><span data-stu-id="58dc4-203">If an MDA event is raised when a debugger is not present, the event message is presented in an unhandled exception dialog box, although it is not an unhandled exception.</span></span> <span data-ttu-id="58dc4-204">若要避免出现该对话框，请在代码未在调试环境中执行时，移除 MDA 启用设置。</span><span class="sxs-lookup"><span data-stu-id="58dc4-204">To avoid the dialog box, remove the MDA-enabling settings when your code is not executing in a debugging environment.</span></span>

<span data-ttu-id="58dc4-205">当你的代码执行在 Visual Studio 集成的开发环境 (IDE) 中时，可以避免针对特定 MDA 事件出现的异常对话框。</span><span class="sxs-lookup"><span data-stu-id="58dc4-205">When your code executes in the Visual Studio integrated development environment (IDE), you can avoid the exception dialog box that appears for specific MDA events.</span></span> <span data-ttu-id="58dc4-206">为此，请在**调试**菜单中，选择**Windows** > **异常设置**。</span><span class="sxs-lookup"><span data-stu-id="58dc4-206">To do that, on the **Debug** menu, choose **Windows** > **Exception Settings**.</span></span> <span data-ttu-id="58dc4-207">在中**异常设置**窗口中，展开**托管调试助手**列表中，，然后清除**中断时引发**为单个 MDA 的复选框。</span><span class="sxs-lookup"><span data-stu-id="58dc4-207">In the **Exception Settings** window, expand the **Managed Debugging Assistants** list, and then clear the **Break When Thrown** check box for the individual MDA.</span></span> <span data-ttu-id="58dc4-208">此外可以使用此对话框*启用*MDA 异常对话框的显示。</span><span class="sxs-lookup"><span data-stu-id="58dc4-208">You can also use this dialog box to *enable* the display of MDA exception dialog boxes.</span></span>

## <a name="mda-output"></a><span data-ttu-id="58dc4-209">MDA 输出</span><span class="sxs-lookup"><span data-stu-id="58dc4-209">MDA Output</span></span>

<span data-ttu-id="58dc4-210">MDA 输出结果类似于下面的示例，其中显示了从输出`PInvokeStackImbalance`MDA:</span><span class="sxs-lookup"><span data-stu-id="58dc4-210">MDA output is similar to the following example, which shows the output from the `PInvokeStackImbalance` MDA:</span></span>

<span data-ttu-id="58dc4-211">**PInvoke 函数的调用 MDATest ！MDATest.Program::StdCall 具有使堆栈不平衡。这可能是因为托管的 PInvoke 签名与非托管的目标签名不匹配。检查的调用约定和 PInvoke 签名的参数匹配的目标的非托管的签名。**</span><span class="sxs-lookup"><span data-stu-id="58dc4-211">**A call to PInvoke function 'MDATest!MDATest.Program::StdCall' has unbalanced the stack. This is likely because the managed PInvoke signature does not match the unmanaged target signature. Check that the calling convention and parameters of the PInvoke signature match the target unmanaged signature.**</span></span>

## <a name="see-also"></a><span data-ttu-id="58dc4-212">请参阅</span><span class="sxs-lookup"><span data-stu-id="58dc4-212">See also</span></span>

- [<span data-ttu-id="58dc4-213">调试、跟踪和分析</span><span class="sxs-lookup"><span data-stu-id="58dc4-213">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)
