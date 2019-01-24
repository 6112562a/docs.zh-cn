---
title: 如何：浏览数据集使用 Windows 窗体 BindingNavigator 控件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: 62cc5598aae646c11c0e46276e2e3dca97edc335
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717813"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="1d34f-102">如何：浏览数据集使用 Windows 窗体 BindingNavigator 控件</span><span class="sxs-lookup"><span data-stu-id="1d34f-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="1d34f-103">生成数据驱动的应用程序时，经常需要向用户显示数据集合。</span><span class="sxs-lookup"><span data-stu-id="1d34f-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="1d34f-104"><xref:System.Windows.Forms.BindingNavigator> 控件与 <xref:System.Windows.Forms.BindingSource> 组件一起为滚动集合并按顺序显示其中的项提供方便的可扩展解决方案。</span><span class="sxs-lookup"><span data-stu-id="1d34f-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d34f-105">示例</span><span class="sxs-lookup"><span data-stu-id="1d34f-105">Example</span></span>  
 <span data-ttu-id="1d34f-106">下面的代码示例演示如何使用 <xref:System.Windows.Forms.BindingNavigator> 控件来浏览数据。</span><span class="sxs-lookup"><span data-stu-id="1d34f-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="1d34f-107">集合包含在 <xref:System.Data.DataView> 中，后者使用 <xref:System.Windows.Forms.BindingSource> 组件绑定到 <xref:System.Windows.Forms.TextBox> 控件。</span><span class="sxs-lookup"><span data-stu-id="1d34f-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d34f-108">将敏感信息（如密码）存储在连接字符串中可能会影响应用程序的安全性。</span><span class="sxs-lookup"><span data-stu-id="1d34f-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="1d34f-109">若要控制对数据库的访问，一种较为安全的方法是使用 Windows 身份验证（也称为集成安全性）。</span><span class="sxs-lookup"><span data-stu-id="1d34f-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="1d34f-110">有关详细信息，请参阅[保护连接信息](../../../../docs/framework/data/adonet/protecting-connection-information.md)。</span><span class="sxs-lookup"><span data-stu-id="1d34f-110">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1d34f-111">编译代码</span><span class="sxs-lookup"><span data-stu-id="1d34f-111">Compiling the Code</span></span>  
 <span data-ttu-id="1d34f-112">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="1d34f-112">This example requires:</span></span>  
  
-   <span data-ttu-id="1d34f-113">对 System、System.Data、System.Drawing、System.Windows.Forms 和 System.Xml 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="1d34f-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="1d34f-114">Visual Basic 或 Visual C# 生成命令行中的此示例的信息，请参阅[从命令行生成](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[命令行上使用 csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="1d34f-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1d34f-115">也可以通过将代码粘贴到新的项目中生成此示例在 Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="1d34f-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="1d34f-116">另请参阅[如何：编译和运行完整的 Windows 窗体代码示例使用 Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="1d34f-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d34f-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="1d34f-117">See also</span></span>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="1d34f-118">BindingNavigator 控件</span><span class="sxs-lookup"><span data-stu-id="1d34f-118">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="1d34f-119">BindingSource 组件</span><span class="sxs-lookup"><span data-stu-id="1d34f-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [<span data-ttu-id="1d34f-120">如何：将 Windows 窗体控件绑定到类型</span><span class="sxs-lookup"><span data-stu-id="1d34f-120">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
