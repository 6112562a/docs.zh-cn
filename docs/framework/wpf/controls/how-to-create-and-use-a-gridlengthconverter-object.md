---
title: 如何：创建和使用 GridLengthConverter 对象
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
ms.openlocfilehash: b5ab15df4aaf5f6c4ba7bc7a4b36cc5e122b1320
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562047"
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a><span data-ttu-id="891e8-102">如何：创建和使用 GridLengthConverter 对象</span><span class="sxs-lookup"><span data-stu-id="891e8-102">How to: Create and Use a GridLengthConverter Object</span></span>
## <a name="example"></a><span data-ttu-id="891e8-103">示例</span><span class="sxs-lookup"><span data-stu-id="891e8-103">Example</span></span>  
 <span data-ttu-id="891e8-104">下面的示例演示如何创建和使用的实例<xref:System.Windows.GridLengthConverter>。</span><span class="sxs-lookup"><span data-stu-id="891e8-104">The following example shows how to create and use an instance of <xref:System.Windows.GridLengthConverter>.</span></span> <span data-ttu-id="891e8-105">该示例定义一个名为的自定义方法`changeCol`，哪些阶段<xref:System.Windows.Controls.ListBoxItem>到<xref:System.Windows.GridLengthConverter>用于将转换<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的实例<xref:System.Windows.GridLength>。</span><span class="sxs-lookup"><span data-stu-id="891e8-105">The example defines a custom method called `changeCol`, which passes the <xref:System.Windows.Controls.ListBoxItem> to a <xref:System.Windows.GridLengthConverter> that converts the <xref:System.Windows.Controls.ContentControl.Content%2A> of a <xref:System.Windows.Controls.ListBoxItem> to an instance of <xref:System.Windows.GridLength>.</span></span> <span data-ttu-id="891e8-106">转换后的值然后返回作为值传递<xref:System.Windows.Controls.ColumnDefinition.Width%2A>属性的<xref:System.Windows.Controls.ColumnDefinition>元素。</span><span class="sxs-lookup"><span data-stu-id="891e8-106">The converted value is then passed back as the value of the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> property of the <xref:System.Windows.Controls.ColumnDefinition> element.</span></span>  
  
 <span data-ttu-id="891e8-107">该示例还定义第二个自定义方法，称为`changeColVal`。</span><span class="sxs-lookup"><span data-stu-id="891e8-107">The example also defines a second custom method, called `changeColVal`.</span></span> <span data-ttu-id="891e8-108">此自定义方法将转换<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A>的<xref:System.Windows.Controls.Slider>到<xref:System.String>，然后将值改回<xref:System.Windows.Controls.ColumnDefinition>作为<xref:System.Windows.Controls.ColumnDefinition.Width%2A>的元素。</span><span class="sxs-lookup"><span data-stu-id="891e8-108">This custom method converts the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> of a <xref:System.Windows.Controls.Slider> to a <xref:System.String> and then passes that value back to the <xref:System.Windows.Controls.ColumnDefinition> as the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the element.</span></span>  
  
 <span data-ttu-id="891e8-109">请注意，单独[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]文件定义的内容<xref:System.Windows.Controls.ListBoxItem>。</span><span class="sxs-lookup"><span data-stu-id="891e8-109">Note that a separate [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file defines the contents of a <xref:System.Windows.Controls.ListBoxItem>.</span></span>  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="891e8-110">请参阅</span><span class="sxs-lookup"><span data-stu-id="891e8-110">See also</span></span>
- <xref:System.Windows.GridLengthConverter>
- <xref:System.Windows.GridLength>
