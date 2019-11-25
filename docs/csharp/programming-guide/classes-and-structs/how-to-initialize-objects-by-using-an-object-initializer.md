---
title: 如何使用对象初始值设定项初始化对象 - C# 编程指南
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: be555688a645c7689e76b5b4499c44255c18dbc8
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970879"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="662c8-102">如何使用对象初始值设定项初始化对象（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="662c8-102">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="662c8-103">可以使用对象初始值设定项以声明方式初始化类型对象，而无需显式调用类型的构造函数。</span><span class="sxs-lookup"><span data-stu-id="662c8-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="662c8-104">以下示例演示如何将对象初始值设定项用于命名对象。</span><span class="sxs-lookup"><span data-stu-id="662c8-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="662c8-105">编译器通过首先访问默认实例构造函数，然后处理成员初始化来处理对象初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="662c8-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="662c8-106">因此，如果无参数构造函数在类中声明为 `private`，则需要公共访问的对象初始值设定项将失败。</span><span class="sxs-lookup"><span data-stu-id="662c8-106">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="662c8-107">如果要定义匿名类型，则必须使用对象初始值设定项。</span><span class="sxs-lookup"><span data-stu-id="662c8-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="662c8-108">有关详细信息，请参阅[如何在查询中返回元素属性的子集](how-to-return-subsets-of-element-properties-in-a-query.md)。</span><span class="sxs-lookup"><span data-stu-id="662c8-108">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="662c8-109">示例</span><span class="sxs-lookup"><span data-stu-id="662c8-109">Example</span></span>  

<span data-ttu-id="662c8-110">下面的示例演示如何使用对象初始值设定项初始化新的 `StudentName` 类型。</span><span class="sxs-lookup"><span data-stu-id="662c8-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="662c8-111">此示例在 `StudentName` 类型中设置属性：</span><span class="sxs-lookup"><span data-stu-id="662c8-111">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="662c8-112">对象初始值设定项可用于在对象中设置索引器。</span><span class="sxs-lookup"><span data-stu-id="662c8-112">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="662c8-113">下面的示例定义了一个 `BaseballTeam` 类，该类使用索引器获取和设置不同位置的球员。</span><span class="sxs-lookup"><span data-stu-id="662c8-113">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="662c8-114">初始值设定项可以根据位置的缩写或每个位置的棒球记分卡的编号来分配球员：</span><span class="sxs-lookup"><span data-stu-id="662c8-114">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="662c8-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="662c8-115">See also</span></span>

- [<span data-ttu-id="662c8-116">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="662c8-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="662c8-117">对象和集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="662c8-117">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
