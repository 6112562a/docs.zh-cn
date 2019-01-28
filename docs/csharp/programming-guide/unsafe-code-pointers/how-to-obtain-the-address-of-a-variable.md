---
title: 如何：获取变量的地址 - C# 编程指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: cba33803c31ccc144479ad3e7b073ea7057495d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490553"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="d8920-102">如何：获取变量的地址（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="d8920-102">How to: obtain the address of a variable (C# Programming Guide)</span></span>

<span data-ttu-id="d8920-103">若要获取计算结果为固定变量的一元表达式的地址，请使用 address-of 运算符 `&`：</span><span class="sxs-lookup"><span data-stu-id="d8920-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator `&`:</span></span>  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="d8920-104">address-of 运算符只适用于变量。</span><span class="sxs-lookup"><span data-stu-id="d8920-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="d8920-105">如果变量是可移动变量，则可以使用[固定语句](../../../csharp/language-reference/keywords/fixed-statement.md)临时固定变量，再获取其地址。</span><span class="sxs-lookup"><span data-stu-id="d8920-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="d8920-106">由你负责确保变量已初始化。</span><span class="sxs-lookup"><span data-stu-id="d8920-106">It's your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="d8920-107">如果未初始化变量，编译器不会发出错误消息。</span><span class="sxs-lookup"><span data-stu-id="d8920-107">The compiler doesn't issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="d8920-108">你也无法获取常量或值的地址。</span><span class="sxs-lookup"><span data-stu-id="d8920-108">You can't get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8920-109">示例</span><span class="sxs-lookup"><span data-stu-id="d8920-109">Example</span></span>  
 <span data-ttu-id="d8920-110">在此示例中，已声明一个指向 `int` 和 `p` 的指针，并向其赋予了整型变量 `number` 的地址。</span><span class="sxs-lookup"><span data-stu-id="d8920-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="d8920-111">向 `*p` 赋值后导致初始化变量 `number`。</span><span class="sxs-lookup"><span data-stu-id="d8920-111">The variable `number` is initialized as a result of the assignment to `*p`.</span></span> <span data-ttu-id="d8920-112">如果向此赋值语句添加注释，将删除变量 `number` 的初始化，但不会产生任何编译时错误。</span><span class="sxs-lookup"><span data-stu-id="d8920-112">If you comment out this assignment statement, the initialization of the variable `number` is removed, but no compile-time error is issued.</span></span>  

> [!NOTE]
> <span data-ttu-id="d8920-113">使用 [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) 编译器选项编译此示例。</span><span class="sxs-lookup"><span data-stu-id="d8920-113">Compile this example with the [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="d8920-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="d8920-114">See also</span></span>

- [<span data-ttu-id="d8920-115">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="d8920-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d8920-116">指针表达式</span><span class="sxs-lookup"><span data-stu-id="d8920-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="d8920-117">指针类型</span><span class="sxs-lookup"><span data-stu-id="d8920-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="d8920-118">类型</span><span class="sxs-lookup"><span data-stu-id="d8920-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="d8920-119">unsafe</span><span class="sxs-lookup"><span data-stu-id="d8920-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="d8920-120">fixed 语句</span><span class="sxs-lookup"><span data-stu-id="d8920-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="d8920-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="d8920-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
