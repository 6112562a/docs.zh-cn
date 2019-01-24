---
title: 使用 Glyphs 绘制文本
ms.date: 03/30/2017
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
ms.openlocfilehash: 7c7c4946d2c5cc2aa9001cf119b969dd375a1050
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680239"
---
# <a name="draw-text-using-glyphs"></a><span data-ttu-id="6087e-102">使用 Glyphs 绘制文本</span><span class="sxs-lookup"><span data-stu-id="6087e-102">Draw Text Using Glyphs</span></span>
<span data-ttu-id="6087e-103">本主题说明如何使用低级<xref:System.Windows.Documents.Glyphs>对象中显示的文本[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6087e-103">This topic explains how to use the low-level <xref:System.Windows.Documents.Glyphs> object to display text in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="6087e-104">示例</span><span class="sxs-lookup"><span data-stu-id="6087e-104">Example</span></span>  
 <span data-ttu-id="6087e-105">以下示例演示如何定义的属性<xref:System.Windows.Documents.Glyphs>对象中[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6087e-105">The following examples show how to define properties for a <xref:System.Windows.Documents.Glyphs> object in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="6087e-106"><xref:System.Windows.Documents.Glyphs>对象表示的输出<xref:System.Windows.Media.GlyphRun>中[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6087e-106">The <xref:System.Windows.Documents.Glyphs> object represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="6087e-107">示例假定本地计算机上的 C:\WINDOWS\Fonts 文件夹中安装了 Arial、Courier New 和 Times New Roman 字体。</span><span class="sxs-lookup"><span data-stu-id="6087e-107">The examples assume that the Arial, Courier New, and Times New Roman fonts are installed in the C:\WINDOWS\Fonts folder on the local computer.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="6087e-108">此示例演示如何定义的其他属性<xref:System.Windows.Documents.Glyphs>中的对象[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6087e-108">This example shows how to define other properties of <xref:System.Windows.Documents.Glyphs> objects in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6087e-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="6087e-109">See also</span></span>
- [<span data-ttu-id="6087e-110">WPF 中的版式</span><span class="sxs-lookup"><span data-stu-id="6087e-110">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
