---
title: 修改元素、 属性和 XML Tree1 中的节点
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: d548e6f5912437e5c5df27f55fcdb28990e92c8d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814895"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="e0b83-102">修改 XML 树中的元素、特性和节点</span><span class="sxs-lookup"><span data-stu-id="e0b83-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="e0b83-103">下表汇总了修改元素、元素的子元素或元素属性 (Attribute) 时可以使用的方法和属性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="e0b83-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="e0b83-104">下面的方法修改 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="e0b83-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="e0b83-105">方法</span><span class="sxs-lookup"><span data-stu-id="e0b83-105">Method</span></span>|<span data-ttu-id="e0b83-106">描述</span><span class="sxs-lookup"><span data-stu-id="e0b83-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="e0b83-107">用已分析的 XML 替换元素。</span><span class="sxs-lookup"><span data-stu-id="e0b83-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="e0b83-108">移除元素的所有内容（子节点和属性）。</span><span class="sxs-lookup"><span data-stu-id="e0b83-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="e0b83-109">移除元素的属性。</span><span class="sxs-lookup"><span data-stu-id="e0b83-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="e0b83-110">替换元素的所有内容（子节点和属性）。</span><span class="sxs-lookup"><span data-stu-id="e0b83-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="e0b83-111">替换元素的属性。</span><span class="sxs-lookup"><span data-stu-id="e0b83-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="e0b83-112">设置属性的值。</span><span class="sxs-lookup"><span data-stu-id="e0b83-112">Sets the value of an attribute.</span></span> <span data-ttu-id="e0b83-113">如果该属性不存在，则创建该属性。</span><span class="sxs-lookup"><span data-stu-id="e0b83-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="e0b83-114">如果值设置为 `null`，则移除该属性。</span><span class="sxs-lookup"><span data-stu-id="e0b83-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="e0b83-115">设置子元素的值。</span><span class="sxs-lookup"><span data-stu-id="e0b83-115">Sets the value of a child element.</span></span> <span data-ttu-id="e0b83-116">如果该元素不存在，则创建该元素。</span><span class="sxs-lookup"><span data-stu-id="e0b83-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="e0b83-117">如果值设置为 `null`，则移除该元素。</span><span class="sxs-lookup"><span data-stu-id="e0b83-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="e0b83-118">用指定的文本替换元素的内容（子节点）。</span><span class="sxs-lookup"><span data-stu-id="e0b83-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="e0b83-119">设置元素的值。</span><span class="sxs-lookup"><span data-stu-id="e0b83-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="e0b83-120">下面的方法修改 <xref:System.Xml.Linq.XAttribute>。</span><span class="sxs-lookup"><span data-stu-id="e0b83-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="e0b83-121">方法</span><span class="sxs-lookup"><span data-stu-id="e0b83-121">Method</span></span>|<span data-ttu-id="e0b83-122">描述</span><span class="sxs-lookup"><span data-stu-id="e0b83-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="e0b83-123">设置属性的值。</span><span class="sxs-lookup"><span data-stu-id="e0b83-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="e0b83-124">设置属性的值。</span><span class="sxs-lookup"><span data-stu-id="e0b83-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="e0b83-125">下面的方法修改 <xref:System.Xml.Linq.XNode>（包括 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>）。</span><span class="sxs-lookup"><span data-stu-id="e0b83-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="e0b83-126">方法</span><span class="sxs-lookup"><span data-stu-id="e0b83-126">Method</span></span>|<span data-ttu-id="e0b83-127">描述</span><span class="sxs-lookup"><span data-stu-id="e0b83-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="e0b83-128">用新内容替换节点。</span><span class="sxs-lookup"><span data-stu-id="e0b83-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="e0b83-129">下面的方法修改 <xref:System.Xml.Linq.XContainer>（<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>）。</span><span class="sxs-lookup"><span data-stu-id="e0b83-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="e0b83-130">方法</span><span class="sxs-lookup"><span data-stu-id="e0b83-130">Method</span></span>|<span data-ttu-id="e0b83-131">描述</span><span class="sxs-lookup"><span data-stu-id="e0b83-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="e0b83-132">用新内容替换子节点。</span><span class="sxs-lookup"><span data-stu-id="e0b83-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0b83-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="e0b83-133">See also</span></span>

- [<span data-ttu-id="e0b83-134">修改 XML 树 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0b83-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
