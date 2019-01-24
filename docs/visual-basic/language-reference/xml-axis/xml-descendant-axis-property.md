---
title: XML 后代轴属性 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 3b8d13e606f28896cae88162d572470e49af3739
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730277"
---
# <a name="xml-descendant-axis-property-visual-basic"></a><span data-ttu-id="ed7d9-102">XML 后代轴属性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed7d9-102">XML Descendant Axis Property (Visual Basic)</span></span>
<span data-ttu-id="ed7d9-103">提供对以下的后代的访问：<xref:System.Xml.Linq.XElement>对象，<xref:System.Xml.Linq.XDocument>对象、 一系列<xref:System.Xml.Linq.XElement>对象或一系列<xref:System.Xml.Linq.XDocument>对象。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-103">Provides access to the descendants of the following: an <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed7d9-104">语法</span><span class="sxs-lookup"><span data-stu-id="ed7d9-104">Syntax</span></span>  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a><span data-ttu-id="ed7d9-105">部件</span><span class="sxs-lookup"><span data-stu-id="ed7d9-105">Parts</span></span>  
 `object`  
 <span data-ttu-id="ed7d9-106">必需。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-106">Required.</span></span> <span data-ttu-id="ed7d9-107"><xref:System.Xml.Linq.XElement> 对象、<xref:System.Xml.Linq.XDocument> 对象、<xref:System.Xml.Linq.XElement> 对象的集合或 <xref:System.Xml.Linq.XDocument> 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-107">An <xref:System.Xml.Linq.XElement> object, an <xref:System.Xml.Linq.XDocument> object, a collection of <xref:System.Xml.Linq.XElement> objects, or a collection of <xref:System.Xml.Linq.XDocument> objects.</span></span>  
  
 <span data-ttu-id="ed7d9-108">...<</span><span class="sxs-lookup"><span data-stu-id="ed7d9-108">...<</span></span>  
 <span data-ttu-id="ed7d9-109">必需。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-109">Required.</span></span> <span data-ttu-id="ed7d9-110">表示子代轴属性的开头。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-110">Denotes the start of a descendant axis property.</span></span>  
  
 `descendant`  
 <span data-ttu-id="ed7d9-111">必需。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-111">Required.</span></span> <span data-ttu-id="ed7d9-112">若要访问，窗体的子代节点的名称 [`prefix``:`]`name`。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-112">Name of the descendant nodes to access, of the form [`prefix``:`]`name`.</span></span>  
  
|<span data-ttu-id="ed7d9-113">部件</span><span class="sxs-lookup"><span data-stu-id="ed7d9-113">Part</span></span>|<span data-ttu-id="ed7d9-114">描述</span><span class="sxs-lookup"><span data-stu-id="ed7d9-114">Description</span></span>|  
|----------|-----------------|  
|`prefix`|<span data-ttu-id="ed7d9-115">可选。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-115">Optional.</span></span> <span data-ttu-id="ed7d9-116">子代节点的 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-116">XML namespace prefix for the descendant node.</span></span> <span data-ttu-id="ed7d9-117">必须使用定义的全局 XML 命名空间`Imports`语句。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-117">Must be a global XML namespace that is defined by using an `Imports` statement.</span></span>|  
|`name`|<span data-ttu-id="ed7d9-118">必需。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-118">Required.</span></span> <span data-ttu-id="ed7d9-119">子代节点的本地名称。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-119">Local name of the descendant node.</span></span> <span data-ttu-id="ed7d9-120">请参阅[声明的 XML 元素和特性的名称](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-120">See [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span>|  
  
 \>  
 <span data-ttu-id="ed7d9-121">必需。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-121">Required.</span></span> <span data-ttu-id="ed7d9-122">表示子代轴属性的结尾。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-122">Denotes the end of a descendant axis property.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ed7d9-123">返回值</span><span class="sxs-lookup"><span data-stu-id="ed7d9-123">Return Value</span></span>  
 <span data-ttu-id="ed7d9-124"><xref:System.Xml.Linq.XElement> 对象的集合。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-124">A collection of <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed7d9-125">备注</span><span class="sxs-lookup"><span data-stu-id="ed7d9-125">Remarks</span></span>  
 <span data-ttu-id="ed7d9-126">可以使用 XML 子代轴属性按名称从访问子代节点<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>对象，或从一系列<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XDocument>对象。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-126">You can use an XML descendant axis property to access descendant nodes by name from an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> object, or from a collection of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument> objects.</span></span> <span data-ttu-id="ed7d9-127">使用 XML`Value`属性来访问返回的集合中的第一个子代节点的值。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-127">Use the XML `Value` property to access the value of the first descendant node in the returned collection.</span></span> <span data-ttu-id="ed7d9-128">有关详细信息，请参阅[XML 值属性](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-128">For more information, see [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).</span></span>  
  
 <span data-ttu-id="ed7d9-129">Visual Basic 编译器将调用转换为子代轴属性<xref:System.Xml.Linq.XContainer.Descendants%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-129">The Visual Basic compiler converts descendant axis properties into calls to the <xref:System.Xml.Linq.XContainer.Descendants%2A> method.</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="ed7d9-130">XML 命名空间</span><span class="sxs-lookup"><span data-stu-id="ed7d9-130">XML Namespaces</span></span>  
 <span data-ttu-id="ed7d9-131">子代轴属性中的名称可以使用只有 XML 命名空间与全局声明`Imports`语句。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-131">The name in a descendant axis property can use only XML namespaces declared globally with the `Imports` statement.</span></span> <span data-ttu-id="ed7d9-132">它不能使用在 XML 元素文本中局部声明的 XML 命名空间。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-132">It cannot use XML namespaces declared locally within XML element literals.</span></span> <span data-ttu-id="ed7d9-133">有关详细信息，请参阅[Imports 语句 (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-133">For more information, see [Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed7d9-134">示例</span><span class="sxs-lookup"><span data-stu-id="ed7d9-134">Example</span></span>  
 <span data-ttu-id="ed7d9-135">下面的示例演示如何访问名为的第一个子代节点的值`name`和名为的所有子代节点的值`phone`从`contacts`对象。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-135">The following example shows how to access the value of the first descendant node named `name` and the values of all descendant nodes named `phone` from the `contacts` object.</span></span>  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 <span data-ttu-id="ed7d9-136">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="ed7d9-136">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a><span data-ttu-id="ed7d9-137">示例</span><span class="sxs-lookup"><span data-stu-id="ed7d9-137">Example</span></span>  
 <span data-ttu-id="ed7d9-138">下面的示例声明 `ns` 作为 XML 命名空间前缀。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-138">The following example declares `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="ed7d9-139">然后，它使用的命名空间前缀来创建 XML 文本和访问具有限定名称的第一个子节点的值`ns:name`。</span><span class="sxs-lookup"><span data-stu-id="ed7d9-139">It then uses the prefix of the namespace to create an XML literal and access the value of the first child node with the qualified name `ns:name`.</span></span>  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 <span data-ttu-id="ed7d9-140">此代码显示以下文本：</span><span class="sxs-lookup"><span data-stu-id="ed7d9-140">This code displays the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="ed7d9-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="ed7d9-141">See also</span></span>
- <xref:System.Xml.Linq.XElement>
- [<span data-ttu-id="ed7d9-142">XML 轴属性</span><span class="sxs-lookup"><span data-stu-id="ed7d9-142">XML Axis Properties</span></span>](../../../visual-basic/language-reference/xml-axis/index.md)
- [<span data-ttu-id="ed7d9-143">XML 文本</span><span class="sxs-lookup"><span data-stu-id="ed7d9-143">XML Literals</span></span>](../../../visual-basic/language-reference/xml-literals/index.md)
- [<span data-ttu-id="ed7d9-144">在 Visual Basic 中创建 XML</span><span class="sxs-lookup"><span data-stu-id="ed7d9-144">Creating XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="ed7d9-145">已声明的 XML 元素和特性的名称</span><span class="sxs-lookup"><span data-stu-id="ed7d9-145">Names of Declared XML Elements and Attributes</span></span>](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
