---
title: 操作说明：通过指针访问成员 - C# 编程指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 153e5f1cfc1f4f8309a31ab58d699a273b417563
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546486"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a><span data-ttu-id="1b88d-102">如何：通过指针访问成员（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="1b88d-102">How to: access a member with a pointer (C# Programming Guide)</span></span>
<span data-ttu-id="1b88d-103">若要访问不安全上下文中声明的结构成员，可使用成员访问运算符，如以下示例所示，其中 `p` 是包含成员 `x` 的 [struct](../../../csharp/language-reference/keywords/struct.md) 的指针。</span><span class="sxs-lookup"><span data-stu-id="1b88d-103">To access a member of a struct that is declared in an unsafe context, you can use the member access operator as shown in the following example in which `p` is a pointer to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains a member `x`.</span></span>  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a><span data-ttu-id="1b88d-104">示例</span><span class="sxs-lookup"><span data-stu-id="1b88d-104">Example</span></span>  
 <span data-ttu-id="1b88d-105">此示例中，对包含 `x` 和 `y` 两个坐标的 [struct](../../../csharp/language-reference/keywords/struct.md) `CoOrds` 进行了声明和实例化。</span><span class="sxs-lookup"><span data-stu-id="1b88d-105">In this example, a [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, that contains the two coordinates `x` and `y` is declared and instantiated.</span></span> <span data-ttu-id="1b88d-106">通过使用成员访问运算符 `->` 和实例 `home` 的指针，为 `x` 和 `y` 赋值。</span><span class="sxs-lookup"><span data-stu-id="1b88d-106">By using the member access operator `->` and a pointer to the instance `home`, `x` and `y` are assigned values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b88d-107">请注意，表达式 `p->x` 等效于表达式 `(*p).x`，使用这两个表达式中任何一个获得的结果相同。</span><span class="sxs-lookup"><span data-stu-id="1b88d-107">Notice that the expression `p->x` is equivalent to the expression `(*p).x`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1b88d-108">请参阅</span><span class="sxs-lookup"><span data-stu-id="1b88d-108">See also</span></span>

- [<span data-ttu-id="1b88d-109">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="1b88d-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1b88d-110">指针表达式</span><span class="sxs-lookup"><span data-stu-id="1b88d-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="1b88d-111">指针类型</span><span class="sxs-lookup"><span data-stu-id="1b88d-111">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="1b88d-112">类型</span><span class="sxs-lookup"><span data-stu-id="1b88d-112">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="1b88d-113">unsafe</span><span class="sxs-lookup"><span data-stu-id="1b88d-113">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="1b88d-114">fixed 语句</span><span class="sxs-lookup"><span data-stu-id="1b88d-114">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="1b88d-115">stackalloc</span><span class="sxs-lookup"><span data-stu-id="1b88d-115">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
