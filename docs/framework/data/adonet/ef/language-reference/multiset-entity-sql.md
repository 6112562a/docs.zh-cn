---
title: MULTISET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: eb90a377-e47a-43a5-b308-e993b6d611e6
ms.openlocfilehash: eb676feeb168e1fb184f3869a18e138bff34211b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929346"
---
# <a name="multiset-entity-sql"></a>MULTISET (Entity SQL)
根据值列表创建多集的实例。 MULTISET 构造函数中的所有值都必须具有兼容类型 `T`。 不允许使用空的多集构造函数。  
  
## <a name="syntax"></a>语法  
  
```  
MULTISET ( expression [{, expression }] )  
or  
{ expression [{, expression }] }  
```  
  
## <a name="arguments"></a>自变量  
 `expression`  
 任何有效的值列表。  
  
## <a name="return-value"></a>返回值  
 > 类型\<的集合。  
  
## <a name="remarks"></a>备注  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 提供了三种构造函数：行构造函数、对象构造函数和多集（或集合）构造函数。 有关详细信息, 请参阅[构造类型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)。  
  
 多集构造函数根据值列表创建多集的实例。 该构造函数中的所有值都必须具有兼容类型。  
  
 例如，下面的表达式创建整数的多集。  
  
 `MULTISET(1, 2, 3)`  
  
 `{1, 2, 3}`  
  
> [!NOTE]
> 仅当包装多集具有单个多重集元素时才支持嵌套的多集文本;例如, `{{1, 2, 3}}`。 当包装多集具有多个多集元素（如 `{{1, 2}, {3, 4}}`）时，不支持嵌套多集文本。  
  
## <a name="example"></a>示例  
 下面的 Entity SQL 查询使用 MULTISET 运算符根据值列表创建多集的实例。 此查询基于 AdventureWorks 销售模型。 若要编译并运行此查询，请执行下列步骤：  
  
1. [按照如何:执行返回 StructuralType 结果](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)的查询。  
  
2. 将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#MULTISET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#multiset)]  
  
## <a name="see-also"></a>请参阅

- [构造类型](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md)
- [实体 SQL 引用](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
