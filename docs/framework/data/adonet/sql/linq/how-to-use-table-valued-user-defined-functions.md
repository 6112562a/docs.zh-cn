---
title: 如何：使用表值用户定义的函数
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: c4b5290e4f1aa69c7f55951d526ccb303a5a95ec
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003184"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a><span data-ttu-id="5942a-102">如何：使用表值用户定义的函数</span><span class="sxs-lookup"><span data-stu-id="5942a-102">How to: Use Table-Valued User-Defined Functions</span></span>
<span data-ttu-id="5942a-103">表值函数返回单个行集（与存储过程不同，存储过程可返回多个结果形状）。</span><span class="sxs-lookup"><span data-stu-id="5942a-103">A table-valued function returns a single rowset (unlike stored procedures, which can return multiple result shapes).</span></span> <span data-ttu-id="5942a-104">由于表值函数的返回类型为 `Table`，因此在 SQL 中可以使用表的任何地方均可以使用表值函数。</span><span class="sxs-lookup"><span data-stu-id="5942a-104">Because the return type of a table-valued function is `Table`, you can use a table-valued function anywhere in SQL that you can use a table.</span></span> <span data-ttu-id="5942a-105">此外，您还可以完全像处理表那样来处理表值函数。</span><span class="sxs-lookup"><span data-stu-id="5942a-105">You can also treat the table-valued function just as you would a table.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5942a-106">示例</span><span class="sxs-lookup"><span data-stu-id="5942a-106">Example</span></span>  
 <span data-ttu-id="5942a-107">下面的 SQL 函数显式声明其返回一个 `TABLE`。</span><span class="sxs-lookup"><span data-stu-id="5942a-107">The following SQL function explicitly states that it returns a `TABLE`.</span></span> <span data-ttu-id="5942a-108">因此，隐式定义了所返回的行集结构。</span><span class="sxs-lookup"><span data-stu-id="5942a-108">Therefore, the returned rowset structure is implicitly defined.</span></span>  
  
```sql
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="5942a-109">按如下方式映射此函数：</span><span class="sxs-lookup"><span data-stu-id="5942a-109">maps the function as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="5942a-110">示例</span><span class="sxs-lookup"><span data-stu-id="5942a-110">Example</span></span>  
 <span data-ttu-id="5942a-111">下面的 SQL 代码说明你可以对此函数返回的表执行联接，以及像处理任何其他表一样处理它：</span><span class="sxs-lookup"><span data-stu-id="5942a-111">The following SQL code shows that you can join to the table that the function returns and otherwise treat it as you would any other table:</span></span>  
  
```sql
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 <span data-ttu-id="5942a-112">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，此查询的呈现结果如下：</span><span class="sxs-lookup"><span data-stu-id="5942a-112">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], the query would be rendered as follows:</span></span>  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5942a-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="5942a-113">See also</span></span>

- [<span data-ttu-id="5942a-114">用户定义的函数</span><span class="sxs-lookup"><span data-stu-id="5942a-114">User-Defined Functions</span></span>](user-defined-functions.md)
