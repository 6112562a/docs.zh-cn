---
title: 纯功能转换简介 (C#)
ms.date: 07/20/2015
ms.assetid: 8495c9d9-2d02-4aa0-8a10-9e8794b985fe
ms.openlocfilehash: 34e2fdfae7c0243ca6f59354c453396648c3fa85
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592103"
---
# <a name="introduction-to-pure-functional-transformations-c"></a><span data-ttu-id="42f8a-102">纯功能转换简介 (C#)</span><span class="sxs-lookup"><span data-stu-id="42f8a-102">Introduction to Pure Functional Transformations (C#)</span></span>
<span data-ttu-id="42f8a-103">本节介绍函数转换，包括基本概念和支持的语言构造。</span><span class="sxs-lookup"><span data-stu-id="42f8a-103">This section introduces functional transformations, including the underlying concepts and supporting language constructs.</span></span> <span data-ttu-id="42f8a-104">本节对面向对象的编程方法与函数转换编程方法进行了对比，并针对如何转换到后者提供了一些建议。</span><span class="sxs-lookup"><span data-stu-id="42f8a-104">It contrasts the object-oriented and functional transformation approaches to programming, including advice on how to transition to the latter.</span></span> <span data-ttu-id="42f8a-105">尽管可以在很多编程方案中都使用函数转换，但此处使用 XML 转换作为具体示例。</span><span class="sxs-lookup"><span data-stu-id="42f8a-105">Although functional transformations can be used in many programming scenarios, XML transformation is used here as a concrete example.</span></span>  
  
 <span data-ttu-id="42f8a-106">[教程：：操作 WordprocessingML 文档中的内容 (C#)](./shape-of-wordprocessingml-documents.md) 教程提供一系列示例，每个示例都是在前一个示例的基础上生成的。</span><span class="sxs-lookup"><span data-stu-id="42f8a-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](./shape-of-wordprocessingml-documents.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="42f8a-107">这些示例演示用于操作 XML 的纯函数转换方法。</span><span class="sxs-lookup"><span data-stu-id="42f8a-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span> <span data-ttu-id="42f8a-108">本教程假定你了解 C# 的使用知识。</span><span class="sxs-lookup"><span data-stu-id="42f8a-108">This tutorial assumes a working knowledge of C#.</span></span> <span data-ttu-id="42f8a-109">本教程不提供语言构造的详细语义，但提供到相应语言文档的链接。</span><span class="sxs-lookup"><span data-stu-id="42f8a-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="42f8a-110">还假定您已了解基本计算机科学概念和 XML（包括 XML 命名空间）的使用知识。</span><span class="sxs-lookup"><span data-stu-id="42f8a-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42f8a-111">本节内容</span><span class="sxs-lookup"><span data-stu-id="42f8a-111">In This Section</span></span>  
  
|<span data-ttu-id="42f8a-112">主题</span><span class="sxs-lookup"><span data-stu-id="42f8a-112">Topic</span></span>|<span data-ttu-id="42f8a-113">说明</span><span class="sxs-lookup"><span data-stu-id="42f8a-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="42f8a-114">概念和术语（功能转换）(C#)</span><span class="sxs-lookup"><span data-stu-id="42f8a-114">Concepts and Terminology (Functional Transformation) (C#)</span></span>](./concepts-and-terminology-functional-transformation.md)|<span data-ttu-id="42f8a-115">介绍纯函数转换的概念和术语。</span><span class="sxs-lookup"><span data-stu-id="42f8a-115">Introduces the concepts and terminology of pure functional transformations.</span></span>|  
|[<span data-ttu-id="42f8a-116">函数编程与命令式编程 (C#)</span><span class="sxs-lookup"><span data-stu-id="42f8a-116">Functional Programming vs. Imperative Programming (C#)</span></span>](./functional-programming-vs-imperative-programming.md)|<span data-ttu-id="42f8a-117">将函数编程与更传统的命令性（过程）编程进行对比。</span><span class="sxs-lookup"><span data-stu-id="42f8a-117">Compares and contrasts functional programming to more traditional imperative (procedural) programming.</span></span>|  
|[<span data-ttu-id="42f8a-118">重构为纯函数 (C#)</span><span class="sxs-lookup"><span data-stu-id="42f8a-118">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)|<span data-ttu-id="42f8a-119">介绍纯函数，并提供了纯函数和非纯函数的示例。</span><span class="sxs-lookup"><span data-stu-id="42f8a-119">Introduces pure functions, and shows examples of and pure and impure functions.</span></span>|  
|[<span data-ttu-id="42f8a-120">功能转换的适用性 (C#)</span><span class="sxs-lookup"><span data-stu-id="42f8a-120">Applicability of Functional Transformation (C#)</span></span>](./applicability-of-functional-transformation.md)|<span data-ttu-id="42f8a-121">描述函数转换的典型应用场景。</span><span class="sxs-lookup"><span data-stu-id="42f8a-121">Describes typical scenarios for functional transformations.</span></span>|  
|[<span data-ttu-id="42f8a-122">XML 的功能转换 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42f8a-122">Functional Transformation of XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-transformation-of-xml.md)|<span data-ttu-id="42f8a-123">描述在转换 XML 树的上下文中的函数转换。</span><span class="sxs-lookup"><span data-stu-id="42f8a-123">Describes functional transformations in the context of transforming XML trees.</span></span>|  
  