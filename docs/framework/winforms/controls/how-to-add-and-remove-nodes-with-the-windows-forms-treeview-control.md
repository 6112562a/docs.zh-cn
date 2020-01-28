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
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control"></a>如何：添加和删除 Windows 窗体 TreeView 控件中的节点
Windows 窗体 <xref:System.Windows.Forms.TreeView> 控件将顶级节点存储在其 <xref:System.Windows.Forms.TreeView.Nodes%2A> 集合中。 每个 <xref:System.Windows.Forms.TreeNode> 也有其自己的 <xref:System.Windows.Forms.TreeNode.Nodes%2A> 集合来存储其子节点。 这两个集合属性都属于类型 <xref:System.Windows.Forms.TreeNodeCollection>，它提供了标准集合成员，使你能够在节点层次结构的一个级别添加、移除和重新排列节点。  
  
### <a name="to-add-nodes-programmatically"></a>以编程方式添加节点  
  
1. 使用树视图的 <xref:System.Windows.Forms.TreeView.Nodes%2A> 属性的 <xref:System.Windows.Forms.TreeNodeCollection.Add%2A> 方法。  
  
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
  
### <a name="to-remove-nodes-programmatically"></a>以编程方式删除节点  
  
1. 使用树视图的 <xref:System.Windows.Forms.TreeView.Nodes%2A> 属性的 <xref:System.Windows.Forms.TreeNodeCollection.Remove%2A> 方法可移除单个节点或 <xref:System.Windows.Forms.TreeNodeCollection.Clear%2A> 方法，以清除所有节点。  
  
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
  
## <a name="see-also"></a>另请参阅

- [TreeView 控件](treeview-control-windows-forms.md)
- [TreeView 控件概述](treeview-control-overview-windows-forms.md)
- [如何：设置 Windows 窗体 TreeView 控件的图标](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [如何：循环访问 Windows 窗体 TreeView 控件的所有节点](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [如何：确定哪个 TreeView 节点获得了单击](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [如何：向 TreeView 或 ListView 控件（Windows 窗体）添加自定义信息](add-custom-information-to-a-treeview-or-listview-control-wf.md)
