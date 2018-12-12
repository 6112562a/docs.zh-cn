---
title: 虚成员
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: KrzysztofCwalina
ms.openlocfilehash: 1719e9843252c25d1e799471330c6cb08211245b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128917"
---
# <a name="virtual-members"></a>虚成员
可以重写虚拟成员，因此更改行为的子类。 它们是非常类似于在它们提供的可扩展性方面的回调，但它们是在执行性能和内存消耗方面更好。 此外，虚拟成员感觉更自然需要创建一种特殊类型的现有类型 （专用化） 的方案中。  
  
 虚拟成员优于回调和事件，但不是与非虚拟方法相比更好地执行。  
  
 虚拟成员的主要缺点是，虚拟成员的行为仅可以修改在编译时。 可以在运行时修改回调的行为。  
  
 虚拟成员，例如回调 （和可能有多个回调），是成本设计、 测试和维护，因为对虚拟成员的任何调用可以重写不可预知的方式，并可以执行任意代码。 此外，明确定义的虚拟成员的协定，因此设计和记录它们的成本更高版本时通常需要更多精力。  
  
 **X DO NOT** 虚成员，除非你有理由这样做，并且注意与设计、 测试和维护虚拟成员相关的所有成本。  
  
 虚拟成员是更少内能容忍方面可以与其进行而不会破坏兼容性的更改。 此外，它们是慢于非虚拟成员，主要是因为对虚拟成员的调用不是内联。  
  
 **✓ CONSIDER** 限制只将绝对必要的扩展性。  
  
 **✓ DO** 首选受保护的辅助功能的虚拟成员，而公共可访问性。 公共成员应通过调用受保护虚拟成员来提供可扩展性 （如果需要）。  
  
 一个类的公共成员应为该类的直接使用者提供一组合适的功能。 旨在子类中, 被重写虚拟成员和受保护的可访问性是作用域为使用其中的所有虚拟扩展点的好办法。  
  
 *部分版权 © 2005, 2009 Microsoft Corporation。保留所有权利。*  
  
 *通过从 Pearson Education，Inc.的权限重新打印[Framework 设计准则：约定、 语法和模式的可重用.NET 库，第 2 版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，作为 Microsoft Windows 开发系列的一部分发布 2008 年 10 月 22 日由 Addison-wesley 专业人员。*  
  
## <a name="see-also"></a>请参阅

- [框架设计指南](../../../docs/standard/design-guidelines/index.md)  
- [扩展性设计](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
