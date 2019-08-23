---
title: 架构限制
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 73d2980e-e73c-4987-913a-8ddc93d09144
ms.openlocfilehash: 1a2c32d133799ee5338c18d0f51bced49cb3dc4b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963187"
---
# <a name="schema-restrictions"></a><span data-ttu-id="cea53-102">架构限制</span><span class="sxs-lookup"><span data-stu-id="cea53-102">Schema Restrictions</span></span>
<span data-ttu-id="cea53-103">**GetSchema**方法的第二个可选参数是用于限制返回的架构信息量的限制, 并将其作为字符串数组传递到**GetSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="cea53-103">The second optional parameter of the **GetSchema** method is the restrictions that are used to limit the amount of schema information returned, and it is passed to the **GetSchema** method as an array of strings.</span></span> <span data-ttu-id="cea53-104">在数组中的位置确定可以传递的值，这等效于限制数。</span><span class="sxs-lookup"><span data-stu-id="cea53-104">The position in the array determines the values that you can pass, and this is equivalent to the restriction number.</span></span>  
  
 <span data-ttu-id="cea53-105">例如，下表说明使用适用于 SQL Server 的 .NET Framework 数据提供程序时“Tables”架构集合支持的限制。</span><span class="sxs-lookup"><span data-stu-id="cea53-105">For example, the following table describes the restrictions supported by the "Tables" schema collection using the .NET Framework Data Provider for SQL Server.</span></span> <span data-ttu-id="cea53-106">SQL Server 架构集合的其他限制在本主题的结尾处列出。</span><span class="sxs-lookup"><span data-stu-id="cea53-106">Additional restrictions for SQL Server schema collections are listed at the end of this topic.</span></span>  
  
|<span data-ttu-id="cea53-107">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-107">Restriction Name</span></span>|<span data-ttu-id="cea53-108">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-108">Parameter Name</span></span>|<span data-ttu-id="cea53-109">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-109">Restriction Default</span></span>|<span data-ttu-id="cea53-110">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-110">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-111">Catalog</span><span class="sxs-lookup"><span data-stu-id="cea53-111">Catalog</span></span>|@Catalog|<span data-ttu-id="cea53-112">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cea53-112">TABLE_CATALOG</span></span>|<span data-ttu-id="cea53-113">1</span><span class="sxs-lookup"><span data-stu-id="cea53-113">1</span></span>|  
|<span data-ttu-id="cea53-114">Owner</span><span class="sxs-lookup"><span data-stu-id="cea53-114">Owner</span></span>|@Owner|<span data-ttu-id="cea53-115">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cea53-115">TABLE_SCHEMA</span></span>|<span data-ttu-id="cea53-116">2</span><span class="sxs-lookup"><span data-stu-id="cea53-116">2</span></span>|  
|<span data-ttu-id="cea53-117">表</span><span class="sxs-lookup"><span data-stu-id="cea53-117">Table</span></span>|@Name|<span data-ttu-id="cea53-118">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-118">TABLE_NAME</span></span>|<span data-ttu-id="cea53-119">3</span><span class="sxs-lookup"><span data-stu-id="cea53-119">3</span></span>|  
|<span data-ttu-id="cea53-120">TableType</span><span class="sxs-lookup"><span data-stu-id="cea53-120">TableType</span></span>|@TableType|<span data-ttu-id="cea53-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cea53-121">TABLE_TYPE</span></span>|<span data-ttu-id="cea53-122">4</span><span class="sxs-lookup"><span data-stu-id="cea53-122">4</span></span>|  
  
## <a name="specifying-restriction-values"></a><span data-ttu-id="cea53-123">指定限制值</span><span class="sxs-lookup"><span data-stu-id="cea53-123">Specifying Restriction Values</span></span>  
 <span data-ttu-id="cea53-124">要使用“Tables”架构集合的一个限制，只需创建一个包含四个元素的字符串数组，然后在与限制数匹配的元素中填充值。</span><span class="sxs-lookup"><span data-stu-id="cea53-124">To use one of the restrictions of the "Tables" schema collection, simply create an array of strings with four elements, then place a value in the element that matches the restriction number.</span></span> <span data-ttu-id="cea53-125">例如, 若要将**GetSchema**方法返回的表仅限制为 "sales" 架构中的表, 请先将数组的第二个元素设置为 "sales", 然后再将其传递给**GetSchema**方法。</span><span class="sxs-lookup"><span data-stu-id="cea53-125">For example, to restrict the tables returned by the **GetSchema** method to only those tables in the "Sales" schema, set the second element of the array to "Sales" before passing it to the **GetSchema** method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cea53-126">`SqlClient` 和 `OracleClient` 的限制集合还有附加的 `ParameterName` 列。</span><span class="sxs-lookup"><span data-stu-id="cea53-126">The restrictions collections for `SqlClient` and `OracleClient` have an additional `ParameterName` column.</span></span> <span data-ttu-id="cea53-127">为了向后兼容，仍提供限制默认列，但是目前忽略该列。</span><span class="sxs-lookup"><span data-stu-id="cea53-127">The restriction default column is still there for backwards compatibility, but is currently ignored.</span></span> <span data-ttu-id="cea53-128">在指定限制值时，应使用参数化查询（而不是字符串替换）来最大程度地降低受到 SQL 注入式攻击的风险。</span><span class="sxs-lookup"><span data-stu-id="cea53-128">Parameterized queries rather than string replacement should be used to minimize the risk of an SQL injection attack when specifying restriction values.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cea53-129">数组中的元素数必须小于或等于指定架构集合支持的限制数，否则，将引发 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="cea53-129">The number of elements in the array must be less than or equal to the number of restrictions supported for the specified schema collection else an <xref:System.ArgumentException> will be thrown.</span></span> <span data-ttu-id="cea53-130">可以小于最大限制数。</span><span class="sxs-lookup"><span data-stu-id="cea53-130">There can be fewer than the maximum number of restrictions.</span></span> <span data-ttu-id="cea53-131">缺少的限制假定为空（无限制）。</span><span class="sxs-lookup"><span data-stu-id="cea53-131">The missing restrictions are assumed to be null (unrestricted).</span></span>  
  
 <span data-ttu-id="cea53-132">可以通过将**GetSchema**方法与限制架构集合的名称 (即 "限制") 一起调用, 来 .NET Framework 查询受支持的限制列表。</span><span class="sxs-lookup"><span data-stu-id="cea53-132">You can query a .NET Framework managed provider to determine the list of supported restrictions by calling the **GetSchema** method with the name of the restrictions schema collection, which is "Restrictions".</span></span> <span data-ttu-id="cea53-133">此时将返回 <xref:System.Data.DataTable>，包含集合名称、限制名称、默认限制值和限制数的列表。</span><span class="sxs-lookup"><span data-stu-id="cea53-133">This will return a <xref:System.Data.DataTable> with a list of the collection names, the restriction names, the default restriction values, and the restriction numbers.</span></span>  
  
### <a name="example"></a><span data-ttu-id="cea53-134">示例</span><span class="sxs-lookup"><span data-stu-id="cea53-134">Example</span></span>  
 <span data-ttu-id="cea53-135">下面的示例演示如何使用<xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> SQL Server <xref:System.Data.SqlClient.SqlConnection>类的 .NET Framework 数据提供程序的方法来检索与**AdventureWorks**示例数据库中包含的所有表有关的架构信息。并且将返回的信息仅限于 "销售" 架构中的表:</span><span class="sxs-lookup"><span data-stu-id="cea53-135">The following examples demonstrate how to use the <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of the .NET Framework Data Provider for the SQL Server <xref:System.Data.SqlClient.SqlConnection> class to retrieve schema information about all of the tables contained in the **AdventureWorks** sample database, and to restrict the information returned to only those tables in the "Sales" schema:</span></span>  
  
```vb  
Imports System.Data.SqlClient  
  
Module Module1  
Sub Main()  
  Dim connectionString As String = _  
    "Data Source=(local);Database=AdventureWorks;" & _  
       "Integrated Security=true;";  
  
  Dim restrictions(3) As String  
  Using connection As New SqlConnection(connectionString)  
    connection.Open()  
  
    'Specify the restrictions.  
    restrictions(1) = "Sales"  
    Dim table As DataTable = connection.GetSchema("Tables", _  
       restrictions)  
  
    ' Display the contents of the table.  
      For Each row As DataRow In table.Rows  
         For Each col As DataColumn In table.Columns  
            Console.WriteLine("{0} = {1}", col.ColumnName, row(col))  
         Next  
         Console.WriteLine("============================")  
      Next  
    Console.WriteLine("Press any key to continue.")  
    Console.ReadKey()  
  End Using  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
class Program  
{  
  static void Main()  
  {  
    string connectionString =   
       "Data Source=(local);Database=AdventureWorks;" +  
       "Integrated Security=true;";  
    using (SqlConnection connection =  
       new SqlConnection(connectionString))  
    {  
        connection.Open();  
  
        // Specify the restrictions.  
        string[] restrictions = new string[4];  
        restrictions[1] = "Sales";  
        System.Data.DataTable table = connection.GetSchema(  
          "Tables", restrictions);  
  
        // Display the contents of the table.  
        foreach (System.Data.DataRow row in table.Rows)  
        {  
            foreach (System.Data.DataColumn col in table.Columns)  
            {  
                Console.WriteLine("{0} = {1}",   
                  col.ColumnName, row[col]);  
            }  
            Console.WriteLine("============================");  
        }  
        Console.WriteLine("Press any key to continue.");  
        Console.ReadKey();  
    }  
  }  
  
  private static string GetConnectionString()  
  {  
     // To avoid storing the connection string in your code,  
     // you can retrieve it from a configuration file.  
     return "Data Source=(local);Database=AdventureWorks;" +  
        "Integrated Security=true;";  
  }  
  
  private static void DisplayData(System.Data.DataTable table)  
  {  
     foreach (System.Data.DataRow row in table.Rows)  
     {  
        foreach (System.Data.DataColumn col in table.Columns)  
        {  
           Console.WriteLine("{0} = {1}", col.ColumnName, row[col]);  
        }  
     Console.WriteLine("============================");  
     }  
  }  
}  
```  
  
## <a name="sql-server-schema-restrictions"></a><span data-ttu-id="cea53-136">SQL Server 架构限制</span><span class="sxs-lookup"><span data-stu-id="cea53-136">SQL Server Schema Restrictions</span></span>  
 <span data-ttu-id="cea53-137">下表列出了 SQL Server 架构集合的限制。</span><span class="sxs-lookup"><span data-stu-id="cea53-137">The following tables list the restrictions for SQL Server schema collections.</span></span>  
  
### <a name="users"></a><span data-ttu-id="cea53-138">用户</span><span class="sxs-lookup"><span data-stu-id="cea53-138">Users</span></span>  
  
|<span data-ttu-id="cea53-139">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-139">Restriction Name</span></span>|<span data-ttu-id="cea53-140">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-140">Parameter Name</span></span>|<span data-ttu-id="cea53-141">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-141">Restriction Default</span></span>|<span data-ttu-id="cea53-142">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-142">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-143">User_Name</span><span class="sxs-lookup"><span data-stu-id="cea53-143">User_Name</span></span>|@Name|<span data-ttu-id="cea53-144">NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-144">name</span></span>|<span data-ttu-id="cea53-145">1</span><span class="sxs-lookup"><span data-stu-id="cea53-145">1</span></span>|  
  
### <a name="databases"></a><span data-ttu-id="cea53-146">数据库</span><span class="sxs-lookup"><span data-stu-id="cea53-146">Databases</span></span>  
  
|<span data-ttu-id="cea53-147">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-147">Restriction Name</span></span>|<span data-ttu-id="cea53-148">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-148">Parameter Name</span></span>|<span data-ttu-id="cea53-149">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-149">Restriction Default</span></span>|<span data-ttu-id="cea53-150">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-150">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-151">name</span><span class="sxs-lookup"><span data-stu-id="cea53-151">Name</span></span>|@Name|<span data-ttu-id="cea53-152">name</span><span class="sxs-lookup"><span data-stu-id="cea53-152">Name</span></span>|<span data-ttu-id="cea53-153">1</span><span class="sxs-lookup"><span data-stu-id="cea53-153">1</span></span>|  
  
### <a name="tables"></a><span data-ttu-id="cea53-154">表</span><span class="sxs-lookup"><span data-stu-id="cea53-154">Tables</span></span>  
  
|<span data-ttu-id="cea53-155">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-155">Restriction Name</span></span>|<span data-ttu-id="cea53-156">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-156">Parameter Name</span></span>|<span data-ttu-id="cea53-157">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-157">Restriction Default</span></span>|<span data-ttu-id="cea53-158">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-158">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-159">Catalog</span><span class="sxs-lookup"><span data-stu-id="cea53-159">Catalog</span></span>|@Catalog|<span data-ttu-id="cea53-160">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cea53-160">TABLE_CATALOG</span></span>|<span data-ttu-id="cea53-161">1</span><span class="sxs-lookup"><span data-stu-id="cea53-161">1</span></span>|  
|<span data-ttu-id="cea53-162">Owner</span><span class="sxs-lookup"><span data-stu-id="cea53-162">Owner</span></span>|@Owner|<span data-ttu-id="cea53-163">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cea53-163">TABLE_SCHEMA</span></span>|<span data-ttu-id="cea53-164">2</span><span class="sxs-lookup"><span data-stu-id="cea53-164">2</span></span>|  
|<span data-ttu-id="cea53-165">表</span><span class="sxs-lookup"><span data-stu-id="cea53-165">Table</span></span>|@Name|<span data-ttu-id="cea53-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-166">TABLE_NAME</span></span>|<span data-ttu-id="cea53-167">3</span><span class="sxs-lookup"><span data-stu-id="cea53-167">3</span></span>|  
|<span data-ttu-id="cea53-168">TableType</span><span class="sxs-lookup"><span data-stu-id="cea53-168">TableType</span></span>|@TableType|<span data-ttu-id="cea53-169">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cea53-169">TABLE_TYPE</span></span>|<span data-ttu-id="cea53-170">4</span><span class="sxs-lookup"><span data-stu-id="cea53-170">4</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="cea53-171">列</span><span class="sxs-lookup"><span data-stu-id="cea53-171">Columns</span></span>  
  
|<span data-ttu-id="cea53-172">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-172">Restriction Name</span></span>|<span data-ttu-id="cea53-173">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-173">Parameter Name</span></span>|<span data-ttu-id="cea53-174">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-174">Restriction Default</span></span>|<span data-ttu-id="cea53-175">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-175">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-176">Catalog</span><span class="sxs-lookup"><span data-stu-id="cea53-176">Catalog</span></span>|@Catalog|<span data-ttu-id="cea53-177">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cea53-177">TABLE_CATALOG</span></span>|<span data-ttu-id="cea53-178">1</span><span class="sxs-lookup"><span data-stu-id="cea53-178">1</span></span>|  
|<span data-ttu-id="cea53-179">Owner</span><span class="sxs-lookup"><span data-stu-id="cea53-179">Owner</span></span>|@Owner|<span data-ttu-id="cea53-180">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cea53-180">TABLE_SCHEMA</span></span>|<span data-ttu-id="cea53-181">2</span><span class="sxs-lookup"><span data-stu-id="cea53-181">2</span></span>|  
|<span data-ttu-id="cea53-182">表</span><span class="sxs-lookup"><span data-stu-id="cea53-182">Table</span></span>|@Table|<span data-ttu-id="cea53-183">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-183">TABLE_NAME</span></span>|<span data-ttu-id="cea53-184">3</span><span class="sxs-lookup"><span data-stu-id="cea53-184">3</span></span>|  
|<span data-ttu-id="cea53-185">列</span><span class="sxs-lookup"><span data-stu-id="cea53-185">Column</span></span>|@Column|<span data-ttu-id="cea53-186">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-186">COLUMN_NAME</span></span>|<span data-ttu-id="cea53-187">4</span><span class="sxs-lookup"><span data-stu-id="cea53-187">4</span></span>|  
  
### <a name="structuredtypemembers"></a><span data-ttu-id="cea53-188">StructuredTypeMembers</span><span class="sxs-lookup"><span data-stu-id="cea53-188">StructuredTypeMembers</span></span>  
  
|<span data-ttu-id="cea53-189">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-189">Restriction Name</span></span>|<span data-ttu-id="cea53-190">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-190">Parameter Name</span></span>|<span data-ttu-id="cea53-191">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-191">Restriction Default</span></span>|<span data-ttu-id="cea53-192">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-192">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-193">Catalog</span><span class="sxs-lookup"><span data-stu-id="cea53-193">Catalog</span></span>|@Catalog|<span data-ttu-id="cea53-194">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cea53-194">TABLE_CATALOG</span></span>|<span data-ttu-id="cea53-195">1</span><span class="sxs-lookup"><span data-stu-id="cea53-195">1</span></span>|  
|<span data-ttu-id="cea53-196">Owner</span><span class="sxs-lookup"><span data-stu-id="cea53-196">Owner</span></span>|@Owner|<span data-ttu-id="cea53-197">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cea53-197">TABLE_SCHEMA</span></span>|<span data-ttu-id="cea53-198">2</span><span class="sxs-lookup"><span data-stu-id="cea53-198">2</span></span>|  
|<span data-ttu-id="cea53-199">表</span><span class="sxs-lookup"><span data-stu-id="cea53-199">Table</span></span>|@Table|<span data-ttu-id="cea53-200">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-200">TABLE_NAME</span></span>|<span data-ttu-id="cea53-201">3</span><span class="sxs-lookup"><span data-stu-id="cea53-201">3</span></span>|  
|<span data-ttu-id="cea53-202">列</span><span class="sxs-lookup"><span data-stu-id="cea53-202">Column</span></span>|@Column|<span data-ttu-id="cea53-203">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-203">COLUMN_NAME</span></span>|<span data-ttu-id="cea53-204">4</span><span class="sxs-lookup"><span data-stu-id="cea53-204">4</span></span>|  
  
### <a name="views"></a><span data-ttu-id="cea53-205">Views</span><span class="sxs-lookup"><span data-stu-id="cea53-205">Views</span></span>  
  
|<span data-ttu-id="cea53-206">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-206">Restriction Name</span></span>|<span data-ttu-id="cea53-207">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-207">Parameter Name</span></span>|<span data-ttu-id="cea53-208">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-208">Restriction Default</span></span>|<span data-ttu-id="cea53-209">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-209">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-210">Catalog</span><span class="sxs-lookup"><span data-stu-id="cea53-210">Catalog</span></span>|@Catalog|<span data-ttu-id="cea53-211">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cea53-211">TABLE_CATALOG</span></span>|<span data-ttu-id="cea53-212">1</span><span class="sxs-lookup"><span data-stu-id="cea53-212">1</span></span>|  
|<span data-ttu-id="cea53-213">Owner</span><span class="sxs-lookup"><span data-stu-id="cea53-213">Owner</span></span>|@Owner|<span data-ttu-id="cea53-214">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cea53-214">TABLE_SCHEMA</span></span>|<span data-ttu-id="cea53-215">2</span><span class="sxs-lookup"><span data-stu-id="cea53-215">2</span></span>|  
|<span data-ttu-id="cea53-216">表</span><span class="sxs-lookup"><span data-stu-id="cea53-216">Table</span></span>|@Table|<span data-ttu-id="cea53-217">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-217">TABLE_NAME</span></span>|<span data-ttu-id="cea53-218">3</span><span class="sxs-lookup"><span data-stu-id="cea53-218">3</span></span>|  
  
### <a name="viewcolumns"></a><span data-ttu-id="cea53-219">ViewColumns</span><span class="sxs-lookup"><span data-stu-id="cea53-219">ViewColumns</span></span>  
  
|<span data-ttu-id="cea53-220">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-220">Restriction Name</span></span>|<span data-ttu-id="cea53-221">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-221">Parameter Name</span></span>|<span data-ttu-id="cea53-222">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-222">Restriction Default</span></span>|<span data-ttu-id="cea53-223">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-223">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-224">Catalog</span><span class="sxs-lookup"><span data-stu-id="cea53-224">Catalog</span></span>|@Catalog|<span data-ttu-id="cea53-225">VIEW_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cea53-225">VIEW_CATALOG</span></span>|<span data-ttu-id="cea53-226">1</span><span class="sxs-lookup"><span data-stu-id="cea53-226">1</span></span>|  
|<span data-ttu-id="cea53-227">Owner</span><span class="sxs-lookup"><span data-stu-id="cea53-227">Owner</span></span>|@Owner|<span data-ttu-id="cea53-228">VIEW_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cea53-228">VIEW_SCHEMA</span></span>|<span data-ttu-id="cea53-229">2</span><span class="sxs-lookup"><span data-stu-id="cea53-229">2</span></span>|  
|<span data-ttu-id="cea53-230">表</span><span class="sxs-lookup"><span data-stu-id="cea53-230">Table</span></span>|@Table|<span data-ttu-id="cea53-231">VIEW_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-231">VIEW_NAME</span></span>|<span data-ttu-id="cea53-232">3</span><span class="sxs-lookup"><span data-stu-id="cea53-232">3</span></span>|  
|<span data-ttu-id="cea53-233">列</span><span class="sxs-lookup"><span data-stu-id="cea53-233">Column</span></span>|@Column|<span data-ttu-id="cea53-234">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-234">COLUMN_NAME</span></span>|<span data-ttu-id="cea53-235">4</span><span class="sxs-lookup"><span data-stu-id="cea53-235">4</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="cea53-236">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="cea53-236">ProcedureParameters</span></span>  
  
|<span data-ttu-id="cea53-237">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-237">Restriction Name</span></span>|<span data-ttu-id="cea53-238">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-238">Parameter Name</span></span>|<span data-ttu-id="cea53-239">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-239">Restriction Default</span></span>|<span data-ttu-id="cea53-240">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-240">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-241">Catalog</span><span class="sxs-lookup"><span data-stu-id="cea53-241">Catalog</span></span>|@Catalog|<span data-ttu-id="cea53-242">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cea53-242">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="cea53-243">1</span><span class="sxs-lookup"><span data-stu-id="cea53-243">1</span></span>|  
|<span data-ttu-id="cea53-244">Owner</span><span class="sxs-lookup"><span data-stu-id="cea53-244">Owner</span></span>|@Owner|<span data-ttu-id="cea53-245">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cea53-245">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="cea53-246">2</span><span class="sxs-lookup"><span data-stu-id="cea53-246">2</span></span>|  
|<span data-ttu-id="cea53-247">name</span><span class="sxs-lookup"><span data-stu-id="cea53-247">Name</span></span>|@Name|<span data-ttu-id="cea53-248">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-248">SPECIFIC_NAME</span></span>|<span data-ttu-id="cea53-249">3</span><span class="sxs-lookup"><span data-stu-id="cea53-249">3</span></span>|  
|<span data-ttu-id="cea53-250">参数</span><span class="sxs-lookup"><span data-stu-id="cea53-250">Parameter</span></span>|@Parameter|<span data-ttu-id="cea53-251">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-251">PARAMETER_NAME</span></span>|<span data-ttu-id="cea53-252">4</span><span class="sxs-lookup"><span data-stu-id="cea53-252">4</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="cea53-253">过程</span><span class="sxs-lookup"><span data-stu-id="cea53-253">Procedures</span></span>  
  
|<span data-ttu-id="cea53-254">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-254">Restriction Name</span></span>|<span data-ttu-id="cea53-255">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-255">Parameter Name</span></span>|<span data-ttu-id="cea53-256">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-256">Restriction Default</span></span>|<span data-ttu-id="cea53-257">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-257">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="cea53-258">Catalog</span></span>|@Catalog|<span data-ttu-id="cea53-259">SPECIFIC_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cea53-259">SPECIFIC_CATALOG</span></span>|<span data-ttu-id="cea53-260">1</span><span class="sxs-lookup"><span data-stu-id="cea53-260">1</span></span>|  
|<span data-ttu-id="cea53-261">Owner</span><span class="sxs-lookup"><span data-stu-id="cea53-261">Owner</span></span>|@Owner|<span data-ttu-id="cea53-262">SPECIFIC_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cea53-262">SPECIFIC_SCHEMA</span></span>|<span data-ttu-id="cea53-263">2</span><span class="sxs-lookup"><span data-stu-id="cea53-263">2</span></span>|  
|<span data-ttu-id="cea53-264">name</span><span class="sxs-lookup"><span data-stu-id="cea53-264">Name</span></span>|@Name|<span data-ttu-id="cea53-265">SPECIFIC_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-265">SPECIFIC_NAME</span></span>|<span data-ttu-id="cea53-266">3</span><span class="sxs-lookup"><span data-stu-id="cea53-266">3</span></span>|  
|<span data-ttu-id="cea53-267">类型</span><span class="sxs-lookup"><span data-stu-id="cea53-267">Type</span></span>|@Type|<span data-ttu-id="cea53-268">ROUTINE_TYPE</span><span class="sxs-lookup"><span data-stu-id="cea53-268">ROUTINE_TYPE</span></span>|<span data-ttu-id="cea53-269">4</span><span class="sxs-lookup"><span data-stu-id="cea53-269">4</span></span>|  
  
### <a name="indexcolumns"></a><span data-ttu-id="cea53-270">IndexColumns</span><span class="sxs-lookup"><span data-stu-id="cea53-270">IndexColumns</span></span>  
  
|<span data-ttu-id="cea53-271">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-271">Restriction Name</span></span>|<span data-ttu-id="cea53-272">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-272">Parameter Name</span></span>|<span data-ttu-id="cea53-273">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-273">Restriction Default</span></span>|<span data-ttu-id="cea53-274">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-274">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-275">Catalog</span><span class="sxs-lookup"><span data-stu-id="cea53-275">Catalog</span></span>|@Catalog|<span data-ttu-id="cea53-276">db_name()</span><span class="sxs-lookup"><span data-stu-id="cea53-276">db_name()</span></span>|<span data-ttu-id="cea53-277">1</span><span class="sxs-lookup"><span data-stu-id="cea53-277">1</span></span>|  
|<span data-ttu-id="cea53-278">Owner</span><span class="sxs-lookup"><span data-stu-id="cea53-278">Owner</span></span>|@Owner|<span data-ttu-id="cea53-279">user_name()</span><span class="sxs-lookup"><span data-stu-id="cea53-279">user_name()</span></span>|<span data-ttu-id="cea53-280">2</span><span class="sxs-lookup"><span data-stu-id="cea53-280">2</span></span>|  
|<span data-ttu-id="cea53-281">表</span><span class="sxs-lookup"><span data-stu-id="cea53-281">Table</span></span>|@Table|<span data-ttu-id="cea53-282">o.name</span><span class="sxs-lookup"><span data-stu-id="cea53-282">o.name</span></span>|<span data-ttu-id="cea53-283">3</span><span class="sxs-lookup"><span data-stu-id="cea53-283">3</span></span>|  
|<span data-ttu-id="cea53-284">ConstraintName</span><span class="sxs-lookup"><span data-stu-id="cea53-284">ConstraintName</span></span>|@ConstraintName|<span data-ttu-id="cea53-285">x.name</span><span class="sxs-lookup"><span data-stu-id="cea53-285">x.name</span></span>|<span data-ttu-id="cea53-286">4</span><span class="sxs-lookup"><span data-stu-id="cea53-286">4</span></span>|  
|<span data-ttu-id="cea53-287">列</span><span class="sxs-lookup"><span data-stu-id="cea53-287">Column</span></span>|@Column|<span data-ttu-id="cea53-288">c.name</span><span class="sxs-lookup"><span data-stu-id="cea53-288">c.name</span></span>|<span data-ttu-id="cea53-289">5</span><span class="sxs-lookup"><span data-stu-id="cea53-289">5</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="cea53-290">索引</span><span class="sxs-lookup"><span data-stu-id="cea53-290">Indexes</span></span>  
  
|<span data-ttu-id="cea53-291">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-291">Restriction Name</span></span>|<span data-ttu-id="cea53-292">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-292">Parameter Name</span></span>|<span data-ttu-id="cea53-293">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-293">Restriction Default</span></span>|<span data-ttu-id="cea53-294">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-294">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-295">Catalog</span><span class="sxs-lookup"><span data-stu-id="cea53-295">Catalog</span></span>|@Catalog|<span data-ttu-id="cea53-296">db_name()</span><span class="sxs-lookup"><span data-stu-id="cea53-296">db_name()</span></span>|<span data-ttu-id="cea53-297">1</span><span class="sxs-lookup"><span data-stu-id="cea53-297">1</span></span>|  
|<span data-ttu-id="cea53-298">Owner</span><span class="sxs-lookup"><span data-stu-id="cea53-298">Owner</span></span>|@Owner|<span data-ttu-id="cea53-299">user_name()</span><span class="sxs-lookup"><span data-stu-id="cea53-299">user_name()</span></span>|<span data-ttu-id="cea53-300">2</span><span class="sxs-lookup"><span data-stu-id="cea53-300">2</span></span>|  
|<span data-ttu-id="cea53-301">表</span><span class="sxs-lookup"><span data-stu-id="cea53-301">Table</span></span>|@Table|<span data-ttu-id="cea53-302">o.name</span><span class="sxs-lookup"><span data-stu-id="cea53-302">o.name</span></span>|<span data-ttu-id="cea53-303">3</span><span class="sxs-lookup"><span data-stu-id="cea53-303">3</span></span>|  
  
### <a name="userdefinedtypes"></a><span data-ttu-id="cea53-304">UserDefinedTypes</span><span class="sxs-lookup"><span data-stu-id="cea53-304">UserDefinedTypes</span></span>  
  
|<span data-ttu-id="cea53-305">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-305">Restriction Name</span></span>|<span data-ttu-id="cea53-306">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-306">Parameter Name</span></span>|<span data-ttu-id="cea53-307">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-307">Restriction Default</span></span>|<span data-ttu-id="cea53-308">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-308">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-309">assembly_name</span><span class="sxs-lookup"><span data-stu-id="cea53-309">assembly_name</span></span>|@AssemblyName|<span data-ttu-id="cea53-310">assemblies.name</span><span class="sxs-lookup"><span data-stu-id="cea53-310">assemblies.name</span></span>|<span data-ttu-id="cea53-311">1</span><span class="sxs-lookup"><span data-stu-id="cea53-311">1</span></span>|  
|<span data-ttu-id="cea53-312">udt_name</span><span class="sxs-lookup"><span data-stu-id="cea53-312">udt_name</span></span>|@UDTName|<span data-ttu-id="cea53-313">types.assembly_class</span><span class="sxs-lookup"><span data-stu-id="cea53-313">types.assembly_class</span></span>|<span data-ttu-id="cea53-314">2</span><span class="sxs-lookup"><span data-stu-id="cea53-314">2</span></span>|  
  
### <a name="foreignkeys"></a><span data-ttu-id="cea53-315">ForeignKeys</span><span class="sxs-lookup"><span data-stu-id="cea53-315">ForeignKeys</span></span>  
  
|<span data-ttu-id="cea53-316">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-316">Restriction Name</span></span>|<span data-ttu-id="cea53-317">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-317">Parameter Name</span></span>|<span data-ttu-id="cea53-318">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-318">Restriction Default</span></span>|<span data-ttu-id="cea53-319">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-319">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-320">Catalog</span><span class="sxs-lookup"><span data-stu-id="cea53-320">Catalog</span></span>|@Catalog|<span data-ttu-id="cea53-321">CONSTRAINT_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cea53-321">CONSTRAINT_CATALOG</span></span>|<span data-ttu-id="cea53-322">1</span><span class="sxs-lookup"><span data-stu-id="cea53-322">1</span></span>|  
|<span data-ttu-id="cea53-323">Owner</span><span class="sxs-lookup"><span data-stu-id="cea53-323">Owner</span></span>|@Owner|<span data-ttu-id="cea53-324">CONSTRAINT_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cea53-324">CONSTRAINT_SCHEMA</span></span>|<span data-ttu-id="cea53-325">2</span><span class="sxs-lookup"><span data-stu-id="cea53-325">2</span></span>|  
|<span data-ttu-id="cea53-326">表</span><span class="sxs-lookup"><span data-stu-id="cea53-326">Table</span></span>|@Table|<span data-ttu-id="cea53-327">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-327">TABLE_NAME</span></span>|<span data-ttu-id="cea53-328">3</span><span class="sxs-lookup"><span data-stu-id="cea53-328">3</span></span>|  
|<span data-ttu-id="cea53-329">name</span><span class="sxs-lookup"><span data-stu-id="cea53-329">Name</span></span>|@Name|<span data-ttu-id="cea53-330">CONSTRAINT_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-330">CONSTRAINT_NAME</span></span>|<span data-ttu-id="cea53-331">4</span><span class="sxs-lookup"><span data-stu-id="cea53-331">4</span></span>|  
  
## <a name="sql-server-2008-schema-restrictions"></a><span data-ttu-id="cea53-332">SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="cea53-332">SQL Server 2008 Schema Restrictions</span></span>  
 <span data-ttu-id="cea53-333">下表列出了 SQL Server 2008 架构集合的限制。</span><span class="sxs-lookup"><span data-stu-id="cea53-333">The following tables list the restrictions for SQL Server 2008 schema collections.</span></span> <span data-ttu-id="cea53-334">这些限制从 .NET Framework 版本 3.5 SP1 和 SQL Server 2008 开始生效。</span><span class="sxs-lookup"><span data-stu-id="cea53-334">These restrictions are valid beginning with version 3.5 SP1 of the .NET Framework and SQL Server 2008.</span></span> <span data-ttu-id="cea53-335">.NET Framework 和 SQL Server 的早期版本不支持这些限制。</span><span class="sxs-lookup"><span data-stu-id="cea53-335">They are not supported in earlier versions of the .NET Framework and SQL Server.</span></span>  
  
### <a name="columnsetcolumns"></a><span data-ttu-id="cea53-336">ColumnSetColumns</span><span class="sxs-lookup"><span data-stu-id="cea53-336">ColumnSetColumns</span></span>  
  
|<span data-ttu-id="cea53-337">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-337">Restriction Name</span></span>|<span data-ttu-id="cea53-338">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-338">Parameter Name</span></span>|<span data-ttu-id="cea53-339">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-339">Restriction Default</span></span>|<span data-ttu-id="cea53-340">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-340">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-341">Catalog</span><span class="sxs-lookup"><span data-stu-id="cea53-341">Catalog</span></span>|@Catalog|<span data-ttu-id="cea53-342">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cea53-342">TABLE_CATALOG</span></span>|<span data-ttu-id="cea53-343">1</span><span class="sxs-lookup"><span data-stu-id="cea53-343">1</span></span>|  
|<span data-ttu-id="cea53-344">Owner</span><span class="sxs-lookup"><span data-stu-id="cea53-344">Owner</span></span>|@Owner|<span data-ttu-id="cea53-345">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cea53-345">TABLE_SCHEMA</span></span>|<span data-ttu-id="cea53-346">2</span><span class="sxs-lookup"><span data-stu-id="cea53-346">2</span></span>|  
|<span data-ttu-id="cea53-347">表</span><span class="sxs-lookup"><span data-stu-id="cea53-347">Table</span></span>|@Table|<span data-ttu-id="cea53-348">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-348">TABLE_NAME</span></span>|<span data-ttu-id="cea53-349">3</span><span class="sxs-lookup"><span data-stu-id="cea53-349">3</span></span>|  
  
### <a name="allcolumns"></a><span data-ttu-id="cea53-350">AllColumns</span><span class="sxs-lookup"><span data-stu-id="cea53-350">AllColumns</span></span>  
  
|<span data-ttu-id="cea53-351">限制名称</span><span class="sxs-lookup"><span data-stu-id="cea53-351">Restriction Name</span></span>|<span data-ttu-id="cea53-352">参数名称</span><span class="sxs-lookup"><span data-stu-id="cea53-352">Parameter Name</span></span>|<span data-ttu-id="cea53-353">限制默认值</span><span class="sxs-lookup"><span data-stu-id="cea53-353">Restriction Default</span></span>|<span data-ttu-id="cea53-354">限制数</span><span class="sxs-lookup"><span data-stu-id="cea53-354">Restriction Number</span></span>|  
|----------------------|--------------------|-------------------------|------------------------|  
|<span data-ttu-id="cea53-355">Catalog</span><span class="sxs-lookup"><span data-stu-id="cea53-355">Catalog</span></span>|@Catalog|<span data-ttu-id="cea53-356">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="cea53-356">TABLE_CATALOG</span></span>|<span data-ttu-id="cea53-357">1</span><span class="sxs-lookup"><span data-stu-id="cea53-357">1</span></span>|  
|<span data-ttu-id="cea53-358">Owner</span><span class="sxs-lookup"><span data-stu-id="cea53-358">Owner</span></span>|@Owner|<span data-ttu-id="cea53-359">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="cea53-359">TABLE_SCHEMA</span></span>|<span data-ttu-id="cea53-360">2</span><span class="sxs-lookup"><span data-stu-id="cea53-360">2</span></span>|  
|<span data-ttu-id="cea53-361">表</span><span class="sxs-lookup"><span data-stu-id="cea53-361">Table</span></span>|@Table|<span data-ttu-id="cea53-362">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-362">TABLE_NAME</span></span>|<span data-ttu-id="cea53-363">3</span><span class="sxs-lookup"><span data-stu-id="cea53-363">3</span></span>|  
|<span data-ttu-id="cea53-364">列</span><span class="sxs-lookup"><span data-stu-id="cea53-364">Column</span></span>|@Column|<span data-ttu-id="cea53-365">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="cea53-365">COLUMN_NAME</span></span>|<span data-ttu-id="cea53-366">4</span><span class="sxs-lookup"><span data-stu-id="cea53-366">4</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cea53-367">请参阅</span><span class="sxs-lookup"><span data-stu-id="cea53-367">See also</span></span>

- [<span data-ttu-id="cea53-368">ADO.NET 托管提供程序和数据集开发人员中心</span><span class="sxs-lookup"><span data-stu-id="cea53-368">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
