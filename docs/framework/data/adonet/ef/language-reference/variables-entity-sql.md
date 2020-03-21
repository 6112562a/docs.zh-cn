---
title: 变量 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 88ee41bc08711cf84b8b2e273c9ac0f4267d1d34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149812"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="1d057-102">变量 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1d057-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="1d057-103">变量</span><span class="sxs-lookup"><span data-stu-id="1d057-103">Variable</span></span>  
 <span data-ttu-id="1d057-104">变量表达式是对当前作用域中定义的命名表达式的引用。</span><span class="sxs-lookup"><span data-stu-id="1d057-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="1d057-105">变量引用必须是有效的[!INCLUDE[esql](../../../../../../includes/esql-md.md)]标识符，如[标识符](identifiers-entity-sql.md)中定义的那样。</span><span class="sxs-lookup"><span data-stu-id="1d057-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="1d057-106">以下示例演示如何在表达式中使用变量。</span><span class="sxs-lookup"><span data-stu-id="1d057-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="1d057-107">FROM 子句中的 `c` 是变量定义。</span><span class="sxs-lookup"><span data-stu-id="1d057-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="1d057-108">在 SELECT 子句中使用的 `c` 表示变量引用。</span><span class="sxs-lookup"><span data-stu-id="1d057-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d057-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="1d057-109">See also</span></span>

- [<span data-ttu-id="1d057-110">标识符</span><span class="sxs-lookup"><span data-stu-id="1d057-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="1d057-111">参数</span><span class="sxs-lookup"><span data-stu-id="1d057-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="1d057-112">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="1d057-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
