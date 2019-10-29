---
title: 修改 SQL 生成
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: b6c1b71effba17d33c035d0f1df386bf56d405b5
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039887"
---
# <a name="modification-sql-generation"></a><span data-ttu-id="41aa0-102">修改 SQL 生成</span><span class="sxs-lookup"><span data-stu-id="41aa0-102">Modification SQL Generation</span></span>

<span data-ttu-id="41aa0-103">本节讨论如何开发用于（符合 SQL:1999 的数据库）提供程序的修改 SQL 生成模块。</span><span class="sxs-lookup"><span data-stu-id="41aa0-103">This section discusses how to develop a modification SQL generation module for your (SQL:1999-compliant database) provider.</span></span> <span data-ttu-id="41aa0-104">此模块负责将修改命令目录树转换成适当的 SQL INSERT、UPDATE 或 DELETE 语句。</span><span class="sxs-lookup"><span data-stu-id="41aa0-104">This module is responsible for translating a modification command tree into the appropriate SQL INSERT, UPDATE or DELETE statements.</span></span>

<span data-ttu-id="41aa0-105">有关 select 语句的 SQL 生成的信息，请参阅[Sql 生成](sql-generation.md)。</span><span class="sxs-lookup"><span data-stu-id="41aa0-105">For information about SQL generation for select statements, see [SQL Generation](sql-generation.md).</span></span>

## <a name="overview-of-modification-command-trees"></a><span data-ttu-id="41aa0-106">修改命令目录树的概述</span><span class="sxs-lookup"><span data-stu-id="41aa0-106">Overview of Modification Command Trees</span></span>

<span data-ttu-id="41aa0-107">修改 SQL 生成模块可基于给定的输入 DbModificationCommandTree 生成特定于数据库的修改 SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="41aa0-107">The modification SQL generation module generates database-specific modification SQL statements based on a given input DbModificationCommandTree.</span></span>

<span data-ttu-id="41aa0-108">DbModificationCommandTree 是继承自 DbCommandTree 的修改 DML 操作（插入、更新或删除操作）的对象模型表示形式。</span><span class="sxs-lookup"><span data-stu-id="41aa0-108">A DbModificationCommandTree is an object model representation of a modification DML operation (an insert, an update, or a delete operation), inheriting from DbCommandTree.</span></span> <span data-ttu-id="41aa0-109">DbModificationCommandTree 有三种实现：</span><span class="sxs-lookup"><span data-stu-id="41aa0-109">There are three implementations of DbModificationCommandTree:</span></span>

- <span data-ttu-id="41aa0-110">DbInsertCommandTree</span><span class="sxs-lookup"><span data-stu-id="41aa0-110">DbInsertCommandTree</span></span>

- <span data-ttu-id="41aa0-111">DbUpdateCommandTree</span><span class="sxs-lookup"><span data-stu-id="41aa0-111">DbUpdateCommandTree</span></span>

- <span data-ttu-id="41aa0-112">DbDeleteCommandTree</span><span class="sxs-lookup"><span data-stu-id="41aa0-112">DbDeleteCommandTree</span></span>

<span data-ttu-id="41aa0-113">实体框架生成的 DbModificationCommandTree 及其实现始终表示单个行操作。</span><span class="sxs-lookup"><span data-stu-id="41aa0-113">DbModificationCommandTree and its implementations that are produced by the Entity Framework always represent a single row operation.</span></span> <span data-ttu-id="41aa0-114">本节将介绍这些类型及其在 .NET Framework 版本 3.5 中的约束。</span><span class="sxs-lookup"><span data-stu-id="41aa0-114">This section describes these types with their constraints in the .NET Framework version 3.5.</span></span>

<span data-ttu-id="41aa0-115">![关系图](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span><span class="sxs-lookup"><span data-stu-id="41aa0-115">![Diagram](./media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")</span></span>

<span data-ttu-id="41aa0-116">DbModificationCommandTree 具有 Target 属性，该属性表示修改操作的目标集。</span><span class="sxs-lookup"><span data-stu-id="41aa0-116">DbModificationCommandTree has a Target property that represents the target set for the modification operation.</span></span> <span data-ttu-id="41aa0-117">Target 的 Expression 属性定义输入集，始终为 DbScanExpression。</span><span class="sxs-lookup"><span data-stu-id="41aa0-117">The Target’s Expression property, which defines the input set is always DbScanExpression.</span></span>  <span data-ttu-id="41aa0-118">如果其目标的元数据属性 "定义查询" 为非 null，则 DbScanExpression 可以表示表或视图，也可以表示使用查询定义的数据集。</span><span class="sxs-lookup"><span data-stu-id="41aa0-118">A DbScanExpression can either represent a table or a view, or a set of data defined with a query if the metadata property "Defining Query" of its Target is non-null.</span></span>

<span data-ttu-id="41aa0-119">DbScanExpression 表示一个查询，如果使用模型中的定义查询来定义集，但不提供相应的修改操作的功能，则它仅可以获取作为修改目标的提供程序。</span><span class="sxs-lookup"><span data-stu-id="41aa0-119">A DbScanExpression that represents a query could only reach a provider as a target of modification if the set was defined by using a defining query in the model but no function was provided for the corresponding modification operation.</span></span> <span data-ttu-id="41aa0-120">提供程序也许不支持此类方案，例如 SqlClient 就不支持。</span><span class="sxs-lookup"><span data-stu-id="41aa0-120">Providers may not be able to support such a scenario (SqlClient, for example, does not).</span></span>

<span data-ttu-id="41aa0-121">DbInsertCommandTree 表示用一个命令目录树代表的单行插入操作。</span><span class="sxs-lookup"><span data-stu-id="41aa0-121">DbInsertCommandTree represents a single row insert operation expressed as a command tree.</span></span>

```csharp
public sealed class DbInsertCommandTree : DbModificationCommandTree {
   public IList<DbModificationClause> SetClauses { get }
   public DbExpression Returning { get }
}
```

<span data-ttu-id="41aa0-122">DbUpdateCommandTree 表示用一个命令目录树代表的单行更新操作。</span><span class="sxs-lookup"><span data-stu-id="41aa0-122">DbUpdateCommandTree represents a single-row update operation expressed as a command tree.</span></span>

<span data-ttu-id="41aa0-123">DbDeleteCommandTree 表示单独行删除操作，表示为一个命令目录树。</span><span class="sxs-lookup"><span data-stu-id="41aa0-123">DbDeleteCommandTree represents a single row delete operation expressed as a command tree.</span></span>

### <a name="restrictions-on-modification-command-tree-properties"></a><span data-ttu-id="41aa0-124">有关修改命令目录树属性的限制</span><span class="sxs-lookup"><span data-stu-id="41aa0-124">Restrictions on Modification Command Tree Properties</span></span>

<span data-ttu-id="41aa0-125">下面的信息和限制仅适用于修改命令目录树属性。</span><span class="sxs-lookup"><span data-stu-id="41aa0-125">The following information and restrictions apply to the modification command tree properties.</span></span>

#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="41aa0-126">DbInsertCommandTree 和 DbUpdateCommandTree 中的 Returning</span><span class="sxs-lookup"><span data-stu-id="41aa0-126">Returning in DbInsertCommandTree and DbUpdateCommandTree</span></span>

<span data-ttu-id="41aa0-127">当 Returning 不为 null 时，指示该命令返回一个读取器。</span><span class="sxs-lookup"><span data-stu-id="41aa0-127">When non-null, Returning indicates that the command returns a reader.</span></span> <span data-ttu-id="41aa0-128">否则，该命令应返回一个标量值，指示所影响的（已插入或已更新的）行的数量。</span><span class="sxs-lookup"><span data-stu-id="41aa0-128">Otherwise, the command should return a scalar value indicating the number of rows affected (inserted or updated).</span></span>

<span data-ttu-id="41aa0-129">Returning 值指定基于已插入或已更新的行返回结果投影。</span><span class="sxs-lookup"><span data-stu-id="41aa0-129">The Returning value specifies a projection of results to be returned based on the inserted or the updated row.</span></span> <span data-ttu-id="41aa0-130">它仅可以属于表示行的 DbNewInstanceExpression 类型，其每个自变量均为 DbPropertyExpression 并且位于表示对相应 DbModificationCommandTree 的 Target 的引用的 DbVariableReferenceExpression 之上。</span><span class="sxs-lookup"><span data-stu-id="41aa0-130">It can only be of type DbNewInstanceExpression representing a row, with each of its arguments being a DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span> <span data-ttu-id="41aa0-131">Returning 属性中使用的 DbPropertyExpressions 表示的属性始终为存储生成的值或计算值。</span><span class="sxs-lookup"><span data-stu-id="41aa0-131">The properties represented by the DbPropertyExpressions used in the property Returning are always store generated or computed values.</span></span> <span data-ttu-id="41aa0-132">在 DbInsertCommandTree 中，当插入行的表中的属性至少有一个指定为存储生成的值或计算值（在 ssdl 中标记为 StoreGeneratedPattern.Identity 或 StoreGeneratedPattern.Computed）时，Returning 不为 null。</span><span class="sxs-lookup"><span data-stu-id="41aa0-132">In DbInsertCommandTree, Returning is not null when at least one property of the table in which the row is being inserted is specified as store generated or computed (marked as StoreGeneratedPattern.Identity or StoreGeneratedPattern.Computed in the ssdl).</span></span> <span data-ttu-id="41aa0-133">在 DbUpdateCommandTrees 中，当更新行的表中的属性至少有一个指定为存储生成的值或计算值（在 ssdl 中标记为 StoreGeneratedPattern.Computed）时，Returning 不为 null。</span><span class="sxs-lookup"><span data-stu-id="41aa0-133">In DbUpdateCommandTrees, Returning is not null when at least one property of the table in which the row is being updated is specified as store computed (marked as StoreGeneratedPattern.Computed in the ssdl).</span></span>

#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a><span data-ttu-id="41aa0-134">DbInsertCommandTree 和 DbUpdateCommandTree 中的 SetClauses</span><span class="sxs-lookup"><span data-stu-id="41aa0-134">SetClauses in DbInsertCommandTree and DbUpdateCommandTree</span></span>

<span data-ttu-id="41aa0-135">SetClauses 指定插入或更新集子句的列表，这些子句定义插入或更新操作。</span><span class="sxs-lookup"><span data-stu-id="41aa0-135">SetClauses specifies the list of insert or update set clauses that define the insert or update operation.</span></span>

<span data-ttu-id="41aa0-136">此列表的元素指定为类型 DbModificationClause，它在插入或更新修改操作中指定单个子句。</span><span class="sxs-lookup"><span data-stu-id="41aa0-136">The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation.</span></span> <span data-ttu-id="41aa0-137">DbSetClause 继承自 DbModificationClause，并在用于设置属性值的修改操作中指定该子句。</span><span class="sxs-lookup"><span data-stu-id="41aa0-137">DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property.</span></span> <span data-ttu-id="41aa0-138">从 .NET Framework 版本3.5 开始，SetClauses 中的所有元素均为 SetClause 类型。</span><span class="sxs-lookup"><span data-stu-id="41aa0-138">Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.</span></span>

<span data-ttu-id="41aa0-139">Property 指定应进行更新的属性。</span><span class="sxs-lookup"><span data-stu-id="41aa0-139">Property specifies the property that should be updated.</span></span> <span data-ttu-id="41aa0-140">它始终是 DbPropertyExpression 并且位于表示对相应 DbModificationCommandTree 的 Target 的引用的 DbVariableReferenceExpression 之上。</span><span class="sxs-lookup"><span data-stu-id="41aa0-140">It is always a DbPropertyExpression over a DbVariableReferenceExpression, which represents a reference to the Target of the corresponding DbModificationCommandTree.</span></span>

<span data-ttu-id="41aa0-141">Value 指定用来更新属性的新值。</span><span class="sxs-lookup"><span data-stu-id="41aa0-141">Value specifies the new value with which to update the property.</span></span> <span data-ttu-id="41aa0-142">它是 DbConstantExpression 类型或 DbNullExpression 类型。</span><span class="sxs-lookup"><span data-stu-id="41aa0-142">It is either of type DbConstantExpression or DbNullExpression.</span></span>

#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a><span data-ttu-id="41aa0-143">DbUpdateCommandTree 和 DbDeleteCommandTree 中的 Predicate</span><span class="sxs-lookup"><span data-stu-id="41aa0-143">Predicate in DbUpdateCommandTree and DbDeleteCommandTree</span></span>

<span data-ttu-id="41aa0-144">Predicate 指定用于确定应更新或删除目标集合中的哪些成员的谓词。</span><span class="sxs-lookup"><span data-stu-id="41aa0-144">Predicate specifies the predicate used to determine which members of the target collection should be updated or deleted.</span></span> <span data-ttu-id="41aa0-145">它是由 DbExpressions 的下列子集构成的表达式树：</span><span class="sxs-lookup"><span data-stu-id="41aa0-145">It is an expression tree built of the following subset of DbExpressions:</span></span>

- <span data-ttu-id="41aa0-146">种类等于的 DbComparisonExpression，右侧子元素为 DbPropertyExpression，并在 DbConstantExpression 的左侧加上一个。</span><span class="sxs-lookup"><span data-stu-id="41aa0-146">DbComparisonExpression of kind Equals, with the right child being a DbPropertyExpression as restricted below and the left child a DbConstantExpression.</span></span>

- <span data-ttu-id="41aa0-147">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="41aa0-147">DbConstantExpression</span></span>

- <span data-ttu-id="41aa0-148">DbIsNullExpression 在 DbPropertyExpression 上按以下方式限制</span><span class="sxs-lookup"><span data-stu-id="41aa0-148">DbIsNullExpression over a DbPropertyExpression as restricted below</span></span>

- <span data-ttu-id="41aa0-149">DbPropertyExpression 在表示对相应 DbModificationCommandTree 的 Target 的引用的 DbVariableReferenceExpression 之上。</span><span class="sxs-lookup"><span data-stu-id="41aa0-149">DbPropertyExpression over a DbVariableReferenceExpression representing a reference to the Target of the corresponding DbModificationCommandTree.</span></span>

- <span data-ttu-id="41aa0-150">DbAndExpression</span><span class="sxs-lookup"><span data-stu-id="41aa0-150">DbAndExpression</span></span>

- <span data-ttu-id="41aa0-151">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="41aa0-151">DbNotExpression</span></span>

- <span data-ttu-id="41aa0-152">DbOrExpression</span><span class="sxs-lookup"><span data-stu-id="41aa0-152">DbOrExpression</span></span>

## <a name="modification-sql-generation-in-the-sample-provider"></a><span data-ttu-id="41aa0-153">示例提供程序中的修改 SQL 生成</span><span class="sxs-lookup"><span data-stu-id="41aa0-153">Modification SQL Generation in the Sample Provider</span></span>

<span data-ttu-id="41aa0-154">[实体框架示例提供程序](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)演示支持实体框架的 ADO.NET 数据提供程序的组件。</span><span class="sxs-lookup"><span data-stu-id="41aa0-154">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the components of ADO.NET Data Providers that support the Entity Framework.</span></span> <span data-ttu-id="41aa0-155">该示例提供程序以 SQL Server 2005 数据库为目标，并在 System.Data.SqlClient ADO.NET 2.0 数据提供程序之上作为一个包装实现。</span><span class="sxs-lookup"><span data-stu-id="41aa0-155">It targets a SQL Server 2005 database and is implemented as a wrapper on top of System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>

<span data-ttu-id="41aa0-156">该示例提供程序的修改 SQL 生成模块（位于 SQL Generation\DmlSqlGenerator.cs 文件中）采用一个输入 DbModificationCommandTree，并且生成可能带有 SELECT 语句的单个修改 SQL 语句以返回一个读取器（如果 DbModificationCommandTree 指定了读取器）。</span><span class="sxs-lookup"><span data-stu-id="41aa0-156">The modification SQL generation module of the sample provider (located in the file SQL Generation\DmlSqlGenerator.cs) takes an input DbModificationCommandTree and produces a single modification SQL statement possibly followed by a select statement to return a reader if specified by the DbModificationCommandTree.</span></span> <span data-ttu-id="41aa0-157">请注意，生成的命令的形式受目标 SQL Server 数据库影响。</span><span class="sxs-lookup"><span data-stu-id="41aa0-157">Note that the shape of the commands generated is affected by the target SQL Server database.</span></span>

### <a name="helper-classes-expressiontranslator"></a><span data-ttu-id="41aa0-158">帮助器类：ExpressionTranslator</span><span class="sxs-lookup"><span data-stu-id="41aa0-158">Helper Classes: ExpressionTranslator</span></span>

<span data-ttu-id="41aa0-159">ExpressionTranslator 用作一个适用于 DbExpression 类型的所有修改命令目录树属性的通用轻型转换器。</span><span class="sxs-lookup"><span data-stu-id="41aa0-159">ExpressionTranslator serves as a common lightweight translator for all modification command tree properties of type DbExpression.</span></span> <span data-ttu-id="41aa0-160">它支持仅转换修改命令目录树的属性所限于使用的表达式类型，而且它在构建时应用了特定约束。</span><span class="sxs-lookup"><span data-stu-id="41aa0-160">It supports translation of only the expression types to which the properties of the modification command tree are constrained and is built with the particular constraints in mind.</span></span>

<span data-ttu-id="41aa0-161">以下信息讨论如何访问特定的表达式类型（忽略具有细微转换的节点）。</span><span class="sxs-lookup"><span data-stu-id="41aa0-161">The following information discusses visiting specific expression types (nodes with trivial translations are omitted).</span></span>

### <a name="dbcomparisonexpression"></a><span data-ttu-id="41aa0-162">DbComparisonExpression</span><span class="sxs-lookup"><span data-stu-id="41aa0-162">DbComparisonExpression</span></span>

<span data-ttu-id="41aa0-163">当使用 preserveMemberValues = true 构造 ExpressionTranslator 并且右侧的常量为 DbConstantExpression（而不是 DbNullExpression）时，它将左操作数（一个 DbPropertyExpressions）与该 DbConstantExpression 关联。</span><span class="sxs-lookup"><span data-stu-id="41aa0-163">When the ExpressionTranslator is constructed with preserveMemberValues = true, and when the constant to the right is a DbConstantExpression (instead of DbNullExpression), it associates the left operand (a DbPropertyExpressions) with that DbConstantExpression.</span></span> <span data-ttu-id="41aa0-164">如果需要生成一个返回 Select 语句来标识受影响的行，则使用此类型。</span><span class="sxs-lookup"><span data-stu-id="41aa0-164">That is used if a return Select statement needs to be generated to identify the affected row.</span></span>

### <a name="dbconstantexpression"></a><span data-ttu-id="41aa0-165">DbConstantExpression</span><span class="sxs-lookup"><span data-stu-id="41aa0-165">DbConstantExpression</span></span>

<span data-ttu-id="41aa0-166">针对每个所访问的常量，创建一个参数。</span><span class="sxs-lookup"><span data-stu-id="41aa0-166">For each visited constant a parameter is created.</span></span>

### <a name="dbpropertyexpression"></a><span data-ttu-id="41aa0-167">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="41aa0-167">DbPropertyExpression</span></span>

<span data-ttu-id="41aa0-168">假定 DbPropertyExpression 的实例始终表示输入表，除非生成操作已创建一个别名（只会在使用表变量时的更新方案中出现这种情况），否则不需要为输入指定别名；转换默认为属性名。</span><span class="sxs-lookup"><span data-stu-id="41aa0-168">Given that the Instance of the DbPropertyExpression always represents the input table, unless the generation has created an alias (which only happens in update scenarios when a table variable is used), no alias needs to be specified for the input; the translation defaults to the property name.</span></span>

## <a name="generating-an-insert-sql-command"></a><span data-ttu-id="41aa0-169">生成插入 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="41aa0-169">Generating an Insert SQL Command</span></span>

<span data-ttu-id="41aa0-170">对于示例提供程序中给定的 DbInsertCommandTree，生成的插入命令跟在下面两个插入模板中的一个后面。</span><span class="sxs-lookup"><span data-stu-id="41aa0-170">For a given DbInsertCommandTree in the sample provider, the generated insert command follows one of the two insert templates below.</span></span>

<span data-ttu-id="41aa0-171">第一个模板包含一个命令来执行插入操作（假定值在 SetClauses 列表中）以及一个 SELECT 语句来为插入的行返回在 Returning 属性中指定的属性（如果 Returning 属性不为 null）。</span><span class="sxs-lookup"><span data-stu-id="41aa0-171">The first template has a command to perform the insert given the values in the list of SetClauses, and a SELECT statement to return the properties specified in the Returning property for the inserted row if the Returning property was not null.</span></span> <span data-ttu-id="41aa0-172">如果插入行，则谓词元素 "\@@ROWCOUNT > 0" 为 true。</span><span class="sxs-lookup"><span data-stu-id="41aa0-172">The predicate element "\@@ROWCOUNT > 0" is true if a row was inserted.</span></span> <span data-ttu-id="41aa0-173">仅当 Scope_identity 是存储生成的&#124;键时，谓词元素 "KeyMemberI = keyValueI scope_identity （）" 才采用形状 "keyMemberI = keyMemberI （）"，因为 scope_identity （）返回插入到标识中的最后一个标识值（存储区生成的）列。</span><span class="sxs-lookup"><span data-stu-id="41aa0-173">The predicate element "keyMemberI =  keyValueI &#124; scope_identity()" takes the shape  "keyMemberI =  scope_identity()" only if keyMemberI is a store-generated key, because scope_identity() returns the last identity value inserted into an identity (store-generated) column.</span></span>

```sql
-- first insert Template
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

<span data-ttu-id="41aa0-174">如果插入命令指定插入一行，其中的主键是存储生成的，但不是整数类型，因而不能与 scope_identity() 一起使用，则需要第二个模板。</span><span class="sxs-lookup"><span data-stu-id="41aa0-174">The second template is needed if the insert specifies inserting a row where the primary key is store-generated but is not an integer type and therefore can't be used with scope_identity()).</span></span> <span data-ttu-id="41aa0-175">如果存在复合存储生成的键，也要使用第二个模板。</span><span class="sxs-lookup"><span data-stu-id="41aa0-175">It is also used if there is a compound store-generated key.</span></span>

```sql
-- second insert template
DECLARE @generated_keys TABLE [(keyMember0, … keyMemberN)

INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
 OUTPUT inserted.KeyMember0, …, inserted.KeyMemberN INTO @generated_keys
 VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning_over_t>
 FROM @generated_keys  AS g
JOIN <target> AS t ON g.KeyMember0 = t.KeyMember0 AND … g.KeyMemberN = t.KeyMemberN
 WHERE @@ROWCOUNT > 0
```

<span data-ttu-id="41aa0-176">下面的示例使用随示例提供程序提供的模型，</span><span class="sxs-lookup"><span data-stu-id="41aa0-176">The following is an example that uses the model that is included with the sample provider.</span></span> <span data-ttu-id="41aa0-177">它从 DbInsertCommandTree 生成一个插入命令。</span><span class="sxs-lookup"><span data-stu-id="41aa0-177">It generates an insert command from a DbInsertCommandTree.</span></span>

<span data-ttu-id="41aa0-178">下面的代码插入一个 Category：</span><span class="sxs-lookup"><span data-stu-id="41aa0-178">The following code inserts a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = new Category();
   c.CategoryName = "Test Category";
   c.Description = "A new category for testing";
   northwindContext.AddObject("Categories", c);
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="41aa0-179">此代码生成以下传递给提供程序的命令目录树:</span><span class="sxs-lookup"><span data-stu-id="41aa0-179">This code produces the following command tree, which is passed to the provider:</span></span>

```output
DbInsertCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_SetClauses
| |_DbSetClause
| | |_Property
| | | |_Var(target).CategoryName
| | |_Value
| |   |_'Test Category'
| |_DbSetClause
| | |_Property
| | | |_Var(target).Description
| | |_Value
| |   |_'A new category for testing'
| |_DbSetClause
|   |_Property
|   | |_Var(target).Picture
|   |_Value
|     |_null
|_Returning
  |_NewInstance : Record['CategoryID'=Edm.Int32]
    |_Column : 'CategoryID'
      |_Var(target).CategoryID
```

<span data-ttu-id="41aa0-180">示例提供程序生成的存储命令为下面的 SQL 语句：</span><span class="sxs-lookup"><span data-stu-id="41aa0-180">The store command that the sample provider produces is the following SQL statement:</span></span>

```sql
insert [dbo].[Categories]([CategoryName], [Description], [Picture])
values (@p0, @p1, null)
select [CategoryID]
from [dbo].[Categories]
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()
```

## <a name="generating-an-update-sql-command"></a><span data-ttu-id="41aa0-181">生成更新 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="41aa0-181">Generating an Update SQL Command</span></span>

<span data-ttu-id="41aa0-182">对于给定的 DbUpdateCommandTree，生成的更新命令将基于下面的模板：</span><span class="sxs-lookup"><span data-stu-id="41aa0-182">For a given DbUpdateCommandTree, the generated update command is based on the following template:</span></span>

```sql
-- UPDATE Template
UPDATE <target>
SET setClauseProperty0 = setClauseValue0, .. setClausePropertyN = setClauseValueN  | @i = 0
WHERE <predicate>

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

<span data-ttu-id="41aa0-183">仅当未指定 set 子句时，set 子句才具有伪 set 子句（"@i = 0"）。</span><span class="sxs-lookup"><span data-stu-id="41aa0-183">The set clause has the fake set clause ("@i = 0") only if no set clauses are specified.</span></span> <span data-ttu-id="41aa0-184">这将确保重新计算所有存储计算的列。</span><span class="sxs-lookup"><span data-stu-id="41aa0-184">This is to ensure that any store-computed columns are recomputed.</span></span>

<span data-ttu-id="41aa0-185">仅当 Returning 属性不为 null 时，才生成 SELECT 语句以返回在 Returning 属性中指定的属性。</span><span class="sxs-lookup"><span data-stu-id="41aa0-185">Only if the Returning property is not null, a select statement is generated to return the properties specified in the Returning property.</span></span>

<span data-ttu-id="41aa0-186">下面的示例使用随示例提供程序提供的模型生成更新命令。</span><span class="sxs-lookup"><span data-stu-id="41aa0-186">The following example uses the model that is included with the sample provider to generate an update command.</span></span>

<span data-ttu-id="41aa0-187">下面的用户代码更新 Category：</span><span class="sxs-lookup"><span data-stu-id="41aa0-187">The following user code updates a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();
   c.CategoryName = "New test name";
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="41aa0-188">此用户代码生成以下传递给提供程序的命令树：</span><span class="sxs-lookup"><span data-stu-id="41aa0-188">This user code produces the following command tree, which is passed to the provider:</span></span>

```output
DbUpdateCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_SetClauses
| |_DbSetClause
|   |_Property
|   | |_Var(target).CategoryName
|   |_Value
|     |_'New test name'
|_Predicate
| |_
|   |_Var(target).CategoryID
|   |_=
|   |_10
|_Returning
```

<span data-ttu-id="41aa0-189">示例提供程序生成下面的存储命令：</span><span class="sxs-lookup"><span data-stu-id="41aa0-189">The sample provider produces the following store command:</span></span>

```sql
update [dbo].[Categories]
set [CategoryName] = @p0
where ([CategoryID] = @p1)
```

### <a name="generating-a-delete-sql-command"></a><span data-ttu-id="41aa0-190">生成删除 SQL 命令</span><span class="sxs-lookup"><span data-stu-id="41aa0-190">Generating a Delete SQL Command</span></span>

<span data-ttu-id="41aa0-191">对于给定的 DbDeleteCommandTree，生成的 DELETE 命令将基于下面的模板：</span><span class="sxs-lookup"><span data-stu-id="41aa0-191">For a given DbDeleteCommandTree, the generated DELETE command is based on the following template:</span></span>

```sql
-- DELETE Template
DELETE <target>
WHERE <predicate>
```

<span data-ttu-id="41aa0-192">下面的示例使用随示例提供程序提供的模型生成删除命令。</span><span class="sxs-lookup"><span data-stu-id="41aa0-192">The following example uses the model that is included with the sample provider to generate a delete command.</span></span>

<span data-ttu-id="41aa0-193">下面的用户代码删除 Category：</span><span class="sxs-lookup"><span data-stu-id="41aa0-193">The following user code deletes a Category:</span></span>

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();
   northwindContext.DeleteObject(c);
   northwindContext.SaveChanges();
}
```

<span data-ttu-id="41aa0-194">此用户代码生成以下传递给提供程序的命令树。</span><span class="sxs-lookup"><span data-stu-id="41aa0-194">This user code produces the following command tree, which is passed to the provider.</span></span>

```output
DbDeleteCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_Predicate
  |_
    |_Var(target).CategoryID
    |_=
    |_10
```

<span data-ttu-id="41aa0-195">下面的存储命令由示例提供程序生成：</span><span class="sxs-lookup"><span data-stu-id="41aa0-195">The following store command is produced by the sample provider:</span></span>

```sql
delete [dbo].[Categories]
where ([CategoryID] = @p0)
```

## <a name="see-also"></a><span data-ttu-id="41aa0-196">请参阅</span><span class="sxs-lookup"><span data-stu-id="41aa0-196">See also</span></span>

- [<span data-ttu-id="41aa0-197">编写实体框架数据提供程序</span><span class="sxs-lookup"><span data-stu-id="41aa0-197">Writing an Entity Framework Data Provider</span></span>](writing-an-ef-data-provider.md)
