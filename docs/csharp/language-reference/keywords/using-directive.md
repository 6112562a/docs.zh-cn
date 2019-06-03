---
title: using 指令 - C# 参考
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: 072af9850f792cb6d7322724f2adbc978465dc84
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421744"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="2a2d0-102">using 指令（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="2a2d0-102">using directive (C# Reference)</span></span>

<span data-ttu-id="2a2d0-103">`using` 指令有三种用途：</span><span class="sxs-lookup"><span data-stu-id="2a2d0-103">The `using` directive has three uses:</span></span>

- <span data-ttu-id="2a2d0-104">允许在命名空间中使用类型，这样无需在该命名空间中限定某个类型的使用：</span><span class="sxs-lookup"><span data-stu-id="2a2d0-104">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="2a2d0-105">允许访问类型的静态成员和嵌套类型，而无需限定使用类型名称进行访问。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-105">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="2a2d0-106">有关详细信息，请参阅 [using static 指令](using-static.md)。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-106">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="2a2d0-107">为命名空间或类型创建别名。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-107">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="2a2d0-108">这称为 *using 别名指令*。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-108">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="2a2d0-109">`using` 关键字还用于创建 using 语句，此类语句有助于确保正确处理 <xref:System.IDisposable> 对象（如文件和字体）  。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-109">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="2a2d0-110">有关详细信息，请参阅 [using 语句](using-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-110">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="2a2d0-111">Using 静态类型</span><span class="sxs-lookup"><span data-stu-id="2a2d0-111">Using static type</span></span>

<span data-ttu-id="2a2d0-112">你可以访问类型的静态成员，而无需限定使用类型名称进行访问：</span><span class="sxs-lookup"><span data-stu-id="2a2d0-112">You can access static members of a type without having to qualify the access with the type name:</span></span>

```csharp
using static System.Console;
using static System.Math;
class Program
{
    static void Main()
    {
        WriteLine(Sqrt(3*3 + 4*4));
    }
}
```

## <a name="remarks"></a><span data-ttu-id="2a2d0-113">备注</span><span class="sxs-lookup"><span data-stu-id="2a2d0-113">Remarks</span></span>

<span data-ttu-id="2a2d0-114">`using` 指令的范围限于显示它的文件。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-114">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="2a2d0-115">可能出现 `using` 指令的位置：</span><span class="sxs-lookup"><span data-stu-id="2a2d0-115">The `using` directive can appear:</span></span>

- <span data-ttu-id="2a2d0-116">源代码文件的开头，位于任何命名空间或类型定义之前。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-116">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="2a2d0-117">在任何命名空间中，但位于此命名空间中声明的任何命名空间或类型之前。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-117">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="2a2d0-118">否则，将生成编译器错误 [CS1529](../../misc/cs1529.md)。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-118">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="2a2d0-119">创建 `using` 别名指令，以便更易于将标识符限定为命名空间或类型。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-119">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="2a2d0-120">在任何 `using` 指令中，都必须使用完全限定的命名空间或类型，而无需考虑它之前的 `using` 指令。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-120">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="2a2d0-121">`using` 指令的声明中不能使用 `using` 别名。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-121">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="2a2d0-122">例如，以下代码生成一个编译器错误：</span><span class="sxs-lookup"><span data-stu-id="2a2d0-122">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions;
```

<span data-ttu-id="2a2d0-123">创建 `using` 指令，以便在命名空间中使用类型而不必指定命名空间。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-123">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="2a2d0-124">`using` 指令不为你提供对嵌套在指定命名空间中的任何命名空间的访问权限。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-124">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="2a2d0-125">命名空间分为两类：用户定义的命名空间和系统定义的命名空间。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-125">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="2a2d0-126">用户定义的命名空间是在代码中定义的命名空间。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-126">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="2a2d0-127">有关系统定义的命名空间的列表，请参阅 [.NET API 浏览器](../../../../api/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-127">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

<span data-ttu-id="2a2d0-128">有关在其他程序集中引用方法的示例，请参阅[使用命令行创建和使用程序集](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-128">For examples on referencing methods in other assemblies, see [Create and Use Assemblies Using the Command Line](../../programming-guide/concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="2a2d0-129">示例 1</span><span class="sxs-lookup"><span data-stu-id="2a2d0-129">Example 1</span></span>

<span data-ttu-id="2a2d0-130">下面的示例显示如何为命名空间定义和使用 `using` 别名：</span><span class="sxs-lookup"><span data-stu-id="2a2d0-130">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="2a2d0-131">using 别名指令的右侧不能有开放式泛型类型。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-131">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="2a2d0-132">例如，不能为 `List<T>` 创建 using 别名，但可以为 `List<int>` 创建 using 别名。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-132">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="2a2d0-133">示例 2</span><span class="sxs-lookup"><span data-stu-id="2a2d0-133">Example 2</span></span>

<span data-ttu-id="2a2d0-134">下面的示例显示如何为类定义 `using` 指令和 `using` 别名：</span><span class="sxs-lookup"><span data-stu-id="2a2d0-134">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="2a2d0-135">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="2a2d0-135">C# language specification</span></span>

<span data-ttu-id="2a2d0-136">有关详细信息，请参阅 [C# 语言规范](../language-specification/index.md)中的[ Using 指令](~/_csharplang/spec/namespaces.md#using-directives)。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-136">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="2a2d0-137">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="2a2d0-137">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a2d0-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="2a2d0-138">See also</span></span>

- [<span data-ttu-id="2a2d0-139">C# 参考</span><span class="sxs-lookup"><span data-stu-id="2a2d0-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2a2d0-140">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="2a2d0-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2a2d0-141">使用命名空间</span><span class="sxs-lookup"><span data-stu-id="2a2d0-141">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="2a2d0-142">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="2a2d0-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2a2d0-143">命名空间</span><span class="sxs-lookup"><span data-stu-id="2a2d0-143">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="2a2d0-144">using 语句</span><span class="sxs-lookup"><span data-stu-id="2a2d0-144">using Statement</span></span>](using-statement.md)
