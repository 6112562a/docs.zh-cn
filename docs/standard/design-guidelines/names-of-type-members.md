---
title: 类型成员的名称
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: a9cd531100057fbad4884a20e6e7db6ef94e7956
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709213"
---
# <a name="names-of-type-members"></a><span data-ttu-id="c2913-102">类型成员的名称</span><span class="sxs-lookup"><span data-stu-id="c2913-102">Names of Type Members</span></span>
<span data-ttu-id="c2913-103">类型由以下成员构成：方法、属性、事件、构造函数和字段。</span><span class="sxs-lookup"><span data-stu-id="c2913-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="c2913-104">以下各节介绍命名类型成员的准则。</span><span class="sxs-lookup"><span data-stu-id="c2913-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="c2913-105">方法的名称</span><span class="sxs-lookup"><span data-stu-id="c2913-105">Names of Methods</span></span>  
 <span data-ttu-id="c2913-106">方法是执行操作的方式，设计准则要求方法名称为谓词或谓词短语。</span><span class="sxs-lookup"><span data-stu-id="c2913-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="c2913-107">遵循此准则，还有利于区分方法名称与属性和类型名称，后者为名词或形容词性短语。</span><span class="sxs-lookup"><span data-stu-id="c2913-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="c2913-108">**✓ DO** 用谓词或谓词短语为方法命名。</span><span class="sxs-lookup"><span data-stu-id="c2913-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```csharp  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="c2913-109">属性的名称</span><span class="sxs-lookup"><span data-stu-id="c2913-109">Names of Properties</span></span>  
 <span data-ttu-id="c2913-110">与其他成员不同，应向属性给定名词性短语或形容词性名称。</span><span class="sxs-lookup"><span data-stu-id="c2913-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="c2913-111">这是因为属性是指数据，属性的名称应反映这一点。</span><span class="sxs-lookup"><span data-stu-id="c2913-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="c2913-112">属性名称总是采用帕斯卡大小写。</span><span class="sxs-lookup"><span data-stu-id="c2913-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="c2913-113">**✓ 正确做法** 使用名词、名词性短语或形容词为属性命名。</span><span class="sxs-lookup"><span data-stu-id="c2913-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="c2913-114">**X DO NOT** 拥有与“Get”方法同名的属性，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="c2913-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="c2913-115">此模式通常意味着该属性事实上是一种方法。</span><span class="sxs-lookup"><span data-stu-id="c2913-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="c2913-116">**✓**使用一个复数短语来描述集合中的项，而不是使用后跟 "List" 或 "collection" 的短语来命名集合属性。</span><span class="sxs-lookup"><span data-stu-id="c2913-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection".</span></span>  
  
 <span data-ttu-id="c2913-117">**✓ 正确做法** 用肯定性短语（`CanSeek` 而非 `CantSeek`）为布尔属性命名。</span><span class="sxs-lookup"><span data-stu-id="c2913-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="c2913-118">或者，还可以在布尔属性前面添加 "Is"、"Can" 或 "has" 前缀，但前提是在它添加值的位置。</span><span class="sxs-lookup"><span data-stu-id="c2913-118">Optionally, you can also prefix Boolean properties with "Is", "Can", or "Has", but only where it adds value.</span></span>  
  
 <span data-ttu-id="c2913-119">**✓ CONSIDER** 为属性提供与其类型相同的名称。</span><span class="sxs-lookup"><span data-stu-id="c2913-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="c2913-120">例如，以下属性可正确获取和设置名为 `Color` 的枚举值，因此属性名为 `Color`：</span><span class="sxs-lookup"><span data-stu-id="c2913-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```csharp  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="c2913-121">事件的名称</span><span class="sxs-lookup"><span data-stu-id="c2913-121">Names of Events</span></span>  
 <span data-ttu-id="c2913-122">事件始终指操作，可以是即将发生的，也可以是已经发生的。</span><span class="sxs-lookup"><span data-stu-id="c2913-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="c2913-123">因此，对于方法，事件用谓词命名，并用谓词时态指示引发事件的时间。</span><span class="sxs-lookup"><span data-stu-id="c2913-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="c2913-124">**✓ 正确做法** 用谓词或谓词短语为事件命名。</span><span class="sxs-lookup"><span data-stu-id="c2913-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="c2913-125">示例包括`Clicked`、`Painting` 和 `DroppedDown`。</span><span class="sxs-lookup"><span data-stu-id="c2913-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="c2913-126">**✓ 正确做法** 使用现在时和过去时，为事件名称赋予之前和之后的概念。</span><span class="sxs-lookup"><span data-stu-id="c2913-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="c2913-127">例如，在窗口关闭前引发的关闭事件可命名为 `Closing`，而在窗口关闭后后引发的关闭事件可命名为 `Closed`。</span><span class="sxs-lookup"><span data-stu-id="c2913-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="c2913-128">**X DO NOT** 使用“Before”或“After”前缀或后缀指示发生在事件前后。</span><span class="sxs-lookup"><span data-stu-id="c2913-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="c2913-129">请如上所示使用现在时和过去时。</span><span class="sxs-lookup"><span data-stu-id="c2913-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="c2913-130">**✓ 正确做法** 为事件处理程序（用作事件类型的委托）添加“EventHandler”后缀，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="c2913-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="c2913-131">**✓ 正确做法** 在事件处理程序中使用名为 `sender` 和 `e` 的两个参数。</span><span class="sxs-lookup"><span data-stu-id="c2913-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="c2913-132">sender 参数表示引发事件的对象。</span><span class="sxs-lookup"><span data-stu-id="c2913-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="c2913-133">sender 参数的类型通常是 `object`，即使可以使用更具体的类型。</span><span class="sxs-lookup"><span data-stu-id="c2913-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="c2913-134">**✓ 正确做法** 为事件参数类名称添加“EventArgs”后缀。</span><span class="sxs-lookup"><span data-stu-id="c2913-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="c2913-135">字段的名称</span><span class="sxs-lookup"><span data-stu-id="c2913-135">Names of Fields</span></span>  
 <span data-ttu-id="c2913-136">字段命名准则适用于静态公开字段和受保护的字段。</span><span class="sxs-lookup"><span data-stu-id="c2913-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="c2913-137">原则不涉及内部和专用字段，而[成员设计准则](../../../docs/standard/design-guidelines/member.md)不允许使用公开字段或受保护的实例字段。</span><span class="sxs-lookup"><span data-stu-id="c2913-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="c2913-138">**✓ 正确做法** 在字段名称中使用帕斯卡大小写。</span><span class="sxs-lookup"><span data-stu-id="c2913-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="c2913-139">**✓ 正确做法** 使用名词、名词性短语或形容词为字段命名。</span><span class="sxs-lookup"><span data-stu-id="c2913-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="c2913-140">**X DO NOT** 在字段名称中使用前缀。</span><span class="sxs-lookup"><span data-stu-id="c2913-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="c2913-141">例如，请勿使用“g_”或“s_”来指示静态字段。</span><span class="sxs-lookup"><span data-stu-id="c2913-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="c2913-142">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="c2913-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c2913-143">\*在 Pearson Education, Inc. 授权下，由 Addison-Wesley Professional 作为 Microsoft Windows 开发系列的一部分再版自 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)（Framework 设计准则：可重用 .NET 库的约定、惯例和模式第 2 版），由 Krzysztof Cwalina 和 Brad Abrams 发布于 2008 年 10 月 22 日。</span><span class="sxs-lookup"><span data-stu-id="c2913-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2913-144">另请参阅</span><span class="sxs-lookup"><span data-stu-id="c2913-144">See also</span></span>

- [<span data-ttu-id="c2913-145">框架设计指南</span><span class="sxs-lookup"><span data-stu-id="c2913-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="c2913-146">命名规则</span><span class="sxs-lookup"><span data-stu-id="c2913-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
