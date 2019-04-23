---
title: x:Key 指令
ms.date: 03/30/2017
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
ms.openlocfilehash: 6ac878f24de594f8557ded8b0c3356217021b035
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223714"
---
# <a name="xkey-directive"></a><span data-ttu-id="7fe74-102">x:Key 指令</span><span class="sxs-lookup"><span data-stu-id="7fe74-102">x:Key Directive</span></span>
<span data-ttu-id="7fe74-103">唯一标识创建和引用 XAML 定义的字典中的元素。</span><span class="sxs-lookup"><span data-stu-id="7fe74-103">Uniquely identifies elements that are created and referenced in a XAML-defined dictionary.</span></span> <span data-ttu-id="7fe74-104">添加`x:Key`XAML 对象元素的值是标识资源字典，例如在 WPF 中的资源的最常见方法<xref:System.Windows.ResourceDictionary>。</span><span class="sxs-lookup"><span data-stu-id="7fe74-104">Adding an `x:Key` value to a XAML object element is the most common way to identify a resource in a resource dictionary, for example in a WPF <xref:System.Windows.ResourceDictionary>.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="7fe74-105">XAML 属性用法</span><span class="sxs-lookup"><span data-stu-id="7fe74-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a><span data-ttu-id="7fe74-106">XAML 特性用法 （特定于 WPF 的）</span><span class="sxs-lookup"><span data-stu-id="7fe74-106">XAML Attribute Usage (WPF-specific)</span></span>  
  
```  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="7fe74-107">XAML 值</span><span class="sxs-lookup"><span data-stu-id="7fe74-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`stringKeyValue`|<span data-ttu-id="7fe74-108">要用作键的文本字符串。</span><span class="sxs-lookup"><span data-stu-id="7fe74-108">A text string to use as a key.</span></span> <span data-ttu-id="7fe74-109">文本字符串必须符合[XamlName 语法](xamlname-grammar.md)。</span><span class="sxs-lookup"><span data-stu-id="7fe74-109">The text string must conform to the [XamlName Grammar](xamlname-grammar.md).</span></span>|  
|`markupExtensionUsage`|<span data-ttu-id="7fe74-110">在标记扩展分隔符内{}，提供一个对象，用作键的标记扩展用法。</span><span class="sxs-lookup"><span data-stu-id="7fe74-110">Within the markup extension delimiters {}, a markup extension usage that provides an object to use as a key.</span></span> <span data-ttu-id="7fe74-111">请参阅“备注”。</span><span class="sxs-lookup"><span data-stu-id="7fe74-111">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fe74-112">备注</span><span class="sxs-lookup"><span data-stu-id="7fe74-112">Remarks</span></span>  
 <span data-ttu-id="7fe74-113">`x:Key` 支持 XAML 资源字典概念。</span><span class="sxs-lookup"><span data-stu-id="7fe74-113">`x:Key` supports the XAML resource dictionary concept.</span></span> <span data-ttu-id="7fe74-114">作为一种语言的 XAML 不定义资源字典实现，而由特定 UI 框架。</span><span class="sxs-lookup"><span data-stu-id="7fe74-114">XAML as a language doesn't define a resource dictionary implementation, that is left to specific UI frameworks.</span></span> <span data-ttu-id="7fe74-115">若要了解有关如何在 WPF 中实现 XAML 资源字典的详细信息，请参阅[XAML 资源](../wpf/advanced/xaml-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="7fe74-115">To learn more about how XAML resource dictionaries are implemented in WPF, see [XAML Resources](../wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="7fe74-116">在 XAML 2006 和 WPF，`x:Key`必须为属性提供。</span><span class="sxs-lookup"><span data-stu-id="7fe74-116">In XAML 2006 and WPF, `x:Key` must be provided as an attribute.</span></span> <span data-ttu-id="7fe74-117">您仍可以使用非字符串键，但这需要标记扩展用法来提供特性窗体中的非字符串值。</span><span class="sxs-lookup"><span data-stu-id="7fe74-117">You can still use nonstring keys, but this requires a markup extension usage in order to provide the nonstring value in attribute form.</span></span> <span data-ttu-id="7fe74-118">如果使用 XAML 2009`x:Key`可以指定为元素，以显式支持以外的对象类型进行键控的字典字符串而不需要标记扩展中间语言。</span><span class="sxs-lookup"><span data-stu-id="7fe74-118">If you are using XAML 2009, `x:Key` can be specified as an element, to explicitly support dictionaries keyed by object types other than strings without requiring a markup extension intermediate.</span></span> <span data-ttu-id="7fe74-119">请参阅本主题中的"XAML 2009"一节。</span><span class="sxs-lookup"><span data-stu-id="7fe74-119">See the "XAML 2009" section in this topic.</span></span> <span data-ttu-id="7fe74-120">备注部分的其余部分特别适用于 XAML 2006 实现。</span><span class="sxs-lookup"><span data-stu-id="7fe74-120">The remainder of the Remarks section applies specifically to the XAML 2006 implementation.</span></span>  
  
 <span data-ttu-id="7fe74-121">属性值`x:Key`可以中定义的任何字符串[XamlName 语法](xamlname-grammar.md)也可以是计算通过标记扩展的对象。</span><span class="sxs-lookup"><span data-stu-id="7fe74-121">The attribute value of `x:Key` can be any string defined in the [XamlName Grammar](xamlname-grammar.md) or can be an object evaluated through a markup extension.</span></span> <span data-ttu-id="7fe74-122">从 WPF 示例，请参阅"WPF 用法说明"。</span><span class="sxs-lookup"><span data-stu-id="7fe74-122">See "WPF Usage Notes" for an example from WPF.</span></span>  
  
 <span data-ttu-id="7fe74-123">父元素的子元素<xref:System.Collections.IDictionary>实现通常必须包括`x:Key`指定该字典中的唯一键值的属性。</span><span class="sxs-lookup"><span data-stu-id="7fe74-123">Child elements of a parent element that is an <xref:System.Collections.IDictionary> implementation must typically include an `x:Key` attribute that specifies a unique key value within that dictionary.</span></span> <span data-ttu-id="7fe74-124">Frameworks 可以实现具有别名的键属性将替换为`x:Key`对特定类型; 定义此类属性的类型应归因与<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>。</span><span class="sxs-lookup"><span data-stu-id="7fe74-124">Frameworks might implement aliased key properties to substitute for `x:Key` on particular types; types that define such properties should be attributed with <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.</span></span>  
  
 <span data-ttu-id="7fe74-125">指定的代码等效项`x:Key`是用于基础的关键<xref:System.Collections.IDictionary>。</span><span class="sxs-lookup"><span data-stu-id="7fe74-125">The code equivalent of specifying `x:Key` is the key that is used for the underlying <xref:System.Collections.IDictionary>.</span></span> <span data-ttu-id="7fe74-126">例如， `x:Key` WPF 中的资源是等效的值应用于标记`key`的参数<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>时将资源添加到 WPF<xref:System.Windows.ResourceDictionary>在代码中。</span><span class="sxs-lookup"><span data-stu-id="7fe74-126">For example, an `x:Key` that is applied in markup for a resource in WPF is equivalent to the value of the `key` parameter of <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> when you add the resource to a WPF <xref:System.Windows.ResourceDictionary> in code.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="7fe74-127">WPF 用法说明</span><span class="sxs-lookup"><span data-stu-id="7fe74-127">WPF Usage Notes</span></span>  
 <span data-ttu-id="7fe74-128">子对象的父对象，它是<xref:System.Collections.IDictionary>实现，如 WPF <xref:System.Windows.ResourceDictionary>，通常必须包括`x:Key`特性和密钥值必须是唯一的字典中。</span><span class="sxs-lookup"><span data-stu-id="7fe74-128">Child objects of a parent object that is an <xref:System.Collections.IDictionary> implementation, such as the WPF <xref:System.Windows.ResourceDictionary>, must typically include an `x:Key` attribute, and the key value must be unique within that dictionary.</span></span> <span data-ttu-id="7fe74-129">有两个值得注意的例外情况：</span><span class="sxs-lookup"><span data-stu-id="7fe74-129">There are two notable exceptions:</span></span>  
  
-   <span data-ttu-id="7fe74-130">某些 WPF 类型声明一个隐式字典用法键。</span><span class="sxs-lookup"><span data-stu-id="7fe74-130">Some WPF types declare an implicit key for dictionary usage.</span></span> <span data-ttu-id="7fe74-131">例如，<xref:System.Windows.Style>与<xref:System.Windows.Style.TargetType%2A>，或<xref:System.Windows.DataTemplate>与<xref:System.Windows.DataTemplate.DataType%2A>，可以采用<xref:System.Windows.ResourceDictionary>，并使用隐式键。</span><span class="sxs-lookup"><span data-stu-id="7fe74-131">For example, a <xref:System.Windows.Style> with a <xref:System.Windows.Style.TargetType%2A>, or a <xref:System.Windows.DataTemplate> with a <xref:System.Windows.DataTemplate.DataType%2A>, can be  in a <xref:System.Windows.ResourceDictionary> and use the implicit key.</span></span>  
  
-   <span data-ttu-id="7fe74-132">WPF 支持合并的资源字典概念。</span><span class="sxs-lookup"><span data-stu-id="7fe74-132">WPF supports a merged resource dictionary concept.</span></span> <span data-ttu-id="7fe74-133">可之间合并的字典中，共享密钥和共享的键行为可以使用访问<xref:System.Windows.FrameworkContentElement.FindResource%2A>。</span><span class="sxs-lookup"><span data-stu-id="7fe74-133">Keys can be shared between the merged dictionaries, and the shared key behavior can be accessed using <xref:System.Windows.FrameworkContentElement.FindResource%2A>.</span></span> <span data-ttu-id="7fe74-134">有关详细信息，请参阅[合并资源字典](../wpf/advanced/merged-resource-dictionaries.md)。</span><span class="sxs-lookup"><span data-stu-id="7fe74-134">For more information, see [Merged Resource Dictionaries](../wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
 <span data-ttu-id="7fe74-135">在整个 WPF XAML 实现和应用程序模型中，不会 XAML 标记编译器检查键唯一性。</span><span class="sxs-lookup"><span data-stu-id="7fe74-135">In the overall WPF XAML implementation and application model, key uniqueness is not checked by the XAML markup compiler.</span></span> <span data-ttu-id="7fe74-136">相反，丢失或非唯一`x:Key`值会导致加载时 XAML 分析器错误。</span><span class="sxs-lookup"><span data-stu-id="7fe74-136">Instead, missing or nonunique `x:Key` values cause load-time XAML parser errors.</span></span> <span data-ttu-id="7fe74-137">但是，WPF 的字典的 Visual Studio 处理可以通常在设计阶段注意此类错误。</span><span class="sxs-lookup"><span data-stu-id="7fe74-137">However, Visual Studio handling of dictionaries for WPF can often note such errors in the design phase.</span></span>  
  
 <span data-ttu-id="7fe74-138">请注意，在所示的语法<xref:System.Windows.ResourceDictionary>对象是隐式的 WPF XAML 处理器如何生成一个集合来填充<xref:System.Windows.FrameworkElement.Resources%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="7fe74-138">Note that in the syntax shown, the <xref:System.Windows.ResourceDictionary> object is implicit in how the WPF XAML processor produces a collection to populate a <xref:System.Windows.FrameworkElement.Resources%2A> collection.</span></span> <span data-ttu-id="7fe74-139">一个<xref:System.Windows.ResourceDictionary>未通常提供显式为元素在标记中，但也可以是在某些情况下，如果为了清楚起见希望 (它将是一个集合对象元素之间<xref:System.Windows.FrameworkElement.Resources%2A>属性元素，并在其中的项填充字典）。</span><span class="sxs-lookup"><span data-stu-id="7fe74-139">A <xref:System.Windows.ResourceDictionary> is not typically provided explicitly as an element in markup, although it can be in some cases if wanted for clarity (it would be a collection object element between the <xref:System.Windows.FrameworkElement.Resources%2A> property element and the items within that populate the dictionary).</span></span> <span data-ttu-id="7fe74-140">有关为什么集合对象几乎始终是在标记中的隐式元素的信息，请参阅[XAML 语法详述](../wpf/advanced/xaml-syntax-in-detail.md)。</span><span class="sxs-lookup"><span data-stu-id="7fe74-140">For information about why a collection object is almost always an implicit element in markup, see [XAML Syntax In Detail](../wpf/advanced/xaml-syntax-in-detail.md).</span></span>  
  
 <span data-ttu-id="7fe74-141">在 WPF XAML 实现中，通过定义资源字典键处理<xref:System.Windows.ResourceKey>抽象类。</span><span class="sxs-lookup"><span data-stu-id="7fe74-141">In the WPF XAML implementation, the handling for resource dictionary keys is defined by the <xref:System.Windows.ResourceKey> abstract class.</span></span> <span data-ttu-id="7fe74-142">但是，WPF XAML 处理器会生成有关基于其用法的密钥不同的基础扩展类型。</span><span class="sxs-lookup"><span data-stu-id="7fe74-142">However the WPF XAML processor produces different underlying extension types for keys based on their usages.</span></span> <span data-ttu-id="7fe74-143">例如，键<xref:System.Windows.DataTemplate>或任何派生的类单独处理的并生成一个不同<xref:System.Windows.DataTemplateKey>对象。</span><span class="sxs-lookup"><span data-stu-id="7fe74-143">For example, the key for a <xref:System.Windows.DataTemplate> or any derived class is handled separately, and produces a distinct <xref:System.Windows.DataTemplateKey> object.</span></span>  
  
 <span data-ttu-id="7fe74-144">键和名称使用不同的指令和语言元素 (`x:Key`与`x:Name`) 中的基本 XAML 定义。</span><span class="sxs-lookup"><span data-stu-id="7fe74-144">Keys and names use different directives and language elements (`x:Key` versus `x:Name`) in the basic XAML definition.</span></span> <span data-ttu-id="7fe74-145">键和名称也使用不同的情况下的 WPF 定义和应用程序的这些概念。</span><span class="sxs-lookup"><span data-stu-id="7fe74-145">Keys and names are also used in different situations by the WPF definition and application of these concepts.</span></span> <span data-ttu-id="7fe74-146">有关详细信息，请参阅[WPF XAML 名称范围](../wpf/advanced/wpf-xaml-namescopes.md)。</span><span class="sxs-lookup"><span data-stu-id="7fe74-146">For details, see [WPF XAML Namescopes](../wpf/advanced/wpf-xaml-namescopes.md).</span></span>  
  
 <span data-ttu-id="7fe74-147">如前面所述，密钥的值可以通过标记扩展提供，并可以是字符串值以外的值。</span><span class="sxs-lookup"><span data-stu-id="7fe74-147">As stated previously, the value of a key can be supplied through a markup extension and can be other than a string value.</span></span> <span data-ttu-id="7fe74-148">示例 WPF 方案是，值`x:Key`可能[ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md)。</span><span class="sxs-lookup"><span data-stu-id="7fe74-148">An example WPF scenario is that the value of `x:Key` may be a [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md).</span></span> <span data-ttu-id="7fe74-149">某些控件公开该类型的自定义样式资源的影响而不替换样式的外观和行为，该控件的样式键。</span><span class="sxs-lookup"><span data-stu-id="7fe74-149">Certain controls expose a style key of that type for a custom style resource that influences part of the appearance and behavior of that control without totally replacing the style.</span></span> <span data-ttu-id="7fe74-150">此类密钥的一个示例是<xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="7fe74-150">An example of such a key is <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.</span></span>  
  
 <span data-ttu-id="7fe74-151">WPF 合并的词典功能引入了关于键唯一性和键查找行为的其他注意事项。</span><span class="sxs-lookup"><span data-stu-id="7fe74-151">The WPF merged dictionary feature introduces additional considerations for key uniqueness and key lookup behavior.</span></span> <span data-ttu-id="7fe74-152">有关详细信息，请参阅[合并资源字典](../wpf/advanced/merged-resource-dictionaries.md)。</span><span class="sxs-lookup"><span data-stu-id="7fe74-152">For more information, see [Merged Resource Dictionaries](../wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="7fe74-153">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="7fe74-153">XAML 2009</span></span>  
 <span data-ttu-id="7fe74-154">XAML 2009 解除此限制的`x:Key`始终以特性形式提供。</span><span class="sxs-lookup"><span data-stu-id="7fe74-154">XAML 2009 relaxes the restriction that `x:Key` always be provided in attribute form.</span></span>  
  
 <span data-ttu-id="7fe74-155">在 WPF 中，您可以使用 XAML 2009 功能，但仅针对未标记编译的 XAML。</span><span class="sxs-lookup"><span data-stu-id="7fe74-155">In WPF, you can use XAML 2009 features, but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="7fe74-156">WPF 的已编译标记的 XAML 以及 XAML 的 BAML 形式当前不支持 XAML 2009 关键字和功能。</span><span class="sxs-lookup"><span data-stu-id="7fe74-156">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="7fe74-157">您可以指定在 XAML 2009 下`x:Key`元素通过下面的用法：</span><span class="sxs-lookup"><span data-stu-id="7fe74-157">Under XAML 2009, you can specify `x:Key` elements through the following usage:</span></span>  
  
### <a name="xaml-element-usage-xaml-2009-only"></a><span data-ttu-id="7fe74-158">XAML 元素使用情况 (仅 XAML 2009)</span><span class="sxs-lookup"><span data-stu-id="7fe74-158">XAML Element Usage (XAML 2009 only)</span></span>  
  
```  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a><span data-ttu-id="7fe74-159">XAML 值</span><span class="sxs-lookup"><span data-stu-id="7fe74-159">XAML Values</span></span>  
  
|||  
|-|-|  
|`keyObject`|<span data-ttu-id="7fe74-160">用作键的对象的对象元素给定`object`专用字典中。</span><span class="sxs-lookup"><span data-stu-id="7fe74-160">Object element for the object that is used as the key for a given `object` in a specialized dictionary.</span></span>|  
  
-   <span data-ttu-id="7fe74-161">使用此类容器/父级不在此处显示。</span><span class="sxs-lookup"><span data-stu-id="7fe74-161">The container/parent for this kind of use is not shown here.</span></span> <span data-ttu-id="7fe74-162">`object` 应为表示专用的词典实现的对象元素的子级。</span><span class="sxs-lookup"><span data-stu-id="7fe74-162">`object` is expected to be a child of an object element that represents a specialized dictionary implementation.</span></span> <span data-ttu-id="7fe74-163">`keyObject` 应为对象实例 （或值类型的值），适合用作该特定专用的词典实现的密钥。</span><span class="sxs-lookup"><span data-stu-id="7fe74-163">`keyObject` is expected to be an object instance (or a value of a value type) that is appropriate as the key for that particular specialized dictionary implementation.</span></span>  
  
-   <span data-ttu-id="7fe74-164">WPF 不实现需要这种用法的字典。</span><span class="sxs-lookup"><span data-stu-id="7fe74-164">WPF does not implement dictionaries that require this usage.</span></span> <span data-ttu-id="7fe74-165">对象键是更常规 XAML 语言，其中在 XAML 中创建字典是需要某些自定义词典方案可能是有用的功能。</span><span class="sxs-lookup"><span data-stu-id="7fe74-165">Object keys is more a general feature of the XAML language, possibly useful for certain custom dictionary scenarios where creating the dictionary in XAML is desirable.</span></span> <span data-ttu-id="7fe74-166">有关使用非字符串键用于资源的隐式样式等 WPF 功能，用于建立或指定键的其他方法存在，因此不需要使用对象键。</span><span class="sxs-lookup"><span data-stu-id="7fe74-166">For WPF features such as implicit styles that use non-string keys for resources, other techniques for establishing or specifying the keys exist, so using an object key is not necessary.</span></span>  
  
-   <span data-ttu-id="7fe74-167">*keyObject*也可能是在对象元素窗体，而不是直接对象实例中的标记扩展用法。</span><span class="sxs-lookup"><span data-stu-id="7fe74-167">*keyObject* could also be a markup extension usage in object element form, rather than a direct object instance.</span></span>  
  
## <a name="silverlight-usage-notes"></a><span data-ttu-id="7fe74-168">Silverlight Usage 备注。</span><span class="sxs-lookup"><span data-stu-id="7fe74-168">Silverlight Usage Notes</span></span>  
 <span data-ttu-id="7fe74-169">`x:Key` 适用于 Silverlight 单独说明了。</span><span class="sxs-lookup"><span data-stu-id="7fe74-169">`x:Key` for Silverlight is documented separately.</span></span> <span data-ttu-id="7fe74-170">有关详细信息，请参阅[XAML Namespace （x:）语言功能 (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081)。</span><span class="sxs-lookup"><span data-stu-id="7fe74-170">For more information, see [XAML Namespace (x:) Language Features (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fe74-171">请参阅</span><span class="sxs-lookup"><span data-stu-id="7fe74-171">See also</span></span>

- [<span data-ttu-id="7fe74-172">XAML 资源</span><span class="sxs-lookup"><span data-stu-id="7fe74-172">XAML Resources</span></span>](../wpf/advanced/xaml-resources.md)
- [<span data-ttu-id="7fe74-173">资源和代码</span><span class="sxs-lookup"><span data-stu-id="7fe74-173">Resources and Code</span></span>](../wpf/advanced/resources-and-code.md)
- [<span data-ttu-id="7fe74-174">StaticResource 标记扩展</span><span class="sxs-lookup"><span data-stu-id="7fe74-174">StaticResource Markup Extension</span></span>](../wpf/advanced/staticresource-markup-extension.md)
