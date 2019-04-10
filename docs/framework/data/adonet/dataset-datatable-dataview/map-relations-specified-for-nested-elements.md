---
title: 映射为嵌套元素指定的关系
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: 9772f077991c758be65bbb44b9474f1ad341371f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203140"
---
# <a name="map-relations-specified-for-nested-elements"></a><span data-ttu-id="967b0-102">映射为嵌套元素指定的关系</span><span class="sxs-lookup"><span data-stu-id="967b0-102">Map Relations Specified for Nested Elements</span></span>
<span data-ttu-id="967b0-103">架构可以包含**msdata: relationship**批注来显式指定架构中任意两个元素之间的映射。</span><span class="sxs-lookup"><span data-stu-id="967b0-103">A schema can include an **msdata:Relationship** annotation to explicitly specify the mapping between any two elements in the schema.</span></span> <span data-ttu-id="967b0-104">中指定的两个元素**msdata: relationship**可以嵌套在架构中，但不是一定要。</span><span class="sxs-lookup"><span data-stu-id="967b0-104">The two elements specified in **msdata:Relationship** can be nested in the schema, but do not have to be.</span></span> <span data-ttu-id="967b0-105">映射进程使用**msdata: relationship**架构以生成两个列之间主键/外的键关系中。</span><span class="sxs-lookup"><span data-stu-id="967b0-105">The mapping process uses **msdata:Relationship** in the schema to generate the primary key/foreign key relationship between the two columns.</span></span>  
  
 <span data-ttu-id="967b0-106">下面的示例显示在其中一个 XML 架构**OrderDetail**元素是子元素的**顺序**。</span><span class="sxs-lookup"><span data-stu-id="967b0-106">The following example shows an XML Schema in which the **OrderDetail** element is a child element of **Order**.</span></span> <span data-ttu-id="967b0-107">**Msdata: relationship**标识此父-子关系，并指定**OrderNumber**生成的列**顺序**与相关表**OrderNo**生成的列**OrderDetail**表。</span><span class="sxs-lookup"><span data-stu-id="967b0-107">The **msdata:Relationship** identifies this parent-child relationship and specifies that the **OrderNumber** column of the resulting **Order** table is related to the **OrderNo** column of the resulting **OrderDetail** table.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
 <xs:complexType>  
  <xs:choice maxOccurs="unbounded">  
   <xs:element name="Order">  
    <xs:complexType>  
     <xs:sequence>  
       <xs:element name="OrderNumber" type="xs:string" />  
       <xs:element name="EmpNumber" type="xs:string" />  
       <xs:element name="OrderDetail">  
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"   
                                msdata:parent="Order"   
                                msdata:child="OrderDetail"   
                                msdata:parentkey="OrderNumber"   
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
          <xs:complexType>  
            <xs:sequence>  
             <xs:element name="OrderNo" type="xs:string" />  
             <xs:element name="ItemNo" type="xs:string" />  
            </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:sequence>  
    </xs:complexType>  
   </xs:element>  
  </xs:choice>  
 </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="967b0-108">XML 架构映射过程在 <xref:System.Data.DataSet> 中创建以下内容：</span><span class="sxs-lookup"><span data-stu-id="967b0-108">The XML Schema mapping process creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="967b0-109">**顺序**和一个**OrderDetail**表。</span><span class="sxs-lookup"><span data-stu-id="967b0-109">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
-   <span data-ttu-id="967b0-110">之间的关系**顺序**并**OrderDetail**表。</span><span class="sxs-lookup"><span data-stu-id="967b0-110">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="967b0-111">**嵌套**为此关系的属性设置为**True**因为**顺序**并**OrderDetail**元素都嵌套在架构.</span><span class="sxs-lookup"><span data-stu-id="967b0-111">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 <span data-ttu-id="967b0-112">映射过程不创建任何约束。</span><span class="sxs-lookup"><span data-stu-id="967b0-112">The mapping process does not create any constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="967b0-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="967b0-113">See also</span></span>

- [<span data-ttu-id="967b0-114">从 XML 架构生成数据集关系 (XSD)</span><span class="sxs-lookup"><span data-stu-id="967b0-114">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="967b0-115">将关键 XML 架构 (XSD) 约束映射到数据集约束</span><span class="sxs-lookup"><span data-stu-id="967b0-115">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="967b0-116">ADO.NET 托管提供程序和 DataSet 开发人员中心</span><span class="sxs-lookup"><span data-stu-id="967b0-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
