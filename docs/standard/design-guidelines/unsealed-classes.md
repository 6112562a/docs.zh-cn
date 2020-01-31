---
title: 봉인되지 않은 클래스
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
ms.openlocfilehash: 6804a79e8beee1d42e313509966b46239e66c25f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743560"
---
# <a name="unsealed-classes"></a>봉인되지 않은 클래스
密封类不能从继承，它们会阻止可扩展性。 与此相反，可被继承的类称为非密封类。

 ✔️考虑使用未密封的类，而不添加虚拟成员或受保护成员，这是为框架提供廉价但非常感谢的扩展性的极佳方式。

 开发人员通常希望从非密封的类继承，以便添加自定义构造函数、新方法或方法重载等便利成员。 例如，`System.Messaging.MessageQueue` 是非密封的，因此用户可以创建默认为特定队列路径的自定义队列，或添加自定义方法以简化特定方案的 API。

 在大多数编程语言中，默认情况下类都是非密封的，这也是框架中大多数类的推荐默认值。 框架用户非常需要非密封类型提供的可扩展性，并且这种可扩展性的提供成本相当低，因为非密封类型的相关测试成本也相对较低。

 *部分©2005，2009 Microsoft Corporation。保留所有权利。*

 *Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*

## <a name="see-also"></a>另请参阅

- [프레임워크 디자인 지침](../../../docs/standard/design-guidelines/index.md)
- [확장성을 위한 디자인](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [봉인](../../../docs/standard/design-guidelines/sealing.md)
