---
title: 如何：指定数据库名称
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: a43a7ac541adb984eeb8bb88b7ab96db86baf26c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037565"
---
# <a name="how-to-specify-database-names"></a>如何：指定数据库名称
使用 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 属性 (Attribute) 的 <xref:System.Data.Linq.Mapping.DatabaseAttribute> 属性 (Property) 可在连接未提供名称时指定数据库的名称。  
  
 有关代码示例，请参见<xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>。  
  
### <a name="to-specify-the-name-of-the-database"></a>指定数据库的名称  
  
1. 将 <xref:System.Data.Linq.Mapping.DatabaseAttribute> 属性添加到数据库的类声明中。  
  
2. 将 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 属性 (Property) 添加到 <xref:System.Data.Linq.Mapping.DatabaseAttribute> 属性 (Attribute)。  
  
3. 将 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 属性值设置为您要指定的名称。  
  
## <a name="see-also"></a>请参阅

- [LINQ to SQL 对象模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [如何：通过使用代码编辑器自定义实体类](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
