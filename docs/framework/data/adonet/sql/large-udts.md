---
title: 大型 UDT
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 420ae24e-762b-4e09-b4c3-2112c470ee49
ms.openlocfilehash: 015ce896e49b3a6a932c36db867271b4ac4c64c8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303474"
---
# <a name="large-udts"></a><span data-ttu-id="b32c2-102">大型 UDT</span><span class="sxs-lookup"><span data-stu-id="b32c2-102">Large UDTs</span></span>
<span data-ttu-id="b32c2-103">通过用户定义类型 (UDT)，开发人员可通过在 SQL Server 数据库中存储公共语言运行时 (CLR) 对象来扩展服务器的标量类型系统。</span><span class="sxs-lookup"><span data-stu-id="b32c2-103">User-defined types (UDTs) allow a developer to extend the server's scalar type system by storing common language runtime (CLR) objects in a SQL Server database.</span></span> <span data-ttu-id="b32c2-104">UDT 可以包含多个元素并可具有多种行为，与传统别名数据类型不同，它们由单一 SQL Server 系统数据类型组成。</span><span class="sxs-lookup"><span data-stu-id="b32c2-104">UDTs can contain multiple elements and can have behaviors, unlike the traditional alias data types, which consist of a single SQL Server system data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b32c2-105">必须安装 .NET Framework 3.5 SP1（或更高版本）才能利用针对大型 UDT 增强的 SqlClient 支持。</span><span class="sxs-lookup"><span data-stu-id="b32c2-105">You must install the .NET Framework 3.5 SP1 (or later) to take advantage of the enhanced SqlClient support for large UDTs.</span></span>  
  
 <span data-ttu-id="b32c2-106">以前，UDT 的最大大小限制为 8KB。</span><span class="sxs-lookup"><span data-stu-id="b32c2-106">Previously, UDTs were restricted to a maximum size of 8 kilobytes.</span></span> <span data-ttu-id="b32c2-107">在 SQL Server 2008 中，对于具有 <xref:Microsoft.SqlServer.Server.Format.UserDefined> 格式的 UDT，此限制已被取消。</span><span class="sxs-lookup"><span data-stu-id="b32c2-107">In SQL Server 2008, this restriction has been removed for UDTs that have a format of <xref:Microsoft.SqlServer.Server.Format.UserDefined>.</span></span>  
  
 <span data-ttu-id="b32c2-108">有关用户定义类型的完整文档，请参见与您所使用的 SQL Server 版本对应的 SQL Server 联机丛书。</span><span class="sxs-lookup"><span data-stu-id="b32c2-108">For the complete documentation for user-defined types, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 **<span data-ttu-id="b32c2-109">SQL Server 联机丛书</span><span class="sxs-lookup"><span data-stu-id="b32c2-109">SQL Server Books Online</span></span>**  
  
1. [<span data-ttu-id="b32c2-110">CLR 用户定义的类型</span><span class="sxs-lookup"><span data-stu-id="b32c2-110">CLR User-Defined Types</span></span>](https://go.microsoft.com/fwlink/?LinkId=98366)  
  
## <a name="retrieving-udt-schemas-using-getschema"></a><span data-ttu-id="b32c2-111">使用 GetSchema 检索 UDT 架构</span><span class="sxs-lookup"><span data-stu-id="b32c2-111">Retrieving UDT Schemas Using GetSchema</span></span>  
 <span data-ttu-id="b32c2-112"><xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> 的 <xref:System.Data.SqlClient.SqlConnection> 方法可返回 <xref:System.Data.DataTable> 中的数据库架构信息。</span><span class="sxs-lookup"><span data-stu-id="b32c2-112">The <xref:System.Data.SqlClient.SqlConnection.GetSchema%2A> method of <xref:System.Data.SqlClient.SqlConnection> returns database schema information in a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="b32c2-113">有关详细信息，请参阅[SQL Server 架构集合](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md)。</span><span class="sxs-lookup"><span data-stu-id="b32c2-113">For more information, see [SQL Server Schema Collections](../../../../../docs/framework/data/adonet/sql-server-schema-collections.md).</span></span>  
  
### <a name="getschematable-column-values-for-udts"></a><span data-ttu-id="b32c2-114">UDT 的 GetSchemaTable 列值</span><span class="sxs-lookup"><span data-stu-id="b32c2-114">GetSchemaTable Column Values for UDTs</span></span>  
 <span data-ttu-id="b32c2-115"><xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> 的 <xref:System.Data.SqlClient.SqlDataReader> 方法可返回描述列元数据的 <xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="b32c2-115">The <xref:System.Data.SqlClient.SqlDataReader.GetSchemaTable%2A> method of a <xref:System.Data.SqlClient.SqlDataReader> returns a <xref:System.Data.DataTable> that describes column metadata.</span></span> <span data-ttu-id="b32c2-116">下表介绍了 SQL Server 2005 与 SQL Server 2008 中大型 UDT 的列元数据的差异。</span><span class="sxs-lookup"><span data-stu-id="b32c2-116">The following table describes the differences in the column metadata for large UDTs between SQL Server 2005 and SQL Server 2008.</span></span>  
  
|<span data-ttu-id="b32c2-117">SqlDataReader 列</span><span class="sxs-lookup"><span data-stu-id="b32c2-117">SqlDataReader column</span></span>|<span data-ttu-id="b32c2-118">SQL Server 2005</span><span class="sxs-lookup"><span data-stu-id="b32c2-118">SQL Server 2005</span></span>|<span data-ttu-id="b32c2-119">SQL Server 2008 及更高版本</span><span class="sxs-lookup"><span data-stu-id="b32c2-119">SQL Server 2008 and later</span></span>|  
|--------------------------|---------------------|-------------------------------|  
|`ColumnSize`|<span data-ttu-id="b32c2-120">不定</span><span class="sxs-lookup"><span data-stu-id="b32c2-120">Varies</span></span>|<span data-ttu-id="b32c2-121">不定</span><span class="sxs-lookup"><span data-stu-id="b32c2-121">Varies</span></span>|  
|`NumericPrecision`|<span data-ttu-id="b32c2-122">255</span><span class="sxs-lookup"><span data-stu-id="b32c2-122">255</span></span>|<span data-ttu-id="b32c2-123">255</span><span class="sxs-lookup"><span data-stu-id="b32c2-123">255</span></span>|  
|`NumericScale`|<span data-ttu-id="b32c2-124">255</span><span class="sxs-lookup"><span data-stu-id="b32c2-124">255</span></span>|<span data-ttu-id="b32c2-125">255</span><span class="sxs-lookup"><span data-stu-id="b32c2-125">255</span></span>|  
|`DataType`|`Byte[]`|<span data-ttu-id="b32c2-126">UDT 实例</span><span class="sxs-lookup"><span data-stu-id="b32c2-126">UDT instance</span></span>|  
|`ProviderSpecificDataType`|`SqlTypes.SqlBinary`|<span data-ttu-id="b32c2-127">UDT 实例</span><span class="sxs-lookup"><span data-stu-id="b32c2-127">UDT instance</span></span>|  
|`ProviderType`|<span data-ttu-id="b32c2-128">21 (`SqlDbType.VarBinary`)</span><span class="sxs-lookup"><span data-stu-id="b32c2-128">21 (`SqlDbType.VarBinary`)</span></span>|<span data-ttu-id="b32c2-129">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="b32c2-129">29 (`SqlDbType.Udt`)</span></span>|  
|`NonVersionedProviderType`|<span data-ttu-id="b32c2-130">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="b32c2-130">29 (`SqlDbType.Udt`)</span></span>|<span data-ttu-id="b32c2-131">29 (`SqlDbType.Udt`)</span><span class="sxs-lookup"><span data-stu-id="b32c2-131">29 (`SqlDbType.Udt`)</span></span>|  
|`DataTypeName`|`SqlDbType.VarBinary`|<span data-ttu-id="b32c2-132">由三部分名称指定为*Database.SchemaName.TypeName*。</span><span class="sxs-lookup"><span data-stu-id="b32c2-132">The three part name specified as *Database.SchemaName.TypeName*.</span></span>|  
|`IsLong`|<span data-ttu-id="b32c2-133">不定</span><span class="sxs-lookup"><span data-stu-id="b32c2-133">Varies</span></span>|<span data-ttu-id="b32c2-134">不定</span><span class="sxs-lookup"><span data-stu-id="b32c2-134">Varies</span></span>|  
  
## <a name="sqldatareader-considerations"></a><span data-ttu-id="b32c2-135">SqlDataReader 注意事项</span><span class="sxs-lookup"><span data-stu-id="b32c2-135">SqlDataReader Considerations</span></span>  
 <span data-ttu-id="b32c2-136">从 SQL Server 2008 开始，<xref:System.Data.SqlClient.SqlDataReader> 已得到扩展，可支持检索大型 UDT 值。</span><span class="sxs-lookup"><span data-stu-id="b32c2-136">The <xref:System.Data.SqlClient.SqlDataReader> has been extended beginning in SQL Server 2008 to support retrieving large UDT values.</span></span> <span data-ttu-id="b32c2-137"><xref:System.Data.SqlClient.SqlDataReader> 处理大型 UDT 值的方式取决于您所使用的 SQL Server 版本以及连接字符串中指定的 `Type System Version`。</span><span class="sxs-lookup"><span data-stu-id="b32c2-137">How large UDT values are processed by a <xref:System.Data.SqlClient.SqlDataReader> depends on the version of SQL Server you are using, as well as on the `Type System Version` specified in the connection string.</span></span> <span data-ttu-id="b32c2-138">有关详细信息，请参阅 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。</span><span class="sxs-lookup"><span data-stu-id="b32c2-138">For more information, see <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="b32c2-139">当 <xref:System.Data.SqlClient.SqlDataReader> 设置为 SQL Server 2005 时，<xref:System.Data.SqlTypes.SqlBinary> 的以下方法将返回 `Type System Version` 而不是 UDT：</span><span class="sxs-lookup"><span data-stu-id="b32c2-139">The following methods of <xref:System.Data.SqlClient.SqlDataReader> will return a <xref:System.Data.SqlTypes.SqlBinary> instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificFieldType%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetProviderSpecificValues%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetSqlValues%2A>  
  
 <span data-ttu-id="b32c2-140">当 `Byte[]` 设置为 SQL Server 2005 时，以下方法将返回 `Type System Version` 的数组而不是 UDT：</span><span class="sxs-lookup"><span data-stu-id="b32c2-140">The following methods will return an array of `Byte[]` instead of a UDT when the `Type System Version` is set to SQL Server 2005:</span></span>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValue%2A>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.GetValues%2A>  
  
 <span data-ttu-id="b32c2-141">请注意，不会对 ADO.NET 的当前版本进行任何转换。</span><span class="sxs-lookup"><span data-stu-id="b32c2-141">Note that no conversions are made for the current version of ADO.NET.</span></span>  
  
## <a name="specifying-sqlparameters"></a><span data-ttu-id="b32c2-142">指定 SqlParameters</span><span class="sxs-lookup"><span data-stu-id="b32c2-142">Specifying SqlParameters</span></span>  
 <span data-ttu-id="b32c2-143">下面的 <xref:System.Data.SqlClient.SqlParameter> 属性已得到扩展，可以使用大型 UDT。</span><span class="sxs-lookup"><span data-stu-id="b32c2-143">The following <xref:System.Data.SqlClient.SqlParameter> properties have been extended to work with large UDTs.</span></span>  
  
|<span data-ttu-id="b32c2-144">SqlParameter 属性</span><span class="sxs-lookup"><span data-stu-id="b32c2-144">SqlParameter Property</span></span>|<span data-ttu-id="b32c2-145">描述</span><span class="sxs-lookup"><span data-stu-id="b32c2-145">Description</span></span>|  
|---------------------------|-----------------|  
|<xref:System.Data.SqlClient.SqlParameter.Value%2A>|<span data-ttu-id="b32c2-146">获取或设置表示参数值的对象。</span><span class="sxs-lookup"><span data-stu-id="b32c2-146">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="b32c2-147">默认值为 null。</span><span class="sxs-lookup"><span data-stu-id="b32c2-147">The default is null.</span></span> <span data-ttu-id="b32c2-148">此属性可以是 `SqlBinary`、`Byte[]` 或一个托管对象。</span><span class="sxs-lookup"><span data-stu-id="b32c2-148">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.SqlValue%2A>|<span data-ttu-id="b32c2-149">获取或设置表示参数值的对象。</span><span class="sxs-lookup"><span data-stu-id="b32c2-149">Gets or sets an object that represents the value of the parameter.</span></span> <span data-ttu-id="b32c2-150">默认值为 null。</span><span class="sxs-lookup"><span data-stu-id="b32c2-150">The default is null.</span></span> <span data-ttu-id="b32c2-151">此属性可以是 `SqlBinary`、`Byte[]` 或一个托管对象。</span><span class="sxs-lookup"><span data-stu-id="b32c2-151">The property can be `SqlBinary`, `Byte[]`, or a managed object.</span></span>|  
|<xref:System.Data.SqlClient.SqlParameter.Size%2A>|<span data-ttu-id="b32c2-152">获取或设置要解析的参数值的大小。</span><span class="sxs-lookup"><span data-stu-id="b32c2-152">Gets or sets the size of the parameter value to resolve.</span></span> <span data-ttu-id="b32c2-153">默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="b32c2-153">The default value is 0.</span></span> <span data-ttu-id="b32c2-154">此属性可以是表示参数值大小的一个整数。</span><span class="sxs-lookup"><span data-stu-id="b32c2-154">The property can be an integer that represents the size of the parameter value.</span></span> <span data-ttu-id="b32c2-155">对于大型 UDT，此属性可以是 UDT 的实际大小，也可以是 -1 以表示未知大小。</span><span class="sxs-lookup"><span data-stu-id="b32c2-155">For large UDTs, it can be the actual size of the UDT, or -1 for unknown.</span></span>|  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="b32c2-156">检索数据示例</span><span class="sxs-lookup"><span data-stu-id="b32c2-156">Retrieving Data Example</span></span>  
 <span data-ttu-id="b32c2-157">下面的代码段演示如何检索大型 UDT 数据。</span><span class="sxs-lookup"><span data-stu-id="b32c2-157">The following code fragment demonstrates how to retrieve large UDT data.</span></span> <span data-ttu-id="b32c2-158">`connectionString` 变量假定已与 SQL Server 数据库建立有效的连接，`commandString` 变量假定存在首先列出主键列的有效 SELECT 语句。</span><span class="sxs-lookup"><span data-stu-id="b32c2-158">The `connectionString` variable assumes a valid connection to a SQL Server database and the `commandString` variable assumes a valid SELECT statement with the primary key column listed first.</span></span>  
  
```csharp  
using (SqlConnection connection = new SqlConnection(   
    connectionString, commandString))  
{  
  connection.Open();  
  SqlCommand command = new SqlCommand(commandString);  
  SqlDataReader reader = command.ExecuteReader();  
  while (reader.Read())  
  {  
    // Retrieve the value of the Primary Key column.  
    int id = reader.GetInt32(0);  
  
    // Retrieve the value of the UDT.  
    LargeUDT udt = (LargeUDT)reader[1];  
  
    // You can also use GetSqlValue and GetValue.  
    // LargeUDT udt = (LargeUDT)reader.GetSqlValue(1);  
    // LargeUDT udt = (LargeUDT)reader.GetValue(1);  
  
    Console.WriteLine(  
     "ID={0} LargeUDT={1}", id, udt);  
  }  
reader.close  
}  
```  
  
```vb  
Using connection As New SqlConnection( _  
    connectionString, commandString)  
    connection.Open()  
    Dim command As New SqlCommand(commandString, connection)  
    Dim reader As SqlDataReader  
    reader = command.ExecuteReader  
  
    While reader.Read()  
      ' Retrieve the value of the Primary Key column.  
      Dim id As Int32 = reader.GetInt32(0)  
  
      ' Retrieve the value of the UDT.  
      Dim udt As LargeUDT = CType(reader(1), LargeUDT)  
  
     ' You can also use GetSqlValue and GetValue.  
     ' Dim udt As LargeUDT = CType(reader.GetSqlValue(1), LargeUDT)  
     ' Dim udt As LargeUDT = CType(reader.GetValue(1), LargeUDT)  
  
      ' Print values.  
      Console.WriteLine("ID={0} LargeUDT={1}", id, udt)  
    End While  
    reader.Close()  
End Using  
```  
  
## <a name="see-also"></a><span data-ttu-id="b32c2-159">请参阅</span><span class="sxs-lookup"><span data-stu-id="b32c2-159">See also</span></span>

- [<span data-ttu-id="b32c2-160">配置参数和参数数据类型</span><span class="sxs-lookup"><span data-stu-id="b32c2-160">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="b32c2-161">检索数据库架构信息</span><span class="sxs-lookup"><span data-stu-id="b32c2-161">Retrieving Database Schema Information</span></span>](../../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [<span data-ttu-id="b32c2-162">SQL Server 数据类型映射</span><span class="sxs-lookup"><span data-stu-id="b32c2-162">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)
- [<span data-ttu-id="b32c2-163">SQL Server 二进制和大值数据</span><span class="sxs-lookup"><span data-stu-id="b32c2-163">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="b32c2-164">ADO.NET 托管提供程序和 DataSet 开发人员中心</span><span class="sxs-lookup"><span data-stu-id="b32c2-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
