---
title: 可访问性域 - C# 参考
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 4a4319b03f3e0d7f9ec721e611b78c124a8a8ee5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713837"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="f5090-102">可访问域（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="f5090-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="f5090-103">成员的可访问域可指定成员可以引用哪些程序分区。</span><span class="sxs-lookup"><span data-stu-id="f5090-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="f5090-104">如果成员嵌套于其他类型中，则该成员的可访问域是由该成员的[可访问性级别](./accessibility-levels.md)和直接包含类型的可访问域这二者共同确定的。</span><span class="sxs-lookup"><span data-stu-id="f5090-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="f5090-105">顶级类型的可访问域至少是在其中进行声明的项目的程序文本。</span><span class="sxs-lookup"><span data-stu-id="f5090-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="f5090-106">也就是说，该域包含此项目的所有源文件。</span><span class="sxs-lookup"><span data-stu-id="f5090-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="f5090-107">嵌套类型的可访问域至少是在其中进行声明的类型的程序文本。</span><span class="sxs-lookup"><span data-stu-id="f5090-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="f5090-108">也就是说，域是类型的主题，其中包括所有嵌套类型。</span><span class="sxs-lookup"><span data-stu-id="f5090-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="f5090-109">嵌套类型的可访问域决不能超出包含类型的可访问域。</span><span class="sxs-lookup"><span data-stu-id="f5090-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="f5090-110">下例说明了这些概念。</span><span class="sxs-lookup"><span data-stu-id="f5090-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5090-111">示例</span><span class="sxs-lookup"><span data-stu-id="f5090-111">Example</span></span>  
 <span data-ttu-id="f5090-112">此示例包含一个顶级类型 `T1` 和两个嵌套类 `M1` 和 `M2`。</span><span class="sxs-lookup"><span data-stu-id="f5090-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="f5090-113">这两个类包含的字段具有不同的已声明可访问性。</span><span class="sxs-lookup"><span data-stu-id="f5090-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="f5090-114">在 `Main` 方法中，每条语句后跟注释以指示每个成员的可访问域。</span><span class="sxs-lookup"><span data-stu-id="f5090-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="f5090-115">请注意，试图引用不可访问成员的语句将被注释掉。如果想要查看通过引用不可访问成员引起的编译器错误，请一次删除一条注释。</span><span class="sxs-lookup"><span data-stu-id="f5090-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="f5090-116">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="f5090-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f5090-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="f5090-117">See also</span></span>

- [<span data-ttu-id="f5090-118">C# 参考</span><span class="sxs-lookup"><span data-stu-id="f5090-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f5090-119">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="f5090-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f5090-120">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="f5090-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="f5090-121">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="f5090-121">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="f5090-122">可访问性级别</span><span class="sxs-lookup"><span data-stu-id="f5090-122">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="f5090-123">对使用可访问性级别的限制</span><span class="sxs-lookup"><span data-stu-id="f5090-123">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="f5090-124">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="f5090-124">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="f5090-125">public</span><span class="sxs-lookup"><span data-stu-id="f5090-125">public</span></span>](./public.md)
- [<span data-ttu-id="f5090-126">专用</span><span class="sxs-lookup"><span data-stu-id="f5090-126">private</span></span>](./private.md)
- [<span data-ttu-id="f5090-127">受保护</span><span class="sxs-lookup"><span data-stu-id="f5090-127">protected</span></span>](./protected.md)
- [<span data-ttu-id="f5090-128">internal</span><span class="sxs-lookup"><span data-stu-id="f5090-128">internal</span></span>](./internal.md)
