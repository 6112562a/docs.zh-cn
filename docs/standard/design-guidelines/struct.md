---
title: 结构设计
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
author: KrzysztofCwalina
ms.openlocfilehash: e787c5b34848a561b43c3457341673f11cc2bd00
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775545"
---
# <a name="struct-design"></a><span data-ttu-id="7310a-102">结构设计</span><span class="sxs-lookup"><span data-stu-id="7310a-102">Struct Design</span></span>
<span data-ttu-id="7310a-103">常规用途的值类型通常称为结构，其 C# 关键字。</span><span class="sxs-lookup"><span data-stu-id="7310a-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="7310a-104">本部分提供有关常规结构设计指导原则。</span><span class="sxs-lookup"><span data-stu-id="7310a-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="7310a-105">**X 不**结构提供一个无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="7310a-105">**X DO NOT** provide a parameterless constructor for a struct.</span></span>  
  
 <span data-ttu-id="7310a-106">遵循此原则将允许创建结构数组，而无需对数组的每个项运行构造函数。</span><span class="sxs-lookup"><span data-stu-id="7310a-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="7310a-107">请注意，C#不允许结构具有无参数构造函数。</span><span class="sxs-lookup"><span data-stu-id="7310a-107">Notice that C# does not allow structs to have parameterless constructors.</span></span>  
  
 <span data-ttu-id="7310a-108">**X 切忌**定义可变值类型。</span><span class="sxs-lookup"><span data-stu-id="7310a-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="7310a-109">可变值类型有几个问题。</span><span class="sxs-lookup"><span data-stu-id="7310a-109">Mutable value types have several problems.</span></span> <span data-ttu-id="7310a-110">例如，当属性 getter 返回值类型时，调用者会收到一个副本。</span><span class="sxs-lookup"><span data-stu-id="7310a-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="7310a-111">由于该副本是隐式创建的，因此开发人员可能不会意识到他们正在改变副本，而不是原始值。</span><span class="sxs-lookup"><span data-stu-id="7310a-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="7310a-112">此外，某些语言（尤其是动态语言）在使用可变值类型时会遇到问题，因为即使局部变量在解除引用时也会导致生成副本。</span><span class="sxs-lookup"><span data-stu-id="7310a-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="7310a-113">**✓ 务必**确保所有实例数据设置为零、false 或 null（视情况而定）的状态是有效的。</span><span class="sxs-lookup"><span data-stu-id="7310a-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="7310a-114">这可以防止在创建结构数组时意外创建无效实例。</span><span class="sxs-lookup"><span data-stu-id="7310a-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="7310a-115">**✓ 务必**为值类型实现 <xref:System.IEquatable%601>。</span><span class="sxs-lookup"><span data-stu-id="7310a-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="7310a-116">值类型的 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 方法会导致装箱，并且其默认实现效率不高，因为它使用反射。</span><span class="sxs-lookup"><span data-stu-id="7310a-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="7310a-117"><xref:System.IEquatable%601.Equals%2A> 可以有更好的性能，并且可以进行实现，这样它就不会导致装箱。</span><span class="sxs-lookup"><span data-stu-id="7310a-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="7310a-118">X 请勿显式扩展 <xref:System.ValueType>。 </span><span class="sxs-lookup"><span data-stu-id="7310a-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="7310a-119">实际上，大多数语言禁止此行为。</span><span class="sxs-lookup"><span data-stu-id="7310a-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="7310a-120">一般情况下，结构可能非常有用，但应仅用于不经常装箱的单个不可变的小值。</span><span class="sxs-lookup"><span data-stu-id="7310a-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="7310a-121">*Portions © 2005, 2009 Microsoft Corporation 版权所有。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="7310a-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7310a-122">*经 Pearson Education, Inc 授权，转载自[框架设计准则：可重用的 .NET 库的约定、习惯用语和模式，第 2 版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 作者：Krzysztof Cwalina 和 Brad Abrams，由 Addison Wesley Professional 于 2008 年 10 月 22 日印发，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="7310a-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7310a-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="7310a-123">See also</span></span>

- [<span data-ttu-id="7310a-124">类型设计准则</span><span class="sxs-lookup"><span data-stu-id="7310a-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="7310a-125">框架设计指南</span><span class="sxs-lookup"><span data-stu-id="7310a-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="7310a-126">在类和结构之间选择</span><span class="sxs-lookup"><span data-stu-id="7310a-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
