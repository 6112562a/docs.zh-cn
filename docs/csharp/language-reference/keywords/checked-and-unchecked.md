---
title: Checked 和 Unchecked - C# 参考
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: a3b1ef8e6d8e496eda74ab25b3fe17f8174bac11
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713720"
---
# <a name="checked-and-unchecked-c-reference"></a><span data-ttu-id="96a45-102">Checked 和 Unchecked（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="96a45-102">Checked and Unchecked (C# Reference)</span></span>
<span data-ttu-id="96a45-103">C# 语句既可以在已检查的上下文中执行，也可以在未检查的上下文中执行。</span><span class="sxs-lookup"><span data-stu-id="96a45-103">C# statements can execute in either checked or unchecked context.</span></span> <span data-ttu-id="96a45-104">在已检查的上下文中，算法溢出引发异常。</span><span class="sxs-lookup"><span data-stu-id="96a45-104">In a checked context, arithmetic overflow raises an exception.</span></span> <span data-ttu-id="96a45-105">在未选中的上下文中忽略算术溢出并将结果截断，方法是：丢弃任何不适应目标类型的高序位。</span><span class="sxs-lookup"><span data-stu-id="96a45-105">In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.</span></span>  
  
- <span data-ttu-id="96a45-106">[checked](checked.md) 指定已检查的上下文。</span><span class="sxs-lookup"><span data-stu-id="96a45-106">[checked](checked.md) Specify checked context.</span></span>  
  
- <span data-ttu-id="96a45-107">[unchecked](unchecked.md) 指定未检查的上下文。</span><span class="sxs-lookup"><span data-stu-id="96a45-107">[unchecked](unchecked.md) Specify unchecked context.</span></span>  
  
 <span data-ttu-id="96a45-108">下列操作受溢出检查的影响：</span><span class="sxs-lookup"><span data-stu-id="96a45-108">The following operations are affected by the overflow checking:</span></span>  
  
- <span data-ttu-id="96a45-109">表达式在整型上使用下列预定义运算符：</span><span class="sxs-lookup"><span data-stu-id="96a45-109">Expressions using the following predefined operators on integral types:</span></span>  
  
     <span data-ttu-id="96a45-110">`++`，`--`，一元 `-`，`+`，`-`，`*`，`/`</span><span class="sxs-lookup"><span data-stu-id="96a45-110">`++`, `--`, unary `-`, `+`, `-`, `*`, `/`</span></span>  
  
- <span data-ttu-id="96a45-111">整型类型之间或从 `float` 或 `double` 到整型类型的显式数字转换。</span><span class="sxs-lookup"><span data-stu-id="96a45-111">Explicit numeric conversions between integral types, or from `float` or `double` to an integral type.</span></span>  
  
 <span data-ttu-id="96a45-112">如果既未指定 `checked`，也未指定 `unchecked`，则非常量表达式（在运行时计算的表达式）的默认上下文将由 [-checked](../compiler-options/checked-compiler-option.md) 编译器选项的值定义。</span><span class="sxs-lookup"><span data-stu-id="96a45-112">If neither `checked` nor `unchecked` is specified, the default context for non-constant expressions (expressions that are evaluated at run time) is defined by the value of the [-checked](../compiler-options/checked-compiler-option.md) compiler option.</span></span> <span data-ttu-id="96a45-113">默认情况下，该选项的值未设置，且算术运算在未选中的上下文中执行。</span><span class="sxs-lookup"><span data-stu-id="96a45-113">By default the value of that option is unset and arithmetic operations are executed in an unchecked context.</span></span>
 
 <span data-ttu-id="96a45-114">对于常量表达式（可在编译时完全计算的表达式），将始终选中默认上下文。</span><span class="sxs-lookup"><span data-stu-id="96a45-114">For constant expressions (expressions that can be fully evaluated at compile time), the default context is always checked.</span></span> <span data-ttu-id="96a45-115">除非在未选中的上下文中显式放置常量表达式，否则在编译时间计算表达式过程中出现的溢出将导致编译时错误。</span><span class="sxs-lookup"><span data-stu-id="96a45-115">Unless a constant expression is explicitly placed in an unchecked context, overflows that occur during the compile-time evaluation of the expression cause compile-time errors.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="96a45-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="96a45-116">See also</span></span>

- [<span data-ttu-id="96a45-117">C# 参考</span><span class="sxs-lookup"><span data-stu-id="96a45-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="96a45-118">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="96a45-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="96a45-119">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="96a45-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="96a45-120">语句关键字</span><span class="sxs-lookup"><span data-stu-id="96a45-120">Statement Keywords</span></span>](statement-keywords.md)
