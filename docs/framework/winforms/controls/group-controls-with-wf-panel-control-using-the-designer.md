---
title: 如何：通过使用设计器使用 Windows 窗体 Panel 控件对控件进行分组
ms.date: 03/30/2017
helpviewer_keywords:
- Panel control [Windows Forms], grouping controls
- controls [Windows Forms], grouping
- Windows Forms controls, grouping
ms.assetid: 7e1cd708-fdb1-49d8-9ca2-5640b276bf2e
ms.openlocfilehash: 1a3fcac56df1328c12d7a5dcb542138afdb486f5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214827"
---
# <a name="how-to-group-controls-with-the-windows-forms-panel-control-using-the-designer"></a><span data-ttu-id="3ac6f-102">如何：通过使用设计器使用 Windows 窗体 Panel 控件对控件进行分组</span><span class="sxs-lookup"><span data-stu-id="3ac6f-102">How to: Group Controls with the Windows Forms Panel Control Using the Designer</span></span>
<span data-ttu-id="3ac6f-103">Windows 窗体<xref:System.Windows.Forms.Panel>控件用于分组其他控件。</span><span class="sxs-lookup"><span data-stu-id="3ac6f-103">Windows Forms <xref:System.Windows.Forms.Panel> controls are used to group other controls.</span></span> <span data-ttu-id="3ac6f-104">有三个原因与组控件。</span><span class="sxs-lookup"><span data-stu-id="3ac6f-104">There are three reasons to group controls.</span></span> <span data-ttu-id="3ac6f-105">一个是 visual 对于清除用户界面; 相关窗体元素的分组另一种是以编程方式分组的单选按钮，例如;最后一个是用于在设计时作为一个单元移动控件。</span><span class="sxs-lookup"><span data-stu-id="3ac6f-105">One is visual grouping of related form elements for a clear user interface; another is programmatic grouping, of radio buttons for example; the last is for moving the controls as a unit at design time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ac6f-106">显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。</span><span class="sxs-lookup"><span data-stu-id="3ac6f-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3ac6f-107">若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。</span><span class="sxs-lookup"><span data-stu-id="3ac6f-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3ac6f-108">有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="3ac6f-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-create-a-group-of-controls"></a><span data-ttu-id="3ac6f-109">若要创建的一组控件</span><span class="sxs-lookup"><span data-stu-id="3ac6f-109">To create a group of controls</span></span>  
  
1.  <span data-ttu-id="3ac6f-110">拖动<xref:System.Windows.Forms.Panel>控件从**Windows 窗体**拖到窗体工具箱选项卡中的。</span><span class="sxs-lookup"><span data-stu-id="3ac6f-110">Drag a <xref:System.Windows.Forms.Panel> control from the **Windows Forms** tab of the Toolbox onto a form.</span></span>  
  
2.  <span data-ttu-id="3ac6f-111">将其他控件添加到每个面板内绘制的面板。</span><span class="sxs-lookup"><span data-stu-id="3ac6f-111">Add other controls to the panel, drawing each inside the panel.</span></span>  
  
     <span data-ttu-id="3ac6f-112">如果你想要将括在面板中的现有控件，可以选择所有控件，将它们剪切到剪贴板，再都选择<xref:System.Windows.Forms.Panel>控件，然后再将其粘贴到面板。</span><span class="sxs-lookup"><span data-stu-id="3ac6f-112">If you have existing controls that you want to enclose in a panel, you can select all the controls, cut them to the Clipboard, select the <xref:System.Windows.Forms.Panel> control, and then paste them into the panel.</span></span> <span data-ttu-id="3ac6f-113">您还可以将它们拖到面板。</span><span class="sxs-lookup"><span data-stu-id="3ac6f-113">You can also drag them into the panel.</span></span>  
  
3.  <span data-ttu-id="3ac6f-114">（可选）如果你想要将边框添加到面板，设置其<xref:System.Windows.Forms.BorderStyle>属性。</span><span class="sxs-lookup"><span data-stu-id="3ac6f-114">(Optional) If you want to add a border to a panel, set its <xref:System.Windows.Forms.BorderStyle> property.</span></span> <span data-ttu-id="3ac6f-115">有三种选择： <xref:System.Windows.Forms.BorderStyle.Fixed3D>， <xref:System.Windows.Forms.BorderStyle.FixedSingle>，和<xref:System.Windows.Forms.BorderStyle.None>。</span><span class="sxs-lookup"><span data-stu-id="3ac6f-115">There are three choices: <xref:System.Windows.Forms.BorderStyle.Fixed3D>, <xref:System.Windows.Forms.BorderStyle.FixedSingle>, and <xref:System.Windows.Forms.BorderStyle.None>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ac6f-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="3ac6f-116">See also</span></span>

- [<span data-ttu-id="3ac6f-117">Panel 控件</span><span class="sxs-lookup"><span data-stu-id="3ac6f-117">Panel Control</span></span>](panel-control-windows-forms.md)
- [<span data-ttu-id="3ac6f-118">Panel 控件概述</span><span class="sxs-lookup"><span data-stu-id="3ac6f-118">Panel Control Overview</span></span>](panel-control-overview-windows-forms.md)
- [<span data-ttu-id="3ac6f-119">如何：设置 Panel 控件的背景</span><span class="sxs-lookup"><span data-stu-id="3ac6f-119">How to: Set the Background of a Panel</span></span>](how-to-set-the-background-of-a-windows-forms-panel.md)
