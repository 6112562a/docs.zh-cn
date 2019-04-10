---
title: 工厂模型概述
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 3b1d438ce5a7dbb22772d6c5dc97f196b3263d38
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221829"
---
# <a name="factory-model-overview"></a><span data-ttu-id="3fe34-102">工厂模型概述</span><span class="sxs-lookup"><span data-stu-id="3fe34-102">Factory Model Overview</span></span>
<span data-ttu-id="3fe34-103">ADO.NET 2.0 在 <xref:System.Data.Common> 命名空间中引入了新基类。</span><span class="sxs-lookup"><span data-stu-id="3fe34-103">ADO.NET 2.0 introduced new base classes in the <xref:System.Data.Common> namespace.</span></span> <span data-ttu-id="3fe34-104">基类为抽象类，这意味着它们不能直接实例化。</span><span class="sxs-lookup"><span data-stu-id="3fe34-104">The base classes are abstract, which means that they can't be directly instantiated.</span></span> <span data-ttu-id="3fe34-105">这些基类包括 <xref:System.Data.Common.DbConnection>、<xref:System.Data.Common.DbCommand> 和 <xref:System.Data.Common.DbDataAdapter>，它们由 .NET Framework 数据提供程序（如 <xref:System.Data.SqlClient> 和 <xref:System.Data.OleDb>）共享。</span><span class="sxs-lookup"><span data-stu-id="3fe34-105">They include <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, and <xref:System.Data.Common.DbDataAdapter> and are shared by the .NET Framework data providers, such as <xref:System.Data.SqlClient> and <xref:System.Data.OleDb>.</span></span> <span data-ttu-id="3fe34-106">添加基类简化了向 .NET Framework 数据提供程序添加功能的过程，不再需要创建新接口。</span><span class="sxs-lookup"><span data-stu-id="3fe34-106">The addition of base classes simplifies adding functionality to the .NET Framework data providers without having to create new interfaces.</span></span>  
  
 <span data-ttu-id="3fe34-107">ADO.NET 2.0 中还引入了一些抽象基类，使开发人员能够编写不依赖于特定数据提供程序的一般数据访问代码。</span><span class="sxs-lookup"><span data-stu-id="3fe34-107">ADO.NET 2.0 also introduced abstract base classes, which enable a developer to write generic data access code that does not depend on a specific data provider.</span></span>  
  
## <a name="the-factory-design-pattern"></a><span data-ttu-id="3fe34-108">工厂设计模式</span><span class="sxs-lookup"><span data-stu-id="3fe34-108">The Factory Design Pattern</span></span>  
 <span data-ttu-id="3fe34-109">编写独立于提供程序的代码的编程模型基于“工厂”设计模式的使用，此模式使用单个 API 跨多个提供程序访问数据库。</span><span class="sxs-lookup"><span data-stu-id="3fe34-109">The programming model for writing provider-independent code is based on the use of the "factory" design pattern, which uses a single API to access databases across multiple providers.</span></span> <span data-ttu-id="3fe34-110">此模式的命名非常恰当，因为它需单独使用专用的对象来创建其他对象，与实际的工厂非常类似。</span><span class="sxs-lookup"><span data-stu-id="3fe34-110">This pattern is aptly named, as it calls for the use of a specialized object solely to create other objects, much like a real-world factory.</span></span> <span data-ttu-id="3fe34-111">有关工厂设计模式的更详细说明，请参阅[编写泛型数据访问代码，在 ASP.NET 2.0 和 ADO.NET 2.0 中](https://go.microsoft.com/fwlink/?LinkId=55915)。</span><span class="sxs-lookup"><span data-stu-id="3fe34-111">For a more detailed description of the factory design pattern, see [Writing Generic Data Access Code in ASP.NET 2.0 and ADO.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=55915).</span></span>
  
 <span data-ttu-id="3fe34-112">从 ADO.NET 2.0 开始，<xref:System.Data.Common.DbProviderFactories> 类提供 `static`（或 Visual Basic 中的 `Shared`）方法以用于创建 <xref:System.Data.Common.DbProviderFactory> 实例。</span><span class="sxs-lookup"><span data-stu-id="3fe34-112">Starting with ADO.NET 2.0, the <xref:System.Data.Common.DbProviderFactories> class provides `static` (or `Shared` in Visual Basic) methods for creating a <xref:System.Data.Common.DbProviderFactory> instance.</span></span> <span data-ttu-id="3fe34-113">该实例随后会基于提供程序信息和运行时提供的连接字符串返回正确的强类型对象。</span><span class="sxs-lookup"><span data-stu-id="3fe34-113">The instance then returns a correct strongly typed object based on provider information and the connection string supplied at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fe34-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="3fe34-114">See also</span></span>

- [<span data-ttu-id="3fe34-115">获取 DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="3fe34-115">Obtaining a DbProviderFactory</span></span>](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="3fe34-116">DbConnection、DbCommand 和 DbException</span><span class="sxs-lookup"><span data-stu-id="3fe34-116">DbConnection, DbCommand and DbException</span></span>](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [<span data-ttu-id="3fe34-117">使用 DbDataAdapter 修改数据</span><span class="sxs-lookup"><span data-stu-id="3fe34-117">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="3fe34-118">ADO.NET 托管提供程序和 DataSet 开发人员中心</span><span class="sxs-lookup"><span data-stu-id="3fe34-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
