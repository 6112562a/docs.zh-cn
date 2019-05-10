---
title: 如何：通过在每个 Windows 窗体各自的线程上显示此 Windows 窗体来支持 COM 互操作
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 56eaf438455754c69b2df3ff798cf6d2ac6f7549
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64636972"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="7ff50-102">如何：通过在每个 Windows 窗体各自的线程上显示此 Windows 窗体来支持 COM 互操作</span><span class="sxs-lookup"><span data-stu-id="7ff50-102">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>
<span data-ttu-id="7ff50-103">可通过在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 消息循环上显示窗体来解决 COM 互操作性问题 ，可使用 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> 方法来创建该消息循环。</span><span class="sxs-lookup"><span data-stu-id="7ff50-103">You can resolve COM interoperability problems by displaying your form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="7ff50-104">若要使 Windows 窗体在 COM 客户端应用程序上正确工作，必须在 Windows 窗体消息循环上运行该窗体。</span><span class="sxs-lookup"><span data-stu-id="7ff50-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="7ff50-105">若要执行此操作，请使用以下方法之一：</span><span class="sxs-lookup"><span data-stu-id="7ff50-105">To do this, use one of the following approaches:</span></span>  
  
- <span data-ttu-id="7ff50-106">使用 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> 方法显示 Windows 窗体。</span><span class="sxs-lookup"><span data-stu-id="7ff50-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="7ff50-107">有关详细信息，请参阅[如何：通过显示 Windows 窗体使用 ShowDialog 方法来支持 COM 互操作](com-interop-by-displaying-a-windows-form-shadow.md)。</span><span class="sxs-lookup"><span data-stu-id="7ff50-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](com-interop-by-displaying-a-windows-form-shadow.md).</span></span>  
  
- <span data-ttu-id="7ff50-108">在单独的线程上显示每个 Windows 窗体。</span><span class="sxs-lookup"><span data-stu-id="7ff50-108">Display each Windows Form on a separate thread.</span></span>  
  
 <span data-ttu-id="7ff50-109">没有对此功能在 Visual Studio 中的广泛支持。</span><span class="sxs-lookup"><span data-stu-id="7ff50-109">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="7ff50-110">另请参阅[演练：通过在其自己的线程上显示每个 Windows 窗体支持 COM 互操作](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="7ff50-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ff50-111">示例</span><span class="sxs-lookup"><span data-stu-id="7ff50-111">Example</span></span>  
 <span data-ttu-id="7ff50-112">下面的代码示例演示如何在单独的线程上显示窗体，并调用 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> 方法来启动该线程上的 Windows 窗体消息泵。</span><span class="sxs-lookup"><span data-stu-id="7ff50-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="7ff50-113">若要使用此方法，必须使用 <xref:System.Windows.Forms.Control.Invoke%2A> 方法，封送任何从非托管应用程序对窗体的调用。</span><span class="sxs-lookup"><span data-stu-id="7ff50-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>  
  
 <span data-ttu-id="7ff50-114">此方法要求窗体上的每个实例通过使用其自身的消息循环在自己的线程上运行。</span><span class="sxs-lookup"><span data-stu-id="7ff50-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="7ff50-115">每个线程上运行的消息循环不能超过一个。</span><span class="sxs-lookup"><span data-stu-id="7ff50-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="7ff50-116">因此，不能更改客户端应用程序的消息循环。</span><span class="sxs-lookup"><span data-stu-id="7ff50-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="7ff50-117">但是，可修改 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 组件以启动使用其自身的消息循环的新线程。</span><span class="sxs-lookup"><span data-stu-id="7ff50-117">However, you can modify the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component to start a new thread that uses its own message loop.</span></span>  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7ff50-118">编译代码</span><span class="sxs-lookup"><span data-stu-id="7ff50-118">Compiling the Code</span></span>  
  
- <span data-ttu-id="7ff50-119">将 `COMForm`、 `Form1`和 `FormManager` 类型编译成名为 `COMWinform.dll`的程序集。</span><span class="sxs-lookup"><span data-stu-id="7ff50-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="7ff50-120">使用 [Packaging an Assembly for COM](../../interop/packaging-an-assembly-for-com.md)中所述的一个方法来注册 COM 互操作的程序集。</span><span class="sxs-lookup"><span data-stu-id="7ff50-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="7ff50-121">现在，你可以在非托管应用程序中使用该程序集以及它对应的的类型库 (.tlb) 文件。</span><span class="sxs-lookup"><span data-stu-id="7ff50-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="7ff50-122">例如，可在 Visual Basic 6.0 可执行项目中将类型库用作引用。</span><span class="sxs-lookup"><span data-stu-id="7ff50-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff50-123">请参阅</span><span class="sxs-lookup"><span data-stu-id="7ff50-123">See also</span></span>

- [<span data-ttu-id="7ff50-124">向 COM 公开 .NET Framework 组件</span><span class="sxs-lookup"><span data-stu-id="7ff50-124">Exposing .NET Framework Components to COM</span></span>](../../interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="7ff50-125">将 COM 的程序集打包</span><span class="sxs-lookup"><span data-stu-id="7ff50-125">Packaging an Assembly for COM</span></span>](../../interop/packaging-an-assembly-for-com.md)
- [<span data-ttu-id="7ff50-126">向 COM 注册程序集</span><span class="sxs-lookup"><span data-stu-id="7ff50-126">Registering Assemblies with COM</span></span>](../../interop/registering-assemblies-with-com.md)
- [<span data-ttu-id="7ff50-127">如何：通过显示 Windows 窗体使用 ShowDialog 方法来支持 COM 互操作</span><span class="sxs-lookup"><span data-stu-id="7ff50-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](com-interop-by-displaying-a-windows-form-shadow.md)
- [<span data-ttu-id="7ff50-128">Windows 窗体和非托管应用程序概述</span><span class="sxs-lookup"><span data-stu-id="7ff50-128">Windows Forms and Unmanaged Applications Overview</span></span>](windows-forms-and-unmanaged-applications-overview.md)
