---
title: DataAdapter 数据表和 DataColumn 映射
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 54af7c2f449f8eb289841fb3eca357c6916404aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032690"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="cff26-102">DataAdapter 数据表和 DataColumn 映射</span><span class="sxs-lookup"><span data-stu-id="cff26-102">DataAdapter DataTable and DataColumn Mappings</span></span>
<span data-ttu-id="cff26-103">一个**DataAdapter**包含零个或多集合<xref:System.Data.Common.DataTableMapping>中的对象及其**TableMappings**属性。</span><span class="sxs-lookup"><span data-stu-id="cff26-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="cff26-104">一个**DataTableMapping**提供了从对数据源，查询返回的数据之间的主映射和<xref:System.Data.DataTable>。</span><span class="sxs-lookup"><span data-stu-id="cff26-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="cff26-105">**DataTableMapping**可以将名称传递来代替**DataTable**到名称**填充**方法**DataAdapter**。</span><span class="sxs-lookup"><span data-stu-id="cff26-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="cff26-106">下面的示例创建**DataTableMapping**名为**AuthorsMapping**有关**作者**表。</span><span class="sxs-lookup"><span data-stu-id="cff26-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="cff26-107">一个**DataTableMapping**使您能够使用中的列名**DataTable**从数据库中的不同。</span><span class="sxs-lookup"><span data-stu-id="cff26-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="cff26-108">**DataAdapter**使用此映射来更新表时的列匹配。</span><span class="sxs-lookup"><span data-stu-id="cff26-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="cff26-109">如果未指定**TableName**或**DataTableMapping**时调用的名称**填充**或者**更新**方法**DataAdapter**，则**DataAdapter**寻找**DataTableMapping**名为"Table"。</span><span class="sxs-lookup"><span data-stu-id="cff26-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="cff26-110">如果该**DataTableMapping**不存在**TableName**的**DataTable**为"Table"。</span><span class="sxs-lookup"><span data-stu-id="cff26-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="cff26-111">可以指定默认值**DataTableMapping**通过创建**DataTableMapping** "Table"的名称。</span><span class="sxs-lookup"><span data-stu-id="cff26-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="cff26-112">下面的代码示例将创建**DataTableMapping** (从<xref:System.Data.Common>命名空间)，并使其指定的默认映射**DataAdapter**通过其命名为"Table"。</span><span class="sxs-lookup"><span data-stu-id="cff26-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="cff26-113">该示例然后将映射从查询结果中的第一个表的列 (**客户**表的**Northwind**数据库) 到一组更为用户友好名称中**Northwind 客户**表中<xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="cff26-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="cff26-114">对于未映射的列，将使用数据源中的列名称。</span><span class="sxs-lookup"><span data-stu-id="cff26-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =   
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 <span data-ttu-id="cff26-115">在更高级的情况下，你可能决定想相同**DataAdapter**以支持不同的映射不同的表加载。</span><span class="sxs-lookup"><span data-stu-id="cff26-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="cff26-116">若要执行此操作，只需添加附加**DataTableMapping**对象。</span><span class="sxs-lookup"><span data-stu-id="cff26-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="cff26-117">当**填充**方法传递的一个实例**数据集**和一个**DataTableMapping**名称，如果具有该名称的映射存在，则为; 否则为**DataTable**这使用名称。</span><span class="sxs-lookup"><span data-stu-id="cff26-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="cff26-118">以下示例创建两个**DataTableMapping**一个名为**客户**和一个**DataTable**的名称**BizTalkSchema**。</span><span class="sxs-lookup"><span data-stu-id="cff26-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="cff26-119">该示例然后将映射到 SELECT 语句返回的行**BizTalkSchema** **DataTable**。</span><span class="sxs-lookup"><span data-stu-id="cff26-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =   
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
>  <span data-ttu-id="cff26-120">如果没有为列映射提供源列名称或者没有为表映射提供源表名称，则将自动生成默认名称。</span><span class="sxs-lookup"><span data-stu-id="cff26-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="cff26-121">如果为列映射提供没有源列，则列映射提供递增的默认名称的**SourceColumn** *N*开头**SourceColumn1**。</span><span class="sxs-lookup"><span data-stu-id="cff26-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="cff26-122">如果为表映射提供没有源表名称，则表映射提供递增的默认名称的**SourceTable** *N*，从开始**SourceTable1**。</span><span class="sxs-lookup"><span data-stu-id="cff26-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cff26-123">我们建议你避免的命名约定**SourceColumn** *N*为列映射，或**SourceTable** *N*表映射，因为所提供的名称可能与中现有默认列映射名称冲突**ColumnMappingCollection**或表中的映射名称**DataTableMappingCollection**.</span><span class="sxs-lookup"><span data-stu-id="cff26-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="cff26-124">如果提供的名称已经存在，将引发异常。</span><span class="sxs-lookup"><span data-stu-id="cff26-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="cff26-125">处理多个结果集</span><span class="sxs-lookup"><span data-stu-id="cff26-125">Handling Multiple Result Sets</span></span>  
 <span data-ttu-id="cff26-126">如果你**SelectCommand**返回多个表**填充**自动生成具有递增的值中的表的表名称**数据集**，从开始在窗体上指定表名和继续**TableName** *N*，从开始**TableName1**。</span><span class="sxs-lookup"><span data-stu-id="cff26-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="cff26-127">可以使用表映射自动生成的表名称映射到要为表中指定的名称**数据集**。</span><span class="sxs-lookup"><span data-stu-id="cff26-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="cff26-128">例如，对于**SelectCommand** ，它返回两个表**客户**并**订单**，发出以下调用到**填充**。</span><span class="sxs-lookup"><span data-stu-id="cff26-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 <span data-ttu-id="cff26-129">在中创建两个表**数据集**:**客户**并**Customers1**。</span><span class="sxs-lookup"><span data-stu-id="cff26-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="cff26-130">可以使用表映射以确保第二个表名为**订单**而不是**Customers1**。</span><span class="sxs-lookup"><span data-stu-id="cff26-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="cff26-131">若要执行此操作，将映射的源表**Customers1**到**数据集**表**订单**，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="cff26-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a><span data-ttu-id="cff26-132">请参阅</span><span class="sxs-lookup"><span data-stu-id="cff26-132">See also</span></span>

- [<span data-ttu-id="cff26-133">DataAdapters 和 DataReaders</span><span class="sxs-lookup"><span data-stu-id="cff26-133">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="cff26-134">在 ADO.NET 中检索和修改数据</span><span class="sxs-lookup"><span data-stu-id="cff26-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [<span data-ttu-id="cff26-135">ADO.NET 托管提供程序和数据集开发人员中心</span><span class="sxs-lookup"><span data-stu-id="cff26-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
