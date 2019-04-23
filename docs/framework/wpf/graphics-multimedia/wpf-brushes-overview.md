---
title: WPF 画笔概述
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 14e3d095d50f41e5b20a79d76c464bcf28c99327
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132205"
---
# <a name="wpf-brushes-overview"></a><span data-ttu-id="a0e73-102">WPF 画笔概述</span><span class="sxs-lookup"><span data-stu-id="a0e73-102">WPF Brushes Overview</span></span>
<span data-ttu-id="a0e73-103">在屏幕上可见的所有内容是可见的因为它通过画笔绘制。</span><span class="sxs-lookup"><span data-stu-id="a0e73-103">Everything visible on your screen is visible because it was painted by a brush.</span></span> <span data-ttu-id="a0e73-104">例如，画笔用于描述背景的按钮、 文本、 前的景色和形状的填充。</span><span class="sxs-lookup"><span data-stu-id="a0e73-104">For example, a brush is used to describe the background of a button, the foreground of text, and the fill of a shape.</span></span> <span data-ttu-id="a0e73-105">本主题介绍的概念与绘制[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]画笔，并提供示例。</span><span class="sxs-lookup"><span data-stu-id="a0e73-105">This topic introduces the concepts of painting with [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] brushes and provides examples.</span></span> <span data-ttu-id="a0e73-106">借助画笔，可以利用任意内容（从简单的纯色到复杂的图案和图像集）绘制 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="a0e73-106">Brushes enable you to paint [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] objects with anything from simple, solid colors to complex sets of patterns and images.</span></span>  
  
<a name="paintingwithbrush"></a>   
## <a name="painting-with-a-brush"></a><span data-ttu-id="a0e73-107">使用画笔进行绘制</span><span class="sxs-lookup"><span data-stu-id="a0e73-107">Painting with a Brush</span></span>  
 <span data-ttu-id="a0e73-108">一个<xref:System.Windows.Media.Brush>"绘制"其输出区域。</span><span class="sxs-lookup"><span data-stu-id="a0e73-108">A <xref:System.Windows.Media.Brush> "paints" an area with its output.</span></span> <span data-ttu-id="a0e73-109">不同画笔具有不同类型的输出。</span><span class="sxs-lookup"><span data-stu-id="a0e73-109">Different brushes have different types of output.</span></span> <span data-ttu-id="a0e73-110">某些画笔绘制用纯色，其他人使用渐变、 模式、 图像或绘图区域。</span><span class="sxs-lookup"><span data-stu-id="a0e73-110">Some brushes paint an area with a solid color, others with a gradient, pattern, image, or drawing.</span></span> <span data-ttu-id="a0e73-111">下图显示了每个不同的示例<xref:System.Windows.Media.Brush>类型。</span><span class="sxs-lookup"><span data-stu-id="a0e73-111">The following illustration shows examples of each of the different <xref:System.Windows.Media.Brush> types.</span></span>  
  
 <span data-ttu-id="a0e73-112">![画笔类型](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")</span><span class="sxs-lookup"><span data-stu-id="a0e73-112">![Brush types](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")</span></span>  
<span data-ttu-id="a0e73-113">画笔示例</span><span class="sxs-lookup"><span data-stu-id="a0e73-113">Brush examples</span></span>  
  
 <span data-ttu-id="a0e73-114">大多数的视觉对象，可以指定绘制方式。</span><span class="sxs-lookup"><span data-stu-id="a0e73-114">Most visual objects enable you to specify how they are painted.</span></span> <span data-ttu-id="a0e73-115">下表列出了一些常见对象和属性可以使用<xref:System.Windows.Media.Brush>。</span><span class="sxs-lookup"><span data-stu-id="a0e73-115">The following table lists some common objects and properties with which you can use a <xref:System.Windows.Media.Brush>.</span></span>  
  
|<span data-ttu-id="a0e73-116">类</span><span class="sxs-lookup"><span data-stu-id="a0e73-116">Class</span></span>|<span data-ttu-id="a0e73-117">画笔属性</span><span class="sxs-lookup"><span data-stu-id="a0e73-117">Brush properties</span></span>|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<span data-ttu-id="a0e73-118"><xref:System.Windows.Controls.Border.BorderBrush%2A>， <xref:System.Windows.Controls.Border.Background%2A></span><span class="sxs-lookup"><span data-stu-id="a0e73-118"><xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A></span></span>|  
|<xref:System.Windows.Controls.Control>|<span data-ttu-id="a0e73-119"><xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A></span><span class="sxs-lookup"><span data-stu-id="a0e73-119"><xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A></span></span>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<span data-ttu-id="a0e73-120"><xref:System.Windows.Shapes.Shape.Fill%2A>， <xref:System.Windows.Shapes.Shape.Stroke%2A></span><span class="sxs-lookup"><span data-stu-id="a0e73-120"><xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A></span></span>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 <span data-ttu-id="a0e73-121">以下各节介绍了不同<xref:System.Windows.Media.Brush>类型，并提供每个示例。</span><span class="sxs-lookup"><span data-stu-id="a0e73-121">The following sections describe the different <xref:System.Windows.Media.Brush> types and provide an example of each.</span></span>  
  
<a name="paintwithsolidcolorbrush"></a>   
## <a name="paint-with-a-solid-color"></a><span data-ttu-id="a0e73-122">使用纯色进行绘制</span><span class="sxs-lookup"><span data-stu-id="a0e73-122">Paint with a Solid Color</span></span>  
 <span data-ttu-id="a0e73-123">一个<xref:System.Windows.Media.SolidColorBrush>使用纯色绘制区域<xref:System.Windows.Media.Color>。</span><span class="sxs-lookup"><span data-stu-id="a0e73-123">A <xref:System.Windows.Media.SolidColorBrush> paints an area with a solid <xref:System.Windows.Media.Color>.</span></span> <span data-ttu-id="a0e73-124">有多种方式来指定<xref:System.Windows.Media.SolidColorBrush.Color%2A>的<xref:System.Windows.Media.SolidColorBrush>： 例如，您可以指定其 alpha、 红色、 蓝色和绿色通道或使用提供的预定义的颜色之一<xref:System.Windows.Media.Colors>类。</span><span class="sxs-lookup"><span data-stu-id="a0e73-124">There are a variety of ways to specify the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush>: for example, you can specify its alpha, red, blue, and green channels or use one of the predefined color provided by the <xref:System.Windows.Media.Colors> class.</span></span>  
  
 <span data-ttu-id="a0e73-125">下面的示例使用<xref:System.Windows.Media.SolidColorBrush>绘制<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="a0e73-125">The following example uses a <xref:System.Windows.Media.SolidColorBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="a0e73-126">下图显示绘制的矩形。</span><span class="sxs-lookup"><span data-stu-id="a0e73-126">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="a0e73-127">![使用 SolidColorBrush 绘制的矩形](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="a0e73-127">![A rectangle painted using a SolidColorBrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")</span></span>  
<span data-ttu-id="a0e73-128">使用 SolidColorBrush 绘制的矩形</span><span class="sxs-lookup"><span data-stu-id="a0e73-128">A Rectangle painted using a SolidColorBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 <span data-ttu-id="a0e73-129">有关详细信息<xref:System.Windows.Media.SolidColorBrush>类，请参阅[使用纯色和渐变概述进行绘制](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e73-129">For more information about the <xref:System.Windows.Media.SolidColorBrush> class, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithlineargradientbrush"></a>   
## <a name="paint-with-a-linear-gradient"></a><span data-ttu-id="a0e73-130">使用线性渐变进行绘制</span><span class="sxs-lookup"><span data-stu-id="a0e73-130">Paint with a Linear Gradient</span></span>  
 <span data-ttu-id="a0e73-131">一个<xref:System.Windows.Media.LinearGradientBrush>绘制带有线性渐变的区域。</span><span class="sxs-lookup"><span data-stu-id="a0e73-131">A <xref:System.Windows.Media.LinearGradientBrush> paints an area with a linear gradient.</span></span> <span data-ttu-id="a0e73-132">线性渐变混合行，渐变轴跨两个或多个颜色。</span><span class="sxs-lookup"><span data-stu-id="a0e73-132">A linear gradient blends two or more colors across a line, the gradient axis.</span></span> <span data-ttu-id="a0e73-133">您使用<xref:System.Windows.Media.GradientStop>对象渐变和它们的位置中指定的颜色。</span><span class="sxs-lookup"><span data-stu-id="a0e73-133">You use <xref:System.Windows.Media.GradientStop> objects to specify the colors in the gradient and their positions.</span></span>  
  
 <span data-ttu-id="a0e73-134">下面的示例使用<xref:System.Windows.Media.LinearGradientBrush>绘制<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="a0e73-134">The following example uses a <xref:System.Windows.Media.LinearGradientBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="a0e73-135">下图显示绘制的矩形。</span><span class="sxs-lookup"><span data-stu-id="a0e73-135">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="a0e73-136">![使用 LinearGradientBrush 绘制的矩形](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")</span><span class="sxs-lookup"><span data-stu-id="a0e73-136">![A rectangle painted using a LinearGradientBrush](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")</span></span>  
<span data-ttu-id="a0e73-137">使用 LinearGradientBrush 绘制的矩形</span><span class="sxs-lookup"><span data-stu-id="a0e73-137">A Rectangle painted using a LinearGradientBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 <span data-ttu-id="a0e73-138">有关详细信息<xref:System.Windows.Media.LinearGradientBrush>类，请参阅[使用纯色和渐变概述进行绘制](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e73-138">For more information about the <xref:System.Windows.Media.LinearGradientBrush> class, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithradialgradientbrush"></a>   
## <a name="paint-with-a-radial-gradient"></a><span data-ttu-id="a0e73-139">使用径向渐变进行绘制</span><span class="sxs-lookup"><span data-stu-id="a0e73-139">Paint with a Radial Gradient</span></span>  
 <span data-ttu-id="a0e73-140">一个<xref:System.Windows.Media.RadialGradientBrush>使用径向渐变绘制区域。</span><span class="sxs-lookup"><span data-stu-id="a0e73-140">A <xref:System.Windows.Media.RadialGradientBrush> paints an area with a radial gradient.</span></span> <span data-ttu-id="a0e73-141">径向渐变混合跨一个圆圈的两个或多个颜色。</span><span class="sxs-lookup"><span data-stu-id="a0e73-141">A radial gradient blends two or more colors across a circle.</span></span> <span data-ttu-id="a0e73-142">如同<xref:System.Windows.Media.LinearGradientBrush>类，使用<xref:System.Windows.Media.GradientStop>对象渐变和它们的位置中指定的颜色。</span><span class="sxs-lookup"><span data-stu-id="a0e73-142">As with the <xref:System.Windows.Media.LinearGradientBrush> class, you use <xref:System.Windows.Media.GradientStop> objects to specify the colors in the gradient and their positions.</span></span>  
  
 <span data-ttu-id="a0e73-143">下面的示例使用<xref:System.Windows.Media.RadialGradientBrush>绘制<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="a0e73-143">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="a0e73-144">下图显示绘制的矩形。</span><span class="sxs-lookup"><span data-stu-id="a0e73-144">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="a0e73-145">![使用 RadialGradientBrush 绘制的矩形](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")</span><span class="sxs-lookup"><span data-stu-id="a0e73-145">![A rectangle painted using a RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")</span></span>  
<span data-ttu-id="a0e73-146">使用 RadialGradientBrush 绘制的矩形</span><span class="sxs-lookup"><span data-stu-id="a0e73-146">A Rectangle painted using a RadialGradientBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 <span data-ttu-id="a0e73-147">有关详细信息<xref:System.Windows.Media.RadialGradientBrush>类，请参阅[使用纯色和渐变概述进行绘制](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e73-147">For more information about the <xref:System.Windows.Media.RadialGradientBrush> class, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithimage"></a>   
## <a name="paint-with-an-image"></a><span data-ttu-id="a0e73-148">使用图像进行绘制</span><span class="sxs-lookup"><span data-stu-id="a0e73-148">Paint with an Image</span></span>  
 <span data-ttu-id="a0e73-149"><xref:System.Windows.Media.ImageBrush>使用绘制区域<xref:System.Windows.Media.ImageSource>。</span><span class="sxs-lookup"><span data-stu-id="a0e73-149">An <xref:System.Windows.Media.ImageBrush> paints an area with a <xref:System.Windows.Media.ImageSource>.</span></span>  
  
 <span data-ttu-id="a0e73-150">下面的示例使用<xref:System.Windows.Media.ImageBrush>绘制<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="a0e73-150">The following example uses an <xref:System.Windows.Media.ImageBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="a0e73-151">下图显示绘制的矩形。</span><span class="sxs-lookup"><span data-stu-id="a0e73-151">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="a0e73-152">![使用 imagebrush 绘制的矩形](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")</span><span class="sxs-lookup"><span data-stu-id="a0e73-152">![A Rectangle painted by an ImageBrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")</span></span>  
<span data-ttu-id="a0e73-153">使用图像绘制的矩形</span><span class="sxs-lookup"><span data-stu-id="a0e73-153">A Rectangle painted using a Image</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 <span data-ttu-id="a0e73-154">有关详细信息<xref:System.Windows.Media.ImageBrush>类，请参阅[使用图像、 绘图和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e73-154">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithdrawing"></a>   
## <a name="paint-with-a-drawing"></a><span data-ttu-id="a0e73-155">使用绘图进行绘制</span><span class="sxs-lookup"><span data-stu-id="a0e73-155">Paint with a Drawing</span></span>  
 <span data-ttu-id="a0e73-156">一个<xref:System.Windows.Media.DrawingBrush>使用绘制区域<xref:System.Windows.Media.Drawing>。</span><span class="sxs-lookup"><span data-stu-id="a0e73-156">A <xref:System.Windows.Media.DrawingBrush> paints an area with a <xref:System.Windows.Media.Drawing>.</span></span> <span data-ttu-id="a0e73-157">一个<xref:System.Windows.Media.Drawing>可以包含形状、 图像、 文本和媒体。</span><span class="sxs-lookup"><span data-stu-id="a0e73-157">A <xref:System.Windows.Media.Drawing> can contain shapes, images, text, and media.</span></span>  
  
 <span data-ttu-id="a0e73-158">下面的示例使用<xref:System.Windows.Media.DrawingBrush>绘制<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="a0e73-158">The following example uses a <xref:System.Windows.Media.DrawingBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="a0e73-159">下图显示绘制的矩形。</span><span class="sxs-lookup"><span data-stu-id="a0e73-159">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="a0e73-160">![使用 DrawingBrush 绘制的矩形](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")</span><span class="sxs-lookup"><span data-stu-id="a0e73-160">![A rectangle painted using a DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")</span></span>  
<span data-ttu-id="a0e73-161">使用 DrawingBrush 绘制的矩形</span><span class="sxs-lookup"><span data-stu-id="a0e73-161">A Rectangle painted using a DrawingBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 <span data-ttu-id="a0e73-162">有关详细信息<xref:System.Windows.Media.DrawingBrush>类，请参阅[使用图像、 绘图和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e73-162">For more information about the <xref:System.Windows.Media.DrawingBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithvisual"></a>   
## <a name="paint-with-a-visual"></a><span data-ttu-id="a0e73-163">使用视觉对象进行绘制</span><span class="sxs-lookup"><span data-stu-id="a0e73-163">Paint with a Visual</span></span>  
 <span data-ttu-id="a0e73-164">一个<xref:System.Windows.Media.VisualBrush>使用绘制区域<xref:System.Windows.Media.Visual>对象。</span><span class="sxs-lookup"><span data-stu-id="a0e73-164">A <xref:System.Windows.Media.VisualBrush> paints an area with a <xref:System.Windows.Media.Visual> object.</span></span> <span data-ttu-id="a0e73-165">视觉对象的示例包括<xref:System.Windows.Controls.Button>， <xref:System.Windows.Controls.Page>，和<xref:System.Windows.Controls.MediaElement>。</span><span class="sxs-lookup"><span data-stu-id="a0e73-165">Examples of Visual objects include <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>, and <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="a0e73-166">一个<xref:System.Windows.Media.VisualBrush>，还可以将内容从一部分到另一个区域，则应用程序是用于创建反射效果和放大屏幕的部分非常有用。</span><span class="sxs-lookup"><span data-stu-id="a0e73-166">A <xref:System.Windows.Media.VisualBrush> also enables you to project content from one portion of your application into another area; it's very useful for creating reflection effects and magnifying portions of the screen.</span></span>  
  
 <span data-ttu-id="a0e73-167">下面的示例使用<xref:System.Windows.Media.VisualBrush>绘制<xref:System.Windows.Shapes.Shape.Fill%2A>的<xref:System.Windows.Shapes.Rectangle>。</span><span class="sxs-lookup"><span data-stu-id="a0e73-167">The following example uses a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="a0e73-168">下图显示绘制的矩形。</span><span class="sxs-lookup"><span data-stu-id="a0e73-168">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="a0e73-169">![使用 VisualBrush 绘制的矩形](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")</span><span class="sxs-lookup"><span data-stu-id="a0e73-169">![A rectangle painted using a VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")</span></span>  
<span data-ttu-id="a0e73-170">使用 VisualBrush 绘制的矩形</span><span class="sxs-lookup"><span data-stu-id="a0e73-170">A Rectangle painted using a VisualBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 <span data-ttu-id="a0e73-171">有关详细信息<xref:System.Windows.Media.VisualBrush>类，请参阅[使用图像、 绘图和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e73-171">For more information about the <xref:System.Windows.Media.VisualBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>   
## <a name="paint-using-predefined-and-system-brushes"></a><span data-ttu-id="a0e73-172">使用预定义画笔和系统画笔进行绘制</span><span class="sxs-lookup"><span data-stu-id="a0e73-172">Paint using Predefined and System Brushes</span></span>  
 <span data-ttu-id="a0e73-173">为方便起见，Windows Presentation Foundation (WPF) 提供了一组预定义的系统画笔用于绘制对象。</span><span class="sxs-lookup"><span data-stu-id="a0e73-173">For convenience, Windows Presentation Foundation (WPF) provides a set of predefined and system brushes that you can use to paint objects.</span></span>  
  
-   <span data-ttu-id="a0e73-174">有关可用的预定义画笔的列表，请参阅<xref:System.Windows.Media.Brushes>类。</span><span class="sxs-lookup"><span data-stu-id="a0e73-174">For a list of available predefined brushes, see the <xref:System.Windows.Media.Brushes> class.</span></span> <span data-ttu-id="a0e73-175">有关演示如何使用预定义的画笔的示例，请参阅[使用纯色绘制区域](how-to-paint-an-area-with-a-solid-color.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e73-175">For an example showing how to use a predefined brush, see [Paint an Area with a Solid Color](how-to-paint-an-area-with-a-solid-color.md).</span></span>  
  
-   <span data-ttu-id="a0e73-176">有关可用的系统画笔的列表，请参阅<xref:System.Windows.SystemColors>类。</span><span class="sxs-lookup"><span data-stu-id="a0e73-176">For a list of available system brushes, see the <xref:System.Windows.SystemColors> class.</span></span> <span data-ttu-id="a0e73-177">有关示例，请参阅[使用系统画笔绘制区域](how-to-paint-an-area-with-a-system-brush.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e73-177">For an example, see [Paint an Area with a System Brush](how-to-paint-an-area-with-a-system-brush.md).</span></span>  
  
<a name="commonbrushfeatures"></a>   
## <a name="common-brush-features"></a><span data-ttu-id="a0e73-178">常见的画笔功能</span><span class="sxs-lookup"><span data-stu-id="a0e73-178">Common Brush Features</span></span>  
 <span data-ttu-id="a0e73-179"><xref:System.Windows.Media.Brush> 对象提供<xref:System.Windows.Media.Brush.Opacity%2A>属性，可用于使画笔显示为透明或部分透明。</span><span class="sxs-lookup"><span data-stu-id="a0e73-179"><xref:System.Windows.Media.Brush> objects provide an <xref:System.Windows.Media.Brush.Opacity%2A> property that can be used to make a brush transparent or partially transparent.</span></span> <span data-ttu-id="a0e73-180"><xref:System.Windows.Media.Brush.Opacity%2A>值为 0，则画笔完全透明，而<xref:System.Windows.Media.Brush.Opacity%2A>值为 1，则画笔完全不透明。</span><span class="sxs-lookup"><span data-stu-id="a0e73-180">An <xref:System.Windows.Media.Brush.Opacity%2A> value of 0 makes a brush completely transparent, while an <xref:System.Windows.Media.Brush.Opacity%2A> value of 1 makes a brush completely opaque.</span></span> <span data-ttu-id="a0e73-181">下面的示例使用<xref:System.Windows.Media.Brush.Opacity%2A>属性以使<xref:System.Windows.Media.SolidColorBrush>25%不透明。</span><span class="sxs-lookup"><span data-stu-id="a0e73-181">The following example uses the <xref:System.Windows.Media.Brush.Opacity%2A> property to make a <xref:System.Windows.Media.SolidColorBrush> 25 percent opaque.</span></span>  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 <span data-ttu-id="a0e73-182">如果画笔包含部分透明的颜色，颜色的不透明度值通过画笔的不透明度值相乘相结合。</span><span class="sxs-lookup"><span data-stu-id="a0e73-182">If the brush contains colors that are partially transparent, the opacity value of the color is combined through multiplication with the opacity value of the brush.</span></span> <span data-ttu-id="a0e73-183">例如，如果画笔的不透明度值 0.5 和画笔中使用的颜色还具有 0.5 的不透明度值，输出颜色具有 0.25 的不透明度值。</span><span class="sxs-lookup"><span data-stu-id="a0e73-183">For example, if a brush has an opacity value of 0.5 and a color used in the brush also has an opacity value of 0.5, the output color has an opacity value of 0.25.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0e73-184">若要更改一个画笔的不透明度值更改整个元素使用的不透明度比效率更高其<xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType>属性。</span><span class="sxs-lookup"><span data-stu-id="a0e73-184">It's more efficient to change the opacity value of a brush than it is to change the opacity of an entire element using its <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="a0e73-185">可以旋转、 缩放、 倾斜和转换画笔的内容通过使用其<xref:System.Windows.Media.Brush.Transform%2A>或<xref:System.Windows.Media.Brush.RelativeTransform%2A>属性。</span><span class="sxs-lookup"><span data-stu-id="a0e73-185">You can rotate, scale, skew, and translate a brush's content by using its <xref:System.Windows.Media.Brush.Transform%2A> or <xref:System.Windows.Media.Brush.RelativeTransform%2A> properties.</span></span> <span data-ttu-id="a0e73-186">有关详细信息，请参阅[画笔转换概述](brush-transformation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e73-186">For more information, see [Brush Transformation Overview](brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="a0e73-187">因为它们<xref:System.Windows.Media.Animation.Animatable>对象，<xref:System.Windows.Media.Brush>对象可进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="a0e73-187">Because they are <xref:System.Windows.Media.Animation.Animatable> objects, <xref:System.Windows.Media.Brush> objects can be animated.</span></span> <span data-ttu-id="a0e73-188">有关详细信息，请参阅 [动画概述](animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e73-188">For more information, see [Animation Overview](animation-overview.md).</span></span>  
  
<a name="freezable_features"></a>   
### <a name="freezable-features"></a><span data-ttu-id="a0e73-189">Freezable 功能</span><span class="sxs-lookup"><span data-stu-id="a0e73-189">Freezable Features</span></span>  
 <span data-ttu-id="a0e73-190">因为它继承自<xref:System.Windows.Freezable>类，<xref:System.Windows.Media.Brush>类提供多种特殊功能：<xref:System.Windows.Media.Brush>对象可声明为[资源](../advanced/xaml-resources.md)、 在多个对象之间共享和克隆。</span><span class="sxs-lookup"><span data-stu-id="a0e73-190">Because it inherits from the <xref:System.Windows.Freezable> class, the <xref:System.Windows.Media.Brush> class provides several special features: <xref:System.Windows.Media.Brush> objects can be declared as [resources](../advanced/xaml-resources.md), shared among multiple objects, and cloned.</span></span> <span data-ttu-id="a0e73-191">此外，所有<xref:System.Windows.Media.Brush>除类型<xref:System.Windows.Media.VisualBrush>可以变为只读以提高性能并变为线程安全。</span><span class="sxs-lookup"><span data-stu-id="a0e73-191">In addition, all the <xref:System.Windows.Media.Brush> types except <xref:System.Windows.Media.VisualBrush> can be made read-only to improve performance and made thread-safe.</span></span>  
  
 <span data-ttu-id="a0e73-192">有关所提供的不同功能的详细信息<xref:System.Windows.Freezable>对象，请参阅[Freezable 对象概述](../advanced/freezable-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="a0e73-192">For more information about the different features provided by <xref:System.Windows.Freezable> objects, see [Freezable Objects Overview](../advanced/freezable-objects-overview.md).</span></span>  
  
 <span data-ttu-id="a0e73-193">有关原因的详细信息<xref:System.Windows.Media.VisualBrush>对象不能为冻结，请参阅<xref:System.Windows.Media.VisualBrush>类型页。</span><span class="sxs-lookup"><span data-stu-id="a0e73-193">For more information on why <xref:System.Windows.Media.VisualBrush> objects cannot be frozen, see the <xref:System.Windows.Media.VisualBrush> type page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0e73-194">请参阅</span><span class="sxs-lookup"><span data-stu-id="a0e73-194">See also</span></span>

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [<span data-ttu-id="a0e73-195">使用纯色和渐变进行绘制概述</span><span class="sxs-lookup"><span data-stu-id="a0e73-195">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="a0e73-196">使用图像、绘图和视觉对象进行绘制</span><span class="sxs-lookup"><span data-stu-id="a0e73-196">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="a0e73-197">Freezable 对象概述</span><span class="sxs-lookup"><span data-stu-id="a0e73-197">Freezable Objects Overview</span></span>](../advanced/freezable-objects-overview.md)
- [<span data-ttu-id="a0e73-198">画笔示例</span><span class="sxs-lookup"><span data-stu-id="a0e73-198">Brushes Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159973)
- [<span data-ttu-id="a0e73-199">ImageBrush 示例</span><span class="sxs-lookup"><span data-stu-id="a0e73-199">ImageBrush Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160005)
- [<span data-ttu-id="a0e73-200">VisualBrush 示例</span><span class="sxs-lookup"><span data-stu-id="a0e73-200">VisualBrush Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160049)
- [<span data-ttu-id="a0e73-201">帮助主题</span><span class="sxs-lookup"><span data-stu-id="a0e73-201">How-to Topics</span></span>](brushes-how-to-topics.md)
- [<span data-ttu-id="a0e73-202">其他性能建议</span><span class="sxs-lookup"><span data-stu-id="a0e73-202">Other Performance Recommendations</span></span>](../advanced/optimizing-performance-other-recommendations.md)
