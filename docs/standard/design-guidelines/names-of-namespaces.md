---
title: 命名空间的名称
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 0678f695e3ae7c40660031862c9073a21fd72491
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709226"
---
# <a name="names-of-namespaces"></a>命名空间的名称
与其他命名准则一样，为命名空间命名的目的是为了让使用该框架的程序员能够通过名称快速了解命名空间所涉及的内容。 以下模板指定了为命名空间命名的一般规则：  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 下面是一些示例：  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ 务必**使用一个公司名作为命名空间的前缀，以防止不同公司的命名空间具有相同的名称。  
  
 **✓ 务必**在命名空间名称的第二级名称中使用稳定的、与版本无关的产品名称。  
  
 **X 不要**使用企业组织的层次结构作为命名空间层次结构中名称的基础，因为公司内的群组名称往往是短期的。应围绕相关技术的群组来组织命名空间的层次结构。 围绕一组相关技术组织命名空间的层次结构。  
  
 **✓ 务必**使用 PascalCasing，并使用句点分隔命名空间组件（例如，`Microsoft.Office.PowerPoint`）。 如果品牌使用非传统的大小写形式，则应遵循由品牌定义的大小写，即使与通常的命名空间大小写不符也是如此。  
  
 **✓ 考虑**在适当时使用复数形式的命名空间名称。  
  
 例如，请使用 `System.Collections` 而不是 `System.Collection`。 但此规则不适用于品牌名称和首字母缩写词。 例如，请使用 `System.IO` 而不是 `System.IOs`。  
  
 **X 不要**对命名空间和该命名空间中的类型使用相同的名称。  
  
 例如，如果将命名空间命名为 `Debug`，就不应在该命名空间中提供一个名为 `Debug` 的类。 某些编译器要求这些类型为完全限定类型。  
  
### <a name="namespaces-and-type-name-conflicts"></a>命名空间和类型名称冲突  
 **X 不要**引入泛型类型名称，如 `Element`、`Node`、`Log` 和 `Message` 等。  
  
 很多情况下，这样做会导致在常见方案中发生类型名称冲突。 一般情况下，这样做很可能会导致类型名称冲突。应限定泛型类型名称（`FormElement`、`XmlNode`、`EventLog`、`SoapMessage`）。  
  
 针对不同类别的命名空间，存在避免类型名称冲突的特定准则。  
  
- **应用程序模型命名空间**  
  
     属于同一应用程序模型的命名空间经常一起使用，但它们几乎从不与其他应用程序模型的命名空间一起使用。 例如，<xref:System.Windows.Forms?displayProperty=nameWithType> 命名空间很少与 <xref:System.Web.UI?displayProperty=nameWithType> 命名空间一起使用。以下是一个常见的应用程序模型命名空间组的列表： 下面列出了众所周知的应用程序模型命名空间组：  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X 不要**在单个应用程序模型中为名称空间中的类型指定相同的名称。  
  
     例如，不要在 <xref:System.Web.UI.Adapters?displayProperty=nameWithType> 命名空间中添加名为 `Page` 的类型，因为 <xref:System.Web.UI?displayProperty=nameWithType> 命名空间已包含名为 `Page` 的类型。  
  
- **基础结构命名空间**  
  
     该组包含在开发常见应用程序期间鲜少导入的命名空间。 例如，`.Design` 命名空间主要用于开发编程工具。 避免与这些命名空间中的类型发生冲突并不重要。  
  
- **核心命名空间**  
  
     核心命名空间包括所有 `System` 命名空间，不包括应用程序模型命名空间和基础结构命名空间。 核心命名空间包括 `System`、`System.IO`、`System.Xml` 和 `System.Net` 等。  
  
     **X 不要**指定与核心命名空间中任何类型相冲突的类型名称。  
  
     例如，永远不要将 `Stream` 用作类型名称。 它会与十分常用的类型 <xref:System.IO.Stream?displayProperty=nameWithType> 相冲突。  
  
- **技术命名空间组**  
  
     此类别包括前两个命名空间节点一致 (`(<Company>.<Technology>*`) 的所有命名空间，例如 `Microsoft.Build.Utilities` 和 `Microsoft.Build.Tasks`。 属于同一单一技术的类型之间不能相互冲突，这一点很重要。  
  
     **X DO NOT** 分配会冲突的类型名称与某个单一技术中其他类型。  
  
     **X 不要**让技术命名空间和应用程序模型命名空间中的类型之间产生类型名称冲突（除非不打算将该技术与该应用程序模型一起使用）。  
  
 *部分©2005，2009 Microsoft Corporation。保留所有权利。*  
  
 *在 Pearson Education, Inc. 授权下，由 Addison-Wesley Professional 作为 Microsoft Windows 开发系列的一部分再版自 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)（Framework 设计准则：可重用 .NET 库的约定、惯例和模式第 2 版），由 Krzysztof Cwalina 和 Brad Abrams 发布于 2008 年 10 月 22 日。  
  
## <a name="see-also"></a>另请参阅

- [框架设计指南](../../../docs/standard/design-guidelines/index.md)
- [命名规则](../../../docs/standard/design-guidelines/naming-guidelines.md)
