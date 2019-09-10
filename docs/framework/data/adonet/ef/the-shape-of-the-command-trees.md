---
title: 命令目录树的形状
ms.date: 03/30/2017
ms.assetid: 2215585e-ca47-45f8-98d4-8cb982f8c1d3
ms.openlocfilehash: 8368354049a77a56a5aa54ab500619576f41b0dc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854262"
---
# <a name="the-shape-of-the-command-trees"></a><span data-ttu-id="23919-102">命令目录树的形状</span><span class="sxs-lookup"><span data-stu-id="23919-102">The Shape of the Command Trees</span></span>

<span data-ttu-id="23919-103">SQL 生成模块负责生成基于给定输入查询命令目录树表达式的后端特定 SQL 查询。</span><span class="sxs-lookup"><span data-stu-id="23919-103">The SQL generation module is responsible for generating a backend specific SQL query based on a given input query command tree expression.</span></span> <span data-ttu-id="23919-104">本节讨论查询命令目录树的特征、属性和结构。</span><span class="sxs-lookup"><span data-stu-id="23919-104">This section discusses the characteristics, properties, and structure of the query command trees.</span></span>

## <a name="query-command-trees-overview"></a><span data-ttu-id="23919-105">查询命令目录树概述</span><span class="sxs-lookup"><span data-stu-id="23919-105">Query Command Trees Overview</span></span>

<span data-ttu-id="23919-106">查询命令目录树是查询的对象模型表示形式。</span><span class="sxs-lookup"><span data-stu-id="23919-106">A query command tree is an object model representation of a query.</span></span> <span data-ttu-id="23919-107">查询命令目录树有两个用途：</span><span class="sxs-lookup"><span data-stu-id="23919-107">Query command trees serve two purposes:</span></span>

- <span data-ttu-id="23919-108">表示针对实体框架指定的输入查询。</span><span class="sxs-lookup"><span data-stu-id="23919-108">To express an input query that is specified against the Entity Framework.</span></span>

- <span data-ttu-id="23919-109">表示为提供程序给定的输出查询并描述针对后端的查询。</span><span class="sxs-lookup"><span data-stu-id="23919-109">To express an output query that is given to a provider and describes a query against the backend.</span></span>

<span data-ttu-id="23919-110">查询命令目录树支持比符合 SQL:1999 的查询更丰富的语义，包括支持使用嵌套集合和类型操作（如检查一个实体是否属于某个特定类型或基于类型筛选集）。</span><span class="sxs-lookup"><span data-stu-id="23919-110">Query command trees support richer semantics than SQL:1999 compliant queries, including support for working with nested collections and type operations, like checking whether an entity is of a particular type, or filtering sets based on a type.</span></span>

<span data-ttu-id="23919-111">DBQueryCommandTree.Query 属性是用于描述查询逻辑的表达式树的根。</span><span class="sxs-lookup"><span data-stu-id="23919-111">The DBQueryCommandTree.Query property is the root of the expression tree that describes the query logic.</span></span> <span data-ttu-id="23919-112">DBQueryCommandTree.Parameters 属性包含查询中使用的参数的列表。</span><span class="sxs-lookup"><span data-stu-id="23919-112">The DBQueryCommandTree.Parameters property contains a list of parameters that are used in the query.</span></span> <span data-ttu-id="23919-113">表达式树由 DbExpression 对象组成。</span><span class="sxs-lookup"><span data-stu-id="23919-113">The expression tree is composed of DbExpression objects.</span></span>

<span data-ttu-id="23919-114">DbExpression 对象表示某个计算。</span><span class="sxs-lookup"><span data-stu-id="23919-114">A DbExpression object represents some computation.</span></span> <span data-ttu-id="23919-115">用于编写查询表达式的实体框架提供多种类型的表达式，这些表达式包括常量、变量、函数、构造函数和筛选器联接等标准关系运算符。</span><span class="sxs-lookup"><span data-stu-id="23919-115">Several kinds of expressions are provided by the Entity Framework for composing query expressions, including constants, variables, functions, constructors, and standard relational operators like filter and join.</span></span> <span data-ttu-id="23919-116">每个 DbExpression 对象都有一个 ResultType 属性，该属性表示该表达式生成的结果的类型。</span><span class="sxs-lookup"><span data-stu-id="23919-116">Every DbExpression object has a ResultType property that represents the type of the result produced by that expression.</span></span> <span data-ttu-id="23919-117">此类型表示为 TypeUsage。</span><span class="sxs-lookup"><span data-stu-id="23919-117">This type is expressed as a TypeUsage.</span></span>

## <a name="shapes-of-the-output-query-command-tree"></a><span data-ttu-id="23919-118">输出查询命令目录树的形状</span><span class="sxs-lookup"><span data-stu-id="23919-118">Shapes of the Output Query Command Tree</span></span>

<span data-ttu-id="23919-119">输出查询命令目录树紧密表示关系 (SQL) 查询，并遵循比应用于查询命令目录树的规则更严格的规则。</span><span class="sxs-lookup"><span data-stu-id="23919-119">Output query command trees closely represent relational (SQL) queries and adhere to much stricter rules than those that apply to query command trees.</span></span> <span data-ttu-id="23919-120">它们通常包含易于转换为 SQL 的构造。</span><span class="sxs-lookup"><span data-stu-id="23919-120">They typically contain constructs that are easily translated to SQL.</span></span>

<span data-ttu-id="23919-121">输入命令目录树是针对概念模型表示的，此模型支持导航属性、实体间的关联以及继承。</span><span class="sxs-lookup"><span data-stu-id="23919-121">Input command trees are expressed against the conceptual model, which supports navigation properties, associations among entities, and inheritance.</span></span> <span data-ttu-id="23919-122">输出命令目录树是针对存储模型表示的。</span><span class="sxs-lookup"><span data-stu-id="23919-122">Output command trees are expressed against the storage model.</span></span> <span data-ttu-id="23919-123">输入命令目录树允许你投影嵌套集合，而输出命令目录树不允许你这样做。</span><span class="sxs-lookup"><span data-stu-id="23919-123">Input command trees allow you to project nested collections, but output command trees do not.</span></span>

<span data-ttu-id="23919-124">输出查询命令目录树是使用 DbExpression 对象的子集生成的，并且对该子集中的一些表达式的使用会受到限制。</span><span class="sxs-lookup"><span data-stu-id="23919-124">Output query command trees are built using a subset of the available DbExpression objects and even some expressions in that subset have restricted usage.</span></span>

<span data-ttu-id="23919-125">输出命令目录树中不存在诸如检查一个给定表达式是否属于某个特定类型或检查是否基于某个类型筛选集这样的类型操作。</span><span class="sxs-lookup"><span data-stu-id="23919-125">Type operations, like checking whether a given expression is of a particular type or filtering sets based on a type, are not present in output command trees.</span></span>

<span data-ttu-id="23919-126">在输出命令目录树中，只有返回布尔值的表达式才用于投影，并且仅用于需要谓词的表达式中的谓词（如筛选语句或 Case 语句）。</span><span class="sxs-lookup"><span data-stu-id="23919-126">In output command trees, only expressions that return Boolean values are used for projections and only for predicates in expressions requiring a predicate, like a filter or a case statement.</span></span>

<span data-ttu-id="23919-127">输出查询命令目录树的根是一个 DbProjectExpression 对象。</span><span class="sxs-lookup"><span data-stu-id="23919-127">The root of an output query command trees is a DbProjectExpression object.</span></span>

### <a name="expression-types-not-present-in-output-query-command-trees"></a><span data-ttu-id="23919-128">输出查询命令目录树中不存在表达式类型</span><span class="sxs-lookup"><span data-stu-id="23919-128">Expression Types Not Present in Output Query Command Trees</span></span>

<span data-ttu-id="23919-129">下列表达式类型在输出查询命令目录树中无效，并且提供程序无需处理这些类型：</span><span class="sxs-lookup"><span data-stu-id="23919-129">The following expression types are not valid in an output query command tree and do not need to be handled by providers:</span></span>

- <span data-ttu-id="23919-130">DbDerefExpression</span><span class="sxs-lookup"><span data-stu-id="23919-130">DbDerefExpression</span></span>

- <span data-ttu-id="23919-131">DbEntityRefExpression</span><span class="sxs-lookup"><span data-stu-id="23919-131">DbEntityRefExpression</span></span>

- <span data-ttu-id="23919-132">DbRefKeyExpression</span><span class="sxs-lookup"><span data-stu-id="23919-132">DbRefKeyExpression</span></span>

- <span data-ttu-id="23919-133">DbIsOfExpression</span><span class="sxs-lookup"><span data-stu-id="23919-133">DbIsOfExpression</span></span>

- <span data-ttu-id="23919-134">DbOfTypeExpression</span><span class="sxs-lookup"><span data-stu-id="23919-134">DbOfTypeExpression</span></span>

- <span data-ttu-id="23919-135">DbRefExpression</span><span class="sxs-lookup"><span data-stu-id="23919-135">DbRefExpression</span></span>

- <span data-ttu-id="23919-136">DbRelationshipNavigationExpression</span><span class="sxs-lookup"><span data-stu-id="23919-136">DbRelationshipNavigationExpression</span></span>

- <span data-ttu-id="23919-137">DbTreatExpression</span><span class="sxs-lookup"><span data-stu-id="23919-137">DbTreatExpression</span></span>

### <a name="expression-restrictions-and-notes"></a><span data-ttu-id="23919-138">表达式限制和说明</span><span class="sxs-lookup"><span data-stu-id="23919-138">Expression Restrictions and Notes</span></span>

<span data-ttu-id="23919-139">许多表达式只能以受限方式在输出查询命令目录树中进行使用：</span><span class="sxs-lookup"><span data-stu-id="23919-139">Many expressions can only be used in a restricted manner in output query command trees:</span></span>

#### <a name="dbfunctionexpression"></a><span data-ttu-id="23919-140">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="23919-140">DbFunctionExpression</span></span>

<span data-ttu-id="23919-141">可以传递以下函数类型：</span><span class="sxs-lookup"><span data-stu-id="23919-141">The following function types can be passed:</span></span>

- <span data-ttu-id="23919-142">由 Edm 命名空间识别的规范函数。</span><span class="sxs-lookup"><span data-stu-id="23919-142">Canonical functions that are recognized by the Edm namespace.</span></span>

- <span data-ttu-id="23919-143">由 BuiltInAttribute 识别的内置（存储）函数。</span><span class="sxs-lookup"><span data-stu-id="23919-143">Built-in (store) functions that are recognized by the BuiltInAttribute.</span></span>

- <span data-ttu-id="23919-144">用户定义的函数。</span><span class="sxs-lookup"><span data-stu-id="23919-144">User-defined functions.</span></span>

<span data-ttu-id="23919-145">规范函数（有关详细信息，请参阅[规范函数](./language-reference/canonical-functions.md)）被指定为实体框架的一部分，并且提供程序应根据这些规范提供规范函数的实现。</span><span class="sxs-lookup"><span data-stu-id="23919-145">Canonical functions (see [Canonical Functions](./language-reference/canonical-functions.md) for more information) are specified as part of the Entity Framework, and providers should supply implementations for canonical functions based on those specifications.</span></span> <span data-ttu-id="23919-146">存储函数基于相应的提供程序清单中的规范。</span><span class="sxs-lookup"><span data-stu-id="23919-146">Store functions are based on the specifications in the corresponding provider manifest.</span></span> <span data-ttu-id="23919-147">用户定义的函数基于 SSDL 中的规范。</span><span class="sxs-lookup"><span data-stu-id="23919-147">User defined functions are based on specifications in the SSDL.</span></span>

<span data-ttu-id="23919-148">另外，具有 NiladicFunction 特性的函数没有任何参数，并且此类函数在转换时末尾不应有括号。</span><span class="sxs-lookup"><span data-stu-id="23919-148">Also, functions having the NiladicFunction attribute have no arguments and should be translated without the parenthesis at the end.</span></span>  <span data-ttu-id="23919-149">也就是说，  *\<functionName*  *>而不是functionName>（）。\<*</span><span class="sxs-lookup"><span data-stu-id="23919-149">That is, to *\<functionName>* instead of *\<functionName>()*.</span></span>

#### <a name="dbnewinstanceexpression"></a><span data-ttu-id="23919-150">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="23919-150">DbNewInstanceExpression</span></span>

<span data-ttu-id="23919-151">DbNewInstanceExpression 只能在以下两种情况下出现：</span><span class="sxs-lookup"><span data-stu-id="23919-151">DbNewInstanceExpression can only occur in the following two cases:</span></span>

- <span data-ttu-id="23919-152">作为 DbProjectExpression 的 Projection 属性。</span><span class="sxs-lookup"><span data-stu-id="23919-152">As the Projection property of DbProjectExpression.</span></span>  <span data-ttu-id="23919-153">在此情况下，以下限制将适用：</span><span class="sxs-lookup"><span data-stu-id="23919-153">When used as such the following restrictions apply:</span></span>

  - <span data-ttu-id="23919-154">结果类型必须是行类型。</span><span class="sxs-lookup"><span data-stu-id="23919-154">The result type must be a row type.</span></span>

  - <span data-ttu-id="23919-155">它包含的每个参数都是一个生成带基元类型的结果的表达式。</span><span class="sxs-lookup"><span data-stu-id="23919-155">Each of its arguments is an expression that produces a result with a primitive type.</span></span> <span data-ttu-id="23919-156">通常，每个参数都是一个标量表达式（如 DbVariableReferenceExpression 上的 PropertyExpression）、一个函数调用或一个 DbVariableReferenceExpression 上的 DbPropertyExpression 或函数调用的算术计算。</span><span class="sxs-lookup"><span data-stu-id="23919-156">Typically, each argument is a scalar expression, like a PropertyExpression over a DbVariableReferenceExpression, a function invocation, or an arithmetic computation of the DbPropertyExpression over a DbVariableReferenceExpression or a function invocation.</span></span> <span data-ttu-id="23919-157">然而，表示标量子查询的的表达式也可以在 DbNewInstanceExpression 的参数列表中出现。</span><span class="sxs-lookup"><span data-stu-id="23919-157">However, an expression representing a scalar subquery can also occur in the list of arguments for a DbNewInstanceExpression.</span></span> <span data-ttu-id="23919-158">表示标量子查询的表达式是一种表达式树，它表示一个子查询，该子查询只返回一个具有 DbElementExpression 对象根的基元类型的行和一个列</span><span class="sxs-lookup"><span data-stu-id="23919-158">An expression that represents a scalar subquery is an expression tree that represents a subquery that returns exactly one row and one column of a primitive type with a DbElementExpression object root</span></span>

- <span data-ttu-id="23919-159">与集合返回类型一起使用，在此情况下，它定义一个作为自变量提供的表达式的新集合。</span><span class="sxs-lookup"><span data-stu-id="23919-159">With a collection return type, in which case it defines a new collection of the expressions provided as arguments.</span></span>

#### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="23919-160">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="23919-160">DbVariableReferenceExpression</span></span>

<span data-ttu-id="23919-161">A DbVariableReferenceExpression 必须是 DbPropertyExpression 节点的子级。</span><span class="sxs-lookup"><span data-stu-id="23919-161">A DbVariableReferenceExpression has to be a child of DbPropertyExpression node.</span></span>

#### <a name="dbgroupbyexpression"></a><span data-ttu-id="23919-162">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="23919-162">DbGroupByExpression</span></span>

<span data-ttu-id="23919-163">DbGroupByExpression 的 Aggregates 属性只能具有类型 DbFunctionAggregate 的元素。</span><span class="sxs-lookup"><span data-stu-id="23919-163">The Aggregates property of a DbGroupByExpression can only have elements of type DbFunctionAggregate.</span></span> <span data-ttu-id="23919-164">不存在其他聚合类型。</span><span class="sxs-lookup"><span data-stu-id="23919-164">There are no other aggregate types.</span></span>

#### <a name="dblimitexpression"></a><span data-ttu-id="23919-165">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="23919-165">DbLimitExpression</span></span>

<span data-ttu-id="23919-166">属性 Limit 只能为 DbConstantExpression 或 DbParameterReferenceExpression。</span><span class="sxs-lookup"><span data-stu-id="23919-166">The property Limit can only be a DbConstantExpression or a DbParameterReferenceExpression.</span></span> <span data-ttu-id="23919-167">另外，从 3.5 版的 .NET Framework 开始，属性 WithTies 始终为 false。</span><span class="sxs-lookup"><span data-stu-id="23919-167">Also property WithTies is always false as of version 3.5 of the .NET Framework.</span></span>

#### <a name="dbscanexpression"></a><span data-ttu-id="23919-168">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="23919-168">DbScanExpression</span></span>

<span data-ttu-id="23919-169">在输出命令目录树中使用时，DbScanExpression 会有效地表示扫描表、视图或存储查询，由 EntitySetBase：： Target 表示。</span><span class="sxs-lookup"><span data-stu-id="23919-169">When used in output command trees, the DbScanExpression effectively represents a scan over a table, a view, or a store query, represented by EntitySetBase::Target.</span></span>

<span data-ttu-id="23919-170">如果目标的元数据属性 "定义查询" 为非 null，则它表示一个查询，该数据在提供程序的特定语言（或方言）中以存储架构定义中指定的形式提供。</span><span class="sxs-lookup"><span data-stu-id="23919-170">If the metadata property "Defining Query" of the target is non-null, then it represents a query, the query text for which is provided in that metadata property in the provider’s specific language (or dialect) as specified in the store schema definition.</span></span>

<span data-ttu-id="23919-171">否则，目标表示一个表或视图。</span><span class="sxs-lookup"><span data-stu-id="23919-171">Otherwise, the target represents a table or a view.</span></span> <span data-ttu-id="23919-172">它的架构前缀位于 "Schema" 元数据属性中，如果不为 null，则为实体容器名称。</span><span class="sxs-lookup"><span data-stu-id="23919-172">Its schema prefix is either in the "Schema" metadata property, if not null, otherwise is the entity container name.</span></span>  <span data-ttu-id="23919-173">表名或视图名为 "Table" metadata 属性，如果不为 null，则为实体集基的 Name 属性。</span><span class="sxs-lookup"><span data-stu-id="23919-173">The table or view name is either the "Table" metadata property, if not null, otherwise the Name property of the entity set base.</span></span>

<span data-ttu-id="23919-174">所有这些属性源自存储架构定义文件 (SSDL) 中对应的 EntitySet 的定义。</span><span class="sxs-lookup"><span data-stu-id="23919-174">All these properties originate from the definition of the corresponding EntitySet in the store schema definition file (the SSDL).</span></span>

### <a name="using-primitive-types"></a><span data-ttu-id="23919-175">使用基元类型</span><span class="sxs-lookup"><span data-stu-id="23919-175">Using Primitive Types</span></span>

<span data-ttu-id="23919-176">在输出命令目录树中引用基元类型时，通常会在概念模型的基元类型中引用它们。</span><span class="sxs-lookup"><span data-stu-id="23919-176">When primitive types are referenced in output command trees, they are typically referenced in the conceptual model's primitive types.</span></span> <span data-ttu-id="23919-177">不过，对于某些表达式，提供程序需要相应的存储基元类型。</span><span class="sxs-lookup"><span data-stu-id="23919-177">However, for certain expressions, providers need the corresponding store primitive type.</span></span> <span data-ttu-id="23919-178">此类表达式包括 DbCastExpression 且可能包括 DbNullExpression（如果提供程序需要将 null 强制转换为相应类型）等。</span><span class="sxs-lookup"><span data-stu-id="23919-178">Examples of such expressions include DbCastExpression and possibly DbNullExpression, if the provider needs to cast the null to the corresponding type.</span></span> <span data-ttu-id="23919-179">在这些情况下，提供程序应基于基元类型的类别和 facet 对提供程序类型进行映射。</span><span class="sxs-lookup"><span data-stu-id="23919-179">In these cases, providers should do the mapping to the provider type based on the primitive type kind and its facets.</span></span>

## <a name="see-also"></a><span data-ttu-id="23919-180">请参阅</span><span class="sxs-lookup"><span data-stu-id="23919-180">See also</span></span>

- [<span data-ttu-id="23919-181">SQL 生成</span><span class="sxs-lookup"><span data-stu-id="23919-181">SQL Generation</span></span>](sql-generation.md)
