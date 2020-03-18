---
title: 如何使用 My 命名空间 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 063b46a32ced859c6c86e40c4a6b9870c3decd24
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700414"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="bdcc2-102">如何使用 My 命名空间（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="bdcc2-102">How to use the My namespace (C# Programming Guide)</span></span>
<span data-ttu-id="bdcc2-103"><xref:Microsoft.VisualBasic.MyServices> 命名空间（在 Visual Basic 中为 `My`）使访问多个 .NET Framework 类变得轻松直观，让你能够编写与计算机、应用程序、设置、资源等交互的代码。</span><span class="sxs-lookup"><span data-stu-id="bdcc2-103">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET Framework classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="bdcc2-104">虽然最初设计用于 Visual Basic，但 `MyServices` 命名空间仍可用于 C# 应用程序。</span><span class="sxs-lookup"><span data-stu-id="bdcc2-104">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="bdcc2-105">有关使用 Visual Basic 的 `MyServices` 命名空间的详细信息，请参阅[使用 My 开发](../../../visual-basic/developing-apps/development-with-my/index.md)。</span><span class="sxs-lookup"><span data-stu-id="bdcc2-105">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="adding-a-reference"></a><span data-ttu-id="bdcc2-106">添加引用</span><span class="sxs-lookup"><span data-stu-id="bdcc2-106">Adding a Reference</span></span>  
 <span data-ttu-id="bdcc2-107">可以在解决方案中使用 `MyServices` 类之前，必须添加对 Visual Basic 库的引用。</span><span class="sxs-lookup"><span data-stu-id="bdcc2-107">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
#### <a name="to-add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="bdcc2-108">添加对 Visual Basic 库的引用</span><span class="sxs-lookup"><span data-stu-id="bdcc2-108">To add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="bdcc2-109">在解决方案资源管理器中，右键单击“引用”节点并选择“添加引用”    。</span><span class="sxs-lookup"><span data-stu-id="bdcc2-109">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="bdcc2-110">出现“引用”对话框时，向下滚动列表，然后选择“Microsoft.VisualBasic.dll”  。</span><span class="sxs-lookup"><span data-stu-id="bdcc2-110">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="bdcc2-111">同时建议将以下行包括在程序开头的 `using` 部分。</span><span class="sxs-lookup"><span data-stu-id="bdcc2-111">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="bdcc2-112">示例</span><span class="sxs-lookup"><span data-stu-id="bdcc2-112">Example</span></span>  
 <span data-ttu-id="bdcc2-113">此示例调用 `MyServices` 命名空间中包含的各种静态方法。</span><span class="sxs-lookup"><span data-stu-id="bdcc2-113">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="bdcc2-114">若要编译此代码，必须向项目添加对 Microsoft.VisualBasic.DLL 的引用。</span><span class="sxs-lookup"><span data-stu-id="bdcc2-114">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="bdcc2-115">并不是 `MyServices` 命名空间中的所有类均可从 C# 应用程序中调用：例如，<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> 类不兼容。</span><span class="sxs-lookup"><span data-stu-id="bdcc2-115">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="bdcc2-116">在此特定情况下，可以改为使用属于 <xref:Microsoft.VisualBasic.FileIO.FileSystem> 的静态方法，这些方法也包含在 VisualBasic.dll 中。</span><span class="sxs-lookup"><span data-stu-id="bdcc2-116">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="bdcc2-117">例如，下面介绍了如何使用此类方法来复制目录：</span><span class="sxs-lookup"><span data-stu-id="bdcc2-117">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="bdcc2-118">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bdcc2-118">See also</span></span>

- [<span data-ttu-id="bdcc2-119">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="bdcc2-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bdcc2-120">命名空间</span><span class="sxs-lookup"><span data-stu-id="bdcc2-120">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="bdcc2-121">使用命名空间</span><span class="sxs-lookup"><span data-stu-id="bdcc2-121">Using Namespaces</span></span>](./using-namespaces.md)
