---
title: 索引器 - C# 编程指南
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 5b135fee12ac5b78b41a657f2eb458ea104143fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923936"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="5d679-102">索引器（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="5d679-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="5d679-103">索引器允许类或结构的实例就像数组一样进行索引。</span><span class="sxs-lookup"><span data-stu-id="5d679-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="5d679-104">无需显式指定类型或实例成员，即可设置或检索索引值。</span><span class="sxs-lookup"><span data-stu-id="5d679-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="5d679-105">索引器类似于[属性](../classes-and-structs/properties.md)，不同之处在于它们的访问器需要使用参数。</span><span class="sxs-lookup"><span data-stu-id="5d679-105">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="5d679-106">以下示例定义了一个泛型类，其中包含用于赋值和检索值的简单 [get](../../language-reference/keywords/get.md) 和 [set](../../language-reference/keywords/set.md) 访问器方法。</span><span class="sxs-lookup"><span data-stu-id="5d679-106">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="5d679-107">`Program` 类创建了此类的一个实例，用于存储字符串。</span><span class="sxs-lookup"><span data-stu-id="5d679-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> <span data-ttu-id="5d679-108">有关更多示例，请参阅[相关部分](./index.md#BKMK_RelatedSections)。</span><span class="sxs-lookup"><span data-stu-id="5d679-108">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="5d679-109">表达式主体定义</span><span class="sxs-lookup"><span data-stu-id="5d679-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="5d679-110">索引器的 get 或 set 访问器包含一个用于返回或设置值的语句很常见。</span><span class="sxs-lookup"><span data-stu-id="5d679-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="5d679-111">为了支持这种情况，表达式主体成员提供了一种经过简化的语法。</span><span class="sxs-lookup"><span data-stu-id="5d679-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="5d679-112">自 C# 6 起，可以表达式主体成员的形式实现只读索引器，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="5d679-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="5d679-113">请注意，`=>` 引入了表达式主体，并未使用 `get` 关键字。</span><span class="sxs-lookup"><span data-stu-id="5d679-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="5d679-114">自 C# 7.0 起，get 和 set 访问器均可作为表达式主体成员实现。</span><span class="sxs-lookup"><span data-stu-id="5d679-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="5d679-115">在这种情况下，必须使用 `get` 和 `set` 关键字。</span><span class="sxs-lookup"><span data-stu-id="5d679-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="5d679-116">例如:</span><span class="sxs-lookup"><span data-stu-id="5d679-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="5d679-117">索引器概述</span><span class="sxs-lookup"><span data-stu-id="5d679-117">Indexers Overview</span></span>  
  
- <span data-ttu-id="5d679-118">使用索引器可以用类似于数组的方式为对象建立索引。</span><span class="sxs-lookup"><span data-stu-id="5d679-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="5d679-119">`get` 取值函数返回值。</span><span class="sxs-lookup"><span data-stu-id="5d679-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="5d679-120">`set` 取值函数分配值。</span><span class="sxs-lookup"><span data-stu-id="5d679-120">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="5d679-121">[this](../../language-reference/keywords/this.md) 关键字用于定义索引器。</span><span class="sxs-lookup"><span data-stu-id="5d679-121">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="5d679-122">[value](../../language-reference/keywords/value.md) 关键字用于定义 `set` 索引器所赋的值。</span><span class="sxs-lookup"><span data-stu-id="5d679-122">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="5d679-123">索引器不必根据整数值进行索引；由你决定如何定义特定的查找机制。</span><span class="sxs-lookup"><span data-stu-id="5d679-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="5d679-124">索引器可被重载。</span><span class="sxs-lookup"><span data-stu-id="5d679-124">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="5d679-125">索引器可以有多个形参，例如当访问二维数组时。</span><span class="sxs-lookup"><span data-stu-id="5d679-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="BKMK_RelatedSections"></a><span data-ttu-id="5d679-126">相关部分</span><span class="sxs-lookup"><span data-stu-id="5d679-126">Related Sections</span></span>  
  
- [<span data-ttu-id="5d679-127">使用索引器</span><span class="sxs-lookup"><span data-stu-id="5d679-127">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="5d679-128">接口中的索引器</span><span class="sxs-lookup"><span data-stu-id="5d679-128">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="5d679-129">属性与索引器之间的比较</span><span class="sxs-lookup"><span data-stu-id="5d679-129">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="5d679-130">限制访问器可访问性</span><span class="sxs-lookup"><span data-stu-id="5d679-130">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="5d679-131">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="5d679-131">C# Language Specification</span></span>  

<span data-ttu-id="5d679-132">有关详细信息，请参阅 [C# 语言规范](../../language-reference/language-specification/index.md)中的[索引器](~/_csharplang/spec/classes.md#indexers)。</span><span class="sxs-lookup"><span data-stu-id="5d679-132">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="5d679-133">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="5d679-133">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5d679-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="5d679-134">See also</span></span>

- [<span data-ttu-id="5d679-135">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="5d679-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5d679-136">属性</span><span class="sxs-lookup"><span data-stu-id="5d679-136">Properties</span></span>](../classes-and-structs/properties.md)
