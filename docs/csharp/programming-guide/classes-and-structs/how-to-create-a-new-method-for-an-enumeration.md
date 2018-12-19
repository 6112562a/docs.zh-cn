---
title: 如何：为枚举创建新方法 - C# 编程指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
ms.openlocfilehash: f8495cd747cf895c4da34c216ba9285182890af1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238724"
---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a><span data-ttu-id="0bb1c-102">如何：为枚举创建新方法（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="0bb1c-102">How to: Create a New Method for an Enumeration (C# Programming Guide)</span></span>
<span data-ttu-id="0bb1c-103">可使用扩展方法添加特定于某个特定枚举类型的功能。</span><span class="sxs-lookup"><span data-stu-id="0bb1c-103">You can use extension methods to add functionality specific to a particular enum type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bb1c-104">示例</span><span class="sxs-lookup"><span data-stu-id="0bb1c-104">Example</span></span>  
 <span data-ttu-id="0bb1c-105">在下面的示例中，`Grades` 枚举表示学生可能在班里收到的字母等级分。</span><span class="sxs-lookup"><span data-stu-id="0bb1c-105">In the following example, the `Grades` enumeration represents the possible letter grades that a student may receive in a class.</span></span> <span data-ttu-id="0bb1c-106">该示例将一个名为 `Passing` 的扩展方法添加到 `Grades` 类型中，以便该类型的每个实例现在都“知道”它是否表示合格的等级分。</span><span class="sxs-lookup"><span data-stu-id="0bb1c-106">An extension method named `Passing` is added to the `Grades` type so that each instance of that type now "knows" whether it represents a passing grade or not.</span></span>  
  
 [!code-csharp[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 <span data-ttu-id="0bb1c-107">请注意，`Extensions` 类还包含一个动态更新的静态变量，并且扩展方法的返回值反映了该变量的当前值。</span><span class="sxs-lookup"><span data-stu-id="0bb1c-107">Note that the `Extensions` class also contains a static variable that is updated dynamically and that the return value of the extension method reflects the current value of that variable.</span></span> <span data-ttu-id="0bb1c-108">这表明在幕后，将在定义扩展方法的静态类上直接调用这些方法。</span><span class="sxs-lookup"><span data-stu-id="0bb1c-108">This demonstrates that, behind the scenes, extension methods are invoked directly on the static class in which they are defined.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0bb1c-109">编译代码</span><span class="sxs-lookup"><span data-stu-id="0bb1c-109">Compiling the Code</span></span>  
 <span data-ttu-id="0bb1c-110">若要运行此代码，请将其复制并粘贴到已在 Visual Studio 中创建的 Visual C# 控制台应用程序项目。</span><span class="sxs-lookup"><span data-stu-id="0bb1c-110">To run this code, copy and paste it into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="0bb1c-111">默认情况下，此项目面向 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 3.5 版，并且具有对 System.Core.dll 的引用和一个用于 System.Linq 的 `using` 指令。</span><span class="sxs-lookup"><span data-stu-id="0bb1c-111">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a `using` directive for System.Linq.</span></span> <span data-ttu-id="0bb1c-112">如果项目中缺少其中一个或多个要求，则可以手动添加它们。</span><span class="sxs-lookup"><span data-stu-id="0bb1c-112">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bb1c-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="0bb1c-113">See Also</span></span>

- [<span data-ttu-id="0bb1c-114">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="0bb1c-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0bb1c-115">扩展方法</span><span class="sxs-lookup"><span data-stu-id="0bb1c-115">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
