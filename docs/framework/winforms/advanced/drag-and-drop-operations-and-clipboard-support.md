---
title: 拖放操作和剪贴板支持
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
ms.openlocfilehash: 281d102ecd02623e7e18ebf4fc569538ebbdaf7f
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/20/2019
ms.locfileid: "56442004"
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a><span data-ttu-id="c7f33-102">拖放操作和剪贴板支持</span><span class="sxs-lookup"><span data-stu-id="c7f33-102">Drag-and-Drop Operations and Clipboard Support</span></span>
<span data-ttu-id="c7f33-103">可以通过处理一系列事件（最主要是 <xref:System.Windows.Forms.Control.DragEnter>、<xref:System.Windows.Forms.Control.DragLeave> 和 <xref:System.Windows.Forms.Control.DragDrop> 事件），在基于 Windows 的应用程序中启用用户拖放操作。</span><span class="sxs-lookup"><span data-stu-id="c7f33-103">You can enable user drag-and-drop operations within a Windows-based application by handling a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
 <span data-ttu-id="c7f33-104">也可以使用简单的方法调用，在基于 Windows 的应用程序中对剪贴板实现用户剪切/复制/粘贴支持和用户数据传输。</span><span class="sxs-lookup"><span data-stu-id="c7f33-104">You can also implement user cut/copy/paste support and user data transfer to the Clipboard within your Windows-based applications by using simple method calls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7f33-105">本节内容</span><span class="sxs-lookup"><span data-stu-id="c7f33-105">In This Section</span></span>  
 [<span data-ttu-id="c7f33-106">演练：在 Windows 窗体中执行拖放操作</span><span class="sxs-lookup"><span data-stu-id="c7f33-106">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 <span data-ttu-id="c7f33-107">说明如何启动拖放操作。</span><span class="sxs-lookup"><span data-stu-id="c7f33-107">Explains how to start a drag-and-drop operation.</span></span>  
  
 [<span data-ttu-id="c7f33-108">如何：执行应用程序之间的拖放操作</span><span class="sxs-lookup"><span data-stu-id="c7f33-108">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 <span data-ttu-id="c7f33-109">演示如何跨应用程序完成拖放操作。</span><span class="sxs-lookup"><span data-stu-id="c7f33-109">Illustrates how to accomplish drag-and-drop operations across applications.</span></span>  
  
 [<span data-ttu-id="c7f33-110">如何：将数据添加到剪贴板</span><span class="sxs-lookup"><span data-stu-id="c7f33-110">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 <span data-ttu-id="c7f33-111">介绍如何以编程方式在剪贴板上插入信息。</span><span class="sxs-lookup"><span data-stu-id="c7f33-111">Describes a way to programmatically insert information on the Clipboard.</span></span>  
  
 [<span data-ttu-id="c7f33-112">如何：从剪贴板中检索数据</span><span class="sxs-lookup"><span data-stu-id="c7f33-112">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 <span data-ttu-id="c7f33-113">介绍如何访问剪贴板上存储的数据。</span><span class="sxs-lookup"><span data-stu-id="c7f33-113">Describes how to access the data stored on the Clipboard.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c7f33-114">相关章节</span><span class="sxs-lookup"><span data-stu-id="c7f33-114">Related Sections</span></span>  
 [<span data-ttu-id="c7f33-115">Windows 窗体中的拖放功能</span><span class="sxs-lookup"><span data-stu-id="c7f33-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="c7f33-116">介绍用于实现拖放行为的方法、事件和类。</span><span class="sxs-lookup"><span data-stu-id="c7f33-116">Describes the methods, events, and classes used to implement drag-and-drop behavior.</span></span>  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 <span data-ttu-id="c7f33-117">介绍要求权限才能继续拖动操作的事件的复杂性。</span><span class="sxs-lookup"><span data-stu-id="c7f33-117">Describes the intricacies of the event that asks permission to continue the drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 <span data-ttu-id="c7f33-118">介绍对开始拖动操作极为重要的方法的复杂性。</span><span class="sxs-lookup"><span data-stu-id="c7f33-118">Describes the intricacies of the method that is central to beginning a drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Clipboard>  
 <span data-ttu-id="c7f33-119">另请参阅[如何：将数据发送到活动的 MDI 子窗体](how-to-send-data-to-the-active-mdi-child.md)。</span><span class="sxs-lookup"><span data-stu-id="c7f33-119">Also see [How to: Send Data to the Active MDI Child](how-to-send-data-to-the-active-mdi-child.md).</span></span>
