---
title: 设计本地化友好布局
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
ms.openlocfilehash: 9556c03699713b7d14f81a6eacc8e4ab337e869b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628626"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a><span data-ttu-id="a23eb-102">如何：设计适合本地化的 Windows 窗体布局</span><span class="sxs-lookup"><span data-stu-id="a23eb-102">How to: Design a Windows Forms Layout that Responds Well to Localization</span></span>
<span data-ttu-id="a23eb-103">创建可供进行本地化的窗体极大地加速了国际市场的开发。</span><span class="sxs-lookup"><span data-stu-id="a23eb-103">Creating forms that are ready to be localized greatly speeds development for international markets.</span></span> <span data-ttu-id="a23eb-104">可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控件实现在控件因 <xref:System.Windows.Forms.Control.Text%2A> 属性值更改而调整大小时正常响应的布局。</span><span class="sxs-lookup"><span data-stu-id="a23eb-104">You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.</span></span>

## <a name="example"></a><span data-ttu-id="a23eb-105">示例</span><span class="sxs-lookup"><span data-stu-id="a23eb-105">Example</span></span>
 <span data-ttu-id="a23eb-106">此窗体演示如何创建在将显示的字符串值翻译成其它语言时按比例进行调整的布局。</span><span class="sxs-lookup"><span data-stu-id="a23eb-106">This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages.</span></span> <span data-ttu-id="a23eb-107">这一翻译过程称为*本地化*。</span><span class="sxs-lookup"><span data-stu-id="a23eb-107">This process of translation is called *localization*.</span></span> <span data-ttu-id="a23eb-108">有关详细信息，请参阅[本地化](../../../standard/globalization-localization/localization.md)。</span><span class="sxs-lookup"><span data-stu-id="a23eb-108">For more information, see [Localization](../../../standard/globalization-localization/localization.md).</span></span>

 <span data-ttu-id="a23eb-109">Visual Studio 中对此任务提供广泛支持。</span><span class="sxs-lookup"><span data-stu-id="a23eb-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="a23eb-110">另请参阅[演练：创建可根据本地化需要调整比例的布局](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="a23eb-110">See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).</span></span>

 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]

## <a name="additional-resources"></a><span data-ttu-id="a23eb-111">其他资源</span><span class="sxs-lookup"><span data-stu-id="a23eb-111">Additional resources</span></span>

1. [<span data-ttu-id="a23eb-112">如何：在 TableLayoutPanel 控件中对齐和拉伸控件</span><span class="sxs-lookup"><span data-stu-id="a23eb-112">How to: Align and Stretch a Control in a TableLayoutPanel Control</span></span>](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)

2. [<span data-ttu-id="a23eb-113">演练：使用 FlowLayoutPanel 在 Windows 窗体上排列控件</span><span class="sxs-lookup"><span data-stu-id="a23eb-113">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)

3. [<span data-ttu-id="a23eb-114">如何：在 TableLayoutPanel 控件中跨行和跨列</span><span class="sxs-lookup"><span data-stu-id="a23eb-114">How to: Span Rows and Columns in a TableLayoutPanel Control</span></span>](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)

4. [<span data-ttu-id="a23eb-115">如何：在 TableLayoutPanel 控件中编辑行和列</span><span class="sxs-lookup"><span data-stu-id="a23eb-115">How to: Edit Columns and Rows in a TableLayoutPanel Control</span></span>](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)

5. [<span data-ttu-id="a23eb-116">演练：使用设计器操作执行常见任务</span><span class="sxs-lookup"><span data-stu-id="a23eb-116">Walkthrough: Perform common tasks using designer actions</span></span>](perform-common-tasks-design-actions.md)

6. [<span data-ttu-id="a23eb-117">演练：使用 TableLayoutPanel 在 Windows 窗体上排列控件</span><span class="sxs-lookup"><span data-stu-id="a23eb-117">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)

7. [<span data-ttu-id="a23eb-118">演练：使用 Padding、Margins 和 AutoSize 属性对 Windows 窗体控件进行布局</span><span class="sxs-lookup"><span data-stu-id="a23eb-118">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)

8. <span data-ttu-id="a23eb-119">[如何：使用 AutoSize 属性和 TableLayoutPanel 控件支持对 Windows 窗体的本地化](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a23eb-119">[How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))</span></span>

9. <span data-ttu-id="a23eb-120">[演练：创建可根据数据输入需要调整大小的 Windows 窗体](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a23eb-120">[Walkthrough: Creating a Resizable Windows Form for Data Entry](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="a23eb-121">编译代码</span><span class="sxs-lookup"><span data-stu-id="a23eb-121">Compiling the Code</span></span>
 <span data-ttu-id="a23eb-122">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="a23eb-122">This example requires:</span></span>

- <span data-ttu-id="a23eb-123">对 System、System.Data、System.Drawing 和 System.Windows.Forms 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="a23eb-123">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="a23eb-124">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a23eb-124">See also</span></span>

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="a23eb-125">本地化</span><span class="sxs-lookup"><span data-stu-id="a23eb-125">Localization</span></span>](../../../standard/globalization-localization/localization.md)
