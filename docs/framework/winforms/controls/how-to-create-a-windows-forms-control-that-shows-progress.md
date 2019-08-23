---
title: 如何：创建显示进度的 Windows 窗体控件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
ms.openlocfilehash: 84f0caace70f9877e84fdd01dc69216dc10fe485
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950580"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a><span data-ttu-id="45c53-102">如何：创建显示进度的 Windows 窗体控件</span><span class="sxs-lookup"><span data-stu-id="45c53-102">How to: Create a Windows Forms Control That Shows Progress</span></span>
<span data-ttu-id="45c53-103">以下代码示例显示了一个名为 `FlashTrackBar` 的自定义控件，可用于向用户显示应用程序的级别或进度。</span><span class="sxs-lookup"><span data-stu-id="45c53-103">The following code example shows a custom control called `FlashTrackBar` that can be used to show the user the level or the progress of an application.</span></span> <span data-ttu-id="45c53-104">它使用渐变来直观地表示进度。</span><span class="sxs-lookup"><span data-stu-id="45c53-104">It uses a gradient to visually represent progress.</span></span>  
  
 <span data-ttu-id="45c53-105">`FlashTrackBar` 控件阐释了以下概念：</span><span class="sxs-lookup"><span data-stu-id="45c53-105">The `FlashTrackBar` control illustrates the following concepts:</span></span>  
  
- <span data-ttu-id="45c53-106">定义自定义属性。</span><span class="sxs-lookup"><span data-stu-id="45c53-106">Defining custom properties.</span></span>  
  
- <span data-ttu-id="45c53-107">定义自定义事件。</span><span class="sxs-lookup"><span data-stu-id="45c53-107">Defining custom events.</span></span> <span data-ttu-id="45c53-108">（`FlashTrackBar` 定义 `ValueChanged` 事件。）</span><span class="sxs-lookup"><span data-stu-id="45c53-108">(`FlashTrackBar` defines the `ValueChanged` event.)</span></span>  
  
- <span data-ttu-id="45c53-109">重写<xref:System.Windows.Forms.Control.OnPaint%2A>方法以提供用于绘制控件的逻辑。</span><span class="sxs-lookup"><span data-stu-id="45c53-109">Overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method to provide logic to draw the control.</span></span>  
  
- <span data-ttu-id="45c53-110">使用其<xref:System.Windows.Forms.Control.ClientRectangle%2A>属性计算用于绘制控件的区域。</span><span class="sxs-lookup"><span data-stu-id="45c53-110">Computing the area available for drawing the control by using its <xref:System.Windows.Forms.Control.ClientRectangle%2A> property.</span></span> <span data-ttu-id="45c53-111">`FlashTrackBar` 在 `OptimizedInvalidate` 方法中执行此操作。</span><span class="sxs-lookup"><span data-stu-id="45c53-111">`FlashTrackBar` does this in its `OptimizedInvalidate` method.</span></span>  
  
- <span data-ttu-id="45c53-112">在 Windows 窗体设计器中更改属性时，实现其序列化或持久性。</span><span class="sxs-lookup"><span data-stu-id="45c53-112">Implementing serialization or persistence for a property when it is changed in the Windows Forms Designer.</span></span> <span data-ttu-id="45c53-113">`FlashTrackBar` 定义用于序列化其 `StartColor` 和 `EndColor` 属性的 `ShouldSerializeStartColor` 和 `ShouldSerializeEndColor` 方法。</span><span class="sxs-lookup"><span data-stu-id="45c53-113">`FlashTrackBar` defines the `ShouldSerializeStartColor` and `ShouldSerializeEndColor` methods for serializing its `StartColor` and `EndColor` properties.</span></span>  
  
 <span data-ttu-id="45c53-114">下表显示了由 `FlashTrackBar` 定义的自定义属性。</span><span class="sxs-lookup"><span data-stu-id="45c53-114">The following table shows the custom properties defined by `FlashTrackBar`.</span></span>  
  
|<span data-ttu-id="45c53-115">Property</span><span class="sxs-lookup"><span data-stu-id="45c53-115">Property</span></span>|<span data-ttu-id="45c53-116">描述</span><span class="sxs-lookup"><span data-stu-id="45c53-116">Description</span></span>|  
|--------------|-----------------|  
|`AllowUserEdit`|<span data-ttu-id="45c53-117">指示用户是否可以通过单击和拖动来更改闪存跟踪条的值。</span><span class="sxs-lookup"><span data-stu-id="45c53-117">Indicates whether the user can change the value of the flash track bar by clicking and dragging it.</span></span>|  
|`EndColor`|<span data-ttu-id="45c53-118">指定跟踪条的结束颜色。</span><span class="sxs-lookup"><span data-stu-id="45c53-118">Specifies the ending color of the track bar.</span></span>|  
|`DarkenBy`|<span data-ttu-id="45c53-119">指定相对于前景渐变加深背景颜色的程度。</span><span class="sxs-lookup"><span data-stu-id="45c53-119">Specifies how much to darken the background with respect to the foreground gradient.</span></span>|  
|`Max`|<span data-ttu-id="45c53-120">指定跟踪条的最大值。</span><span class="sxs-lookup"><span data-stu-id="45c53-120">Specifies the maximum value of the track bar.</span></span>|  
|`Min`|<span data-ttu-id="45c53-121">指定跟踪条的最小值。</span><span class="sxs-lookup"><span data-stu-id="45c53-121">Specifies the minimum value of the track bar.</span></span>|  
|`StartColor`|<span data-ttu-id="45c53-122">指定渐变的开始颜色。</span><span class="sxs-lookup"><span data-stu-id="45c53-122">Specifies the starting color of the gradient.</span></span>|  
|`ShowPercentage`|<span data-ttu-id="45c53-123">指示是否在渐变上显示百分比。</span><span class="sxs-lookup"><span data-stu-id="45c53-123">Indicates whether to display a percentage over the gradient.</span></span>|  
|`ShowValue`|<span data-ttu-id="45c53-124">指示是否在渐变上显示当前值。</span><span class="sxs-lookup"><span data-stu-id="45c53-124">Indicates whether to display the current value over the gradient.</span></span>|  
|`ShowGradient`|<span data-ttu-id="45c53-125">指示跟踪条是否应显示有当前值的颜色渐变。</span><span class="sxs-lookup"><span data-stu-id="45c53-125">Indicates whether the track bar should display a color gradient showing the current value.</span></span>|  
|-   `Value`|<span data-ttu-id="45c53-126">指定跟踪条的当前值。</span><span class="sxs-lookup"><span data-stu-id="45c53-126">Specifies the current value of the track bar.</span></span>|  
  
 <span data-ttu-id="45c53-127">下表显示了 `FlashTrackBar:` 定义的其他成员：property-changed 事件和引发该事件的方法。</span><span class="sxs-lookup"><span data-stu-id="45c53-127">The following table shows additional members defined by `FlashTrackBar:` the property-changed event and the method that raises the event.</span></span>  
  
|<span data-ttu-id="45c53-128">成员</span><span class="sxs-lookup"><span data-stu-id="45c53-128">Member</span></span>|<span data-ttu-id="45c53-129">描述</span><span class="sxs-lookup"><span data-stu-id="45c53-129">Description</span></span>|  
|------------|-----------------|  
|`ValueChanged`|<span data-ttu-id="45c53-130">当跟踪条的 `Value` 属性更改时引发的事件。</span><span class="sxs-lookup"><span data-stu-id="45c53-130">The event that is raised when the `Value` property of the track bar changes.</span></span>|  
|`OnValueChanged`|<span data-ttu-id="45c53-131">引发 `ValueChanged` 事件的方法。</span><span class="sxs-lookup"><span data-stu-id="45c53-131">The method that raises the `ValueChanged` event.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="45c53-132">`FlashTrackBar`使用类作为事件数据和<xref:System.EventHandler>事件委托。 <xref:System.EventArgs></span><span class="sxs-lookup"><span data-stu-id="45c53-132">`FlashTrackBar` uses the <xref:System.EventArgs> class for event data and <xref:System.EventHandler> for the event delegate.</span></span>  
  
 <span data-ttu-id="45c53-133">若要处理相应的*事件名称*事件, 请`FlashTrackBar`重写继承自<xref:System.Windows.Forms.Control?displayProperty=nameWithType>的以下方法:</span><span class="sxs-lookup"><span data-stu-id="45c53-133">To handle the corresponding *EventName* events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 <span data-ttu-id="45c53-134">若要处理相应的属性更改事件, `FlashTrackBar`将重写从<xref:System.Windows.Forms.Control?displayProperty=nameWithType>其继承的以下方法:</span><span class="sxs-lookup"><span data-stu-id="45c53-134">To handle the corresponding property-changed events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a><span data-ttu-id="45c53-135">示例</span><span class="sxs-lookup"><span data-stu-id="45c53-135">Example</span></span>  
 <span data-ttu-id="45c53-136">`FlashTrackBar` 控件定义了两个 UI 类型编辑器（`FlashTrackBarValueEditor` 和 `FlashTrackBarDarkenByEditor`），它们显示在以下代码列表中。</span><span class="sxs-lookup"><span data-stu-id="45c53-136">The `FlashTrackBar` control defines two UI type editors, `FlashTrackBarValueEditor` and `FlashTrackBarDarkenByEditor`, which are shown in the following code listings.</span></span> <span data-ttu-id="45c53-137">`HostApp` 类在 Windows 窗体上使用 `FlashTrackBar` 控件。</span><span class="sxs-lookup"><span data-stu-id="45c53-137">The `HostApp` class uses the `FlashTrackBar` control on a Windows Form.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="45c53-138">请参阅</span><span class="sxs-lookup"><span data-stu-id="45c53-138">See also</span></span>

- <span data-ttu-id="45c53-139">[扩展设计时支持](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="45c53-139">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- [<span data-ttu-id="45c53-140">Windows 窗体控件开发基础知识</span><span class="sxs-lookup"><span data-stu-id="45c53-140">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)
