---
title: 使用 TreeWalker 在 UI 自动化元素之间导航
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
ms.openlocfilehash: aed8c624a75364dcc97c73ae7ebd6331275ceff4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "61983237"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a><span data-ttu-id="0366a-102">使用 TreeWalker 在 UI 自动化元素之间导航</span><span class="sxs-lookup"><span data-stu-id="0366a-102">Navigate Among UI Automation Elements with TreeWalker</span></span>
> [!NOTE]
>  <span data-ttu-id="0366a-103">本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。</span><span class="sxs-lookup"><span data-stu-id="0366a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0366a-104">有关最新信息[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，请参阅[Windows 自动化 API:UI 自动化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="0366a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="0366a-105">本主题包含代码示例演示如何在中导航[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]元素使用<xref:System.Windows.Automation.TreeWalker>类。</span><span class="sxs-lookup"><span data-stu-id="0366a-105">This topic contains example code that shows how to navigate among [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements by using the <xref:System.Windows.Automation.TreeWalker> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0366a-106">示例</span><span class="sxs-lookup"><span data-stu-id="0366a-106">Example</span></span>  
 <span data-ttu-id="0366a-107">下面的示例使用<xref:System.Windows.Automation.TreeWalker.GetParent%2A>向上遍历[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]树，直到它找到的根元素或桌面。</span><span class="sxs-lookup"><span data-stu-id="0366a-107">The following example uses <xref:System.Windows.Automation.TreeWalker.GetParent%2A> to walk up the [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] tree until it finds the root element, or desktop.</span></span> <span data-ttu-id="0366a-108">正下方的元素是指定元素的父窗口。</span><span class="sxs-lookup"><span data-stu-id="0366a-108">The element just below that is the parent window of the specified element.</span></span>  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a><span data-ttu-id="0366a-109">示例</span><span class="sxs-lookup"><span data-stu-id="0366a-109">Example</span></span>  
 <span data-ttu-id="0366a-110">下面的示例使用<xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A>并<xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A>来创建<xref:System.Windows.Forms.TreeView>显示整个子树的[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]元素中的控件视图和启用的。</span><span class="sxs-lookup"><span data-stu-id="0366a-110">The following example uses <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> and <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> to create a <xref:System.Windows.Forms.TreeView> that shows an entire subtree of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements that are in the control view and that are enabled.</span></span>  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a><span data-ttu-id="0366a-111">请参阅</span><span class="sxs-lookup"><span data-stu-id="0366a-111">See also</span></span>

- [<span data-ttu-id="0366a-112">获取 UI 自动化元素</span><span class="sxs-lookup"><span data-stu-id="0366a-112">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
