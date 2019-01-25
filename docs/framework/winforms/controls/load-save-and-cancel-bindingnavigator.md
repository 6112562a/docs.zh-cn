---
title: 如何：添加负载，保存和取消按钮，为 Windows 窗体 BindingNavigator 控件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], manipulating
- BindingNavigator control [Windows Forms], adding buttons
ms.assetid: faa33042-186e-4bb2-8798-17ceb987ec62
ms.openlocfilehash: dc91a4a91d26cd51a06b1c08dcb76f8966c52594
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671104"
---
# <a name="how-to-add-load-save-and-cancel-buttons-to-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="5b2b7-102">如何：添加负载，保存和取消按钮，为 Windows 窗体 BindingNavigator 控件</span><span class="sxs-lookup"><span data-stu-id="5b2b7-102">How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="5b2b7-103"><xref:System.Windows.Forms.BindingNavigator>控件是特殊用途<xref:System.Windows.Forms.ToolStrip>旨在用于导航和操作绑定到数据窗体上的控件的控件。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-103">The <xref:System.Windows.Forms.BindingNavigator> control is a special-purpose <xref:System.Windows.Forms.ToolStrip> control that is intended for navigating and manipulating controls on your form that are bound to data.</span></span>  
  
 <span data-ttu-id="5b2b7-104">因为它是<xref:System.Windows.Forms.ToolStrip>控件，<xref:System.Windows.Forms.BindingNavigator>组件可以轻松地修改为包含用户的附加或替代命令。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-104">Because it is a <xref:System.Windows.Forms.ToolStrip> control, the <xref:System.Windows.Forms.BindingNavigator> component can be easily modified to include additional or alternative commands for the user.</span></span>  
  
 <span data-ttu-id="5b2b7-105">在下面的过程中，<xref:System.Windows.Forms.TextBox>控件绑定到数据，并<xref:System.Windows.Forms.ToolStrip>添加到窗体的控件修改以包括保存、 加载和取消按钮。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-105">In the following procedure, a <xref:System.Windows.Forms.TextBox> control is bound to data, and the <xref:System.Windows.Forms.ToolStrip> control that is added to the form is modified to include load, save, and cancel buttons.</span></span>  
  
### <a name="to-add-load-save-and-cancel-buttons-to-the-bindingnavigator-component"></a><span data-ttu-id="5b2b7-106">若要添加负载，保存和取消按钮的 BindingNavigator 组件</span><span class="sxs-lookup"><span data-stu-id="5b2b7-106">To add load, save, and cancel buttons to the BindingNavigator component</span></span>  
  
1.  <span data-ttu-id="5b2b7-107">向窗体添加一个 <xref:System.Windows.Forms.TextBox> 控件。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-107">Add a <xref:System.Windows.Forms.TextBox> control to your form.</span></span>  
  
2.  <span data-ttu-id="5b2b7-108">将其绑定到<xref:System.Windows.Forms.BindingSource>，后者已绑定到数据源。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-108">Bind it to a <xref:System.Windows.Forms.BindingSource>, which is bound to a data source.</span></span> <span data-ttu-id="5b2b7-109">此示例中，为<xref:System.Windows.Forms.BindingSource>绑定到数据库。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-109">For this example, the <xref:System.Windows.Forms.BindingSource> is bound to a database.</span></span>  
  
3.  <span data-ttu-id="5b2b7-110">生成数据集和表适配器后，请将<xref:System.Windows.Forms.BindingNavigator>到窗体控件。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-110">After the dataset and table adapter are generated, drag a <xref:System.Windows.Forms.BindingNavigator> control to the form.</span></span>  
  
4.  <span data-ttu-id="5b2b7-111">设置<xref:System.Windows.Forms.BindingNavigator>控件的<xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>属性设置为<xref:System.Windows.Forms.BindingSource>绑定到控件的窗体上。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-111">Set the <xref:System.Windows.Forms.BindingNavigator> control's <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the <xref:System.Windows.Forms.BindingSource> on the form that is bound to the controls.</span></span>  
  
5.  <span data-ttu-id="5b2b7-112">选择 <xref:System.Windows.Forms.BindingNavigator> 控件。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-112">Select the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
6.  <span data-ttu-id="5b2b7-113">单击智能标记标志符号 (![智能标记标志符号](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))，因此**BindingNavigator 任务**对话框，然后选择**编辑项**.</span><span class="sxs-lookup"><span data-stu-id="5b2b7-113">Click the smart tag glyph (![Smart Tag Glyph](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) so the **BindingNavigator Tasks** dialog appears and select **Edit Items**.</span></span>  
  
     <span data-ttu-id="5b2b7-114">**项集合编辑器**出现。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-114">The **Items Collection Editor** appears.</span></span>  
  
7.  <span data-ttu-id="5b2b7-115">在中**项集合编辑器**，完成下列操作：</span><span class="sxs-lookup"><span data-stu-id="5b2b7-115">In the **Items Collection Editor**, complete the following:</span></span>  
  
    1.  <span data-ttu-id="5b2b7-116">添加<xref:System.Windows.Forms.ToolStripSeparator>和三个<xref:System.Windows.Forms.ToolStripButton>通过选择适当类型的项<xref:System.Windows.Forms.ToolStripItem>，然后单击**添加**按钮。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-116">Add a <xref:System.Windows.Forms.ToolStripSeparator> and three <xref:System.Windows.Forms.ToolStripButton> items by selecting the appropriate type of <xref:System.Windows.Forms.ToolStripItem> and clicking the **Add** button.</span></span>  
  
    2.  <span data-ttu-id="5b2b7-117">设置<xref:System.Windows.Forms.ToolStripItem.Name%2A>到按钮的属性**LoadButton**， **SaveButton**，并且**CancelButton**分别。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-117">Set the <xref:System.Windows.Forms.ToolStripItem.Name%2A> property of the buttons to **LoadButton**, **SaveButton**, and **CancelButton**, respectively.</span></span>  
  
    3.  <span data-ttu-id="5b2b7-118">设置<xref:System.Windows.Forms.ToolStripItem.Text%2A>到按钮的属性**负载**，**保存**，并且**取消**。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-118">Set the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property of the buttons to **Load**, **Save**, and **Cancel**.</span></span>  
  
    4.  <span data-ttu-id="5b2b7-119">设置<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>到按钮的每个属性**文本**。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-119">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property for each of the buttons to **Text**.</span></span> <span data-ttu-id="5b2b7-120">或者，可以将此属性设置为**图像**或**ImageAndText**，并设置中显示的图像<xref:System.Windows.Forms.ToolStripItem.Image%2A>属性。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-120">Alternatively, you can set this property to **Image** or **ImageAndText**, and set the image to be displayed in the <xref:System.Windows.Forms.ToolStripItem.Image%2A> property.</span></span>  
  
    5.  <span data-ttu-id="5b2b7-121">单击**确定**以关闭对话框。这些按钮将添加到<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-121">Click **OK** to close the dialog box.The buttons are added to the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
8.  <span data-ttu-id="5b2b7-122">右键单击窗体，然后选择**查看代码**。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-122">Right-click the form and choose **View Code**.</span></span>  
  
9. <span data-ttu-id="5b2b7-123">在代码编辑器中，找到将数据加载到表适配器的代码的行。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-123">In the Code Editor, find the line of code that loads data into the table adapter.</span></span> <span data-ttu-id="5b2b7-124">此代码生成设置在步骤 2 中的数据绑定时。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-124">This code was generated when you set up the data binding in step 2.</span></span> <span data-ttu-id="5b2b7-125">代码应如下所示： `TableAdapterName.Fill(DataSetName.TableName)`。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-125">The code should be similar to the following: `TableAdapterName.Fill(DataSetName.TableName)`.</span></span> <span data-ttu-id="5b2b7-126">它将很有可能是窗体的<xref:System.Windows.Forms.Form.Load>事件。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-126">It will most likely be in the form's <xref:System.Windows.Forms.Form.Load> event.</span></span>  
  
10. <span data-ttu-id="5b2b7-127">创建事件处理程序<xref:System.Windows.Forms.ToolStripItem.Click>的事件**负载**<xref:System.Windows.Forms.ToolStripButton>之前创建并将此数据加载代码移到它。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-127">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Load** <xref:System.Windows.Forms.ToolStripButton> you created earlier and move this data-loading code into it.</span></span>  
  
     <span data-ttu-id="5b2b7-128">你的代码应类似于下面：</span><span class="sxs-lookup"><span data-stu-id="5b2b7-128">Your code should now look similar to the following:</span></span>  
  
    ```vb  
    Private Sub LoadButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles LoadButton.Click  
        TableAdapterName.Fill(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Fill(DataSetName.TableName);  
    }  
    ```  
  
11. <span data-ttu-id="5b2b7-129">创建事件处理程序<xref:System.Windows.Forms.ToolStripItem.Click>的事件**保存**<xref:System.Windows.Forms.ToolStripButton>之前创建和编写代码以更新表控件内的数据绑定到。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-129">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Save**<xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to update the data within the table the control is bound to.</span></span>  
  
    ```vb  
    Private Sub SaveButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles SaveButton.Click  
        TableAdapterName.Update(DataSetName.TableName)  
    End Sub  
    ```  
  
    ```csharp  
    private void SaveButton_Click(System.Object sender,   
        System.EventArgs e)  
    {  
        TableAdapterName.Update(DataSetName.TableName);  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="5b2b7-130">在某些情况下，<xref:System.Windows.Forms.BindingNavigator>组件已**保存**按钮，但没有代码将生成的 Windows 窗体设计器。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-130">In some cases, the <xref:System.Windows.Forms.BindingNavigator> component will already have a **Save** button, but no code will have been generated by the Windows Forms Designer.</span></span> <span data-ttu-id="5b2b7-131">在这种情况下，可以将前面的代码中放置<xref:System.Windows.Forms.ToolStripItem.Click>这个按钮，而不是创建全新的按钮上的事件处理程序<xref:System.Windows.Forms.ToolStrip>。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-131">In this case, you can place the preceding code in the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for that button, rather than creating an entirely new button on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="5b2b7-132">但是，该按钮默认处于禁用状态，因此必须设置<xref:System.Windows.Forms.ToolBarButton.Enabled%2A>属性的按钮为`true`以使按钮函数正确。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-132">However, the button is disabled by default, so you must set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property of the button to `true` to have the button function correctly.</span></span>
  
12. <span data-ttu-id="5b2b7-133">创建事件处理程序<xref:System.Windows.Forms.ToolStripItem.Click>的事件**取消**<xref:System.Windows.Forms.ToolStripButton>之前创建和编写代码来取消对显示的数据记录的任何更改。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-133">Create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event of the **Cancel** <xref:System.Windows.Forms.ToolStripButton> you created earlier and write code to cancel any changes to the data record that is displayed.</span></span>  
  
    ```vb  
    Private Sub CancelButton_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles CancelButton.Click  
        BindingSourceName.CancelEdit()  
    End Sub  
    ```  
  
    ```csharp  
    private void CancelButton_Click(System.Object sender, System.EventArgs e)  
    {  
        BindingSourceName.CancelEdit();  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5b2b7-134"><xref:System.Windows.Forms.BindingSource.CancelEdit%2A>方法的范围限定为一行数据。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-134">The <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> method is scoped to the row of data.</span></span> <span data-ttu-id="5b2b7-135">保存您在导航到下一条记录之前查看该单个记录时进行任何更改。</span><span class="sxs-lookup"><span data-stu-id="5b2b7-135">Save any changes you make while viewing that individual record before navigating to the next record.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b2b7-136">请参阅</span><span class="sxs-lookup"><span data-stu-id="5b2b7-136">See also</span></span>
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.ToolStrip>
- [<span data-ttu-id="5b2b7-137">BindingNavigator 控件</span><span class="sxs-lookup"><span data-stu-id="5b2b7-137">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="5b2b7-138">BindingSource 组件概述</span><span class="sxs-lookup"><span data-stu-id="5b2b7-138">BindingSource Component Overview</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)
