---
title: 如何：控制投影的类型 (C#)
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 4aea9fd07ff2a128da9be0a17e5f70a25c9f3853
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146558"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="53722-102">如何：控制投影的类型 (C#)</span><span class="sxs-lookup"><span data-stu-id="53722-102">How to: Control the Type of a Projection (C#)</span></span>
<span data-ttu-id="53722-103">投影是一个过程，这一过程包括：获取一组数据，筛选这些数据，更改数据形状，甚至更改数据的类型。</span><span class="sxs-lookup"><span data-stu-id="53722-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="53722-104">大多数查询表达式都可执行投影。</span><span class="sxs-lookup"><span data-stu-id="53722-104">Most query expressions perform projections.</span></span> <span data-ttu-id="53722-105">本节中介绍的大多数查询表达式的计算结果都是 <xref:System.Collections.Generic.IEnumerable%601> 的 <xref:System.Xml.Linq.XElement>，不过，可以控制投影的类型从而创建其他类型的集合。</span><span class="sxs-lookup"><span data-stu-id="53722-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="53722-106">本主题演示如何执行此操作。</span><span class="sxs-lookup"><span data-stu-id="53722-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53722-107">示例</span><span class="sxs-lookup"><span data-stu-id="53722-107">Example</span></span>  
 <span data-ttu-id="53722-108">下面的示例定义一个新类型 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="53722-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="53722-109">然后，查询表达式在 `Customer` 子句中实例化新的 `Select` 对象。</span><span class="sxs-lookup"><span data-stu-id="53722-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="53722-110">这样，查询表达式的类型就是 <xref:System.Collections.Generic.IEnumerable%601> 的 `Customer`。</span><span class="sxs-lookup"><span data-stu-id="53722-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="53722-111">本示例使用下面的 XML 文档：[示例 XML 文件：客户和订单 (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md)。</span><span class="sxs-lookup"><span data-stu-id="53722-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
public class Customer  
{  
    private string customerID;  
    public string CustomerID{ get{return customerID;} set{customerID = value;}}  
  
    private string companyName;  
    public string CompanyName{ get{return companyName;} set{companyName = value;}}  
  
    private string contactName;  
    public string ContactName { get{return contactName;} set{contactName = value;}}  
  
    public Customer(string customerID, string companyName, string contactName)  
    {  
        CustomerID = customerID;  
        CompanyName = companyName;  
        ContactName = contactName;  
    }  
  
    public override string ToString()  
    {  
        return $"{this.customerID}:{this.companyName}:{this.contactName}";
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement custOrd = XElement.Load("CustomersOrders.xml");  
        IEnumerable<Customer> custList =  
            from el in custOrd.Element("Customers").Elements("Customer")  
            select new Customer(  
                (string)el.Attribute("CustomerID"),  
                (string)el.Element("CompanyName"),  
                (string)el.Element("ContactName")  
            );  
        foreach (Customer cust in custList)  
            Console.WriteLine(cust);  
    }  
}  
```  
  
 <span data-ttu-id="53722-112">此代码生成以下输出：</span><span class="sxs-lookup"><span data-stu-id="53722-112">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="53722-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="53722-113">See Also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>  
- [<span data-ttu-id="53722-114">投影和转换 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="53722-114">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
