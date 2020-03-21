---
title: TemplateBinding 标记扩展
ms.date: 03/30/2017
f1_keywords:
- TemplateBinding
- TemplateBindingExtension
helpviewer_keywords:
- XAML [WPF], TemplateBinding markup extension
- TemplateBinding markup extensions [WPF]
ms.assetid: 1d25bbfc-dbc2-499d-9f12-419d23d4ac6a
ms.openlocfilehash: 8cebbf717f66b072bc84b2068193ff2fe76ea87b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187284"
---
# <a name="templatebinding-markup-extension"></a>TemplateBinding 标记扩展
连接某一控件模板中的属性值，使之成为模板化控件上另一个属性的值。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性用法  
  
```xml  
<object property="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-attribute-usage-for-setter-property-in-template-or-style"></a>XAML 特性用法（适用于模板或样式的 Setter 属性）  
  
```xml  
<Setter Property="propertyName" Value="{TemplateBinding sourceProperty}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`propertyName`|在资源库语法中设置的属性的 <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType>。|  
|`sourceProperty`|另一个在要模板化的类型上存在的依赖项属性，由其 <xref:System.Windows.DependencyProperty.Name%2A?displayProperty=nameWithType> 来指定。<br /><br /> - 或 -<br /><br /> 由要模板化的目标类型之外的类型所定义的“dotted-down”属性名称。 这实际上是 <xref:System.Windows.PropertyPath>。 请参阅[属性路径 XAML 语法](propertypath-xaml-syntax.md)。|  
  
## <a name="remarks"></a>备注  
 A`TemplateBinding`是模板方案[绑定](binding-markup-extension.md)的优化形式，类似于 使用`Binding``{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=OneWay}`构造的 绑定。 `TemplateBinding` 始终为单向绑定，即使所涉及的属性默认为双向绑定。 所涉及的两个属性都必须是依赖项属性。 为了实现对模板化父级的双向绑定，请使用`{Binding RelativeSource={RelativeSource TemplatedParent}, Mode=TwoWay, Path=MyDependencyProperty}`以下绑定语句。
  
 [相对源](relativesource-markupextension.md)是另一个标记扩展，有时用于与模板中执行相对属性绑定`TemplateBinding`，而不是一起使用。  
  
 此处未介绍将控件模板描述为概念;有关详细信息，请参阅[控件样式和模板](../controls/control-styles-and-templates.md)。  
  
 特性语法是最常用于该标记扩展的语法。 在 `TemplateBinding` 标识符字符串之后提供的字符串标记被指定为基础 <xref:System.Windows.TemplateBindingExtension.Property%2A> 扩展类的 <xref:System.Windows.TemplateBindingExtension> 值。  
  
 对象元素语法也可行，但因为没有实际的应用，所以未进行演示。 `TemplateBinding` 用于使用计算的表达式来填充资源库内的值，因此使用 `TemplateBinding` 的对象元素语法来填充 `<Setter.Property>` 属性元素语法就会变得繁冗而多余。  
  
 `TemplateBinding` 还可以在详细特性用法中使用，以便将 <xref:System.Windows.TemplateBindingExtension.Property%2A> 属性指定为一个 property=value 对：  
  
```xml  
<object property="{TemplateBinding Property=sourceProperty}" .../>  
```  
  
 如果扩展具有一个以上的可设置属性，或者某些属性是可选的，则详细用法通常会很有用。 由于 `TemplateBinding` 仅有一个可设置的属性，并且此属性是必需的，因此该详细用法不具有典型性。  
  
 在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 处理器实现中，此标记扩展的处理由<xref:System.Windows.TemplateBindingExtension>类定义。  
  
 `TemplateBinding` 是标记扩展。 当要求转义特性值应为非文本值或非处理程序名称时，通常会实现标记扩展，相对于只在某些类型或属性上放置类型转换器而言，此需求更具有全局性。 XAML 中的所有标记扩展在其属性语法中使用`{``}`和 字符，这是 XAML 处理器识别标记扩展必须处理该属性的约定。 有关详细信息，请参阅[标记扩展和 WPF XAML](markup-extensions-and-wpf-xaml.md)。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Style>
- <xref:System.Windows.Controls.ControlTemplate>
- [样式设置和模板化](../controls/styling-and-templating.md)
- [XAML 概述 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [标记扩展和 WPF XAML](markup-extensions-and-wpf-xaml.md)
- [RelativeSource MarkupExtension](relativesource-markupextension.md)
- [Binding 标记扩展](binding-markup-extension.md)
