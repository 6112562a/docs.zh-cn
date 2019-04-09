---
title: 为类型化的数据集进行批注
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: d8a1a12a4d8ab5e6f4b0fe6ad6c2a3759aa65aa9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085124"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="646b6-102">为类型化的数据集进行批注</span><span class="sxs-lookup"><span data-stu-id="646b6-102">Annotating Typed DataSets</span></span>
<span data-ttu-id="646b6-103">批注使您能够在不修改基础架构的情况下修改类型化 <xref:System.Data.DataSet> 中元素的名称。</span><span class="sxs-lookup"><span data-stu-id="646b6-103">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="646b6-104">如果修改基础架构中的元素的名称会使类型化**数据集**要引用的对象执行不存在于数据源，并且会丢失对存在于数据源中的对象的引用。</span><span class="sxs-lookup"><span data-stu-id="646b6-104">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="646b6-105">使用批注，你可以自定义对象的名称类型化**数据集**随着更有意义的名称，使代码更易于阅读，类型化**数据集**客户端使用，同时保持更容易基础架构保持不变。</span><span class="sxs-lookup"><span data-stu-id="646b6-105">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="646b6-106">例如，以下架构元素的**客户**表的**Northwind**数据库将导致**DataRow**的对象名称**CustomersRow**和一个<xref:System.Data.DataRowCollection>名为**客户**。</span><span class="sxs-lookup"><span data-stu-id="646b6-106">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="646b6-107">一个**DataRowCollection**的名称**客户**客户端代码中有意义，但**DataRow**的名称**CustomersRow**会令人误解因为它是单个对象。</span><span class="sxs-lookup"><span data-stu-id="646b6-107">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="646b6-108">此外，共同方案中，将来引用对象而无需**行**标识符，而是会将只是称为**客户**对象。</span><span class="sxs-lookup"><span data-stu-id="646b6-108">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="646b6-109">解决方法是对架构进行批注并识别新名称**DataRow**并**DataRowCollection**对象。</span><span class="sxs-lookup"><span data-stu-id="646b6-109">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="646b6-110">下面是上一架构的批注版本。</span><span class="sxs-lookup"><span data-stu-id="646b6-110">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="646b6-111">指定**typedName**的值**客户**会导致**DataRow**对象的名称**客户**。</span><span class="sxs-lookup"><span data-stu-id="646b6-111">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="646b6-112">指定**typedPlural**的值**客户**保留**DataRowCollection**的名称**客户**。</span><span class="sxs-lookup"><span data-stu-id="646b6-112">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="646b6-113">下表显示可用的批注。</span><span class="sxs-lookup"><span data-stu-id="646b6-113">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="646b6-114">批注</span><span class="sxs-lookup"><span data-stu-id="646b6-114">Annotation</span></span>|<span data-ttu-id="646b6-115">描述</span><span class="sxs-lookup"><span data-stu-id="646b6-115">Description</span></span>|  
|----------------|-----------------|  
|**<span data-ttu-id="646b6-116">typedName</span><span class="sxs-lookup"><span data-stu-id="646b6-116">typedName</span></span>**|<span data-ttu-id="646b6-117">对象的名称。</span><span class="sxs-lookup"><span data-stu-id="646b6-117">Name of the object.</span></span>|  
|**<span data-ttu-id="646b6-118">typedPlural</span><span class="sxs-lookup"><span data-stu-id="646b6-118">typedPlural</span></span>**|<span data-ttu-id="646b6-119">对象集合的名称。</span><span class="sxs-lookup"><span data-stu-id="646b6-119">Name of a collection of objects.</span></span>|  
|**<span data-ttu-id="646b6-120">typedParent</span><span class="sxs-lookup"><span data-stu-id="646b6-120">typedParent</span></span>**|<span data-ttu-id="646b6-121">对象在父关系中被引用时的名称。</span><span class="sxs-lookup"><span data-stu-id="646b6-121">Name of the object when referred to in a parent relationship.</span></span>|  
|**<span data-ttu-id="646b6-122">typedChildren</span><span class="sxs-lookup"><span data-stu-id="646b6-122">typedChildren</span></span>**|<span data-ttu-id="646b6-123">用于从子关系中返回对象的方法的名称。</span><span class="sxs-lookup"><span data-stu-id="646b6-123">Name of the method to return objects from a child relationship.</span></span>|  
|**<span data-ttu-id="646b6-124">nullValue</span><span class="sxs-lookup"><span data-stu-id="646b6-124">nullValue</span></span>**|<span data-ttu-id="646b6-125">如果基础值为值**DBNull**。</span><span class="sxs-lookup"><span data-stu-id="646b6-125">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="646b6-126">请参阅下表中的**nullValue**批注。</span><span class="sxs-lookup"><span data-stu-id="646b6-126">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="646b6-127">默认值是 **_throw**。</span><span class="sxs-lookup"><span data-stu-id="646b6-127">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="646b6-128">下表显示了可以为指定的值**nullValue**批注。</span><span class="sxs-lookup"><span data-stu-id="646b6-128">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="646b6-129">nullValue 值</span><span class="sxs-lookup"><span data-stu-id="646b6-129">nullValue Value</span></span>|<span data-ttu-id="646b6-130">描述</span><span class="sxs-lookup"><span data-stu-id="646b6-130">Description</span></span>|  
|---------------------|-----------------|  
|*<span data-ttu-id="646b6-131">替换值</span><span class="sxs-lookup"><span data-stu-id="646b6-131">Replacement Value</span></span>*|<span data-ttu-id="646b6-132">指定要返回的值。</span><span class="sxs-lookup"><span data-stu-id="646b6-132">Specify a value to be returned.</span></span> <span data-ttu-id="646b6-133">所返回的值必须匹配该元素的类型。</span><span class="sxs-lookup"><span data-stu-id="646b6-133">The returned value must match the type of the element.</span></span> <span data-ttu-id="646b6-134">例如，使用 `nullValue="0"` 可为空整数字段返回 0。</span><span class="sxs-lookup"><span data-stu-id="646b6-134">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|**<span data-ttu-id="646b6-135">_throw</span><span class="sxs-lookup"><span data-stu-id="646b6-135">_throw</span></span>**|<span data-ttu-id="646b6-136">引发异常。</span><span class="sxs-lookup"><span data-stu-id="646b6-136">Throw an exception.</span></span> <span data-ttu-id="646b6-137">这是默认设置。</span><span class="sxs-lookup"><span data-stu-id="646b6-137">This is the default.</span></span>|  
|**<span data-ttu-id="646b6-138">_null</span><span class="sxs-lookup"><span data-stu-id="646b6-138">_null</span></span>**|<span data-ttu-id="646b6-139">如果遇到基元类型，则返回空引用或引发异常。</span><span class="sxs-lookup"><span data-stu-id="646b6-139">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|**<span data-ttu-id="646b6-140">_empty</span><span class="sxs-lookup"><span data-stu-id="646b6-140">_empty</span></span>**|<span data-ttu-id="646b6-141">对于字符串，返回**String.Empty**，否则返回从空构造函数创建的对象。</span><span class="sxs-lookup"><span data-stu-id="646b6-141">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="646b6-142">如果遇到基元类型，则引发异常。</span><span class="sxs-lookup"><span data-stu-id="646b6-142">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="646b6-143">下表显示了在类型化的对象的默认值**数据集**以及可用的批注。</span><span class="sxs-lookup"><span data-stu-id="646b6-143">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="646b6-144">对象/方法/事件</span><span class="sxs-lookup"><span data-stu-id="646b6-144">Object/Method/Event</span></span>|<span data-ttu-id="646b6-145">默认</span><span class="sxs-lookup"><span data-stu-id="646b6-145">Default</span></span>|<span data-ttu-id="646b6-146">批注</span><span class="sxs-lookup"><span data-stu-id="646b6-146">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|**<span data-ttu-id="646b6-147">DataTable</span><span class="sxs-lookup"><span data-stu-id="646b6-147">DataTable</span></span>**|<span data-ttu-id="646b6-148">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="646b6-148">TableNameDataTable</span></span>|<span data-ttu-id="646b6-149">typedPlural</span><span class="sxs-lookup"><span data-stu-id="646b6-149">typedPlural</span></span>|  
|<span data-ttu-id="646b6-150">**DataTable**方法</span><span class="sxs-lookup"><span data-stu-id="646b6-150">**DataTable** Methods</span></span>|<span data-ttu-id="646b6-151">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="646b6-151">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="646b6-152">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="646b6-152">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="646b6-153">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="646b6-153">DeleteTableNameRow</span></span>|<span data-ttu-id="646b6-154">typedName</span><span class="sxs-lookup"><span data-stu-id="646b6-154">typedName</span></span>|  
|**<span data-ttu-id="646b6-155">DataRowCollection</span><span class="sxs-lookup"><span data-stu-id="646b6-155">DataRowCollection</span></span>**|<span data-ttu-id="646b6-156">TableName</span><span class="sxs-lookup"><span data-stu-id="646b6-156">TableName</span></span>|<span data-ttu-id="646b6-157">typedPlural</span><span class="sxs-lookup"><span data-stu-id="646b6-157">typedPlural</span></span>|  
|**<span data-ttu-id="646b6-158">DataRow</span><span class="sxs-lookup"><span data-stu-id="646b6-158">DataRow</span></span>**|<span data-ttu-id="646b6-159">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="646b6-159">TableNameRow</span></span>|<span data-ttu-id="646b6-160">typedName</span><span class="sxs-lookup"><span data-stu-id="646b6-160">typedName</span></span>|  
|**<span data-ttu-id="646b6-161">DataColumn</span><span class="sxs-lookup"><span data-stu-id="646b6-161">DataColumn</span></span>**|<span data-ttu-id="646b6-162">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="646b6-162">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="646b6-163">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="646b6-163">DataRow.ColumnName</span></span>|<span data-ttu-id="646b6-164">typedName</span><span class="sxs-lookup"><span data-stu-id="646b6-164">typedName</span></span>|  
|**<span data-ttu-id="646b6-165">属性</span><span class="sxs-lookup"><span data-stu-id="646b6-165">Property</span></span>**|<span data-ttu-id="646b6-166">PropertyName</span><span class="sxs-lookup"><span data-stu-id="646b6-166">PropertyName</span></span>|<span data-ttu-id="646b6-167">typedName</span><span class="sxs-lookup"><span data-stu-id="646b6-167">typedName</span></span>|  
|<span data-ttu-id="646b6-168">**子**访问器</span><span class="sxs-lookup"><span data-stu-id="646b6-168">**Child** Accessor</span></span>|<span data-ttu-id="646b6-169">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="646b6-169">GetChildTableNameRows</span></span>|<span data-ttu-id="646b6-170">typedChildren</span><span class="sxs-lookup"><span data-stu-id="646b6-170">typedChildren</span></span>|  
|<span data-ttu-id="646b6-171">**父**访问器</span><span class="sxs-lookup"><span data-stu-id="646b6-171">**Parent** Accessor</span></span>|<span data-ttu-id="646b6-172">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="646b6-172">TableNameRow</span></span>|<span data-ttu-id="646b6-173">typedParent</span><span class="sxs-lookup"><span data-stu-id="646b6-173">typedParent</span></span>|  
|<span data-ttu-id="646b6-174">**数据集**事件</span><span class="sxs-lookup"><span data-stu-id="646b6-174">**DataSet** Events</span></span>|<span data-ttu-id="646b6-175">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="646b6-175">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="646b6-176">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="646b6-176">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="646b6-177">typedName</span><span class="sxs-lookup"><span data-stu-id="646b6-177">typedName</span></span>|  
  
 <span data-ttu-id="646b6-178">若要使用类型化**数据集**批注，您必须包括以下**xmlns** XML 架构定义语言 (XSD) 架构中的引用。</span><span class="sxs-lookup"><span data-stu-id="646b6-178">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="646b6-179">若要从数据库表创建 xsd，请参阅<xref:System.Data.DataSet.WriteXmlSchema%2A>或[使用 Visual Studio 中的数据集](/visualstudio/data-tools/dataset-tools-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="646b6-179">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="646b6-180">下面是示例带批注的架构公开**客户**表的**Northwind**具有与关系数据库**订单**包含的表。</span><span class="sxs-lookup"><span data-stu-id="646b6-180">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"   
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""   
      xmlns:xs="http://www.w3.org/2001/XMLSchema"   
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"   
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"   
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="646b6-181">下面的代码示例使用强类型化**数据集**从示例架构创建。</span><span class="sxs-lookup"><span data-stu-id="646b6-181">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="646b6-182">它使用一个<xref:System.Data.SqlClient.SqlDataAdapter>来填充**客户**表，另一个<xref:System.Data.SqlClient.SqlDataAdapter>填充**订单**表。</span><span class="sxs-lookup"><span data-stu-id="646b6-182">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="646b6-183">强类型化**数据集**定义**Datarelation**。</span><span class="sxs-lookup"><span data-stu-id="646b6-183">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",   
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new   
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =   
    customers.Customers.NewCustomer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="646b6-184">请参阅</span><span class="sxs-lookup"><span data-stu-id="646b6-184">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="646b6-185">类型化数据集</span><span class="sxs-lookup"><span data-stu-id="646b6-185">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [<span data-ttu-id="646b6-186">数据集、数据表和数据视图</span><span class="sxs-lookup"><span data-stu-id="646b6-186">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="646b6-187">ADO.NET 托管提供程序和 DataSet 开发人员中心</span><span class="sxs-lookup"><span data-stu-id="646b6-187">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
