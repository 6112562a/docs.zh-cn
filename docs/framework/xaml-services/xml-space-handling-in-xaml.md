---
title: XAML 中的 xml:space 处理
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: d15bab1ad9234959048fa7b7c3fa2bbbeca5fe6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193312"
---
# <a name="xmlspace-handling-in-xaml"></a><span data-ttu-id="aeadf-102">XAML 中的 xml:space 处理</span><span class="sxs-lookup"><span data-stu-id="aeadf-102">xml:space Handling in XAML</span></span>
<span data-ttu-id="aeadf-103">`xml:space`属性是声明了大量空白处理行为对象元素中的 XML 定义的属性。</span><span class="sxs-lookup"><span data-stu-id="aeadf-103">The `xml:space` attribute is an XML-defined attribute that declares the significant white-space processing behavior within an object element.</span></span> <span data-ttu-id="aeadf-104">此行为是相关的所有内容 （内部文本） 元素中包含其中`xml:space`声明和范围也限于子元素。</span><span class="sxs-lookup"><span data-stu-id="aeadf-104">This behavior is relevant for all content (inner text) contained within the element where `xml:space` is declared, and also scopes to child elements.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="aeadf-105">XAML 属性用法</span><span class="sxs-lookup"><span data-stu-id="aeadf-105">XAML Attribute Usage</span></span>  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 <span data-ttu-id="aeadf-106">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="aeadf-106">\- or -</span></span>  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a><span data-ttu-id="aeadf-107">备注</span><span class="sxs-lookup"><span data-stu-id="aeadf-107">Remarks</span></span>  
 <span data-ttu-id="aeadf-108">用于定义`xml:space`中包括其两个可能值的 XAML 属性派生自`xml:space`由 W3C XML 规范定义的"特殊特性"。</span><span class="sxs-lookup"><span data-stu-id="aeadf-108">The definition for the `xml:space` attribute in XAML including its two possible values is derived from `xml:space` as defined as a "special attribute" by W3C specifications for XML.</span></span>  
  
 <span data-ttu-id="aeadf-109">默认值`xml:space`属性是文本值`"default"`。</span><span class="sxs-lookup"><span data-stu-id="aeadf-109">The default value of the `xml:space` attribute is the literal value `"default"`.</span></span> <span data-ttu-id="aeadf-110">值`"default"`，或者如果`xml:space`根本未指定，分析大量空白区域的行为是默认的处理，如本主题中所定义[空格处理在 XAML 中](whitespace-processing-in-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="aeadf-110">For the value `"default"`, or if `xml:space` is not indicated at all, the behavior of significant white-space parsing is the default handling, as defined in the topic [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
 <span data-ttu-id="aeadf-111">若要保留在对象元素内容中的空白区域，指定`xml:space="preserve"`在该对象元素。</span><span class="sxs-lookup"><span data-stu-id="aeadf-111">To preserve white space within object element content, specify `xml:space="preserve"` on that object element.</span></span>  
  
 <span data-ttu-id="aeadf-112">在大多数解释下`xml:space`属性效果和属性的值的作用域为子元素。</span><span class="sxs-lookup"><span data-stu-id="aeadf-112">Under most interpretations, the `xml:space` attribute effects and the value of the attribute are scoped to child elements.</span></span>  
  
 <span data-ttu-id="aeadf-113">在 XAML 中处理空白的完整讨论，请参阅[空格处理在 XAML 中](whitespace-processing-in-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="aeadf-113">For a complete discussion of white-space processing in XAML, see [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeadf-114">请参阅</span><span class="sxs-lookup"><span data-stu-id="aeadf-114">See also</span></span>

- [<span data-ttu-id="aeadf-115">XAML 中的空白处理</span><span class="sxs-lookup"><span data-stu-id="aeadf-115">White-space processing in XAML</span></span>](whitespace-processing-in-xaml.md)
- [<span data-ttu-id="aeadf-116">XAML 概述 (WPF)</span><span class="sxs-lookup"><span data-stu-id="aeadf-116">XAML Overview (WPF)</span></span>](../wpf/advanced/xaml-overview-wpf.md)
