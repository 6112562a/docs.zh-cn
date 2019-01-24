---
title: 如何：执行参数化的 Entity SQL 查询使用 EntityCommand
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: a9b4069004cc48fa05efa29b4467aa1dca47fb29
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610092"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="6cb44-102">如何：执行参数化的 Entity SQL 查询使用 EntityCommand</span><span class="sxs-lookup"><span data-stu-id="6cb44-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="6cb44-103">本主题演示如何执行[!INCLUDE[esql](../../../../../includes/esql-md.md)]通过使用具有参数的查询<xref:System.Data.EntityClient.EntityCommand>对象。</span><span class="sxs-lookup"><span data-stu-id="6cb44-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="6cb44-104">运行本示例中的代码</span><span class="sxs-lookup"><span data-stu-id="6cb44-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="6cb44-105">添加[AdventureWorks 销售模型](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)到你的项目和配置项目以使用[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6cb44-105">Add the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="6cb44-106">有关详细信息，请参阅[如何：使用实体数据模型向导](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)。</span><span class="sxs-lookup"><span data-stu-id="6cb44-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="6cb44-107">在应用程序的代码页中，添加以下 `using` 语句（在 Visual Basic 中为 `Imports`）：</span><span class="sxs-lookup"><span data-stu-id="6cb44-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="6cb44-108">示例</span><span class="sxs-lookup"><span data-stu-id="6cb44-108">Example</span></span>  
 <span data-ttu-id="6cb44-109">以下示例显示如何使用两个参数构造一个查询字符串。</span><span class="sxs-lookup"><span data-stu-id="6cb44-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="6cb44-110">然后，它创建 <xref:System.Data.EntityClient.EntityCommand>，将两个参数添加到该 <xref:System.Data.EntityClient.EntityParameter> 的 <xref:System.Data.EntityClient.EntityCommand> 集合，并循环访问 `Contact` 项的集合。</span><span class="sxs-lookup"><span data-stu-id="6cb44-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="6cb44-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="6cb44-111">See also</span></span>
- [<span data-ttu-id="6cb44-112">如何：执行参数化的查询</span><span class="sxs-lookup"><span data-stu-id="6cb44-112">How to: Execute a Parameterized Query</span></span>](https://msdn.microsoft.com/library/42048f03-c65c-4d98-b50a-3e7d537a63e8)
- [<span data-ttu-id="6cb44-113">实体 SQL 语言</span><span class="sxs-lookup"><span data-stu-id="6cb44-113">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
