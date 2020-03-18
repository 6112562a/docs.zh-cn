---
title: -target:exe（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 6087a64bea5a59bfcfc5372f6a9d6eb8b9c940cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606463"
---
# <a name="-targetexe-c-compiler-options"></a><span data-ttu-id="d944a-102">-target:exe（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="d944a-102">-target:exe (C# Compiler Options)</span></span>
<span data-ttu-id="d944a-103">-target:exe 选项将使编译器创建可执行文件 (EXE) 和控制台应用程序  。</span><span class="sxs-lookup"><span data-stu-id="d944a-103">The **-target:exe** option causes the compiler to create an executable (EXE), console application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d944a-104">语法</span><span class="sxs-lookup"><span data-stu-id="d944a-104">Syntax</span></span>  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a><span data-ttu-id="d944a-105">备注</span><span class="sxs-lookup"><span data-stu-id="d944a-105">Remarks</span></span>  
 <span data-ttu-id="d944a-106">默认情况下，-target:exe 选项有效  。</span><span class="sxs-lookup"><span data-stu-id="d944a-106">The **-target:exe** option is in effect by default.</span></span> <span data-ttu-id="d944a-107">将创建扩展名为 .exe 的可执行文件。</span><span class="sxs-lookup"><span data-stu-id="d944a-107">The executable file will be created with the .exe extension.</span></span>  
  
 <span data-ttu-id="d944a-108">使用 [-target:winexe](./target-winexe-compiler-option.md) 创建 Windows 程序可执行文件。</span><span class="sxs-lookup"><span data-stu-id="d944a-108">Use [-target:winexe](./target-winexe-compiler-option.md) to create a Windows program executable.</span></span>  
  
 <span data-ttu-id="d944a-109">除非使用 [-out](./out-compiler-option.md) 选项进行指定，否则输出文件名采用包含 [Main](../../programming-guide/main-and-command-args/index.md) 方法的输入文件的名称。</span><span class="sxs-lookup"><span data-stu-id="d944a-109">Unless otherwise specified with the [-out](./out-compiler-option.md) option, the output file name takes the name of the input file that contains the [Main](../../programming-guide/main-and-command-args/index.md) method.</span></span>  
  
 <span data-ttu-id="d944a-110">在命令行中进行指定时，-out 或 -target:module 选项上所有文件都用于创建 .exe 文件  </span><span class="sxs-lookup"><span data-stu-id="d944a-110">When specified at the command line, all files up to the next **-out** or **-target:module** option are used to create the .exe file</span></span>  
  
 <span data-ttu-id="d944a-111">编译为 .exe 文件的源代码文件中只需要一个 **Main** 方法。</span><span class="sxs-lookup"><span data-stu-id="d944a-111">One and only one **Main** method is required in the source code files that are compiled into an .exe file.</span></span> <span data-ttu-id="d944a-112">如果代码具有多个附带 Main 方法的类，则可使用 [-main](./main-compiler-option.md) 编译器选项指定包含 Main 方法的类   。</span><span class="sxs-lookup"><span data-stu-id="d944a-112">The [-main](./main-compiler-option.md) compiler option lets you specify which class contains the **Main** method, in cases where your code has more than one class with a **Main** method.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d944a-113">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="d944a-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d944a-114">打开项目的“属性”  页。</span><span class="sxs-lookup"><span data-stu-id="d944a-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="d944a-115">单击“应用程序”  属性页。</span><span class="sxs-lookup"><span data-stu-id="d944a-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="d944a-116">修改“输出类型”  属性。</span><span class="sxs-lookup"><span data-stu-id="d944a-116">Modify the **Output type** property.</span></span>  
  
 <span data-ttu-id="d944a-117">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。</span><span class="sxs-lookup"><span data-stu-id="d944a-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d944a-118">示例</span><span class="sxs-lookup"><span data-stu-id="d944a-118">Example</span></span>  
 <span data-ttu-id="d944a-119">以下每个命令行都将编译 `in.cs` 并创建 `in.exe`：</span><span class="sxs-lookup"><span data-stu-id="d944a-119">Each of the following command lines will compile `in.cs`, creating `in.exe`:</span></span>  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d944a-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d944a-120">See also</span></span>

- [<span data-ttu-id="d944a-121">-target（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="d944a-121">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="d944a-122">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="d944a-122">C# Compiler Options</span></span>](./index.md)
