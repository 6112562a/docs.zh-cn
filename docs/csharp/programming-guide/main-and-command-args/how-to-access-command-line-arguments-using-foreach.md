---
title: 如何：使用 foreach 访问命令行参数 - C# 编程指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
ms.openlocfilehash: 79c798bb6ec16fc639d37defc40da5af770e5bba
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242427"
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="6f2a4-102">如何：使用 foreach 访问命令行参数（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="6f2a4-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="6f2a4-103">循环访问数组的另一种方法是使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 语句，如本例所示。</span><span class="sxs-lookup"><span data-stu-id="6f2a4-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="6f2a4-104">`foreach` 语句可用于循环访问数组、.NET Framework 集合类或任何实现 <xref:System.Collections.IEnumerable> 接口的类或结构。</span><span class="sxs-lookup"><span data-stu-id="6f2a4-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f2a4-105">在 Visual Studio 中运行应用程序时，可在[“项目设计器”->“调试”页](/visualstudio/ide/reference/debug-page-project-designer)中指定命令行参数。</span><span class="sxs-lookup"><span data-stu-id="6f2a4-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f2a4-106">示例</span><span class="sxs-lookup"><span data-stu-id="6f2a4-106">Example</span></span>  
 <span data-ttu-id="6f2a4-107">此示例演示如何使用 `foreach` 打印命令行参数。</span><span class="sxs-lookup"><span data-stu-id="6f2a4-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6f2a4-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="6f2a4-108">See Also</span></span>

- <xref:System.Array>  
- <xref:System.Collections>  
- [<span data-ttu-id="6f2a4-109">在命令行上使用 csc.exe 生成</span><span class="sxs-lookup"><span data-stu-id="6f2a4-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [<span data-ttu-id="6f2a4-110">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="6f2a4-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6f2a4-111">foreach, in</span><span class="sxs-lookup"><span data-stu-id="6f2a4-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
- [<span data-ttu-id="6f2a4-112">Main() 和命令行参数</span><span class="sxs-lookup"><span data-stu-id="6f2a4-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [<span data-ttu-id="6f2a4-113">如何：显示命令行参数</span><span class="sxs-lookup"><span data-stu-id="6f2a4-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
- [<span data-ttu-id="6f2a4-114">Main() 返回值</span><span class="sxs-lookup"><span data-stu-id="6f2a4-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
