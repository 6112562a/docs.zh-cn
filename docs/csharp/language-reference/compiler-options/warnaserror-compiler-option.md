---
title: -warnaserror（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 7d43941629e933ac5a9e9c9d6a1388b6194f8d99
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503474"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="73ee5-102">-warnaserror（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="73ee5-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="73ee5-103">-warnaserror+ 选项将所有警告视为错误 </span><span class="sxs-lookup"><span data-stu-id="73ee5-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73ee5-104">语法</span><span class="sxs-lookup"><span data-stu-id="73ee5-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="73ee5-105">备注</span><span class="sxs-lookup"><span data-stu-id="73ee5-105">Remarks</span></span>  
 <span data-ttu-id="73ee5-106">通常报告为警告的消息被报告为错误，生成过程暂停（不生成任何输出文件）。</span><span class="sxs-lookup"><span data-stu-id="73ee5-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="73ee5-107">默认情况下，-warnaserror- 将生效，导致警告不会阻止生成输出文件  。</span><span class="sxs-lookup"><span data-stu-id="73ee5-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="73ee5-108">-warnaserror 与 -warnaserror+ 相同，会导致将警告视为错误   。</span><span class="sxs-lookup"><span data-stu-id="73ee5-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="73ee5-109">（可选）如果希望仅将一些特定警告视为错误，则可以指定视为错误的警告编号的逗号分隔列表。</span><span class="sxs-lookup"><span data-stu-id="73ee5-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span> <span data-ttu-id="73ee5-110">可以使用可为 null  的简写形式指定所有为 Null 性警告的集合。</span><span class="sxs-lookup"><span data-stu-id="73ee5-110">The set of all nullability warnings can be specified with the **nullable** shorthand.</span></span>
  
 <span data-ttu-id="73ee5-111">使用 [-warn](./warn-compiler-option.md) 指定想要编译器显示的警告等级。</span><span class="sxs-lookup"><span data-stu-id="73ee5-111">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="73ee5-112">使用 [-nowarn](./nowarn-compiler-option.md) 禁用某些警告。</span><span class="sxs-lookup"><span data-stu-id="73ee5-112">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="73ee5-113">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="73ee5-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="73ee5-114">打开项目的“属性”  页。</span><span class="sxs-lookup"><span data-stu-id="73ee5-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="73ee5-115">单击“生成”  属性页。</span><span class="sxs-lookup"><span data-stu-id="73ee5-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="73ee5-116">修改“将警告视为错误”  属性。</span><span class="sxs-lookup"><span data-stu-id="73ee5-116">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="73ee5-117">若要以编程方式设置此编译器选项，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>。</span><span class="sxs-lookup"><span data-stu-id="73ee5-117">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73ee5-118">示例</span><span class="sxs-lookup"><span data-stu-id="73ee5-118">Example</span></span>  
 <span data-ttu-id="73ee5-119">编译 `in.cs` 并使编译器不显示警告：</span><span class="sxs-lookup"><span data-stu-id="73ee5-119">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="73ee5-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="73ee5-120">See also</span></span>

- [<span data-ttu-id="73ee5-121">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="73ee5-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="73ee5-122">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="73ee5-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
