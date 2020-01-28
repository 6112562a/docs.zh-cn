---
title: 用 TreeView 控件添加和删除节点
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: de1b82db-4905-449a-9f59-af271a6b6673
ms.openlocfilehash: 02b3a7286798c6f2a6426e09c8fc6c18b74a6bf0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731960"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a><span data-ttu-id="bac4c-102">如何：添加和删除 Windows 窗体 TreeView 控件中的节点</span><span class="sxs-lookup"><span data-stu-id="bac4c-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control</span></span>
<span data-ttu-id="bac4c-103">Windows 窗体 <xref:System.Windows.Forms.TreeView> 控件将顶级节点存储在其 <xref:System.Windows.Forms.TreeView.Nodes%2A> 集合中。</span><span class="sxs-lookup"><span data-stu-id="bac4c-103">The Windows Forms <xref:System.Windows.Forms.TreeView> control stores the top-level nodes in its <xref:System.Windows.Forms.TreeView.Nodes%2A> collection.</span></span> <span data-ttu-id="bac4c-104">每个 <xref:System.Windows.Forms.TreeNode> 也有其自己的 <xref:System.Windows.Forms.TreeNode.Nodes%2A> 集合来存储其子节点。</span><span class="sxs-lookup"><span data-stu-id="bac4c-104">Each <xref:System.Windows.Forms.TreeNode> also has its own <xref:System.Windows.Forms.TreeNode.Nodes%2A> collection to store its child nodes.</span></span> <span data-ttu-id="bac4c-105">这两个集合属性都属于类型 <xref:System.Windows.Forms.TreeNodeCollection>，它提供了标准集合成员，使你能够在节点层次结构的一个级别添加、移除和重新排列节点。</span><span class="sxs-lookup"><span data-stu-id="bac4c-105">Both collection properties are of type <xref:System.Windows.Forms.TreeNodeCollection>, which provides standard collection members that enable you to add, remove, and rearrange the nodes at a single level of the node hierarchy.</span></span>  
  
### <a name="to-add-nodes-programmatically"></a><span data-ttu-id="bac4c-106">以编程方式添加节点</span><span class="sxs-lookup"><span data-stu-id="bac4c-106">To add nodes programmatically</span></span>  
  
1. <span data-ttu-id="bac4c-107">使用树视图的 <xref:System.Windows.Forms.TreeView.Nodes%2A> 属性的 <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="bac4c-107">Use the <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
    ```vb  
    ' Adds new node as a child node of the currently selected node.  
    Dim newNode As TreeNode = New TreeNode("Text for new node")  
    TreeView1.SelectedNode.Nodes.Add(newNode)  
    ```  
  
    ```csharp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode newNode = new TreeNode("Text for new node");  
    treeView1.SelectedNode.Nodes.Add(newNode);  
    ```  
  
    ```cpp  
    // Adds new node as a child node of the currently selected node.  
    TreeNode ^ newNode = new TreeNode("Text for new node");  
    treeView1->SelectedNode->Nodes->Add(newNode);  
    ```  
  
### <a name="to-remove-nodes-programmatically"></a><span data-ttu-id="bac4c-108">以编程方式删除节点</span><span class="sxs-lookup"><span data-stu-id="bac4c-108">To remove nodes programmatically</span></span>  
  
1. <span data-ttu-id="bac4c-109">使用树视图的 <xref:System.Windows.Forms.TreeView.Nodes%2A> 属性的 <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> 方法可移除单个节点或 <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> 方法，以清除所有节点。</span><span class="sxs-lookup"><span data-stu-id="bac4c-109">Use the <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> method of the tree view's <xref:System.Windows.Forms.TreeView.Nodes%2A> property to remove a single node, or the <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> method to clear all nodes.</span></span>  
  
    ```vb  
    ' Removes currently selected node, or root if nothing is selected.  
    TreeView1.Nodes.Remove(TreeView1.SelectedNode)  
    ' Clears all nodes.  
    TreeView1.Nodes.Clear()  
    ```  
  
    ```csharp  
    // Removes currently selected node, or root if nothing   
    // is selected.  
    treeView1.Nodes.Remove(treeView1.SelectedNode);  
    // Clears all nodes.  
    TreeView1.Nodes.Clear();  
    ```  
  
    ```cpp  
    // Removes currently selected node, or root if nothing  
    // is selected.  
    treeView1->Nodes->Remove(treeView1->SelectedNode);  
    // Clears all nodes.  
    treeView1->Nodes->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bac4c-110">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bac4c-110">See also</span></span>

- [<span data-ttu-id="bac4c-111">TreeView 控件</span><span class="sxs-lookup"><span data-stu-id="bac4c-111">TreeView Control</span></span>](treeview-control-windows-forms.md)
- [<span data-ttu-id="bac4c-112">TreeView 控件概述</span><span class="sxs-lookup"><span data-stu-id="bac4c-112">TreeView Control Overview</span></span>](treeview-control-overview-windows-forms.md)
- [<span data-ttu-id="bac4c-113">如何：设置 Windows 窗体 TreeView 控件的图标</span><span class="sxs-lookup"><span data-stu-id="bac4c-113">How to: Set Icons for the Windows Forms TreeView Control</span></span>](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [<span data-ttu-id="bac4c-114">如何：循环访问 Windows 窗体 TreeView 控件的所有节点</span><span class="sxs-lookup"><span data-stu-id="bac4c-114">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [<span data-ttu-id="bac4c-115">如何：确定哪个 TreeView 节点获得了单击</span><span class="sxs-lookup"><span data-stu-id="bac4c-115">How to: Determine Which TreeView Node Was Clicked</span></span>](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [<span data-ttu-id="bac4c-116">如何：向 TreeView 或 ListView 控件（Windows 窗体）添加自定义信息</span><span class="sxs-lookup"><span data-stu-id="bac4c-116">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](add-custom-information-to-a-treeview-or-listview-control-wf.md)
