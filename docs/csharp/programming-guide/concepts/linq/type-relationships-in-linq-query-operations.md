---
title: LINQ 查询操作中的类型关系 (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
ms.openlocfilehash: 42519a74be1bd6934bc7a3304d154321697d128c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591020"
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="45046-102">LINQ 查询操作中的类型关系 (C#)</span><span class="sxs-lookup"><span data-stu-id="45046-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="45046-103">若要有效编写查询，应了解完整的查询操作中的变量类型是如何全部彼此关联的。</span><span class="sxs-lookup"><span data-stu-id="45046-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="45046-104">如果了解这些关系，就能够更容易地理解文档中的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 示例和代码示例。</span><span class="sxs-lookup"><span data-stu-id="45046-104">If you understand these relationships you will more easily comprehend the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and code examples in the documentation.</span></span> <span data-ttu-id="45046-105">另外，还能了解在使用 `var` 隐式对变量进行类型化时的后台操作。</span><span class="sxs-lookup"><span data-stu-id="45046-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="45046-106">查询操作在数据源、查询本身及查询执行中是强类型化的。</span><span class="sxs-lookup"><span data-stu-id="45046-106">query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="45046-107">查询中变量的类型必须与数据源中元素的类型和 `foreach` 语句中迭代变量的类型兼容。</span><span class="sxs-lookup"><span data-stu-id="45046-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="45046-108">此强类型保证在编译时捕获类型错误，以便可以在用户遇到这些错误之前更正它们。</span><span class="sxs-lookup"><span data-stu-id="45046-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="45046-109">为了演示这些类型关系，下面的大多数示例对所有变量使用显式类型。</span><span class="sxs-lookup"><span data-stu-id="45046-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="45046-110">最后一个示例演示在利用使用 [var](../../../language-reference/keywords/var.md) 的隐式类型时，如何应用相同的原则。</span><span class="sxs-lookup"><span data-stu-id="45046-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="45046-111">不转换源数据的查询</span><span class="sxs-lookup"><span data-stu-id="45046-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="45046-112">下图演示不对数据执行转换的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects 查询操作。</span><span class="sxs-lookup"><span data-stu-id="45046-112">The following illustration shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="45046-113">源包含一个字符串序列，查询输出也是一个字符串序列。</span><span class="sxs-lookup"><span data-stu-id="45046-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 ![关系图显示 LINQ 查询中数据类型的关系。](./media/type-relationships-in-linq-query-operations/linq-query-data-type-relation.png)  
  
1. <span data-ttu-id="45046-115">数据源的类型参数决定范围变量的类型。</span><span class="sxs-lookup"><span data-stu-id="45046-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="45046-116">所选对象的类型决定查询变量的类型。</span><span class="sxs-lookup"><span data-stu-id="45046-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="45046-117">此处的 `name` 是一个字符串。</span><span class="sxs-lookup"><span data-stu-id="45046-117">Here `name` is a string.</span></span> <span data-ttu-id="45046-118">因此，查询变量是一个 `IEnumerable<string>`。</span><span class="sxs-lookup"><span data-stu-id="45046-118">Therefore, the query variable is an `IEnumerable<string>`.</span></span>  
  
3. <span data-ttu-id="45046-119">在 `foreach` 语句中循环访问查询变量。</span><span class="sxs-lookup"><span data-stu-id="45046-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="45046-120">因为查询变量是一个字符串序列，所以迭代变量也是一个字符串。</span><span class="sxs-lookup"><span data-stu-id="45046-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="45046-121">转换源数据的查询</span><span class="sxs-lookup"><span data-stu-id="45046-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="45046-122">下图演示对数据执行简单转换的 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 查询操作。</span><span class="sxs-lookup"><span data-stu-id="45046-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="45046-123">查询将一个 `Customer` 对象序列用作输入，并只选择结果中的 `Name` 属性。</span><span class="sxs-lookup"><span data-stu-id="45046-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="45046-124">因为 `Name` 是一个字符串，所以查询生成一个字符串序列作为输出。</span><span class="sxs-lookup"><span data-stu-id="45046-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 ![关系图显示转换数据类型的查询。](./media/type-relationships-in-linq-query-operations/linq-query-transform-data-type.png)  
  
1. <span data-ttu-id="45046-126">数据源的类型参数决定范围变量的类型。</span><span class="sxs-lookup"><span data-stu-id="45046-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2. <span data-ttu-id="45046-127">`select` 语句返回 `Name` 属性，而非完整的 `Customer` 对象。</span><span class="sxs-lookup"><span data-stu-id="45046-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="45046-128">因为 `Name` 是一个字符串，所以 `custNameQuery` 的类型参数是 `string`，而非 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="45046-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3. <span data-ttu-id="45046-129">因为 `custNameQuery` 是一个字符串序列，所以 `foreach` 循环的迭代变量也必须是 `string`。</span><span class="sxs-lookup"><span data-stu-id="45046-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="45046-130">下图演示稍微复杂的转换。</span><span class="sxs-lookup"><span data-stu-id="45046-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="45046-131">`select` 语句返回只捕获原始 `Customer` 对象的两个成员的匿名类型。</span><span class="sxs-lookup"><span data-stu-id="45046-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 ![关系图显示转换数据类型的更复杂的查询。](./media/type-relationships-in-linq-query-operations/linq-complex-query-transform-data-type.png)  
  
1. <span data-ttu-id="45046-133">数据源的类型参数始终为查询中范围变量的类型。</span><span class="sxs-lookup"><span data-stu-id="45046-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2. <span data-ttu-id="45046-134">因为 `select` 语句生成匿名类型，所以必须使用 `var` 隐式类型化查询变量。</span><span class="sxs-lookup"><span data-stu-id="45046-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3. <span data-ttu-id="45046-135">因为查询变量的类型是隐式的，所以 `foreach` 循环中的迭代变量也必须是隐式的。</span><span class="sxs-lookup"><span data-stu-id="45046-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="45046-136">让编译器推断类型信息</span><span class="sxs-lookup"><span data-stu-id="45046-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="45046-137">虽然需要了解查询操作中的类型关系，但是也可以选择让编译器执行全部工作。</span><span class="sxs-lookup"><span data-stu-id="45046-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="45046-138">关键字 [var](../../../language-reference/keywords/var.md) 可用于查询操作中的任何本地变量。</span><span class="sxs-lookup"><span data-stu-id="45046-138">The keyword [var](../../../language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="45046-139">下图与前面讨论的第二个示例相似。</span><span class="sxs-lookup"><span data-stu-id="45046-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="45046-140">但是，编译器为查询操作中的各个变量提供强类型。</span><span class="sxs-lookup"><span data-stu-id="45046-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 ![关系图显示具有隐式类型的类型流。](./media/type-relationships-in-linq-query-operations/linq-type-flow-implicit-typing.png)  
  
 <span data-ttu-id="45046-142">有关 `var` 的详细信息，请参阅[隐式类型本地变量](../../classes-and-structs/implicitly-typed-local-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="45046-142">For more information about `var`, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
