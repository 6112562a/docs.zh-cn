---
title: -errorreport（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 27c7500a3d33ec17680896f21f0e44d98fee94c9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638465"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="a2bd0-102">-errorreport（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="a2bd0-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="a2bd0-103">此选项提供向 Microsoft 报告 C# 内部编译错误的简便方法。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2bd0-104">在 Windows Vista 和 Windows Server 2008 上，为 Visual Studio 制定的错误报告设置不会替代通过 Windows 错误报告 (WER) 制定的设置。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="a2bd0-105">WER 设置始终优先于 Visual Studio 错误报告设置。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2bd0-106">语法</span><span class="sxs-lookup"><span data-stu-id="a2bd0-106">Syntax</span></span>  
  
```console  
-errorreport:{ none | prompt | queue | send }  
```  
  
## <a name="arguments"></a><span data-ttu-id="a2bd0-107">自变量</span><span class="sxs-lookup"><span data-stu-id="a2bd0-107">Arguments</span></span>  
 <span data-ttu-id="a2bd0-108">**none**</span><span class="sxs-lookup"><span data-stu-id="a2bd0-108">**none**</span></span>  
 <span data-ttu-id="a2bd0-109">不收集有关内部编译器错误的报告，或不向 Microsoft 发送报告。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>  
  
 <span data-ttu-id="a2bd0-110">**提示**</span><span class="sxs-lookup"><span data-stu-id="a2bd0-110">**prompt**</span></span>  
 <span data-ttu-id="a2bd0-111">当您收到内部编译器错误时，提示您发送报告。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-111">Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="a2bd0-112">**提示**是在开发环境中编译应用程序时的默认值。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-112">**prompt** is the default when you compile an application in the development environment.</span></span>  
  
 <span data-ttu-id="a2bd0-113">**queue**</span><span class="sxs-lookup"><span data-stu-id="a2bd0-113">**queue**</span></span>  
 <span data-ttu-id="a2bd0-114">将错误报告排入队列。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-114">Queues the error report.</span></span> <span data-ttu-id="a2bd0-115">使用管理凭据登录时，可以报告自上次登录以来的任何故障。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-115">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="a2bd0-116">系统最多每 3 天 1 次提醒你发送故障报告。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-116">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="a2bd0-117">**排队**是在命令行编译应用程序时的默认值。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-117">**queue** is the default when you compile an application at the command line.</span></span>  
  
 <span data-ttu-id="a2bd0-118">**发送**</span><span class="sxs-lookup"><span data-stu-id="a2bd0-118">**send**</span></span>  
 <span data-ttu-id="a2bd0-119">自动向 Microsoft 发送内部编译器错误报告。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-119">Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="a2bd0-120">若要启用此选项，必须首先同意 Microsoft 数据收集策略。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-120">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="a2bd0-121">首次在计算机上指定 -errorreport:send 时，编译器消息将引导你访问包含 Microsoft 数据收集策略的网站。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-121">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>  
    
## <a name="remarks"></a><span data-ttu-id="a2bd0-122">备注</span><span class="sxs-lookup"><span data-stu-id="a2bd0-122">Remarks</span></span>  
 <span data-ttu-id="a2bd0-123">当编译器无法处理源代码文件时，会导致内部编译器错误 (ICE)。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-123">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="a2bd0-124">出现 ICE 时，编译器不会生成可用于修复代码的输出文件或任何有用的诊断。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-124">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>  
  
 <span data-ttu-id="a2bd0-125">在早期版本中，收到 ICE 时，我们欢迎你与 Microsoft 产品支持服务联系以报告问题。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-125">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="a2bd0-126">通过使用 -errorreport，可向 Visual C# 团队提供 ICE 信息。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-126">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="a2bd0-127">你的错误报告可以帮助改进未来的编译器版本。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-127">Your error reports can help improve future compiler releases.</span></span>  
  
 <span data-ttu-id="a2bd0-128">用户能否发送报告取决于计算机和用户策略权限。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-128">A user's ability to send reports depends on computer and user policy permissions.</span></span>  
  
 <span data-ttu-id="a2bd0-129">有关错误调试器的详细信息，请参阅 [Description of the Dr.Watson for Windows (Drwtsn32.exe) Tool](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool)（Windows Dr. Watson (Drwtsn32.exe) 工具的说明）。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-129">For more information about error debugger, see [Description of the Dr. Watson for Windows (Drwtsn32.exe) Tool](https://support.microsoft.com/help/308538/description-of-the-dr--watson-for-windows-drwtsn32-exe-tool).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="a2bd0-130">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="a2bd0-130">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="a2bd0-131">打开项目的“属性”页。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-131">Open the project's **Properties** page.</span></span> <span data-ttu-id="a2bd0-132">有关详细信息，请参阅 [“项目设计器”->“生成”页 (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-132">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="a2bd0-133">单击“生成”属性页。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-133">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="a2bd0-134">单击 **“高级”** 按钮。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-134">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="a2bd0-135">修改“内部编译器错误报告”属性。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-135">Modify the **Internal Compiler Error Reporting** property.</span></span>  
  
 <span data-ttu-id="a2bd0-136">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>。</span><span class="sxs-lookup"><span data-stu-id="a2bd0-136">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2bd0-137">请参阅</span><span class="sxs-lookup"><span data-stu-id="a2bd0-137">See also</span></span>

- [<span data-ttu-id="a2bd0-138">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="a2bd0-138">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
