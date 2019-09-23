---
title: Regsvcs.exe（.NET 服务安装工具）
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 032f43aa16dbca0f4ab0477d586e7568230b7381
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044267"
---
# <a name="regsvcsexe-net-services-installation-tool"></a><span data-ttu-id="ed300-102">Regsvcs.exe（.NET 服务安装工具）</span><span class="sxs-lookup"><span data-stu-id="ed300-102">Regsvcs.exe (.NET Services Installation Tool)</span></span>
<span data-ttu-id="ed300-103">.NET 服务安装工具执行下列操作：</span><span class="sxs-lookup"><span data-stu-id="ed300-103">The .NET Services Installation tool performs the following actions:</span></span>  
  
- <span data-ttu-id="ed300-104">加载并注册程序集。</span><span class="sxs-lookup"><span data-stu-id="ed300-104">Loads and registers an assembly.</span></span>  
  
- <span data-ttu-id="ed300-105">生成、注册类型库并将其安装到指定的 COM+ 应用程序中。</span><span class="sxs-lookup"><span data-stu-id="ed300-105">Generates, registers, and installs a type library into a specified COM+ application.</span></span>  
  
- <span data-ttu-id="ed300-106">配置以编程方式添加到类的服务。</span><span class="sxs-lookup"><span data-stu-id="ed300-106">Configures services that you have added programmatically to your class.</span></span>  
  
 <span data-ttu-id="ed300-107">若要运行此工具，请使用 Visual Studio 开发人员命令提示（或 Windows 7 中的 Visual Studio 命令提示）。</span><span class="sxs-lookup"><span data-stu-id="ed300-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="ed300-108">有关详细信息，请参阅[命令提示](developer-command-prompt-for-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="ed300-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="ed300-109">在命令提示符处，键入以下内容：</span><span class="sxs-lookup"><span data-stu-id="ed300-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed300-110">语法</span><span class="sxs-lookup"><span data-stu-id="ed300-110">Syntax</span></span>  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
## <a name="parameters"></a><span data-ttu-id="ed300-111">参数</span><span class="sxs-lookup"><span data-stu-id="ed300-111">Parameters</span></span>  
  
|<span data-ttu-id="ed300-112">参数</span><span class="sxs-lookup"><span data-stu-id="ed300-112">Argument</span></span>|<span data-ttu-id="ed300-113">说明</span><span class="sxs-lookup"><span data-stu-id="ed300-113">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ed300-114">assemblyFile.dll </span><span class="sxs-lookup"><span data-stu-id="ed300-114">*assemblyFile.dll*</span></span>|<span data-ttu-id="ed300-115">源程序集文件。</span><span class="sxs-lookup"><span data-stu-id="ed300-115">The source assembly file.</span></span> <span data-ttu-id="ed300-116">此程序集必须用强名称进行签名。</span><span class="sxs-lookup"><span data-stu-id="ed300-116">The assembly must be signed with a strong name.</span></span> <span data-ttu-id="ed300-117">有关详细信息，请参阅[使用强名称为程序集签名](../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="ed300-117">For more information, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span>|  
  
|<span data-ttu-id="ed300-118">选项</span><span class="sxs-lookup"><span data-stu-id="ed300-118">Option</span></span>|<span data-ttu-id="ed300-119">说明</span><span class="sxs-lookup"><span data-stu-id="ed300-119">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="ed300-120">/appdir: path  </span><span class="sxs-lookup"><span data-stu-id="ed300-120">**/appdir:** *path*</span></span>|<span data-ttu-id="ed300-121">指定应用程序的根目录。</span><span class="sxs-lookup"><span data-stu-id="ed300-121">Specifies the root directory of the application.</span></span>|  
|<span data-ttu-id="ed300-122">/appname: applicationName  </span><span class="sxs-lookup"><span data-stu-id="ed300-122">**/appname:** *applicationName*</span></span>|<span data-ttu-id="ed300-123">指定要查找或创建的 COM+ 应用程序的名称。</span><span class="sxs-lookup"><span data-stu-id="ed300-123">Specifies the name of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="ed300-124">**/c**</span><span class="sxs-lookup"><span data-stu-id="ed300-124">**/c**</span></span>|<span data-ttu-id="ed300-125">创建目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="ed300-125">Creates the target application.</span></span>|  
|<span data-ttu-id="ed300-126">/componly </span><span class="sxs-lookup"><span data-stu-id="ed300-126">**/componly**</span></span>|<span data-ttu-id="ed300-127">只配置组件；忽略方法和接口。</span><span class="sxs-lookup"><span data-stu-id="ed300-127">Configures components only; ignores methods and interfaces.</span></span>|  
|<span data-ttu-id="ed300-128">/exapp </span><span class="sxs-lookup"><span data-stu-id="ed300-128">**/exapp**</span></span>|<span data-ttu-id="ed300-129">指定此工具需要现有应用程序。</span><span class="sxs-lookup"><span data-stu-id="ed300-129">Specifies to the tool to expect an existing application.</span></span>|  
|<span data-ttu-id="ed300-130">/extlb </span><span class="sxs-lookup"><span data-stu-id="ed300-130">**/extlb**</span></span>|<span data-ttu-id="ed300-131">使用现有类型库。</span><span class="sxs-lookup"><span data-stu-id="ed300-131">Uses an existing type library.</span></span>|  
|<span data-ttu-id="ed300-132">/fc </span><span class="sxs-lookup"><span data-stu-id="ed300-132">**/fc**</span></span>|<span data-ttu-id="ed300-133">查找或创建目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="ed300-133">Finds or creates the target application.</span></span>|  
|<span data-ttu-id="ed300-134">**/help**</span><span class="sxs-lookup"><span data-stu-id="ed300-134">**/help**</span></span>|<span data-ttu-id="ed300-135">显示该工具的命令语法和选项。</span><span class="sxs-lookup"><span data-stu-id="ed300-135">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="ed300-136">/noreconfig </span><span class="sxs-lookup"><span data-stu-id="ed300-136">**/noreconfig**</span></span>|<span data-ttu-id="ed300-137">不重新配置现有的目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="ed300-137">Does not reconfigure an existing target application.</span></span>|  
|<span data-ttu-id="ed300-138">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="ed300-138">**/nologo**</span></span>|<span data-ttu-id="ed300-139">取消显示 Microsoft 启动版权标志。</span><span class="sxs-lookup"><span data-stu-id="ed300-139">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="ed300-140">/parname: name  </span><span class="sxs-lookup"><span data-stu-id="ed300-140">**/parname:** *name*</span></span>|<span data-ttu-id="ed300-141">指定要查找或创建的 COM+ 应用程序的名称或 ID。</span><span class="sxs-lookup"><span data-stu-id="ed300-141">Specifies the name or id of the COM+ application to either find or create.</span></span>|  
|<span data-ttu-id="ed300-142">/reconfig </span><span class="sxs-lookup"><span data-stu-id="ed300-142">**/reconfig**</span></span>|<span data-ttu-id="ed300-143">重新配置现有目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="ed300-143">Reconfigures an existing target application.</span></span> <span data-ttu-id="ed300-144">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="ed300-144">This is the default.</span></span>|  
|<span data-ttu-id="ed300-145">/tlb: typelibraryfile  </span><span class="sxs-lookup"><span data-stu-id="ed300-145">**/tlb:** *typelibraryfile*</span></span>|<span data-ttu-id="ed300-146">指定要安装的类型库文件。</span><span class="sxs-lookup"><span data-stu-id="ed300-146">Specifies the type library file to install.</span></span>|  
|<span data-ttu-id="ed300-147">/u </span><span class="sxs-lookup"><span data-stu-id="ed300-147">**/u**</span></span>|<span data-ttu-id="ed300-148">卸载目标应用程序。</span><span class="sxs-lookup"><span data-stu-id="ed300-148">Uninstalls the target application.</span></span>|  
|<span data-ttu-id="ed300-149">**/quiet**</span><span class="sxs-lookup"><span data-stu-id="ed300-149">**/quiet**</span></span>|<span data-ttu-id="ed300-150">指定安静模式；取消显示登录和成功消息。</span><span class="sxs-lookup"><span data-stu-id="ed300-150">Specifies quiet mode; suppresses the logo and success message display.</span></span>|  
|<span data-ttu-id="ed300-151">**/?**</span><span class="sxs-lookup"><span data-stu-id="ed300-151">**/?**</span></span>|<span data-ttu-id="ed300-152">显示该工具的命令语法和选项。</span><span class="sxs-lookup"><span data-stu-id="ed300-152">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed300-153">备注</span><span class="sxs-lookup"><span data-stu-id="ed300-153">Remarks</span></span>  
 <span data-ttu-id="ed300-154">Regsvcs.exe 需要由 assemblyFile.dll 指定的源程序集文件  。</span><span class="sxs-lookup"><span data-stu-id="ed300-154">Regsvcs.exe requires a source assembly file specified by *assemblyFile.dll*.</span></span> <span data-ttu-id="ed300-155">此程序集必须用强名称进行签名。</span><span class="sxs-lookup"><span data-stu-id="ed300-155">This assembly must be signed with a strong name.</span></span> <span data-ttu-id="ed300-156">有关强名称签名的更多信息，请参阅[使用强名称为程序集签名](../../standard/assembly/sign-strong-name.md)。</span><span class="sxs-lookup"><span data-stu-id="ed300-156">For more information on strong name signing, see [Signing an Assembly with a Strong Name](../../standard/assembly/sign-strong-name.md).</span></span> <span data-ttu-id="ed300-157">目标应用程序的名称和类型库文件的名称都是可选的。</span><span class="sxs-lookup"><span data-stu-id="ed300-157">The names of the target application and the type library file are optional.</span></span> <span data-ttu-id="ed300-158">如果 applicationName 参数尚不存在，则该参数可从源程序集文件生成并且将由 Regsvcs.exe 创建  。</span><span class="sxs-lookup"><span data-stu-id="ed300-158">The *applicationName* argument can be generated from the source assembly file and will be created by Regsvcs.exe, if it does not already exist.</span></span> <span data-ttu-id="ed300-159">typelibraryfile 参数可以指定类型库名称  。</span><span class="sxs-lookup"><span data-stu-id="ed300-159">The *typelibraryfile* argument can specify a type library name.</span></span> <span data-ttu-id="ed300-160">如果未指定类型库名称，默认情况下，Regsvcs.exe 将使用程序集名称。</span><span class="sxs-lookup"><span data-stu-id="ed300-160">If you do not specify a type library name, Regsvcs.exe uses the assembly name as the default.</span></span>  
  
 <span data-ttu-id="ed300-161">当 Regsvcs.exe 注册组件的方法时，它需要遵从那些方法的[要求](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100))和[链接要求](../misc/link-demands.md)。</span><span class="sxs-lookup"><span data-stu-id="ed300-161">When Regsvcs.exe registers a component's methods, it is subject to the [demands](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) and [link demands](../misc/link-demands.md) on those methods.</span></span> <span data-ttu-id="ed300-162">因为该工具在完全受信任的环境中执行，所以大多数权限要求都会成功。</span><span class="sxs-lookup"><span data-stu-id="ed300-162">Because the tool executes in a fully-trusted environment, most demands for a permission succeed.</span></span> <span data-ttu-id="ed300-163">但是，如果组件中的方法受 <xref:System.Security.Permissions.StrongNameIdentityPermission> 或 <xref:System.Security.Permissions.PublisherIdentityPermission> 的要求或链接要求保护，则 Regsvcs.exe 无法注册这些组件。</span><span class="sxs-lookup"><span data-stu-id="ed300-163">However, Regsvcs.exe cannot register components with methods protected by a demand or link demand for the <xref:System.Security.Permissions.StrongNameIdentityPermission> or the <xref:System.Security.Permissions.PublisherIdentityPermission>.</span></span>  
  
 <span data-ttu-id="ed300-164">你必须在本地计算机上具有管理特权才能使用 Regsvcs.exe。</span><span class="sxs-lookup"><span data-stu-id="ed300-164">You must have administrative privileges on the local computer to use Regsvcs.exe.</span></span>  
  
 <span data-ttu-id="ed300-165">如果 Regsvcs.exe 在执行上述任何操作时失败，它将显示相应的错误信息。</span><span class="sxs-lookup"><span data-stu-id="ed300-165">If Regsvcs.exe fails while performing any of these actions, it displays corresponding error messages.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ed300-166">示例</span><span class="sxs-lookup"><span data-stu-id="ed300-166">Examples</span></span>  
 <span data-ttu-id="ed300-167">下面的命令将 `myTest.dll` 中包含的所有公共类添加到 `myTargetApp`（一个现有的 COM+ 应用程序）中，同时生成 `myTest.tlb` 类型库。</span><span class="sxs-lookup"><span data-stu-id="ed300-167">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `myTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 <span data-ttu-id="ed300-168">下面的命令将 `myTest.dll` 中包含的所有公共类添加到 `myTargetApp`（一个现有的 COM+ 应用程序）中，同时生成 `newTest.tlb` 类型库。</span><span class="sxs-lookup"><span data-stu-id="ed300-168">The following command adds all public classes contained in `myTest.dll` to `myTargetApp` (an existing COM+ application) and produces the `newTest.tlb` type library.</span></span>  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="ed300-169">请参阅</span><span class="sxs-lookup"><span data-stu-id="ed300-169">See also</span></span>

- [<span data-ttu-id="ed300-170">工具</span><span class="sxs-lookup"><span data-stu-id="ed300-170">Tools</span></span>](index.md)
- [<span data-ttu-id="ed300-171">如何：使用强名称为程序集签名</span><span class="sxs-lookup"><span data-stu-id="ed300-171">How to: Sign an Assembly with a Strong Name</span></span>](../../standard/assembly/sign-strong-name.md)
- [<span data-ttu-id="ed300-172">命令提示</span><span class="sxs-lookup"><span data-stu-id="ed300-172">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
