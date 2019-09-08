---
title: 入门
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: bd82b7e83149aaa53cf1b240cb79f8747bccba47
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793910"
---
# <a name="getting-started"></a>入门
通过使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，您可以像访问[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]内存中集合一样，使用该技术来访问 SQL 数据库。  
  
 例如，在下面的代码中，创建了 `nw` 对象来表示 `Northwind` 数据库，将 `Customers` 表作为目标，筛选出了来自 `Customers` 的 `London` 行，并选择了一个表示 `CompanyName` 的字符串以进行检索。  
  
 执行循环时，将检索到 `CompanyName` 值的集合。  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>后续步骤  
 有关其他一些示例，包括插入和更新，请参阅[可以对 LINQ to SQL 执行的操作](what-you-can-do-with-linq-to-sql.md)。  
  
 接下来，请试着按一些演练和教程中的说明动手操作，实际体验一下 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的使用。 请参阅[通过演练学习](learning-by-walkthroughs.md)。  
  
 最后，请阅读[使用 LINQ to SQL 的典型步骤](typical-steps-for-using-linq-to-sql.md)， [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]了解如何开始使用自己的项目。  
  
## <a name="see-also"></a>请参阅

- [LINQ to SQL](index.md)
- [LINQ （C#）简介](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [LINQ 简介 (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [LINQ to SQL 对象模型](the-linq-to-sql-object-model.md)
