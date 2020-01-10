---
title: 框架设计准则
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 623391de63891c1695a63482a424bb76a861deba
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709304"
---
# <a name="framework-design-guidelines"></a>框架设计准则
本部分提供的准则适用于设计那些可扩展 .NET Framework 并与之交互的库。 目的是通过提供独立于开发所用编程语言的统一编程模型，帮助库设计者确保 API 的一致性和易用性。 建议在开发可扩展 .NET Framework 的类和组件时遵循这些设计准则。 不一致的库设计会对开发人员的工作效率产生负面影响，影响用户采用它。  
  
 这些准则已整理成简单的建议，其开头词为`要 `Do``，`考虑 `Consider``，`避免 `Avoid``和`不要 `Do not``。 这些准则旨在帮助类库设计人员了解如何在不同解决方案之间进行权衡取舍。 在某些情况下，若要进行良好的库设计，必须违反这些设计准则。 这种情况应该很罕见，重要的是，你的决定要有明确和令人信服的理由。  
  
 这些准则摘自 Krzysztof Cwalina 和 Brad Abrams 的书《Framework 设计指南： 可重用 .NET 库的约定、惯用法和模式》，第 2 版。  
  
## <a name="in-this-section"></a>本节内容  
 [命名规则](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 提供在类库中命名程序集、名称空间、类型和成员的准则。  
  
 [类型设计准则](../../../docs/standard/design-guidelines/type.md)  
 提供使用静态和抽象类、接口、枚举、结构和其他类型的指导原则。  
  
 [成员设计准则](../../../docs/standard/design-guidelines/member.md)  
 提供设计和使用属性、方法、构造函数、字段、事件、运算符和参数的准则。  
  
 [扩展性设计](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 讨论可扩展性机制，例如子类化，使用事件、虚拟成员和回调，并说明如何选择最符合框架要求的机制。  
  
 [异常的设计准则](../../../docs/standard/design-guidelines/exceptions.md)  
 介绍设计、引发和捕获异常的设计准则。  
  
 [使用准则](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 介绍常见类型（如数组、属性和集合、支持序列化及重载相等运算符）的使用准则。  
  
 [常用设计模型](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 提供有关选择和实现依赖项属性的准则。  
  
 *部分©2005，2009 Microsoft Corporation。保留所有权利。*  
  
 *在 Pearson Education, Inc. 授权下，由 Addison-Wesley Professional 作为 Microsoft Windows 开发系列的一部分再版自 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)（Framework 设计准则：可重用 .NET 库的约定、惯例和模式第 2 版），由 Krzysztof Cwalina 和 Brad Abrams 发布于 2008 年 10 月 22 日。  
  
## <a name="see-also"></a>另请参阅

- [概述](../../../docs/framework/get-started/overview.md)
- [开发指南](../../../docs/framework/development-guide.md)
