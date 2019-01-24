---
title: 插入、更新和删除操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
ms.openlocfilehash: 7dd2eb64a9320d88c7bc3b5feb6578d70f5910b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503659"
---
# <a name="insert-update-and-delete-operations"></a><span data-ttu-id="fa10c-102">插入、更新和删除操作</span><span class="sxs-lookup"><span data-stu-id="fa10c-102">Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="fa10c-103">在 `Insert` 中执行 `Update`、`Delete` 和 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 操作的方法是：向对象模型中添加对象、更改和移除对象模型中的对象。</span><span class="sxs-lookup"><span data-stu-id="fa10c-103">You perform `Insert`, `Update`, and `Delete` operations in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] by adding, changing, and removing objects in your object model.</span></span> <span data-ttu-id="fa10c-104">默认情况下，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会将您所做的操作转换成 SQL，然后将这些更改提交至数据库。</span><span class="sxs-lookup"><span data-stu-id="fa10c-104">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your actions to SQL and submits the changes to the database.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="fa10c-105">在操作和保持对对象所做更改方面有着最大的灵活性。</span><span class="sxs-lookup"><span data-stu-id="fa10c-105">offers maximum flexibility in manipulating and persisting changes that you made to your objects.</span></span> <span data-ttu-id="fa10c-106">实体对象可用（通过查询检索它们或通过重新构造它们）后，就可以像应用程序中的典型对象一样更改实体对象。</span><span class="sxs-lookup"><span data-stu-id="fa10c-106">As soon as entity objects are available (either by retrieving them through a query or by constructing them anew), you can change them as typical objects in your application.</span></span> <span data-ttu-id="fa10c-107">也就是说，可以更改它们的值、 可以将其添加到集合中，和可以从集合中删除它们。</span><span class="sxs-lookup"><span data-stu-id="fa10c-107">That is, you can change their values, you can add them to your collections, and you can remove them from your collections.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="fa10c-108">会跟踪您所做的更改，并且在您调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时就可以将这些更改传回数据库。</span><span class="sxs-lookup"><span data-stu-id="fa10c-108">tracks your changes and is ready to transmit them back to the database when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="fa10c-109">不支持且无法识别级联删除操作。</span><span class="sxs-lookup"><span data-stu-id="fa10c-109">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="fa10c-110">如果你想要删除的行有约束的表中，必须设置`ON DELETE CASCADE`中在数据库中，foreign key 约束的规则或使用你自己的代码首先删除阻止删除父对象的子对象。</span><span class="sxs-lookup"><span data-stu-id="fa10c-110">If you want to delete a row in a table that has constraints against it, you must either set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database, or use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span> <span data-ttu-id="fa10c-111">否则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="fa10c-111">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="fa10c-112">有关详细信息，请参阅[如何：从数据库中删除行](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md)。</span><span class="sxs-lookup"><span data-stu-id="fa10c-112">For more information, see [How to: Delete Rows From the Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).</span></span>  
  
 <span data-ttu-id="fa10c-113">以下摘录会用到 Northwind 示例数据库中的 `Customer` 和 `Order` 类。</span><span class="sxs-lookup"><span data-stu-id="fa10c-113">The following excerpts use the `Customer` and `Order` classes from the Northwind sample database.</span></span> <span data-ttu-id="fa10c-114">为简洁起见，不显示类定义。</span><span class="sxs-lookup"><span data-stu-id="fa10c-114">Class definitions are not shown for brevity.</span></span>  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 <span data-ttu-id="fa10c-115">当您调用 <xref:System.Data.Linq.DataContext.SubmitChanges%2A> 时，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 会自动生成并执行它为将您所做的更改传回数据库而必须具备的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="fa10c-115">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatically generates and executes the SQL commands that it must have to transmit your changes back to the database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa10c-116">您可以使用自己的自定义逻辑来重写此行为，这通常是通过存储过程来实现的。</span><span class="sxs-lookup"><span data-stu-id="fa10c-116">You can override this behavior by using your own custom logic, typically by way of a stored procedure.</span></span> <span data-ttu-id="fa10c-117">有关详细信息，请参阅[开发人员在重写默认行为的职责](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="fa10c-117">For more information, see [Responsibilities of the Developer In Overriding Default Behavior](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).</span></span>  
>   
>  <span data-ttu-id="fa10c-118">使用 Visual Studio 的开发人员可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]来开发用于此目的的存储的过程。</span><span class="sxs-lookup"><span data-stu-id="fa10c-118">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to develop stored procedures for this purpose.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa10c-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="fa10c-119">See also</span></span>
- [<span data-ttu-id="fa10c-120">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="fa10c-120">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="fa10c-121">自定义插入、更新和删除操作</span><span class="sxs-lookup"><span data-stu-id="fa10c-121">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
