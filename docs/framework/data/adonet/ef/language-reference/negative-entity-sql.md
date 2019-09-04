---
title: '- 负极（实体 SQL）'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: effd537bcd53052830f2195e18ca959b49d87255
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249927"
---
# <a name="--negative-entity-sql"></a>-（负号）(Entity SQL)
返回数值表达式的值的负值。  
  
## <a name="syntax"></a>语法  
  
```  
- expression  
```  
  
## <a name="arguments"></a>自变量  
 `expression`  
 任何一种数值数据类型的任何有效表达式。  
  
## <a name="result-types"></a>结果类型  
 `expression`的数据类型。  
  
## <a name="remarks"></a>备注  
 如果 `expression` 为无符号类型，则结果类型将是与 `expression`的类型相关性最密切的有符号类型。 例如，如果 `expression` 属于 Byte 类型，则将返回类型为 Int16 的值。  
  
## <a name="example"></a>示例  
 以下 Entity SQL 查询使用 - 算数运算符以返回数值表达式的值的负值。 此查询基于 AdventureWorks 销售模型。 若要编译并运行此查询，请执行下列步骤：  
  
1. [按照如何：执行返回 StructuralType 结果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查询。  
  
2. 将以下查询作为参数传递给 `ExecuteStructuralTypeQuery` 方法：  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a>请参阅

- [实体 SQL 引用](entity-sql-reference.md)
