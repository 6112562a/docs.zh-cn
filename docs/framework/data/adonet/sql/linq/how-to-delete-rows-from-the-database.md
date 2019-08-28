---
title: 如何：从数据库中删除行
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2144c99b-8055-4080-a5c6-1ea14335e2a3
ms.openlocfilehash: 48377aed85aebcf83cb61b4d4dcf9bb732d0cb0e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041183"
---
# <a name="how-to-delete-rows-from-the-database"></a><span data-ttu-id="edb2a-102">如何：从数据库中删除行</span><span class="sxs-lookup"><span data-stu-id="edb2a-102">How to: Delete Rows From the Database</span></span>

<span data-ttu-id="edb2a-103">您可以通过删除与表相关的集合中的[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]相应对象来删除数据库中的行。</span><span class="sxs-lookup"><span data-stu-id="edb2a-103">You can delete rows in a database by removing the corresponding [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] objects from their table-related collection.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="edb2a-104">将所做的更改转换为`DELETE`相应的 SQL 命令。</span><span class="sxs-lookup"><span data-stu-id="edb2a-104">translates your changes to the appropriate SQL `DELETE` commands.</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="edb2a-105">不支持且无法识别级联删除操作。</span><span class="sxs-lookup"><span data-stu-id="edb2a-105">does not support or recognize cascade-delete operations.</span></span> <span data-ttu-id="edb2a-106">如果要在对行有约束的表中删除行，则必须完成以下任务之一：</span><span class="sxs-lookup"><span data-stu-id="edb2a-106">If you want to delete a row in a table that has constraints against it, you must complete either of the following tasks:</span></span>

- <span data-ttu-id="edb2a-107">在数据库的外键约束中设置 `ON DELETE CASCADE` 规则。</span><span class="sxs-lookup"><span data-stu-id="edb2a-107">Set the `ON DELETE CASCADE` rule in the foreign-key constraint in the database.</span></span>

- <span data-ttu-id="edb2a-108">使用你自己的代码先删除阻止删除父对象的子对象。</span><span class="sxs-lookup"><span data-stu-id="edb2a-108">Use your own code to first delete the child objects that prevent the parent object from being deleted.</span></span>

 <span data-ttu-id="edb2a-109">否则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="edb2a-109">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="edb2a-110">请参见本主题中后面的第二个代码示例。</span><span class="sxs-lookup"><span data-stu-id="edb2a-110">See the second code example later in this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="edb2a-111">您可以重写 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、`Insert` 和 `Update` 数据库操作的 `Delete` 默认方法。</span><span class="sxs-lookup"><span data-stu-id="edb2a-111">You can override [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default methods for `Insert`, `Update`, and `Delete` database operations.</span></span> <span data-ttu-id="edb2a-112">有关详细信息, 请参阅[自定义插入、更新和删除操作](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。</span><span class="sxs-lookup"><span data-stu-id="edb2a-112">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>
>
> <span data-ttu-id="edb2a-113">使用 Visual Studio 的开发人员可以使用对象关系设计器来开发用于实现相同目的的存储过程。</span><span class="sxs-lookup"><span data-stu-id="edb2a-113">Developers using Visual Studio can use the Object Relational Designer to develop stored procedures for the same purpose.</span></span>

<span data-ttu-id="edb2a-114">以下步骤假定您已通过有效的 <xref:System.Data.Linq.DataContext> 连接到 Northwind 数据库。</span><span class="sxs-lookup"><span data-stu-id="edb2a-114">The following steps assume that a valid <xref:System.Data.Linq.DataContext> connects you to the Northwind database.</span></span> <span data-ttu-id="edb2a-115">有关详细信息，请参阅[如何：连接到数据库](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="edb2a-115">For more information, see [How to: Connect to a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).</span></span>

### <a name="to-delete-a-row-in-the-database"></a><span data-ttu-id="edb2a-116">删除数据库中的行</span><span class="sxs-lookup"><span data-stu-id="edb2a-116">To delete a row in the database</span></span>

1. <span data-ttu-id="edb2a-117">查询数据库中要删除的行。</span><span class="sxs-lookup"><span data-stu-id="edb2a-117">Query the database for the row to be deleted.</span></span>

2. <span data-ttu-id="edb2a-118">调用 <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="edb2a-118">Call the <xref:System.Data.Linq.Table%601.DeleteOnSubmit%2A> method.</span></span>

3. <span data-ttu-id="edb2a-119">将更改提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="edb2a-119">Submit the change to the database.</span></span>

## <a name="example"></a><span data-ttu-id="edb2a-120">示例</span><span class="sxs-lookup"><span data-stu-id="edb2a-120">Example</span></span>

<span data-ttu-id="edb2a-121">这第一个代码示例查询数据库中 11000 号订单的详细信息，将这些订单详细信息标记为删除，然后将这些更改提交到数据库。</span><span class="sxs-lookup"><span data-stu-id="edb2a-121">This first code example queries the database for order details that belong to Order #11000, marks these order details for deletion, and submits these changes to the database.</span></span>

[!code-csharp[System.Data.Linq.Table#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#3)]
[!code-vb[System.Data.Linq.Table#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="edb2a-122">示例</span><span class="sxs-lookup"><span data-stu-id="edb2a-122">Example</span></span>

<span data-ttu-id="edb2a-123">在第二个示例中，目的是删除订单（10250 号）。</span><span class="sxs-lookup"><span data-stu-id="edb2a-123">In this second example, the objective is to remove an order (#10250).</span></span> <span data-ttu-id="edb2a-124">代码首先检查 `OrderDetails` 表以查看要删除的订单是否有子项。</span><span class="sxs-lookup"><span data-stu-id="edb2a-124">The code first examines the `OrderDetails` table to see whether the order to be removed has children there.</span></span> <span data-ttu-id="edb2a-125">如果订单有子项，则首先将子项标为删除，然后将订单标为删除。</span><span class="sxs-lookup"><span data-stu-id="edb2a-125">If the order has children, first the children and then the order are marked for removal.</span></span> <span data-ttu-id="edb2a-126"><xref:System.Data.Linq.DataContext> 为实际删除设置正确的顺序，以使发送到数据库的删除命令遵守数据库约束。</span><span class="sxs-lookup"><span data-stu-id="edb2a-126">The <xref:System.Data.Linq.DataContext> puts the actual deletes in correct order so that delete commands sent to the database abide by the database constraints.</span></span>

[!code-csharp[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCascadeWorkaround/cs/Program.cs#1)]
[!code-vb[DLinqCascadeWorkaround#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCascadeWorkaround/vb/Module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="edb2a-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="edb2a-127">See also</span></span>

- [<span data-ttu-id="edb2a-128">如何：管理更改冲突</span><span class="sxs-lookup"><span data-stu-id="edb2a-128">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [<span data-ttu-id="edb2a-129">如何：分配存储过程以便执行更新、插入和删除操作（O/R 设计器）</span><span class="sxs-lookup"><span data-stu-id="edb2a-129">How to: Assign stored procedures to perform updates, inserts, and deletes (O/R Designer)</span></span>](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [<span data-ttu-id="edb2a-130">进行和提交数据更改</span><span class="sxs-lookup"><span data-stu-id="edb2a-130">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
