---
title: 可访问性级别 - C# 参考
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 26fbc2a6d86aead537465c304146630f8bcd3ad4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713816"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="30704-102">可访问性级别（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="30704-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="30704-103">使用访问修饰符 `public`、`protected`、`internal` 或 `private`，为成员指定以下声明的可访问性级别之一。</span><span class="sxs-lookup"><span data-stu-id="30704-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="30704-104">声明的可访问性</span><span class="sxs-lookup"><span data-stu-id="30704-104">Declared accessibility</span></span>|<span data-ttu-id="30704-105">含义</span><span class="sxs-lookup"><span data-stu-id="30704-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="30704-106">访问不受限制。</span><span class="sxs-lookup"><span data-stu-id="30704-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="30704-107">访问限于包含类或派生自包含类的类型。</span><span class="sxs-lookup"><span data-stu-id="30704-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="30704-108">访问限于当前程序集。</span><span class="sxs-lookup"><span data-stu-id="30704-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="30704-109">访问限于当前程序集或派生自包含类的类型。</span><span class="sxs-lookup"><span data-stu-id="30704-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="30704-110">访问限于包含类。</span><span class="sxs-lookup"><span data-stu-id="30704-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="30704-111">访问限于包含类或当前程序集中派生自包含类的类型。</span><span class="sxs-lookup"><span data-stu-id="30704-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="30704-112">自 C# 7.2 之后可用。</span><span class="sxs-lookup"><span data-stu-id="30704-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="30704-113">除使用 `protected internal` 或`private protected` 组合的情况外，一个成员或类型仅允许一个访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="30704-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="30704-114">命名空间中不允许出现访问修饰符。</span><span class="sxs-lookup"><span data-stu-id="30704-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="30704-115">命名空间没有任何访问限制。</span><span class="sxs-lookup"><span data-stu-id="30704-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="30704-116">根据出现成员声明的上下文，仅允许某些声明的可访问性。</span><span class="sxs-lookup"><span data-stu-id="30704-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="30704-117">如果未在成员声明中指定访问修饰符，则将使用默认可访问性。</span><span class="sxs-lookup"><span data-stu-id="30704-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="30704-118">未嵌套在其他类型中的顶级类型只能具有 `internal` 或 `public` 可访问性。</span><span class="sxs-lookup"><span data-stu-id="30704-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="30704-119">这些类型的默认可访问性为 `internal`。</span><span class="sxs-lookup"><span data-stu-id="30704-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="30704-120">作为其他类型的成员的嵌套类型可以具有如下表所示的声明的可访问性。</span><span class="sxs-lookup"><span data-stu-id="30704-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="30704-121">成员</span><span class="sxs-lookup"><span data-stu-id="30704-121">Members of</span></span>|<span data-ttu-id="30704-122">默认成员可访问性</span><span class="sxs-lookup"><span data-stu-id="30704-122">Default member accessibility</span></span>|<span data-ttu-id="30704-123">允许的成员的声明的可访问性</span><span class="sxs-lookup"><span data-stu-id="30704-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="30704-124">None</span><span class="sxs-lookup"><span data-stu-id="30704-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="30704-125">None</span><span class="sxs-lookup"><span data-stu-id="30704-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="30704-126">嵌套类型的可访问性依赖于它的[可访问域](./accessibility-domain.md)，该域是由已声明的成员可访问性和直接包含类型的可访问域这二者共同确定的。</span><span class="sxs-lookup"><span data-stu-id="30704-126">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="30704-127">但是，嵌套类型的可访问域不能超出包含类型的可访问域。</span><span class="sxs-lookup"><span data-stu-id="30704-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="30704-128">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="30704-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="30704-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="30704-129">See also</span></span>

- [<span data-ttu-id="30704-130">C# 参考</span><span class="sxs-lookup"><span data-stu-id="30704-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="30704-131">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="30704-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="30704-132">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="30704-132">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="30704-133">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="30704-133">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="30704-134">可访问域</span><span class="sxs-lookup"><span data-stu-id="30704-134">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="30704-135">对使用可访问性级别的限制</span><span class="sxs-lookup"><span data-stu-id="30704-135">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="30704-136">访问修饰符</span><span class="sxs-lookup"><span data-stu-id="30704-136">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="30704-137">public</span><span class="sxs-lookup"><span data-stu-id="30704-137">public</span></span>](./public.md)
- [<span data-ttu-id="30704-138">专用</span><span class="sxs-lookup"><span data-stu-id="30704-138">private</span></span>](./private.md)
- [<span data-ttu-id="30704-139">受保护</span><span class="sxs-lookup"><span data-stu-id="30704-139">protected</span></span>](./protected.md)
- [<span data-ttu-id="30704-140">internal</span><span class="sxs-lookup"><span data-stu-id="30704-140">internal</span></span>](./internal.md)
