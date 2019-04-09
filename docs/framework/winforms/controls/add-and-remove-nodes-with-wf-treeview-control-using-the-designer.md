---
title: 如何：通过使用设计器添加和删除 Windows 窗体 TreeView 控件中的节点
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: cfac0d02ec1effdd521ca68ae4cb44b5a5a7a597
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124847"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="42e8f-102">如何：通过使用设计器添加和删除 Windows 窗体 TreeView 控件中的节点</span><span class="sxs-lookup"><span data-stu-id="42e8f-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>
<span data-ttu-id="42e8f-103">因为 Windows 窗体<xref:System.Windows.Forms.TreeView>控件以分层方式，添加您必须特别注意到其父节点是节点时将显示节点。</span><span class="sxs-lookup"><span data-stu-id="42e8f-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>  
  
 <span data-ttu-id="42e8f-104">下面的过程需要**Windows 应用程序**包含一个窗体，其中包含项目<xref:System.Windows.Forms.TreeView>控件。</span><span class="sxs-lookup"><span data-stu-id="42e8f-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="42e8f-105">有关设置此类项目的信息，请参阅[如何：创建 Windows 窗体应用程序项目](/visualstudio/ide/step-1-create-a-windows-forms-application-project)和[如何：将控件添加到 Windows 窗体](how-to-add-controls-to-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="42e8f-105">For information about setting up such a project, see [How to: Create a Windows Forms application project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) and [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42e8f-106">显示的对话框和菜单命令可能会与“帮助”中的描述不同，具体取决于你现用的设置或版本。</span><span class="sxs-lookup"><span data-stu-id="42e8f-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="42e8f-107">若要更改设置，请在 **“工具”** 菜单上选择 **“导入和导出设置”** 。</span><span class="sxs-lookup"><span data-stu-id="42e8f-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="42e8f-108">有关详细信息，请参阅[个性化设置 Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide)。</span><span class="sxs-lookup"><span data-stu-id="42e8f-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="42e8f-109">若要添加或删除在设计器中的节点</span><span class="sxs-lookup"><span data-stu-id="42e8f-109">To add or remove nodes in the designer</span></span>  
  
1.  <span data-ttu-id="42e8f-110">选择 <xref:System.Windows.Forms.TreeView> 控件。</span><span class="sxs-lookup"><span data-stu-id="42e8f-110">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
2.  <span data-ttu-id="42e8f-111">在中**属性**窗口中，单击**省略号**(![VisualStudioEllipsesButton 屏幕快照](../media/vbellipsesbutton.png "vbEllipsesButton")) 按钮旁边<xref:System.Windows.Forms.TreeView.Nodes%2A>属性。</span><span class="sxs-lookup"><span data-stu-id="42e8f-111">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
     <span data-ttu-id="42e8f-112">**树节点编辑器**出现。</span><span class="sxs-lookup"><span data-stu-id="42e8f-112">The **TreeNode Editor** appears.</span></span>  
  
3.  <span data-ttu-id="42e8f-113">若要将节点添加，必须存在的根节点;如果不存在，首先必须通过单击添加根**添加根**按钮。</span><span class="sxs-lookup"><span data-stu-id="42e8f-113">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="42e8f-114">然后可以通过选择根节点或任何其他节点并单击添加子节点**添加子项**按钮。</span><span class="sxs-lookup"><span data-stu-id="42e8f-114">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>  
  
4.  <span data-ttu-id="42e8f-115">若要删除节点，请选择节点以删除，然后单击**删除**按钮。</span><span class="sxs-lookup"><span data-stu-id="42e8f-115">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42e8f-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="42e8f-116">See also</span></span>

- [<span data-ttu-id="42e8f-117">TreeView 控件</span><span class="sxs-lookup"><span data-stu-id="42e8f-117">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="42e8f-118">TreeView 控件概述</span><span class="sxs-lookup"><span data-stu-id="42e8f-118">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="42e8f-119">如何：设置 Windows 窗体 TreeView 控件的图标</span><span class="sxs-lookup"><span data-stu-id="42e8f-119">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="42e8f-120">如何：循环访问 Windows 窗体 TreeView 控件的所有节点</span><span class="sxs-lookup"><span data-stu-id="42e8f-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="42e8f-121">如何：确定被单击的 TreeView 节点</span><span class="sxs-lookup"><span data-stu-id="42e8f-121">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="42e8f-122">如何：向 TreeView 或 ListView 控件添加自定义信息（Windows 窗体）</span><span class="sxs-lookup"><span data-stu-id="42e8f-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
