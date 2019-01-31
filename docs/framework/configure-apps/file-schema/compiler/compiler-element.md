---
title: <compiler> 元素
ms.date: 08/14/2018
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compiler
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers/compiler
helpviewer_keywords:
- compiler configuration elements, <compiler> element
- <compiler> element
- compiler configuration attributes
- compiler element
ms.assetid: 7a151659-b803-4c27-b5ce-1c4aa0d5a823
ms.openlocfilehash: 704d9388a742b333efc3e888233bbf19b8e462c1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286762"
---
# <a name="compiler-element"></a><span data-ttu-id="bdfee-102">\<编译器 > 元素</span><span class="sxs-lookup"><span data-stu-id="bdfee-102">\<compiler> Element</span></span>

<span data-ttu-id="bdfee-103">指定语言提供程序的编译器配置属性。</span><span class="sxs-lookup"><span data-stu-id="bdfee-103">Specifies the compiler configuration attributes for a language provider.</span></span>

<span data-ttu-id="bdfee-104">\<配置元素 > \<system.codedom 元素 > \<compilers 元素 >\<编译器 > 元素</span><span class="sxs-lookup"><span data-stu-id="bdfee-104">\<configuration Element> \<system.codedom Element> \<compilers Element> \<compiler> Element</span></span>

## <a name="syntax"></a><span data-ttu-id="bdfee-105">语法</span><span class="sxs-lookup"><span data-stu-id="bdfee-105">Syntax</span></span>

```xml
<compiler
  language="languageName[;...;...]"
  extension="fileExtension[;...;...]"
  type="typeName, assemblyName"
  warningLevel="number"
  compilerOptions="option1 option2"
/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bdfee-106">特性和元素</span><span class="sxs-lookup"><span data-stu-id="bdfee-106">Attributes and Elements</span></span>

<span data-ttu-id="bdfee-107">下列各节描述了特性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bdfee-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bdfee-108">特性</span><span class="sxs-lookup"><span data-stu-id="bdfee-108">Attributes</span></span>

|<span data-ttu-id="bdfee-109">特性</span><span class="sxs-lookup"><span data-stu-id="bdfee-109">Attribute</span></span>|<span data-ttu-id="bdfee-110">描述</span><span class="sxs-lookup"><span data-stu-id="bdfee-110">Description</span></span>|
|---------------|-----------------|
|`compilerOptions`|<span data-ttu-id="bdfee-111">可选特性。</span><span class="sxs-lookup"><span data-stu-id="bdfee-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="bdfee-112">指定用于编译的其他特定于编译器的参数。</span><span class="sxs-lookup"><span data-stu-id="bdfee-112">Specifies additional compiler-specific arguments for compilation.</span></span> <span data-ttu-id="bdfee-113">值`compilerOptions`属性通常编译器的编译器选项主题中列出。</span><span class="sxs-lookup"><span data-stu-id="bdfee-113">The values for the `compilerOptions` attribute are typically listed in a compiler options topic for the compiler.</span></span>|
|`extension`|<span data-ttu-id="bdfee-114">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="bdfee-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="bdfee-115">提供以分号分隔的语言提供程序的源文件所使用的文件扩展名的列表。</span><span class="sxs-lookup"><span data-stu-id="bdfee-115">Provides a semicolon-separated list of file name extensions used by source files for the language provider.</span></span> <span data-ttu-id="bdfee-116">例如，".cs"。</span><span class="sxs-lookup"><span data-stu-id="bdfee-116">For example, ".cs".</span></span>|
|`language`|<span data-ttu-id="bdfee-117">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="bdfee-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="bdfee-118">提供语言提供程序支持的语言名称之间用分号分隔的列表。</span><span class="sxs-lookup"><span data-stu-id="bdfee-118">Provides a semicolon-separated list of language names supported by the language provider.</span></span> <span data-ttu-id="bdfee-119">例如，"c#; cs; csharp"。</span><span class="sxs-lookup"><span data-stu-id="bdfee-119">For example, "c#;cs;csharp".</span></span>|
|`type`|<span data-ttu-id="bdfee-120">必需的特性。</span><span class="sxs-lookup"><span data-stu-id="bdfee-120">Required attribute.</span></span><br /><br /> <span data-ttu-id="bdfee-121">指定语言提供程序，包括包含的提供程序实现的程序集名称的类型的名称。</span><span class="sxs-lookup"><span data-stu-id="bdfee-121">Specifies the type name of the language provider, including the name of the assembly containing the provider implementation.</span></span> <span data-ttu-id="bdfee-122">类型名称必须满足中定义的要求[指定完全限定的类型名称](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)。</span><span class="sxs-lookup"><span data-stu-id="bdfee-122">The type name must meet the requirements defined in [Specifying Fully Qualified Type Names](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|
|`warningLevel`|<span data-ttu-id="bdfee-123">可选特性。</span><span class="sxs-lookup"><span data-stu-id="bdfee-123">Optional attribute.</span></span><br /><br /> <span data-ttu-id="bdfee-124">指定的默认编译器警告等级;确定在该语言提供程序将编译警告视为错误的级别。</span><span class="sxs-lookup"><span data-stu-id="bdfee-124">Specifies the default compiler warning level; determines the level at which the language provider treats compilation warnings as errors.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="bdfee-125">子元素</span><span class="sxs-lookup"><span data-stu-id="bdfee-125">Child Elements</span></span>

|<span data-ttu-id="bdfee-126">元素</span><span class="sxs-lookup"><span data-stu-id="bdfee-126">Element</span></span>|<span data-ttu-id="bdfee-127">描述</span><span class="sxs-lookup"><span data-stu-id="bdfee-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdfee-128">\<providerOption > 元素</span><span class="sxs-lookup"><span data-stu-id="bdfee-128">\<providerOption> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/provideroption-element.md)|<span data-ttu-id="bdfee-129">指定语言提供程序的编译器版本特性。</span><span class="sxs-lookup"><span data-stu-id="bdfee-129">Specifies compiler version attributes for a language provider.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bdfee-130">父元素</span><span class="sxs-lookup"><span data-stu-id="bdfee-130">Parent Elements</span></span>

|<span data-ttu-id="bdfee-131">元素</span><span class="sxs-lookup"><span data-stu-id="bdfee-131">Element</span></span>|<span data-ttu-id="bdfee-132">描述</span><span class="sxs-lookup"><span data-stu-id="bdfee-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bdfee-133">\<configuration> 元素</span><span class="sxs-lookup"><span data-stu-id="bdfee-133">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="bdfee-134">公共语言运行时和 .NET Framework 应用程序所使用的每个配置文件中的根元素。</span><span class="sxs-lookup"><span data-stu-id="bdfee-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|[<span data-ttu-id="bdfee-135">\<system.codedom > 元素</span><span class="sxs-lookup"><span data-stu-id="bdfee-135">\<system.codedom> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/system-codedom-element.md)|<span data-ttu-id="bdfee-136">指定可用语言提供程序的编译器配置设置。</span><span class="sxs-lookup"><span data-stu-id="bdfee-136">Specifies compiler configuration settings for available language providers.</span></span>|
|[<span data-ttu-id="bdfee-137">\<编译器 > 元素</span><span class="sxs-lookup"><span data-stu-id="bdfee-137">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)|<span data-ttu-id="bdfee-138">编译器配置元素; 容器包含零个或多`<compiler>`元素。</span><span class="sxs-lookup"><span data-stu-id="bdfee-138">Container for compiler configuration elements; contains zero or more `<compiler>` elements.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bdfee-139">备注</span><span class="sxs-lookup"><span data-stu-id="bdfee-139">Remarks</span></span>

<span data-ttu-id="bdfee-140">每个`<compiler>`元素指定特定的语言提供程序的编译器配置属性。</span><span class="sxs-lookup"><span data-stu-id="bdfee-140">Each `<compiler>` element specifies the compiler configuration attributes for a specific language provider.</span></span> <span data-ttu-id="bdfee-141">提供程序可扩展<xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>类的特定语言;`<compiler>`元素定义的编译器和语言提供程序的代码生成器设置。</span><span class="sxs-lookup"><span data-stu-id="bdfee-141">The provider extends the <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> class for a specific language; the `<compiler>` element defines the compiler and code generator settings for the language provider.</span></span>

<span data-ttu-id="bdfee-142">.NET Framework 在计算机配置文件 (Machine.config) 中定义初始编译器设置。</span><span class="sxs-lookup"><span data-stu-id="bdfee-142">The .NET Framework defines the initial compiler settings in the machine configuration file (Machine.config).</span></span> <span data-ttu-id="bdfee-143">开发人员和编译器供应商可以添加新 <xref:System.CodeDom.Compiler.CodeDomProvider> 实现的配置设置。</span><span class="sxs-lookup"><span data-stu-id="bdfee-143">Developers and compiler vendors can add configuration settings for a new <xref:System.CodeDom.Compiler.CodeDomProvider> implementation.</span></span> <span data-ttu-id="bdfee-144">使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以编程方式枚举计算机上的语言提供程序和编译器配置设置。</span><span class="sxs-lookup"><span data-stu-id="bdfee-144">Use the <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> method to programmatically enumerate language provider and compiler configuration settings on a computer.</span></span>

<span data-ttu-id="bdfee-145">在应用程序或 Web 配置文件的编译器元素可以补充或替代计算机配置文件中的设置。</span><span class="sxs-lookup"><span data-stu-id="bdfee-145">Compiler elements in the application or Web configuration file can supplement or override the settings in the machine configuration file.</span></span> <span data-ttu-id="bdfee-146">如果为相同的语言名称或相同的文件扩展名配置了多个提供程序实现，最后一个匹配的配置将覆盖该语言名称或文件扩展的任何先前已配置提供程序。</span><span class="sxs-lookup"><span data-stu-id="bdfee-146">If more than one provider implementation is configured for the same language name or the same file extension, the last matching configuration overrides any previous configured providers for that language name or file extension.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="bdfee-147">配置文件</span><span class="sxs-lookup"><span data-stu-id="bdfee-147">Configuration File</span></span>

<span data-ttu-id="bdfee-148">计算机配置文件和应用程序配置文件中，可以使用此元素。</span><span class="sxs-lookup"><span data-stu-id="bdfee-148">This element can be used in the machine configuration file and the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="bdfee-149">示例</span><span class="sxs-lookup"><span data-stu-id="bdfee-149">Example</span></span>

<span data-ttu-id="bdfee-150">下面的示例演示一个典型的编译器配置元素：</span><span class="sxs-lookup"><span data-stu-id="bdfee-150">The following example illustrates a typical compiler configuration element:</span></span>

```xml
<configuration>
  <system.codedom>
    <compilers>
      <!-- zero or more compiler elements -->
      <compiler
        language="c#;cs;csharp"
        extension=".cs"
        type="Microsoft.CSharp.CSharpCodeProvider, System,
          Version=2.0.3600.0, Culture=neutral,
          PublicKeyToken=b77a5c561934e089"
        compilerOptions="/optimize"
        warningLevel="1" />
    </compilers>
  </system.codedom>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="bdfee-151">请参阅</span><span class="sxs-lookup"><span data-stu-id="bdfee-151">See also</span></span>

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [<span data-ttu-id="bdfee-152">配置文件架构</span><span class="sxs-lookup"><span data-stu-id="bdfee-152">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="bdfee-153">\<编译器 > 元素</span><span class="sxs-lookup"><span data-stu-id="bdfee-153">\<compilers> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/compiler/compilers-element.md)
- [<span data-ttu-id="bdfee-154">指定完全限定的类型名称</span><span class="sxs-lookup"><span data-stu-id="bdfee-154">Specifying Fully Qualified Type Names</span></span>](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)
- <span data-ttu-id="bdfee-155">[（ASP.NET 设置架构） compilation 的 compilers 的 compiler 元素](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="bdfee-155">[compiler Element for compilers for compilation (ASP.NET Settings Schema)](https://msdn.microsoft.com/library/f7d6b078-5d42-4134-b3f7-62e1aba1df1e(v=vs.100))</span></span>
