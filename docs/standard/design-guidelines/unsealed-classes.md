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
# <a name="unsealed-classes"></a><span data-ttu-id="8e64a-102">봉인되지 않은 클래스</span><span class="sxs-lookup"><span data-stu-id="8e64a-102">Unsealed Classes</span></span>
<span data-ttu-id="8e64a-103">密封类不能从继承，它们会阻止可扩展性。</span><span class="sxs-lookup"><span data-stu-id="8e64a-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="8e64a-104">与此相反，可被继承的类称为非密封类。</span><span class="sxs-lookup"><span data-stu-id="8e64a-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>

 <span data-ttu-id="8e64a-105">✔️考虑使用未密封的类，而不添加虚拟成员或受保护成员，这是为框架提供廉价但非常感谢的扩展性的极佳方式。</span><span class="sxs-lookup"><span data-stu-id="8e64a-105">✔️ CONSIDER using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>

 <span data-ttu-id="8e64a-106">开发人员通常希望从非密封的类继承，以便添加自定义构造函数、新方法或方法重载等便利成员。</span><span class="sxs-lookup"><span data-stu-id="8e64a-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="8e64a-107">例如，`System.Messaging.MessageQueue` 是非密封的，因此用户可以创建默认为特定队列路径的自定义队列，或添加自定义方法以简化特定方案的 API。</span><span class="sxs-lookup"><span data-stu-id="8e64a-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>

 <span data-ttu-id="8e64a-108">在大多数编程语言中，默认情况下类都是非密封的，这也是框架中大多数类的推荐默认值。</span><span class="sxs-lookup"><span data-stu-id="8e64a-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="8e64a-109">框架用户非常需要非密封类型提供的可扩展性，并且这种可扩展性的提供成本相当低，因为非密封类型的相关测试成本也相对较低。</span><span class="sxs-lookup"><span data-stu-id="8e64a-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>

 <span data-ttu-id="8e64a-110">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="8e64a-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="8e64a-111">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="8e64a-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="8e64a-112">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8e64a-112">See also</span></span>

- [<span data-ttu-id="8e64a-113">프레임워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="8e64a-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="8e64a-114">확장성을 위한 디자인</span><span class="sxs-lookup"><span data-stu-id="8e64a-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="8e64a-115">봉인</span><span class="sxs-lookup"><span data-stu-id="8e64a-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
