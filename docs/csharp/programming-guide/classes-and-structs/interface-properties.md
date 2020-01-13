---
title: 接口属性 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: ff892a35f4be6600c00bc0c72c2f789ef6eb4408
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705530"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="dc64c-102">接口属性（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="dc64c-102">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="dc64c-103">可以在[接口](../../language-reference/keywords/interface.md)上声明属性。</span><span class="sxs-lookup"><span data-stu-id="dc64c-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="dc64c-104">下面是接口属性访问器的示例：</span><span class="sxs-lookup"><span data-stu-id="dc64c-104">The following is an example of an interface property accessor:</span></span>

[!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]

<span data-ttu-id="dc64c-105">接口属性的访问器没有正文。</span><span class="sxs-lookup"><span data-stu-id="dc64c-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="dc64c-106">因此，访问器的用途是指示属性为读写、只读还是只写。</span><span class="sxs-lookup"><span data-stu-id="dc64c-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>

## <a name="example"></a><span data-ttu-id="dc64c-107">示例</span><span class="sxs-lookup"><span data-stu-id="dc64c-107">Example</span></span>

<span data-ttu-id="dc64c-108">在此示例中，接口 `IEmployee` 具有读写属性 `Name` 和只读属性 `Counter`。</span><span class="sxs-lookup"><span data-stu-id="dc64c-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="dc64c-109">类 `Employee` 实现 `IEmployee` 接口，并使用这两个属性。</span><span class="sxs-lookup"><span data-stu-id="dc64c-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="dc64c-110">程序读取新员工的姓名以及当前员工数，并显示员工名称和计算的员工数。</span><span class="sxs-lookup"><span data-stu-id="dc64c-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="dc64c-111">可以使用属性的完全限定名称，它引用其中声明成员的接口。</span><span class="sxs-lookup"><span data-stu-id="dc64c-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="dc64c-112">例如：</span><span class="sxs-lookup"><span data-stu-id="dc64c-112">For example:</span></span>

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

<span data-ttu-id="dc64c-113">这称为[显式接口实现](../interfaces/explicit-interface-implementation.md)。</span><span class="sxs-lookup"><span data-stu-id="dc64c-113">This is called [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="dc64c-114">例如，如果 `Employee` 类正在实现接口 `ICitizen` 和接口 `IEmployee`，而这两个接口都具有 `Name` 属性，则需要用到显式接口成员实现。</span><span class="sxs-lookup"><span data-stu-id="dc64c-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="dc64c-115">即是说下列属性声明：</span><span class="sxs-lookup"><span data-stu-id="dc64c-115">That is, the following property declaration:</span></span>

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

<span data-ttu-id="dc64c-116">在 `IEmployee` 接口中实现 `Name` 属性，而以下声明：</span><span class="sxs-lookup"><span data-stu-id="dc64c-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]

<span data-ttu-id="dc64c-117">在 `ICitizen` 接口中实现 `Name` 属性。</span><span class="sxs-lookup"><span data-stu-id="dc64c-117">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="dc64c-118">示例输出</span><span class="sxs-lookup"><span data-stu-id="dc64c-118">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="dc64c-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="dc64c-119">See also</span></span>

- [<span data-ttu-id="dc64c-120">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="dc64c-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dc64c-121">属性</span><span class="sxs-lookup"><span data-stu-id="dc64c-121">Properties</span></span>](./properties.md)
- [<span data-ttu-id="dc64c-122">使用属性</span><span class="sxs-lookup"><span data-stu-id="dc64c-122">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="dc64c-123">属性与索引器之间的比较</span><span class="sxs-lookup"><span data-stu-id="dc64c-123">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="dc64c-124">索引器</span><span class="sxs-lookup"><span data-stu-id="dc64c-124">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="dc64c-125">接口</span><span class="sxs-lookup"><span data-stu-id="dc64c-125">Interfaces</span></span>](../interfaces/index.md)
