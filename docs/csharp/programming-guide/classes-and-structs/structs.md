---
title: 结构 - C# 编程指南
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 609169d4624802f679f9661b7aa0596403cc48e7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261612"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="2f7c6-102">结构（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="2f7c6-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="2f7c6-103">通过使用[结构](../../language-reference/keywords/struct.md)关键字来定义结构，例如：</span><span class="sxs-lookup"><span data-stu-id="2f7c6-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
<span data-ttu-id="2f7c6-104">结构与类的大部分语法相同。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="2f7c6-105">结构名称必须是有效的 C# [标识符名称](../inside-a-program/identifier-names.md)。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="2f7c6-106">结构在以下方面比类的限制更多：</span><span class="sxs-lookup"><span data-stu-id="2f7c6-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="2f7c6-107">在结构声明中，除非将字段声明为 const 或 static，否则无法初始化。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="2f7c6-108">结构不能声明默认构造函数（没有参数的构造函数）或终结器。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-108">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="2f7c6-109">结构在分配时进行复制。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-109">Structs are copied on assignment.</span></span> <span data-ttu-id="2f7c6-110">将结构分配给新变量时，将复制所有数据，并且对新副本所做的任何修改不会更改原始副本的数据。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="2f7c6-111">在处理值类型的集合（如 `Dictionary<string, myStruct>`）时，请务必记住这一点。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="2f7c6-112">结构是值类型，不同于类，类是引用类型。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="2f7c6-113">与类不同，无需使用 `new` 运算符即可对结构进行实例化。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="2f7c6-114">结构可以声明具有参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-114">Structs can declare constructors that have parameters.</span></span> 
- <span data-ttu-id="2f7c6-115">一个结构无法继承自另一个结构或类，并且它不能为类的基类。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="2f7c6-116">所有结构都直接继承自 <xref:System.ValueType>，后者继承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="2f7c6-117">结构可以实现接口。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-117">A struct can implement interfaces.</span></span> 
- <span data-ttu-id="2f7c6-118">结构不能为 `null`，并且不能向结构变量分配 `null`，除非将变量声明为可为 null 的类型。</span><span class="sxs-lookup"><span data-stu-id="2f7c6-118">A struct cannot be `null`, and a struct variable cannot be assigned `null` unless the variable is declared as a nullable type.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="2f7c6-119">相关章节</span><span class="sxs-lookup"><span data-stu-id="2f7c6-119">Related sections</span></span>  

<span data-ttu-id="2f7c6-120">更多相关信息：</span><span class="sxs-lookup"><span data-stu-id="2f7c6-120">For more information:</span></span>  
  
- [<span data-ttu-id="2f7c6-121">使用结构</span><span class="sxs-lookup"><span data-stu-id="2f7c6-121">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="2f7c6-122">构造函数</span><span class="sxs-lookup"><span data-stu-id="2f7c6-122">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="2f7c6-123">可以为 null 的类型</span><span class="sxs-lookup"><span data-stu-id="2f7c6-123">Nullable Types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="2f7c6-124">如何：了解向方法传递结构与类引用的区别</span><span class="sxs-lookup"><span data-stu-id="2f7c6-124">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [<span data-ttu-id="2f7c6-125">如何：在结构之间实现用户定义的转换</span><span class="sxs-lookup"><span data-stu-id="2f7c6-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a><span data-ttu-id="2f7c6-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="2f7c6-126">See also</span></span>

- [<span data-ttu-id="2f7c6-127">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="2f7c6-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2f7c6-128">类和结构</span><span class="sxs-lookup"><span data-stu-id="2f7c6-128">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="2f7c6-129">类</span><span class="sxs-lookup"><span data-stu-id="2f7c6-129">Classes</span></span>](classes.md)
- [<span data-ttu-id="2f7c6-130">标识符名称</span><span class="sxs-lookup"><span data-stu-id="2f7c6-130">Identifier names</span></span>](../inside-a-program/identifier-names.md)
