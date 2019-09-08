---
title: 如何：使用反射提供程序创建数据服务（WCF 数据服务）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: feee679c37cd3dafb80021752ee25444c54f0809
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791008"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="ac670-102">如何：使用反射提供程序创建数据服务（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="ac670-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
<span data-ttu-id="ac670-103">使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可以定义基于任意类的数据模型，前提是这些类作为实现 <xref:System.Linq.IQueryable%601> 接口的对象公开。</span><span class="sxs-lookup"><span data-stu-id="ac670-103">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="ac670-104">有关详细信息，请参阅[数据服务提供程序](data-services-providers-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ac670-104">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac670-105">示例</span><span class="sxs-lookup"><span data-stu-id="ac670-105">Example</span></span>  
 <span data-ttu-id="ac670-106">下面的示例定义一个包括 `Orders` 和 `Items` 的数据模型。</span><span class="sxs-lookup"><span data-stu-id="ac670-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="ac670-107">实体容器类 `OrderItemData` 具有两个公共方法，这两个方法返回 <xref:System.Linq.IQueryable%601> 接口。</span><span class="sxs-lookup"><span data-stu-id="ac670-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="ac670-108">这些接口是 `Orders` 和 `Items` 实体类型的实体集。</span><span class="sxs-lookup"><span data-stu-id="ac670-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="ac670-109">`Order` 可以包括多个 `Items`，因此 `Orders` 实体类型具有一个返回 `Items` 对象集合的 `Items` 导航属性。</span><span class="sxs-lookup"><span data-stu-id="ac670-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="ac670-110">`OrderItemData` 实体容器类是 <xref:System.Data.Services.DataService%601> 数据服务派生自的 `OrderItems` 类的泛型类型。</span><span class="sxs-lookup"><span data-stu-id="ac670-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ac670-111">由于此示例演示内存中数据提供程序，且未在当前对象实例外保存更改，因此实现 <xref:System.Data.Services.IUpdatable> 接口不会带来任何好处。</span><span class="sxs-lookup"><span data-stu-id="ac670-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="ac670-112">有关实现<xref:System.Data.Services.IUpdatable>接口的示例，请参阅[如何：使用 LINQ to SQL 数据源](create-a-data-service-using-linq-to-sql-wcf.md)创建数据服务。</span><span class="sxs-lookup"><span data-stu-id="ac670-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="ac670-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="ac670-113">See also</span></span>

- [<span data-ttu-id="ac670-114">如何：使用 LINQ to SQL 数据源创建数据服务</span><span class="sxs-lookup"><span data-stu-id="ac670-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="ac670-115">数据服务提供程序</span><span class="sxs-lookup"><span data-stu-id="ac670-115">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="ac670-116">如何：使用 ADO.NET 实体框架数据源创建数据服务</span><span class="sxs-lookup"><span data-stu-id="ac670-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
