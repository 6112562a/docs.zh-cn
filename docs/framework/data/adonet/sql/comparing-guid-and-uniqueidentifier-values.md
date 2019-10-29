---
title: 比较 GUID 和 uniqueidentifier 值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: aababd75-2335-43e3-ace8-4b7ae84191a8
ms.openlocfilehash: 18f7ad8f6ef9cdf726bdf606ab108e2c5140aed7
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040467"
---
# <a name="comparing-guid-and-uniqueidentifier-values"></a>比较 GUID 和 uniqueidentifier 值
SQL Server 中的全局唯一标识符 (GUID) 数据类型由 `uniqueidentifier` 数据类型表示，用于存储 16 字节的二进制值。 GUID 是一个二进制数字，其主要用途是作为标识符，该标识符在拥有位于许多地点的许多计算机的网络中必须是唯一的。 GUID 可以通过调用 Transact-SQL NEWID 函数生成，保证在全局是唯一的。 有关详细信息，请参阅[uniqueidentifier （transact-sql）](/sql/t-sql/data-types/uniqueidentifier-transact-sql)。  
  
## <a name="working-with-sqlguid-values"></a>使用 SqlGuid 值  
 因为 GUID 值很长并且不明确，所以对用户没有意义。 如果键值使用随机生成的 GUID，并且您插入了许多行，将随机 I/O 编入索引可能会对性能造成负面影响。 与其他数据类型相比，GUID 也相对较大。 通常，我们建议只对没有其他适用的数据类型的范围非常窄的方案使用 GUID。  
  
### <a name="comparing-guid-values"></a>比较 GUID 值  
 `uniqueidentifier` 值可以使用比较运算符。 但是，没有通过比较两个值的位模式实现排序。 允许对 `uniqueidentifier` 值进行的唯一操作是比较（=、< >、\<、>、\<=、> =）以及检查是否为 null （IS NULL 和 IS NOT NULL）。 不允许使用任何其他算术运算符。  
  
 <xref:System.Guid> 和 <xref:System.Data.SqlTypes.SqlGuid> 都具有 `CompareTo` 方法，用于比较不同的 GUID 值。 但是，`System.Guid.CompareTo` 和 `SqlTypes.SqlGuid.CompareTo` 的实现方式有所不同。 <xref:System.Data.SqlTypes.SqlGuid> 使用 SQL Server 行为来实现 `CompareTo`，其中，值的最后 6 个字节是最高有效字节。 <xref:System.Guid> 计算全部 16 个字节。 以下示例演示这种行为的差异。 代码的第一部分显示未排序的 <xref:System.Guid> 值，代码的第二部分显示排序的 <xref:System.Guid> 值。 第三部分显示排序的 <xref:System.Data.SqlTypes.SqlGuid> 值。 输出显示在代码列表下。  
  
 [!code-csharp[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.Guid#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.Guid/VB/source.vb#1)]  
  
 此示例将生成下列结果。  
  
```output  
Unsorted Guids:  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
  
Sorted Guids:  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
  
Sorted SqlGuids:  
2aaaaaaa-bbbb-cccc-dddd-1eeeeeeeeeee  
3aaaaaaa-bbbb-cccc-dddd-2eeeeeeeeeee  
1aaaaaaa-bbbb-cccc-dddd-3eeeeeeeeeee  
```  
  
## <a name="see-also"></a>请参阅

- [SQL Server 数据类型和 ADO.NET](sql-server-data-types.md)
- [ADO.NET 概述](../ado-net-overview.md)
