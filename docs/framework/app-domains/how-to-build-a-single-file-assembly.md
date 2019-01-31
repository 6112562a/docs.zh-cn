---
title: 如何：生成单文件程序集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5c0b5dc2e001121ab54447bae4a5eed3290a580
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597835"
---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="1254e-102">如何：生成单文件程序集</span><span class="sxs-lookup"><span data-stu-id="1254e-102">How to: Build a Single-File Assembly</span></span>

<span data-ttu-id="1254e-103">单文件程序集（最简单的程序集类型）包含类型信息和实现，以及[程序集清单](../../../docs/framework/app-domains/assembly-manifest.md)。</span><span class="sxs-lookup"><span data-stu-id="1254e-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="1254e-104">可以使用命令行编译器或 Visual Studio 创建单文件程序集。</span><span class="sxs-lookup"><span data-stu-id="1254e-104">You can use command-line compilers or Visual Studio to create a single-file assembly.</span></span> <span data-ttu-id="1254e-105">默认情况下，编译器创建扩展名为 .exe 的程序集文件。</span><span class="sxs-lookup"><span data-stu-id="1254e-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>

> [!NOTE]
> <span data-ttu-id="1254e-106">适用于 C# 和 Visual Basic 的 Visual Studio 只能用于创建单文件程序集。</span><span class="sxs-lookup"><span data-stu-id="1254e-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="1254e-107">如果要创建多文件程序集，则必须使用命令行编译器或 Visual C++。</span><span class="sxs-lookup"><span data-stu-id="1254e-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="1254e-108">以下步骤说明如何使用命令行编译器创建单文件程序集。</span><span class="sxs-lookup"><span data-stu-id="1254e-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="1254e-109">创建扩展名为 .exe 的程序集</span><span class="sxs-lookup"><span data-stu-id="1254e-109">To create an assembly with an .exe extension</span></span>

1.  <span data-ttu-id="1254e-110">在命令提示符处，键入下列命令：</span><span class="sxs-lookup"><span data-stu-id="1254e-110">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="1254e-111">\<compiler command> \<module name></span><span class="sxs-lookup"><span data-stu-id="1254e-111">\<*compiler command*> \<*module name*></span></span>

     <span data-ttu-id="1254e-112">在此命令中，“compiler command”是代码模块中所用语言的编译器命令，“module name”是要编译为程序集的代码模块的名称。</span><span class="sxs-lookup"><span data-stu-id="1254e-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

 <span data-ttu-id="1254e-113">以下示例从名为 `myCode` 的代码模块创建名为 `myCode.exe` 的程序集。</span><span class="sxs-lookup"><span data-stu-id="1254e-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>

```console
csc myCode.cs
```

```console
vbc myCode.vb
```

### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="1254e-114">创建扩展名为 .exe 的程序集并指定输出文件名</span><span class="sxs-lookup"><span data-stu-id="1254e-114">To create an assembly with an .exe extension and specify the output file name</span></span>

1.  <span data-ttu-id="1254e-115">在命令提示符处，键入下列命令：</span><span class="sxs-lookup"><span data-stu-id="1254e-115">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="1254e-116">\<compiler command> /out:\<file name> \<module name></span><span class="sxs-lookup"><span data-stu-id="1254e-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

     <span data-ttu-id="1254e-117">在此命令中，“compiler command”是代码模块中所用语言的编译器命令，“file name”是输出文件名称，而“module name”是要编译为程序集的代码模块的名称。</span><span class="sxs-lookup"><span data-stu-id="1254e-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

 <span data-ttu-id="1254e-118">以下示例从名为 `myCode` 的代码模块创建名为 `myAssembly.exe` 的程序集。</span><span class="sxs-lookup"><span data-stu-id="1254e-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>

```console
csc -out:myAssembly.exe myCode.cs
```

```console
vbc -out:myAssembly.exe myCode.vb
```

## <a name="creating-library-assemblies"></a><span data-ttu-id="1254e-119">创建库程序集</span><span class="sxs-lookup"><span data-stu-id="1254e-119">Creating Library Assemblies</span></span>
 <span data-ttu-id="1254e-120">库程序集与类库相似。</span><span class="sxs-lookup"><span data-stu-id="1254e-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="1254e-121">它包含将由其他程序集引用的类型，但没有开始执行的入口点。</span><span class="sxs-lookup"><span data-stu-id="1254e-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

### <a name="to-create-a-library-assembly"></a><span data-ttu-id="1254e-122">创建库程序集</span><span class="sxs-lookup"><span data-stu-id="1254e-122">To create a library assembly</span></span>

1.  <span data-ttu-id="1254e-123">在命令提示符处，键入下列命令：</span><span class="sxs-lookup"><span data-stu-id="1254e-123">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="1254e-124">\<compiler command> /t:library \<module name></span><span class="sxs-lookup"><span data-stu-id="1254e-124">\<*compiler command*> **-t:library** \<*module name*></span></span>

     <span data-ttu-id="1254e-125">在此命令中，“compiler command”是代码模块中所用语言的编译器命令，“module name”是要编译为程序集的代码模块的名称。</span><span class="sxs-lookup"><span data-stu-id="1254e-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="1254e-126">也可以使用其他编译器选项，例如 -out: 选项。</span><span class="sxs-lookup"><span data-stu-id="1254e-126">You can also use other compiler options, such as the **-out:** option.</span></span>

 <span data-ttu-id="1254e-127">以下示例从名为 `myCode` 的代码模块创建名为 `myCodeAssembly.dll` 的库程序集。</span><span class="sxs-lookup"><span data-stu-id="1254e-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>

```console
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="1254e-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="1254e-128">See also</span></span>

- [<span data-ttu-id="1254e-129">创建程序集</span><span class="sxs-lookup"><span data-stu-id="1254e-129">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="1254e-130">多文件程序集</span><span class="sxs-lookup"><span data-stu-id="1254e-130">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="1254e-131">如何：生成单文件程序集</span><span class="sxs-lookup"><span data-stu-id="1254e-131">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="1254e-132">使用程序集编程</span><span class="sxs-lookup"><span data-stu-id="1254e-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)