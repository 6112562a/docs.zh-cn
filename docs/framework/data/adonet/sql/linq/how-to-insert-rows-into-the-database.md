---
title: 如何：将行插入数据库中
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 44d99680-69c7-4879-a732-f6771b334211
ms.openlocfilehash: 3e365f0c12b2c1c6ddfa91c96ad5769b63c9e25e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2019
ms.locfileid: "70043594"
---
# <a name="how-to-insert-rows-into-the-database"></a>如何：将行插入数据库中

您可以通过将对象添加到关联[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601>的集合, 然后将更改提交到数据库, 将这些行插入到数据库中。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]将所做的更改转换为`INSERT`相应的 SQL 命令。

> [!NOTE]
> 您可以重写 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、`Insert` 和 `Update` 数据库操作的 `Delete` 默认方法。 有关详细信息, 请参阅[自定义插入、更新和删除操作](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)。
>
> 使用 Visual Studio 的开发人员可以使用对象关系设计器来开发用于实现相同目的的存储过程。

以下步骤假定您已通过有效的 <xref:System.Data.Linq.DataContext> 连接到 Northwind 数据库。 有关详细信息，请参阅[如何：连接到数据库](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md)。

### <a name="to-insert-a-row-into-the-database"></a>向数据库中插入行

1. 创建一个包含要提交的列数据的新对象。

2. 将新对象添加到与[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]数据库中的目标表关联的`Table`集合中。

3. 将更改提交到数据库。

## <a name="example"></a>示例

下面的代码示例创建一个类型为 `Order` 的新对象，并用相应的值填充此对象。 然后，它将这个新对象添加到 `Order` 集合中。 最后，它将所做的更改提交到数据库中，使之成为 `Orders` 表中的一个新行。

[!code-csharp[System.Data.Linq.Table#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#1)]
[!code-vb[System.Data.Linq.Table#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#1)]

## <a name="see-also"></a>请参阅

- [如何：管理更改冲突](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
- [DataContext 方法（O/R 设计器）](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [如何：分配存储过程以便执行更新、插入和删除操作（O/R 设计器）](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [进行和提交数据更改](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
