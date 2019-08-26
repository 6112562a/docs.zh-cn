---
title: -define（C# 编译器选项）
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: cb9de387b319ff4b81dcd1ccc37f04d8b6b3123a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924801"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="82dfb-102">-define（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="82dfb-102">-define (C# Compiler Options)</span></span>
<span data-ttu-id="82dfb-103">-define 选项将 `name` 定义为程序中所有源代码文件的符号  。</span><span class="sxs-lookup"><span data-stu-id="82dfb-103">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82dfb-104">语法</span><span class="sxs-lookup"><span data-stu-id="82dfb-104">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="82dfb-105">自变量</span><span class="sxs-lookup"><span data-stu-id="82dfb-105">Arguments</span></span>  
 <span data-ttu-id="82dfb-106">`name`， `name2`</span><span class="sxs-lookup"><span data-stu-id="82dfb-106">`name`, `name2`</span></span>  
 <span data-ttu-id="82dfb-107">一个或多个要定义的符号的名称。</span><span class="sxs-lookup"><span data-stu-id="82dfb-107">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82dfb-108">备注</span><span class="sxs-lookup"><span data-stu-id="82dfb-108">Remarks</span></span>  
 <span data-ttu-id="82dfb-109">-define 选项具有与使用 [#define](../preprocessor-directives/preprocessor-define.md) 预处理器指令相同的效果，但编译器选项对项目中的所有文件都有效  。</span><span class="sxs-lookup"><span data-stu-id="82dfb-109">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="82dfb-110">符号在源文件中保持已定义状态，直到源文件中的 [#undef](../preprocessor-directives/preprocessor-undef.md) 指令删除该定义。</span><span class="sxs-lookup"><span data-stu-id="82dfb-110">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="82dfb-111">使用 -define 选项时，一个文件中的 `#undef` 指令不影响项目中其他的源代码文件。</span><span class="sxs-lookup"><span data-stu-id="82dfb-111">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="82dfb-112">可以将由此选项创建的符号同 [#if](../preprocessor-directives/preprocessor-if.md)、[#else](../preprocessor-directives/preprocessor-else.md)、[#elif](../preprocessor-directives/preprocessor-elif.md) 和 [#endif](../preprocessor-directives/preprocessor-endif.md) 一起使用，对源文件进行条件编译。</span><span class="sxs-lookup"><span data-stu-id="82dfb-112">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="82dfb-113">-d 是 -define 的缩写形式   。</span><span class="sxs-lookup"><span data-stu-id="82dfb-113">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="82dfb-114">通过使用分号或逗号分隔符号名称，可用 -define 定义多个符号  。</span><span class="sxs-lookup"><span data-stu-id="82dfb-114">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="82dfb-115">例如:</span><span class="sxs-lookup"><span data-stu-id="82dfb-115">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="82dfb-116">C# 编译器本身不定义源代码中使用的符号或宏；所有符号定义必须都是用户定义的。</span><span class="sxs-lookup"><span data-stu-id="82dfb-116">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82dfb-117">同 C++ 等语言一样，C# `#define` 不允许为符号赋值。</span><span class="sxs-lookup"><span data-stu-id="82dfb-117">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="82dfb-118">例如，`#define` 不能用于创建宏或定义常数。</span><span class="sxs-lookup"><span data-stu-id="82dfb-118">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="82dfb-119">如果需要定义一个常数，请使用 `enum` 变量。</span><span class="sxs-lookup"><span data-stu-id="82dfb-119">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="82dfb-120">若要创建 C++ 风格的宏，请考虑泛型等替代项。</span><span class="sxs-lookup"><span data-stu-id="82dfb-120">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="82dfb-121">由于宏非常容易出错，所以 C# 不允许使用宏，但提供了更安全的替代项。</span><span class="sxs-lookup"><span data-stu-id="82dfb-121">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="82dfb-122">在 Visual Studio 开发环境中设置此编译器选项</span><span class="sxs-lookup"><span data-stu-id="82dfb-122">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="82dfb-123">打开项目的“属性”  页。</span><span class="sxs-lookup"><span data-stu-id="82dfb-123">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="82dfb-124">在“生成”选项卡上，键入要在“条件编译符号”框中定义的符号   。</span><span class="sxs-lookup"><span data-stu-id="82dfb-124">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="82dfb-125">例如，如果使用以下代码示例，只需在文本框中键入 `xx`。</span><span class="sxs-lookup"><span data-stu-id="82dfb-125">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="82dfb-126">有关如何以编程方式设置此编译器选项的信息，请参阅 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>。</span><span class="sxs-lookup"><span data-stu-id="82dfb-126">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82dfb-127">示例</span><span class="sxs-lookup"><span data-stu-id="82dfb-127">Example</span></span>  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="82dfb-128">请参阅</span><span class="sxs-lookup"><span data-stu-id="82dfb-128">See also</span></span>

- [<span data-ttu-id="82dfb-129">C# 编译器选项</span><span class="sxs-lookup"><span data-stu-id="82dfb-129">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="82dfb-130">管理项目和解决方案属性</span><span class="sxs-lookup"><span data-stu-id="82dfb-130">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
