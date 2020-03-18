---
title: 多维数组 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: eb49f4386b6106328f1613b5ec70794ac26fc9b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715036"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="994dd-102">多维数组（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="994dd-102">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="994dd-103">数组可具有多个维度。</span><span class="sxs-lookup"><span data-stu-id="994dd-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="994dd-104">例如，以下声明创建一个具有四行两列的二维数组。</span><span class="sxs-lookup"><span data-stu-id="994dd-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="994dd-105">以下声明创建一个具有三个维度（4、2 和 3）的数组。</span><span class="sxs-lookup"><span data-stu-id="994dd-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="994dd-106">数组初始化</span><span class="sxs-lookup"><span data-stu-id="994dd-106">Array Initialization</span></span>

 <span data-ttu-id="994dd-107">声明后即可初始化数组，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="994dd-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="994dd-108">还可在不指定秩的情况下初始化数组。</span><span class="sxs-lookup"><span data-stu-id="994dd-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="994dd-109">如果选择在不初始化的情况下声明数组变量，则必须使用 `new` 运算符将数组赋予变量。</span><span class="sxs-lookup"><span data-stu-id="994dd-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="994dd-110">`new` 的用法如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="994dd-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="994dd-111">以下示例将值赋予特定的数组元素。</span><span class="sxs-lookup"><span data-stu-id="994dd-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="994dd-112">同样，以下示例将获取特定数组元素的值并将其赋予变量 `elementValue`。</span><span class="sxs-lookup"><span data-stu-id="994dd-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="994dd-113">以下代码示例将数组元素初始化为默认值（交错数组除外）。</span><span class="sxs-lookup"><span data-stu-id="994dd-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="994dd-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="994dd-114">See also</span></span>

- [<span data-ttu-id="994dd-115">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="994dd-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="994dd-116">数组</span><span class="sxs-lookup"><span data-stu-id="994dd-116">Arrays</span></span>](./index.md)
- [<span data-ttu-id="994dd-117">一维数组</span><span class="sxs-lookup"><span data-stu-id="994dd-117">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="994dd-118">交错数组</span><span class="sxs-lookup"><span data-stu-id="994dd-118">Jagged Arrays</span></span>](./jagged-arrays.md)
