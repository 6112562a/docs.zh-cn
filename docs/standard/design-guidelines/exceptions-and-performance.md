---
title: 异常和性能
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: afa4e748599781a5979823320d8913ff5357d415
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741642"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="a393d-102">异常和性能</span><span class="sxs-lookup"><span data-stu-id="a393d-102">Exceptions and Performance</span></span>
<span data-ttu-id="a393d-103">一个常见的与异常相关的问题是，如果异常用于通常会失败的代码，则实现的性能将变得不可接受。</span><span class="sxs-lookup"><span data-stu-id="a393d-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="a393d-104">这确实是一个问题。</span><span class="sxs-lookup"><span data-stu-id="a393d-104">This is a valid concern.</span></span> <span data-ttu-id="a393d-105">当成员引发异常时，其性能可能会慢几个数量级。</span><span class="sxs-lookup"><span data-stu-id="a393d-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="a393d-106">但是，在严格遵守禁止使用错误代码的异常准则的同时，仍可能实现良好的性能。</span><span class="sxs-lookup"><span data-stu-id="a393d-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="a393d-107">本部分中描述了两种建议的模式。</span><span class="sxs-lookup"><span data-stu-id="a393d-107">Two patterns described in this section suggest ways to do this.</span></span>

 <span data-ttu-id="a393d-108">❌ 不使用错误代码，原因是异常可能会对性能产生负面影响。</span><span class="sxs-lookup"><span data-stu-id="a393d-108">❌ DO NOT use error codes because of concerns that exceptions might affect performance negatively.</span></span>

 <span data-ttu-id="a393d-109">为了提高性能，可以使用 Tester-Doer 模式或 Try-Parse 模式，如以下两部分所述。</span><span class="sxs-lookup"><span data-stu-id="a393d-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>

## <a name="tester-doer-pattern"></a><span data-ttu-id="a393d-110">Tester-Doer 模式</span><span class="sxs-lookup"><span data-stu-id="a393d-110">Tester-Doer Pattern</span></span>
 <span data-ttu-id="a393d-111">有时，通过将成员分成两部分，可以改善异常引发成员的性能。</span><span class="sxs-lookup"><span data-stu-id="a393d-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="a393d-112">让我们看看 <xref:System.Collections.Generic.ICollection%601> 接口的 <xref:System.Collections.Generic.ICollection%601.Add%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a393d-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 <span data-ttu-id="a393d-113">如果集合是只读的，则方法 `Add` 引发。</span><span class="sxs-lookup"><span data-stu-id="a393d-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="a393d-114">在通常预期方法调用会失败的情况下，这可能会导致性能问题。</span><span class="sxs-lookup"><span data-stu-id="a393d-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="a393d-115">优化此问题的方法之一是在尝试添加值之前测试集合是否可写。</span><span class="sxs-lookup"><span data-stu-id="a393d-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 <span data-ttu-id="a393d-116">用于测试条件的成员（在我们的示例中为属性 `IsReadOnly`）称为 "测试人员"。</span><span class="sxs-lookup"><span data-stu-id="a393d-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="a393d-117">用于执行可能引发的操作的成员（本示例中的 `Add` 方法）称为 doer。</span><span class="sxs-lookup"><span data-stu-id="a393d-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>

 <span data-ttu-id="a393d-118">✔️考虑在常见方案中可能会引发异常的成员的 Doer 模式，以避免与异常相关的性能问题。</span><span class="sxs-lookup"><span data-stu-id="a393d-118">✔️ CONSIDER the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

## <a name="try-parse-pattern"></a><span data-ttu-id="a393d-119">Try-Parse 模式</span><span class="sxs-lookup"><span data-stu-id="a393d-119">Try-Parse Pattern</span></span>
 <span data-ttu-id="a393d-120">对于性能极其敏感的 API，应使用比上一部分中介绍的 Tester-Doer 模式更快的模式。</span><span class="sxs-lookup"><span data-stu-id="a393d-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="a393d-121">该模式要求调整成员名称，以使明确定义的测试用例成为成员语义的一部分。</span><span class="sxs-lookup"><span data-stu-id="a393d-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="a393d-122">例如，<xref:System.DateTime> 定义一个 <xref:System.DateTime.Parse%2A> 方法，当字符串的分析失败时，该方法将引发异常。</span><span class="sxs-lookup"><span data-stu-id="a393d-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="a393d-123">它还定义了一个相应的 <xref:System.DateTime.TryParse%2A> 方法，该方法尝试进行分析，但如果分析不成功，则返回 false，并返回使用 `out` 参数成功分析的结果。</span><span class="sxs-lookup"><span data-stu-id="a393d-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 <span data-ttu-id="a393d-124">使用此模式时，务必要严格定义 try 功能。</span><span class="sxs-lookup"><span data-stu-id="a393d-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="a393d-125">如果在已妥善定义 try 的情况下，成员仍因某个原因失败，则该成员仍必须引发相应异常。</span><span class="sxs-lookup"><span data-stu-id="a393d-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>

 <span data-ttu-id="a393d-126">✔️考虑在常见方案中可能会引发异常的成员的试验分析模式，以避免与异常相关的性能问题。</span><span class="sxs-lookup"><span data-stu-id="a393d-126">✔️ CONSIDER the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

 <span data-ttu-id="a393d-127">✔️对实现此模式的方法使用前缀 "Try" 和 Boolean 返回类型。</span><span class="sxs-lookup"><span data-stu-id="a393d-127">✔️ DO use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>

 <span data-ttu-id="a393d-128">✔️使用 Try Parse 模式为每个成员提供异常引发成员。</span><span class="sxs-lookup"><span data-stu-id="a393d-128">✔️ DO provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>

 <span data-ttu-id="a393d-129">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="a393d-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="a393d-130">\*在 Pearson Education, Inc. 授权下，由 Addison-Wesley Professional 作为 Microsoft Windows 开发系列的一部分再版自 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)（Framework 设计准则：可重用 .NET 库的约定、惯例和模式第 2 版），由 Krzysztof Cwalina 和 Brad Abrams 发布于 2008 年 10 月 22 日。</span><span class="sxs-lookup"><span data-stu-id="a393d-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="a393d-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a393d-131">See also</span></span>

- [<span data-ttu-id="a393d-132">框架设计指南</span><span class="sxs-lookup"><span data-stu-id="a393d-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="a393d-133">异常的设计准则</span><span class="sxs-lookup"><span data-stu-id="a393d-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
