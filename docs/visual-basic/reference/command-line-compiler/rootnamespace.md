---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: 4df4e74fc13c922f51f5b74c3c152bdea28b4431
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005209"
---
# <a name="-rootnamespace"></a><span data-ttu-id="77041-102">-rootnamespace</span><span class="sxs-lookup"><span data-stu-id="77041-102">-rootnamespace</span></span>
<span data-ttu-id="77041-103">指定所有类型声明的命名空间。</span><span class="sxs-lookup"><span data-stu-id="77041-103">Specifies a namespace for all type declarations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77041-104">语法</span><span class="sxs-lookup"><span data-stu-id="77041-104">Syntax</span></span>  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a><span data-ttu-id="77041-105">自变量</span><span class="sxs-lookup"><span data-stu-id="77041-105">Arguments</span></span>  
  
|<span data-ttu-id="77041-106">术语</span><span class="sxs-lookup"><span data-stu-id="77041-106">Term</span></span>|<span data-ttu-id="77041-107">定义</span><span class="sxs-lookup"><span data-stu-id="77041-107">Definition</span></span>|  
|---|---|  
|`namespace`|<span data-ttu-id="77041-108">命名空间的名称，其中包含当前项目的所有类型声明。</span><span class="sxs-lookup"><span data-stu-id="77041-108">The name of the namespace in which to enclose all type declarations for the current project.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77041-109">备注</span><span class="sxs-lookup"><span data-stu-id="77041-109">Remarks</span></span>  
 <span data-ttu-id="77041-110">如果使用 Visual Studio 可执行文件 (Devenv.exe) 来编译在 Visual Studio 集成开发环境中创建的项目，请使用 `-rootnamespace` 指定 <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="77041-110">If you use the Visual Studio executable file (Devenv.exe) to compile a project created in the Visual Studio integrated development environment, use `-rootnamespace` to specify the value of the <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> property.</span></span> <span data-ttu-id="77041-111">有关详细信息，请参阅 [Devenv 命令行开关](/visualstudio/ide/reference/devenv-command-line-switches)。</span><span class="sxs-lookup"><span data-stu-id="77041-111">See [Devenv Command Line Switches](/visualstudio/ide/reference/devenv-command-line-switches) for more information.</span></span>  
  
 <span data-ttu-id="77041-112">使用公共语言运行时 MSIL 反汇编程序 (`Ildasm.exe`) 来查看输出文件中的命名空间名称。</span><span class="sxs-lookup"><span data-stu-id="77041-112">Use the common language runtime MSIL Disassembler (`Ildasm.exe`) to view the namespace names in your output file.</span></span>  
  
|<span data-ttu-id="77041-113">在 Visual Studio 集成开发环境中设置 -rootnamespace</span><span class="sxs-lookup"><span data-stu-id="77041-113">To set -rootnamespace in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="77041-114">1.在 **“解决方案资源管理器”** 中选择一个项目。</span><span class="sxs-lookup"><span data-stu-id="77041-114">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="77041-115">在“项目”菜单上，单击“属性”   。</span><span class="sxs-lookup"><span data-stu-id="77041-115">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="77041-116">2.单击“应用程序”  选项卡。</span><span class="sxs-lookup"><span data-stu-id="77041-116">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="77041-117">3.修改“根命名空间”  框中的值。</span><span class="sxs-lookup"><span data-stu-id="77041-117">3.  Modify the value in the **Root Namespace** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="77041-118">示例</span><span class="sxs-lookup"><span data-stu-id="77041-118">Example</span></span>  
 <span data-ttu-id="77041-119">下面的代码编译 `In.vb`，并将所有类型声明包含在命名空间 `mynamespace` 中。</span><span class="sxs-lookup"><span data-stu-id="77041-119">The following code compiles `In.vb` and encloses all type declarations in the namespace `mynamespace`.</span></span>  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="77041-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="77041-120">See also</span></span>

- [<span data-ttu-id="77041-121">Visual Basic 命令行编译器</span><span class="sxs-lookup"><span data-stu-id="77041-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="77041-122">Ildasm.exe（IL 反汇编程序）</span><span class="sxs-lookup"><span data-stu-id="77041-122">Ildasm.exe (IL Disassembler)</span></span>](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [<span data-ttu-id="77041-123">示例编译命令行</span><span class="sxs-lookup"><span data-stu-id="77041-123">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
