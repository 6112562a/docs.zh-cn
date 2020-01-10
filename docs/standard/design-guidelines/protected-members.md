---
title: 受保护的成员
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: 14ef02a760c9d4b77fe058334baffd63fcf29cfd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709096"
---
# <a name="protected-members"></a>受保护的成员
受保护的成员本身不提供任何可扩展性，但它们可以通过子类化使可扩展性更强大。 它们可用于公开高级自定义选项，而不会毫无必要地使主公共接口复杂化。  
  
 框架设计者需要小心使用受保护的成员，因为“受保护”一词会给人一种虚假的安全感。 任何人都能够对未密封的类进行子类化并访问受保护的成员，因此所有用于公共成员的防御性编码实践都适用于受保护的成员。  
  
 **✓ 考虑** 使用受保护的高级自定义的成员。  
  
 **✓ DO** 处理未密封类作为公共以便进行安全、 文档和兼容性分析中的受保护的成员。  
  
 任何人都可以从类继承并访问受保护的成员。  
  
 *部分©2005，2009 Microsoft Corporation。保留所有权利。*  
  
 *在 Pearson Education, Inc. 授权下，由 Addison-Wesley Professional 作为 Microsoft Windows 开发系列的一部分再版自 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)（Framework 设计准则：可重用 .NET 库的约定、惯例和模式第 2 版），由 Krzysztof Cwalina 和 Brad Abrams 发布于 2008 年 10 月 22 日。  
  
## <a name="see-also"></a>另请参阅

- [框架设计指南](../../../docs/standard/design-guidelines/index.md)
- [扩展性设计](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
