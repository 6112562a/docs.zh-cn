---
title: 如何：从 MDI 下拉菜单 （Windows 窗体） 中删除 ToolStripMenuItem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: 7c84d260783e3a511b5ef6a651c71f1ee55acffe
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295336"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a><span data-ttu-id="1e039-102">如何：从 MDI 下拉菜单 （Windows 窗体） 中删除 ToolStripMenuItem</span><span class="sxs-lookup"><span data-stu-id="1e039-102">How to: Remove a ToolStripMenuItem from an MDI Drop-Down Menu (Windows Forms)</span></span>
<span data-ttu-id="1e039-103">在某些应用程序中，多文档界面 (MDI) 子窗口的类型可以不同于 MDI 父窗口。</span><span class="sxs-lookup"><span data-stu-id="1e039-103">In some applications, the kind of a multiple-document interface (MDI) child window can be different from the MDI parent window.</span></span> <span data-ttu-id="1e039-104">例如，MDI 父窗口可能为电子表格，而 MDI 子窗口可能为图表。</span><span class="sxs-lookup"><span data-stu-id="1e039-104">For example, the MDI parent might be a spreadsheet, and the MDI child might be a chart.</span></span> <span data-ttu-id="1e039-105">在这种情况下，由于激活了不同类型的 MDI 子窗口，你想用 MDI 子菜单上的内容更新 MDI 父菜单的内容。</span><span class="sxs-lookup"><span data-stu-id="1e039-105">In that case, you want to update the contents of the MDI parent's menu with the contents of the MDI child's menu as MDI child windows of different kinds are activated.</span></span>  
  
 <span data-ttu-id="1e039-106">以下过程使用<xref:System.Windows.Forms.Form.IsMdiContainer%2A>， <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>， <xref:System.Windows.Forms.MergeAction>，和<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>属性，以从 MDI 父菜单的下拉部分移除菜单项。</span><span class="sxs-lookup"><span data-stu-id="1e039-106">The following procedure uses the <xref:System.Windows.Forms.Form.IsMdiContainer%2A>, <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>, <xref:System.Windows.Forms.MergeAction>, and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties to remove a menu item from the drop-down part of the MDI parent menu.</span></span> <span data-ttu-id="1e039-107">关闭 MDI 子窗口将移除的菜单项还原到 MDI 父菜单。</span><span class="sxs-lookup"><span data-stu-id="1e039-107">Closing the MDI child window restores the removed menu items to the MDI parent menu.</span></span>  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a><span data-ttu-id="1e039-108">若要从 MDI 下拉菜单移除 MenuStrip</span><span class="sxs-lookup"><span data-stu-id="1e039-108">To remove a MenuStrip from an MDI drop-down menu</span></span>  
  
1. <span data-ttu-id="1e039-109">创建一个窗体并将其 <xref:System.Windows.Forms.Form.IsMdiContainer%2A> 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="1e039-109">Create a form and set its <xref:System.Windows.Forms.Form.IsMdiContainer%2A> property to `true`.</span></span>  
  
2. <span data-ttu-id="1e039-110">将 <xref:System.Windows.Forms.MenuStrip> 添加到 `Form1` 并将 <xref:System.Windows.Forms.MenuStrip> 的 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> 属性设置为 `true`。</span><span class="sxs-lookup"><span data-stu-id="1e039-110">Add a <xref:System.Windows.Forms.MenuStrip> to `Form1` and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the <xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
3. <span data-ttu-id="1e039-111">添加到顶级菜单项`Form1`<xref:System.Windows.Forms.MenuStrip>并设置其<xref:System.Windows.Forms.Control.Text%2A>属性设置为`&File`。</span><span class="sxs-lookup"><span data-stu-id="1e039-111">Add a top-level menu item to the `Form1`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.Control.Text%2A> property to `&File`.</span></span>  
  
4. <span data-ttu-id="1e039-112">添加到的三个子菜单项`&File`菜单项并设置其<xref:System.Windows.Forms.ToolStripItem.Text%2A>属性设置为`&Open`， `&Import from`，和`E&xit`。</span><span class="sxs-lookup"><span data-stu-id="1e039-112">Add three submenu items to the `&File` menu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Open`, `&Import from`, and `E&xit`.</span></span>  
  
5. <span data-ttu-id="1e039-113">添加到的两个子菜单项`&Import from`子菜单项并设置其<xref:System.Windows.Forms.ToolStripItem.Text%2A>属性设置为`&Word`和`&Excel`。</span><span class="sxs-lookup"><span data-stu-id="1e039-113">Add two submenu items to the `&Import from` submenu item and set their <xref:System.Windows.Forms.ToolStripItem.Text%2A> properties to `&Word` and `&Excel`.</span></span>  
  
6. <span data-ttu-id="1e039-114">向项目添加窗体中，添加<xref:System.Windows.Forms.MenuStrip>到的窗体，并设置<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>的属性`Form2`<xref:System.Windows.Forms.MenuStrip>到`true`。</span><span class="sxs-lookup"><span data-stu-id="1e039-114">Add a form to the project, add a <xref:System.Windows.Forms.MenuStrip> to the form, and set the <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> property of the `Form2`<xref:System.Windows.Forms.MenuStrip> to `true`.</span></span>  
  
7. <span data-ttu-id="1e039-115">添加到顶级菜单项`Form2`<xref:System.Windows.Forms.MenuStrip>并设置其<xref:System.Windows.Forms.ToolStripItem.Text%2A>属性设置为`&File`。</span><span class="sxs-lookup"><span data-stu-id="1e039-115">Add a top-level menu item to the `Form2`<xref:System.Windows.Forms.MenuStrip> and set its <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to `&File`.</span></span>  
  
8. <span data-ttu-id="1e039-116">添加`&Import from`子菜单项`&File`菜单`Form2`，并添加`&Word`子菜单项到`&File`菜单。</span><span class="sxs-lookup"><span data-stu-id="1e039-116">Add an `&Import from` submenu item to the `&File` menu of `Form2`, and add an `&Word` submenu item to the `&File` menu.</span></span>  
  
9. <span data-ttu-id="1e039-117">设置<xref:System.Windows.Forms.MergeAction>并<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>的属性`Form2`下表中所示的菜单项。</span><span class="sxs-lookup"><span data-stu-id="1e039-117">Set the <xref:System.Windows.Forms.MergeAction> and <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> properties of the `Form2` menu items as shown in the following table.</span></span>  
  
    |<span data-ttu-id="1e039-118">Form2 的菜单项</span><span class="sxs-lookup"><span data-stu-id="1e039-118">Form2 menu item</span></span>|<span data-ttu-id="1e039-119">MergeAction 值</span><span class="sxs-lookup"><span data-stu-id="1e039-119">MergeAction value</span></span>|<span data-ttu-id="1e039-120">MergeIndex 值</span><span class="sxs-lookup"><span data-stu-id="1e039-120">MergeIndex value</span></span>|  
    |---------------------|-----------------------|----------------------|  
    |<span data-ttu-id="1e039-121">文件</span><span class="sxs-lookup"><span data-stu-id="1e039-121">File</span></span>|<span data-ttu-id="1e039-122">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="1e039-122">MatchOnly</span></span>|<span data-ttu-id="1e039-123">-1</span><span class="sxs-lookup"><span data-stu-id="1e039-123">-1</span></span>|  
    |<span data-ttu-id="1e039-124">从导入</span><span class="sxs-lookup"><span data-stu-id="1e039-124">Import from</span></span>|<span data-ttu-id="1e039-125">MatchOnly</span><span class="sxs-lookup"><span data-stu-id="1e039-125">MatchOnly</span></span>|<span data-ttu-id="1e039-126">-1</span><span class="sxs-lookup"><span data-stu-id="1e039-126">-1</span></span>|  
    |<span data-ttu-id="1e039-127">字</span><span class="sxs-lookup"><span data-stu-id="1e039-127">Word</span></span>|<span data-ttu-id="1e039-128">删除</span><span class="sxs-lookup"><span data-stu-id="1e039-128">Remove</span></span>|<span data-ttu-id="1e039-129">-1</span><span class="sxs-lookup"><span data-stu-id="1e039-129">-1</span></span>|  
  
10. <span data-ttu-id="1e039-130">在中`Form1`，创建的事件处理程序<xref:System.Windows.Forms.Control.Click>事件的`&Open`<xref:System.Windows.Forms.ToolStripMenuItem>。</span><span class="sxs-lookup"><span data-stu-id="1e039-130">In `Form1`, create an event handler for the <xref:System.Windows.Forms.Control.Click> event of the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>  
  
11. <span data-ttu-id="1e039-131">事件处理程序中插入类似于下面的代码示例，若要创建和显示的新实例的代码`Form2`作为的 MDI 子级`Form1`:</span><span class="sxs-lookup"><span data-stu-id="1e039-131">Within the event handler, insert code similar to the following code example to create and display new instances of `Form2` as MDI children of `Form1`:</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
12. <span data-ttu-id="1e039-132">将代码置于类似于下面的代码示例中`&Open`<xref:System.Windows.Forms.ToolStripMenuItem>注册事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="1e039-132">Place code similar to the following code example in the `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> to register the event handler.</span></span>  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1e039-133">编译代码</span><span class="sxs-lookup"><span data-stu-id="1e039-133">Compiling the Code</span></span>  
 <span data-ttu-id="1e039-134">此示例需要：</span><span class="sxs-lookup"><span data-stu-id="1e039-134">This example requires:</span></span>  
  
-   <span data-ttu-id="1e039-135">名为 `Form1` 和 `Form2` 的两个 <xref:System.Windows.Forms.Form> 控件。</span><span class="sxs-lookup"><span data-stu-id="1e039-135">Two <xref:System.Windows.Forms.Form> controls named `Form1` and `Form2`.</span></span>  
  
-   <span data-ttu-id="1e039-136">`Form1` 上名为 `menuStrip1` 的 <xref:System.Windows.Forms.MenuStrip> 控件和 `Form2` 上名为 `menuStrip2` 的 <xref:System.Windows.Forms.MenuStrip> 控件。</span><span class="sxs-lookup"><span data-stu-id="1e039-136">A <xref:System.Windows.Forms.MenuStrip> control on `Form1` named `menuStrip1`, and a <xref:System.Windows.Forms.MenuStrip> control on `Form2` named `menuStrip2`.</span></span>  
  
-   <span data-ttu-id="1e039-137">对 <xref:System?displayProperty=nameWithType> 和 <xref:System.Windows.Forms?displayProperty=nameWithType> 程序集的引用。</span><span class="sxs-lookup"><span data-stu-id="1e039-137">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e039-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="1e039-138">See also</span></span>

- [<span data-ttu-id="1e039-139">如何：创建 MDI 父窗体</span><span class="sxs-lookup"><span data-stu-id="1e039-139">How to: Create MDI Parent Forms</span></span>](../advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="1e039-140">如何：创建 MDI 子窗体</span><span class="sxs-lookup"><span data-stu-id="1e039-140">How to: Create MDI Child Forms</span></span>](../advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="1e039-141">MenuStrip 控件概述</span><span class="sxs-lookup"><span data-stu-id="1e039-141">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
