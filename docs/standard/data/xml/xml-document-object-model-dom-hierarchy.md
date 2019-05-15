---
title: XML 文档对象模型 (DOM) 层次结构
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 79078b16f0d56c40a3dcfeabaaed9b5cbb7753a0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64589828"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="01ed9-102">XML 文档对象模型 (DOM) 层次结构</span><span class="sxs-lookup"><span data-stu-id="01ed9-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="01ed9-103">下图显示了 XML 文档对象模型 (DOM) 的类层次结构，其中万维网联合会 (W3C) 名称用括号括起来，另外还有相关的类名。</span><span class="sxs-lookup"><span data-stu-id="01ed9-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="01ed9-104">![XML 文档对象模型 &#40;DOM&#41; 层次结构](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="01ed9-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="01ed9-105">XML 文档对象模型 (DOM) 层次结构</span><span class="sxs-lookup"><span data-stu-id="01ed9-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="01ed9-106">下列类不继承自 XmlNode：</span><span class="sxs-lookup"><span data-stu-id="01ed9-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
- <span data-ttu-id="01ed9-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="01ed9-107">**XmlImplementation**</span></span>  
  
- <span data-ttu-id="01ed9-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="01ed9-108">**XmlNamedNodeMap**</span></span>  
  
- <span data-ttu-id="01ed9-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="01ed9-109">**XmlNodeList**</span></span>  
  
- <span data-ttu-id="01ed9-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="01ed9-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="01ed9-111">XmlImplementation 类用于创建 XML 文档。</span><span class="sxs-lookup"><span data-stu-id="01ed9-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="01ed9-112">有关详细信息，请参阅 [XML 文档创建](../../../../docs/standard/data/xml/xml-document-creation.md)。</span><span class="sxs-lookup"><span data-stu-id="01ed9-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="01ed9-113">XmlNamedNodeMap 类处理无序节点集。</span><span class="sxs-lookup"><span data-stu-id="01ed9-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="01ed9-114">有关详细信息，请参阅[按名称或索引检索无序节点](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md)。</span><span class="sxs-lookup"><span data-stu-id="01ed9-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="01ed9-115">XmlNodeList 类处理有序节点列表。</span><span class="sxs-lookup"><span data-stu-id="01ed9-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="01ed9-116">有关详细信息，请参阅[按索引检索有序节点](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md)。</span><span class="sxs-lookup"><span data-stu-id="01ed9-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="01ed9-117">XmlNodeChangedEventArgs 类处理在 XmlDocument 上注册的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="01ed9-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="01ed9-118">有关详细信息，请参阅[使用 XmlNodeChangedEventArgs 在 XML 文档中处理事件](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)。</span><span class="sxs-lookup"><span data-stu-id="01ed9-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="01ed9-119">XmlLinkedNode 类继承自 XmlNode。</span><span class="sxs-lookup"><span data-stu-id="01ed9-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="01ed9-120">它用于重写 XmlNode 中的两个方法：PreviousSibling 和 NextSibling 方法。</span><span class="sxs-lookup"><span data-stu-id="01ed9-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="01ed9-121">然后，这些重写方法由包含上一个和下一个同级的类 XmlCharacterData、XmlDeclaration、XmlDocumentType、XmlElement、XmlEntityReference 和 XmlProcessingInstruction 继承和使用。</span><span class="sxs-lookup"><span data-stu-id="01ed9-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01ed9-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="01ed9-122">See also</span></span>

- [<span data-ttu-id="01ed9-123">XML 文档对象模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="01ed9-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
