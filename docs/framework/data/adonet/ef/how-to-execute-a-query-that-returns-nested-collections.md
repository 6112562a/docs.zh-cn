---
title: 如何：执行返回嵌套的集合的查询
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: f429b8e8f546669fba64b9ee04222d399971936e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654511"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="571e3-102">如何：执行返回嵌套的集合的查询</span><span class="sxs-lookup"><span data-stu-id="571e3-102">How to: Execute a Query that Returns Nested Collections</span></span>
<span data-ttu-id="571e3-103">这些内容演示如何使用 <xref:System.Data.EntityClient.EntityCommand> 对象针对概念模型执行命令，以及如何使用 <xref:System.Data.EntityClient.EntityDataReader> 检索嵌套集合结果。</span><span class="sxs-lookup"><span data-stu-id="571e3-103">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="571e3-104">运行本示例中的代码</span><span class="sxs-lookup"><span data-stu-id="571e3-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="571e3-105">添加[AdventureWorks 销售模型](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)到你的项目和配置项目以使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="571e3-105">Add the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="571e3-106">有关详细信息，请参阅[如何：使用实体数据模型向导](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)。</span><span class="sxs-lookup"><span data-stu-id="571e3-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="571e3-107">在应用程序的代码页中，添加以下 `using` 语句（在 Visual Basic 中为 `Imports`）：</span><span class="sxs-lookup"><span data-stu-id="571e3-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="571e3-108">示例</span><span class="sxs-lookup"><span data-stu-id="571e3-108">Example</span></span>  
 <span data-ttu-id="571e3-109">一个*嵌套集合*是位于另一个集合的集合。</span><span class="sxs-lookup"><span data-stu-id="571e3-109">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="571e3-110">以下代码检索 `Contacts` 的集合以及与每个 `SalesOrderHeaders` 关联的 `Contact` 的嵌套集合。</span><span class="sxs-lookup"><span data-stu-id="571e3-110">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="571e3-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="571e3-111">See also</span></span>
- [<span data-ttu-id="571e3-112">用于实体框架的 EntityClient 提供程序</span><span class="sxs-lookup"><span data-stu-id="571e3-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
