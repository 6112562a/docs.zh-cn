---
title: PrintDocument 组件概述（Windows 窗体）
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 2facbf0a567f81aa6debe2ca60f7f8eabc794bb0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532329"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="19206-102">PrintDocument 组件概述（Windows 窗体）</span><span class="sxs-lookup"><span data-stu-id="19206-102">PrintDocument Component Overview (Windows Forms)</span></span>
<span data-ttu-id="19206-103">Windows 窗体 [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) 组件用于设置属性，这些属性描述在基于 Windows 的应用程序中要打印什么内容以及打印文档的能力。</span><span class="sxs-lookup"><span data-stu-id="19206-103">The Windows Forms [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="19206-104">此组件可与 [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) 组件一起使用，控制文档打印的各个方面。</span><span class="sxs-lookup"><span data-stu-id="19206-104">It can be used in conjunction with the [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>  
  
## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="19206-105">使用 PrintDocument 组件</span><span class="sxs-lookup"><span data-stu-id="19206-105">Working with the PrintDocument Component</span></span>  
 <span data-ttu-id="19206-106">涉及的主要方案的两个<xref:System.Drawing.Printing.PrintDocument>组件是：</span><span class="sxs-lookup"><span data-stu-id="19206-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>  
  
-   <span data-ttu-id="19206-107">简单的打印作业，如打印单个文本文件。</span><span class="sxs-lookup"><span data-stu-id="19206-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="19206-108">在这种情况下将添加<xref:System.Drawing.Printing.PrintDocument>组件向 Windows 窗体，然后添加打印文件的编程逻辑<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="19206-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="19206-109">编程逻辑应以使用<xref:System.Drawing.Printing.PrintDocument.Print%2A>方法打印文档。</span><span class="sxs-lookup"><span data-stu-id="19206-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="19206-110">此方法将发送<xref:System.Drawing.Graphics>中包含的对象<xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A>属性的<xref:System.Drawing.Printing.PrintPageEventArgs>类到打印机。</span><span class="sxs-lookup"><span data-stu-id="19206-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="19206-111">有关演示如何打印文本文档中使用的示例<xref:System.Drawing.Printing.PrintDocument>组件，请参阅[如何：打印 Windows 窗体中的多页文本文件](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="19206-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="19206-112">更复杂的打印作业，如想要重新使用已编写的打印逻辑的情况。</span><span class="sxs-lookup"><span data-stu-id="19206-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="19206-113">在这种情况中将派生中的新组件<xref:System.Drawing.Printing.PrintDocument>组件和重写 (请参阅[重写](~/docs/visual-basic/language-reference/modifiers/overrides.md)适用于 Visual Basic 或[重写](~/docs/csharp/language-reference/keywords/override.md)的C#)<xref:System.Drawing.Printing.PrintDocument.PrintPage>事件。</span><span class="sxs-lookup"><span data-stu-id="19206-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](~/docs/visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](~/docs/csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
 <span data-ttu-id="19206-114">添加到窗体时<xref:System.Drawing.Printing.PrintDocument>组件在 Windows 窗体设计器底部的任务栏中显示。</span><span class="sxs-lookup"><span data-stu-id="19206-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19206-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="19206-115">See also</span></span>
- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="19206-116">Windows 窗体打印支持</span><span class="sxs-lookup"><span data-stu-id="19206-116">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
- [<span data-ttu-id="19206-117">PrintDocument 组件</span><span class="sxs-lookup"><span data-stu-id="19206-117">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)
