---
title: 如何：在 Windows 窗体中访问键控集合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keyed collections [Windows Forms]
- collections [Windows Forms], accessing with keys
ms.assetid: b9b79b8b-d9bf-4f8c-b9d6-9578bc3219d3
ms.openlocfilehash: a88e4766a1e774582bcd0356c9b6e77bc31f1960
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928526"
---
# <a name="how-to-access-keyed-collections-in-windows-forms"></a><span data-ttu-id="84b64-102">如何：在 Windows 窗体中访问键控集合</span><span class="sxs-lookup"><span data-stu-id="84b64-102">How to: Access Keyed Collections in Windows Forms</span></span>

- <span data-ttu-id="84b64-103">可以通过键访问各个集合项。</span><span class="sxs-lookup"><span data-stu-id="84b64-103">You can access individual collection items by key.</span></span> <span data-ttu-id="84b64-104">此功能已添加到 Windows 窗体应用程序通常使用的许多集合类中。</span><span class="sxs-lookup"><span data-stu-id="84b64-104">This functionality has been added to many collection classes that are typically used by Windows Forms applications.</span></span> <span data-ttu-id="84b64-105">下面的列表显示了一些具有可访问键控集合的集合类：</span><span class="sxs-lookup"><span data-stu-id="84b64-105">The following list shows some of the collection classes that have accessible keyed collections:</span></span>  
  
- <xref:System.Windows.Forms.ListView.ListViewItemCollection>  
  
- <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection>  
  
- <xref:System.Windows.Forms.Control.ControlCollection>  
  
- <xref:System.Windows.Forms.TabControl.TabPageCollection>  
  
- <xref:System.Windows.Forms.TreeNodeCollection>  
  
 <span data-ttu-id="84b64-106">与集合中的项关联的键通常是项的名称。</span><span class="sxs-lookup"><span data-stu-id="84b64-106">The key associated with an item in a collection is typically the name of the item.</span></span> <span data-ttu-id="84b64-107">下面的过程演示如何使用集合类来执行常见任务。</span><span class="sxs-lookup"><span data-stu-id="84b64-107">The following procedures show you how to use collection classes to perform common tasks.</span></span>  
  
### <a name="to-find-and-give-focus-to-a-nested-control-in-a-control-collection"></a><span data-ttu-id="84b64-108">查找焦点并将焦点放在控件集合中的嵌套控件上</span><span class="sxs-lookup"><span data-stu-id="84b64-108">To find and give focus to a nested control in a control collection</span></span>  
  
- <span data-ttu-id="84b64-109"><xref:System.Windows.Forms.Control.ControlCollection.Find%2A>使用和<xref:System.Windows.Forms.Control.Focus%2A>方法来指定要查找并将焦点提供给的控件的名称。</span><span class="sxs-lookup"><span data-stu-id="84b64-109">Use the <xref:System.Windows.Forms.Control.ControlCollection.Find%2A> and <xref:System.Windows.Forms.Control.Focus%2A> methods to specify the name of the control to find and give focus to.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#1)]  
  
### <a name="to-access-an-image-in-an-image-collection"></a><span data-ttu-id="84b64-110">访问映像集合中的图像</span><span class="sxs-lookup"><span data-stu-id="84b64-110">To access an image in an image collection</span></span>  
  
- <span data-ttu-id="84b64-111">使用 " <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A>属性" 指定要访问的映像的名称。</span><span class="sxs-lookup"><span data-stu-id="84b64-111">Use the <xref:System.Windows.Forms.ImageList.ImageCollection.Item%2A> property to specify the name of the image you want to access.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#2)]  
  
### <a name="to-set-a-tab-page-as-the-selected-tab"></a><span data-ttu-id="84b64-112">将选项卡页设置为选定的选项卡</span><span class="sxs-lookup"><span data-stu-id="84b64-112">To set a tab page as the selected tab</span></span>  
  
- <span data-ttu-id="84b64-113">结合使用<xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A>属性和属性以指定要设置为所选选项卡的选项卡页的名称。 <xref:System.Windows.Forms.TabControl.SelectedTab%2A></span><span class="sxs-lookup"><span data-stu-id="84b64-113">Use the <xref:System.Windows.Forms.TabControl.SelectedTab%2A> property together with the <xref:System.Windows.Forms.TabControl.TabPageCollection.Item%2A> property to specify the name of the tab page to set as the selected tab.</span></span>  
  
     [!code-csharp[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.KeyedCollectionsEx#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyedCollectionsEx/VB/Form1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="84b64-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="84b64-114">See also</span></span>

- [<span data-ttu-id="84b64-115">Windows 窗体入门</span><span class="sxs-lookup"><span data-stu-id="84b64-115">Getting Started with Windows Forms</span></span>](getting-started-with-windows-forms.md)
- [<span data-ttu-id="84b64-116">如何：在 Windows 窗体 ImageList 组件中添加或删除图像</span><span class="sxs-lookup"><span data-stu-id="84b64-116">How to: Add or Remove Images with the Windows Forms ImageList Component</span></span>](./controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)
