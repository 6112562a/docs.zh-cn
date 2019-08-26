---
title: 使用 XPathNavigator 匹配节点
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882e92c6c8cb6e638ca299ed4c43b9da8f4bf235
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923326"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="da308-102">使用 XPathNavigator 匹配节点</span><span class="sxs-lookup"><span data-stu-id="da308-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="da308-103"><xref:System.Xml.XPath.XPathNavigator> 类提供了 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法来确定节点是否与 XPath 表达式匹配。</span><span class="sxs-lookup"><span data-stu-id="da308-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="da308-104"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法使用 XPath 表达式作为输入并返回一个 <xref:System.Boolean>，指示当前节点是否与给定的 XPath 表达式或给定的已编译 <xref:System.Xml.XPath.XPathExpression> 对象匹配。</span><span class="sxs-lookup"><span data-stu-id="da308-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="da308-105">匹配节点</span><span class="sxs-lookup"><span data-stu-id="da308-105">Matching Nodes</span></span>  
 <span data-ttu-id="da308-106">如果当前节点与指定的 XPath 表达式匹配，<xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法将返回 `true`。</span><span class="sxs-lookup"><span data-stu-id="da308-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="da308-107">例如，在以下代码示例中，如果当前节点为元素 <xref:System.Xml.XPath.XPathNavigator.Matches%2A>，并且元素 `true` 具有属性 `b`，`b` 方法将返回 `c`。</span><span class="sxs-lookup"><span data-stu-id="da308-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da308-108"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> 方法不会改变 <xref:System.Xml.XPath.XPathNavigator> 的状态。</span><span class="sxs-lookup"><span data-stu-id="da308-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a><span data-ttu-id="da308-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="da308-109">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="da308-110">使用 XPath 数据模型处理 XML 数据</span><span class="sxs-lookup"><span data-stu-id="da308-110">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="da308-111">使用 XPathNavigator 选择 XML 数据</span><span class="sxs-lookup"><span data-stu-id="da308-111">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="da308-112">使用 XPathNavigator 计算 XPath 表达式</span><span class="sxs-lookup"><span data-stu-id="da308-112">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="da308-113">XPath 查询识别的节点类型</span><span class="sxs-lookup"><span data-stu-id="da308-113">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="da308-114">XPath 查询和命名空间</span><span class="sxs-lookup"><span data-stu-id="da308-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="da308-115">已编译的 XPath 表达式</span><span class="sxs-lookup"><span data-stu-id="da308-115">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
