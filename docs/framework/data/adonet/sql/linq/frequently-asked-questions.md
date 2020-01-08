---
title: 常见问题
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 3cc879e97438138554f1d39cf588e01bfbba28a6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634693"
---
# <a name="frequently-asked-questions"></a><span data-ttu-id="e827c-102">常见问题</span><span class="sxs-lookup"><span data-stu-id="e827c-102">Frequently Asked Questions</span></span>

<span data-ttu-id="e827c-103">以下各节介绍了实现 LINQ 时可能会遇到的一些常见问题。</span><span class="sxs-lookup"><span data-stu-id="e827c-103">The following sections answer some common issues that you might encounter when you implement LINQ.</span></span>

<span data-ttu-id="e827c-104">其他问题在[疑难解答](troubleshooting.md)中得到了解决。</span><span class="sxs-lookup"><span data-stu-id="e827c-104">Additional issues are addressed in [Troubleshooting](troubleshooting.md).</span></span>

## <a name="cannot-connect"></a><span data-ttu-id="e827c-105">无法连接</span><span class="sxs-lookup"><span data-stu-id="e827c-105">Cannot Connect</span></span>

<span data-ttu-id="e827c-106">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-106">Q.</span></span> <span data-ttu-id="e827c-107">我无法连接到数据库。</span><span class="sxs-lookup"><span data-stu-id="e827c-107">I cannot connect to my database.</span></span>

<span data-ttu-id="e827c-108">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-108">A.</span></span> <span data-ttu-id="e827c-109">请确保您的连接字符串正确且您的 SQL Server 实例正在运行。</span><span class="sxs-lookup"><span data-stu-id="e827c-109">Make sure your connection string is correct and that your SQL Server instance is running.</span></span> <span data-ttu-id="e827c-110">另请注意，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 要求启用命名管道协议。</span><span class="sxs-lookup"><span data-stu-id="e827c-110">Note also that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] requires the Named Pipes protocol to be enabled.</span></span> <span data-ttu-id="e827c-111">有关详细信息，请参阅[通过演练学习](learning-by-walkthroughs.md)。</span><span class="sxs-lookup"><span data-stu-id="e827c-111">For more information, see [Learning by Walkthroughs](learning-by-walkthroughs.md).</span></span>

## <a name="changes-to-database-lost"></a><span data-ttu-id="e827c-112">对数据库的更改丢失</span><span class="sxs-lookup"><span data-stu-id="e827c-112">Changes to Database Lost</span></span>

<span data-ttu-id="e827c-113">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-113">Q.</span></span> <span data-ttu-id="e827c-114">我对数据库中的数据进行了更改，但是在重新运行应用程序时更改已丢失。</span><span class="sxs-lookup"><span data-stu-id="e827c-114">I made a change to data in the database, but when I reran my application, the change was no longer there.</span></span>

<span data-ttu-id="e827c-115">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-115">A.</span></span> <span data-ttu-id="e827c-116">请确保您调用了 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 来将结果保存到数据库。</span><span class="sxs-lookup"><span data-stu-id="e827c-116">Make sure that you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> to save results to the database.</span></span>

## <a name="database-connection-open-how-long"></a><span data-ttu-id="e827c-117">数据库连接：可以打开多长时间？</span><span class="sxs-lookup"><span data-stu-id="e827c-117">Database Connection: Open How Long?</span></span>

<span data-ttu-id="e827c-118">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-118">Q.</span></span> <span data-ttu-id="e827c-119">我的数据库连接可以保持打开状态多长时间？</span><span class="sxs-lookup"><span data-stu-id="e827c-119">How long does my database connection remain open?</span></span>

<span data-ttu-id="e827c-120">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-120">A.</span></span> <span data-ttu-id="e827c-121">一个连接通常会一直保持打开状态，直至您使用完查询结果为止。</span><span class="sxs-lookup"><span data-stu-id="e827c-121">A connection typically remains open until you consume the query results.</span></span> <span data-ttu-id="e827c-122">如果您需要花时间处理所有结果并且愿意对结果进行缓存，请将 <xref:System.Linq.Enumerable.ToList%2A> 应用于查询。</span><span class="sxs-lookup"><span data-stu-id="e827c-122">If you expect to take time to process all the results and are not opposed to caching the results, apply <xref:System.Linq.Enumerable.ToList%2A> to the query.</span></span> <span data-ttu-id="e827c-123">在每个对象仅处理一次的常见方案中，流模型比 `DataReader` 和 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 都更为适合。</span><span class="sxs-lookup"><span data-stu-id="e827c-123">In common scenarios where each object is processed only one time, the streaming model is superior in both `DataReader` and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>

<span data-ttu-id="e827c-124">连接使用的准确详细信息与以下内容有关：</span><span class="sxs-lookup"><span data-stu-id="e827c-124">The exact details of connection usage depend on the following:</span></span>

- <span data-ttu-id="e827c-125">使用连接对象构造 <xref:System.Data.Linq.DataContext> 时的连接状态。</span><span class="sxs-lookup"><span data-stu-id="e827c-125">Connection status if the <xref:System.Data.Linq.DataContext> is constructed with a connection object.</span></span>

- <span data-ttu-id="e827c-126">连接字符串设置（例如，启用多活动结果集 (MARS)）。</span><span class="sxs-lookup"><span data-stu-id="e827c-126">Connection string settings (for example, enabling Multiple Active Result Sets (MARS).</span></span> <span data-ttu-id="e827c-127">有关详细信息，请参阅[多个活动结果集 (MARS)](../multiple-active-result-sets-mars.md)。</span><span class="sxs-lookup"><span data-stu-id="e827c-127">For more information, see [Multiple Active Result Sets (MARS)](../multiple-active-result-sets-mars.md).</span></span>

## <a name="updating-without-querying"></a><span data-ttu-id="e827c-128">在不进行查询的情况下更新</span><span class="sxs-lookup"><span data-stu-id="e827c-128">Updating Without Querying</span></span>

<span data-ttu-id="e827c-129">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-129">Q.</span></span> <span data-ttu-id="e827c-130">是否可以在不先查询数据库的情况下更新表数据？</span><span class="sxs-lookup"><span data-stu-id="e827c-130">Can I update table data without first querying the database?</span></span>

<span data-ttu-id="e827c-131">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-131">A.</span></span> <span data-ttu-id="e827c-132">虽然 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 没有基于集的更新命令，但是可以使用以下方法之一进行更新而无需先进行查询：</span><span class="sxs-lookup"><span data-stu-id="e827c-132">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] does not have set-based update commands, you can use either of the following techniques to update without first querying:</span></span>

- <span data-ttu-id="e827c-133">使用 <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> 发送 SQL 代码。</span><span class="sxs-lookup"><span data-stu-id="e827c-133">Use <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> to send SQL code.</span></span>

- <span data-ttu-id="e827c-134">创建对象的新实例，并初始化所有影响更新的当前值（字段）。</span><span class="sxs-lookup"><span data-stu-id="e827c-134">Create a new instance of the object and initialize all the current values (fields) that affect the update.</span></span> <span data-ttu-id="e827c-135">然后使用 <xref:System.Data.Linq.DataContext> 将对象附加到 <xref:System.Data.Linq.Table%601.Attach%2A> 并修改您要更改的字段。</span><span class="sxs-lookup"><span data-stu-id="e827c-135">Then attach the object to the <xref:System.Data.Linq.DataContext> by using <xref:System.Data.Linq.Table%601.Attach%2A> and modify the field you want to change.</span></span>

## <a name="unexpected-query-results"></a><span data-ttu-id="e827c-136">意外的查询结果</span><span class="sxs-lookup"><span data-stu-id="e827c-136">Unexpected Query Results</span></span>

<span data-ttu-id="e827c-137">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-137">Q.</span></span> <span data-ttu-id="e827c-138">我的查询返回了意外的结果。</span><span class="sxs-lookup"><span data-stu-id="e827c-138">My query is returning unexpected results.</span></span> <span data-ttu-id="e827c-139">如何检查所发生的情况？</span><span class="sxs-lookup"><span data-stu-id="e827c-139">How can I inspect what is occurring?</span></span>

<span data-ttu-id="e827c-140">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-140">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e827c-141">提供了几种工具用于检查其生成的 SQL 代码。</span><span class="sxs-lookup"><span data-stu-id="e827c-141">provides several tools for inspecting the SQL code it generates.</span></span> <span data-ttu-id="e827c-142">其中最重要的工具就是 <xref:System.Data.Linq.DataContext.Log%2A>。</span><span class="sxs-lookup"><span data-stu-id="e827c-142">One of the most important is <xref:System.Data.Linq.DataContext.Log%2A>.</span></span> <span data-ttu-id="e827c-143">有关详细信息，请参阅[调试支持](debugging-support.md)。</span><span class="sxs-lookup"><span data-stu-id="e827c-143">For more information, see [Debugging Support](debugging-support.md).</span></span>

## <a name="unexpected-stored-procedure-results"></a><span data-ttu-id="e827c-144">意外的存储过程结果</span><span class="sxs-lookup"><span data-stu-id="e827c-144">Unexpected Stored Procedure Results</span></span>

<span data-ttu-id="e827c-145">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-145">Q.</span></span> <span data-ttu-id="e827c-146">我有一个存储过程，其返回值由 `MAX()` 进行计算。</span><span class="sxs-lookup"><span data-stu-id="e827c-146">I have a stored procedure whose return value is calculated by `MAX()`.</span></span> <span data-ttu-id="e827c-147">当我将该存储过程拖到 O/R 设计器图面时，返回值是不正确的。</span><span class="sxs-lookup"><span data-stu-id="e827c-147">When I drag the stored procedure to the O/R Designer surface, the return value is not correct.</span></span>

<span data-ttu-id="e827c-148">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-148">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e827c-149">提供了两种方法来通过存储过程返回数据库生成的值：</span><span class="sxs-lookup"><span data-stu-id="e827c-149">provides two ways to return database-generated values by way of stored procedures:</span></span>

- <span data-ttu-id="e827c-150">通过命名输出结果。</span><span class="sxs-lookup"><span data-stu-id="e827c-150">By naming the output result.</span></span>

- <span data-ttu-id="e827c-151">通过显式指定输出参数。</span><span class="sxs-lookup"><span data-stu-id="e827c-151">By explicitly specifying an output parameter.</span></span>

<span data-ttu-id="e827c-152">下面是错误输出的示例。</span><span class="sxs-lookup"><span data-stu-id="e827c-152">The following is an example of incorrect output.</span></span> <span data-ttu-id="e827c-153">因为 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 无法映射结果，所以始终返回 0：</span><span class="sxs-lookup"><span data-stu-id="e827c-153">Because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot map the results, it always returns 0:</span></span>

```sql
create procedure proc2

as

begin

select max(i) from t where name like 'hello'

end
```

<span data-ttu-id="e827c-154">下面是使用输出参数获得正确输出的示例：</span><span class="sxs-lookup"><span data-stu-id="e827c-154">The following is an example of correct output by using an output parameter:</span></span>

```sql
create procedure proc2

@result int OUTPUT

as

select @result = MAX(i) from t where name like 'hello'

go
```

<span data-ttu-id="e827c-155">下面是通过命名输出结果获得正确输出的示例：</span><span class="sxs-lookup"><span data-stu-id="e827c-155">The following is an example of correct output by naming the output result:</span></span>

```sql
create procedure proc2

as

begin

select nax(i) AS MaxResult from t where name like 'hello'

end
```

<span data-ttu-id="e827c-156">有关详细信息，请参阅[使用存储过程自定义操作](customizing-operations-by-using-stored-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="e827c-156">For more information, see [Customizing Operations By Using Stored Procedures](customizing-operations-by-using-stored-procedures.md).</span></span>

## <a name="serialization-errors"></a><span data-ttu-id="e827c-157">序列化错误</span><span class="sxs-lookup"><span data-stu-id="e827c-157">Serialization Errors</span></span>

<span data-ttu-id="e827c-158">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-158">Q.</span></span> <span data-ttu-id="e827c-159">当我尝试序列化时，出现以下错误： "Type ' ChangeTracker + StandardChangeTracker ' .。。未标记为可序列化。 "</span><span class="sxs-lookup"><span data-stu-id="e827c-159">When I try to serialize, I get the following error: "Type 'System.Data.Linq.ChangeTracker+StandardChangeTracker' ... is not marked as serializable."</span></span>

<span data-ttu-id="e827c-160">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-160">A.</span></span> <span data-ttu-id="e827c-161">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的代码生成支持 <xref:System.Runtime.Serialization.DataContractSerializer> 序列化，</span><span class="sxs-lookup"><span data-stu-id="e827c-161">Code generation in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports <xref:System.Runtime.Serialization.DataContractSerializer> serialization.</span></span> <span data-ttu-id="e827c-162">而不支持 <xref:System.Xml.Serialization.XmlSerializer> 或 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>。</span><span class="sxs-lookup"><span data-stu-id="e827c-162">It does not support <xref:System.Xml.Serialization.XmlSerializer> or <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="e827c-163">有关详细信息，请参阅[序列化](serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="e827c-163">For more information, see [Serialization](serialization.md).</span></span>

## <a name="multiple-dbml-files"></a><span data-ttu-id="e827c-164">多个 DBML 文件</span><span class="sxs-lookup"><span data-stu-id="e827c-164">Multiple DBML Files</span></span>

<span data-ttu-id="e827c-165">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-165">Q.</span></span> <span data-ttu-id="e827c-166">如果我有多个 DBML 文件共享一些公用的表，我会收到一个编译器错误消息。</span><span class="sxs-lookup"><span data-stu-id="e827c-166">When I have multiple DBML files that share some tables in common, I get a compiler error.</span></span>

<span data-ttu-id="e827c-167">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-167">A.</span></span> <span data-ttu-id="e827c-168">将对象关系设计器的**上下文命名空间**和**实体命名空间**属性设置为每个 DBML 文件的非重复值。</span><span class="sxs-lookup"><span data-stu-id="e827c-168">Set the **Context Namespace** and **Entity Namespace** properties from the Object Relational Designer to a distinct value for each DBML file.</span></span> <span data-ttu-id="e827c-169">此方法可以避免名称/命名空间冲突。</span><span class="sxs-lookup"><span data-stu-id="e827c-169">This approach eliminates the name/namespace collision.</span></span>

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a><span data-ttu-id="e827c-170">避免在插入或更新时显式设置数据库生成的值</span><span class="sxs-lookup"><span data-stu-id="e827c-170">Avoiding Explicit Setting of Database-Generated Values on Insert or Update</span></span>

<span data-ttu-id="e827c-171">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-171">Q.</span></span> <span data-ttu-id="e827c-172">我的一个数据库表具有一个默认为 SQL `DateCreated` 的 `Getdate()` 列。</span><span class="sxs-lookup"><span data-stu-id="e827c-172">I have a database table with a `DateCreated` column that defaults to SQL `Getdate()`.</span></span> <span data-ttu-id="e827c-173">在我试图使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 插入新记录时，该值会设置为 `NULL`。</span><span class="sxs-lookup"><span data-stu-id="e827c-173">When I try to insert a new record by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the value gets set to `NULL`.</span></span> <span data-ttu-id="e827c-174">我希望其设置为数据库默认值。</span><span class="sxs-lookup"><span data-stu-id="e827c-174">I would expect it to be set to the database default.</span></span>

<span data-ttu-id="e827c-175">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-175">A.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e827c-176">会自动为标识（自动增加）和 rowguidcol（数据库生成的 GUID）以及时间戳列处理这种情况。</span><span class="sxs-lookup"><span data-stu-id="e827c-176">handles this situation automatically for identity (auto-increment) and rowguidcol (database-generated GUID) and timestamp columns.</span></span> <span data-ttu-id="e827c-177">在其他情况下，应手动设置 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` 并 <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/属性。</span><span class="sxs-lookup"><span data-stu-id="e827c-177">In other cases, you should manually set <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` and <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/<xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> properties.</span></span>

## <a name="multiple-dataloadoptions"></a><span data-ttu-id="e827c-178">多个 DataLoadOptions</span><span class="sxs-lookup"><span data-stu-id="e827c-178">Multiple DataLoadOptions</span></span>

<span data-ttu-id="e827c-179">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-179">Q.</span></span> <span data-ttu-id="e827c-180">是否可以指定其他加载选项而不覆盖原先的选项？</span><span class="sxs-lookup"><span data-stu-id="e827c-180">Can I specify additional load options without overwriting the first?</span></span>

<span data-ttu-id="e827c-181">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-181">A.</span></span> <span data-ttu-id="e827c-182">可以。</span><span class="sxs-lookup"><span data-stu-id="e827c-182">Yes.</span></span> <span data-ttu-id="e827c-183">不会覆盖原先的选项，如下面的示例中所示：</span><span class="sxs-lookup"><span data-stu-id="e827c-183">The first is not overwritten, as in the following example:</span></span>

```vb
Dim dlo As New DataLoadOptions()
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)
```

```csharp
DataLoadOptions dlo = new DataLoadOptions();
dlo.LoadWith<Order>(o => o.Customer);
dlo.LoadWith<Order>(o => o.OrderDetails);
```

## <a name="errors-using-sql-compact-35"></a><span data-ttu-id="e827c-184">使用 SQL Compact 3.5 时的错误</span><span class="sxs-lookup"><span data-stu-id="e827c-184">Errors Using SQL Compact 3.5</span></span>

<span data-ttu-id="e827c-185">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-185">Q.</span></span> <span data-ttu-id="e827c-186">将表拖出 SQL Server Compact 3.5 数据库时出错。</span><span class="sxs-lookup"><span data-stu-id="e827c-186">I get an error when I drag tables out of a SQL Server Compact 3.5 database.</span></span>

<span data-ttu-id="e827c-187">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-187">A.</span></span> <span data-ttu-id="e827c-188">对象关系设计器不支持 SQL Server Compact 3.5，不过 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 运行时也是如此。</span><span class="sxs-lookup"><span data-stu-id="e827c-188">The Object Relational Designer does not support SQL Server Compact 3.5, although the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime does.</span></span> <span data-ttu-id="e827c-189">在这种情况下，必须创建您自己的实体类并添加合适的属性。</span><span class="sxs-lookup"><span data-stu-id="e827c-189">In this situation, you must create your own entity classes and add the appropriate attributes.</span></span>

## <a name="errors-in-inheritance-relationships"></a><span data-ttu-id="e827c-190">继承关系中的错误</span><span class="sxs-lookup"><span data-stu-id="e827c-190">Errors in Inheritance Relationships</span></span>

<span data-ttu-id="e827c-191">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-191">Q.</span></span> <span data-ttu-id="e827c-192">我使用了对象关系设计器中的工具箱继承形状连接两个实体，但却出现错误。</span><span class="sxs-lookup"><span data-stu-id="e827c-192">I used the toolbox inheritance shape in the Object Relational Designer to connect two entities, but I get errors.</span></span>

<span data-ttu-id="e827c-193">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-193">A.</span></span> <span data-ttu-id="e827c-194">仅创建关系是不够的。</span><span class="sxs-lookup"><span data-stu-id="e827c-194">Creating the relationship is not enough.</span></span> <span data-ttu-id="e827c-195">还必须提供其他信息，例如鉴别器列、基类鉴别器值和派生类鉴别器值。</span><span class="sxs-lookup"><span data-stu-id="e827c-195">You must provide information such as the discriminator column, base class discriminator value, and derived class discriminator value.</span></span>

## <a name="provider-model"></a><span data-ttu-id="e827c-196">提供程序模型</span><span class="sxs-lookup"><span data-stu-id="e827c-196">Provider Model</span></span>

<span data-ttu-id="e827c-197">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-197">Q.</span></span> <span data-ttu-id="e827c-198">是否有公共提供程序模型可用？</span><span class="sxs-lookup"><span data-stu-id="e827c-198">Is a public provider model available?</span></span>

<span data-ttu-id="e827c-199">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-199">A.</span></span> <span data-ttu-id="e827c-200">没有任何公共提供程序模型可用。</span><span class="sxs-lookup"><span data-stu-id="e827c-200">No public provider model is available.</span></span> <span data-ttu-id="e827c-201">目前 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 仅支持 SQL Server 和 SQL Server Compact 3.5。</span><span class="sxs-lookup"><span data-stu-id="e827c-201">At this time, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] supports SQL Server and SQL Server Compact 3.5 only.</span></span>

## <a name="sql-injection-attacks"></a><span data-ttu-id="e827c-202">SQL 注入式攻击</span><span class="sxs-lookup"><span data-stu-id="e827c-202">SQL-Injection Attacks</span></span>

<span data-ttu-id="e827c-203">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-203">Q.</span></span> <span data-ttu-id="e827c-204">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 如何防范 SQL 注入式攻击？</span><span class="sxs-lookup"><span data-stu-id="e827c-204">How is [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] protected from SQL-injection attacks?</span></span>

<span data-ttu-id="e827c-205">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-205">A.</span></span> <span data-ttu-id="e827c-206">对于通过串联用户输入而组成的传统 SQL 查询，SQL 注入已成为重大风险。</span><span class="sxs-lookup"><span data-stu-id="e827c-206">SQL injection has been a significant risk for traditional SQL queries formed by concatenating user input.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e827c-207">通过在查询中使用 <xref:System.Data.SqlClient.SqlParameter> 来避免这种注入。</span><span class="sxs-lookup"><span data-stu-id="e827c-207">avoids such injection by using <xref:System.Data.SqlClient.SqlParameter> in queries.</span></span> <span data-ttu-id="e827c-208">用户输入会转换为参数值。</span><span class="sxs-lookup"><span data-stu-id="e827c-208">User input is turned into parameter values.</span></span> <span data-ttu-id="e827c-209">此方法可防止通过客户输入使用恶意命令。</span><span class="sxs-lookup"><span data-stu-id="e827c-209">This approach prevents malicious commands from being used from customer input.</span></span>

## <a name="changing-read-only-flag-in-dbml-files"></a><span data-ttu-id="e827c-210">更改 DBML 文件中的只读标志</span><span class="sxs-lookup"><span data-stu-id="e827c-210">Changing Read-only Flag in DBML Files</span></span>

<span data-ttu-id="e827c-211">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-211">Q.</span></span> <span data-ttu-id="e827c-212">如何在从 DBML 文件创建对象模型时消除某些属性中的设置器？</span><span class="sxs-lookup"><span data-stu-id="e827c-212">How do I eliminate setters from some properties when I create an object model from a DBML file?</span></span>

<span data-ttu-id="e827c-213">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-213">A.</span></span> <span data-ttu-id="e827c-214">对于此高级方案，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="e827c-214">Take the following steps for this advanced scenario:</span></span>

1. <span data-ttu-id="e827c-215">在 .dbml 文件中，通过将 <xref:System.Data.Linq.ITable.IsReadOnly%2A> 标志更改为 `True` 来修改属性。</span><span class="sxs-lookup"><span data-stu-id="e827c-215">In the .dbml file, modify the property by changing the <xref:System.Data.Linq.ITable.IsReadOnly%2A> flag to `True`.</span></span>

2. <span data-ttu-id="e827c-216">添加一个分部类。</span><span class="sxs-lookup"><span data-stu-id="e827c-216">Add a partial class.</span></span> <span data-ttu-id="e827c-217">为只读成员创建一个带参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="e827c-217">Create a constructor with parameters for the read-only members.</span></span>

3. <span data-ttu-id="e827c-218">检查默认的 <xref:System.Data.Linq.Mapping.UpdateCheck> 值 (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) 以确定该值对于您的应用程序是否正确。</span><span class="sxs-lookup"><span data-stu-id="e827c-218">Review the default <xref:System.Data.Linq.Mapping.UpdateCheck> value (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) to determine whether that is the correct value for your application.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="e827c-219">如果你使用的是 Visual Studio 中的对象关系设计器，则可能会覆盖你所做的更改。</span><span class="sxs-lookup"><span data-stu-id="e827c-219">If you are using the Object Relational Designer in Visual Studio, your changes might be overwritten.</span></span>

## <a name="aptca"></a><span data-ttu-id="e827c-220">APTCA</span><span class="sxs-lookup"><span data-stu-id="e827c-220">APTCA</span></span>

<span data-ttu-id="e827c-221">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-221">Q.</span></span> <span data-ttu-id="e827c-222">System.Data.Linq 是否标记为供部分受信任的代码使用？</span><span class="sxs-lookup"><span data-stu-id="e827c-222">Is System.Data.Linq marked for use by partially trusted code?</span></span>

<span data-ttu-id="e827c-223">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-223">A.</span></span> <span data-ttu-id="e827c-224">是的，System.web 程序集位于用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 属性标记的 .NET Framework 程序集中。</span><span class="sxs-lookup"><span data-stu-id="e827c-224">Yes, the System.Data.Linq.dll assembly is among those .NET Framework assemblies marked with the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="e827c-225">如果没有此标记，.NET Framework 中的程序集将仅供完全受信任的代码使用。</span><span class="sxs-lookup"><span data-stu-id="e827c-225">Without this marking, assemblies in the .NET Framework are intended for use only by fully trusted code.</span></span>

<span data-ttu-id="e827c-226">允许部分受信任的调用方 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的主要方案是允许从 Web 应用程序访问 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 程序集，其中的*信任*配置为 Medium。</span><span class="sxs-lookup"><span data-stu-id="e827c-226">The principal scenario in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] for allowing partially trusted callers is to enable the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly to be accessed from Web applications, where the *trust* configuration is Medium.</span></span>

## <a name="mapping-data-from-multiple-tables"></a><span data-ttu-id="e827c-227">映射来自多个表的数据</span><span class="sxs-lookup"><span data-stu-id="e827c-227">Mapping Data from Multiple Tables</span></span>

<span data-ttu-id="e827c-228">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-228">Q.</span></span> <span data-ttu-id="e827c-229">我的实体中的数据来自多个表。</span><span class="sxs-lookup"><span data-stu-id="e827c-229">The data in my entity comes from multiple tables.</span></span> <span data-ttu-id="e827c-230">如果映射这些数据？</span><span class="sxs-lookup"><span data-stu-id="e827c-230">How do I map it?</span></span>

<span data-ttu-id="e827c-231">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-231">A.</span></span> <span data-ttu-id="e827c-232">您可以在数据库中创建一个视图并将实体映射到该视图。</span><span class="sxs-lookup"><span data-stu-id="e827c-232">You can create a view in a database and map the entity to the view.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e827c-233">会为视图生成 SQL，与它为表生成 SQL 相同。</span><span class="sxs-lookup"><span data-stu-id="e827c-233">generates the same SQL for views as it does for tables.</span></span>

> [!NOTE]
> <span data-ttu-id="e827c-234">这种情况下的视图用法有一些限制。</span><span class="sxs-lookup"><span data-stu-id="e827c-234">The use of views in this scenario has limitations.</span></span> <span data-ttu-id="e827c-235">当基础视图支持在 <xref:System.Data.Linq.Table%601> 上执行的操作时，此方法最为安全。</span><span class="sxs-lookup"><span data-stu-id="e827c-235">This approach works most safely when the operations performed on <xref:System.Data.Linq.Table%601> are supported by the underlying view.</span></span> <span data-ttu-id="e827c-236">只有您知道要执行的操作。</span><span class="sxs-lookup"><span data-stu-id="e827c-236">Only you know which operations are intended.</span></span> <span data-ttu-id="e827c-237">例如，大多数应用程序都是只读的，而另一个就前往数字 `Create`仅通过对视图使用存储过程来 /`Update`/`Delete` 操作。</span><span class="sxs-lookup"><span data-stu-id="e827c-237">For example, most applications are read-only, and another sizeable number perform `Create`/`Update`/`Delete` operations only by using stored procedures against views.</span></span>

## <a name="connection-pooling"></a><span data-ttu-id="e827c-238">连接池</span><span class="sxs-lookup"><span data-stu-id="e827c-238">Connection Pooling</span></span>

<span data-ttu-id="e827c-239">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-239">Q.</span></span> <span data-ttu-id="e827c-240">是否具有对 <xref:System.Data.Linq.DataContext> 池有所帮助的构造？</span><span class="sxs-lookup"><span data-stu-id="e827c-240">Is there a construct that can help with <xref:System.Data.Linq.DataContext> pooling?</span></span>

<span data-ttu-id="e827c-241">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-241">A.</span></span> <span data-ttu-id="e827c-242">请不要试图重用 <xref:System.Data.Linq.DataContext> 的实例。</span><span class="sxs-lookup"><span data-stu-id="e827c-242">Do not try to reuse instances of <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="e827c-243">每个 <xref:System.Data.Linq.DataContext> 都会保持对应一个特定编辑/查询会话的状态（包括标识缓存）。</span><span class="sxs-lookup"><span data-stu-id="e827c-243">Each <xref:System.Data.Linq.DataContext> maintains state (including an identity cache) for one particular edit/query session.</span></span> <span data-ttu-id="e827c-244">若要获取基于数据库当前状态的新实例，请使用新的 <xref:System.Data.Linq.DataContext>。</span><span class="sxs-lookup"><span data-stu-id="e827c-244">To obtain new instances based on the current state of the database, use a new <xref:System.Data.Linq.DataContext>.</span></span>

<span data-ttu-id="e827c-245">你仍可以使用基础 ADO.NET 连接池。</span><span class="sxs-lookup"><span data-stu-id="e827c-245">You can still use underlying ADO.NET connection pooling.</span></span> <span data-ttu-id="e827c-246">有关详细信息，请参阅 [SQL Server 连接池 (ADO.NET)](../../sql-server-connection-pooling.md)。</span><span class="sxs-lookup"><span data-stu-id="e827c-246">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../sql-server-connection-pooling.md).</span></span>

## <a name="second-datacontext-is-not-updated"></a><span data-ttu-id="e827c-247">第二个 DataContext 未更新</span><span class="sxs-lookup"><span data-stu-id="e827c-247">Second DataContext Is Not Updated</span></span>

<span data-ttu-id="e827c-248">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-248">Q.</span></span> <span data-ttu-id="e827c-249">我使用 <xref:System.Data.Linq.DataContext> 的一个实例存储数据库中的值。</span><span class="sxs-lookup"><span data-stu-id="e827c-249">I used one instance of <xref:System.Data.Linq.DataContext> to store values in the database.</span></span> <span data-ttu-id="e827c-250">但是，相同数据库上的另一个 <xref:System.Data.Linq.DataContext> 未反映更新的值。</span><span class="sxs-lookup"><span data-stu-id="e827c-250">However, a second <xref:System.Data.Linq.DataContext> on the same database does not reflect the updated values.</span></span> <span data-ttu-id="e827c-251">第二个 <xref:System.Data.Linq.DataContext> 实例似乎返回缓存的值。</span><span class="sxs-lookup"><span data-stu-id="e827c-251">The second <xref:System.Data.Linq.DataContext> instance seems to return cached values.</span></span>

<span data-ttu-id="e827c-252">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-252">A.</span></span> <span data-ttu-id="e827c-253">此行为是设计使然。</span><span class="sxs-lookup"><span data-stu-id="e827c-253">This behavior is by design.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="e827c-254">会继续返回您在第一个实例中看到的相同实例/值。</span><span class="sxs-lookup"><span data-stu-id="e827c-254">continues to return the same instances/values that you saw in the first instance.</span></span> <span data-ttu-id="e827c-255">在进行更新时使用开放式并发。</span><span class="sxs-lookup"><span data-stu-id="e827c-255">When you make updates, you use optimistic concurrency.</span></span> <span data-ttu-id="e827c-256">原始数据用于检查当前数据库状态，以确定该数据实际上仍未更改。</span><span class="sxs-lookup"><span data-stu-id="e827c-256">The original data is used to check against the current database state to assert that it is in fact still unchanged.</span></span> <span data-ttu-id="e827c-257">如果该数据已更改，则会发生冲突，您的应用程序必须解决该冲突。</span><span class="sxs-lookup"><span data-stu-id="e827c-257">If it has changed, a conflict occurs and your application must resolve it.</span></span> <span data-ttu-id="e827c-258">您的应用程序可以选择将原始状态重置为当前数据库状态并尝试再次更新。</span><span class="sxs-lookup"><span data-stu-id="e827c-258">One option of your application is to reset the original state to the current database state and to try the update again.</span></span> <span data-ttu-id="e827c-259">有关详细信息，请参阅[如何：管理更改冲突](how-to-manage-change-conflicts.md)。</span><span class="sxs-lookup"><span data-stu-id="e827c-259">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>

<span data-ttu-id="e827c-260">您也可以将 <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> 设置为 false，这样可以关闭缓存和更改跟踪。</span><span class="sxs-lookup"><span data-stu-id="e827c-260">You can also set <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> to false, which turns off caching and change tracking.</span></span> <span data-ttu-id="e827c-261">然后便可以在每次查询时检索最新值。</span><span class="sxs-lookup"><span data-stu-id="e827c-261">You can then retrieve the latest values every time that you query.</span></span>

## <a name="cannot-call-submitchanges-in-read-only-mode"></a><span data-ttu-id="e827c-262">无法在只读模式下调用 SubmitChanges</span><span class="sxs-lookup"><span data-stu-id="e827c-262">Cannot Call SubmitChanges in Read-only Mode</span></span>

<span data-ttu-id="e827c-263">问：</span><span class="sxs-lookup"><span data-stu-id="e827c-263">Q.</span></span> <span data-ttu-id="e827c-264">当我试图在只读模式下调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时收到错误消息。</span><span class="sxs-lookup"><span data-stu-id="e827c-264">When I try to call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> in read-only mode, I get an error.</span></span>

<span data-ttu-id="e827c-265">答：</span><span class="sxs-lookup"><span data-stu-id="e827c-265">A.</span></span> <span data-ttu-id="e827c-266">只读模式关闭了上下文跟踪更改的功能。</span><span class="sxs-lookup"><span data-stu-id="e827c-266">Read-only mode turns off the ability of the context to track changes.</span></span>

## <a name="see-also"></a><span data-ttu-id="e827c-267">另请参阅</span><span class="sxs-lookup"><span data-stu-id="e827c-267">See also</span></span>

- [<span data-ttu-id="e827c-268">引用</span><span class="sxs-lookup"><span data-stu-id="e827c-268">Reference</span></span>](reference.md)
- [<span data-ttu-id="e827c-269">疑难解答</span><span class="sxs-lookup"><span data-stu-id="e827c-269">Troubleshooting</span></span>](troubleshooting.md)
- [<span data-ttu-id="e827c-270">LINQ to SQL 中的安全性</span><span class="sxs-lookup"><span data-stu-id="e827c-270">Security in LINQ to SQL</span></span>](security-in-linq-to-sql.md)
