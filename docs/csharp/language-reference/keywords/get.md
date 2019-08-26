---
title: get - C# 参考
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: 783814a575e95fc9deb5c9cdef235a5636f5f529
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602142"
---
# <a name="get-c-reference"></a><span data-ttu-id="2ae17-102">get（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="2ae17-102">get (C# Reference)</span></span>

<span data-ttu-id="2ae17-103">`get` 关键字在属性或索引器中定义访问器  方法，它将返回属性值或索引器元素。</span><span class="sxs-lookup"><span data-stu-id="2ae17-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="2ae17-104">有关详细信息，请参阅[属性](../../programming-guide/classes-and-structs/properties.md)、[自动实现的属性](../../programming-guide/classes-and-structs/auto-implemented-properties.md)和[索引器](../../programming-guide/indexers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2ae17-104">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="2ae17-105">以下示例为名为 `Seconds` 的属性同时定义 `get` 和 `set` 访问器。</span><span class="sxs-lookup"><span data-stu-id="2ae17-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="2ae17-106">它使用名为 `_seconds` 的私有字段备份属性值。</span><span class="sxs-lookup"><span data-stu-id="2ae17-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="2ae17-107">通常，`get` 访问器包含返回一个值的单个语句，如前面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="2ae17-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="2ae17-108">从 C# 7.0 开始，可以将 `get` 访问器作为 expression-bodied 成员实现。</span><span class="sxs-lookup"><span data-stu-id="2ae17-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="2ae17-109">以下示例将 `get` 和 `set` 访问器都作为 expression-bodied 成员实现。</span><span class="sxs-lookup"><span data-stu-id="2ae17-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="2ae17-110">对于属性的 `get` 和 `set` 访问器不执行除设置或检索私有支持字段中的值以外的任何其他操作的简单情况，可以利用 C# 编译器对自动实现的属性的支持。</span><span class="sxs-lookup"><span data-stu-id="2ae17-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="2ae17-111">以下示例将 `Hours` 作为自动实现的属性来实现。</span><span class="sxs-lookup"><span data-stu-id="2ae17-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="2ae17-112">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="2ae17-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2ae17-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="2ae17-113">See also</span></span>

- [<span data-ttu-id="2ae17-114">C# 参考</span><span class="sxs-lookup"><span data-stu-id="2ae17-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2ae17-115">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="2ae17-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2ae17-116">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="2ae17-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="2ae17-117">属性</span><span class="sxs-lookup"><span data-stu-id="2ae17-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
