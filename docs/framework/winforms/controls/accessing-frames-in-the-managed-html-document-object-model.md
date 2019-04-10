---
title: 在托管 HTML 文档对象模型中访问框架
ms.date: 03/30/2017
helpviewer_keywords:
- HTML [Windows Forms], dOM
- managed HTML DOM
- HTML [Windows Forms], managed
- HTML DOM [Windows Forms], managed
- frames [Windows Forms], accessing
- DOM [Windows Forms], accessing frames in managed HTML
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
ms.openlocfilehash: 9b2719ca000ab86b9ca40f9e78af46cbf598d16e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337625"
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a><span data-ttu-id="12528-102">在托管 HTML 文档对象模型中访问框架</span><span class="sxs-lookup"><span data-stu-id="12528-102">Accessing Frames in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="12528-103">一些 HTML 文档组成共*帧*，或可以存放其自己独特的 HTML 文档的 windows。</span><span class="sxs-lookup"><span data-stu-id="12528-103">Some HTML documents are composed out of *frames*, or windows that can hold their own distinct HTML documents.</span></span> <span data-ttu-id="12528-104">使用框架可以轻松地创建 HTML 页面，页面中的一个或多个部分（如导航栏）保持静态，而其它框架则不断更改内容。</span><span class="sxs-lookup"><span data-stu-id="12528-104">Using frames makes it easy to create HTML pages in which one or more pieces of the page remain static, such as a navigation bar, while other frames constantly change their content.</span></span>  
  
 <span data-ttu-id="12528-105">HTML 作者可通过以下两种方式之一创建框架：</span><span class="sxs-lookup"><span data-stu-id="12528-105">HTML authors can create frames in one of two ways:</span></span>  
  
-   <span data-ttu-id="12528-106">使用 `FRAMESET` 和 `FRAME` 标记，创建固定窗口。</span><span class="sxs-lookup"><span data-stu-id="12528-106">Using the `FRAMESET` and `FRAME` tags, which create fixed windows.</span></span>  
  
 <span data-ttu-id="12528-107">或</span><span class="sxs-lookup"><span data-stu-id="12528-107">-or-</span></span>  
  
-   <span data-ttu-id="12528-108">使用 `IFRAME` 标记，创建一个可以在运行时重新定位的浮动窗口。</span><span class="sxs-lookup"><span data-stu-id="12528-108">Using the `IFRAME` tag, which creates a floating window that can be repositioned at run time.</span></span>  
  
1. <span data-ttu-id="12528-109">由于框架包含 HTML 文档，所以它们在文档对象模型 (DOM) 中表示为窗口元素和框架元素。</span><span class="sxs-lookup"><span data-stu-id="12528-109">Because frames contain HTML documents, they are represented in the Document Object Model (DOM) as both window elements and frame elements.</span></span>  
  
2. <span data-ttu-id="12528-110">通过使用 <xref:System.Windows.Forms.HtmlWindow> 的框架集合访问 `FRAME` 或 `IFRAME` 标记时，就是在检索与该框架对应的窗口元素。</span><span class="sxs-lookup"><span data-stu-id="12528-110">When you access a `FRAME` or `IFRAME` tag by using the Frames collection of <xref:System.Windows.Forms.HtmlWindow>, you are retrieving the window element corresponding to the frame.</span></span> <span data-ttu-id="12528-111">这表示框架的所有动态属性，如框架的当前 URL、文档和大小。</span><span class="sxs-lookup"><span data-stu-id="12528-111">This represents all of the frame's dynamic properties, such as its current URL, document, and size.</span></span>  
  
3. <span data-ttu-id="12528-112">通过使用 <xref:System.Windows.Forms.HtmlWindow> 的 <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> 属性、<xref:System.Windows.Forms.HtmlElement.Children%2A> 集合或者诸如 <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> 或 <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> 等方法访问 `FRAME` 或 `IFRAME` 标记时，就是在检索框架元素。</span><span class="sxs-lookup"><span data-stu-id="12528-112">When you access a `FRAME` or `IFRAME` tag by using the <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> property of <xref:System.Windows.Forms.HtmlWindow>, the <xref:System.Windows.Forms.HtmlElement.Children%2A> collection, or methods such as <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> or <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, you are retrieving the frame element.</span></span> <span data-ttu-id="12528-113">这表示框架的静态属性，包括原始 HTML 文件中指定的 URL。</span><span class="sxs-lookup"><span data-stu-id="12528-113">This represents the static properties of the frame, including the URL specified in the original HTML file.</span></span>  
  
## <a name="frames-and-security"></a><span data-ttu-id="12528-114">框架和安全性</span><span class="sxs-lookup"><span data-stu-id="12528-114">Frames and Security</span></span>  
 <span data-ttu-id="12528-115">对框架的访问复杂，因为托管的 HTML DOM 实现称为一种安全措施*跨框架脚本安全*。</span><span class="sxs-lookup"><span data-stu-id="12528-115">Access to frames is complicated by the fact that the managed HTML DOM implements a security measure known as *cross-frame scripting security*.</span></span> <span data-ttu-id="12528-116">如果文档包含在不同域中具有两个或多个 `FRAME` 的 `FRAMESET`，则这些 `FRAME` 相互之间不能交互。</span><span class="sxs-lookup"><span data-stu-id="12528-116">If a document contains a `FRAMESET` with two or more `FRAME`s in different domains, these `FRAME`s cannot interact with one another.</span></span> <span data-ttu-id="12528-117">换而言之，`FRAME`网站上的显示内容不能访问中的信息`FRAME`如承载第三方站点的`http://www.adatum.com/`。</span><span class="sxs-lookup"><span data-stu-id="12528-117">In other words, a `FRAME` that displays content from your Web site cannot access information in a `FRAME` that hosts a third-party site such as `http://www.adatum.com/`.</span></span> <span data-ttu-id="12528-118">在 <xref:System.Windows.Forms.HtmlWindow> 类级别实现此安全。</span><span class="sxs-lookup"><span data-stu-id="12528-118">This security is implemented at the level of the <xref:System.Windows.Forms.HtmlWindow> class.</span></span> <span data-ttu-id="12528-119">可以获取有关托管另一个网站的 `FRAME` 的常规信息（如其 URL），但不能访问其 <xref:System.Windows.Forms.HtmlWindow.Document%2A> 或更改其宿主 `FRAME` 或 `IFRAME` 的大小或位置。</span><span class="sxs-lookup"><span data-stu-id="12528-119">You can obtain general information about a `FRAME` hosting another Web site, such as its URL, but you will be unable to access its <xref:System.Windows.Forms.HtmlWindow.Document%2A> or change the size or location of its hosting `FRAME` or `IFRAME`.</span></span>  
  
 <span data-ttu-id="12528-120">此规则也适用于使用 <xref:System.Windows.Forms.HtmlWindow.Open%2A> 和 <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> 方法打开的窗口。</span><span class="sxs-lookup"><span data-stu-id="12528-120">This rule also applies to windows that you open using the <xref:System.Windows.Forms.HtmlWindow.Open%2A> and <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> methods.</span></span> <span data-ttu-id="12528-121">如果打开的窗口位于与 <xref:System.Windows.Forms.WebBrowser> 控件中托管的页面不同的域中，则你将不能移动该窗口或检查其内容。</span><span class="sxs-lookup"><span data-stu-id="12528-121">If the window you open is in a different domain from the page hosted in the <xref:System.Windows.Forms.WebBrowser> control, you will not be able to move that window or examine its contents.</span></span> <span data-ttu-id="12528-122">如果使用 <xref:System.Windows.Forms.WebBrowser> 控件来显示与用于部署基于 Windows 窗体的应用程序的网站不同的网站，也会强制这些限制。</span><span class="sxs-lookup"><span data-stu-id="12528-122">These restrictions are also enforced if you use the <xref:System.Windows.Forms.WebBrowser> control to display a Web site that is different from the Web site used to deploy your Windows Forms-based application.</span></span> <span data-ttu-id="12528-123">如果使用 [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] 部署技术来安装来自网站 A 的应用程序，并且使用 <xref:System.Windows.Forms.WebBrowser> 来显示网站 B，将不能访问网站 B 的数据。</span><span class="sxs-lookup"><span data-stu-id="12528-123">If you use [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] deployment technology to install your application from Web site A, and you use the <xref:System.Windows.Forms.WebBrowser> to display Web site B, you will not be able to access Web site B's data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12528-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="12528-124">See also</span></span>

- [<span data-ttu-id="12528-125">\<帧 > 元素</span><span class="sxs-lookup"><span data-stu-id="12528-125">\<frame> element</span></span>](https://developer.mozilla.org/docs/Web/HTML/Element/frame)
- [<span data-ttu-id="12528-126">使用托管 HTML 文档对象模型</span><span class="sxs-lookup"><span data-stu-id="12528-126">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
