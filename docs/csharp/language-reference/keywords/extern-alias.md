---
title: extern 别名 - C# 参考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- alias_CSharpKeyword
helpviewer_keywords:
- extern alias keyword [C#]
- aliases [C#], extern keyword
- aliases, extern keyword
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
ms.openlocfilehash: 09d1247c51f0e600973840cfef2d3b396d9bf0d0
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520290"
---
# <a name="extern-alias-c-reference"></a><span data-ttu-id="cff2e-102">外部别名（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="cff2e-102">extern alias (C# Reference)</span></span>
<span data-ttu-id="cff2e-103">有时你可能不得不引用具有相同的完全限定类型名称的程序集的两个版本。</span><span class="sxs-lookup"><span data-stu-id="cff2e-103">You might have to reference two versions of assemblies that have the same fully-qualified type names.</span></span> <span data-ttu-id="cff2e-104">例如，可能需要在同一应用程序中使用某程序集的两个或多个版本。</span><span class="sxs-lookup"><span data-stu-id="cff2e-104">For example, you might have to use two or more versions of an assembly in the same application.</span></span> <span data-ttu-id="cff2e-105">通过使用外部程序集别名，可在别名命名的根级别命名空间内包装每个程序集的命名空间，使其能够在同一文件中使用。</span><span class="sxs-lookup"><span data-stu-id="cff2e-105">By using an external assembly alias, the namespaces from each assembly can be wrapped inside root-level namespaces named by the alias, which enables them to be used in the same file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cff2e-106">[外部](./extern.md)关键字还被用作方法修饰符，用于声明在非托管代码中编写的方法。</span><span class="sxs-lookup"><span data-stu-id="cff2e-106">The [extern](./extern.md) keyword is also used as a method modifier, declaring a method written in unmanaged code.</span></span>  
  
 <span data-ttu-id="cff2e-107">若要引用具有相同的完全限定类型名称的两个程序集，必须在命令提示符处指定别名，如下所示：</span><span class="sxs-lookup"><span data-stu-id="cff2e-107">To reference two assemblies with the same fully-qualified type names, an alias must be specified at a command prompt, as follows:</span></span>  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 <span data-ttu-id="cff2e-108">这将创建外部别名 `GridV1` 和 `GridV2`。</span><span class="sxs-lookup"><span data-stu-id="cff2e-108">This creates the external aliases `GridV1` and `GridV2`.</span></span> <span data-ttu-id="cff2e-109">若要从程序中使用这些别名，请通过使用 `extern` 关键字引用它们。</span><span class="sxs-lookup"><span data-stu-id="cff2e-109">To use these aliases from within a program, reference them by using the `extern` keyword.</span></span> <span data-ttu-id="cff2e-110">例如:</span><span class="sxs-lookup"><span data-stu-id="cff2e-110">For example:</span></span>  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 <span data-ttu-id="cff2e-111">每个外部别名声明都会引入与全局命名空间并行（但不位于其中）的额外根级别命名空间。</span><span class="sxs-lookup"><span data-stu-id="cff2e-111">Each extern alias declaration introduces an additional root-level namespace that parallels (but does not lie within) the global namespace.</span></span> <span data-ttu-id="cff2e-112">因此，可以使用其完全限定的名称（根植于相应的命名空间别名中）无歧义地引用每个程序集的类型。</span><span class="sxs-lookup"><span data-stu-id="cff2e-112">Thus types from each assembly can be referred to without ambiguity by using their fully qualified name, rooted in the appropriate namespace-alias.</span></span>  
  
 <span data-ttu-id="cff2e-113">在上一示例中，`GridV1::Grid` 是 `grid.dll` 中的网格控件，`GridV2::Grid` 是 `grid20.dll` 中的网格控件。</span><span class="sxs-lookup"><span data-stu-id="cff2e-113">In the previous example, `GridV1::Grid` would be the grid control from `grid.dll`, and `GridV2::Grid` would be the grid control from `grid20.dll`.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="cff2e-114">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="cff2e-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cff2e-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="cff2e-115">See also</span></span>

- [<span data-ttu-id="cff2e-116">C# 参考</span><span class="sxs-lookup"><span data-stu-id="cff2e-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cff2e-117">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="cff2e-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cff2e-118">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="cff2e-118">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="cff2e-119">::运算符</span><span class="sxs-lookup"><span data-stu-id="cff2e-119">:: Operator</span></span>](../operators/namespace-alias-qualifier.md)
- [<span data-ttu-id="cff2e-120">-reference（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="cff2e-120">-reference (C# Compiler Options)</span></span>](../compiler-options/reference-compiler-option.md)
