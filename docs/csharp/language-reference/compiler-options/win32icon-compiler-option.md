---
title: -win32icon（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 7bc7da8121ec1190908d9b94fc7c987f9888c020
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59317442"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="64471-102">-win32icon（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="64471-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="64471-103">-win32icon 选项在输出文件中插入 .ico 文件，为输出文件赋予其在文件资源管理器中所需的外观。</span><span class="sxs-lookup"><span data-stu-id="64471-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64471-104">语法</span><span class="sxs-lookup"><span data-stu-id="64471-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="64471-105">自变量</span><span class="sxs-lookup"><span data-stu-id="64471-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="64471-106">想向输出文件添加的 .ico 文件。</span><span class="sxs-lookup"><span data-stu-id="64471-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64471-107">备注</span><span class="sxs-lookup"><span data-stu-id="64471-107">Remarks</span></span>  
 <span data-ttu-id="64471-108">可以使用[资源编译器](/windows/desktop/menurc/resource-compiler)创建的 .ico 文件。</span><span class="sxs-lookup"><span data-stu-id="64471-108">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="64471-109">在编译 Visual C++ 程序时会调用资源编译器；.ico 文件是从 .rc 文件创建的。</span><span class="sxs-lookup"><span data-stu-id="64471-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="64471-110">请参阅 [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md)（引用）或 [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md)（附加）.NET Framework 资源文件。</span><span class="sxs-lookup"><span data-stu-id="64471-110">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="64471-111">请参阅 [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) 导入 .res 文件。</span><span class="sxs-lookup"><span data-stu-id="64471-111">See [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="64471-112">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="64471-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="64471-113">打开项目的“属性”页。</span><span class="sxs-lookup"><span data-stu-id="64471-113">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="64471-114">单击“应用程序”属性页。</span><span class="sxs-lookup"><span data-stu-id="64471-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="64471-115">修改“应用程序图标”属性。</span><span class="sxs-lookup"><span data-stu-id="64471-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="64471-116">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>。</span><span class="sxs-lookup"><span data-stu-id="64471-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64471-117">示例</span><span class="sxs-lookup"><span data-stu-id="64471-117">Example</span></span>  
 <span data-ttu-id="64471-118">编译 `in.cs` 并附加 .ico 文件 `rf.ico` 以生成 `in.exe`：</span><span class="sxs-lookup"><span data-stu-id="64471-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="64471-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="64471-119">See also</span></span>

- [<span data-ttu-id="64471-120">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="64471-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="64471-121">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="64471-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
