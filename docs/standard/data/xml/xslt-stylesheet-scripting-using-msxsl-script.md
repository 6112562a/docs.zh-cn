---
title: 使用 &lt;msxsl:script&gt; 编写 XSLT 样式表脚本
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c57f8964172d351ddae048ea36e63a13cf2578d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563426"
---
# <a name="xslt-stylesheet-scripting-using-ltmsxslscriptgt"></a><span data-ttu-id="808ed-102">使用 &lt;msxsl:script&gt; 编写 XSLT 样式表脚本</span><span class="sxs-lookup"><span data-stu-id="808ed-102">XSLT Stylesheet Scripting Using &lt;msxsl:script&gt;</span></span>
<span data-ttu-id="808ed-103"><xref:System.Xml.Xsl.XslTransform> 类使用 `script` 元素支持嵌入的脚本。</span><span class="sxs-lookup"><span data-stu-id="808ed-103">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="808ed-104"><xref:System.Xml.Xsl.XslTransform> 类在 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] 中已过期。</span><span class="sxs-lookup"><span data-stu-id="808ed-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="808ed-105">可以使用 <xref:System.Xml.Xsl.XslCompiledTransform> 类执行可扩展样式表语言转换 (XSLT) 转换。</span><span class="sxs-lookup"><span data-stu-id="808ed-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="808ed-106">请参阅[使用 XslCompiledTransform 类](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md)和[从 XslTransform 类迁移](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md)，以获取详细信息。</span><span class="sxs-lookup"><span data-stu-id="808ed-106">See [Using the XslCompiledTransform Class](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="808ed-107"><xref:System.Xml.Xsl.XslTransform> 类使用 `script` 元素支持嵌入的脚本。</span><span class="sxs-lookup"><span data-stu-id="808ed-107">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="808ed-108">加载样式表时，任何已定义的函数都会通过包装在类定义中来编译为 Microsoft 中间语言 (MSIL)，因此不会有任何性能损失。</span><span class="sxs-lookup"><span data-stu-id="808ed-108">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="808ed-109">`<msxsl:script>` 元素定义如下：</span><span class="sxs-lookup"><span data-stu-id="808ed-109">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="808ed-110">其中 `msxsl` 是绑定到命名空间 `urn:schemas-microsoft-com:xslt` 的前缀。</span><span class="sxs-lookup"><span data-stu-id="808ed-110">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="808ed-111">`language` 属性不是强制属性，但如果指定该属性，其值必须是下列值之一：C#、VB、JScript、JavaScript、VisualBasic 或 CSharp。</span><span class="sxs-lookup"><span data-stu-id="808ed-111">The `language` attribute is not mandatory, but if specified, its value must be one of the following: C#, VB, JScript, JavaScript, VisualBasic, or CSharp.</span></span> <span data-ttu-id="808ed-112">如果未指定，则默认语言为 JScript。</span><span class="sxs-lookup"><span data-stu-id="808ed-112">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="808ed-113">`language-name` 不区分大小写，所以“JavaScript”和“javascript”等效。</span><span class="sxs-lookup"><span data-stu-id="808ed-113">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="808ed-114">`implements-prefix` 属性是必选项。</span><span class="sxs-lookup"><span data-stu-id="808ed-114">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="808ed-115">此属性用于声明命名空间并将其与脚本块关联。</span><span class="sxs-lookup"><span data-stu-id="808ed-115">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="808ed-116">此属性的值是表示命名空间的前缀。</span><span class="sxs-lookup"><span data-stu-id="808ed-116">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="808ed-117">此命名空间可以在样式表中的某一位置定义。</span><span class="sxs-lookup"><span data-stu-id="808ed-117">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="808ed-118">因为 `msxsl:script` 元素属于命名空间 `urn:schemas-microsoft-com:xslt`，因此样式表必须包含命名空间声明 `xmlns:msxsl=urn:schemas-microsoft-com:xslt`。</span><span class="sxs-lookup"><span data-stu-id="808ed-118">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="808ed-119">如果脚本调用方没有 <xref:System.Security.Permissions.SecurityPermissionFlag> 访问权限，样式表中的脚本绝不会编译，且无法调用 <xref:System.Xml.Xsl.XslTransform.Load%2A>。</span><span class="sxs-lookup"><span data-stu-id="808ed-119">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="808ed-120">如果调用方有 `UnmanagedCode` 权限，则脚本将编译，但允许的操作取决于加载时提供的证据。</span><span class="sxs-lookup"><span data-stu-id="808ed-120">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="808ed-121">如果使用一个接受 <xref:System.Xml.Xsl.XslTransform.Load%2A> 或 <xref:System.Xml.XmlReader> 的 <xref:System.Xml.XPath.XPathNavigator> 方法加载样式表，则需要使用接受 <xref:System.Xml.Xsl.XslTransform.Load%2A> 自变量作为其参数的 <xref:System.Security.Policy.Evidence> 重载。</span><span class="sxs-lookup"><span data-stu-id="808ed-121">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="808ed-122">为提供证据，调用方必须拥有 <xref:System.Security.Permissions.SecurityPermissionFlag> 权限，以提供脚本程序集的 `Evidence`。</span><span class="sxs-lookup"><span data-stu-id="808ed-122">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="808ed-123">如果调用方没有此权限，则可以将 `Evidence` 参数设置为 `null`。</span><span class="sxs-lookup"><span data-stu-id="808ed-123">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="808ed-124">这会导致 <xref:System.Xml.Xsl.XslTransform.Load%2A> 函数在发现脚本时失败。</span><span class="sxs-lookup"><span data-stu-id="808ed-124">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="808ed-125">`ControlEvidence` 权限是一种权力很大的权限，只应授予高度可信任的代码。</span><span class="sxs-lookup"><span data-stu-id="808ed-125">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="808ed-126">若要从您的程序集中得到证据，请使用 `this.GetType().Assembly.Evidence`。</span><span class="sxs-lookup"><span data-stu-id="808ed-126">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="808ed-127">若要从统一资源标识符 (URI) 得到证据，请使用 `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`。</span><span class="sxs-lookup"><span data-stu-id="808ed-127">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="808ed-128">如果使用接受 <xref:System.Xml.Xsl.XslTransform.Load%2A> 但没有 <xref:System.Xml.XmlResolver> 的 `Evidence` 方法，则程序集的安全区域默认为“完全信任”。</span><span class="sxs-lookup"><span data-stu-id="808ed-128">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="808ed-129">有关详细信息，请参阅 <xref:System.Security.SecurityZone> 和[命名权限集](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3)。</span><span class="sxs-lookup"><span data-stu-id="808ed-129">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="808ed-130">函数可以在 `msxsl:script` 元素内声明。</span><span class="sxs-lookup"><span data-stu-id="808ed-130">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="808ed-131">下表显示了默认情况下支持的命名空间。</span><span class="sxs-lookup"><span data-stu-id="808ed-131">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="808ed-132">可以在列出的命名空间的外部使用类。</span><span class="sxs-lookup"><span data-stu-id="808ed-132">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="808ed-133">然而，这些类必须是完全限定的。</span><span class="sxs-lookup"><span data-stu-id="808ed-133">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="808ed-134">默认命名空间</span><span class="sxs-lookup"><span data-stu-id="808ed-134">Default Namespaces</span></span>|<span data-ttu-id="808ed-135">说明</span><span class="sxs-lookup"><span data-stu-id="808ed-135">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="808ed-136">系统</span><span class="sxs-lookup"><span data-stu-id="808ed-136">System</span></span>|<span data-ttu-id="808ed-137">系统类。</span><span class="sxs-lookup"><span data-stu-id="808ed-137">System class.</span></span>|  
|<span data-ttu-id="808ed-138">System.Collection</span><span class="sxs-lookup"><span data-stu-id="808ed-138">System.Collection</span></span>|<span data-ttu-id="808ed-139">集合类。</span><span class="sxs-lookup"><span data-stu-id="808ed-139">Collection classes.</span></span>|  
|<span data-ttu-id="808ed-140">System.Text</span><span class="sxs-lookup"><span data-stu-id="808ed-140">System.Text</span></span>|<span data-ttu-id="808ed-141">文本类。</span><span class="sxs-lookup"><span data-stu-id="808ed-141">Text classes.</span></span>|  
|<span data-ttu-id="808ed-142">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="808ed-142">System.Text.RegularExpressions</span></span>|<span data-ttu-id="808ed-143">正则表达式类。</span><span class="sxs-lookup"><span data-stu-id="808ed-143">Regular expression classes.</span></span>|  
|<span data-ttu-id="808ed-144">System.Xml</span><span class="sxs-lookup"><span data-stu-id="808ed-144">System.Xml</span></span>|<span data-ttu-id="808ed-145">核心 XML 类。</span><span class="sxs-lookup"><span data-stu-id="808ed-145">Core XML classes.</span></span>|  
|<span data-ttu-id="808ed-146">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="808ed-146">System.Xml.Xsl</span></span>|<span data-ttu-id="808ed-147">XSLT 类。</span><span class="sxs-lookup"><span data-stu-id="808ed-147">XSLT classes.</span></span>|  
|<span data-ttu-id="808ed-148">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="808ed-148">System.Xml.XPath</span></span>|<span data-ttu-id="808ed-149">XML 路径语言 (XPath) 类。</span><span class="sxs-lookup"><span data-stu-id="808ed-149">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="808ed-150">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="808ed-150">Microsoft.VisualBasic</span></span>|<span data-ttu-id="808ed-151">Microsoft Visual Basic 脚本类。</span><span class="sxs-lookup"><span data-stu-id="808ed-151">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="808ed-152">声明函数时，该函数包含在脚本块中。</span><span class="sxs-lookup"><span data-stu-id="808ed-152">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="808ed-153">样式表可以包含多个脚本块，每个脚本块彼此独立运行。</span><span class="sxs-lookup"><span data-stu-id="808ed-153">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="808ed-154">也就是说，如果在脚本块的内部执行，则无法调用在其他脚本块中定义的函数，除非该脚本块声明为具有同一命名空间和同一脚本语言。</span><span class="sxs-lookup"><span data-stu-id="808ed-154">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="808ed-155">由于每个脚本块都可以使用自己的语言，因此脚本块的分析将遵照语言分析器的语法规则进行，必须使用适合所使用语言的语法。</span><span class="sxs-lookup"><span data-stu-id="808ed-155">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="808ed-156">例如，如果使用的是 C# 脚本块，则在该块中使用 XML 注释节点 `<!-- an XML comment -->` 是错误的。</span><span class="sxs-lookup"><span data-stu-id="808ed-156">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="808ed-157">由脚本函数定义的所提供的自变量以及返回值必须是万维网联合会 (W3C) XPath 或 XSLT 类型之一。</span><span class="sxs-lookup"><span data-stu-id="808ed-157">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="808ed-158">下表展示了相应的 W3C 类型、相当的 .NET Framework 类（类型），以及 W3C 类型是 XPath 类型还是 XSLT 类型。</span><span class="sxs-lookup"><span data-stu-id="808ed-158">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="808ed-159">类型</span><span class="sxs-lookup"><span data-stu-id="808ed-159">Type</span></span>|<span data-ttu-id="808ed-160">相当的 .NET Framework 类（类型）</span><span class="sxs-lookup"><span data-stu-id="808ed-160">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="808ed-161">XPath 类型还是 XSLT 类型</span><span class="sxs-lookup"><span data-stu-id="808ed-161">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="808ed-162">String</span><span class="sxs-lookup"><span data-stu-id="808ed-162">String</span></span>|<span data-ttu-id="808ed-163">System.String</span><span class="sxs-lookup"><span data-stu-id="808ed-163">System.String</span></span>|<span data-ttu-id="808ed-164">XPath</span><span class="sxs-lookup"><span data-stu-id="808ed-164">XPath</span></span>|  
|<span data-ttu-id="808ed-165">Boolean</span><span class="sxs-lookup"><span data-stu-id="808ed-165">Boolean</span></span>|<span data-ttu-id="808ed-166">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="808ed-166">System.Boolean</span></span>|<span data-ttu-id="808ed-167">XPath</span><span class="sxs-lookup"><span data-stu-id="808ed-167">XPath</span></span>|  
|<span data-ttu-id="808ed-168">数字</span><span class="sxs-lookup"><span data-stu-id="808ed-168">Number</span></span>|<span data-ttu-id="808ed-169">System.Double</span><span class="sxs-lookup"><span data-stu-id="808ed-169">System.Double</span></span>|<span data-ttu-id="808ed-170">XPath</span><span class="sxs-lookup"><span data-stu-id="808ed-170">XPath</span></span>|  
|<span data-ttu-id="808ed-171">Result Tree Fragment</span><span class="sxs-lookup"><span data-stu-id="808ed-171">Result Tree Fragment</span></span>|<span data-ttu-id="808ed-172">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="808ed-172">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="808ed-173">XSLT</span><span class="sxs-lookup"><span data-stu-id="808ed-173">XSLT</span></span>|  
|<span data-ttu-id="808ed-174">Node Set</span><span class="sxs-lookup"><span data-stu-id="808ed-174">Node Set</span></span>|<span data-ttu-id="808ed-175">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="808ed-175">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="808ed-176">XPath</span><span class="sxs-lookup"><span data-stu-id="808ed-176">XPath</span></span>|  
  
 <span data-ttu-id="808ed-177">如果脚本函数使用下列数值类型之一：Int16、UInt16、Int32、UInt32、Int64、UInt64、Single 或 Decimal，则会将其强制转换为 Double，映射为 W3C XPath 类型的数字。</span><span class="sxs-lookup"><span data-stu-id="808ed-177">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="808ed-178">所有其他类型都通过调用 `ToString` 方法强制转换为字符串。</span><span class="sxs-lookup"><span data-stu-id="808ed-178">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="808ed-179">如果脚本函数使用上述类型以外的类型，或者如果函数在样式表加载到 <xref:System.Xml.Xsl.XslTransform> 对象中时不进行编译，则会引发异常。</span><span class="sxs-lookup"><span data-stu-id="808ed-179">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="808ed-180">使用 `msxsl:script` 元素时，强烈建议将脚本添加到 CDATA 部分中，无论使用何种语言。</span><span class="sxs-lookup"><span data-stu-id="808ed-180">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="808ed-181">例如，下面的 XML 显示放置代码的 CDATA 节的模板。</span><span class="sxs-lookup"><span data-stu-id="808ed-181">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="808ed-182">强烈建议将所有脚本内容都放置在 CDATA 节内，因为给定语言的运算符、标识符或分隔符有可能被错误地解释为 XML。</span><span class="sxs-lookup"><span data-stu-id="808ed-182">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="808ed-183">下面的示例显示如何在脚本中使用逻辑 AND 运算符。</span><span class="sxs-lookup"><span data-stu-id="808ed-183">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="808ed-184">由于“&”符没有转义，因此将引发异常。</span><span class="sxs-lookup"><span data-stu-id="808ed-184">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="808ed-185">文档以 XML 形式加载，并且不对 `msxsl:script` 元素标记之间的文本应用任何特殊处理。</span><span class="sxs-lookup"><span data-stu-id="808ed-185">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="808ed-186">示例</span><span class="sxs-lookup"><span data-stu-id="808ed-186">Example</span></span>  
 <span data-ttu-id="808ed-187">已知圆的半径，下面的示例使用嵌入脚本计算圆的周长。</span><span class="sxs-lookup"><span data-stu-id="808ed-187">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.               
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
    writer.Close()  
  End Sub   
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main()  
   {  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.               
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }  
}  
```  
  
## <a name="input"></a><span data-ttu-id="808ed-188">输入</span><span class="sxs-lookup"><span data-stu-id="808ed-188">Input</span></span>  
 <span data-ttu-id="808ed-189">number.xml</span><span class="sxs-lookup"><span data-stu-id="808ed-189">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>  
```  
  
 <span data-ttu-id="808ed-190">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="808ed-190">calc.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius)  
     {  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">    
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>   
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="808ed-191">输出</span><span class="sxs-lookup"><span data-stu-id="808ed-191">Output</span></span>  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>    
```  
  
## <a name="see-also"></a><span data-ttu-id="808ed-192">请参阅</span><span class="sxs-lookup"><span data-stu-id="808ed-192">See also</span></span>

- [<span data-ttu-id="808ed-193">XslTransform 类实现 XSLT 处理器</span><span class="sxs-lookup"><span data-stu-id="808ed-193">XslTransform Class Implements the XSLT Processor</span></span>](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)
