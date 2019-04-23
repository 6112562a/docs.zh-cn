---
title: 如何：查询信息
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: aedf89f1e570b34d31050fabb91842cefe351488
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162837"
---
# <a name="how-to-query-for-information"></a><span data-ttu-id="18c05-102">如何：查询信息</span><span class="sxs-lookup"><span data-stu-id="18c05-102">How to: Query for Information</span></span>
<span data-ttu-id="18c05-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中的查询与 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 中的查询使用相同的语法。</span><span class="sxs-lookup"><span data-stu-id="18c05-103">Queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] use the same syntax as queries in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="18c05-104">唯一的区别是中引用的对象[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]查询映射到数据库中的元素。</span><span class="sxs-lookup"><span data-stu-id="18c05-104">The only difference is that the objects referenced in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries are mapped to elements in a database.</span></span> <span data-ttu-id="18c05-105">有关详细信息，请参阅 [LINQ 查询简介 (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="18c05-105">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="18c05-106">将您编写的查询转换成等效的 SQL 查询，然后将它们发送至服务器进行处理。</span><span class="sxs-lookup"><span data-stu-id="18c05-106">translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span>  
  
 <span data-ttu-id="18c05-107">在 [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] 应用程序中，可能需要特别注意 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 查询的某些功能。</span><span class="sxs-lookup"><span data-stu-id="18c05-107">Some features of [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] queries might need special attention in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications.</span></span> <span data-ttu-id="18c05-108">有关详细信息，请参阅[查询概念](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="18c05-108">For more information, see [Query Concepts](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18c05-109">示例</span><span class="sxs-lookup"><span data-stu-id="18c05-109">Example</span></span>  
 <span data-ttu-id="18c05-110">下面的查询请求来自伦敦的客户的列表。</span><span class="sxs-lookup"><span data-stu-id="18c05-110">The following query asks for a list of customers from London.</span></span> <span data-ttu-id="18c05-111">在此示例中，`Customers` 是 Northwind 示例数据库中的表。</span><span class="sxs-lookup"><span data-stu-id="18c05-111">In this example, `Customers` is a table in the Northwind sample database.</span></span>  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="18c05-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="18c05-112">See also</span></span>

- [<span data-ttu-id="18c05-113">创建对象模型</span><span class="sxs-lookup"><span data-stu-id="18c05-113">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [<span data-ttu-id="18c05-114">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="18c05-114">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="18c05-115">查询数据库</span><span class="sxs-lookup"><span data-stu-id="18c05-115">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
