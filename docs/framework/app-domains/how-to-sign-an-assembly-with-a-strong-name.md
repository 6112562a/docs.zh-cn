---
title: 如何：使用强名称为程序集签名
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b109ec82d139e3b3eb321c90d5f41dd1eae216f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927924"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="5e1ad-102">如何：使用强名称为程序集签名</span><span class="sxs-lookup"><span data-stu-id="5e1ad-102">How to: Sign an Assembly with a Strong Name</span></span>
<span data-ttu-id="5e1ad-103">可通过许多方法为程序集签署强名称：</span><span class="sxs-lookup"><span data-stu-id="5e1ad-103">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="5e1ad-104">在 Visual Studio 中，通过使用项目的 **“属性”** 对话框中的 **“签名”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-104">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="5e1ad-105">这是为程序集签署强名称的最简单且最方便的方法。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-105">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="5e1ad-106">通过使用 [程序集链接器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 将 .NET Framework 代码模块（.netmodule 文件）与密钥文件链接。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-106">By using the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a .netmodule file) with a key file.</span></span>  
  
- <span data-ttu-id="5e1ad-107">通过使用程序集特性将强名称信息插入代码中。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-107">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="5e1ad-108">你可以使用 <xref:System.Reflection.AssemblyKeyFileAttribute> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 特性，具体取决于要使用的密钥文件所在的位置。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-108">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="5e1ad-109">通过使用编译器选项。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-109">By using compiler options.</span></span>  
  
 <span data-ttu-id="5e1ad-110">要使用强名称为程序集签名，必须具有加密密钥对。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-110">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="5e1ad-111">有关创建密钥对的详细信息，请参阅[如何：创建公钥/私钥对](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-111">For more information about creating a key pair, see [How to: Create a Public-Private Key Pair](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="5e1ad-112">使用 Visual Studio 创建程序集并为程序集签署强名称</span><span class="sxs-lookup"><span data-stu-id="5e1ad-112">To create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="5e1ad-113">在“解决方案资源管理器”  中，打开项目的快捷菜单，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-113">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="5e1ad-114">选择 **“签名”** 选项卡。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-114">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="5e1ad-115">选择“为程序集签名”  框。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-115">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="5e1ad-116">在“选择强名称密钥文件”  框中，选择“\<浏览…>”  ，然后导航到该密钥文件。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-116">In the **Choose a strong name key file** box, choose **\<Browse…>**, and then navigate to the key file.</span></span> <span data-ttu-id="5e1ad-117">若要创建新的密钥文件，请选择“\<新建…>”  ，然后在“创建强名称密钥”  对话框中输入其名称。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-117">To create a new key file, choose **\<New…>** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e1ad-118">为了[延迟为程序集签名](../../../docs/framework/app-domains/delay-sign-assembly.md)，请选择公钥文件。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-118">In order to [delay sign an assembly](../../../docs/framework/app-domains/delay-sign-assembly.md), choose a public key file.</span></span>  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="5e1ad-119">使用程序集链接器创建程序集并为程序集签署强名称</span><span class="sxs-lookup"><span data-stu-id="5e1ad-119">To create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
- <span data-ttu-id="5e1ad-120">在 [Visual Studio 开发人员命令提示](../../../docs/framework/tools/developer-command-prompt-for-vs.md)处，键入以下命令：</span><span class="sxs-lookup"><span data-stu-id="5e1ad-120">At the [Developer Command Prompt for Visual Studio](../../../docs/framework/tools/developer-command-prompt-for-vs.md), type the following command:</span></span>  
  
     <span data-ttu-id="5e1ad-121">**al** **/out:** \<*assemblyName*>  *\<moduleName>* **/keyfile:** \<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="5e1ad-121">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  
  
     <span data-ttu-id="5e1ad-122">其中：</span><span class="sxs-lookup"><span data-stu-id="5e1ad-122">where:</span></span>  
  
     <span data-ttu-id="5e1ad-123">*assemblyName*</span><span class="sxs-lookup"><span data-stu-id="5e1ad-123">*assemblyName*</span></span>  
     <span data-ttu-id="5e1ad-124">程序集链接器将发出的强签名的程序集的名称（.dll 或 .exe 文件）。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-124">The name of the strongly signed assembly (a .dll or .exe file) that Assembly Linker will emit.</span></span>  
  
     <span data-ttu-id="5e1ad-125">*moduleName*</span><span class="sxs-lookup"><span data-stu-id="5e1ad-125">*moduleName*</span></span>  
     <span data-ttu-id="5e1ad-126">包含一个或多个类型的 .NET Framework 代码模块的名称（.netmodule 文件）。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-126">The name of a .NET Framework code module (a .netmodule file) that includes one or more types.</span></span> <span data-ttu-id="5e1ad-127">可以通过在 C# 或 Visual Basic 中使用 `/target:module` 开关编译代码来创建 .netmodule 文件。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-127">You can create a .netmodule file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>  
  
     <span data-ttu-id="5e1ad-128">*keyfileName*</span><span class="sxs-lookup"><span data-stu-id="5e1ad-128">*keyfileName*</span></span>  
     <span data-ttu-id="5e1ad-129">包含密钥对的容器或文件的名称。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-129">The name of the container or file that contains the key pair.</span></span> <span data-ttu-id="5e1ad-130">程序集链接器解释与当前目录相关的相对路径。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-130">Assembly Linker interprets a relative path in relationship to the current directory.</span></span>  
  
 <span data-ttu-id="5e1ad-131">下面的示例使用密钥文件 `MyAssembly.dll` 为程序集 `sgKey.snk`签署强名称。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-131">The following example signs the assembly `MyAssembly.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 <span data-ttu-id="5e1ad-132">有关此工具的详细信息，请参阅 [程序集链接器](../../../docs/framework/tools/al-exe-assembly-linker.md)。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-132">For more information about this tool, see [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="5e1ad-133">使用特性为程序集签署强名称</span><span class="sxs-lookup"><span data-stu-id="5e1ad-133">To sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="5e1ad-134">将 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 特性添加到源代码文件中，并指定包含为程序集签署强名称时要使用的密钥对的文件或容器的名称。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-134">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  
  
2. <span data-ttu-id="5e1ad-135">通常会编译源代码文件。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-135">Compile the source code file normally.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5e1ad-136">当 C# 和 Visual Basic 编译器在源代码中遇到 <xref:System.Reflection.AssemblyKeyFileAttribute> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 特性时，会发出编译器警告（分别为 CS1699 和 BC41008）。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-136">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="5e1ad-137">你可以忽略这些警告。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-137">You can ignore the warnings.</span></span>  
  
 <span data-ttu-id="5e1ad-138">下面的代码示例将 <xref:System.Reflection.AssemblyKeyFileAttribute> 特性用于名为 `keyfile.snk`的密钥文件（位于编译程序集的目录中）。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-138">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called `keyfile.snk`, which is located in the directory where the assembly is compiled.</span></span>  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 <span data-ttu-id="5e1ad-139">在编译源文件时，也可以延迟为程序集签名。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-139">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="5e1ad-140">有关更多信息，请参见 [延迟为程序集签名](../../../docs/framework/app-domains/delay-sign-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-140">For more information, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="5e1ad-141">使用编译器为程序集签署强名称</span><span class="sxs-lookup"><span data-stu-id="5e1ad-141">To sign an assembly with a strong name by using the compiler</span></span>  
  
- <span data-ttu-id="5e1ad-142">使用 C# 和 Visual Basic 中的 `/keyfile` 或 `/delaysign` 编译器选项，或使用 C++ 中的 `/KEYFILE` 或 `/DELAYSIGN` 链接器选项编译源代码文件。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-142">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="5e1ad-143">在选项名称后，添加冒号和密钥文件的名称。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-143">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="5e1ad-144">使用命令行编译器时，你可以将密钥文件复制到包含源代码文件的目录中。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-144">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  
  
     <span data-ttu-id="5e1ad-145">有关延迟签名的信息，请参阅 [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-145">For information on delay signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
     <span data-ttu-id="5e1ad-146">下面的示例使用 C# 编译器并借助密钥文件 `UtilityLibrary.dll` 为程序集 `sgKey.snk` 签署强名称。</span><span class="sxs-lookup"><span data-stu-id="5e1ad-146">The following example uses the C# compiler and signs the assembly `UtilityLibrary.dll` with a strong name by using the key file `sgKey.snk`.</span></span>  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5e1ad-147">请参阅</span><span class="sxs-lookup"><span data-stu-id="5e1ad-147">See also</span></span>

- [<span data-ttu-id="5e1ad-148">创建和使用具有强名称的程序集</span><span class="sxs-lookup"><span data-stu-id="5e1ad-148">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [<span data-ttu-id="5e1ad-149">如何：创建公钥/私钥对</span><span class="sxs-lookup"><span data-stu-id="5e1ad-149">How to: Create a Public-Private Key Pair</span></span>](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [<span data-ttu-id="5e1ad-150">Al.exe（程序集链接器）</span><span class="sxs-lookup"><span data-stu-id="5e1ad-150">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="5e1ad-151">延迟签发程序集</span><span class="sxs-lookup"><span data-stu-id="5e1ad-151">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [<span data-ttu-id="5e1ad-152">管理程序集签名和清单签名</span><span class="sxs-lookup"><span data-stu-id="5e1ad-152">Managing Assembly and Manifest Signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="5e1ad-153">“项目设计器”->“签名”页</span><span class="sxs-lookup"><span data-stu-id="5e1ad-153">Signing Page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
