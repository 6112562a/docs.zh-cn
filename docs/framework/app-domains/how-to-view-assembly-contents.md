---
title: 如何：查看程序集内容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5aff7ec439e845c4be8d43ae622fe44fa2c476c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597861"
---
# <a name="how-to-view-assembly-contents"></a><span data-ttu-id="e54ad-102">如何：查看程序集内容</span><span class="sxs-lookup"><span data-stu-id="e54ad-102">How to: View Assembly Contents</span></span>
<span data-ttu-id="e54ad-103">可使用 [Ildasm.exe（IL 反汇编程序）](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)查看文件中的 Microsoft 中间语言 (MSIL) 信息。</span><span class="sxs-lookup"><span data-stu-id="e54ad-103">You can use the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) to view Microsoft intermediate language (MSIL) information in a file.</span></span> <span data-ttu-id="e54ad-104">如果要检查的文件是程序集，此信息可包括程序集的属性以及对其他模块和程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="e54ad-104">If the file being examined is an assembly, this information can include the assembly's attributes, as well as references to other modules and assemblies.</span></span> <span data-ttu-id="e54ad-105">此信息有助于确定文件是程序集还是程序集的一部分，以及文件是否具有对其他模块或程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="e54ad-105">This information can be helpful in determining whether a file is an assembly or part of an assembly, and whether the file has references to other modules or assemblies.</span></span>  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a><span data-ttu-id="e54ad-106">使用 Ildasm.exe 显示程序集的内容</span><span class="sxs-lookup"><span data-stu-id="e54ad-106">To display the contents of an assembly using Ildasm.exe</span></span>  
  
1.  <span data-ttu-id="e54ad-107">在命令提示符处键入 ildasm \<assembly name>。</span><span class="sxs-lookup"><span data-stu-id="e54ad-107">Type **ildasm** \<*assembly name*> at the command prompt.</span></span> <span data-ttu-id="e54ad-108">例如，以下命令反汇编 `Hello.exe` 程序集。</span><span class="sxs-lookup"><span data-stu-id="e54ad-108">For example, the following command disassembles the `Hello.exe` assembly.</span></span>  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a><span data-ttu-id="e54ad-109">查看程序集清单信息</span><span class="sxs-lookup"><span data-stu-id="e54ad-109">To view assembly manifest information</span></span>  
  
1.  <span data-ttu-id="e54ad-110">在“MSIL 反汇编程序”窗口双击“清单”图标。</span><span class="sxs-lookup"><span data-stu-id="e54ad-110">Double-click the MANIFEST icon in the MSIL Disassembler window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e54ad-111">示例</span><span class="sxs-lookup"><span data-stu-id="e54ad-111">Example</span></span>  
 <span data-ttu-id="e54ad-112">下例以基本的“Hello, World”程序开始。</span><span class="sxs-lookup"><span data-stu-id="e54ad-112">The following example starts with a basic "Hello, World" program.</span></span> <span data-ttu-id="e54ad-113">编译该程序后，使用 Ildasm.exe 反汇编 Hello.exe 程序集并查看程序集清单。</span><span class="sxs-lookup"><span data-stu-id="e54ad-113">After compiling the program, use Ildasm.exe to disassemble the Hello.exe assembly and view the assembly manifest.</span></span>  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 <span data-ttu-id="e54ad-114">在 Hello.exe 程序集上运行 ildasm.exe 命令，然后在 IL DASM 窗口中双击“清单”图标生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="e54ad-114">Running the command ildasm.exe on the Hello.exe assembly and double-clicking the MANIFEST icon in the IL DASM window produces the following output:</span></span>  
  
```  
// Metadata version: v4.0.30319  
.assembly extern mscorlib  
{  
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..  
  .ver 4:0:0:0  
}  
.assembly Hello  
{  
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )   
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx  
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.  
  .hash algorithm 0x00008004  
  .ver 0:0:0:0  
}  
.module Hello.exe  
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}  
.imagebase 0x00400000  
.file alignment 0x00000200  
.stackreserve 0x00100000  
.subsystem 0x0003       // WINDOWS_CUI  
.corflags 0x00000001    //  ILONLY  
// Image base: 0x00600000  
```  
  
 <span data-ttu-id="e54ad-115">下表描述了本例所使用 Hello.exe 程序集的程序集清单中的各项指令。</span><span class="sxs-lookup"><span data-stu-id="e54ad-115">The following table describes each directive in the assembly manifest of the Hello.exe assembly used in the example.</span></span>  
  
|<span data-ttu-id="e54ad-116">指令</span><span class="sxs-lookup"><span data-stu-id="e54ad-116">Directive</span></span>|<span data-ttu-id="e54ad-117">说明</span><span class="sxs-lookup"><span data-stu-id="e54ad-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e54ad-118">.assembly extern \< assembly name ></span><span class="sxs-lookup"><span data-stu-id="e54ad-118">**.assembly extern \<** *assembly name* **>**</span></span>|<span data-ttu-id="e54ad-119">指定包含当前模块所引用项目的另一程序集（在此示例中为 `mscorlib`）。</span><span class="sxs-lookup"><span data-stu-id="e54ad-119">Specifies another assembly that contains items referenced by the current module (in this example, `mscorlib`).</span></span>|  
|<span data-ttu-id="e54ad-120">.publickeytoken \< token ></span><span class="sxs-lookup"><span data-stu-id="e54ad-120">**.publickeytoken \<** *token* **>**</span></span>|<span data-ttu-id="e54ad-121">指定引用程序集的实际密钥的标记。</span><span class="sxs-lookup"><span data-stu-id="e54ad-121">Specifies the token of the actual key of the referenced assembly.</span></span>|  
|<span data-ttu-id="e54ad-122">.ver \< version number ></span><span class="sxs-lookup"><span data-stu-id="e54ad-122">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="e54ad-123">指定引用程序集的版本号。</span><span class="sxs-lookup"><span data-stu-id="e54ad-123">Specifies the version number of the referenced assembly.</span></span>|  
|<span data-ttu-id="e54ad-124">.assembly \< assembly name ></span><span class="sxs-lookup"><span data-stu-id="e54ad-124">**.assembly \<** *assembly name* **>**</span></span>|<span data-ttu-id="e54ad-125">指定程序集名称。</span><span class="sxs-lookup"><span data-stu-id="e54ad-125">Specifies the assembly name.</span></span>|  
|<span data-ttu-id="e54ad-126">.hash algorithm \< int32 value ></span><span class="sxs-lookup"><span data-stu-id="e54ad-126">**.hash algorithm \<** *int32 value* **>**</span></span>|<span data-ttu-id="e54ad-127">指定使用的哈希算法。</span><span class="sxs-lookup"><span data-stu-id="e54ad-127">Specifies the hash algorithm used.</span></span>|  
|<span data-ttu-id="e54ad-128">.ver \< version number ></span><span class="sxs-lookup"><span data-stu-id="e54ad-128">**.ver \<** *version number* **>**</span></span>|<span data-ttu-id="e54ad-129">指定程序集的版本号。</span><span class="sxs-lookup"><span data-stu-id="e54ad-129">Specifies the version number of the assembly.</span></span>|  
|<span data-ttu-id="e54ad-130">.module \< file name ></span><span class="sxs-lookup"><span data-stu-id="e54ad-130">**.module \<** *file name* **>**</span></span>|<span data-ttu-id="e54ad-131">指定组成程序集的模块名称。</span><span class="sxs-lookup"><span data-stu-id="e54ad-131">Specifies the name of the modules that make up the assembly.</span></span> <span data-ttu-id="e54ad-132">在此示例中，程序集只包含一个文件。</span><span class="sxs-lookup"><span data-stu-id="e54ad-132">In this example, the assembly consists of only one file.</span></span>|  
|<span data-ttu-id="e54ad-133">.subsystem \< value ></span><span class="sxs-lookup"><span data-stu-id="e54ad-133">**.subsystem \<** *value* **>**</span></span>|<span data-ttu-id="e54ad-134">指定程序要求的应用程序环境。</span><span class="sxs-lookup"><span data-stu-id="e54ad-134">Specifies the application environment required for the program.</span></span> <span data-ttu-id="e54ad-135">在此示例中，值 3 表示该可执行文件从控制台运行。</span><span class="sxs-lookup"><span data-stu-id="e54ad-135">In this example, the value 3 indicates that this executable is run from a console.</span></span>|  
|<span data-ttu-id="e54ad-136">.corflags</span><span class="sxs-lookup"><span data-stu-id="e54ad-136">**.corflags**</span></span>|<span data-ttu-id="e54ad-137">当前是元数据中的一个保留字段。</span><span class="sxs-lookup"><span data-stu-id="e54ad-137">Currently a reserved field in the metadata.</span></span>|  
  
 <span data-ttu-id="e54ad-138">根据程序集的内容，程序集清单可包含许多不同的指令。</span><span class="sxs-lookup"><span data-stu-id="e54ad-138">An assembly manifest can contain a number of different directives, depending on the contents of the assembly.</span></span> <span data-ttu-id="e54ad-139">有关程序集清单中指令的详尽列表，请参阅 ECMA 文档，特别是“Partition II:Metadata Definition and Semantics”（第 2 部分：元数据定义和语义）和“Partition III:CIL Instruction Set”（第 3 部分：CIL 指令集）。</span><span class="sxs-lookup"><span data-stu-id="e54ad-139">For an extensive list of the directives in the assembly manifest, see the ECMA documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="e54ad-140">可联机获取该文档；请参阅 MSDN 上的 [ECMA C# 和公共语言基础结构标准](https://go.microsoft.com/fwlink/?LinkID=99212)和 Ecma International 网站上的[标准 ECMA-335 - 公共语言基础结构 (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552)。</span><span class="sxs-lookup"><span data-stu-id="e54ad-140">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e54ad-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="e54ad-141">See also</span></span>
- [<span data-ttu-id="e54ad-142">应用程序域和程序集</span><span class="sxs-lookup"><span data-stu-id="e54ad-142">Application Domains and Assemblies</span></span>](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)
- [<span data-ttu-id="e54ad-143">应用程序域和程序集用法主题</span><span class="sxs-lookup"><span data-stu-id="e54ad-143">Application Domains and Assemblies How-to Topics</span></span>](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [<span data-ttu-id="e54ad-144">Ildasm.exe（IL 反汇编程序）</span><span class="sxs-lookup"><span data-stu-id="e54ad-144">Ildasm.exe (IL Disassembler)</span></span>](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
